---
layout: default
title: Assist_Sum_Limit_CurrentMode_MDD
nav_order: 1
parent: Assist Limi 
---
{% raw %}
# Module –  [module]

# High-Level Description

This module combines and limits the various assist command signals from
EPS modules. It puts out several torque commands from different points
in the summation and limiting process.

# Figures

## Component Diagram

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/AstLmt_CM/doc/mediax/media/image2.png"
style="width:2.91667in;height:4.1875in" />

#  Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

| Module Inputs               | Module Outputs |                              |
|-----------------------------------|--|------------------------------------|
| AssistCmd_MtrNm_f32         |                | LimitPercentFiltered_Uls_f32 |
| AssistEOTDamping_MtrNm_f32  |                |                              |
| AssistEOTGain_Uls_f32       |                |                              |
| AssistEOTLimit_MtrNm_f32    |                | PreLimitForStall_MtrNm_f32   |
|                             |                | PreLimitTorque_MtrNm_f32     |
| AssistStallLimit_MtrNm_f32  |                | SumLimTrqCmd_MtrNm_T_f32     |
| AssistVehSpdLimit_MtrNm_f32 |                | TrqLimitMin_MtrNm_f32        |
| CombinedDamping_MtrNm_f32   |                |                              |
| DefeatLimitService_Cnt_lgc  |                |                              |
|                             |                |                              |
| LimitedReturn_MtrNm_f32     |                |                              |
| LrnPnCtrCCDisable_Cnt_lgc   |                |                              |
| LrnPnCtrEnable_Cnt_lgc      |                |                              |
| LrnPnCtrTCmd_MtrNm_f32      |                |                              |
|                             |                |                              |
| OpTrqOvr_MtrNm_f32          |                |                              |
| OutputRampMult_Uls_f32      |                |                              |
| PosServCCDisable_Cnt_lgc    |                |                              |
| PowerLimitPerc_Uls_f32      |                |                              |
| PrkAssistCmd_MtrNm_f32      |                |                              |
| PullCompCmd_MtrNm_f32       |                |                              |
| ThermalLimitPerc_Uls_f32    |                |                              |
| ThermalLimit_MtrNm_f32      |                |                              |
| VehSpd_Kph_f32              |                |                              |
| WheelImbalanceCmd_MtrNm_f32 |                |                              |
| TSMitCommand_MtrNm_f32      |                |                              |

## Module Internal Variables

This section identifies the name, range and resolutions for module
specific data created by this module. If there are no range restrictions
on the variable, the term “FULL” is placed into the table for legal
range.

<table>
<colgroup>
<col style="width: 31%" />
<col style="width: 15%" />
<col style="width: 13%" />
<col style="width: 13%" />
<col style="width: 26%" />
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
<td>AstLmt_ManualTrqCmd_MtrNm_M_f32</td>
<td>Single Precision Float</td>
<td>-16</td>
<td>15.9995</td>
<td>ASTLMT_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>AstLmt_ManualTrqCmdEn_Cnt_M_lgc</td>
<td>n/a</td>
<td>FALSE</td>
<td>TRUE</td>
<td>ASTLMT_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="odd">
<td>AstLmt_SteeringAsstDefeat_Cnt_M_lgc</td>
<td>n/a</td>
<td>FALSE</td>
<td>TRUE</td>
<td>ASTLMT_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
</tbody>
</table>

### User defined typedef definition/declaration 

This section documents any user types uniquely used for the module.

<table>
<colgroup>
<col style="width: 37%" />
<col style="width: 24%" />
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
<td>None</td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

# Constant Data Dictionary

## Calibration Constants

This section lists the calibrations used by the module. For details on
calibration constants, refer to the Data Dictionary for the application.

| Constant Name                |
|------------------------------|
| k_SumLimPlCmpLimit_MtrNm_f32 |
|                              |

## Program(fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

| Constant Name | Resolution | Units | Value |
|---------------|------------|-------|-------|
| None          |            |       |       |

####  [section]

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

| Constant Name              |
|----------------------------|
| D_ZERO_ULS_F32             |
| D_ONE_ULS_F32              |
| D_MTRTRQCMDLOLMT_MTRNM_F32 |
| D_MTRTRQCMDHILMT_MTRNM_F32 |
| FLT_EPSILON                |

### Module specific Lookup Tables Constants

| Constant Name | Resolution | Value | Software Segment |
|---------------|------------|-------|------------------|
| None          |            |       |                  |

#  Functions/Macros used by the Sub-Modules 

## Library Functions / Macros 

The library and functions / Macros that are called by the various sub
modules are identified below,

1.  Abs_f32_m

2.  Sign_f32_m

3.  Min_m

4.  Max_m

5.  Limit_m

## Data Hiding Functions

1.  Rte_Call_SteeringAsstDefeat_WriteBlock

2.  Rte_Pim_SteerAsstDefeat

3.  Rte_Call_AstLmt_Per1_CP0_CheckpointReached

4.  Rte_Call_AstLmt_Per1_CP1_CheckpointReached

## Global Functions/Macros Defined by this Module

None

## Local Functions/Macros Used by this MDD only

None

# Software Module Implementation

## Runtime Environment (RTE) Initial Values

This section lists the initial values of data written by this module but
controlled by the RTE. After RTE initialization, the data in this table
will contain these values.

| Data                                       | Value |
|--------------------------------------------|-------|
| Rte_InitValue_AssistCmd_MtrNm_f32          | 0     |
| Rte_InitValue_AssistEOTDamping_MtrNm_f32   | 0     |
| Rte_InitValue_AssistEOTGain_Uls_f32        | 1     |
| Rte_InitValue_AssistEOTLimit_MtrNm_f32     | 8.8   |
| Rte_InitValue_AssistStallLimit_MtrNm_f32   | 8.8   |
| Rte_InitValue_AssistVehSpdLimit_MtrNm_f32  | 8.8   |
| Rte_InitValue_CombinedDamping_MtrNm_f32    | 0     |
| Rte_InitValue_DefeatLimitService_Cnt_lgc   | FALSE |
| Rte_InitValue_LimitPercentFiltered_Uls_f32 | 0     |
| Rte_InitValue_LimitedReturn_MtrNm_f32      | 0     |
| Rte_InitValue_LrnPnCtrCCDisable_Cnt_lgc    | FALSE |
| Rte_InitValue_LrnPnCtrEnable_Cnt_lgc       | FALSE |
| Rte_InitValue_LrnPnCtrTCmd_MtrNm_f32       | 0     |
| Rte_InitValue_OpTrqOvr_MtrNm_f32           | 0     |
| Rte_InitValue_OutputRampMult_Uls_f32       | 0     |
| Rte_InitValue_PosServCCDisable_Cnt_lgc     | FALSE |
| Rte_InitValue_PowerLimitPerc_Uls_f32       | 0     |
| Rte_InitValue_SumLimTrqCmd_MtrNm_f32       | 0     |
| Rte_InitValue_PreLimitForStall_MtrNm_f32   | 0     |
| Rte_InitValue_PreLimitTorque_MtrNm_f32     | 0     |
| Rte_InitValue_PrkAssistCmd_MtrNm_f32       | 0     |
| Rte_InitValue_PullCompCmd_MtrNm_f32        | 0     |
| Rte_InitValue_ThermalLimit_MtrNm_f32       | 8.8   |
| Rte_InitValue_ThermalLimitPerc_Uls_f32     | 0     |
| Rte_InitValue_VehSpd_Kph_f32               | 0     |
| Rte_InitValue_WheelImbalanceCmd_MtrNm_f32  | 0     |

## Initialization Functions

### Init: AstLmt_Init

#### Design Rationale

#### Program Flow Start

N/A

#### Store Module Inputs to Local Copies

N/A

#### (Processing of function)…..

AstLmt_SteeringAsstDefeat_Cnt_M_lgc = \*Rte_Pim_SteerAsstDefeat()

#### Store Local copy of outputs into Module Outputs

N/A

#### Program Flow End

N/A

##  Periodic Functions [periodic-functions]

### Per: \_Per1

#### Design Rationale

While the FDD specifies the LimitPercentFiltered output to be populated
every 10 ms, the overhead required for another periodic function would
be greater than including the single Max_m() macro in the main 2 ms
periodic function.

#### Program Flow Start

Rte_Call_AstLmt_Per1_CP0_CheckpointReached()

#### Store Module Inputs to Local copies

AssistCmd_MtrNm_T_f32 = Rte_IRead_AstLmt_Per1_AssistCmd_MtrNm_f32()

AssistEOTDamping_MtrNm_T_f32 =
Rte_IRead_AstLmt_Per1_AssistEOTDamping_MtrNm_f32()

AssistEOTGain_Uls_T_f32 = Rte_IRead_AstLmt_Per1_AssistEOTGain_Uls_f32()

AssistEOTLimit_MtrNm_T_f32 =
Rte_IRead_AstLmt_Per1_AssistEOTLimit_MtrNm_f32()

AssistStallLimit_MtrNm_T_f32 =
Rte_IRead_AstLmt_Per1_AssistStallLimit_MtrNm_f32()

AssistVehSpdLimit_MtrNm_T_f32 =
Rte_IRead_AstLmt_Per1_AssistVehSpdLimit_MtrNm_f32()

CombinedDamping_MtrNm_T_f32 =
Rte_IRead_AstLmt_Per1_CombinedDamping_MtrNm_f32()

DefeatLimitService_Cnt_T_lgc =
Rte_IRead_AstLmt_Per1_DefeatLimitService_Cnt_lgc()

LimitedReturn_MtrNm_T_f32 =
Rte_IRead_AstLmt_Per1_LimitedReturn_MtrNm_f32()

LrnPnCtrCCDisable_Cnt_T_lgc =
Rte_IRead_AstLmt_Per1_LrnPnCtrCCDisable_Cnt_lgc()

LrnPnCtrEnable_Cnt_T_lgc =
Rte_IRead_AstLmt_Per1_LrnPnCtrEnable_Cnt_lgc()

LrnPnCtrTCmd_MtrNm_T_f32 =
Rte_IRead_AstLmt_Per1_LrnPnCtrTCmd_MtrNm_f32()

OpTrqOvr_MtrNm_T_f32 = Rte_IRead_AstLmt_Per1_OpTrqOvr_MtrNm_f32()

OutputRampMult_Uls_T_f32 =
Rte_IRead_AstLmt_Per1_OutputRampMult_Uls_f32()

PosServCCDisable_Cnt_T_lgc =
Rte_IRead_AstLmt_Per1_PosServCCDisable_Cnt_lgc()

PowerLimitPerc_Uls_T_f32 =
Rte_IRead_AstLmt_Per1_PowerLimitPerc_Uls_f32()

PrkAssistCmd_MtrNm_T_f32 =
Rte_IRead_AstLmt_Per1_PrkAssistCmd_MtrNm_f32()

PullCompCmd_MtrNm_T_f32 = Rte_IRead_AstLmt_Per1_PullCompCmd_MtrNm_f32()

ThermalLimitPerc_Uls_T_f32 =
Rte_IRead_AstLmt_Per1_ThermalLimitPerc_Uls_f32()

ThermalLimit_MtrNm_T_f32 =
Rte_IRead_AstLmt_Per1_ThermalLimit_MtrNm_f32()

VehSpd_Kph_T_f32 = Rte_IRead_AstLmt_Per1_VehSpd_Kph_f32()

WheelImbalanceCmd_MtrNm_T_f32 =
Rte_IRead_AstLmt_Per1_WheelImbalanceCmd_MtrNm_f32()

TSMitCommand_MtrNm_T_f32 =
Rte_IRead_AstLmt_Per1_TSMitCommand_MtrNm_f32()

#### Preconditioning and Command summation

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/AstLmt_CM/doc/mediax/media/image3.emf)

#### Apply Gain and Limit![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/AstLmt_CM/doc/mediax/media/image5.emf)

#### Assist Reduction Level

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/AstLmt_CM/doc/mediax/media/image6.emf)

#### Store Local copy of outputs into Module Outputs

Rte_IWrite_AstLmt_Per1_TrqLimitMin_MtrNm_f32(TrqLimitMin_MtrNm_T_f32)

Rte_IWrite_AstLmt_Per1_LimitPercentFiltered_Uls_f32(LimitPercentFiltered_Uls_T_f32)

Rte_IWrite_AstLmt_Per1_SumLimTrqCmd_MtrNm_f32(SumLimTrqCmd_MtrNm_T_f32)

Rte_IWrite_AstLmt_Per1_PreLimitForStall_MtrNm_f32(PreLimitForStall_MtrNm_T_f32)

Rte_IWrite_AstLmt_Per1_PreLimitTorque_MtrNm_f32(PreLimitTorque_MtrNm_T_f32)

#### Program Flow End

## Rte_Call_AstLmt_Per1_CP1_CheckpointReached() Fault Recovery Functions

None

## Shutdown Functions

None

## Interrupt Functions

None

## Serial Communication Functions

### SCom: AstLmt_SCom_ManualTrqCmd

|                      |                     |                |       |         |          |
|---------------|---------------------------|------------|-------|-------|------|
|                      |                     | Type           | Min   | Max     | UTP Tol. |
| **Arguments Passed** | EnableManualCtrl    | boolean        | FALSE | TRUE    |          |
|                      | MtrTrqCmd_MtrNm_f32 | float32        | -16   | 15.9995 |          |
| **Return Value**     | RetCode             | Std_ReturnType | 0     | 34      | 0        |

#### Design Rationale

None

#### Program Flow Start

N/A

#### Store Module Inputs to Local copies

Rte_Read_VehSpd_Kph_f32(&VehSpd_Kph_T_f32)

#### Process Manual Torque Command

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/AstLmt_CM/doc/mediax/media/image7.emf)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

N/A

### SCom: AstLmt_Scom_GetSteeringAssistDefeat

|                      |                            |           |       |      |          |
|---------------|---------------------------|------------|-------|-------|------|
|                      |                            | Type      | Min   | Max  | UTP Tol. |
| **Arguments Passed** | SteeringAsstDefeat_Cnt_lgc | \*boolean | FALSE | TRUE |          |
| **Return Value**     | none                       |           |       |      |          |

#### Design Rationale

None

#### Program Flow Start

N/A

#### Store Module Inputs to Local copies

N/A

#### Get Steering Assist Defeat Status

\*SteeringAsstDefeat_Cnt_lgc = \*Rte_Pim_SteerAsstDefeat()

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

N/A

### SCom: AstLmt_Scom_SetSteeringAssistDefeat

|                      |                            |         |       |      |          |
|---------------|---------------------------|------------|-------|-------|------|
|                      |                            | Type    | Min   | Max  | UTP Tol. |
| **Arguments Passed** | SteeringAsstDefeat_Cnt_lgc | boolean | FALSE | TRUE |          |
| **Return Value**     | none                       |         |       |      |          |

#### Design Rationale

None

#### Program Flow Start

N/A

#### Store Module Inputs to Local copies

N/A

#### Get Steering Assist Defeat Status

\*Rte_Pim_SteerAsstDefeat() = SteeringAsstDefeat_Cnt_lgc

Rte_Call_SteeringAsstDefeat_WriteBlock(NULL_PTR)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

N/A

##  

# Execution Requirements

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

| Function Name | Calling Frequency                  | System State(s) in which the function is called |
|--------------------------|-----------------|------------------------------|
| AstLmt_Init   | Executed Once after RTE is started | ColdInit                                        |
| AstLmt_Per1   | 2 ms                               | ALL                                             |

## Execution Requirements for Serial Communication Functions 

| Function Name                       | Sub-Module called by (Serial Comm Function Name)                     |
|-----------------------------|-------------------------------------------|
| AstLmt_Scom_ManualTrqCmd            | Server invocation for OperationPrototype \<ManualTrqCmd\>            |
| AstLmt_Scom_GetSteeringAssistDefeat | Server invocation for OperationPrototype \<GetSteeringAssistDefeat\> |
| AstLmt_Scom_SetSteeringAssistDefeat | Server invocation for OperationPrototype \<SetSteeringAssistDefeat\> |

#  [section-2]

#  Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

| Name of Sub Module                  | Software Segment                  |
|-------------------------------------|-----------------------------------|
| AstLmt_Init                         | RTE_START_SEC_AP_ASTLMT_APPL_CODE |
| AstLmt_Per1                         | RTE_START_SEC_AP_ASTLMT_APPL_CODE |
| AstLmt_Scom_ManualTrqCmd            | RTE_START_SEC_AP_ASTLMT_APPL_CODE |
| AstLmt_Scom_GetSteeringAssistDefeat | RTE_START_SEC_AP_ASTLMT_APPL_CODE |
| AstLmt_Scom_SetSteeringAssistDefeat | RTE_START_SEC_AP_ASTLMT_APPL_CODE |

##  [section-3]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

| Name of Sub Module | Software Segment |
|--------------------|------------------|
| None               |                  |

#  [section-4]

#  Known Issues / Limitations With Design

1.  INLINE functions defined in GlobalMacro.h are not unit tested.

#  Revision Control Log

<table style="width:100%;">
<colgroup>
<col style="width: 6%" />
<col style="width: 6%" />
<col style="width: 64%" />
<col style="width: 11%" />
<col style="width: 11%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Item #</strong></td>
<td><strong>Rev #</strong></td>
<td><strong>Change Description</strong></td>
<td><strong>Date</strong></td>
<td><strong>Author Initials</strong></td>
</tr>
<tr class="even">
<td>1</td>
<td>1.0</td>
<td>Initial Version (SF-04B v001)</td>
<td>07-Aug-12</td>
<td>OT</td>
</tr>
<tr class="odd">
<td>2</td>
<td>2.0</td>
<td>Fixed UTP Issues (global constants)</td>
<td>08-Aug-12</td>
<td>OT</td>
</tr>
<tr class="even">
<td>3</td>
<td>3.0</td>
<td>Added ManualTrqCmd service</td>
<td>16-Aug-12</td>
<td>OT</td>
</tr>
<tr class="odd">
<td>4</td>
<td>4.0</td>
<td>Replaced HwtrqPolarity with assistassembley polarity</td>
<td>11-SEP-12</td>
<td>SAH</td>
</tr>
<tr class="even">
<td>5</td>
<td>5.0</td>
<td><p>- Removed Inputs: MRFMtrVel, AssistAssembly_Polarity,
Assist_PowerLimit</p>
<p>- Removed Output: PostLimit_ForAssistSumCC</p>
<p>- Renamed Output: PreLimit_for_Power to SumLimTrqCmd_MtrNm</p>
<p>- Removed calibration: k_OvrSpdMtrTrq2QLmt_MtrNm</p></td>
<td>01-Dec-12</td>
<td>Selva</td>
</tr>
<tr class="odd">
<td>6</td>
<td>6.0</td>
<td>Updated output limit on sumlimtrqcmd from 0 to -8.8 to match FDD
data dictionary</td>
<td>14-Jan-13</td>
<td>SAH</td>
</tr>
<tr class="even">
<td>7</td>
<td>7.0</td>
<td>Updates to add steering assist defeat</td>
<td>03-Jun-13</td>
<td>VK</td>
</tr>
<tr class="odd">
<td>8</td>
<td>8.0</td>
<td>Update to v4 of FDD. Added new outputs and matched the naming
conventions</td>
<td>23-Nov-13</td>
<td>Selva</td>
</tr>
<tr class="even">
<td>9</td>
<td>9.0</td>
<td>Corrected range of ‘AstLmt_ManualTrqCmd_MtrNm_M_f32’</td>
<td>10-Dec-13</td>
<td>SR</td>
</tr>
<tr class="odd">
<td>10</td>
<td>10.0</td>
<td>Updated to SF-04B v5, modified PreLimitForStall, AssistCmd, and
AbsLimitedTorque</td>
<td>12-June-06</td>
<td>VT</td>
</tr>
<tr class="even">
<td>11</td>
<td>11.0</td>
<td>Unit Testing Findings fixed</td>
<td>11-July-14</td>
<td>KPIT-SSK</td>
</tr>
<tr class="odd">
<td>12</td>
<td>13.0</td>
<td>Updated to SF-04B version 006</td>
<td>25-Aug-14</td>
<td>SB</td>
</tr>
</tbody>
</table>

{% endraw %}