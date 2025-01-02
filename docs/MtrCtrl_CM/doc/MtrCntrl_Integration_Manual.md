---
layout: default
title: MtrCntrl_Integration_Manual
nav_order: 5
parent: Motor Control
---
{% raw %}
[1 Dependencies [2](#dependencies)](#dependencies)

[1.1 SWCs [2](#swcs)](#swcs)

[1.2 Configuration Files to be provided by Integration Project
[2](#configuration-files-to-be-provided-by-integration-project)](#configuration-files-to-be-provided-by-integration-project)

[1.3 Functions to be provided by Integration Project
[2](#functions-to-be-provided-to-integration-project)](#functions-to-be-provided-to-integration-project)

[2 Configuration [3](#configuration)](#configuration)

[2.1 Build Time Config [3](#build-time-config)](#build-time-config)

[2.2 Generator Config [3](#generator-config)](#generator-config)

[3 Integration [4](#integration)](#integration)

[3.1 Global Data [4](#global-data)](#global-data)

[3.2 Component Conflicts
[4](#component-conflicts)](#component-conflicts)

[3.3 Include Path [4](#include-path)](#include-path)

[3.4 ADC2 Changes [4](#_Toc348692770)](#_Toc348692770)

[3.5 Configurator Changes
[4](#configurator-changes)](#configurator-changes)

[3.5.1 DIO [4](#_Toc348692772)](#_Toc348692772)

[3.5.2 Port [5](#_Toc348692773)](#_Toc348692773)

[4 Runnable Scheduling [6](#runnable-scheduling)](#runnable-scheduling)

[5 Memory Mapping [7](#memory-mapping)](#memory-mapping)

[5.1 Mapping [7](#mapping)](#mapping)

[5.2 Usage [7](#usage)](#usage)

[6 Revision Control Log
[8](#revision-control-log)](#revision-control-log)

# Dependencies

## SWCs

| Module | Required Feature |
|--------|------------------|
|        |                  |

## Configuration Files to be provided by Integration Project

MtrCtrl_Cfg.h

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrCtrl_CM/doc/mediax/media/image1.emf)

## Functions to be provided to Integration Project

PICurrCntrl_Per1()

TrqCogCancRefPer1()

# Configuration

## Build Time Config

<table style="width:100%;">
<colgroup>
<col style="width: 36%" />
<col style="width: 53%" />
<col style="width: 9%" />
</colgroup>
<thead>
<tr class="header">
<th>Modules</th>
<th>Notes</th>
<th></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>PICurrentCntrl</p>
<p>TrqCanc</p></td>
<td>Optimization level greater than 3</td>
<td></td>
</tr>
</tbody>
</table>

## Generator Config

| Constant | Notes | SWC |
|----------|-------|-----|
| None     |       |     |

# Integration

## Global Data

The global symbols mapping done in MtrCtrl_Cfg.h.

## Component Conflicts

None

## Include Path

The “include” directory of this SWC needs to be included in the
integration project include search path.

.

## Configurator Changes

None

# Runnable Scheduling

This section specifies the required runnable scheduling.

| Runnable            | Scheduling Requirements                                           | Trigger      |
|------------------|---------------------------------------|---------------|
| TrqCogCancRefPer1() | Must be placed in the motor control ISR, after MtrPos             | Cyclic (ISR) |
| PICurrCntrl_Per1()  | Must be placed in the motor control ISR after TrqCogCancRefPer1() | Cyclic (ISR) |

| Runnable             | Scheduling Requirements                  | Trigger    |
|--------------------|--------------------------------------|---------------|
| CurrParamComp_Init() |                                          | RTE (init) |
| TrqCanc_Init         | Must be placed after CurrParamComp_Init  | RTE (init) |
| QuadDet_Per1         | Must run after TrqReasonable Diagnostics | RTE (2ms)  |
| CurrCmd_Per1         | Must run after QuadDet                   | RTE (2ms)  |
| TrqCanc_Per1         | Must run after CurrCmd_Per1              | RTE (2ms)  |
| PICurrCntrl_Per2()   | Must be placed after TrqCanc_Per1        | RTE (2ms)  |
| CurrParamComp_Per1() | Must be placed after PICurrCntrl_Per2    | RTE (2ms)  |
| PeakCurrEst_Per1()   | Must be placed after PICurrCntrl_Per2    | RTE (2ms)  |
|                      |                                          |            |

\*Note: In motor control ISR include Ap_MtrCtrl.h instead of CDD_Func.h

Proper Initialization of input signals should occur before running each
function for the first time. **(CurrParamComp_Init).**

# Memory Mapping

## Mapping

| Memory Section     | Contents | Notes |
|--------------------|----------|-------|
| RTE Memory mapping |          |       |
|                    |          |       |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

| Feature     | RAM | ROM |
|-------------|-----|-----|
| Full driver |     |     |

## Table 1: ARM Cortex R4 Memory Usage [table-1-arm-cortex-r4-memory-usage]

##  RTE NvM Blocks

| Block Name Size         |
|-------------------------|
| Rte_Pim_CogTrqCal 512   |
| Rte_Pim_CogTrqRplComp 9 |

Note : Size of the NVM block is changed.

##  [section]

# Revision Control Log

|            |                                                                                                      |           |            |
|-------|--------------------------------------------------|----------|-------|
| **Rev \#** | **Change Description**                                                                               | **Date**  | **Author** |
| 1          | Initial version                                                                                      | 25-Mar-13 | Selva      |
| 2          | Updated TrqCanc_Init in RTE Runnables and size of the NVM block CogTrqCal is changed from 512 to 521 | 21-Oct-13 | Selva      |
| 3          | Added new NVM block “Rte_Pim_CogTrqRplComp”                                                          | 23-Oct-13 | Selva      |

{% endraw %}