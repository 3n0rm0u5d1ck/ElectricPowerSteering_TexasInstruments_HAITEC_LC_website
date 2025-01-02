---
layout: default
title: BVDiag_Integration_Manual
nav_order: 2
parent: Battery Voltage Diagnostics
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

| Modules  | Notes |     |
|----------|-------|-----|
| \<None\> |       |     |

## Configuration Files to be provided by Integration Project

##  [section]

Ap_BVDiag_Cfg.h for checkpoint enables

### Da Vinci Parameter Configuration Changes

<table>
<colgroup>
<col style="width: 39%" />
<col style="width: 47%" />
<col style="width: 12%" />
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
<td>B1_BATTVOLTDIAG</td>
<td><p>This parameter will be turned ON only if customer requires $B1
NTC</p>
<p>STD_ON : Enables NTC $B1 logic</p>
<p>STD_Off : Disables NTC $B1 logic</p></td>
<td></td>
</tr>
<tr class="even">
<td>B1_BATTVOLTDIAG_ELPW</td>
<td><p>This parameter will be turned ON if the customer requires $B1 NTC
be enabled via input from SrlComInput via receiver port</p>
<p>STD_ON: Enables conditional setting of B1 via input</p>
<p>STD_OFF: Disables conditional setting of B1 via input</p></td>
<td></td>
</tr>
</tbody>
</table>

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

Batt_Volt_f32 from SER

CCLMSAActive_Cnt_lgc (Note : Only required for BMW as per its SER)

## Required Global Data Outputs

Sets BatteryVoltage Diagnostics

## Specific Include Path present

No

# Runnable Scheduling 

This section specifies the required runnable scheduling.

| Init | Scheduling Requirements | Trigger |
|------|-------------------------|---------|
| None | None                    | Init    |

| Runnable    | Scheduling Requirements | Trigger |
|-------------|-------------------------|---------|
| BVDiag_Per1 |                         | 10ms    |

**.**

# Memory Mapping

## Mapping

| Memory Section                  | Contents | Notes |
|---------------------------------|----------|-------|
| BVDIAG_START_SEC_VAR_CLEARED_32 |          |       |

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

| Block Name |
|------------|
| None       |

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

|            |                                                                       |           |            |
|-------|--------------------------------------------------|----------|-------|
| **Rev \#** | **Change Description**                                                | **Date**  | **Author** |
| 1          | Initial version                                                       | 13-Sep-13 | NRAR       |
| 2          | Added new configuration constant for conditional enabling of B1 fault | 14-Nov-13 | Jared      |

{% endraw %}