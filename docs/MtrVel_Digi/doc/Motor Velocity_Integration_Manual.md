---
layout: default
title: Motor Velocity_Integration_Manual
nav_order: 3
parent: MtrVel_Digi
---
{% raw %}
[1 Dependencies [2](#dependencies)](#dependencies)

[1.1 SWCs [2](#swcs)](#swcs)

[1.2 Functions to be provided to Integration Project
[2](#functions-to-be-provided-to-integration-project)](#functions-to-be-provided-to-integration-project)

[2 Configuration [3](#configuration)](#configuration)

[2.1 Build Time Config [3](#build-time-config)](#build-time-config)

[2.2 Configuration Files to be provided by Integration Project
[3](#configuration-files-to-be-provided-by-integration-project)](#configuration-files-to-be-provided-by-integration-project)

[2.2.1 Da Vinci Config Configuration Changes
[3](#da-vinci-config-configuration-changes)](#da-vinci-config-configuration-changes)

[2.2.2 Manual Configuration Changes
[3](#manual-configuration-changes)](#manual-configuration-changes)

[3 Integration [4](#integration)](#integration)

[3.1 Required Global Data Inputs
[4](#required-global-data-inputs)](#required-global-data-inputs)

[3.2 Specific Include Path present
[4](#specific-include-path-present)](#specific-include-path-present)

[4 Runnable Scheduling [5](#runnable-scheduling)](#runnable-scheduling)

[5 Memory Mapping [5](#memory-mapping)](#memory-mapping)

[5.1 Mapping [5](#mapping)](#mapping)

[5.2 Usage [6](#usage)](#usage)

[5.3 RTE NvM Blocks [6](#rte-nvm-blocks)](#rte-nvm-blocks)

[5.4 Non RTE NvM Blocks [6](#non-rte-nvm-blocks)](#non-rte-nvm-blocks)

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
|        |                  |
|        |                  |
|        |                  |

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
refered. Developer should track the references.

## Functions to be provided to Integration Project

MtrVel3_Per1

# Configuration

## Build Time Config

| Modules | Notes |     |
|---------|-------|-----|
| None    |       |     |

## Configuration Files to be provided by Integration Project

##  [section]

MtrVel_Cfg.h (Refer MtrVel_Cfg_Template.h in tools folder)

### Da Vinci Config Configuration Changes

| Constant | Notes | SWC |
|----------|-------|-----|
| None     |       |     |

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
<td>None</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>D_MTRVELOSBUFSZ_CNT_U08</td>
<td><p>D_MTRVELOSBUFSZ_CNT_U08” is defined as Cal “k_BuffSize_Cnt” in
SF40AB</p>
<p>Confirm with the Program being integrated on for the value that needs
to be configured for this constant</p></td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

# Integration

## Required Global Data Inputs

Motor Position calculated in Motor Control ISR should be used. Motor
Position Non RTE inputs should be processed at the same time rate of
Motor Velocity Buffering Periodic

MtrVel_Read_MechMtrPos1TimeStamp_uS_u32 /\* MtrPos Timestamp Calculated
in 0.062 mSec should be used. Motor Pos should be processed at the same
time rate of Motor Velocity 3 periodic 1\*/

MtrVel_Read_MechMtrPos1_Rev_u0p16 /\* MtrPos Calculated in 0.062 mSec
should be used. Motor Pos should be processed at the same time rate of
Motor Velocity 3 periodic 1 \*/

## Specific Include Path present

Yes

# Runnable Scheduling 

This section specifies the required runnable scheduling.

| Init          | Scheduling Requirements | Trigger |
|---------------|-------------------------|---------|
| MtrVel3_Init1 | Once                    | RTE     |
| MtrVel_Init   | Once                    | RTE     |
| MtrVel2_Init  | Once                    | RTE     |

| Runnable     | Scheduling Requirements                         | Trigger           |
|--------------|-------------------------------------------|---------------|
| MtrVel3_Per1 | After DigMSBCorrPer1 Motor ISR periodic (ES51 ) | Motor Control ISR |
| MtrVel_Per1  | After DigMSBCorr Per2 periodic (ES51 )          | RTE(2mS)          |
| MtrVel_Per2  |                                                 | RTE(2mS)          |
| MtrVel2_Per1 |                                                 | RTE(2mS)          |
| MtrVel2_Per2 |                                                 | RTE(2mS)          |

Note : The Scheduling of the periodic between MtrVel_Per1, MtrVel_Per2,
MtrVel2_Per1 should take care of the following constraints. MtrVel_Per1
and MtrVel_Per2 should reside on the same application . MtrVel2_Per1
should reside on the separate application.

MtrVel_Per1output is used by MtrVel2_Per1 and MtrVel_Per2

MtrVel2_Per1 Output is used by MtrVel_Per2

Hence scheduler should schedule in such a way that there is consistent
set of data are used as inputs for MtrVel_Per2.

# Memory Mapping

## Mapping

| Memory Section                   | Contents | Notes |
|----------------------------------|----------|-------|
| MTRVEL_START_SEC_VAR_CLEARED_32  |          |       |
| MTRVEL_START_SEC_VAR_CLEARED_16  |          |       |
| MTRVEL_START_SEC_VAR_CLEARED_8   |          |       |
| MTRVEL2_START_SEC_VAR_CLEARED_32 |          |       |
| MTRVEL2_START_SEC_VAR_CLEARED_16 |          |       |
| MTRVEL2_START_SEC_VAR_CLEARED_8  |          |       |
| MTRVEL3_START_SEC_VAR_CLEARED_16 |          |       |
| MTRVEL3_START_SEC_VAR_CLEARED_8  |          |       |
| MTRVEL3_START_SEC_VAR_CLEARED_32 |          |       |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

| Feature | RAM | ROM |
|---------|-----|-----|
|         |     |     |

Table 1: ARM Cortex R4 Memory Usage

## RTE NvM Blocks

| Block Name |
|------------|
| None       |

Note : Size of the NVM block if configured in developer

## Non RTE NvM Blocks

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

| **Rev \#** | **Change Description** | **Date** | **Author** |
|------------|------------------------|----------|------------|
| 1          | Initial version        | 1-Aug-13 | nzt9hv     |
|            |                        |          |            |

{% endraw %}