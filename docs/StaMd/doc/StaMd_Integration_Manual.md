---
layout: default
title: StaMd_Integration_Manual
nav_order: 3
parent: State and Modes
---
{% raw %}
[1 Dependencies [2](#dependencies)](#dependencies)

[1.1 SWCs [2](#swcs)](#swcs)

[1.2 Functions to be provided to Integration Project
[2](#global-functionsnon-rte-to-be-provided-to-integration-project)](#global-functionsnon-rte-to-be-provided-to-integration-project)

[2 Configuration [3](#configuration)](#configuration)

[2.1 Build Time Config [3](#build-time-config)](#build-time-config)

[2.2 Configuration Files to be provided by Integration Project
[3](#configuration-files-to-be-provided-by-integration-project)](#configuration-files-to-be-provided-by-integration-project)

[2.2.1 Da Vinci Config generation
[3](#da-vinci-parameter-configuration-changes)](#da-vinci-parameter-configuration-changes)

[2.2.2 Manual Configuration Changes
[3](#da-vinci-parameter-configuration-changes)](#da-vinci-parameter-configuration-changes)

[3 Integration [4](#integration)](#integration)

[3.1 Required Global Data Inputs
[4](#required-global-data-inputs)](#required-global-data-inputs)

[3.2 Optional Global Data Inputs [4](#_Toc357692828)](#_Toc357692828)

[3.3 Specific Include Path present
[4](#specific-include-path-present)](#specific-include-path-present)

[4 Runnable Scheduling [5](#runnable-scheduling)](#runnable-scheduling)

[5 Memory Mapping [6](#memory-mapping)](#memory-mapping)

[5.1 Mapping [6](#mapping)](#mapping)

[5.2 Usage [6](#usage)](#usage)

[5.3 NvM Blocks [6](#non-rte-nvm-blocks)](#non-rte-nvm-blocks)

[6 Compiler Settings [6](#compiler-settings)](#compiler-settings)

[6.1 Preprocessor MACRO [6](#preprocessor-macro)](#preprocessor-macro)

[6.2 Optimization Settings
[6](#optimization-settings)](#optimization-settings)

[7 Revision Control Log
[7](#revision-control-log)](#revision-control-log)

# Dependencies

## SWCs

<table>
<colgroup>
<col style="width: 30%" />
<col style="width: 69%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Module</strong></th>
<th><strong>Required Feature</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>ECUStatup.c</strong></td>
<td><p>StaMd_Init0 needs to be called from EcuStartup_Init2 via a
trusted wrapper after Nvm ‘read all’ is complete, by calling
Call_StaMd_Init0.</p>
<p>ECUStartup needs to also include the Ap_StaMd.h header file.</p>
<p>The StaMd_Init0 is defined outside of the RTE and is responsible for
updating Type H memory across applications at start up. StaMd_Init0
needs to be added to a non-trusted function list in a trusted
application in the O.S.</p></td>
</tr>
<tr class="even">
<td><strong>NtWrap.c, .h, O.S changes</strong></td>
<td><p>Add trusted function call to NtWrap :</p>
<p>/* Trusted wrapper Function */</p>
<p>void TRUSTED_NtWrapS_StaMd_Init0</p>
<p>(TrustedFunctionIndexType FunctionIndex,
TrustedFunctionParameterRefType FunctionParams)</p>
<p>{</p>
<p>StaMd_Init0();</p>
<p>}</p>
<p>…</p>
<p>void <mark>Call_StaMd_Init0</mark>(void)</p>
<p>{</p>
<p>(void) CallTrustedFunction</p>
<p>(NtWrapS_StaMd_Init0,</p>
<p>(TrustedFunctionParameterRefType)0);</p>
<p>}</p></td>
</tr>
<tr class="odd">
<td><strong>Optional NvM Fast Write implementation to meet program
specific ECUReset or Programming session transition timing
requirements.</strong></td>
<td><p>Whenever an ECU Reset (StaMd_SCom_EcuReset) or
FlashBootloader/Programming session service request
(StaMd_SCom_FBLTransitionReq ) the StaMd module is notified by the
corresponding Scom functions, typically called directly from the
diagnostic service handler. The system is then forced to the OFF state
and an output flag, <strong>InitiatePwrDnFastWrite_Cnt_lgc</strong> is
set to TRUE. This flag can be used to trigger a FAST NVM write as an
option to meet ECU Rest and/or FlashBootloader/Programming session
timing requirements.</p>
<p>The <strong>InitiatePwrDnNormalWrite_Cnt_lgc</strong> output flag
will be set to TRUE in case of a normal transition to OFF.</p>
<p>The implementation of the “fast” NvM write is done by running the
main functions responsible for handling the NvM processing continuously
in a WHILE loop until all of NvM, including the closecheck flag used for
NTC $BF, has been written. These main functions (NvM, Ea, NvMProxy etc…)
are typically called from a SchM task. <strong><mark>Since the fast
write occurs in a WHILE loop, it is important that the</mark></strong>
<strong><mark>fast write is implemented in a low
priority</mark></strong> <strong><mark>SchM task.</mark></strong>
<strong><mark>Review the task priorities before
implementation.</mark></strong></p>
<p>For example, see the Ford S550/P552 fast NvM write implementation
below. This is in a priority 2 SchM task. The only other tasks with a
lower priority are the Background task and a SchM init task:</p>
<p><strong>do</strong></p>
<p>{</p>
<p>GetResource(OsRes_MemStackTask);</p>
<p>Eep_30_At25128_MainFunction();</p>
<p>Ea_MainFunction();</p>
<p>NvMProxy_MainFunction();</p>
<p>NvM_MainFunction();</p>
<p>ReleaseResource(OsRes_MemStackTask);</p>
<p>}<strong>while</strong>(<mark>CDD_InitiatePwrDn<strong>FastWrite</strong>_Cnt_G_lgc</mark>
== TRUE);</p>
<p>In the case of a FlashBootloader/Programming session service request
(<strong>StaMd_SCom_FBLTransitionReq)</strong>, once the NvM write is
complete the output flag,
<strong>PwrDnFastWriteComplete_Cnt_lgc</strong>, will be set to TRUE
(<strong>See the Data Dictionary</strong>). The
PwrDn<strong>FastWriteComplete</strong> flag can be used as follows to
complete a FlashBootloader/Programming session transition request:</p>
<p>if (ProgrammingSessionEntered_Cnt_M_lgc == TRUE)</p>
<p>{</p>
<p>if
(<mark>CDD_PwrDn<strong>FastWriteComplete</strong>_Cnt_G_lgc</mark> ==
TRUE)</p>
<p>{</p>
<p>ProgrammingSessionEntered_Cnt_M_lgc = FALSE;</p>
<p>/* <strong>Jump to Bootloader</strong> */</p>
<p>Program Specific Vector to Bootloader</p>
<p>}</p>
<p>}</p>
<p>These status flags can be provided to complex device drivers, such as
SchM, via CDD interface by creating the following global variables:
<strong>CDD_PwrDnFastWriteComplete_Cnt_G_lgc</strong>,
<strong>CDD_InitiatePwrDnFastWrite_Cnt_G_lgc,
CDD_InitiatePwrDnNormalWrite_Cnt_G_lgc</strong></p>
<p><strong>NOTE:</strong> The StaMd_SCom_FBLTransitionReq should only be
used to update NvM, if required, before transitioning to the bootloader
in response to a diagnostic service request to transition to a flash
programming session. Only use this Scom function as intended. Once this
Scom function is called a reset or vector from the application is
expected after the PwrDnFastWriteComplete flag has been set to
true.</p></td>
</tr>
<tr class="even">
<td></td>
<td></td>
</tr>
</tbody>
</table>

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
refered. Developer should track the references.

## Global Functions(Non RTE) to be provided to Integration Project

extern FUNC(void, MCU_CODE) **Mcu_PerformReset**(void);

# Configuration

## Build Time Config

| **Modules**  | **Notes** |     |
|--------------|-----------|-----|
| **\<None\>** |           |     |

## Configuration Files to be provided by Integration Project

##  [section]

**Ap_StaMd_Cfg.h**

### Da Vinci Parameter Configuration Changes

<table>
<colgroup>
<col style="width: 44%" />
<col style="width: 43%" />
<col style="width: 11%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Parameter</strong></th>
<th><strong>Notes</strong></th>
<th><strong>SWC</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>TypeHDataSize</strong></td>
<td>Total size of all Type H data in bytes</td>
<td></td>
</tr>
<tr class="even">
<td><strong>StaMdCPEnable</strong></td>
<td>This container contains the configuration (parameters) for the StaMd
Watchdog checkpoints.</td>
<td></td>
</tr>
<tr class="odd">
<td><strong>StaMdTODType</strong></td>
<td><p>This container defines the configuration for the type of TOD
implementation used:</p>
<p>TOD_2msToggle</p>
<p>TOD_SteadyState (*common setting)</p>
<p>TOD_None</p></td>
<td></td>
</tr>
<tr class="even">
<td><strong>StaMdNvMWriteAllAPI</strong></td>
<td>This container defines the API used for the NvM Write All function.
(*common setting is <strong>NvMProxy_WriteAll</strong> if the NvM proxy
is used).</td>
<td></td>
</tr>
<tr class="odd">
<td><strong>StaMdNvMGetErrorStatusAPI</strong></td>
<td>This container defines the API used for the NvM Get Error Status
function. (*common setting is <strong>NvMProxy_GetErrorStatus</strong>
if the NvM proxy is used).</td>
<td></td>
</tr>
<tr class="even">
<td><strong>StaMdTrnsDiagMgrShtDwnTaskActivation</strong></td>
<td><p>This container defines the DiagMgr shutdown function. If
StaMdCoreOsAppRef matches the application referenced for
DiagMgrDemIfOsAppRef in DiagMgr then the generated output will be a
client/server call and this field is ignored. If they do not match, then
a task activation call is created and the task defined in this field is
activated.</p>
<p><strong>NOTE:</strong> Typical setting is Task_TrnsB_9 for the
application 9 transition function, from which the
StaMd9_Trns_DemShutdown function is called in some programs.</p></td>
<td></td>
</tr>
<tr class="odd">
<td><strong>GenerateExcludeOsAppRef</strong></td>
<td>This parameter defines the application(s) which do not require a
States and Modes component.</td>
<td></td>
</tr>
<tr class="even">
<td><strong>StaMdCoreOsAppRef</strong></td>
<td>This parameter defines the application which contains the core
States and Modes component.</td>
<td></td>
</tr>
<tr class="odd">
<td><strong>StaMdsComOsAppRef</strong></td>
<td>This parameter defines the application which interfaces with the
serial communications functions.</td>
<td></td>
</tr>
<tr class="even">
<td><strong>StaMdSysCovOsAppRef</strong></td>
<td>This parameter defines the application which performs the states and
modes systematic coverage.</td>
<td></td>
</tr>
</tbody>
</table>

### DaVinci Interrupt Configuration Changes

| **ISR Name** | **VIM \#** | **Priority Dependency** | **Notes** |
|--------------|------------|-------------------------|-----------|
| **\<None\>** |            |                         |           |

### Manual Configuration Changes

| **Constant** | **Notes** | **SWC** |
|--------------|-----------|---------|
| **\<None\>** |           |         |

# Integration

## Required Global Data Inputs

## Required Global Data Outputs

## Specific Include Path present

The **…StaMd/include** patch needs to be added to the include search
path of the CCS project. Typical setting:
**"\${workspace_loc:/FORD_S550_P552/StaMd/include}"**

# Runnable Scheduling 

This section specifies the required runnable scheduling.

| **Init** | **Scheduling Requirements** | **Trigger** |
|----------|-----------------------------|-------------|
| None     | None                        | Init        |

| **Runnable** | **Scheduling Requirements** | **Trigger** |
|--------------|-----------------------------|-------------|
|              |                             | 10ms        |

**.**

# Memory Mapping

## Mapping

<table>
<colgroup>
<col style="width: 66%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Memory Section</strong></th>
<th><strong>Contents</strong></th>
<th><strong>Notes</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>STAMD_START_SEC_VAR_SAVED_ZONEHGS_32</p>
<p>STAMD_START_SEC_VAR_SAVED_ZONEHGS_8</p></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

| **Feature**                | **RAM** | **ROM** |
|----------------------------|---------|---------|
| **\<Memmap usuage info\>** |         |         |

Table 1: ARM Cortex R4 Memory Usage

## Non RTE NvM Blocks

| **Block Name** |
|----------------|
| **\<None \>**  |

Note : Size of the NVM block if configured in developer

##  RTE NvM Blocks

| **Block Name** |
|----------------|
| None           |

Note : Size of the NVM block if configured in developer

# Compiler Settings

##  Preprocessor MACRO

\<Define all the preprocessor Macros needed and conditions when
needed\>.

## Optimization Settings

\<Define Optimization levels that are needed and conditions when
needed\>.

##  [section-1]

# Revision Control Log

|            |                                                                        |           |            |
|-------|--------------------------------------------------|----------|-------|
| **Rev \#** | **Change Description**                                                 | **Date**  | **Author** |
| 1          | Initial version                                                        | 12-Dec-13 | BDO        |
| 2          | Updated to FDD ES10B version 13 to address anomaly 5388. CR11347       | 07-Feb-14 | BDO        |
| 3          | Anomaly 7307 - updates for consistency with FDD ES10B version 13 12602 | 28-Oct-14 | BDO        |

{% endraw %}