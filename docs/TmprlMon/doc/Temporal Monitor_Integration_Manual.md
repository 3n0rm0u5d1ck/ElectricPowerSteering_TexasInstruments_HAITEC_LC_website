---
layout: default
title: Temporal Monitor_Integration_Manual
nav_order: 2
parent: Temporal Monitoring
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

None

# Configuration

## Build Time Config

| Modules | Notes |     |
|---------|-------|-----|
| None    |       |     |

## Configuration Files to be provided by Integration Project

##  [section]

**Sa_TmprlMon_Cfg.h** generated by Sa_TmprlMon_Cfg.h.tt

**Sa_TmprlMon2_Cfg.h** generated by Sa_TmprlMon2_Cfg.h.tt

### Da Vinci Parameter Configuration Changes

| Parameter                          | Notes                     | SWC |
|------------------------------------|---------------------------|-----|
| TmprlMonGeneral/TmprlMonCPEnable   | To enable the check point |     |
| TmprlMon2General/TmprlMon2CPEnable | To enable the check point |     |

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

No

# Runnable Scheduling 

This section specifies the required runnable scheduling.

| Init | Scheduling Requirements | Trigger |
|------|-------------------------|---------|
| None | None                    | None    |

<table style="width:100%;">
<colgroup>
<col style="width: 25%" />
<col style="width: 54%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Runnable</th>
<th>Scheduling Requirements</th>
<th>Trigger</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>TmprlMon_Per1</td>
<td>None</td>
<td>RTE (2ms)</td>
</tr>
<tr class="even">
<td>TmprlMon_Per2</td>
<td>None</td>
<td><p>RTE (2ms)</p>
<p>not in Mode(s) &lt;DISABLE, OPERATE, OFF&gt;</p></td>
</tr>
<tr class="odd">
<td>TmprlMon_Per3</td>
<td>None</td>
<td><p>RTE (10ms)</p>
<p>not in Mode(s) &lt;WARMINIT, OFF&gt;</p></td>
</tr>
<tr class="even">
<td>TmprlMon_Trns1</td>
<td>None</td>
<td>RTE on entering WARMINIT mode</td>
</tr>
<tr class="odd">
<td>TmprlMon_Trns2</td>
<td>None</td>
<td>RTE on entering DISABLE mode</td>
</tr>
<tr class="even">
<td>TmprlMon2_Per1</td>
<td>None</td>
<td>RTE (2ms)</td>
</tr>
</tbody>
</table>

**.**

# Memory Mapping

## Mapping

| Memory Section                             | Contents | Notes |
|--------------------------------------------|----------|-------|
| TMPRLMON_START_SEC_CONST_UNSPECIFIED       |          |       |
| TMPRLMON_START_SEC_VAR_CLEARED_UNSPECIFIED |          |       |
| TMPRLMON_START_SEC_VAR_CLEARED_32          |          |       |
| TMPRLMON_START_SEC_VAR_CLEARED_8           |          |       |
| TMPRLMON_START_SEC_VAR_CLEARED_BOOLEAN     |          |       |
| TMPRLMON_START_SEC_VAR_CLEARED_16          |          |       |
| RTE_START_SEC_SA_TMPRLMON2_APPL_CODE       |          |       |
| RTE_START_SEC_SA_TMPRLMON_APPL_CODE        |          |       |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

| Feature | RAM | ROM |
|---------|-----|-----|
| None    |     |     |

Table 1: ARM Cortex R4 Memory Usage

## Non RTE NvM Blocks

| Block Name |
|------------|
| None       |

Note : Size of the NVM block if configured in developer

##  RTE NvM Blocks

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

|            |                        |          |            |
|------------|------------------------|----------|------------|
| **Rev \#** | **Change Description** | **Date** | **Author** |
| 1          | Initial version        | 3-Feb-14 | Rijvi      |

{% endraw %}