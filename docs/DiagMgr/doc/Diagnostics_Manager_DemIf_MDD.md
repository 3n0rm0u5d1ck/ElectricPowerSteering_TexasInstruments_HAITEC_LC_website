---
layout: default
title: Diagnostics_Manager_DemIf_MDD
nav_order: 4
parent: Diagnostic Manager
---
{% raw %}
# Module -- DEM Interface [module----dem-interface]

# High-Level Description

# Figures

## Component Diagram 

# Variable Data Dictionary

| Module Inputs    | Module Outputs |     |
|------------------|----------------|-----|
| IgnCnt_Cnt_u16   |                |     |
| MtrTrq_MtrNm_f32 |                |     |
| VehSpd_Kph_f32   |                |     |
| HwTrq_HwNm_f32   |                |     |
| SystemState_Mode |                |     |

## Module Internal Variables

<table>
<colgroup>
<col style="width: 29%" />
<col style="width: 9%" />
<col style="width: 4%" />
<col style="width: 5%" />
<col style="width: 8%" />
<col style="width: 1%" />
<col style="width: 10%" />
<col style="width: 1%" />
<col style="width: 14%" />
<col style="width: 14%" />
</colgroup>
<thead>
<tr class="header">
<th>Variable Name</th>
<th>Datatype</th>
<th colspan="2">Resolution</th>
<th colspan="2"><p>Legal Range</p>
<p>(min)</p></th>
<th><p>Legal Range</p>
<p>(max)</p></th>
<th colspan="3"><p>Software Segment</p>
<p>{Data Type}</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>DEMEventActive_Cnt_M_lgc[D_NUMOFDEMEVENTS_CNT_U08+1]</td>
<td colspan="9">Refer to Diagnostics_Manager_Core_MDD.docx</td>
</tr>
<tr class="even">
<td>ResetNTCFlag_Cnt_M_u08</td>
<td colspan="9">Diagnostics_Manager_GeneratedCfg_MDD.docx</td>
</tr>
<tr class="odd">
<td>LatchCounter_Cnt_u16</td>
<td colspan="2">uint16</td>
<td colspan="2">1</td>
<td colspan="3">0</td>
<td>65535</td>
<td>DIAGMGRDEMIF_START_SEC_VAR_16</td>
</tr>
<tr class="even">
<td>NTCStrgArray_Cnt_str</td>
<td colspan="9">Refer to Diagnostics_Manager_Core_MDD.docx</td>
</tr>
<tr class="odd">
<td>NTCBlackBoxData_Cnt_str</td>
<td colspan="9">Refer to Diagnostics_Manager_Core_MDD.docx</td>
</tr>
</tbody>
</table>

### User defined typedef definition/declaration 

<table>
<colgroup>
<col style="width: 35%" />
<col style="width: 26%" />
<col style="width: 16%" />
<col style="width: 11%" />
<col style="width: 11%" />
</colgroup>
<thead>
<tr class="header">
<th>Typedef Name</th>
<th>Element Name</th>
<th>User Defined Type</th>
<th><p>Legal Range</p>
<p>(min)</p></th>
<th><p>Legal Range</p>
<p>(max)</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Typedef struct {} NTCLatch_Str</td>
<td>NTC</td>
<td>NTCNumber</td>
<td>0</td>
<td>511</td>
</tr>
<tr class="even">
<td></td>
<td>DiagSettings_Str.Threshold</td>
<td>Uint16</td>
<td>0</td>
<td>65535</td>
</tr>
<tr class="odd">
<td></td>
<td>DiagSettings_Str.PStep</td>
<td>Uint16</td>
<td>0</td>
<td>65535</td>
</tr>
<tr class="even">
<td></td>
<td>DiagSettings_Str.NStep</td>
<td>Uint16</td>
<td>0</td>
<td>65535</td>
</tr>
</tbody>
</table>

# Constant Data Dictionary

## Calibration Constants

| Constant Name               |
|-----------------------------|
| t_SortedNTCs_Cnt_enum\[\]   |
| k_FltRspTbl_Cnt_str\[\]     |
| t_BlkBoxGrp_Ptr_u32\[\]\[\] |
| t_LatchFaults_Cnt_str\[\]   |

##  [section]

## Program(fixed) Constants

### Embedded Constants

#### Local

| Constant Name                | Resolution | Units  | Value                                                              |
|-----------------------------------|---------|--------|----------------------|
| D_EVTNOTPASSBITS_CNT_B8      | N/A        | Counts | (D_TESTFAILEDBIT_CNT_B8 \| D_TESTNOTCOMPLETETHISOPCYCLEBIT_CNT_B8) |
| D_AGINGCOUNTERTHRESH_CNT_U08 | N/A        | Counts | 0x40                                                               |

#### Global

| Constant Name                          |
|----------------------------------------|
| D_NUMOFDEMEVENTS_CNT_U08               |
| D_TESTFAILEDBIT_CNT_B8                 |
| D_TESTNOTCOMPLETETHISOPCYCLEBIT_CNT_B8 |
| D_NTCACTIVEBITS_CNT_B8                 |
| D_MAXLATCHACTIVENTCS_CNT_U08           |

###  [section-1]

### Module specific Lookup Tables Constants

| Constant Name                          | Resolution | Value    | Software Segment |
|-------------------|---------|----------------------------------|------------|
| T_DiagMgrNtcAppInfoMap_Cnt_Str\[SIZE\] |            | Refer \* | AP_DIAGMGR_CONST |
| T_DiagMgrNtcInfoPtr_Cnt_Str\[SIZE\]    |            | Refer \* | AP_DIAGMGR_CONST |
|                                        |            |          |                  |

Note: “ Refer \*” - Refer to Diagnostics_Manager_GeneratedCfg_MDD

Note Size and elements of Table constants varies across projects. Check
project configuration files Under UTP/ Contract folder for data.

#  Functions/Macros used by the Sub-Modules 

## Library Functions / Macros 

The library and functions / Macros that are called by the various sub
modules are identified below,

1.  TableSize_m()

2.  

## Data Hiding Functions

1.  \<None\>

2.  

## Global Functions/Macros Defined by this Module

### Diagnostic Manager Init 1

|                      |               |      |     |     |
|----------------------|---------------|------|-----|-----|
| **Function Name**    | DiagMgr_Init1 | Type | Min | Max |
| **Arguments Passed** | none          |      |     |     |
| **Return Value**     | none          |      |     |     |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DiagMgr/doc/mediax/media/image1.emf)

###  [section-2]

### Diagnostic Manager Transition 1

|                      |               |      |     |     |
|----------------------|---------------|------|-----|-----|
| **Function Name**    | DiagMgr_Trns1 | Type | Min | Max |
| **Arguments Passed** | none          |      |     |     |
| **Return Value**     | none          |      |     |     |

#### Description

Rte_Call_DemIf_RestartDem()

Rte_Call_DemIf_SetOperationCycleState(NxtrDefaultOpCycle,
NXTR_CYCLE_STATE_START)

### Diagnostic Manager StaCtrl Shutdown

|                      |                          |      |     |     |
|----------------------|--------------------------|------|-----|-----|
| **Function Name**    | DiagMgr_StaCtrl_Shutdown | Type | Min | Max |
| **Arguments Passed** | none                     |      |     |     |
| **Return Value**     | none                     |      |     |     |

#### Description

Rte_Call_DemIf_SetOperationCycleState(NxtrDefaultOpCycle,
NXTR_CYCLE_STATE_END)

Rte_Call_DemIf_DemShutdown()

CreateStorageArray(1U)

NvM_SetRamBlockStatus(NVM_BLOCK_DIAGMGR_NTCSTRG, TRUE)

NvM_SetRamBlockStatus(NVM_BLOCK_DIAGMGR_BLACKBOX, TRUE)

### Diagnostic Manager Periodic 2

|                      |              |      |     |     |
|----------------------|--------------|------|-----|-----|
| **Function Name**    | DiagMgr_Per2 | Type | Min | Max |
| **Arguments Passed** | none         |      |     |     |
| **Return Value**     | none         |      |     |     |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DiagMgr/doc/mediax/media/image2.emf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DiagMgr/doc/mediax/media/image3.emf)

### Diagnostic Manager Get NTC Information

|                      |                         |                     |     |      |
|----------|---------------------|----------------------|----------|-----------|
| **Function Name**    | DiagMgr_SCom_GetNTCInfo | Type                | Min | Max  |
| **Arguments Passed** | NTC_Cnt_T_enum          | NTCNumber           | 0   | 511  |
|                      | Param_Ptr_T_u08         | const uint8 pointer | 0   | FULL |
|                      | Status_Ptr_T_u08        | const uint8 pointer | 0   | FULL |
|                      | AgingCounter_Ptr_T_u08  | const uint8 pointer | 0   | FULL |
| **Return Value**     | none                    |                     |     |      |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DiagMgr/doc/mediax/media/image4.emf)

### Diagnostic Manager Reset NTC Status

|                      |                             |      |     |     |
|----------------------|-----------------------------|------|-----|-----|
| **Function Name**    | DiagMgr_SCom_ResetNTCStatus | Type | Min | Max |
| **Arguments Passed** | None                        |      |     |     |
| **Return Value**     | none                        |      |     |     |

#### Description

ResetNTCFlag_Cnt_M_u08 = \~ResetNTCFlag_Cnt_M_u08

### Diagnostic Manager Read Storage Array

|                      |                            |      |     |     |
|----------------------|----------------------------|------|-----|-----|
| **Function Name**    | DiagMgr_SCom_ReadStrgArray | Type | Min | Max |
| **Arguments Passed** | None                       |      |     |     |
|                      |                            |      |     |     |
| **Return Value**     | none                       |      |     |     |

#### Description

CreateStorageArray(0U)

### Diagnostic Manager Clear Black Box

|                      |                            |      |     |     |
|----------------------|----------------------------|------|-----|-----|
| **Function Name**    | DiagMgr_SCom_ClearBlackBox | Type | Min | Max |
| **Arguments Passed** | None                       |      |     |     |
| **Return Value**     | none                       |      |     |     |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DiagMgr/doc/mediax/media/image5.emf)

### Diagnostic Manager Clear Latch Counters

|                      |                                 |      |     |     |
|----------------------|---------------------------------|------|-----|-----|
| **Function Name**    | DiagMgr_SCom_ClearLatchCounters | Type | Min | Max |
| **Arguments Passed** | None                            |      |     |     |
| **Return Value**     | none                            |      |     |     |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DiagMgr/doc/mediax/media/image6.emf)

###  [section-3]

### Update Black Box

|                      |                        |       |     |      |
|----------------------|------------------------|-------|-----|------|
| **Function Name**    | UpdateBlkBox           | Type  | Min | Max  |
| **Arguments Passed** | NTC_Cnt_T_u08          | Uint8 | 0   | FULL |
|                      | Param_Cnt_T_u08        | Uint8 | 0   | FULL |
|                      | BlkBoxGrpIdx_Cnt_T_u08 | Uint8 | 0   | 6    |
| **Return Value**     | none                   |       |     |      |

#### Design Rationale

The configuration option DIAGMGR_IS_MTO_PROGRAM is used to configure the
use of Param1 and Param2 for specific program types. If
DIAGMGR_IS_MTO_PROGRAM is set to TRUE, Param1 is used for Differential
Pressure and Param2 is used for Coil Current Commanded.. Meanwhile, if
DIAGMGR_IS_MTO_PROGRAM is set to FALSE, Param1 is mapped to Handwheel
torque and Param2 is mapped to Motor Torque. It is intended that
DIAGMGR_IS_MTO_PROGRAM will be set to FALSE for EPS systems and TRUE for
MTO systems.

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DiagMgr/doc/mediax/media/image7.emf)

## Local Functions/Macros Used by this MDD only

### Create Storage Array

|                      |                       |       |     |     |
|----------------------|-----------------------|-------|-----|-----|
| **Function Name**    | CreateStorageArray    | Type  | Min | Max |
| **Arguments Passed** | AgingCounterIncrement | uint8 | 0   | 1   |
| **Return Value**     | N/A                   |       |     |     |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DiagMgr/doc/mediax/media/image8.emf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DiagMgr/doc/mediax/media/image9.emf)

# Software Module Implementation

## Runtime Environment (RTE) Initial Values

| Data | Value |
|------|-------|
|      |       |

## Initialization Functions

None

## Periodic Functions

None

## Fault Recovery Functions

None

## Shutdown Functions

None

## Interrupt Functions

None

## Fault Recovery Functions

None

## Shutdown Functions

None

## Interrupt Functions

None

## Serial Communication Functions

None

# Execution Requirements

## Execution Sequence of the Module

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

| Function Name | Calling Frequency | System State(s) in which the function is called |
|--------------------------|-----------------|------------------------------|
|               |                   |                                                 |

## Execution Requirements for Serial Communication Functions 

| Function Name | Sub-Module called by (Serial Comm Function Name) |
|---------------|--------------------------------------------------|
|               |                                                  |

#  [section-4]

#  Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

| Name of Sub Module | Software Segment |
|--------------------|------------------|
|                    |                  |

##  [section-5]

## Global and Local Functions

This table identifies the software segments for local functions
identified in this module.

| Name of Sub Module          | Software Segment         |
|-----------------------------|--------------------------|
| DiagMgr_Trns1               | RTE_AP_DIAGMGR_APPL_CODE |
| DiagMgr_Trns2               | RTE_AP_DIAGMGR_APPL_CODE |
| DiagMgr_Per2                | RTE_AP_DIAGMGR_APPL_CODE |
| DiagMgr_SCom_GetNTCInfo     | RTE_AP_DIAGMGR_APPL_CODE |
| DiagMgr_Scom_ResetNTCStatus | RTE_AP_DIAGMGR_APPL_CODE |
| DiagMgr_Scom_ReadStrgArray  | RTE_AP_DIAGMGR_APPL_CODE |
| DiagMgr_Scom_ClearBlackBox  | RTE_AP_DIAGMGR_APPL_CODE |
| UpdateBlkBox                | AP_DIAGMGR_CODE          |
| CreateStorageArray          | AP_DIAGMGR_CODE          |

#  [section-6]

#  Known Issues / Limitations With Design

1.  The latch active counters will not be stepped/checked on a quick
    ignition cycle as the Init1 function will not be called.

# Revision Control Log

|            |                                                                                                |              |                     |
|-------|-------------------------------------------|------------|------------|
| **Rev \#** | **Change Description**                                                                         | **Date**     | **Author Initials** |
| 1          | Initial MDD version                                                                            | 26-Mar-13    | VK                  |
| 2          | MDD Catch up to match to SRC Ver 5                                                             | 24- June- 13 | NRAR                |
| 3          | Added init function to support latch active diagnostic addition                                | 04-OCT-13    | Jared               |
| 4          | Updated for changes to snapshot configuration to make HwTrq and MtrTrq parameters more generic | 28-Feb-14    | Jared               |

{% endraw %}