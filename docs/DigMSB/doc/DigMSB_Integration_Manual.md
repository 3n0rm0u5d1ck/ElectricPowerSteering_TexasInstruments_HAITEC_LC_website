---
layout: default
title: DigMSB_Integration_Manual
nav_order: 3
parent: DigMSB
---
{% raw %}
**Integration Manual**

**For**

**DigMSB (ES-50A)**

**VERSION: 8.0**

**DATE: 02-06-2015**

**Prepared By:**

**Rijvi Ahmed**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**  
Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                                                                           |            |             |           |
|-----|------------------------------|-------------|-----------|--------------|
| **Sl. No.** | **Description**                                                           | **Author** | **Version** | **Date**  |
| 1           | Initial version                                                           | nzt9hv     | 1           | 31-May-13 |
| 2           | Corrected the Digital MSB                                                 | Nzt9hv     | 2           | 02-Aug-13 |
| 3           | Updated for v 2 ES 50A Draft                                              | Nzt9hv     | 3           | 08-Aug-13 |
| 4           | Note added to provide buffer output synchronisation                       | Nzt9hv     | 4           | 28-Aug-13 |
| 5           | Added new Memmap statement for cleared DIGMSB_START_SEC_VAR_CLEARED_8     | Nzt9hv     | 5           | 23-Sep-13 |
| 6           | Updated for ES50A prerelease                                              | Selva      | 6           | 3-Apr-14  |
| 7           | Updated for ES50A v6                                                      | Selva      | 7           | 23-Apr-14 |
| 8           | Updated for FDD rev.008 and updated to latest Integration Manual Template | Rijvi      | 8           | 06-Feb-15 |

: ARM Cortex R4 Memory Usage

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

| **Abbreviation** | **Description**            |
|------------------|----------------------------|
| DFD              | Design functional diagram  |
| MDD              | Module design Document     |
| FDD              | Functional Design Document |
|                  |                            |
|                  |                            |

# References

This section lists the title & version of all the documents that are
referred for development of this document

| **Sr. No.** | **Title**               | **Version** |
|-------------|-------------------------|-------------|
| 1           | ES50A_DigMSBAllegro1331 | 008         |
|             |                         |             |
|             |                         |             |
|             |                         |             |
|             |                         |             |

# Dependencies

## SWCs

| **Module** | **Required Feature** |
|------------|----------------------|
| **SPINxt** |                      |

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
referred. Developer should track the references.

Note: Integration of DigMSBSigCorr component is required if using DigMSB
component of version 5 or less. DigMSBCorr Component is not needed after
the integration DigMSB v6 or more.

## Global Functions(Non RTE) to be provided to Integration Project

DigMSB_Per1

# Configuration REQUIREMeNTS

## Build Time Config

| **Modules** | **Notes** |     |
|-------------|-----------|-----|
| **None**    |           |     |

## Configuration Files to be provided by Integration Project

DigMSB_Cfg.h ( Refer DigMSB_Cfg_Template.h in tools folder)

(Data synchronization must be provided at the integration level between
2 ms periodic and Motor Control ISR Periodics)

## Da Vinci Parameter Configuration Changes

| **Parameter** | **Notes** | **SWC** |
|---------------|-----------|---------|
| **None**      |           |         |

## DaVinci Interrupt Configuration Changes

| **ISR Name** | **VIM \#** | **Priority Dependency** | **Notes** |
|--------------|------------|-------------------------|-----------|
| **None**     |            |                         |           |

## Manual Configuration Changes

| **Constant** | **Notes** | **SWC** |
|--------------|-----------|---------|
| **None**     |           |         |

# Integration DATAFLOW REQUIREMENTS

## Required Global Data Inputs

## Required Global Data Outputs

MechMtrPos1_Rev_u0p16

SysCMechMtrPos1_Rev_u0p16

SysCorrectedElecMtrPos_Rev_u0p16

MechMtrPos1TimeStamp_uSec_u32

MechMtrPos2TimeStamp_uSec_u32

CorrectedElecMtrPos_Rev_u0p16

UncorrMechMtrPos1_Rev_u0p16

CumMechMtrPos_Rev_s15p16

Die1RxError_Cnt_u16

Die2RxError_Cnt_u16

Die1RxRevCtr_Cnt_u16

Die2RxRevCtr_Cnt_u16

Die1RxMtrPos_Cnt_u16

Die2RxMtrPos_Cnt_u16

RxMtrPos1ParityAccum_Cnt_u16

RxMtrPos1UnderVoltgFltAccum_Cnt_u16

## Specific Include Path present

Yes

# Runnable Scheduling 

This section specifies the required runnable scheduling.

| **Init**        | **Scheduling Requirements** | **Trigger** |
|-----------------|-----------------------------|-------------|
| **DigMSB_Init** | None                        | RTE         |

<table style="width:100%;">
<colgroup>
<col style="width: 25%" />
<col style="width: 54%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Runnable</strong></th>
<th><strong>Scheduling Requirements</strong></th>
<th><strong>Trigger</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>DigMSB_Per2</strong></td>
<td>None</td>
<td>RTE(2 ms)</td>
</tr>
<tr class="even">
<td><strong>DigMSB_Per3</strong></td>
<td>None</td>
<td>RTE(100 ms)</td>
</tr>
<tr class="odd">
<td><strong>DigMSB_Per1</strong></td>
<td><p>Before Motor</p>
<p>Velocity and before Current Measurement</p></td>
<td>ISR (50 us)</td>
</tr>
</tbody>
</table>

**.**

# Memory Map REQUIREMENTS

## Mapping

| **Memory Section**                           | **Contents** | **Notes** |
|----------------------------------------------|--------------|-----------|
| **DIGMSB_START_SEC_VAR_CLEARED_16**          |              |           |
| **DIGMSB_START_SEC_VAR_CLEARED_8**           |              |           |
| **DIGMSB_START_SEC_VAR_CLEARED_BOOLEAN**     |              |           |
| **DIGMSB_START_SEC_VAR_CLEARED_UNSPECIFIED** |              |           |
| **DIGMSB_START_SEC_VAR_CLEARED_32**          |              |           |
| **SA_DIGMSB_CODE**                           |              |           |
| **RTE_START_SEC_SA_DIGMSB_APPL_CODE**        |              |           |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

| **Feature** | **RAM** | **ROM** |
|-------------|---------|---------|
| **None**    |         |         |

## Non RTE NvM Blocks

| **Block Name** |
|----------------|
| **None**       |

Note : Size of the NVM block if configured in developer

##  RTE NvM Blocks

| **Block Name**    |
|-------------------|
| **DigMSBEOLData** |

Note : Size of the NVM block if configured in developer

# Compiler Settings

##  Preprocessor MACRO

None

## Optimization Settings

None

# Appendix

*None*

{% endraw %}