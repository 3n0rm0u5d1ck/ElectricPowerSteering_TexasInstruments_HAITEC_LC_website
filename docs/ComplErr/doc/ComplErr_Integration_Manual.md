---
layout: default
title: ComplErr_Integration_Manual
nav_order: 1
parent: ComplErr
---
{% raw %}
# Integration Manual –ComplErr

Table of Contents

[1 Integration Manual –ComplErr
[1](#integration-manual-complerr)](#integration-manual-complerr)

[1 Dependencies [2](#dependencies)](#dependencies)

[1.1 SWCs [2](#swcs)](#swcs)

[1.2 Global Functions (Non RTE) to be provided to Integration Project
[2](#global-functions-non-rte-to-be-provided-to-integration-project)](#global-functions-non-rte-to-be-provided-to-integration-project)

[1.2.1 ComplErr_Per1() [2](#complerr_per1)](#complerr_per1)

[2 Configuration [2](#configuration)](#configuration)

[2.1 Build Time Config [2](#build-time-config)](#build-time-config)

[2.2 Configuration Files to be provided by Integration Project
[2](#configuration-files-to-be-provided-by-integration-project)](#configuration-files-to-be-provided-by-integration-project)

[2.2.1 Da Vinci Parameter Configuration Changes
[2](#da-vinci-parameter-configuration-changes)](#da-vinci-parameter-configuration-changes)

[2.2.2 DaVinci Interrupt Configuration Changes
[2](#davinci-interrupt-configuration-changes)](#davinci-interrupt-configuration-changes)

[2.2.3 Manual Configuration Changes
[2](#manual-configuration-changes)](#manual-configuration-changes)

[3 Integration [3](#integration)](#integration)

[3.1 Required Global Data Inputs
[3](#required-global-data-inputs)](#required-global-data-inputs)

[3.2 Required Global Data Outputs
[3](#required-global-data-outputs)](#required-global-data-outputs)

[3.3 Specific Include Path present
[3](#specific-include-path-present)](#specific-include-path-present)

[4 Runnable Scheduling [4](#runnable-scheduling)](#runnable-scheduling)

[5 Memory Mapping [5](#memory-mapping)](#memory-mapping)

[5.1 Mapping [5](#mapping)](#mapping)

[5.2 Usage [5](#usage)](#usage)

[5.3 Non RTE NvM Blocks [5](#non-rte-nvm-blocks)](#non-rte-nvm-blocks)

[5.4 RTE NvM Blocks [5](#rte-nvm-blocks)](#rte-nvm-blocks)

[6 Compiler Settings [5](#compiler-settings)](#compiler-settings)

[6.1 Preprocessor MACRO [5](#preprocessor-macro)](#preprocessor-macro)

[6.2 Optimization Settings
[5](#optimization-settings)](#optimization-settings)

[7 Revision Control Log
[6](#revision-control-log)](#revision-control-log)

# Dependencies

## SWCs

| Module | Required Feature |
|--------|------------------|
| None   |                  |

Note: Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
referred. Developer should track the references.

## Global Functions (Non RTE) to be provided to Integration Project

### ComplErr_Per1()

# Configuration

## Build Time Config

| Modules | Notes |     |
|---------|-------|-----|
| None    |       |     |

## Configuration Files to be provided by Integration Project

##  [section]

\<Configuration file that will be generated from this components that
will require Da Vinci Config generation or manual generation. Describe
each parameter \>

### Da Vinci Parameter Configuration Changes

| Parameter | Notes | SWC |
|-----------|-------|-----|
| None      |       |     |

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

None

## Required Global Data Outputs

None

## Specific Include Path present

None

# Runnable Scheduling 

This section specifies the required runnable scheduling.

| Runnable      | Scheduling Requirements | Trigger  |
|---------------|-------------------------|----------|
| ComplErr_Per1 | None                    | RTE(2ms) |

# Memory Mapping

## Mapping

| Memory Section                      | Contents | Notes |
|-------------------------------------|----------|-------|
| RTE_START_SEC_AP_COMPLERR_APPL_CODE |          |       |
|                                     |          |       |
|                                     |          |       |
|                                     |          |       |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

| Feature | RAM | ROM |
|---------|-----|-----|
| N/A     |     |     |

Table 1: ARM Cortex R4 Memory Usage

## Non RTE NvM Blocks

| Block Name |
|------------|
| N/A        |

Note : Size of the NVM block if configured in developer

##  RTE NvM Blocks

| Block Name |
|------------|
| N/A        |

Note : Size of the NVM block if configured in developer

# Compiler Settings

##  Preprocessor MACRO

None

## Optimization Settings

None

##  [section-1]

# Revision Control Log

| **Rev \#** | **Change Description** | **Date** | **Author** |
|------------|------------------------|----------|------------|
| 1          | Initial version        | 08/22/13 | SP         |

{% endraw %}