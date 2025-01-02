---
layout: default
title: PWMCdd_Integration_Manual
nav_order: 4
parent: Component
---
{% raw %}
[1 Dependencies [2](#dependencies)](#dependencies)

[1.1 SWCs [2](#swcs)](#swcs)

[1.2 Global Functions(Non RTE) to be provided to Integration Project
[2](#global-functionsnon-rte-to-be-provided-to-integration-project)](#global-functionsnon-rte-to-be-provided-to-integration-project)

[2 Configuration [3](#configuration)](#configuration)

[2.1 Build Time Config [3](#build-time-config)](#build-time-config)

[2.2 Configuration Files to be provided by Integration Project
[3](#configuration-files-to-be-provided-by-integration-project)](#configuration-files-to-be-provided-by-integration-project)

[2.2.1 Da Vinci Parameter Configuration Changes
[3](#da-vinci-parameter-configuration-changes)](#da-vinci-parameter-configuration-changes)

[2.2.2 DaVinci Interrupt Configuration Changes
[3](#davinci-interrupt-configuration-changes)](#davinci-interrupt-configuration-changes)

[2.2.3 Manual Configuration Changes
[3](#manual-configuration-changes)](#manual-configuration-changes)

[3 Integration [4](#integration)](#integration)

[3.1 Required Global Data Inputs
[4](#required-global-data-inputs)](#required-global-data-inputs)

[3.2 Required Global Data Outputs
[4](#required-global-data-outputs)](#required-global-data-outputs)

[3.3 Specific Include Path present
[4](#specific-include-path-present)](#specific-include-path-present)

[4 Runnable Scheduling [5](#runnable-scheduling)](#runnable-scheduling)

[5 Memory Mapping [6](#memory-mapping)](#memory-mapping)

[5.1 Mapping [6](#mapping)](#mapping)

[5.2 Usage [6](#usage)](#usage)

[5.3 Non RTE NvM Blocks [6](#non-rte-nvm-blocks)](#non-rte-nvm-blocks)

[5.4 RTE NvM Blocks [6](#rte-nvm-blocks)](#rte-nvm-blocks)

[6 Compiler Settings [6](#compiler-settings)](#compiler-settings)

[6.1 Preprocessor MACRO [6](#preprocessor-macro)](#preprocessor-macro)

[6.2 Optimization Settings
[6](#optimization-settings)](#optimization-settings)

[7 Revision Control Log
[7](#revision-control-log)](#revision-control-log)

# Dependencies

## SWCs

| Module   | Required Feature                                      |
|----------|-------------------------------------------------------|
| CDD_Data | Global variables for DC Phs Comp (for using in Nhet/) |

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
referred. Developer should track the references.

## Global Functions(Non RTE) to be provided to Integration Project

CDDPorts_ClearPhsReasSum(uint16 DataAccessBfr_Cnt_T_u16)

CDD_ApplyPWMMtrElecMechPol(sint8 MtrElecMechPol_Cnt_s8)

# Configuration

## Build Time Config

| Modules | Notes |     |
|---------|-------|-----|
| None    |       |     |

## Configuration Files to be provided by Integration Project

##  [section]

\<Configuration file that will generated from this components that will
require Da Vinci Config generation or manual generation. Describe each
parameter \>

### Da Vinci Parameter Configuration Changes

| Parameter | Notes | SWC |
|-----------|-------|-----|
| None      |       |     |

### DaVinci Interrupt Configuration Changes

| ISR Name | VIM \# | Priority Dependency | Notes |
|----------|--------|---------------------|-------|
| None     |        |                     |       |

### Manual Configuration Changes

<table>
<colgroup>
<col style="width: 39%" />
<col style="width: 47%" />
<col style="width: 12%" />
</colgroup>
<thead>
<tr class="header">
<th>Constant</th>
<th>Notes</th>
<th>SWC</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>d_PwmFreq_Hz_Cnt_u16</p>
<p>d_PWMFreqDither_Hz_u16</p></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

# Integration

## Required Global Data Inputs

The following global symbols must be defined in CDD_Data.c and .h
(populated by PwmCdd):

-   uint16: CDD_DCPhsComp_Cnt_G_u16\[3\]

-   uint16: CDD_PWMPeriod_Cnt_G_u16

**NHET/EPWM** version corresponding PWMCdd component spilt and using
global variables CDD_DCPhsComp_Cnt_G_u16 and CDD_PWMPeriod_Cnt_G_u16
should be used.

-   CDD_Read_PhaseAdvanceFinal_Rev_u0p16

-   CDD_Read_CorrectedMtrPos_Rev_u0p16

-   CDD_Read_CommOffset_Cnt_u16

## Required Global Data Outputs

-   CDD_Write_DCPhsBComp_Cnt_u16p0

-   CDD_Write_DCPhsCComp_Cnt_u16p0

## Specific Include Path present

Yes - The “include” directory of this SWC needs to be included in the
integration project include search path.

# Runnable Scheduling 

This section specifies the required runnable scheduling.

| Init        | Scheduling Requirements |                                                              | Trigger |     |
|------------------|-------|-------------------------------|--|---------------|
| PwmCdd_Init |                         | Place in EcuStartup. Execute along with NHET initialization. |         | ISR |

| Runnable    | Scheduling Requirements                                                                                                  | Trigger         |
|-------------------|--------------------------------------|----------------|
| PwmCdd_Per1 | Must be placed in the motor control ISR, before Nhet (or whichever function populates the global variables used byNhet). | Cyclic (ISR) \* |

**.**

# Memory Mapping

## Mapping

| Memory Section                  | Contents             | Notes |
|---------------------------------|----------------------|-------|
| PWMCDD_START_SEC_VAR_CLEARED_16 | Variable Definitions |       |
|                                 |                      |       |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

| Feature     | RAM | ROM |
|-------------|-----|-----|
| Full driver |     |     |

Table 1: ARM Cortex R4 Memory Usage

## Non RTE NvM Blocks

| Block Name |
|------------|
| None       |

Note : Size of the NVM block if configured in developer

##  RTE NvM Blocks

| Block Name |
|------------|
| None       |

Note : Size of the NVM block if configured in developer

# Compiler Settings

##  Preprocessor MACRO

None

## Optimization Settings

None

##  [section-1]

# Revision Control Log

|            |                                                                           |           |            |
|-------|----------------------------------------------|------------|--------|
| **Rev \#** | **Change Description**                                                    | **Date**  | **Author** |
| 1          | Initial version                                                           | 14-Feb-13 | Selva      |
| 2          | Added cal k_PWMBaseFrequency_Hz to replace constant d_PWMFreqBase_Hz_u16. | 21-Jan-14 | LK         |

{% endraw %}