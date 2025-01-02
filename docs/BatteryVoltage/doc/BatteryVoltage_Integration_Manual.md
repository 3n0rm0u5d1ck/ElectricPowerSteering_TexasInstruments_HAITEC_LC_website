---
layout: default
title: BatteryVoltage_Integration_Manual
nav_order: 3
parent: Battery Voltage
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

| **Module**                | **Required Feature**                             |
|-----------------------|-------------------------------------------------|
| **ADC**                   | D_ADC1CURRENTMODE_ULS_LGC configuration constant |
| **Basic System Services** | EnableOvervoltThreshInterrupt()\*                |

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
referred. Developer should track the references.

\* Note: EnableOvervoltThreshInterrupt() must be called from
ECUStartup.c as soon as possible, but AFTER Adc_Init(), so as to allow
configuration of the ADC registers (and subsequently magnitude
threshold).

## Global Functions(Non RTE) to be provided to Integration Project

-   ISR(Isr_OvervoltThresh)

-   Since the ISR that contains the overvoltage threshold diagnostic is
    enabled in ECUStartup.c, the NTC could be set before the RTE starts.
    In this case the non-Rte “report NTC staus” API should be used.
    Also, the application that contains the Battery Voltage ISR and NTC
    is configured at the integration level. A component specific API,
    BATTERYVOLTAGE_REPORTERRORSTATUS, is used in the ISR source code and
    a header file, Template_BatteryVoltage_Cfg.h, needs to be configured
    to link the BATTERYVOLTAGE_REPORTERRORSTATUS() to the appropriate
    NxtrDiagMgr**???**\_ReportNTCStatus() function. Remove the
    “Template\_” from the file name and replace the ??? in the API with
    the appropriate application and place the file in the Header folder
    of the integration project.

-   

# Configuration

## Build Time Config

| **Modules** | **Notes** |     |
|-------------|-----------|-----|
| **None**    |           |     |

## Configuration Files to be provided by Integration Project

##  [section]

\<Configuration file that will generated from this components that will
require Da Vinci Config generation or manual generation. Describe each
parameter \>

### Da Vinci Parameter Configuration Changes

| **Parameter** | **Notes** | **SWC** |
|---------------|-----------|---------|
| **None**      |           |         |

### DaVinci Interrupt Configuration Changes

| **ISR Name**           | **VIM \#** | **Priority Dependency** | **Notes**      |
|----------------|--------|--------------------------|-----------------------|
| **Isr_OvervoltThresh** | 31         | None                    | Category 2 IRQ |

### Manual Configuration Changes

| **Constant**                         | **Notes** | **SWC** |
|--------------------------------------|-----------|---------|
| **BATTERYVOLTAGE_REPORTERRORSTATUS** |           |         |

# Integration

## Required Global Data Inputs

None

## Required Global Data Outputs

None

## Specific Include Path present

No

# Runnable Scheduling 

This section specifies the required runnable scheduling.

| **Init**                 | **Scheduling Requirements** | **Trigger**     |
|--------------------------|-----------------------------|-----------------|
| **BatteryVoltage_Init1** | None                        | RTE (Warm init) |

| **Runnable**            | **Scheduling Requirements** | **Trigger** |
|-------------------------|-----------------------------|-------------|
| **BatteryVoltage_Per1** | None                        | RTE (2ms)   |
| **BatteryVoltage_Per2** | None                        | RTE (4ms)   |

# Memory Mapping

## Mapping

| **Memory Section**                               | **Contents** | **Notes** |
|-------------------------------------------------|------------|-----------|
| **BATTERYVOLTAGE_START_SEC_VAR_CLEARED_32**      | float32      | None      |
| **BATTERYVOLTAGE_START_SEC_VAR_CLEARED_16**      | uint16       | None      |
| **BATTERYVOLTAGE_START_SEC_VAR_CLEARED_BOOLEAN** | boolean      | None      |

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
| **None**       |

Note : Size of the NVM block if configured in developer

##  RTE NvM Blocks

| **Block Name**                |
|-------------------------------|
| **OvervoltageData (6 bytes)** |

Note : Size of the NVM block if configured in developer

# Compiler Settings

##  Preprocessor MACRO

None

## Optimization Settings

None

##  [section-1]

# Revision Control Log

| **Rev \#** | **Change Description**                                               | **Date**  | **Author** |
|-------|--------------------------------------------------|----------|-------|
| 1          | Initial version                                                      | 16-Apr-13 | Jared      |
| 2          | Added Overvoltage Threshold ISR, some cleanup, updated template      | 3-Jan-14  | Jared      |
| 3          | Added BATTERYVOLTAGE_REPORTERRORSTATUS and new template header file. | 8-Jan-14  | BDO        |

{% endraw %}