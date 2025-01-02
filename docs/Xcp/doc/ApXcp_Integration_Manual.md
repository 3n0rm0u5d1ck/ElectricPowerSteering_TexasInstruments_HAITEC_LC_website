---
layout: default
title: ApXcp_Integration_Manual
nav_order: 1
parent: Xcp
---
{% raw %}
[1 Dependencies [2](#dependencies)](#dependencies)

[1.1 SWCs [2](#_Toc357692819)](#_Toc357692819)

[1.2 Functions to be provided to Integration Project
[2](#_Toc357692820)](#_Toc357692820)

[2 Configuration
[3](#getsetindexes-and-getpersindexes)](#getsetindexes-and-getpersindexes)

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

## GetSetIndexes() and GetPersIndexes()

### Overview

The integration specific functions below, GetSetIndexes and
GetPersIndexes, are used to return an array of tuning identifiers to the
tune-on-the-fly (or online calibration as defined in the XCP specs)
function. They are used to copy the active sets or personalities into
RAM. The functions should be implemented in an integration specific
component that determines the desired personality and desired set
identifiers sent to tuning select authority SWC.

If tune-on-the-fly functionality is disabled, the functions below do not
need to be defined.

If tune-on-the-fly is enabled and the lookup functions are disabled, the
functions below do not need to be defined. When a copy cal page XCP
command is called, the personalities are copied from 0 to a max limit
based on the active tuning set that is currently being used. In the case
of the tuning sets being copied, only the active tuning set is copied in
to the RAM.

| **Module**                          | **Required API**                |
|-------------------------------------|---------------------------------|
| **\<Integration Specific Module\>** | Function outline defined below: |

### Function Prototypes

The actual implementation of the function will vary between programs.
However, the function should be structured so the passed arguments are
of the same time to provide a common interface to the XCP functions.

<table>
<colgroup>
<col style="width: 26%" />
<col style="width: 35%" />
<col style="width: 8%" />
<col style="width: 5%" />
<col style="width: 7%" />
<col style="width: 7%" />
<col style="width: 7%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Function Name</strong></td>
<td>GetSetIndexes or GetPersndexes</td>
<td>Type</td>
<td>Dir.</td>
<td>Min</td>
<td>Max</td>
<td>UTP Tol.</td>
</tr>
<tr class="even">
<td><strong>Arguments Passed</strong></td>
<td>NumOfSets_Cnt_T_u8<br />
or<br />
NumOfPers_Cnt_T_u8</td>
<td>uint8</td>
<td>I</td>
<td>0</td>
<td>255</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>data</td>
<td>uint8*</td>
<td>I/O</td>
<td>0</td>
<td>255</td>
<td></td>
</tr>
<tr class="even">
<td><strong>Return Value</strong></td>
<td>N/A</td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

### Example 1 -- BMW

The following example illustrates a similar situation found in the BMW
program. Active personalities are determined by coding bits. Using the
GetPersIndexes function, the function will loop through the
personalities to find the index of the personality that contains the
matching coding ID. The indexes are returned and the active
personalities are copied into RAM.

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/Xcp/doc/mediax/media/image1.emf)

## ProcessXCPPID()

### Overview

This function must be available to this module to call by the
integration manual. This should be provided by the CMS component which
does the processing on XCP PIDs. This function is required to allow the
CMS component to figure out when an XCP PID is finished being read or
written.

| **Module**     | **Required API**                |
|----------------|---------------------------------|
| **CMS Common** | Function outline defined below: |

### Function Prototypes

|                      |                |       |      |     |     |          |
|----------------------|----------------|-------|------|-----|-----|----------|
| **Function Name**    | ProcessXCPPID  | Type  | Dir. | Min | Max | UTP Tol. |
| **Arguments Passed** | Size_Cnt_T_u08 | uint8 | I    | 1   | 8   |          |
| **Return Value**     | N/A            |       |      |     |     |          |

# Configuration

## Build Time Config

| Modules | Notes |     |
|---------|-------|-----|
| None    |       |     |

## Configuration Files to be provided by Integration Project

### Da Vinci Parameter Configuration Changes

<table>
<colgroup>
<col style="width: 45%" />
<col style="width: 43%" />
<col style="width: 11%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Notes</th>
<th>SWC</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>D_NUMOFVLDEEMEMRGNS_CNT_U08</td>
<td>Generated in Ap_ApXcp.Cfg.h if external EEPROM access is set to
STD_ON in Configurator. Value will be determined by the EEPROM memory
access defined in the ECUC file.</td>
<td>ApXcp</td>
</tr>
<tr class="even">
<td>BC_XCP_EXTEEPACCESS</td>
<td>Set to STD_ON in Configurator if XCP access to external EEPROM is
required.</td>
<td>ApXcp</td>
</tr>
<tr class="odd">
<td>BC_XCP_TUNEONFLY</td>
<td>Set to STD_ON in Configuartor if tune-on-the-fly support is
required.</td>
<td>ApXcp</td>
</tr>
<tr class="even">
<td>BC_XCP_PERSINDEXLOOKUP</td>
<td>Set to STD_ON in Configurator if a function call to GetPersIndexes
is required to return the indexes of active personalities. Note:
BC_XCP_TUNEONFLY must be set to STD_ON</td>
<td>ApXcp</td>
</tr>
<tr class="odd">
<td>BC_XCP_SETINDEXLOOKUP</td>
<td>Set to STD_ON in Configurator if a function call to GetSetIndexes is
required to return the indexes of active sets. Note: BC_XCP_TUNEONFLY
must be set to STD_ON</td>
<td>ApXcp</td>
</tr>
<tr class="even">
<td>&lt;Non Trusted Function Stack Size&gt;</td>
<td>This needs to be configured (to a non-zero value) for the task or
ISR that handles the XCP commands. This is required to support
application switching for XCP writes. Please note this is only required
if a program has non-trusted applications configured.</td>
<td>Os</td>
</tr>
<tr class="odd">
<td>&lt;Trusted/Non Trusted functions for XCP writes&gt;</td>
<td><p>If a program has multiple applications configured, non-trusted or
trusted functions must be configured for each application. This is
required to allow the XCP write commands to switch context before
performing the write. These functions should end up calling
ApXcpWriteCommon() to perform the write.</p>
<p>Ex:</p>
<p>NtWrapS_XcpWriteAp8()</p>
<p>NtWrapS_XcpWriteAp9()</p>
<p>TWrapS_XcpWriteAp0</p></td>
<td>Os</td>
</tr>
<tr class="even">
<td>BC_XCP_TOTFRAMSIZE_UNT_32</td>
<td>This should be set to the same size as the amount of RAM allocated
to TOTF. Also used as the size of the buffer if Segment16 is
enabled.</td>
<td>ApXcp</td>
</tr>
<tr class="odd">
<td>BC_XCP_SEG[x]ENABLE</td>
<td>This should be set to STD_ON to enable the number segment, where [x]
= Segment number.</td>
<td>ApXcp</td>
</tr>
<tr class="even">
<td>BC_XCP_MAXPERCOPY_CNT_U8</td>
<td>Used with segment 0, the number represents the number of tuning
personalities to copy into RAM. Must be set to at least 1.</td>
<td>ApXcp</td>
</tr>
<tr class="odd">
<td>CalConstNumOfPerSymbol</td>
<td>Set to the number of tuning personalties constant. Typically this is
defined in CalConstants.h with the name D_NUMOFPERS_CNT_U16.</td>
<td>ApXcp</td>
</tr>
<tr class="even">
<td>BC_XCP_MAXSETCOPY_CNT_U8</td>
<td>Used with segment 1, the number represents the number of tuning sets
to copy into RAM. Must be set to at least 1.</td>
<td>ApXcp</td>
</tr>
<tr class="odd">
<td>CalConstNumOfSetSymbol</td>
<td>Set to the number of tuning sets constant. Typically this is defined
in CalConstants.h with the name D_NUMOFTUNSETS_CNT_U16.</td>
<td>ApAcp</td>
</tr>
<tr class="even">
<td>BC_XCP_SEG16LNKSYMB</td>
<td>Used with segment 16. The linker symbol represents the start address
of the custom memory range to copy into RAM.</td>
<td>ApXcp</td>
</tr>
<tr class="odd">
<td>BC_XCP_SEG16LNKSYMBLEN_CNT_U8</td>
<td>Used with segment 16. The linker symbol represents the size of the
custom memory range to copy into RAM.</td>
<td>ApXcp</td>
</tr>
</tbody>
</table>

### DaVinci Interrupt Configuration Changes

| ISR Name | VIM \# | Priority Dependency | Notes |
|----------|--------|---------------------|-------|
|          |        |                     |       |

### Manual Configuration Changes

| Constant | Notes | SWC |
|----------|-------|-----|
|          |       |     |

### GENy Configuration Changes

<table>
<colgroup>
<col style="width: 39%" />
<col style="width: 46%" />
<col style="width: 14%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Notes</th>
<th>SWC</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>User configuration file</td>
<td><p>ApXcp component functionality relies on a callout function for
XCP memory writing from the XCP module as delivered by vector. To enable
this callout function, a user configuration file typically needs to be
included in the GENy configuration to enable the appropriate build
constant. See attached file below</p>
<p><img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/Xcp/doc/mediax/media/image2.wmf" /></p></td>
<td>GENy XCP configuration</td>
</tr>
<tr class="even">
<td>General Settings-&gt;Enable Calibration</td>
<td>This should be enabled to allow download commands</td>
<td>GENy XCP configuration</td>
</tr>
<tr class="odd">
<td>General Settings-&gt;Memory Write Protection</td>
<td>This should be enabled to allow checking of XCP access on the
addresses requested for writing.</td>
<td>GENy XCP configuration</td>
</tr>
<tr class="even">
<td>General Settings-&gt;Memory Read Protection</td>
<td>This should be enabled to allow checking of XCP access on the
addresses requested for reading.</td>
<td>GENy XCP configuration</td>
</tr>
<tr class="odd">
<td>EEPROM Access-&gt;Read Access</td>
<td>This needs to be enabled if external EEPROM is available and needs
to be read through XCP</td>
<td>GENy XCP configuration</td>
</tr>
<tr class="even">
<td>EEPROM Access-&gt;Write Access</td>
<td>This needs to be enabled if external EEPROM is available and needs
to be written through XCP</td>
<td>GENy XCP configuration</td>
</tr>
<tr class="odd">
<td>Standard Commands-&gt;User Defined Command</td>
<td>This needs to be enabled for CMS XCP support</td>
<td>GENy XCP configuration</td>
</tr>
<tr class="even">
<td>Block Transfer-&gt;Block Upload</td>
<td>Needs to be enabled to support large XCP PID reads</td>
<td>GENy XCP configuration</td>
</tr>
<tr class="odd">
<td>Block Transfer-&gt;Block Download</td>
<td>Needs to be enabled to support large XCP PID writes</td>
<td>GENy XCP configuration</td>
</tr>
<tr class="even">
<td>Page Switching-&gt;Page Switching</td>
<td>Needs to be enabled only if Tune On the Fly Support is turned
on</td>
<td>GENy XCP configuration</td>
</tr>
<tr class="odd">
<td>Page Switching-&gt;General Paging Info</td>
<td>Needs to be enabled only if Tune On the Fly Support is turned
on</td>
<td>GENy XCP configuration</td>
</tr>
<tr class="even">
<td>Page Switching-&gt;Copy Page</td>
<td>Needs to be enabled only if Tune On the Fly Support is turned
on</td>
<td>GENy XCP configuration</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

# Integration

## Required Global Data Inputs

\<Mention any global variable that this component requires for other
components\>

## Required Global Data Outputs

\<Mention any global variable that this component requires for other
components\>

## Specific Include Path present

Yes

# Runnable Scheduling 

This section specifies the required runnable scheduling.

| Init       | Scheduling Requirements                                                     | Trigger      |
|------------------|--------------------------------------|----------------|
| ApXcp_Init | Should be called prior to the start of the O/S (typically EcuStartup_Init1) | Once At Init |

| Runnable   | Scheduling Requirements                                                                                                                                    | Trigger    |
|-------------------|---------------------------------------|---------------|
| ApXcp_Per1 | None                                                                                                                                                       | RTE (10ms) |
| DAQ_2msTL  |                                                                                                                                                            | RTE (2ms)  |
| DAQ_1msTL  | This function should only be scheduled if 1ms DAQ support is required. If not, it needs to be deleted from the integration project in the ApXcp Component. | RTE (1ms)  |

**.**

# Memory Mapping

## Mapping

| Memory Section           | Contents | Notes |
|--------------------------|----------|-------|
| \< Memory mapping Info\> |          |       |
|                          |          |       |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

| Feature                | RAM | ROM |
|------------------------|-----|-----|
| \<Memmap usuage info\> |     |     |

Table 1: ARM Cortex R4 Memory Usage

## Non RTE NvM Blocks

| Block Name                            |
|---------------------------------------|
| \<NVM block used Non RTE functions \> |

Note : Size of the NVM block if configured in developer

##  RTE NvM Blocks

| Block Name                           |
|--------------------------------------|
| \<NVM block used in RTE functions \> |

Note : Size of the NVM block if configured in developer

# Compiler Settings

##  Preprocessor MACRO

\<Define all the preprocessor Macros needed and conditions when
needed\>.

## Optimization Settings

\<Define Optimization levels that are needed and conditions when
needed\>.

##  [section]

# Revision Control Log

|            |                                                                               |            |            |
|-------|--------------------------------------------------|----------|-------|
| **Rev \#** | **Change Description**                                                        | **Date**   | **Author** |
| 1          | Initial version                                                               | 30-July-13 | KJS        |
| 2          | Updates for better description of configuration requirements                  | 29-Aug-13  | LWW        |
| 3          | Added updates for new configuration constants generated with tune on the fly. | 10-Oct-13  | KJS        |

{% endraw %}