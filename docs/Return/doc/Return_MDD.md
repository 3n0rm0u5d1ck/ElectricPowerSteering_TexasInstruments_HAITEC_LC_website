---
layout: default
title: Return_MDD
nav_order: 2
parent: Return 
---
{% raw %}
# Module -- Return [module----return]

# High-Level Description

This function uses the Absolute Hand Wheel position, Hand Wheel Torque,
Hand Wheel Velocity and Vehicle Speed to derive the desired Return
Torque command.

# Figures

## Component Diagram

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/Return/doc/mediax/media/image1.png"
style="width:3.05208in;height:3.99097in" />

None

### Diagram – \_L5_Per

This diagram describes the functional characteristics and data flow of a
given function.

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/Return/doc/mediax/media/image2.emf)

#  Module Inputs and Outputs

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

(Note: Full variable names required in table.)

(Note: All global variables including End Of Line data used should be
shown here)

| Module Inputs (Global Variable Name) | Module Outputs (Global Variable Name) |
|----------------------------------|--------------------------------------|
| HandwheelVel_HwRadpS_f32             | ReturnCmd_MtrNm_f32                   |
| HandwheelAuthority_Uls_f32           |                                       |
| HandwheelPosition_HwDeg_f32          |                                       |
| HwTorque_HwNm_f32                    |                                       |
| VehicleSpeed_Kph_f32                 |                                       |
| SrlComSvcDft_Cnt_b32                 |                                       |
| ReturnDDFactor_Uls_f32               |                                       |
| PAReturnSclFct_Uls_f32               |                                       |
| Return Offset_HwDeg_f32              |                                       |
| AssistMechTempEst_DegC_f32           |                                       |
| DefeatReturnSvc_Cnt_lgc              |                                       |

## Module Internal Variables

This section identifies the name, range and resolutions for module
specific data created by this module. If there are no range restrictions
on the variable, the term “FULL” is placed into the table for legal
range.

(Note: If no module specific variables are used by the design, place the
text “None” in the first Variable Name cell in the table)

<table style="width:100%;">
<colgroup>
<col style="width: 35%" />
<col style="width: 13%" />
<col style="width: 13%" />
<col style="width: 12%" />
<col style="width: 24%" />
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
<td>CurrentOffset_HwDeg_M_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td>20</td>
<td>RETURN_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>CrntHandWheelAthScl_Uls_M_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td>1</td>
<td>RETURN_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>HwPosReturnCmd _MtrNm_D_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td>0.5</td>
<td>RETURN_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>HwTrqReturnScl_Uls _D_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td>1</td>
<td>RETURN_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>HwVelReturnScl_Uls _D_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td>50</td>
<td>RETURN_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>TempReturnScl_Uls_D_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td>10</td>
<td>RETURN_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>AbsHwPosReturn_HwDeg_D_u12p4</td>
<td>0.0625</td>
<td>0</td>
<td>1640</td>
<td>RETURN_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td>SgnHwPosReturn_HwDeg_D_f32</td>
<td>Single Precision Float</td>
<td>-1</td>
<td>1</td>
<td>RETURN_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>RtrnBasicReturn_MtrNm_D_f32</td>
<td>SinglePrecisionFloating point</td>
<td>-10</td>
<td>10</td>
<td>RETURN_START_SEC_VAR_CLEARED_32</td>
</tr>
</tbody>
</table>

### User defined typedef definition/declaration 

This section documents any user types uniquely used for the module.

| Variable Name | Typedef Name | Storage Type | Safety Critical Classification |
|---------------|--------------|--------------|--------------------------------|
| None          |              |              |                                |

# Constant Data Dictionary

## Calibration Constants

This section lists the calibrations used by the module. For details on
calibration constants, refer to the Data Dictionary for the application.

(Note: If no calibrations are used by the design, place the text “None”
in the first location in the table)

| Constant Name                       |
|-------------------------------------|
| t_ReturnVSpdTblBS_Kph_u9p7          |
| t2_ReturnPosTblXM_HwDeg_u12p4       |
| t2_ReturnPosTblYM_MtrNm_u5p11       |
| t2_ReturnSclTrqTblXM_HwNm_T_u8p8    |
| t2_ReturnSclTrqTblYM_Uls_u8p8       |
| t2_ReturnSclVelTblXM_HwRadpS_T_u7p9 |
| t2_ReturnSclVelTblYM_Uls_u8p8       |
| k_RtnOffsetSlew_HwDegpS_f32         |
| k_RtnOffsetRange_HWDeg_f32          |
| t_ReturnTempScaleXTbl_DegC_s11p4    |
| t_ReturnTempScaleSclYTbl_Uls_u8p8   |
| t_HWAuthRetScl_X_Uls_u8p8           |
| t_HWAuth RetScl_Y_Uls_u9p7          |
| k_RtnHWAuthSlew_UlspS_f32           |
| k_RtnLimit_MtrNm_f32                |

## Program(fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

| Constant Name | Resolution | Value |
|---------------|------------|-------|
|               |            |       |
|               |            |       |

#### Note: RtnLoopTime depends on the rate of the periodic function. [note-rtnlooptime-depends-on-the-rate-of-the-periodic-function.]

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

| Constant Name                 |
|-------------------------------|
| BC_RETURN_FAULTINJECTIONPOINT |
| STD_ON                        |
| FLTINJ_RETURN                 |
| D_2MS_SEC_F32                 |

### Module specific Lookup Tables Constants

(This is for lookup tables (arrays) with fixed values, same name as
other tables)

| Constant Name | Resolution | Value | Software Segment |
|---------------|------------|-------|------------------|
|               |            |       |                  |

# Software Module Implementation

## Initialization Functions

### Init: \_L5_Init()

#### Design Rationale

None

#### Module Outputs

None

#### Module Internal 

None

##  Periodic Functions

### Per: \_L5_Per

#### Design Rationale

None

#### Program Flow Start

Rte_Call_Return_Per1_CP0_CheckpointReached()

#### Store Module Inputs to Local copies

HwVel_HwRadpS_T_f32 = Rte_IRead_Return_Per1_HandwheelVel_HwRadpS_f32 ()

FinHwPosAuth_Uls_T_f32 =
Rte_IRead_Return_Per1_HandwheelAuthority_Uls_f32 ()

FinHwPos_HwDeg_T_f32 = Rte_IRead_Return_Per1_HandwheelPosition_HwDeg_f32
()

HwTrq_HwNm_T_f32 = Rte_IRead_Return_Per1_HwTorque_HwNm_f32 ()

DrvDynSclFct_Uls_T_f32 = Rte_IRead_Return_Per1_ReturnDDFactor_Uls_f32()

PrkAstSclFct_Uls_T_f32 = Rte_IRead_Return_Per1_PAReturnSclFct_Uls_f32 ()

AssistMechTempEst_T_DegC_f32 =
Rte_IRead_Return_Per1_AssistMechTempEst_DegC_f32()

ReturnOffset_HwDeg_T_f32 =
Rte_IRead_Return_Per1_ReturnOffset_HwDeg_f32()

VehSpd_Kph_T_f32 = Rte_IRead_Return_Per1_VehSpd_Kph_f32 ()

DiagStsHwPosDis_Cnt_T_lgc = Rte_IRead_Return_Per1\_
DiagStsHwPosDis_Cnt_lgc ()

DefeatReturnSvc_Cnt_T_lgc =
Rte_IRead_Return_Per1_DefeatReturnSvc_Cnt_lgc()

VehSpd_Kph_T_u9p7 = FPM_FloatToFixed_m(VehSpd_Kph_T_f32,
u9p7_T)FinHwPosAuth_Uls_T_u8p8 =
FPM_FloatToFixed_m(FinHwPosAuth_Uls_T_f32, u8p8_T)

FinHwPos_HwDeg_T_s11p4 = FPM_FloatToFixed_m(FinHwPos_HwDeg_T_f32,
s11p4_T)

HwTrq_HwNm_T_s7p8 = FPM_FloatToFixed_m(HwTrq_HwNm_T_f32, s7p8_T)

HwVel_HwRadpS_T_s6p9 = FPM_FloatToFixed_m(HwVel_HwRadpS_T_f32, s6p9_T)

AssistMechTempEst_DegC_T_s11p4 =
FPM_FloatToFixed_m(AssistMechTempEst_DegC_f32, s11p4_T)

Local Variables:

HwVel_HwRadpS_T_f32

FinHwPosAuth_Uls_T_f32

FinHwPos_HwDeg_T_f32

HwTrq_HwNm_T_f32

VehSpd_Kph_T_f32

VehSpd_Kph_T_u9p7

FinHwPos_HwDeg_T_s11p4

HwTrq_HwNm_T_s7p8

HwVel_HwRadpS_T_s6p9

HwPosReturnCmd_MtrNm_T_u5p11

HwPosReturnCmd_MtrNm_T_f32

HwTrqReturnScl_Uls_T_u8p8

HwTrqReturnScl_Uls_T_f32

HwVelReturnScl_Uls_T_u8p8

HwVelReturnScl_Uls_T_f32

ReturnCmd_MtrNm_T_f32

DrvDynSclFct_Uls_T_f32

PrkAstSclFct_Uls_T_f32

AssistMechTempEst_T_DegC_f32

ReturnOffset_HwDeg_T_f32

FinHwPosAuth_Uls_T_u8p8

AssistMechTempEst_DegC_T_s11p4

TempReturnScl_Uls_T_u8p8

TempReturnScl_Uls_f32

ScaledReturn_MtrNm_f32

HandWheelAthScl_Pct_T_u10p6

CrntHandWheelAthScl_Uls_f32

OffsetDiff_HwDeg_T_u9p7

OffsetDiff_HwDeg_T_u10p6

HandWheelAthScl_Uls_T_u10p6

DiagStsHwPosDis_Cnt_T_lgc

EOLRtnRange_MtrNm_T_f32

HwPosReturnCmd_MtrNm_T_f32

CurrentOffset_HwDeg_T_s11p4

HandWheelAthScl_Uls_T_f32

DefeatReturnSvc_Cnt_T_lgc

#### Determine Return Command

##### 

##### Input Conditioning [input-conditioning]

##### ![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/Return/doc/mediax/media/image3.emf) [section-1]

#####  [section-2]

##### Hand Wheel Position Return Command

The return command is determined as a function of Hand Wheel Position
and Vehicle Speed.

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/Return/doc/mediax/media/image4.emf)

##### Hand Wheel Torque Return Multiplier

The return command is scaled between 0 and 100 percent as a function of
Hand Wheel Torque and Vehicle Speed.

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/Return/doc/mediax/media/image5.emf)

##### Hand Wheel Velocity Return Multiplier

The return command is scaled between 0 and 100 percent as a function of
Hand Wheel Velocity and Vehicle Speed.

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/Return/doc/mediax/media/image6.emf)

##### Calculate Temperature Dependant Return Multiplier

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/Return/doc/mediax/media/image7.emf)

##### Return Scale [return-scale]

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/Return/doc/mediax/media/image8.emf)

##### Calculate Return Torque

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/Return/doc/mediax/media/image9.emf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/Return/doc/mediax/media/image10.emf)

#### Store Local copy of outputs into Module Outputs

Rte_IWrite_Return_Per1_ReturnCmd_MtrNm_f32(ReturnCmd_MtrNm_T_f32)

HwPosReturnCmd_MtrNm_D_f32 = HwPosReturnCmd_MtrNm_T_f32

HwTrqReturnScl_Uls_D_f32 = HwTrqReturnScl_Uls_T_f32

HwVelReturnScl_Uls_D_f32 = HwVelReturnScl_Uls_T_f32

TempReturnScl_Uls_D_f32 = TempReturnScl_Uls_f32

#### Program Flow End

Rte_Call_Return_Per1_CP1_CheckpointReached()

##  Fault Recovery Functions

None

## Shutdown Functions

None

## Interrupt Functions

None

## Serial Communication Functions

None

## Local Function/Macro Definitions

None

#  Execution Requirements

## Execution Sequence of the Module

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

| Function Name | Task List | Calling Frequency | System State(s) in which the function is called |
|------------------|------------------|------------------|------------------|
| \_L5_Per()    |           | 2ms               | All                                             |

## Execution Requirements for Serial Communication Functions 

| Function Name | Sub-Module called by (Serial Comm Function Name) |
|---------------|--------------------------------------------------|
| None          |                                                  |

#  [section-3]

#  Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

| Name of Sub Module | Software Segment        |
|--------------------|-------------------------|
| \_L5_Per()         | RTE_AP_RETURN_APPL_CODE |

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

| **Item \#** | **Rev \#** | **Change Description**                                                                                                             | **Date**    | **Author Initials** |
|------|--------|------------------------------------------|---------|---------|
| 1           | 1.0        | Initial release                                                                                                                    | 16MAY11     | SAH                 |
| 2           | 2          | Apply scale factors from driving-dynamics and parking-assist. Replace computed handwheel velocity with global input.               | 01-Jun-11   | YY                  |
| 3           | 3          | Updated for FDD \#SF-02                                                                                                            | 17_Nov_11   | M. Story            |
| 4           | 4          | Fixed Macro Names                                                                                                                  | 29 Nov11    | M. Story            |
| 5           | 5          | Version 5 did not get checked in properly – so changes were lost and are in version 6                                              | 03Dec2011   | SMW                 |
| 6           | 6          | Updated calibration sign for temperature (need to be signed) and also update global input reads to match latest component template | 05Dec11     | SMW                 |
| 8           | 8          | Updated Globals based on UTP issue                                                                                                 | 07Dec11     | M. Story            |
| 9           | 9          | Corrected display variable assignments                                                                                             | 21Dec11     | M. Story            |
| 10          | 10         | Changed ReturnRange to float32 from Uint16                                                                                         | 04PR12      | M. Story            |
| 11          | 11         | Added FLTINJ and some updates as per SF02 Ver004                                                                                   | 10May12     | NRAR                |
| 12          | 12         | Anom 3317 fix for RateLimiter scaling issue                                                                                        | 16 May 12   | NRAR                |
| 13          | 13         | Move EOLRtnRange_MtrNm_f32 from EEPROM to flash, adding k_RtnLimit_MtrNm_f32CR5873                                                 | 20July12    | BDO                 |
| 14          | 14         | Added checkpoints and memmap software segment is updated for static variables                                                      | 23-Sep-2012 | Selva               |
| 15          | 15         | Corrected anomaly 4893                                                                                                             | 27-Apr-13   | KJS                 |
| 16          | 16         | Updated to SF-02 V 006                                                                                                             | 23-May-13   | SP                  |

{% endraw %}