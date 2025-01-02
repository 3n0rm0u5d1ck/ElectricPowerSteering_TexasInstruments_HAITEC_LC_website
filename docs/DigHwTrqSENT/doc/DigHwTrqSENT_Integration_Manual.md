---
layout: default
title: DigHwTrqSENT_Integration_Manual
nav_order: 3
parent: DigHwTrqSENT
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

| Module   | Required Feature |
|----------|------------------|
| \<None\> |                  |

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
refered. Developer should track the references.

## Global Functions(Non RTE) to be provided to Integration Project

\< None\>

# Configuration

## Build Time Config

| Modules                             | Notes                  |     |
|-------------------------------------|------------------------|-----|
| BC_DIGHWTRQSENT_FAULTINJECTIONPOINT | Fault injection points |     |

## Configuration Files to be provided by Integration Project

##  [section]

Sa_DigHwTrqSENT_Cfg.h for checkpoint enables

### Da Vinci Parameter Configuration Changes

| Parameter | Notes | SWC |
|-----------|-------|-----|
| \<None\>  |       |     |

### DaVinci Interrupt Configuration Changes

| ISR Name | VIM \# | Priority Dependency | Notes |
|----------|--------|---------------------|-------|
| \<None\> |        |                     |       |

### Manual Configuration Changes

| Constant | Notes | SWC |
|----------|-------|-----|
| \<None\> |       |     |

# Integration

## Required Global Data Inputs

T1_HwNm_f32 from FDD ES-34B

T2_HwNm_f32 from FDD ES-34B

## Required Global Data Outputs

HwTorque_HwNm_f32

SysCHwTorque_HwNm_f32

## Specific Include Path present

No

# Runnable Scheduling 

This section specifies the required runnable scheduling.

| Init                 | Scheduling Requirements | Trigger |
|----------------------|-------------------------|---------|
| DigHwTrqSENT_Init1() | None                    | Init    |

| Runnable                     | Scheduling Requirements                                                                                     | Trigger  |
|--------------------------|--------------------------------|--------------|
| DigHwTrqSENT_Per1            | After update of T1_HwNm_f32 and T2_HwNm_f32                                                                 | 2 ms     |
| DigHwTrqSENT_Per2            | None                                                                                                        | 4 ms     |
| DigHwTrqSENT_Per3            | None                                                                                                        | 100 ms   |
| DigHwTrqSENT_SCom_ClrTrqTrim | triggered by server invocation for OperationPrototype \<ClrTrqTrim\> of PortPrototype \<DigHwTrqSENT_SCom\> | On event |
| DigHwTrqSENT_SCom_SetTrqTrim | triggered by server invocation for OperationPrototype \<SetTrqTrim\> of PortPrototype \<DigHwTrqSENT_SCom\> | On event |
| DigHwTrqSENT_SCom_TrimData   | triggered by server invocation for OperationPrototype \<TrimData\> of PortPrototype \<DigHwTrqSENT_SCom\>   | On event |
| DigHwTrqSENT_SCom_WriteData  | triggered by server invocation for OperationPrototype \<WriteData\> of PortPrototype \<DigHwTrqSENT_SCom\>  | On event |

**.**

# Memory Mapping

## Mapping

| Memory Section                                 | Contents | Notes         |
|------------------------------------------------|----------|---------------|
| DIGHWTRQSENT_START_SEC_VAR_CLEARED_32          |          |               |
| DIGHWTRQSENT_START_SEC_VAR_CLEARED_UNSPECIFIED |          |               |
| DIGHWTRQSENT_START_SEC_VAR_SAVED_ZONEH_32      |          | Zone H EEPROM |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

| Feature                | RAM | ROM |
|------------------------|-----|-----|
| \<Memmap usuage info\> |     |     |

Table 1: ARM Cortex R4 Memory Usage

## Non RTE NvM Blocks

| Block Name |
|------------|
| \<None \>  |

Note : Size of the NVM block if configured in developer

##  RTE NvM Blocks

| Block Name       |
|------------------|
| DigHwTrqSENTTrim |

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

|            |                                                                                                         |           |            |
|-------|--------------------------------------------------|----------|-------|
| **Rev \#** | **Change Description**                                                                                  | **Date**  | **Author** |
| 1          | Initial version                                                                                         | 01-Jul-13 | KMC        |
| 2          | Updated per Design Review CR 11619 – Corrected Runnable Names – Removed “Sa\_” from Init, Per functions | 03-Mar-14 | SB         |
| 3          | Turned on track changes and corrected rev 2 changes                                                     | 01-Apr-14 | SB         |
| 4          | Implemented ES04C Rev 006                                                                               | 09-Jun-14 | SB         |
| 5          | Implemented ES04C Rev 007 and added the function DigHwTrqSENT_Scom_WriteData                            | 08-Aug-14 | VS         |

{% endraw %}