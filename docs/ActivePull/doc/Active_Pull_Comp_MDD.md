---
layout: default
title: Active_Pull_Comp_MDD
nav_order: 1
parent: Active Pull
---
{% raw %}
# Module -- Active Pull Compensation [module----active-pull-compensation]

# High-Level Description

This module corrects for vehicle pull issues by compensation for both
long and short term torque offsets.

# Figures

## Component Diagram

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ActivePull/doc/mediax/media/image1.tiff"
style="width:3.54167in;height:3.54167in" alt="123.tif" />

#  Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

| Module Inputs                 | Module Outputs |                       |
|-------------------------------|----------------|-----------------------|
| HwTorque_HwNm_f32             |                | PullCompCmd_MtrNm_f32 |
| HandwheelPosition_HwDeg_f32   |                |                       |
| HandwheelAuthority_Uls_f32    |                |                       |
| VehicleSpeed_Kph_f32          |                |                       |
| VehicleSpeedValid_Cnt_lgc     |                |                       |
| HandwheelVelocity_HwRadpS_f32 |                |                       |
| SrlComYawRate_DegpS_f32       |                |                       |
| DisableLearning_Cnt_lgc       |                |                       |
| DisableOutput_Cnt_lgc         |                |                       |

## Module Internal Variables

This section identifies the name, range and resolutions for module
specific data created by this module. If there are no range restrictions
on the variable, the term “FULL” is placed into the table for legal
range.

<table>
<colgroup>
<col style="width: 32%" />
<col style="width: 15%" />
<col style="width: 13%" />
<col style="width: 12%" />
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
<td>DecGain_Uls_M_f32</td>
<td>Single Precision Float</td>
<td>0.0000135</td>
<td>0.00054</td>
<td>ACTIVEPULL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>IncGain_Uls_M_f32</td>
<td>Single Precision Float</td>
<td>0.0000135</td>
<td>0.00054</td>
<td>ACTIVEPULL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>LTIntGain_Uls_M_f32</td>
<td>Single Precision Float</td>
<td>0.00001875</td>
<td>0.00045</td>
<td>ACTIVEPULL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>LTWindUpLimit_HwNm_M_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td>4</td>
<td>ACTIVEPULL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>STStepSize_HwNm_M_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td> 20000</td>
<td>ACTIVEPULL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>PullCompStepSize_HwNm_M_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td>0.2</td>
<td>ACTIVEPULL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>ResetPer1_Cnt_M_lgc</td>
<td>n/a</td>
<td>FALSE</td>
<td>TRUE</td>
<td>ACTIVEPULL_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="even">
<td>ResetPer2_Cnt_M_lgc</td>
<td>n/a</td>
<td>FALSE</td>
<td>TRUE</td>
<td>ACTIVEPULL_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="odd">
<td>ResetPer3_Cnt_M_lgc</td>
<td>n/a</td>
<td>FALSE</td>
<td>TRUE</td>
<td>ACTIVEPULL_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="even">
<td>HwTorqueSV_HwNm_M_Str</td>
<td>LPF32KSV_Str</td>
<td>N/A</td>
<td>N/A</td>
<td>ACTIVEPULL_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="odd">
<td>HwTorqueSV_HwNm_M_Str.K_Uls_f32</td>
<td>Float32</td>
<td>0.001255848</td>
<td>0.715390457</td>
<td></td>
</tr>
<tr class="even">
<td>HwTorqueSV_HwNm_M_Str.SV_Uls_f32</td>
<td>Float32</td>
<td>-10</td>
<td>10</td>
<td></td>
</tr>
<tr class="odd">
<td>SrlComYawRateSV_DegpS_M_Str</td>
<td>LPF32KSV_Str</td>
<td>N/A</td>
<td>N/A</td>
<td>ACTIVEPULL_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="even">
<td>SrlComYawRateSV_DegpS_M_Str.K_Uls_f32</td>
<td>Float32</td>
<td>0.001255848</td>
<td>0.715390457</td>
<td></td>
</tr>
<tr class="odd">
<td>SrlComYawRateSV_DegpS_M_Str.SV_Uls_f32</td>
<td>Float32</td>
<td>-128</td>
<td>127.9375</td>
<td></td>
</tr>
<tr class="even">
<td>EnableTime_mS_M_u32</td>
<td>1</td>
<td>0</td>
<td>4294967295</td>
<td>ACTIVEPULL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>EnableLearn_Cnt_M_lgc</td>
<td>n/a</td>
<td>FALSE</td>
<td>TRUE</td>
<td>ACTIVEPULL_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="even">
<td>HwTorqueSTSV_HwNm_M_Str</td>
<td>LPF32KSV_Str</td>
<td>N/A</td>
<td>N/A</td>
<td>ACTIVEPULL_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="odd">
<td>HwTorqueSTSV_HwNm_M_Str.K_Uls_f32</td>
<td>Float32</td>
<td>0.001255848</td>
<td>0.715390457</td>
<td></td>
</tr>
<tr class="even">
<td>HwTorqueSTSV_HwNm_M_Str.SV_Uls_f32</td>
<td>Float32</td>
<td>-10</td>
<td>10</td>
<td></td>
</tr>
<tr class="odd">
<td>STComp_HwNm_M_f32</td>
<td>Single Precision Float</td>
<td>-4</td>
<td>4</td>
<td>ACTIVEPULL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>STOppSignTime_mS_M_u32</td>
<td>1</td>
<td>0</td>
<td>4294967295</td>
<td>ACTIVEPULL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>PullCompCmd_HwNm_M_f32</td>
<td>Single Precision Float</td>
<td>-8.8</td>
<td>8.8</td>
<td>ACTIVEPULL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>LTComp_HwNm_M_f32</td>
<td>Single Precision Float</td>
<td>-4</td>
<td>4</td>
<td>ACTIVEPULL_START_SEC_VAR_SAVED_ZONEH_32</td>
</tr>
<tr class="odd">
<td>HwTorqueLTSV_HwNm_M_Str</td>
<td>LPF32KSV_Str</td>
<td>N/A</td>
<td>N/A</td>
<td>ACTIVEPULL_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="even">
<td>HwTorqueLTSV_HwNm_M_Str.K_Uls_f32</td>
<td>Float32</td>
<td>0.006263487</td>
<td>1</td>
<td></td>
</tr>
<tr class="odd">
<td>HwTorqueLTSV_HwNm_M_Str.SV_Uls_f32</td>
<td>Float32</td>
<td>-14</td>
<td>14</td>
<td></td>
</tr>
<tr class="even">
<td>SComLTComp_HwNm_M_f32</td>
<td>Single Precision Float</td>
<td>-4</td>
<td>4</td>
<td>ACTIVEPULL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>SComLTCompSet_Cnt_M_lgc</td>
<td>n/a</td>
<td>FALSE</td>
<td>TRUE</td>
<td>ACTIVEPULL_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="even">
<td>SComSTComp_HwNm_M_f32</td>
<td>Single Precision Float</td>
<td>-4</td>
<td>4</td>
<td>ACTIVEPULL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>SComSTCompSet_Cnt_M_lgc</td>
<td>n/a</td>
<td>FALSE</td>
<td>TRUE</td>
<td>ACTIVEPULL_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="even">
<td>PrevLTLearnTime_Min_M_u16</td>
<td>1</td>
<td>0</td>
<td>120</td>
<td>ACTIVEPULL_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="odd">
<td>PrevSTLearnTimeInc_Sec_M_u12p4</td>
<td>0.0625</td>
<td>0</td>
<td>200</td>
<td>ACTIVEPULL_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td>PrevSTLearnTimeDec_Sec_M_u12p4</td>
<td>0.0625</td>
<td>0</td>
<td>200</td>
<td>ACTIVEPULL_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="odd">
<td>HwTrqFilt_HwNm_D_f32</td>
<td>Single Precision Float</td>
<td>-10</td>
<td>10</td>
<td>ACTIVEPULL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>YawRateFilt_DegpS_D_f32</td>
<td>Single Precision Float</td>
<td>-128</td>
<td>127.9375</td>
<td>ACTIVEPULL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>STError_HwNm_D_f32</td>
<td>Single Precision Float</td>
<td>-10</td>
<td>10</td>
<td>ACTIVEPULL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>STIntGain_Uls_D_f32</td>
<td>Single Precision Float</td>
<td>0.0000135</td>
<td>0.00054</td>
<td>ACTIVEPULL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>STReset_Cnt_D_lgc</td>
<td>n/a</td>
<td>FALSE</td>
<td>TRUE</td>
<td>ACTIVEPULL_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="even">
<td>LTError_HwNm_D_f32</td>
<td>Single Precision Float</td>
<td>-14</td>
<td>14</td>
<td>ACTIVEPULL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>PrevVehSpd_Kph_M_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td>511</td>
<td>ACTIVEPULL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>VehSpdRate_KphpS_M_f32</td>
<td>Single Precision Float</td>
<td>-5110</td>
<td>5110</td>
<td>ACTIVEPULL_START_SEC_VAR_CLEARED_32</td>
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

| Constant Name                    |
|----------------------------------|
| k_YawRateFilt_Hz_f32             |
| k_HwTrqFilt_Hz_f32               |
| k_STResetHwTrq_HwNm_f32          |
| k_STResetHwPos_HwDeg_f32         |
| k_STResetYawRate_DegpS_f32       |
| k_EnableHwTrqMax_HwNm_f32        |
| k_EnableHwPosMax_HwDeg_f32       |
| k_EnableHwAuthMin_Uls_f32        |
| k_EnableHwVelMax_DegpS_f32       |
| k_EnableVehSpdRateMax_KphpS_f32  |
| k_EnableVehSpdMin_Kph_f32        |
| k_EnableVehSpdMax_Kph_f32        |
| k_EnableYawRateMax_DegpS_f32     |
| k_EnableTime_mS_u32              |
| k_STLimit_HwNm_f32               |
| k_STLearnTimeInc_Sec_f32         |
| k_STLearnTimeDec_Sec_f32         |
| k_STOppSignTime_mS_u32           |
| k_STRampTime_Sec_f32             |
| k_STIntInputLimit_HwNm_f32       |
| k_STFilt_Hz_f32                  |
| k_FiltDeadband_HwNm_f32          |
| k_LTLimit_HwNm_f32               |
| k_LTLearnTime_Min_f32            |
| k_LTFilt_Hz_f32                  |
| k_LTIntInputLimit_HwNm_f32       |
| k_TotalLimit_HwNm_f32            |
| k_HwNmToMtrNm_Uls_f32            |
| t_VehSpdScaleTblX_Kph_u9p7\[4\]  |
| t_VehSpdScaleTblY_Uls_u2p14\[4\] |
| k_OutputMaxRate_HwNmpS_f32       |

The filter constants were derived from the requirements in SF-09 in
conjunction with the following filter analyses. Note that the upper
frequency limits defined in the requirements for some values were not
achievable. The data dictionary reflects the limits of both the
requirements and the software limitations.

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ActivePull/doc/mediax/media/image2.emf)
![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ActivePull/doc/mediax/media/image3.emf)
![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ActivePull/doc/mediax/media/image4.emf)

## Program(fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

| Constant Name                | Resolution             | Units     | Value |
|------------------------------|------------------------|-----------|-------|
| D_MINTOSEC_SECPMIN_F32       | Single Precision Float | SecPerMin | 60    |
| D_STINTSCALER_ULS_F32        | Single Precision Float | Unitless  | 1.35  |
| D_STSAMPLETIME_SEC_F32       | Single Precision Float | Seconds   | 0.002 |
| D_LTINTSCALER_ULS_F32        | Single Precision Float | Unitless  | 1.35  |
| D_LTSAMPLETIME_SEC_F32       | Single Precision Float | Seconds   | 0.1   |
| D_PULLCOMPSAMPLETIME_SEC_F32 | Single Precision Float | Seconds   | 0.002 |

####  [section]

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

| Constant Name              |
|----------------------------|
| D_FALSE_CNT_LGC            |
| D_180OVRPI_ULS_F32         |
| D_2MS_SEC_F32              |
| D_ZERO_ULS_F32             |
| D_MTRTRQCMDLOLMT_MTRNM_F32 |
| D_MTRTRQCMDHILMT_MTRNM_F32 |

### Module specific Lookup Tables Constants

| Constant Name | Resolution | Value | Software Segment |
|---------------|------------|-------|------------------|
| None          |            |       |                  |

#  Functions/Macros used by the Sub-Modules 

## Library Functions / Macros 

The library and functions / Macros that are called by the various sub
modules are identified below,

1.  FPM_FloatToFixed_m

2.  FPM_FixedToFloat_m

3.  LPF_SvUpdate_s16InFixKTrunc_m

4.  Abs_f32_m

5.  Min_m

6.  Max_m

7.  Sign_f32_m

8.  Limit_m

9.  IntplVarXY_u16_u16Xu16Y_Cnt

## Data Hiding Functions

1.  \<None\>

2.  

## Global Functions/Macros Defined by this Module

None

## Local Functions/Macros Used by this MDD only

None

# Software Module Implementation

## Runtime Environment (RTE) Initial Values

This section lists the initial values of data written by this module but
controlled by the RTE. After RTE initialization, the data in this table
will contain these values.

| Data                                        | Value |
|---------------------------------------------|-------|
| Rte_InitValue_DisableLearning_Cnt_lgc       | FALSE |
| Rte_InitValue_DisableOutput_Cnt_lgc         | FALSE |
| Rte_InitValue_HandwheelAuthority_Uls_f32    | 0     |
| Rte_InitValue_HandwheelPosition_HwDeg_f32   | 0     |
| Rte_InitValue_HandwheelVelocity_HwRadpS_f32 | 0     |
| Rte_InitValue_HwTorque_HwNm_f32             | 0     |
| Rte_InitValue_PullCompCmd_MtrNm_f32         | 0     |
| Rte_InitValue_SrlComYawRate_DegpS_f32       | 0     |
| Rte_InitValue_VehicleSpeed_Kph_f32          | 0     |
| Rte_InitValue_VehicleSpeedRate_KphpS_f32    | 0     |
| Rte_InitValue_VehicleSpeedValid_Cnt_lgc     | FALSE |

## Initialization Functions

### Init: ActivePull_Init1

#### Design Rationale

This initialization function is used to set values that are based solely
on calibrations and constants (values which will not change over the
course of an ignition cycle). This includes preliminary gain
calculations, limits, and step sizes. It also initializes the
LTComp_HwNm_M_f32 module-internal variable with the appropriate value
from NvM.

#### Module Internal 

LTWindUpLimit_HwNm_M_f32 = Min_m(k_TotalLimit_HwNm_f32,
k_LTLimit_HwNm_f32)

STStepSize_HwNm_M_f32 = (D_STSAMPLETIME_SEC_F32 \* k_STLimit_HwNm_f32) /
k_STRampTime_Sec_f32

PullCompStepSize_HwNm_M_f32 = k_OutputMaxRate_HwNmpS_f32 \*
D_PULLCOMPSAMPLETIME_SEC_F32

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ActivePull/doc/mediax/media/image5.emf)

##  Periodic Functions

### Per: ActivePull_Per1

#### Design Rationale

The requirements in SF-13 show a signal called Reset_Svc. This is shown
as an input flag to the function. However, the reset service has been
implemented as a service call. In order to avoid any thread-based
issues, the service sets a separate variable for each periodic
(ResetPer1_Cnt_M_lgc, in this case) to TRUE. Then, near the beginning of
the execution of the periodic, this value is read. If it has been set to
true, it is immediately set to FALSE, and a local copy
(ResetSvc_Cnt_T_lgc) is set to TRUE. In this way, each periodic uses its
own local copy just as the design dictates using the input signal. The
local copy will be set to true for one execution of each periodic
function.

The SCom function to set the STComp is done in a similar fashion. The
Scom function sets SComSTCompSet_Cnt_M_lgc to TRUE and when
ActivePull_Per1 finds this value set to TRUE, it sets it back to FALSE
and uses SComSTComp_HwNm_M_f32 as the state variable (instead of
STComp_HwNm_M_f32, as it normally would). The state variable itself is
never changed, but the output of the next execution of ActivePull_Per1
will reflect the new value.

#### Program Flow Start

Rte_Call_ActivePull_Per1_CP0_CheckpointReached()

#### Store Module Inputs to Local copies

DisableLearning_Cnt_T_lgc =
Rte_Iread_ActivePull_Per1_DisableLearning_Cnt_lgc()

DisableOutput_Cnt_T_lgc =
Rte_Iread_ActivePull_Per1_DisableOutput_Cnt_lgc()

HandwheelAuthority_Uls_T_f32 =
Rte_Iread_ActivePull_Per1_HandwheelAuthority_Uls_f32()

HandwheelPosition_HwDeg_T_f32 =
Rte_Iread_ActivePull_Per1_HandwheelPosition_HwDeg_f32()

HandwheelVelocity_HwRadpS_T_f32 =
Rte_Iread_ActivePull_Per1_HandwheelVelocity_HwRadpS_f32()

HwTorque_HwNm_T_f32 = Rte_Iread_ActivePull_Per1_HwTorque_HwNm_f32()

SrlComYawRate_DegpS_T_f32 =
Rte_Iread_ActivePull_Per1_SrlComYawRate_DegpS_f32()

VehicleSpeedValid_Cnt_T_lgc =
Rte_Iread_ActivePull_Per1_VehicleSpeedValid_Cnt_lgc()

VehicleSpeed_Kph_T_f32 =
Rte_Iread_ActivePull_Per1_VehicleSpeed_Kph_f32()

LTComp_HwNm_T_f32 = LTComp_HwNm_M_f32

PrevSTComp_HwNm_T_f32 = STComp_HwNm_M_f32

####  Check for Scom Functions

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ActivePull/doc/mediax/media/image6.emf)

#### Filter Inputs

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ActivePull/doc/mediax/media/image7.emf)

#### Active Compensation Enable

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ActivePull/doc/mediax/media/image8.emf)

#### Determine Enable Learning

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ActivePull/doc/mediax/media/image9.emf)

#### Short Term Compensation Filter

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ActivePull/doc/mediax/media/image10.emf)

#### Calculate Integrator Gains

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ActivePull/doc/mediax/media/image11.emf)

#### Error Integrator & Active Limit

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ActivePull/doc/mediax/media/image12.emf)

#### Store Local copy of outputs into Module Outputs

HwTrqFilt_HwNm_D_f32 = HwTrqFilt_HwNm_T_f32

YawRateFilt_DegpS_D_f32 = YawRateFilt_DegpS_T_f32

STError_HwNm_D_f32 = STError_HwNm_T_f32

STIntGain_Uls_D_f32 = STIntGain_Uls_T_f32

STReset_Cnt_D_lgc = STReset_Cnt_T_lgc

STComp_HwNm_M_f32 = STComp_HwNm_T_f32

EnableLearn_Cnt_M_lgc = EnableLearning_Cnt_T_lgc

#### Program Flow End

Rte_Call_ActivePull_Per1_CP1_CheckpointReached()

### Per: ActivePull_Per2

#### Design Rationale

The Reset_Svc functionality is defined in section 6.3.1.1.

#### Program Flow Start

#### Rte_Call_ActivePull_Per2_CP0_CheckpointReached()Store Module Inputs to Local copies

VehicleSpeed_Kph_T_f32 =
Rte_Iread_ActivePull_Per2_VehicleSpeed_Kph_f32()

DisableOutput_Cnt_T_lgc =
Rte_Iread_ActivePull_Per2_DisableOutput_Cnt_lgc()

PrevPullCompCmd_HwNm_T_f32 = PullCompCmd_HwNm_M_f32

STComp_HwNm_T_f32 = STComp_HwNm_M_f32

LTComp_HwNm_T_f32 = LTComp_HwNm_M_f32

#### Check for Reset

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ActivePull/doc/mediax/media/image13.emf)

#### Calculate Active Compensation

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ActivePull/doc/mediax/media/image14.emf)

#### Store Local copy of outputs into Module Outputs

PullCompCmd_HwNm_M_f32 = PullCompCmd_HwNm_T_f32

Rte_Iwrite_ActivePull_Per2_PullCompCmd_MtrNm_f32(PullCompCmd_MtrNm_T_f32)

####  Program Flow End

### Rte_Call_ActivePull_Per2_CP1_CheckpointReached()Per: ActivePull_Per3

#### Design Rationale

The Reset_Svc and state variable functionality are defined in section
6.3.1.1. Note that the Scom functions will have no effect until the next
execution of ActivePull_Per3, which could result in a propagation delay
of up to 100 ms.

#### Program Flow Start

#### Rte_Call_ActivePull_Per3_CP0_CheckpointReached()Store Module Inputs to Local copies

VehSpd_Kph_T_f32 = Rte_IRead_ActivePull_Per3_VehicleSpeed_Kph_f32()

HwTorque_HwNm_T_f32 = Rte_Iread_ActivePull_Per3_HwTorque_HwNm_f32()

EnableLearning_Cnt_T_lgc = EnableLearn_Cnt_M_lgc

STComp_HwNm_T_f32 = STComp_HwNm_M_f32

PrevLTComp_HwNm_T_f32 = LTComp_HwNm_M_f32

#### Check for Scom Functions

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ActivePull/doc/mediax/media/image15.emf)

#### Long Term Compensation Filter

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ActivePull/doc/mediax/media/image16.emf)

#### Error Integrator

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ActivePull/doc/mediax/media/image17.emf)

#### Store Local copy of outputs into Module Outputs

LTError_HwNm_D_f32 = LTError_HwNm_T_f32

LTComp_HwNm_M_f32 = LTComp_HwNm_T_f32

#### Program Flow End

Rte_Call_ActivePull_Per3_CP1_CheckpointReached()

##  Fault Recovery Functions

None

## Shutdown Functions

None

## Interrupt Functions

None

## Serial Communication Functions

### Scom: ActivePull_Scom_Reset

|                      |      |      |     |     |          |
|----------------------|------|------|-----|-----|----------|
|                      |      | Type | Min | Max | UTP Tol. |
| **Arguments Passed** | None |      |     |     |          |
| **Return Value**     | None |      |     |     |          |

#### Design Rationale

#### Program Flow Start

N/A

#### Store Module Inputs to Local copies

####  Reset Service

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ActivePull/doc/mediax/media/image18.emf)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

N/A

### Scom: ActivePull_Scom_SetLTComp

|                      |                 |         |     |     |          |
|----------------------|-----------------|---------|-----|-----|----------|
|                      |                 | Type    | Min | Max | UTP Tol. |
| **Arguments Passed** | LTComp_HwNm_f32 | float32 | -10 | 10  |          |
| **Return Value**     | None            |         |     |     |          |

#### Design Rationale

This function helps to fulfill the requirement that the “Engineering
interface tool shall provide ability to set state variable to desired
value”. The state variable itself will not be updated until the next
time ActivePull_Per3 is run, but the NvM value is updated immediately.

#### Program Flow Start

N/A

#### Store Module Inputs to Local copies

None

####  

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ActivePull/doc/mediax/media/image19.emf)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

N/A

### Scom: ActivePull_Scom_SetSTComp

|                      |                 |         |     |     |          |
|----------------------|-----------------|---------|-----|-----|----------|
|                      |                 | Type    | Min | Max | UTP Tol. |
| **Arguments Passed** | STComp_HwNm_f32 | float32 | -10 | 10  |          |
| **Return Value**     | None            |         |     |     |          |

#### Design Rationale

This function helps to fulfill the requirement that the “Engineering
interface tool shall provide ability to set state variable to desired
value”. The state variable itself will not be updated until the next
time ActivePull_Per1 is run.

#### Program Flow Start

N/A

#### Store Module Inputs to Local copies

None

####  

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ActivePull/doc/mediax/media/image20.emf)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

N/A

### Scom: ActivePull_Scom_ReadParam

#### Program Flow Start

N/A

#### Store Module Inputs to Local copies

None

#### Read Data

\*PullCompCmd_HwNm_f32 = PullCompCmd_HwNm_M_f32

\*STComp_HwNm_f32 = STComp_HwNm_M_f32

\*LTComp_HwNm_f32 = LTComp_HwNm_M_f32

\*EnableLearn_Cnt_lgc = EnableLearn_Cnt_M_lgc

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

N/A

## Transition Functions

### Trns: ActivePull_Trns1

#### Design Rationale

This function is run when entering the OPERATE state. The LTComp NvM
block is set to write on shutdown (as ActivePull_Per3 will be updating
the NvM block), and the timers associated with ActivePull_Per1 are
initialized.

#### Program Flow Start

N/A

#### Store Module Inputs to Local copies

None

####  Initialization

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ActivePull/doc/mediax/media/image21.emf)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

N/A

##  

# Execution Requirements

## Execution Sequence of the Module

ActivePull_Per1 and Per2 are run at 2ms intervals, while Per3 is run at
a 100ms interval. However, while Per2 is run in all operation states,
Per1 and Per3 are only run in the OPERATE state. ActivePull_Trns1 is run
upon entering the OPERATE state.

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

| Function Name    | Calling Frequency | System State(s) in which the function is called |
|--------------------------|-----------------|------------------------------|
| ActivePull_Init1 | On Event (once)   | On Entering WARMINIT                            |
| ActivePull_Per1  | 2 ms              | OPERATE                                         |
| ActivePull_Per2  | 2 ms              | All                                             |
| ActivePull_Per3  | 100 ms            | OPERATE                                         |
| ActivePull_Trns1 | On Event          | On Entering OPERATE                             |

## Execution Requirements for Serial Communication Functions 

| Function Name             | Sub-Module called by (Serial Comm Function Name) |
|-----------------------------|-------------------------------------------|
| ActivePull_Scom_Reset     |                                                  |
| ActivePull_Scom_SetLTComp |                                                  |
| ActivePull_Scom_SetSTComp |                                                  |
| ActivePull_Scom_ReadParam |                                                  |

#  [section-4]

#  Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

| Name of Sub Module        | Software Segment                      |
|---------------------------|---------------------------------------|
| ActivePull_Init1          | RTE_START_SEC_AP_ACTIVEPULL_APPL_CODE |
| ActivePull_Per1           | RTE_START_SEC_AP_ACTIVEPULL_APPL_CODE |
| ActivePull_Per2           | RTE_START_SEC_AP_ACTIVEPULL_APPL_CODE |
| ActivePull_Per3           | RTE_START_SEC_AP_ACTIVEPULL_APPL_CODE |
| ActivePull_Trns1          | RTE_START_SEC_AP_ACTIVEPULL_APPL_CODE |
| ActivePull_Scom_Reset     | RTE_START_SEC_AP_ACTIVEPULL_APPL_CODE |
| ActivePull_Scom_SetLTComp | RTE_START_SEC_AP_ACTIVEPULL_APPL_CODE |
| ActivePull_Scom_SetSTComp | RTE_START_SEC_AP_ACTIVEPULL_APPL_CODE |
| ActivePull_Scom_ReadParam | RTE_START_SEC_AP_ACTIVEPULL_APPL_CODE |

##  [section-5]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

| Name of Sub Module | Software Segment |
|--------------------|------------------|
|                    |                  |

#  [section-6]

#  Known Issues / Limitations With Design

1.  INLINE functions defined in “GlobalMacro.h” are not unit tested

#  Revision Control Log

<table style="width:100%;">
<colgroup>
<col style="width: 6%" />
<col style="width: 6%" />
<col style="width: 63%" />
<col style="width: 12%" />
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
<td>Initial MDD</td>
<td>01Aug11</td>
<td>LWW</td>
</tr>
<tr class="odd">
<td>2</td>
<td>2.0</td>
<td>Updated to SF-13 rev 001 (started from scratch)</td>
<td>02-Apr-12</td>
<td>OT</td>
</tr>
<tr class="even">
<td>3</td>
<td>3.0</td>
<td>Fixed buffered reads in Reset Scom function (changed to direct
reads)</td>
<td>18-Apr-12</td>
<td>OT</td>
</tr>
<tr class="odd">
<td>4</td>
<td>4.0</td>
<td>Removed PIM from Scom and made LT learned variable to a typH. Added
support for FDAD Common manufacturing srvc DID</td>
<td>22-Apr-12</td>
<td>VK</td>
</tr>
<tr class="even">
<td>5</td>
<td>5.0</td>
<td>Updates to meet SF-13 rev 002</td>
<td>26-June-12</td>
<td>VK</td>
</tr>
<tr class="odd">
<td>6</td>
<td>6.0</td>
<td>Corrected module internal variable ranges</td>
<td>29-June-12</td>
<td>VK</td>
</tr>
<tr class="even">
<td>7</td>
<td>7.0</td>
<td><p>1) Removed VehSpdRate global input and made necessary changes in
Per1</p>
<p>2) Added VehicleSpeedRate logic in Per3 -Ver 003 updates</p>
<p>3) Changed LPF from fixed to float</p></td>
<td>23-July-12</td>
<td>NRAR</td>
</tr>
<tr class="odd">
<td>8</td>
<td>8.0</td>
<td>Inserted safe watchdog checkpoints</td>
<td>15-Sept-12</td>
<td>BWL</td>
</tr>
<tr class="even">
<td>9</td>
<td>9.0</td>
<td>Corrected static variable to MDD format</td>
<td>18-sep-12</td>
<td>SSK</td>
</tr>
<tr class="odd">
<td>10</td>
<td>10.0</td>
<td>Updated calibration table Y datatype to u2p14 for anomaly
correction, removed condition checks on SCom function</td>
<td>20 Oct 12</td>
<td>LWW</td>
</tr>
<tr class="even">
<td>11</td>
<td>11.0</td>
<td>Anomaly 5379 fixed.</td>
<td>07-Aug-13</td>
<td>SP</td>
</tr>
<tr class="odd">
<td>12</td>
<td>12.0</td>
<td>Anomaly 5764 (to revert changes made as part of the previous Anomaly
5379 fix)</td>
<td>16-Apr-14</td>
<td>LK</td>
</tr>
</tbody>
</table>

{% endraw %}