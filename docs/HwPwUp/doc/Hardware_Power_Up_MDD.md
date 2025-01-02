---
layout: default
title: Hardware_Power_Up_MDD
nav_order: 3
parent: Hardware Power Up
---
{% raw %}
# Module – Hardware Power Up Sequence [module-hardware-power-up-sequence]

# High-Level Description

This module controls the startup initialization sequence for several
modules that would otherwise conflict with one another. It uses a series
of boolean inputs and outputs to control these modules.

# Figures

## Component Diagram

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/HwPwUp/doc/mediax/media/image1.png"
style="width:3.35764in;height:2.47708in" />

#  Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

| Module Inputs                | Module Outputs |                           |
|------------------------------|----------------|---------------------------|
| PwrDiscATestComplete_Cnt_lgc |                | PwrDiscATestStart_Cnt_lgc |
| TMFTestComplete_Cnt_lgc      |                | TMFTestStart_Cnt_lgc      |
| PwrDiscBTestComplete_Cnt_lgc |                | PwrDiscBTestStart_Cnt_lgc |
| MtrDrvrInitComplete_Cnt_lgc  |                | MtrDrvrInitStart_Cnt_lgc  |

#  [section]

# Module Internal Variables

This section identifies the name, range and resolutions for module
specific data created by this module. If there are no range restrictions
on the variable, the term “FULL” is placed into the table for legal
range.

<table>
<colgroup>
<col style="width: 31%" />
<col style="width: 14%" />
<col style="width: 13%" />
<col style="width: 13%" />
<col style="width: 28%" />
</colgroup>
<thead>
<tr class="header">
<th>Variable Name</th>
<th>Resolution</th>
<th><p>Legal Range</p>
<p>(min)</p></th>
<th><p>Legal Range</p>
<p>(max)</p></th>
<th>Software Segment</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>HwPwUp_PowerUpState_Cnt_M_enum</td>
<td>1</td>
<td>0</td>
<td>6</td>
<td>HWPWUP_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="even">
<td>HwPwUp_PwrDiscATestStart_Cnt_M_lgc</td>
<td>boolean</td>
<td>FALSE</td>
<td>TRUE</td>
<td>HWPWUP_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="odd">
<td>HwPwUp_TMFTestStart_Cnt_M_lgc</td>
<td>boolean</td>
<td>FALSE</td>
<td>TRUE</td>
<td>HWPWUP_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="even">
<td>HwPwUp_PwrDiscBTestStart_Cnt_M_lgc</td>
<td>boolean</td>
<td>FALSE</td>
<td>TRUE</td>
<td>HWPWUP_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="odd">
<td>HwPwUp_MtrDrvrInitStart_Cnt_M_lgc</td>
<td>boolean</td>
<td>FALSE</td>
<td>TRUE</td>
<td>HWPWUP_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
</tbody>
</table>

### User defined typedef definition/declaration 

This section documents any user types uniquely used for the module.

<table>
<colgroup>
<col style="width: 28%" />
<col style="width: 33%" />
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
<td>PowerUpSequenceType</td>
<td><p>PWRUP_PWRDISCSTEPA = 0</p>
<p>PWRUP_TMFINIT = 1</p>
<p>PWRUP_PWRDISCSTEPB = 2</p>
<p>PWRUP_MTRDRIVERINIT = 3</p>
<p>PWRUP_WARMINITCOMPLETE = 4</p>
<p>PWRUP_RUN = 5</p>
<p>PWRUP_DISABLE = 6</p></td>
<td>uint8</td>
<td>0</td>
<td>6</td>
</tr>
</tbody>
</table>

# Constant Data Dictionary

## Calibration Constants

This section lists the calibrations used by the module. For details on
calibration constants, refer to the Data Dictionary for the application.

| Constant Name |
|---------------|
| none          |

## Program(fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

| Constant Name              | Resolution | Units  | Value        |
|----------------------------|------------|--------|--------------|
| D_PWRDISCSTEPAMASK_CNT_U16 | 1          | Counts | 0x0001       |
| D_PWRDISCSTEPBMASK_CNT_U16 | 1          | Counts | 0x0004       |
| D_PGMSPECMASK_CNT_U16      | 1          | Counts | configurable |

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

| Constant Name |
|---------------|
| None          |

### Module specific Lookup Tables Constants

| Constant Name | Resolution | Value | Software Segment |
|---------------|------------|-------|------------------|
| None          |            |       |                  |

#  Functions/Macros used by the Sub-Modules 

## Library Functions / Macros 

The library and functions / Macros that are called by the various sub
modules are identified below,

1.  None

## Data Hiding Functions

1.  Rte_Call_MilestoneRqst_WarmInitMilestoneComplete

2.  Rte_Call_MilestoneRqst_WarmInitMilestoneNotComplete

## Global Functions/Macros Defined by this Module

None

# Software Module Implementation

## Runtime Environment (RTE) Initial Values

This section lists the initial values of data written by this module but
controlled by the RTE. After RTE initialization, the data in this table
will contain these values.

| Data                                       | Value |
|--------------------------------------------|-------|
| Rte_InitValue_MtrDrvrInitComplete_Cnt_lgc  | FALSE |
| Rte_InitValue_MtrDrvrInitStart_Cnt_lgc     | FALSE |
| Rte_InitValue_PwrDiscATestComplete_Cnt_lgc | FALSE |
| Rte_InitValue_PwrDiscATestStart_Cnt_lgc    | FALSE |
| Rte_InitValue_PwrDiscBTestComplete_Cnt_lgc | FALSE |
| Rte_InitValue_PwrDiscBTestStart_Cnt_lgc    | FALSE |
| Rte_InitValue_TMFTestComplete_Cnt_lgc      | FALSE |
| Rte_InitValue_TMFTestStart_Cnt_lgc         | FALSE |

## Initialization Functions

None

##  Periodic Functions

### Per: \_Per1

#### Design Rationale

None

#### Program Flow Start

Rte_Call_HwPwUp_Per1_CP0_CheckpointReached()

#### Store Module Inputs to Local copies

PwrDiscATestComplete_Cnt_T_lgc =
Rte_IRead_HwPwUp_Per1_PwrDiscATestComplete_Cnt_lgc()

TMFTestComplete_Cnt_T_lgc =
Rte_IRead_HwPwUp_Per1_TMFTestComplete_Cnt_lgc()

PwrDiscBTestComplete_Cnt_T_lgc =
Rte_IRead_HwPwUp_Per1_PwrDiscBTestComplete_Cnt_lgc()

MtrDrvrInitComplete_Cnt_T_lgc =
Rte_IRead_HwPwUp_Per1_MtrDrvrInitComplete_Cnt_lgc()

#### Process State Machine

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/HwPwUp/doc/mediax/media/image2.emf)

#### Store Local copy of outputs into Module Outputs

Rte_IWrite_HwPwUp_Per1_PwrDiscATestStart_Cnt_lgc(HwPwUp_PwrDiscATestStart_Cnt_M_lgc)

Rte_IWrite_HwPwUp_Per1_TMFTestStart_Cnt_lgc(HwPwUp_TMFTestStart_Cnt_M_lgc)

Rte_IWrite_HwPwUp_Per1_PwrDiscBTestStart_Cnt_lgc(HwPwUp_PwrDiscBTestStart_Cnt_M_lgc)

Rte_IWrite_HwPwUp_Per1_MtrDrvrInitStart_Cnt_lgc(HwPwUp_MtrDrvrInitStart_Cnt_M_lgc)

#### Program Flow End

Rte_Call_HwPwUp_Per1_CP1_CheckpointReached()

##  Fault Recovery Functions

None

## Shutdown Functions

None

## Interrupt Functions

None

## Serial Communication Functions

None

## Transition Functions

### Trns: \_Trns1

#### Design Rationale

None

#### Program Flow Start

N/A

#### Store Module Inputs to Local copies

None

#### Reset State Machine and Outputs

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/HwPwUp/doc/mediax/media/image3.emf)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

N/A

### Trns: \_Trns2

#### Design Rationale

None

#### Program Flow Start

N/A

#### Store Module Inputs to Local copies

None

#### Set Power Up State

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/HwPwUp/doc/mediax/media/image4.emf)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

N/A

##  

# Execution Requirements

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

| Function Name | Calling Frequency | System State(s) in which the function is called |
|--------------------------|-----------------|------------------------------|
| HwPwUp_Per1   | 2 ms              | ALL                                             |
| HwPwUp_Trns1  | On Event          | On Entering WARMINIT, On Leaving DISABLE        |
| HwPwUp_Trns2  | On Event          | On Entering DISABLE                             |

## Execution Requirements for Serial Communication Functions 

| Function Name | Sub-Module called by (Serial Comm Function Name) |
|---------------|--------------------------------------------------|
| None          |                                                  |

#  [section-2]

#  Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

| Name of Sub Module | Software Segment                  |
|--------------------|-----------------------------------|
| HwPwUp_Per1        | RTE_START_SEC_AP_HWPWUP_APPL_CODE |
| HwPwUp_Trns1       | RTE_START_SEC_AP_HWPWUP_APPL_CODE |
| HwPwUp_Trns2       | RTE_START_SEC_AP_HWPWUP_APPL_CODE |

##  [section-3]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

| Name of Sub Module | Software Segment |
|--------------------|------------------|
| None               |                  |

#  [section-4]

#  Known Issues / Limitations With Design

1.  None

#  Revision Control Log

|             |            |                                                                               |            |                     |
|------|------|--------------------------------------------|---------|---------|
| **Item \#** | **Rev \#** | **Change Description**                                                        | **Date**   | **Author Initials** |
| 1           | 1.0        | Initial Version (FDD 13B v001)                                                | 11-Sep-12  | OT                  |
| 2           | 2.0        | UTP Updates                                                                   | 17-Sep-12  | OT                  |
| 3           | 3.0        | Added checkpoints and memmap software segment is updated for static variables | 29-Sep-12  | Selva               |
| 4           | 4.0        | Anomaly 3912 – fixed writing outputs in all branches                          | 24-Oct-12  | OT                  |
| 5           | 5.0        | Changed k_PgmSpecMask_Cnt_u16 to D_PGMSPECMASK_CNT_U16 (configurable)         | 08-Nov-12  | JJW                 |
| 6           | 6.0        | Updated to FDD V003                                                           | 14-Mar-13  | SP                  |
| 8           | 8.0        | Updated to FDD v005                                                           | 04-June-14 | Selva               |

{% endraw %}