---
layout: default
title: AbsHwPos_TcI2cVd_Integration_Manual
nav_order: 2
parent: AbsHwPos_TcI2cVd
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

| Module          | Required Feature                       |
|-----------------|----------------------------------------|
| \<Name of SWC\> | \<Addition of global data, function\*. |

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
refered. Developer should track the references.

## Global Functions(Non RTE) to be provided to Integration Project

None

# Configuration

## Build Time Config

| Modules | Notes |     |
|---------|-------|-----|
| None    |       |     |

## Configuration Files to be provided by Integration Project

##  [section]

Ap_AbsHwPos_Cfg.h (generated using Ap_AbsHwPos_Cfg.h.tt)

### Da Vinci Parameter Configuration Changes

| Parameter                        | Notes                        | SWC      |
|----------------------------------|------------------------------|----------|
| AbsHwPosGeneral\AbsHwPosCPEnable | Enable checkpoints if needed | AbsHwPos |

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

CumMechMtrPosCRF_Deg_f32

AlignedCumMechMtrPosCRF_Deg_f32

TurnsCntrValidity_Cnt_u08

I2CHwAbsPos_HwDeg_f32

I2CHwAbsPosValid_Cnt_lgc

SensorlessHwPos_HwDeg_f32

SensorlessAuthority_Uls_f32

ComplError_HwDeg_f32

DiagStatusHwPosReducedPerf_Cnt_lgc

ManufMode_Cnt_enum

## Required Global Data Outputs

HandwheelPosition_HwDeg_f32

HandwheelAuthority_Uls_f32

RelHwPos_HwDeg_f32

HwPosSource_Cnt_u16

SrlComHwPos_HwDeg_f32

SrlComHwPosStatus_Cnt_u16

## Specific Include Path present

No

# Runnable Scheduling 

This section specifies the required runnable scheduling.

| Init           | Scheduling Requirements                                | Trigger     |
|-------------------|---------------------------------------|---------------|
| AbsHwPos_Init1 | Called from RTE before first call of periodic function | RTE at init |

| Runnable                   | Scheduling Requirements                                | Trigger   |
|------------------------|-----------------------------------|--------------|
| AbsHwPos_Per1              | Call before 2ms periodic that uses RelHwPos_HwDeg_f32  | RTE 2 ms  |
| AbsHwPos_Per2              | Call after 2ms periodic that outputs VDHwPos_HwDeg_f32 | RTE 2 ms  |
| AbsHwPos_Per3              | None                                                   | RTE 4 ms  |
| AbsHwPos_Per4              | None                                                   | RTE 10 ms |
| AbsHwPos_SCom_CustSetTrim  | Common Manufacturing                                   | On event  |
| AbsHwPos_SCom_CustClrTrim  | Common Manufacturing                                   | On event  |
| AbsHwPos_SCom_NxtSetTrim   | Common Manufacturing                                   | On event  |
| AbsHwPos_SCom_NxtClearTrim | Common Manufacturing                                   | On event  |

**.**

# Memory Mapping

## Mapping

| Memory Section                             | Contents | Notes |
|--------------------------------------------|----------|-------|
| ABSHWPOS_START_SEC_VAR_CLEARED_UNSPECIFIED |          |       |
| ABSHWPOS_START_SEC_VAR_CLEARED_BOOLEAN     |          |       |
| ABSHWPOS_START_SEC_VAR_CLEARED_16          |          |       |
| ABSHWPOS_START_SEC_VAR_CLEARED_32          |          |       |
| RTE_START_SEC_AP_ABSHWPOS_APPL_CODE        |          |       |

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
| EOLVehCntrOffset |

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

|            |                                                                                                                                                    |             |            |
|-------|--------------------------------------------------|----------|-------|
| **Rev \#** | **Change Description**                                                                                                                             | **Date**    | **Author** |
| 1.0        | Initial version                                                                                                                                    | 26-Nov-13   | KMC        |
| 2.0        | Updated per ES5G rev 006 - Renamed the inputs VD_HwPos and VD_Authority to Sensorless_HwPos and Sensorless_Authority to match updated SF42 outputs | 22-Aug-2014 | SB         |

{% endraw %}