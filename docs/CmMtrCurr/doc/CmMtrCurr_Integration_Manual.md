---
layout: default
title: CmMtrCurr_Integration_Manual
nav_order: 2
parent: Component
---
{% raw %}
1 Dependencies 2

1.1 SWCs 2

1.2 Functions to be provided to Integration Project 2

2 Configuration 3

2.1 Build Time Config 3

2.2 Configuration Files to be provided by Integration Project 3

2.2.1 Da Vinci Config Configuration Changes 3

2.2.2 Manual Configuration Changes 3

3 Integration 5

3.1 Required Global Data Inputs 5

3.2 Required Global Output Inputs 5

3.3 Specific Include Path present 5

4 Runnable Scheduling 6

5 Memory Mapping 7

5.1 Mapping 7

5.2 Usage 7

5.3 RTE NvM Blocks 7

5.4 Non RTE NvM Blocks 7

6 Compiler Settings 7

6.1 Preprocessor MACRO 7

6.2 Optimization Settings 7

7 Revision Control Log 8

# Dependencies

## SWCs

| Module                        | Required Feature   |
|-------------------------------|--------------------|
| For version ES01 -008 or more | ADC 33E v3 or more |

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
refered. Developer should track the references.

## Functions to be provided to Integration Project

CurrDQPer1

# Configuration

## Build Time Config

| Modules | Notes |     |
|---------|-------|-----|
| None    |       |     |

## Configuration Files to be provided by Integration Project

##  [section]

CmMtrCurr_Cfg.h ( Refer CmMtrCurr_Cfg_Template.h in tools folder)

(Data synchronization must be provided at the integration level between
2 ms periodic and Motor Control ISR Periodic’s)

Outputs from the CmMtrCurr (Motor Control ISR) periodic must be
synchronized with the outputs from Motor position.

### Da Vinci Config Configuration Changes

| Constant       | Notes                                       | SWC |
|----------------|---------------------------------------------|-----|
| MTRCURRPHASEBC | PhaseB and Phase C used in Curr Measurement |     |
| MTRCURRPHASECB | PhaseC and Phase B used in Curr Measurement |     |
| MTRCURRPHASEAC | PhaseA and Phase C used in Curr Measurement |     |
| MTRCURRPHASECA | PhaseC and Phase A used in Curr Measurement |     |
| MTRCURRPHASEAB | PhaseA and Phase B used in Curr Measurement |     |
| MTRCURRPHASEBA | PhaseB and Phase A used in Curr Measurement |     |

Note: Only one of the configuration can be selected based on the
requirements. Make sure order matches oreder in ADC data read ie
MTRCURRPHASEBC - “BC” represents current_1 is phase B and current_2 is
phase C .

### Manual Configuration Changes

| Constant | Notes | SWC |
|----------|-------|-----|
| none     |       |     |
|          |       |     |
|          |       |     |
|          |       |     |
|          |       |     |
|          |       |     |

# Integration

## Required Global Data Inputs

ADC2OffsetComp_Cnt_u8p8 ( mapped from ADC Configuration 33E)

For other inputs. Refer the template in tools folder of this component

## Required Global Output Inputs

For other inputs. Refer the template in tools folder of this component

## Specific Include Path present

Yes

# Runnable Scheduling 

This section specifies the required runnable scheduling.

| Init           | Scheduling Requirements | Trigger |
|----------------|-------------------------|---------|
| CmMtrCurr_Init | None                    | RTE     |

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
<td>CmMtrCurr_Per2</td>
<td>None</td>
<td>RTE(2MilliS)</td>
</tr>
<tr class="even">
<td>CmMtrCurr_Per3</td>
<td>Runs only in operate.</td>
<td>RTE(2MilliS)</td>
</tr>
<tr class="odd">
<td>CmMtrCurr_Per1</td>
<td>None</td>
<td>RTE(100 MilliS)</td>
</tr>
<tr class="even">
<td>CurrDQPer1</td>
<td><p>After Motor position processing</p>
<p>(As Corrected Motor position is used as input for this
component.)</p></td>
<td>ISR (125MicroS)</td>
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

**.**

# Memory Mapping

## Mapping

| Memory Section                          | Contents | Notes |
|-----------------------------------------|----------|-------|
| CMMTRCURR_START_SEC_VAR_CLEARED_16      |          |       |
| CMMTRCURR_START_SEC_VAR_CLEARED_8       |          |       |
| CMMTRCURR_START_SEC_VAR_CLEARED_BOOLEAN |          |       |
| CMMTRCURR_START_SEC_VAR_CLEARED_32      |          |       |
| SA_CMMTRCURR_CODE                       |          |       |
| RTE_START_SEC_SA_CMMTRCURR_APPL_CODE    |          |       |

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

|            |                                         |           |            |
|-------|--------------------------------------------------|----------|-------|
| **Rev \#** | **Change Description**                  | **Date**  | **Author** |
| 1          | Initial version                         | 7-Sep- 13 | nzt9hv     |
| 2          | Update for ADC Calibration compensation | 27-Ju-14  | Selva      |
|            |                                         |           |            |
|            |                                         |           |            |

{% endraw %}