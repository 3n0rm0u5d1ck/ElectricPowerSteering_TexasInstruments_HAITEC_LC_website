---
layout: default
title: SVDiag_Integration_Manual
nav_order: 5
parent: Component
---
{% raw %}
**Integration Manual**

**For**

**Sine Voltage Generation Diagnostics (ES-49)**

**VERSION: 2**

**DATE: 02-12-2014**

**Prepared By:**

**Rijvi Ahmed,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**  
Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                                                   |            |             |             |
|-----|--------------------|--------------------|---------|--------------------|
| **Sl. No.** | **Description**                                   | **Author** | **Version** | **Date**    |
| 1           | Initial version                                   | VT         | 1           | 03-Oct-2013 |
| 2           | Updated for FDD rev.008 and updated the template. | Rijvi      | 2           | 01-Dec-2014 |

**<u>  
Table of Contents</u>**

[1 Abbrevations And Acronyms
[4](#abbrevations-and-acronyms)](#abbrevations-and-acronyms)

[2 References [5](#references)](#references)

[3 Dependencies [6](#dependencies)](#dependencies)

[3.1 SWCs [6](#swcs)](#swcs)

[3.2 Global Functions(Non RTE) to be provided to Integration Project
[6](#global-functionsnon-rte-to-be-provided-to-integration-project)](#global-functionsnon-rte-to-be-provided-to-integration-project)

[4 Configuration REQUIREMeNTS
[7](#configuration-requirements)](#configuration-requirements)

[4.1 Build Time Config [7](#build-time-config)](#build-time-config)

[4.2 Configuration Files to be provided by Integration Project
[7](#configuration-files-to-be-provided-by-integration-project)](#configuration-files-to-be-provided-by-integration-project)

[4.3 Da Vinci Parameter Configuration Changes
[7](#da-vinci-parameter-configuration-changes)](#da-vinci-parameter-configuration-changes)

[4.4 DaVinci Interrupt Configuration Changes
[7](#davinci-interrupt-configuration-changes)](#davinci-interrupt-configuration-changes)

[4.5 Manual Configuration Changes
[7](#manual-configuration-changes)](#manual-configuration-changes)

[5 Integration DATAFLOW REQUIREMENTS
[8](#integration-dataflow-requirements)](#integration-dataflow-requirements)

[5.1 Required Global Data Inputs
[8](#required-global-data-inputs)](#required-global-data-inputs)

[5.2 Required Global Data Outputs
[8](#required-global-data-outputs)](#required-global-data-outputs)

[5.3 Specific Include Path present
[8](#specific-include-path-present)](#specific-include-path-present)

[6 Runnable Scheduling [9](#runnable-scheduling)](#runnable-scheduling)

[7 Memory Map REQUIREMENTS
[10](#memory-map-requirements)](#memory-map-requirements)

[7.1 Mapping [10](#mapping)](#mapping)

[7.2 Usage [10](#usage)](#usage)

[7.3 Non RTE NvM Blocks [10](#non-rte-nvm-blocks)](#non-rte-nvm-blocks)

[7.4 RTE NvM Blocks [10](#rte-nvm-blocks)](#rte-nvm-blocks)

[8 Compiler Settings [11](#compiler-settings)](#compiler-settings)

[8.1 Preprocessor MACRO [11](#preprocessor-macro)](#preprocessor-macro)

[8.2 Optimization Settings
[11](#optimization-settings)](#optimization-settings)

[9 Appendix [12](#appendix)](#appendix)

# Abbrevations And Acronyms

| **Abbreviation** | **Description**           |
|------------------|---------------------------|
| DFD              | Design functional diagram |
| MDD              | Module design Document    |

# References

This section lists the title & version of all the documents that are
referred for development of this document

| **Sr. No.** | **Title**                                              | **Version** |
|----------|----------------------------------------------|-----------------|
| 1           | FDD ES-49. Sine Voltage Generation Diagnostics - EA3.x | 008         |

# Dependencies

## SWCs

| **Module** | **Required Feature** |
|------------|----------------------|
| None       | None                 |

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
referred. Developer should track the references.

## Global Functions(Non RTE) to be provided to Integration Project

Global function (except the ones that are defined in RTE modules) that
is defined in this component but used by other function

# Configuration REQUIREMeNTS

## Build Time Config

| **Modules** | **Notes** |     |
|-------------|-----------|-----|
| **None**    |           |     |

## Configuration Files to be provided by Integration Project

None

## Da Vinci Parameter Configuration Changes

| **Parameter** | **Notes** | **SWC** |
|---------------|-----------|---------|
| None          |           |         |

## DaVinci Interrupt Configuration Changes

| **ISR Name** | **VIM \#** | **Priority Dependency** | **Notes** |
|--------------|------------|-------------------------|-----------|
| None         |            |                         |           |

## Manual Configuration Changes

| **Constant** | **Notes** | **SWC** |
|--------------|-----------|---------|
| None         |           |         |

# Integration DATAFLOW REQUIREMENTS

## Required Global Data Inputs

ExpectedOnTimeA_Cnt_u32

ExpectedOnTimeB_Cnt_u32

ExpectedOnTimeC_Cnt_u32

LRPRCorrectedMtrPosCaptured_Rev_f32

LRPRModulationIndexCaptured_Uls_f32

LRPRPhaseadvanceCaptured_Cnt_s16

MeasuredOnTimeA_Cnt_u32

MeasuredOnTimeB_Cnt_u32

MeasuredOnTimeC_Cnt_u32

MotorVelMRFUnfiltered_MtrRadpS_f32

MtrElecMechPolarity_Cnt_s08

PDActivateTest_Cnt_lgc

MtrDrvrInitStart_Cnt_lgc

GateDriveResetActive_Cnt_lgc \*

## Required Global Data Outputs

SVDiag_LowPhReasErrorAcc_Cnt_u16

SVDiag_HighResPhsReasDisable_u8

SVDiag_LowResPhsReasDisable_u8

SVDiag_MtrDrvInitComp_Cnt_lgc

SVDiag_GateDriveFltAcc_Cnt_u16

SVDiag_GenGateDriveFltAcc_Cnt_u16

SVDiag_OnStateFltAcc_Cnt_u16

GateDriveResetActive_Cnt_lgc \*

\*\[ GateDriveResetActive_Cnt_lgc is an input for the module
**Ap_DigPhsReasDiag.C** and is an output for the module
**Sa_MtrDrvDiag.C** \]

## Specific Include Path present

No

# Runnable Scheduling 

This section specifies the required runnable scheduling.

| **Init**            | **Scheduling Requirements**                                                 | **Trigger**      |
|-------------------|---------------------------------------|---------------|
| DigPhsReasDiag_Init | Executed once after the RTE is started before first call of MtrDrvDiag_Per1 | RTE (at Startup) |

| **Runnable**          | **Scheduling Requirements**            | **Trigger**      |
|-------------------|---------------------------------------|---------------|
| DigPhsReasDiag_Per1   | Not in OFF, DISABLE, or WARMINIT modes | Rte 2ms task     |
| DigPhsReasDiag_Trans1 | In OPERATE mode                        | On entering mode |
| MtrDrvDiag_Per1       | Not in DISABLE or OFF modes            | Rte 2ms task     |
| MtrDrvDiag_Per2       | Not in OPERATE or WARMINIT modes       | Rte 2ms task     |
| MtrDrvDiag_Trns1      | In WARMINIT mode                       | On entering mode |

**.**

# Memory Map REQUIREMENTS

## Mapping

| **Memory Section**                           | **Contents** | **Notes** |
|----------------------------------------------|--------------|-----------|
| **\< Memory mapping Info\>\***               |              |           |
| DIGPHSREASDIAG_START_SEC_VAR_CLEARED_32      |              |           |
| DIGPHSREASDIAG_START_SEC_VAR_CLEARED_BOOLEAN |              |           |
| DIGPHSREASDIAG_START_SEC_VAR_CLEARED_16      |              |           |
| DIGPHSREASDIAG_START_SEC_VAR_CLEARED_8       |              |           |
| MTRDRVDIAG_START_SEC_VAR_CLEARED_32          |              |           |
| MTRDRVDIAG_START_SEC_VAR_CLEARED_16          |              |           |
| MTRDRVDIAG_START_SEC_VAR_CLEARED_BOOLEAN     |              |           |
| MTRDRVDIAG_START_SEC_VAR_CLEARED_UNSPECIFIED |              |           |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

| **Feature** | **RAM** | **ROM** |
|-------------|---------|---------|
| Full        |         |         |

Table 1: ARM Cortex R4 Memory Usage

## Non RTE NvM Blocks

| **Block Name** |
|----------------|
| None           |

Note : Size of the NVM block if configured in developer

##  RTE NvM Blocks

| **Block Name** |
|----------------|
| None           |

Note : Size of the NVM block if configured in developer

# Compiler Settings

##  Preprocessor MACRO

None

## Optimization Settings

None

# Appendix

*None*

{% endraw %}