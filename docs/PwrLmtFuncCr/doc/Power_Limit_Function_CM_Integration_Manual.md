---
layout: default
title: Power_Limit_Function_CM_Integration_Manual
nav_order: 3
parent: Power Limit Function 
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

[3.2 Required Global Data Outputs [4](#_Toc365472032)](#_Toc365472032)

[3.3 Specific Include Path present [4](#_Toc365472033)](#_Toc365472033)

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

\< Global function (except the ones that are defined in RTE modules)
that is defined in this component but used by other function\>

# Configuration

## Build Time Config

| Modules | Notes |     |
|---------|-------|-----|
| None    |       |     |

## Configuration Files to be provided by Integration Project

##  [section]

Ap_PwrLmtFuncCr_Cfg.h

### Da Vinci Parameter Configuration Changes

| Parameter                                | Notes                        | SWC          |
|----------------------------------|--------------------------|-------------|
| PwrLmtFuncCrGeneral/PwrLmtFuncCrCPEnable | Enable checkpoints if needed | PwrLmtFuncCr |

### DaVinci Interrupt Configuration Changes

| ISR Name                                | VIM \# | Priority Dependency | Notes |
|-------------|--------|---------------------------|-------------------------|
| \<Configurator Changes for Interrupts\> |        |                     |       |

### Manual Configuration Changes

| Constant                             | Notes | SWC |
|--------------------------------------|-------|-----|
| \<Additional configuration changes\> |       |     |

# Integration

## Required Global Data Inputs

<span id="_Toc365472032" class="anchor"></span>

EstKe_VpRadpS_f32

MotorVelMRF_MtrRadpS_f32

PosServEnable_Cnt_lgc

Vecu_Volt_f32

CntDisMtrTrqCmdMRF_MtrNm_f32

AltFaultActive_Cnt_lgc

## Required Global Data Outputs

<span id="_Toc365472033" class="anchor"></span>

MRFMtrTrqCmd_MtrNm_f32

FltTrqLmt_Uls_f32

ThresholdExceeded_Cnt_lgc

## Specific Include Path present

\< No \>

# Runnable Scheduling 

This section specifies the required runnable scheduling.

| Init               | Scheduling Requirements                                | Trigger     |
|-------------------|---------------------------------------|---------------|
| PwrLmtFuncCr_Init1 | Called from RTE before first call of periodic function | RTE at init |

| Runnable          | Scheduling Requirements       | Trigger  |
|-------------------|-------------------------------|----------|
| PwrLmtFuncCr_Per1 | Not in WARMINIT, OFF, DISABLE | RTE 2ms  |
| PwrLmtFuncCr_Per2 | Not in WARMINIT, OFF, DISABLE | RTE 10ms |

**.**

# Memory Mapping

## Mapping

| Memory Section                                 | Contents | Notes |
|------------------------------------------------|----------|-------|
| PWRLMTFUNCCR_START_SEC_VAR_CLEARED_32          |          |       |
| PWRLMTFUNCCR_START_SEC_VAR_CLEARED_BOOLEAN     |          |       |
| PWRLMTFUNCCR_START_SEC_VAR_CLEARED_UNSPECIFIED |          |       |
| RTE_START_SEC_AP_PWRLMTFUNCCR_APPL_CODE        |          |       |

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

##  [section-1]

# Revision Control Log

|            |                        |           |            |
|------------|------------------------|-----------|------------|
| **Rev \#** | **Change Description** | **Date**  | **Author** |
| 1          | Initial version        | 28-Aug-13 | KMC        |

{% endraw %}