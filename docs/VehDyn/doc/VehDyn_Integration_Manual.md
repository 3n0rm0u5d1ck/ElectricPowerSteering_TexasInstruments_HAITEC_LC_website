---
layout: default
title: VehDyn_Integration_Manual
nav_order: 3
parent: VehDyn
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

| Module | Required Feature |
|--------|------------------|
| None   |                  |

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
refered. Developer should track the references.

## Global Functions(Non RTE) to be provided to Integration Project

\< Global function (except the ones that are defined in RTE modules)
that is defined in this component but used by other function\>

None

# Configuration

## Build Time Config

| Modules | Notes |     |
|---------|-------|-----|
| None    |       |     |

## Configuration Files to be provided by Integration Project

##  [section]

Ap_VehDyn_Cfg.h (generated using Ap_VehDyn_Cfg.h.tt)

### Da Vinci Parameter Configuration Changes

| Parameter                    | Notes                        | SWC    |
|------------------------------|------------------------------|--------|
| VehDynGeneral/VehDynCPEnable | Enable checkpoints if needed | VehDyn |

### DaVinci Interrupt Configuration Changes

| ISR Name | VIM \# | Priority Dependency | Notes |
|----------|--------|---------------------|-------|
| None     |        |                     |       |

### Manual Configuration Changes

| Constant | Notes | SWC |
|----------|-------|-----|
| None     |       |     |

# Integration

## Required Global Data Inputs

VehicleSpeed_Kph_f32

HwTorque_HwNm_f32

TorqueCmdCRF_MtrNm_f32

VehicleSpeedValid_Cnt_lgc

MotorVelCRF_MtrRadpS_f32

RelHwPos_HwDeg_f32

CcwEOT_HwDeg_f32

CwEOT_HwDeg_f32

HwAuth_Uls_f32

HandwheelPosition_HwDeg_f32

MechMtrPos1_Rev_f32

## Required Global Data Outputs

SensorlessHwAuth_Uls_f32

SensorlessHwPos_HwDeg_f32

## Specific Include Path present

\< No \>

# Runnable Scheduling 

This section specifies the required runnable scheduling.

| Init         | Scheduling Requirements                                | Trigger     |
|-------------------|---------------------------------------|---------------|
| VehDyn_Init1 | Called from RTE before first call of periodic function | RTE at init |

| Runnable    | Scheduling Requirements                                                                                                     | Trigger  |
|-------------------|---------------------------------------|---------------|
| VehDyn_Per1 | Should be called after the 2ms periodic that outputs RelHwPos and before the 2ms periodic that uses VDHwPos and VDAuthority | RTE 2 ms |

| Runnable     | Scheduling Requirements                                                                                          | Trigger         |
|-------------------|---------------------------------------|---------------|
| VehDyn_Trns1 | triggered on entering of Mode \<OFF\> of ModeDeclarationGroupPrototype \<Mode\> of PortPrototype \<SystemState\> | RTE at shutdown |

**.**

# Memory Mapping

## Mapping

| Memory Section                           | Contents | Notes |
|------------------------------------------|----------|-------|
| VEHDYN_START_SEC_VAR_CLEARED_UNSPECIFIED |          |       |
| VEHDYN_START_SEC_VAR_CLEARED_BOOLEAN     |          |       |
| RTE_START_SEC_AP_VEHDYN_APPL_CODE        |          |       |
| VEHDYN_START_SEC_VAR_CLEARED_32          |          |       |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

| Feature               | RAM | ROM |
|-----------------------|-----|-----|
| \<Memmap usage info\> |     |     |

Table 1: ARM Cortex R4 Memory Usage

## Non RTE NvM Blocks

| Block Name |
|------------|
| None       |

Note : Size of the NVM block if configured in developer

##  RTE NvM Blocks

| Block Name  |
|-------------|
| VehDynReset |

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

|            |                                      |           |            |
|------------|--------------------------------------|-----------|------------|
| **Rev \#** | **Change Description**               | **Date**  | **Author** |
| 1          | Initial version                      | 19-Aug-13 | KMC        |
| 2          | Updated per SF42 - VCDMotPos rev 002 | 21-Aug-14 | SB         |
| 3          | Updated to SF42 – VCDMotPos v004     | 16-Jan-15 | SB         |

{% endraw %}