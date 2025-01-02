---
layout: default
title: State_Output_Control_MDD
nav_order: 2
parent: State Output Control
---
{% raw %}
# Module – State Output Control [module-state-output-control]

# High-Level Description

This function performs the ramp up and ramp down of the Torque Command.

# Figures

## Diagram – Function Data Sharing

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/StOpCtrl/doc/mediax/media/image1.emf)

###   [section]

# Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

(Note: Full variable names required in table.)

(Note: All global variables including End Of Line data used should be
shown here)

| Module Inputs (Global Variable Name) | Module Outputs (Global Variable Name) |
|----------------------------------|--------------------------------------|
| <s>TrqCmd_MtrNm_f32</s>              | <s>FinalTrqCmd_MtrNm_f32</s>          |
| <s>SrlComSvcDft_Cnt_b32</s>          | OutputRampMult_Uls_f32                |
| DiagRampRate_XpmS_32                 | RampDwnStatusComplete_Cnt_lgc         |
| DiagRampValue_Uls_f32                |                                       |
| OperRampRate_XpmS_f32                |                                       |
| OperRampValue_Uls_f32                |                                       |
| RampSrlComSvcDft_Cnt_lgc             |                                       |
| DiagStsDiagRmpActive_Cnt_lgc         |                                       |

## Module Internal Variables

This section identifies the name, range and resolutions for module
specific data created by this module. If there are no range restrictions
on the variable, the term “FULL” is placed into the table for legal
range.

<table style="width:100%;">
<colgroup>
<col style="width: 41%" />
<col style="width: 12%" />
<col style="width: 13%" />
<col style="width: 13%" />
<col style="width: 18%" />
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
<td><del>AttenFactor_Uls_M_f32</del></td>
<td>Single precision floating point</td>
<td>1.175494351e-038</td>
<td>3.402823466e+038</td>
<td></td>
</tr>
<tr class="even">
<td><del>ActvRampUsr_Cnt_M_u16</del></td>
<td>1</td>
<td>0</td>
<td>16</td>
<td></td>
</tr>
<tr class="odd">
<td>PrevOutputRampMult_Uls_M_f32</td>
<td>Single precision floating point</td>
<td>0</td>
<td>1</td>
<td>STOPCTRL_START_SEC_VAR_NOINIT_32</td>
</tr>
<tr class="even">
<td>PrevTargetRampMult_Uls_M_f32</td>
<td>Single precision floating point</td>
<td>0</td>
<td>1</td>
<td>STOPCTRL_START_SEC_VAR_NOINIT_32</td>
</tr>
<tr class="odd">
<td>PrevRate_XpmS_M_f32</td>
<td>Single precision floating point</td>
<td>0.0001</td>
<td>0.5</td>
<td>STOPCTRL_START_SEC_VAR_NOINIT_32</td>
</tr>
<tr class="even">
<td>RampState_M_Str</td>
<td>RampState_T</td>
<td>See 3.1.1</td>
<td>See 3.1.1</td>
<td>STOPCTRL_START_SEC_VAR_NOINIT_UNSPECIFIED</td>
</tr>
</tbody>
</table>

### User defined typedef definition/declaration 

This section documents any user types uniquely used for the module.

<table>
<colgroup>
<col style="width: 34%" />
<col style="width: 31%" />
<col style="width: 13%" />
<col style="width: 9%" />
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
<td>RampState_T</td>
<td><p>StartTime_mS_u32</p>
<p>Duration_mS_u32</p>
<p>StartVal_Uls_f32</p>
<p>EndVal_Uls_f32</p></td>
<td><p>uint32</p>
<p>uint32</p>
<p>float32</p>
<p>float32</p></td>
<td><p>0</p>
<p>0</p>
<p>0</p>
<p>0</p></td>
<td><p>2^<sup>32</sup>-1</p>
<p>2^<sup>32</sup>-1</p>
<p>1</p>
<p>1</p></td>
</tr>
</tbody>
</table>

# Constant Data Dictionary

## Calibration Constants

This section lists the calibrations used by the module. For details on
calibration constants, refer to the Data Dictionary for the application.

| Constant Name |
|---------------|
|               |

## Program(fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

| Constant Name      | Resolution                      | Value |
|--------------------|---------------------------------|-------|
| D_TWO_MS_U32       | 1                               | 2     |
| D_MAXRAMP_XPMS_F32 | Single precision floating point | 0.5   |

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

| Constant Name |
|---------------|
|               |

###  Module specific Lookup Tables Constants

(This is for lookup tables (arrays) with fixed values, same name as
other tables)

| Constant Name | Resolution | Value | Software Segment |
|---------------|------------|-------|------------------|
| None          |            |       |                  |

## Lookup Table Definitions

# Software Module Implementation

## Initialization Functions

None

## Periodic Functions

### Per: \_Per1

#### Design Rationale

NOTE: For “starttime” calculations there is tendency for underflow and
this is expected in s/w design. So for unittesting, VBA model should be
implemented

such that it handles underflow and behaves like source code design.

#### Program Flow Start

#### Store Module Inputs to Local copies

Rte_Call_StOpCtrl_Per1_CP0_CheckpointReached() OperRampRate_XpmS_T_f32
as float32

OperRampValue_Uls_T_f32 as float32

DiagRampValue_Uls_T_f32 as float32

DiagRampRate_XpmS_T_f32 as float32

DiagStsDiagRmpActive_Cnt_T_lgc as Boolean

RampSrlComSvcDft_Cnt_T_lgc as Boolean

Rate_T_f32 as float32

Target_T_f32 as float32

DiffOutputRampMult_T_f32 as float32

DiffRate_T_f32 as float32

OperRampRate_XpmS_T_f32 = Rte_IRead_StOpCtrl_Per1_OperRampRate_XpmS_f32

OperRampValue_Uls_T_f32 =Rte_Iread_StOpCtrl_Per1_OperRampValue_Uls_f32

DiagRampValue_Uls_T_f32=Rte_Iread_StOpCtrl_Per1_DiagRampValue_Uls_f32

DiagRampRate_XpmS_T_f32=Rte_Iread_StOpCtrl_Per1_DiagRampRate_XpmS_f32

DiagStsDiagRmpActive_Cnt_T_lgc =
Rte_Iread_StOpCtrl_Per1_DiagStsDiagRmpActive_Cnt_lgc

RampSrlComSvcDft_Cnt_T_lgc=
Rte_Iread_StOpCtrl_Per1_RampSrlComSvcDft_Cnt_lgc

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/StOpCtrl/doc/mediax/media/image2.emf)

#### Store Local copy of outputs into Module Outputs

Rte_Iwrite_StOpCtrl_Per1_RampDwnStatusComplete_Cnt_lgc(RampDwnStatusComplete_T_lgc)

Rte_Iwrite_StOpCtrl_Per1_OutputRampMult_Uls_f32(NewOutputRampMult_T_f32)

#### Program Flow End

Rte_Call_StOpCtrl_Per1_CP1_CheckpointReached()

## Fault Recovery Functions

None

## Shutdown Functions

None

## Interrupt Functions

None

## Serial Communication Functions

None

## Local Function/Macro Definitions

### RampLib

| **Function Name**    | RampLib          | Type        | Min | Max |
|----------------------|------------------|-------------|-----|-----|
| **Arguments Passed** | rampState_T_Str  | RampState_T | \*  | \*  |
|                      |                  |             |     |     |
| **Return Value**     | Output_Uls_T_f32 | Float       |     |     |

#### \*Note: For ranges on structure elements check Table 3.1.1 of MDD [note-for-ranges-on-structure-elements-check-table-3.1.1-of-mdd]

#### Description

Rte_Call_SystemTime_DtrmnElapsedTime_mS_u32(rampState_T_Str.StartTime_mS_u32,
&ElapsedRamp_mS_T_u32)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/StOpCtrl/doc/mediax/media/image3.emf)

###  [section-1]

#  Execution Requirements

## Execution Sequence of the Module

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

| Function Name   | Calling Frequency | System State(s) in which the function is called |
|---------------------------|----------------|-----------------------------|
| StOpCtrl_Per1() | 2 ms              | ALL States                                      |
|                 |                   |                                                 |

##  [section-2]

## Execution Requirements for Serial Communication Functions 

| Function Name | Sub-Module called by (Serial Comm Function Name) |
|---------------|--------------------------------------------------|
| None          |                                                  |

#  [section-3]

#  Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

| Name of Sub Module | Software Segment                                                       |
|------------------------------------|------------------------------------|
| StOpCtrl_Per1()    | RTE_START_SEC_AP_STOPCTRL_APPL_CODE RTE_STOP_SEC_AP_STOPCTRL_APPL_CODE |
|                    |                                                                        |

##  [section-4]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 49%" />
</colgroup>
<thead>
<tr class="header">
<th>Name of Sub Module</th>
<th>Software Segment</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>RampLib</td>
<td><p>RTE_START_SEC_AP_STOPCTRL_APPL_CODE</p>
<p>RTE_STOP_SEC_AP_STOPCTRL_APPL_CODE</p></td>
</tr>
</tbody>
</table>

#  Known Issues / Limitations With Design

1.  (Item \#1)

#  Revision Control Log

| **Item \#** | **Rev \#** | **Change Description**                                                        | **Date**  | **Author Initials** |
|------|------|--------------------------------------------|---------|---------|
| 1           | 1.0        | Initial release                                                               | 07-Jun-11 | SAH                 |
| 2           | 2.0        | FDD SF05                                                                      | 5-Jan-12  | NRAR                |
| 3           | 3.0        | Value for D_MAXRAMP_XPMS_F32 is fixed                                         | 6-Jan-12  | NRAR                |
| 4           | 4.0        | DiagStsF1Active_Cnt_lgc is renamed to DiagStsDiagRmpActive_Cnt_lgc            | 12-Jan-12 | NRAR                |
| 5           | 4.0        | PrevRate_XpmS_M_f32 range correction                                          | 23-Jan-12 | NRAR                |
| 6           | 5.0        | Anom \#3272 Ramp output vs. target fix                                        | 13-Aug-12 | BWL                 |
| 7           | 6.0        | Added checkpoints and memmap software segment is updated for static variables | 23-Sep-12 | Selva               |

{% endraw %}