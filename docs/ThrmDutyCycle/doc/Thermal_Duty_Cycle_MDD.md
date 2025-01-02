---
layout: default
title: Thermal_Duty_Cycle_MDD
nav_order: 2
parent: Thermal Duty Cycle
---
{% raw %}
# Module – Thermal Duty Cycle [module-thermal-duty-cycle]

# High-Level Description

This module computes a duty cycle limit based on system temperatures. It
also outputs a unity scalar value to scale the assist command and a
value representing the percentage of reduction.

# Figures

## Component Diagram

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ThrmDutyCycle/doc/mediax/media/image1.png"
style="width:3.625in;height:3.86111in" />

#  Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

| Module Inputs            | Module Outputs |                        |
|--------------------------|----------------|------------------------|
| MtrPkCurr_AmpSq_f32      |                | ThermalLimit_MtrNm_f32 |
| FilteredPkCurr_AmpSq_f32 |                | DutyCycleLevel_Uls_f32 |
| MotorVelCRF_MtrRadpS_f32 |                | ThermLimitPerc_Uls_f32 |
| FiltMeasTemp_DegC_f32    |                |                        |
| SiTempEst_DegC_f32       |                |                        |
| MagTempEst_DegC_f32      |                |                        |
| CuTempEst_DegC_f32       |                |                        |
| DiagStsDefTemp \_Cnt_lgc |                |                        |
| DefeatDutySvc_Cnt_lgc    |                |                        |
| IgnTimeOff_Cnt_u32       |                |                        |
| VehTimeValid_Cnt_lgc     |                |                        |

## Module Internal Variables

This section identifies the name, range and resolutions for module
specific data created by this module. If there are no range restrictions
on the variable, the term “FULL” is placed into the table for legal
range.

<table>
<colgroup>
<col style="width: 15%" />
<col style="width: 19%" />
<col style="width: 14%" />
<col style="width: 11%" />
<col style="width: 11%" />
<col style="width: 27%" />
</colgroup>
<thead>
<tr class="header">
<th colspan="2">Variable Name</th>
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
<td colspan="2">ThrmDutyCycle_TrqCmdTblYRam_MtrNm_M_u9p7[8]</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>THRMLDUTYCYCLE_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td colspan="2">ThrmDutyCycle_AbsTempFltAcc_Cnt_M_u16</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>THRMLDUTYCYCLE_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="odd">
<td colspan="2">ThrmDutyCycle_Filter1KSV_M_str</td>
<td>LPF32KSV_Str</td>
<td></td>
<td></td>
<td>THRMLDUTYCYCLE_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="even">
<td></td>
<td>SV_Uls_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>K_Uls_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td></td>
</tr>
<tr class="even">
<td colspan="2">ThrmDutyCycle_Filter2KSV_M_str</td>
<td>LPF32KSV_Str</td>
<td></td>
<td></td>
<td>THRMLDUTYCYCLE_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="odd">
<td></td>
<td>SV_Uls_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>K_Uls_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td></td>
</tr>
<tr class="odd">
<td colspan="2">ThrmDutyCycle_Filter3KSV_M_str</td>
<td>LPF32KSV_Str</td>
<td></td>
<td></td>
<td>THRMLDUTYCYCLE_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="even">
<td></td>
<td>SV_Uls_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>K_Uls_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td></td>
</tr>
<tr class="even">
<td colspan="2">ThrmDutyCycle_Filter4KSV_M_str</td>
<td>LPF32KSV_Str</td>
<td></td>
<td></td>
<td>THRMLDUTYCYCLE_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="odd">
<td></td>
<td>SV_Uls_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>K_Uls_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td></td>
</tr>
<tr class="odd">
<td colspan="2">ThrmDutyCycle_Filter5KSV_M_str</td>
<td>LPF32KSV_Str</td>
<td></td>
<td></td>
<td>THRMLDUTYCYCLE_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="even">
<td></td>
<td>SV_Uls_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>K_Uls_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td></td>
</tr>
<tr class="even">
<td colspan="2">ThrmDutyCycle_Filter6KSV_M_str</td>
<td>LPF32KSV_Str</td>
<td></td>
<td></td>
<td>THRMLDUTYCYCLE_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="odd">
<td></td>
<td>SV_Uls_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>K_Uls_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td></td>
</tr>
<tr class="odd">
<td colspan="2">ThrmDutyCycle_AbsTempLimit_MtrNm_M_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>THRMLDUTYCYCLE_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td colspan="2">ThrmDutyCycle_Mult12Temp_DegC_D_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>THRMLDUTYCYCLE_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td colspan="2">ThrmDutyCycle_Mult36Temp_DegC_D_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>THRMLDUTYCYCLE_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td colspan="2">ThrmDutyCycle_MaxOut_AmpSq_D_u16p0</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>THRMLDUTYCYCLE_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="odd">
<td colspan="2">ThrmDutyCycle_ThermLim_MtrNm_D_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>THRMLDUTYCYCLE_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td colspan="2">ThrmDutyCycle_Mult1_Uls_D_u3p13</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>THRMLDUTYCYCLE_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="odd">
<td colspan="2">ThrmDutyCycle_Mult2_Uls_D_u3p13</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>THRMLDUTYCYCLE_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td colspan="2">ThrmDutyCycle_Mult3_Uls_D_u3p13</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>THRMLDUTYCYCLE_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="odd">
<td colspan="2">ThrmDutyCycle_Mult4_Uls_D_u3p13</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>THRMLDUTYCYCLE_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td colspan="2">ThrmDutyCycle_Mult5_Uls_D_u3p13</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>THRMLDUTYCYCLE_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="odd">
<td colspan="2">ThrmDutyCycle_Mult6_Uls_D_u3p13</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>THRMLDUTYCYCLE_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td colspan="2">ThrmDutyCycle_LastTblVal_MtrNm_D_u9p7</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>THRMLDUTYCYCLE_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="odd">
<td colspan="2">ThrmDutyCycle_LastTblValSlew_MtrNm_D_u9p7</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>THRMLDUTYCYCLE_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td colspan="2">ThrmDutyCycle_AbsCtrlTempLimit_MtrNm_D_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>THRMLDUTYCYCLE_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td colspan="2">ThrmDutyCycle_AbsCuTempLimit_MtrNm_D_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>THRMLDUTYCYCLE_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td colspan="2">ThrmDutyCycle_AbsTempLimit_MtrNm_D_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>THRMLDUTYCYCLE_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td colspan="2">ThrmDutyCycle_ThrmLoadLmtTblYVal_MtrNm_D_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>THRMLDUTYCYCLE_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td colspan="2"></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td colspan="2"></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td colspan="2"></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td colspan="2"></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td colspan="2"> ThrmDutyCycle_CntrFlagInit_Cnt_M_lgc</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>THRMLDUTYCYCLE_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="odd">
<td colspan="2">ThrmDutyCycle_ReInitCntrFlag_Cnt_M_lgc</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>THRMLDUTYCYCLE_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="even">
<td colspan="2">ThrmDutyCycle_ReInitCntrVal_Sec_M_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>THRMLDUTYCYCLE_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td colspan="2">ThrmDutyCycle_eFilt3ValPowerup_Cnt_M_u8</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>THRMLDUTYCYCLE_START_SEC_VAR_CLEARED_8</td>
</tr>
<tr class="even">
<td colspan="2">ThrmDutyCycle_eFilt4ValPowerup_Cnt_M_u8</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>THRMLDUTYCYCLE_START_SEC_VAR_CLEARED_8</td>
</tr>
<tr class="odd">
<td colspan="2">ThrmDutyCycle_eFilt5ValPowerup_Cnt_M_u8</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>THRMLDUTYCYCLE_START_SEC_VAR_CLEARED_8</td>
</tr>
<tr class="even">
<td colspan="2">ThrmDutyCycle_eFilt6ValPowerup_Cnt_M_u8</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>THRMLDUTYCYCLE_START_SEC_VAR_CLEARED_8</td>
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

| Constant Name                      |
|------------------------------------|
| k_EOCCtrlTemp_DegC_f32             |
| k_CtrlTempSlc_Cnt_lgc              |
| k_MtrPrTempSlc_Cnt_lgc             |
| k_AbsMtrVelBkt_MtrRadps_f32        |
| t_MultTblX_DegC_s15p0\[5\]         |
| t_Mult1NSTblY_Uls_u3p13\[5\]       |
| t_Mult2NSTblY_Uls_u3p13\[5\]       |
| t_Mult3NSTblY_Uls_u3p13\[5\]       |
| t_Mult4NSTblY_Uls_u3p13\[5\]       |
| t_Mult5NSTblY_Uls_u3p13\[5\]       |
| t_Mult6NSTblY_Uls_u3p13\[5\]       |
| t_Mult1STblY_Uls_u3p13\[5\]        |
| t_Mult2STblY_Uls_u3p13\[5\]        |
| t_Mult3STblY_Uls_u3p13\[5\]        |
| t_Mult4STblY_Uls_u3p13\[5\]        |
| t_Mult5STblY_Uls_u3p13\[5\]        |
| t_Mult6STblY_Uls_u3p13\[5\]        |
| t_LastTblValNS_MtrNm_u9p7\[5\]     |
| t_LastTblValS_MtrNm_u9p7\[5\]      |
| k_TrqCmdSlewDown_MtrNm_u9p7        |
| k_TrqCmdSlewUp_MtrNm_u9p7          |
| k_SlowFltTempSlc_Cnt_lgc           |
| t_AbsCtrlTmpTblX_DegC_s15p0\[4\]   |
| t_AbsCtrlTmpTblY_MtrNm_u9p7\[4\]   |
| t_AbsCuTmpTblX_DegC_s15p0\[4\]     |
| t_AbsCuTmpTblY_MtrNm_u9p7\[4\]     |
| k_AbsTmpTrqSlewLmt_MtrNm_f32       |
| k_MultTempSlc_Cnt_lgc              |
| k_AbsTempDiag_Cnt_str              |
| k_DutyCycFltTrshld_AmpSq_u16p0     |
| t_ThrmLoadLmtTblX_AmpSq_u16p0\[8\] |
| t_ThrmLoadLmtTblY_MtrNm_u9p7\[8\]  |
| k_DefaultIgnOffTime_Sec_f32        |
| k_IgnOffCntrEnb_Cnt_lgc            |
| k_IgnOffMsgWaitTime_Sec_f32        |

##  [section]

## Program (fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

| Constant Name                  | Resolution             | Units    | Value           |
|-----------------------------|----------------|--------------|--------------|
| D_FILT1LPFKN_HZ_F32            | Single Precision Float | Hz       | 1/(2\*pi\*1.59) |
| D_FILT2LPFKN_HZ_F32            | Single Precision Float | Hz       | 1/(2\*pi\*15.9) |
| D_FILT3LPFKN_HZ_F32            | Single Precision Float | Hz       | 1/(2\*pi\*159)  |
| D_FILT4LPFKN_HZ_F32            | Single Precision Float | Hz       | 1/(2\*pi\*300)  |
| D_FILT5LPFKN_HZ_F32            | Single Precision Float | Hz       | 1/(2\*pi\*1590) |
| D_FILT6LPFKN_HZ_F32            | Single Precision Float | Hz       | 1/(2\*pi\*4000) |
| D_1PERC_ULS_F32                | Single Precision Float | Unitless | 0.01            |
| D_FILTOUTLIM_ULS_F32           | Single Precision Float | Unitless | 200.0           |
| D_DEFEATDUTYCYCLELEVEL_ULS_F32 | Single Precision Float | Unitless | 0.0             |
| D_DEFEATTHERMLIMITPERC_ULS_F32 | Single Precision Float | Unitless | 0.0             |
| D_DEFEATTHERMLIMIT_MTRNM_F32   | Single Precision Float | MtrNm    | 8.8             |
| D_TAU3_SEC_F32                 | Single Precision Float | Sec      | 159             |
| D_TAU4_SEC_F32                 | Single Precision Float | Sec      | 300             |
| D_TAU5_SEC_F32                 | Single Precision Float | Sec      | 1590            |
| D_TAU6_SEC_F32                 | Single Precision Float | Sec      | 4000            |
| D_PER1EXECRATE_SEC_F32         | Single Precision Float | Sec      | 0.1             |
| D_EFILTVALMIN_ULS_F32          | Single Precision Float | Unitless | 0.0             |
| D_EFILTVALMAX_ULS_F32          | Single Precision Float | Unitless | 200.0           |

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

| Constant Name              |
|----------------------------|
| D_MTRTRQCMDHILMT_MTRNM_F32 |
| D_ZERO_ULS_F32             |
| D_ZERO_CNT_U32             |
| D_ONE_ULS_F32              |
| D_ONE_CNT_U16              |
| D_ONE_CNT_U32              |
| D_100MS_SEC_F32            |
| D_ZERO_CNT_U8              |

### Module specific Lookup Tables Constants

| Constant Name | Resolution | Value | Software Segment |
|---------------|------------|-------|------------------|
| None          |            |       |                  |

#  Functions/Macros used by the Sub-Modules 

## Library Functions / Macros 

The library and functions / Macros that are called by the various sub
modules are identified below,

1.  TableSize_m

2.  FPM_FixedToFloat_m

3.  FPM_FloatToFixed_m

4.  LPF_KUpdate_f32_m

5.  LPF_OpUpdate_f32_m

6.  Abs_f32_m

7.  IntplVarXY_u16_s16Xu16Y_Cnt

8.  IntplVarXY_u16_u16Xu16Y_Cnt

9.  Max_m

10. Min_m

11. Limit_m

12. DiagPStep_m

13. DiagNStep_m

14. DiagFailed_m

## Data Hiding Functions

1.  None

## Global Functions/Macros Defined by this Module

None

## Local Functions/Macros Used by this MDD only

### Local Function \#1

|                      |                            |          |         |        |          |
|--------------|----------------------|-------|----------|-------------|-------|
| **Function Name**    | StepVarXY_u16_s16Xu16Y_Cnt | Type     | Min     | Max    | UTP Tol. |
| **Arguments Passed** | TableX                     | sint16\* | -32,768 | 32,767 | N/A      |
|                      | TableY                     | uint16\* | 0       | 65535  | N/A      |
|                      | Size                       | uint16   | 1       | 65535  | N/A      |
|                      | input                      | sint16   | -32,768 | 32,767 | N/A      |
| **Return Value**     | See description            | uint16   | 0       | 65535  | 0        |

NOTE – this function is able to be called with the range of argument
values as shown; full range will not necessarily be reached in the
actual calls to this function in this component. UTP will test this
function only to the limits of the actual parameters in the actual
function calls.

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ThrmDutyCycle/doc/mediax/media/image2.emf)

# Software Module Implementation

## Runtime Environment (RTE) Initial Values

This section lists the initial values of data written by this module but
controlled by the RTE. After RTE initialization, the data in this table
will contain these values.

| Data                                     | Value |
|------------------------------------------|-------|
| Rte_InitValue_CuTempEst_DegC_f32         | 0     |
| Rte_InitValue_DutyCycleLevel_Uls_f32     | 0     |
| Rte_InitValue_FiltMeasTemp_DegC_f32      | 0     |
| Rte_InitValue_FilteredPkCurr_AmpSq_f32   | 0     |
| Rte_InitValue_MagTempEst_DegC_f32        | 0     |
| Rte_InitValue_MotorVelCRF_MtrRadpS_f32   | 0     |
| Rte_InitValue_MtrPkCurr_AmpSq_f32        | 0     |
| Rte_InitValue_SiTempEst_DegC_f32         | 0     |
| Rte_InitValue\_ DiagStsDefTemp \_Cnt_lgc | FALSE |
| Rte_InitValue_ThermLimitPerc_Uls_f32     | 0     |
| Rte_InitValue_ThermalLimit_MtrNm_f32     | 8.8   |
| Rte_InitValue_DefeatDutySvc_Cnt_lgc      | FALSE |
| Rte_InitValue\_ IgnTimeOff_Cnt_u32       | 0     |
| Rte_InitValue\_ VehTimeValid_Cnt_lgc     | FALSE |

## Initialization Functions

### Init: ThrmlDutyCycle_Init1

#### Design Rationale

None

#### Module Outputs

None

#### Store Module Inputs to Local copies

IgnTimeOff_Sec_T_u32 =
Rte_IRead_ThrmlDutyCycle_Init1_IgnTimeOff_Cnt_u32()

VehTimeValid_Cnt_T_lgc =
Rte_IRead_ThrmlDutyCycle_Init1_VehTimeValid_Cnt_lgc()

DefeatDutySvc_Cnt_T_lgc =
Rte_IRead_ThrmlDutyCycle_Init1_DefeatDutySvc_Cnt_lgc()

#### Module Internal 

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ThrmDutyCycle/doc/mediax/media/image3.emf)

##  Periodic Functions

### Per: ThrmlDutyCycle_Per1

#### Design Rationale

Function NxtrDiagMgr_GetNTCFailed with argument NTC_Num_Thermistor is
used to get the input called Diag_Status in the FDD. This function
returns TRUE if the specified NTC is currently in a FAILED state. The
FDD owner has confirmed that this is what is meant in the FDD by the use
of the Diag_Status input described as “Thermistor fault flag” and also
called “Temp_Sens_DTC_Active”.

#### Program Flow Start

Rte_Call_ThrmlDutyCycle_Per1_CP0_CheckpointReached()

#### Store Module Inputs to Local copies

CuTempEst_DegC_T_f32 =
Rte_IRead_ThrmlDutyCycle_Per1_CuTempEst_DegC_f32()

FiltMeasTemp_DegC_T_f32 =
Rte_IRead_ThrmlDutyCycle_Per1_FiltMeasTemp_DegC_f32()

FiltPkCurr_AmpSq_T_f32 =
Rte_IRead_ThrmlDutyCycle_Per1_FilteredPkCurr_AmpSq_f32()

MagTempEst_DegC_T_f32 =
Rte_IRead_ThrmlDutyCycle_Per1_MagTempEst_DegC_f32()

MotorVelCRF_MtrRadpS_T_f32 =
Rte_IRead_ThrmlDutyCycle_Per1_MotorVelCRF_MtrRadpS_f32()

MtrPkCurr_AmpSq_T_f32 =
Rte_IRead_ThrmlDutyCycle_Per1_MtrPkCurr_AmpSq_f32()

SiTempEst_DegC_T_f32 =
Rte_IRead_ThrmlDutyCycle_Per1_SiTempEst_DegC_f32()

DefeatDutySvc_Cnt_T_lgc =
Rte_IRead_ThrmlDutyCycle_Per1_DefeatDutySvc_Cnt_lgc_Cnt_lgc();

PrevAbsTempLimit_MtrNm_T_f32 = AbsTempLimit_MtrNm_M_f32

AbsMotorVelCRF_MtrRadpS_T_f32 = Abs_f32_m(MotorVelCRF_MtrRadpS_T_f32)

Rte_Call\_NxtrDiagMgr_GetNTCFailed(NTC_Num_Thermistor,
&DiagStsDefTemp_Cnt_T_lgc)

VehTimeValid_Cnt_T_lgc =
Rte_IRead_ThrmlDutyCycle_Per1_VehTimeValid_Cnt_lgc();

IgnTimeOff_Cnt_T_u32 =
Rte_IRead_ThrmlDutyCycle_Per1_IgnTimeOff_Cnt_u32();

#### Filter Re-Init

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ThrmDutyCycle/doc/mediax/media/image4.emf)

#### Temperature Selection

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ThrmDutyCycle/doc/mediax/media/image5.emf)

#### Load Limiting – Multiplier

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ThrmDutyCycle/doc/mediax/media/image6.emf)

#### Load Limiting – Max Filter Percentage

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ThrmDutyCycle/doc/mediax/media/image7.emf)

#### Load Limiting – Thermal Load Limit

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ThrmDutyCycle/doc/mediax/media/image8.emf)

#### Temperature Limiting

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ThrmDutyCycle/doc/mediax/media/image9.emf)

#### Temperature Limiting Status

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ThrmDutyCycle/doc/mediax/media/image10.emf)

#### Store Local copy of outputs into Module Outputs

ThrmDutyCycle_AbsTempLimit_MtrNm_M_f32 = AbsTempLimitSlew_MtrNm_T_f32

ThrmDutyCycle_Mult12Temp_DegC_D_f32 = Mult12Temp_DegC_T_f32

ThrmDutyCycle_Mult36Temp_DegC_D_f32 = Mult36Temp_DegC_T_f32

ThrmDutyCycle_MaxOut_AmpSq_D_u16p0 = MaxOut_Uls_T_u16p0

ThrmDutyCycle_ThermLim_MtrNm_D_f32 = ThermalLoadLmt_MtrNm_T_f32

ThrmDutyCycle_Mult1_Uls_D_u3p13 = Mult1_Uls_T_u3p13

ThrmDutyCycle_Mult2_Uls_D_u3p13 = Mult2_Uls_T_u3p13

ThrmDutyCycle_Mult3_Uls_D_u3p13 = Mult3_Uls_T_u3p13

ThrmDutyCycle_Mult4_Uls_D_u3p13 = Mult4_Uls_T_u3p13

ThrmDutyCycle_Mult5_Uls_D_u3p13 = Mult5_Uls_T_u3p13

ThrmDutyCycle_Mult6_Uls_D_u3p13 = Mult6_Uls_T_u3p13

ThrmDutyCycle_LastTblVal_MtrNm_D_u9p7 = LastTblValRaw_MtrNm_T_u9p7

ThrmDutyCycle_LastTblValSlew_MtrNm_D_u9p7 = LastTblVal_MtrNm_T_u9p7

ThrmDutyCycle_AbsCtrlTempLimit_MtrNm_D_f32 =
AbsCtrlTempLimit_MtrNm_T_f32

ThrmDutyCycle_AbsCuTempLimit_MtrNm_D_f32 = AbsCuTempLimit_MtrNm_T_f32

ThrmDutyCycle_AbsTempLimit_MtrNm_D_f32 = AbsTempLimit_MtrNm_T_f32

ThrmDutyCycle_ThrmLoadLmtTblYVal_MtrNm_D_f32 = DivFactor_MtrNm_T_f32

Rte_IWrite_ThrmlDutyCycle_Per1_DutyCycleLevel_Uls_f32(MaxSlowFilt_Uls_T_f32)

Rte_IWrite_ThrmlDutyCycle_Per1_ThermLimitPerc_Uls_f32(ThermLimitPerc_Uls_T_f32)

Rte_IWrite_ThrmlDutyCycle_Per1_ThermalLimit_MtrNm_f32(ThermalLimit_MtrNm_T_f32)

#### Program Flow End

Rte_Call_ThrmlDutyCycle_Per1_CP1_CheckpointReached()

##  Fault Recovery Functions

None

## Shutdown Functions

None

## Interrupt Functions

None

## Serial Communication Functions

None

##  

# Execution Requirements

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

| Function Name        | Calling Frequency | System State(s) in which the function is called |
|--------------------------|-----------------|------------------------------|
| ThrmlDutyCycle_Init1 | On Event          | On Init                                         |
| ThrmlDutyCycle_Per1  | 100 ms            | ALL                                             |

## Execution Requirements for Serial Communication Functions 

| Function Name | Sub-Module called by (Serial Comm Function Name) |
|---------------|--------------------------------------------------|
| None          |                                                  |

#  [section-2]

#  Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

| Name of Sub Module   | Software Segment                          |
|----------------------|-------------------------------------------|
| ThrmlDutyCycle_Init1 | RTE_START_SEC_AP_THRMLDUTYCYCLE_APPL_CODE |
| ThrmlDutyCycle_Per1  | RTE_START_SEC_AP_THRMLDUTYCYCLE_APPL_CODE |

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

2.  Unit test of StepVarXY_u16_s16Xu16Y_Cnt() function will test
    argument range only to the limits of the actual parameters in the
    actual function calls in the module.

#  Revision Control Log

<table>
<colgroup>
<col style="width: 7%" />
<col style="width: 68%" />
<col style="width: 11%" />
<col style="width: 12%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Rev #</strong></td>
<td><strong>Change Description</strong></td>
<td><strong>Date</strong></td>
<td><strong>Author Initials</strong></td>
</tr>
<tr class="even">
<td>1.0</td>
<td>Initial Version (implements SF-09 v001)</td>
<td>21-May-12</td>
<td>OT</td>
</tr>
<tr class="odd">
<td>2.0</td>
<td>Updated initial value of AssistThermScalar output, added limit on
maxout terms to prevent overflow per new FDD design</td>
<td>30-May-12</td>
<td>LWW</td>
</tr>
<tr class="even">
<td>3.0</td>
<td>Updated values of 6 filter embedded data constants- Anom 3445</td>
<td>16-June-12</td>
<td>NRAR</td>
</tr>
<tr class="odd">
<td>4.0</td>
<td>Updated to SF-09 v003</td>
<td>09-Jul-12</td>
<td>OT</td>
</tr>
<tr class="even">
<td>5.0</td>
<td>Updated to SF-09 v004</td>
<td>09-Aug-12</td>
<td>BWL</td>
</tr>
<tr class="odd">
<td>6.0</td>
<td>MDD fixes per unit test review.</td>
<td>10-Aug-12</td>
<td>BWL</td>
</tr>
<tr class="even">
<td>7.0</td>
<td>Added checkpoints and memmap software segment is updated for static
variables</td>
<td>24-Sep-12</td>
<td>Selva</td>
</tr>
<tr class="odd">
<td>8.0</td>
<td>Replaced multiplier interpolation with step function.</td>
<td>16-Oct-12</td>
<td>BWL</td>
</tr>
<tr class="even">
<td>9.0</td>
<td>Updated to SF-09 v006</td>
<td>29-Jan-13</td>
<td>Selva</td>
</tr>
<tr class="odd">
<td>10</td>
<td>Corrected Diag_Status reading function</td>
<td>31-Jan-13</td>
<td>Selva</td>
</tr>
<tr class="even">
<td>11</td>
<td>Updated to SF-09 v007</td>
<td>20-Feb-13</td>
<td>SP</td>
</tr>
<tr class="odd">
<td>12</td>
<td>Fix Anomoly 4517</td>
<td>28-Feb-13</td>
<td>Selva</td>
</tr>
<tr class="even">
<td>13,14</td>
<td><p>Updated to SF-09 v008`</p>
<p>Tessy Unit test fixes</p></td>
<td>09-Apr-13</td>
<td>Selva</td>
</tr>
<tr class="odd">
<td>15</td>
<td>Updated to SF-09 v010 – new logic for calculating AbsTempLimit; also
updated module and display variable names per naming conventions.</td>
<td>05-Sep-13</td>
<td>KMC</td>
</tr>
<tr class="even">
<td>16</td>
<td>Updated to SF-09 v11 -- new logic for reinit of the filter state
variables based on ignition off time.</td>
<td>17-Sep-13</td>
<td>KJS</td>
</tr>
<tr class="odd">
<td>17</td>
<td>Updated to SF-09 v012 – updated filter init and reinit to use the
default ignition off time when DefeatDutySvc is TRUE</td>
<td>25-Sep-13</td>
<td>KMC</td>
</tr>
<tr class="even">
<td>18</td>
<td>Updated some incorrect module level variable names; added notes
regarding unit test of function StepVarXY_u16_s16Xu16Y_Cnt()</td>
<td>27-Sep-13</td>
<td>KMC</td>
</tr>
<tr class="odd">
<td>19</td>
<td>Updated flowcharts for naming conventions, SetNTCStatus parameter
byte 0x00 when PASSED, and limiting on ThermLimitPerc output. Added note
about NTCFailed. All for CR10070.</td>
<td>1-Oct-13</td>
<td>KMC</td>
</tr>
<tr class="even">
<td>20</td>
<td>Added 4 new module internal variables and modified flowcharts for
fix of anomaly 5736; added two new constants and modified flowcharts for
fix of anomaly 5739.</td>
<td>14-Nov-13</td>
<td>KMC</td>
</tr>
<tr class="odd">
<td>21</td>
<td>Updated to SF09 revision 14. Moved the four filters from TypeH to
their own NvM block</td>
<td>22-Nov-13</td>
<td>KJS</td>
</tr>
</tbody>
</table>

{% endraw %}