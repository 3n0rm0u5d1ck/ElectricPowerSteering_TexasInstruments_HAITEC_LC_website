---
layout: default
title: NvMProxy_Integration_Manual
nav_order: 2
parent: Nvm Proxy
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
<th>Module</th>
<th>Required Feature</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>NvM</td>
<td><p>NvM_WriteBlock()</p>
<p>NvM_GetBlockStatus()</p></td>
</tr>
<tr class="even">
<td>DiagMgr</td>
<td>NxtrDiagMgr#_ReportNTCStatus()</td>
</tr>
<tr class="odd">
<td>Crc</td>
<td>Crc_CalculateCRC16()</td>
</tr>
</tbody>
</table>

## Global Functions(Non RTE) to be provided to Integration Project

NvMProxy_Init

NvMProxy_MainFunction

NvMProxy_WriteBlock

NvMProxy_WriteAll

NvMProxy_GetErrorStatus

NvMProxy_SetRamBlockStatus

# Configuration

## Build Time Config

| Modules | Notes |     |
|---------|-------|-----|
| None    |       |     |

## Configuration Files to be provided by Integration Project

### Da Vinci Parameter Configuration Changes

<table>
<colgroup>
<col style="width: 29%" />
<col style="width: 55%" />
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
<td><em>NvMProxyConfigSet/NvMProxyBlock/</em>NvmRamBlockDataAddressSecure</td>
<td><p>The symbol name of the secured buffer location for the block
data</p>
<p>NOTE: For blocks defined by PIM memory in the Rte, this parameter is
the symbol name that Developer inserts into the NvM Ram block
configuration parameter for the associated NvM block)</p></td>
<td>NvMProxy</td>
</tr>
<tr class="even">
<td><em>NvMProxyConfigSet/NvMProxyBlock/</em>InitBlockHandling</td>
<td><p>This parameter chooses the type of protection handling done on
the block at initialization:</p>
<p><strong>None:</strong> No specific handling needed</p>
<p><strong>CRC16:</strong> Run a 16 bit CRC on the NvM block and check
it against the CRC stored in the NvM block (last two bytes). Failures
will trigger the fail action specified in the “InitCheckFailResponse”
configuration</p>
<p><strong>Redundant:</strong> Run redundant storage check on the NvM
block. The 1’s compliment of the block data is stored in the NvM block
to protect against corruption. Failures will trigger the fail action
specified in the “InitCheckFailResponse” configuration</p>
<p><strong>ZeroData:</strong> Ignore what is stored in NvM and always
over-ride the NvM RAM buffer with zeros. This is useful for blocks that
may be un</p></td>
<td>NvMProxy</td>
</tr>
<tr class="odd">
<td><em>NvMProxyConfigSet/NvMProxyBlock/</em>InitCheckFailResponse</td>
<td><p>Defines the type of response to occur if the NvM block fails
either the CRC16 or Redundant check at initialization:</p>
<p><strong>N/A:</strong> This should be chosen if the block doesn’t have
CRC16 or Redundant InitBlockHandling turned on</p>
<p><strong>SetNTC_0x0A:</strong> This should be chosen to set NTC 0x0A
(should be calibrated to a critical shutdown fault- F1)</p>
<p><strong>SetNTC_0x08_LoadROMDefaults:</strong> This should be chosen
to set NTC 0x08 (should be calibrated to be a non-shutdown fault (F3)
and mapped to a CTC that lights lamp). Also, default values will be
loaded from FLASH memory at the symbolic location specified in the
“ROMDefault_Or_NotificationFunction_Symbol” configuration parameter.</p>
<p><strong>SetNTC_0x08_CallNotificationFunction:</strong> This should be
chosen to set NTC 0x08 (should be calibrated to be a non-shutdown fault
(F3) and mapped to a CTC that lights lamp). Also, a user defined
function will be called. The function name is to be specified in the the
“ROMDefault_Or_NotificationFunction_Symbol” configuration parameter.</p>
<p><strong>SetNTC_0x07_LoadROMDefaults:</strong> This should be chosen
to set NTC 0x07 (should be calibrated to be a non-shutdown fault (F3)
and mapped to a CTC that does not light lamp). Also, default values will
be loaded from FLASH memory at the symbolic location specified in the
“ROMDefault_Or_NotificationFunction_Symbol” configuration parameter.</p>
<p><strong>SetNTC_0x07_CallNotificationFunction:</strong> This should be
chosen to set NTC 0x07 (should be calibrated to be a non-shutdown fault
(F3) and mapped to a CTC that does not light lamp). Also, a user defined
function will be called. The function name is to be specified in the the
“ROMDefault_Or_NotificationFunction_Symbol” configuration parameter.</p>
<p><strong>SetNTC_0x06_LoadROMDefaults:</strong> This should be chosen
to set NTC 0x06 (should be calibrated to be a non-shutdown fault (F3)
and not mapped to a CTC). Also, default values will be loaded from FLASH
memory at the symbolic location specified in the
“ROMDefault_Or_NotificationFunction_Symbol” configuration parameter.</p>
<p><strong>SetNTC_0x06_CallNotificationFunction:</strong> This should be
chosen to set NTC 0x06 (should be calibrated to be a non-shutdown fault
(F3) and not mapped to a CTC). Also, a user defined function will be
called. The function name is to be specified in the the
“ROMDefault_Or_NotificationFunction_Symbol” configuration
parameter.</p></td>
<td>NvMProxy</td>
</tr>
<tr class="even">
<td><em>NvMProxyConfigSet/NvMProxyBlock/</em>ROMDefault_Or_NotificationFunction_Symbol</td>
<td><p>This parameter defines the symbolic name of the FLASH constant
that contains the default values to load into NvM RAM if the block fails
its CRC16 or Redundant check at initialization in the case of the
“InitCheckFailResponse” parameter being either
“SetNTC_0x08_LoadROMDefaults”, “SetNTC_0x07_LoadROMDefaults” or
“SetNTC_0x06_LoadROMDefaults”. It defines the symbolic name of the
notification function in the case of the “InitCheckFailResponse”
parameter being either “SetNTC_0x08_CallNotificationFunction”,
“SetNTC_0x07_CallNotificationFunction” or
“SetNTC_0x06_CallNotificationFunction”.</p>
<p>This parameter should be set to “NULL_PTR” if CRC16 or Redundant
block initialization handling is not turned on.</p></td>
<td>NvMProxy</td>
</tr>
<tr class="odd">
<td><em>NvMProxyConfigSet/NvMProxyBlock/</em>NvMRamGlobalShared</td>
<td>Set to “True” if the NvM block’s RAM is already in “Global Shared”
memory. This avoids creating another buffer. This is typically the case
for “TypeH” blocks and the EEPROM close check block.</td>
<td>NvMProxy</td>
</tr>
<tr class="even">
<td><em>NvMProxyConfigSet/NvMProxyBlock/</em>NvMBlockDescriptorRef</td>
<td>Reference to the NvMBlockDescriptor container that defines the NvM
block linked to this proxy configuration.</td>
<td>NvMProxy</td>
</tr>
<tr class="odd">
<td><em>NvMProxyGeneral/</em> NvMProxyIncludes</td>
<td>This contains a list of project specific include files that need to
be compiled into the NvMProxy</td>
<td>NvMProxy</td>
</tr>
<tr class="even">
<td><em>NvMProxyGeneral/</em> FailureAPI</td>
<td>This should be set to the diagnostic manager’s API for setting
faults. This should be set to the “ReportNTCStatus” API since it is
called during initialization. It is configurable because the API depends
on the application number. Typically this should be set to
“NxtrDiagMgr10_ReportNTCStatus” (assuming Ap 10 is the ASILD
application)</td>
<td>NvMProxy</td>
</tr>
<tr class="odd">
<td><em>DiagMgrConfigSet/DiagMgrEventParameter</em></td>
<td>This module needs four DiagMgr NTCs added to the configuration: NTC
0x0A, NTC 0x08, NTC 0x07, and NTC 0x06. These need to be configured as
“DIAGMGR_EVENT_KIND_BSW”</td>
<td>DiagMgr</td>
</tr>
</tbody>
</table>

### DaVinci Interrupt Configuration Changes

| ISR Name | VIM \# | Priority Dependency | Notes |
|----------|--------|---------------------|-------|
| N/A      |        |                     |       |

### Manual Configuration Changes

| Constant                  | Notes                                                                                                                                                                                                                                                                                           | SWC  |
|-----------------------------|----------------------------------|----------|
| NVMPROXY_EXCLUSIVE_AREA_0 | This exclusive are covers the areas of execution within the component that are operating on the request buffer. The buffer is operated on by the MainFunction and the WriteBlock functions. An appropriate level of protection must be employed to maintain exclusive usage of the buffer data. | SchM |

# Integration

The following import steps must be completed :

1.  Place CBD project structure to appropriate integration folder

2.  Execute the “Integrate.bat” script from the Tools directory of this
    component to perform the necessary integration steps:

    1.  The script creates the required directories in the integration
        project, “Generators/Artt/NvMProxy” and
        “Generators/Components/\_Schemes/NvMProxy/bswmd”

    2.  The script then copies the required files from the CBD generate
        directory into the new directories.

3.  If this is the first time integration, then perform the Davinci
    Configurator 3rd party component integration procedure.

4.  Configure NvM proxy component per program needs

5.  Generate NvM proxy and import generated Cd_NvMProxy_swc.arxml into
    davinci developer and map all NvM service needs on the blocks
    needing proxies to the NvM Proxy service component (instead of the
    NvM service component)

**SPECIAL INTEGRATION NOTES:**

NvM Block Sizes

> If CRC16 protection is chosen on a block, the NvM configuration needs
> to be increased by “2” to hold the CRC. The CRC value will be stored
> in the last two bytes of the data block.
>
> Similarly, if Redundant protection is chosen on a block, the NvM
> configuration needs to be doubled to hold the redundant data.
>
> Because of compiler alignment restrictions, it is HIGHLY recommended
> to use the debugger in Code Composer to analyze the compiled size of
> the NvM block. This can be done by using the
> sizeof(\<NvMRamShadowName\>) in the expressions window. The resulting
> size shown should get the added “2” or doubling in the NvM
> Configuration.

NvM Configuration

> The NvM configuration parameter “NvMRamBlockDataAddress” configuration
> for all blocks using the NvM proxy need to have “NvMP\_” pre-pended to
> the normal name of the RAM shadow symbol. **Please note that if the
> block is linked through Davinci Developer Per-Instance Memory Mapping,
> this name will automatically revert back (remove the** **“NvMP\_”)**
> **every time the Davinci Developer project is saved** **and the block
> size may be reverted to the original size (without the added CRC size
> or doubling for redundant store).**

ROM Defaults and Notification Functions

> If “ROM defaults” or “Notification Functions” are configured via the
> “InitCheckFailResponse” parameter, it is up to the integration project
> to provide the ROM default data or the notification function named per
> the “ROMDefault_Or_NotificationFunction_Symbol” parameter. The ROM
> default option will use a blind memory copy, so it is important that
> the same NvM RAM Shadow datatype is used for ROM constant to ensure
> proper data alignment.

## Required Global Data Inputs

N/A

## Required Global Data Outputs

N/A

## Specific Include Path present

Yes

# Runnable Scheduling 

This section specifies the required runnable scheduling.

| Init            | Scheduling Requirements                                                                                                             | Trigger |
|-------------------|---------------------------------------|---------------|
| NvMProxy_Init() | Must be executed after NvM driver has initialized the unsecured block data to be forwarded to the secured memory by this component. | Init    |

| Runnable                | Scheduling Requirements                                              | Trigger                  |
|----------------------|-----------------------------------|----------------|
| NvMProxy_MainFunction() | Run prior to NvM_MainFunction for minimal request processing latency | Same as NvM_MainFunction |

**.**

# Memory Mapping

## Mapping

<table>
<colgroup>
<col style="width: 64%" />
<col style="width: 16%" />
<col style="width: 18%" />
</colgroup>
<thead>
<tr class="header">
<th>Memory Section</th>
<th>Contents</th>
<th>Notes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>NVMPROXY_START_SEC_VAR_NOINIT_8</td>
<td></td>
<td><p>Typically allocated to application in which NvM driver
resides.</p>
<p>Not required to be allocated to Global shared memeory.</p></td>
</tr>
<tr class="even">
<td>NVMPROXY_START_SEC_VAR_CLEARED_16</td>
<td></td>
<td>Must be allocated into Global Shared memory</td>
</tr>
<tr class="odd">
<td>NVMPROXY_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
<td></td>
<td>Must be allocated into Global Shared memory</td>
</tr>
<tr class="even">
<td>NVMPROXY_START_SEC_CODE</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>NVMPROXY_START_SEC_CONST_UNSPECIFIED</td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

| Feature | RAM | ROM |
|---------|-----|-----|
|         |     |     |

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

|            |                                                |          |            |
|-------|--------------------------------------------------|----------|-------|
| **Rev \#** | **Change Description**                         | **Date** | **Author** |
| 1          | Initial version                                |          | JJW        |
| 2          | Updates per generation definition              | 10/18/12 | JJW        |
| 3          | Updates for CRC and Redundant checking feature | 12/02/13 | LWW        |

{% endraw %}