---
layout: default
title: CmMtrCurr_MDD
nav_order: 3
parent: Component
---
{% raw %}
# Module -- CmMtrCurr [module----cmmtrcurr]

# High-Level Description

The Current Measurement function is responsible for measuring the motor
phase currents used as feedback by the Motor Control FDD. Two motor
phase currents are measured using a shunt resistor and a differential
amplifier circuitry, and along with the motor position are transformed
into direct (D) and quadrature (Q) axes currents using the combined
Clarke/Park transform

UNIT Test Notes:

Unit test should be done with enabling one of the six predefned macro
MTRCURRPHASEBC, MTRCURRPHASECB, MTRCRRPHASECA, MTRCURRPHASEAB,
MTRCURRPHASEAC, MTRCURRPHASEBA. Hence it should have six UTP results
(one for each Macro enabled).

# Figures

## Component diagram

#  Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

| Module Inputs               | Module Outputs |                             |
|-----------------------------|----------------|-----------------------------|
| ADCMtrCurr1_Volt_f32        |                | MtrCurrQax_Amps_f32         |
| ADCMtrCurr2_Volt_f32        |                | MtrCurrDax_Amps_f32         |
| MtrVel_MtrRadpS_f32         |                | CurrentGainSvc_Cnt_lgc      |
| FiltCntrlTemp_DegC_f32      |                | ComOffset_Cnt_u16           |
| MtrCurrAngle_Rev_f32        |                | ElecPosDelayComp_Rad_f32    |
| VehSpd_Kph_f32              |                | CorrMtrCurrPosition_Rev_f32 |
| VhSpdValid_Cnt_lgc          |                | MtrCurrK1_Amps_f32          |
| Vecu_Volt_f32               |                | MtrCurrK2_Amps_f32          |
| MtrCurr1TempOffset_Volt_f32 |                | MtrCurr1_Volts_f32          |
| MtrCurr2TempOffset_Volt_f32 |                | MtrCurr2_Volts_f32          |
| Phs1Curr_Cnt_u16            |                | MtrCurrQax_Amps_f32         |
| Phs2Curr_Cnt_u16            |                | MtrCurrDax_Amps_f32         |
| MtrElecPol_Cnt_s08          |                | CurrentGainSvc_Cnt_lgc      |
| DCPhsBComp_Cnt_u16          |                |                             |
| DCPhsCComp_Cnt_u16          |                |                             |
| DCPhsCComp_Cnt_u16          |                |                             |
| DCPhsBComp_Cnt_u16          |                |                             |
| DCPhsAComp_Cnt_u16          |                |                             |
| DCPhsBComp_Cnt_u16          |                |                             |
| DCPhsBComp_Cnt_u16          |                |                             |
| DCPhsAComp_Cnt_u16          |                |                             |
| DCPhsAComp_Cnt_u16          |                |                             |
| DCPhsCComp_Cnt_u16          |                |                             |
| DCPhsCComp_Cnt_u16          |                |                             |
| DCPhsAComp_Cnt_u16          |                |                             |
| ADC2OffsetComp_Cnt_u8p8     |                |                             |

## Module Internal Variables

This section identifies the name, range and resolutions for module
specific data created by this module. If there are no range restrictions
on the variable, the term “FULL” is placed into the table for legal
range.

<table style="width:100%;">
<colgroup>
<col style="width: 29%" />
<col style="width: 17%" />
<col style="width: 11%" />
<col style="width: 11%" />
<col style="width: 31%" />
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
<td>CmMtrCurr_CorrMtrCurr1_Amp_D_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>CmMtrCurr_CorrMtrCurr2_Amp_D_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>CmMtrCurr_CurrVectPosition_Rev_D_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>CmMtrCurr_VectPosCosTheta_Uls_D_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>CmMtrCurr_VectPosSinTheta_Uls_D_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>CmMtrCurr_CurrCorrDiag_Amp_D_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>CmMtrCurr_FiltCurrCorrDiag_Amp_D_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>CmMtrCurr_ CurrentGainSvc_Cnt_M_lgc</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="odd">
<td>CmMtrCurr_CurrCorrDiagKSV_M_str</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="even">
<td>CurrCorrDiagKSV_M_str.SV_Uls_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="odd">
<td>CurrCorrDiagKSV_M_str.K_Uls_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="even">
<td>CmMtrCurr_MtrCurr1LpFltrSV_Volt_M_u3p29</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>CmMtrCurr_MtrCurr2LpFltrSV_Volt_M_u3p29</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>CmMtrCurr_FiltMtrCurr1_Volt_M_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>CmMtrCurr_FiltMtrCurr2_Volt_M_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>CmMtrCurr_MtrCurr1SumHi_Volt_M_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>CmMtrCurr_MtrCurr2SumHi_Volt_M_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>CmMtrCurr_MtrCurr1SumLo_Volt_M_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>CmMtrCurr_MtrCurr2SumLo_Volt_M_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>CmMtrCurr_MtrCurr1SumZero_Volt_M_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>CmMtrCurr_MtrCurr2SumZero_Volt_M_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>CmMtrCurr_VecuSum_Volt_M_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>CmMtrCurr_MtrCurr1OffsetHi_Volt_M_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>CmMtrCurr_MtrCurr2OffsetHi_Volt_M_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>CmMtrCurr_MtrCurr1OffsetLo_Volt_M_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>CmMtrCurr_MtrCurr2OffsetLo_Volt_M_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>CmMtrCurr_MtrCurr1OffsetZero_Volt_M_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>CmMtrCurr_MtrCurr2OffsetZero_Volt_M_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>CmMtrCurr_MtrCurrValCmd_VoltCnt_M_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>CmMtrCurr_MtrCurr1OffDelta_VoltpVoltCnt_M_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>CmMtrCurr_MtrCurr2OffDelta_VoltpVoltCnt_M_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>CmMtrCurr_CurrOffAvgCounter_Cnt_M_u16</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="odd">
<td>CmMtrCurr_CurrOffState_Uls_M_enum</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="even">
<td>CmMtrCurr_CurroffProcessFlag_M_enum</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="odd">
<td>CmMtrCurr_CurrOffTrimFlag_Cnt_M_lgc</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="even">
<td>CmMtrCurr_MtrCurr1Offset_Volt_D_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>CmMtrCurr_MtrCurr2Offset_Volt_D_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>CmMtrCurr_CorrMtrCurr1_Amp_D_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>CmMtrCurr_CorrMtrCurr2_Amp_D_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CMMTRCURR_START_SEC_VAR_CLEARED_32</td>
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
<td>CurrTempOffsetType</td>
<td>CurrTempOffsetX_DegC_s10p5</td>
<td>CurrTempOffsetTblType</td>
<td>-50</td>
<td>150</td>
</tr>
<tr class="even">
<td></td>
<td>CurrOffsetY1_Volts_s4p11</td>
<td>CurrTempOffsetTblType</td>
<td>-0.026</td>
<td>0.026</td>
</tr>
<tr class="odd">
<td></td>
<td>CurrOffsetY2_Volts_s4p11</td>
<td>CurrTempOffsetTblType</td>
<td>-0.026</td>
<td>0.026</td>
</tr>
<tr class="even">
<td>PhaseCurrCal_DataType</td>
<td>EOLMtrCurrVcalCmd_VoltCnts_f32</td>
<td>float</td>
<td>0</td>
<td>80000</td>
</tr>
<tr class="odd">
<td></td>
<td>EOLPhscurr1Gain_AmpspVolt_f32</td>
<td>float</td>
<td>20</td>
<td>125</td>
</tr>
<tr class="even">
<td></td>
<td>EOLMtrCurr2OffsetDiff_Volts_f32</td>
<td>float</td>
<td>1.0</td>
<td>3.0</td>
</tr>
<tr class="odd">
<td></td>
<td>EOLMtrCurr1OffsetDiff_Volts_f32</td>
<td>float</td>
<td>1.0</td>
<td>3.0</td>
</tr>
<tr class="even">
<td></td>
<td>EOLMtrCurr1OffsetLo_Volts_f32</td>
<td>float</td>
<td>1.0</td>
<td>3.0</td>
</tr>
<tr class="odd">
<td></td>
<td>EOLMtrCurr2OffsetLo_Volts_f32</td>
<td>float</td>
<td>1.0</td>
<td>3.0</td>
</tr>
<tr class="even">
<td></td>
<td>EOLPhscurr2Gain_AmpspVolt_f32</td>
<td>float</td>
<td>20</td>
<td>125</td>
</tr>
<tr class="odd">
<td>CurrTempOffsetTblType[16]</td>
<td></td>
<td>Sint16</td>
<td>Full</td>
<td>Full</td>
</tr>
</tbody>
</table>

# Constant Data Dictionary

## Calibration Constants

This section lists the calibrations used by the module. For details on
calibration constants, refer to the Data Dictionary for the application.

| Constant Name                      |
|------------------------------------|
| k_CurrCorrErrFiltFc_Hz_f32         |
| k_CurrCorrErrThresh_Amps_f32       |
| k_MtrPosComputDelay_Sec_f32        |
| k_MtrCurrEOLMinOffset_Volts_f32    |
| k_MtrCurrEOLMaxOffset_Volts_f32    |
| k_MtrCurrEOLMinGain_AmpspVolts_f32 |
| k_MtrCurrEOLMaxGain_AmpspVolts_f32 |
| k_CurrGainNumerator_Amps_f32       |
| k_MaxCurrOffMtrVel_RadpS_f32       |
| k_CurrOffGainKn_Cnt_u16            |
| k_CurrCorrErrFiltFc_Hz_f32         |
| k_CurrCorrErrThresh_Amps_f32       |
| k_MtrPosComputDelay_Sec_f32        |
| k_MtrCurrOffLoComOff_Cnt_u16       |
| k_CurrOffNoofAvg_Cnt_u16           |

## Program(fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

| Constant Name                  | Resolution             | Units     | Value                                                                                             |
|-------------------------------|--------------|--------------|--------------|
| D_ADCREF_VOLT_F32              | Single Precision float | Volt      | 5.0F                                                                                              |
| D_ADCFULLSCALE_CNT_U16         | 1                      | Cnt       | 4095U                                                                                             |
| D_SCALERADTOCNTS_ULS_F32       | Single Precision float | Uls       | 10430.3783505F                                                                                    |
| D_REVWITHROUND_ULS_F32         | Single Precision float | Uls       | 65536.5F                                                                                          |
| D_ROUND_ULS_F32                | Single Precision float | Uls       | 0.5F                                                                                              |
| D_ADCCOMPOFFSAMPLESIZE_CNT_U16 | 1                      | Cnt       | 256u                                                                                              |
| D_SCALE_VOLTSPERCOUNT_F32      | Single Precision float | VoltspSec | (D_ADCREF_VOLT_F32/((float32)D_ADCFULLSCALE_CNT_U16 \* (float32) D_ADCCOMPOFFSAMPLESIZE_CNT_U16)) |
| D_CNVRTP29TOP13_CNT_U16        | 1                      | Cnt       | 16U                                                                                               |
| D_30DEGREES_CNT_U16            | 1                      | Cnt       | 5461U                                                                                             |
| D_ONEDIVSQRT3_F32              | Single Precision float | Cnt       | 0.57735F                                                                                          |
| D_POSITIVEONE_CNT_S8           | 1                      | Cnt       | 1                                                                                                 |
| D_CURRDQMAX_AMP_F32            | Single Precision float | Amp       | 220                                                                                               |
| D_MTRCURROFFHICOMOFF_CNT_U16   | 1                      | Cnt       | 4000U                                                                                             |
| D_MTRCURROFFLOCOMOFF_CNT_U16   | 1                      | Cnt       | 500U                                                                                              |
| D_CURROFFNOOFAVG_CNT_U16       | 1                      | Cnt       | 64U                                                                                               |
| D_MTRCURROFFZEROCOMOFF_CNT_U16 | 1                      | Cnt       | 0U                                                                                                |
| D_MINVCALCMD_CNT_F32           | Single Precision float | Cnt       | 17500.0F                                                                                          |
|                                |                        |           |                                                                                                   |
|                                |                        |           |                                                                                                   |

####  [section]

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

| Constant Name         |
|-----------------------|
| D_2PI_ULS_F32         |
| D_FALSE_CNT_LGC       |
| D_VECUMIN_VOLTS_F32   |
| D_ZERO_ULS_F32        |
| D_ZERO_CNT_U16        |
| D_ZERO_CNT_U32        |
| D_MTRPOLESDIV2_CNT_U8 |
| D_2MS_SEC_F32         |

### Module specific Lookup Tables Constants

(This is for lookup tables (arrays) with fixed values, same name as
other tables)

| Constant Name | Resolution | Value | Software Segment |
|---------------|------------|-------|------------------|
| None          |            |       |                  |

#  Functions/Macros used by the Sub-Modules 

## Library Functions / Macros 

The library and functions / Macros that are called by the various sub
modules are identified below,

1.  Cosf

2.  Sinf

3.  Limit_m

4.  Abs_f32_m

5.  TableSize_m

6.  FPM_FloatToFixed_m

7.  FPM_FixedToFloat_m

8.  IntplVarXY_s16_s16Xs16Y_Cnt

9.  LPF_SvUpdate_u16InFixKTrunc_m

10. LPF_OpUpdate_u16InFixKTrunc_m

11. LPF_SvUpdate_s16InFixKTrunc_m

12. LPF_OpUpdate_s16InFixKTrunc_m

13. LPF_KUpdate_f32_m

14. LPF_OpUpdate_f32_m

## Data Hiding Functions

1.  CmMtrCurr_Read_MRFMtrVel_MtrRadpS_f32

2.  CmMtrCurr_Read_Vecu_Volt_f32

3.  CmMtrCurr_Read_Phs1Curr_Cnt_u16

4.  CmMtrCurr_Read_Phs2Curr_Cnt_u16

5.  CmMtrCurr_Read_DCPhsAComp_Cnt_u16

6.  CmMtrCurr_Read_DCPhsBComp_Cnt_u16

7.  CmMtrCurr_Read_DCPhsCComp_Cnt_u16

8.  CmMtrCurr_Read_MtrCurr1TempOffset_Volt_f32

9.  CmMtrCurr_Read_MtrCurr2TempOffset_Volt_f32

10. CmMtrCurr_Read_MtrElecPol_Cnt_s08

11. CmMtrCurr_Read_MtrPosElec_Rev_u0p16

12. CmMtrCurr_Write_ElecPosDelayComp_Rad_f32

13. CmMtrCurr_Write_MtrCurrQax_Amp_f32

14. CmMtrCurr_Write_MtrCurrDax_Amp_f32

15. CmMtrCurr_Write_CorrMtrPosElec_Rev_f32

16. CmMtrCurr_Write_MtrCurrK1_Amps_f32

17. CmMtrCurr_Write_MtrCurrK2_Amps_f32

18. CmMtrCurr_Write_MtrCurr1_Volts_f32

19. CmMtrCurr_Write_MtrCurr2_Volts_f32

## Global Functions/Macros Defined by this Module

None

## Local Functions/Macros Used by this MDD only

None

# Software Module Implementation

## Runtime Environment (RTE) Initial Values

This section lists the initial values of data written by this module but
controlled by the RTE. After RTE initialization, the data in this table
will contain these values.

| Data                        | Value |
|-----------------------------|-------|
| Rte_InitValue_Vecu_Volt_f32 | 5     |

## Initialization Functions

### Init: CmMtrCurr_Init

#### Design Rationale

None

#### Module Outputs

None

#### Module Internal 

## IF ((Rte_Pim_ShCurrCal()-\>EOLMtrCurrVcalCmd_VoltCnts_f32) \>= D_MINVCALCMD_CNT_F32) [if-rte_pim_shcurrcal-eolmtrcurrvcalcmd_voltcnts_f32-d_minvcalcmd_cnt_f32]

##  [section-1]

CmMtrCurr_MtrCurr1OffDelta_VoltpVoltCnt_M_f32 =
((Rte_Pim_ShCurrCal()-\>EOLMtrCurr1OffsetDiff_Volts_f32) /
(Rte_Pim_ShCurrCal()-\>EOLMtrCurrVcalCmd_VoltCnts_f32))

CmMtrCurr_MtrCurr2OffDelta_VoltpVoltCnt_M_f32 =
((Rte_Pim_ShCurrCal()-\>EOLMtrCurr2OffsetDiff_Volts_f32) /
(Rte_Pim_ShCurrCal()-\>EOLMtrCurrVcalCmd_VoltCnts_f32))

## ELSE [else]

## CmMtrCurr_MtrCurr1OffDelta_VoltpVoltCnt_M_f32 = D_ZERO_ULS_F32 [cmmtrcurr_mtrcurr1offdelta_voltpvoltcnt_m_f32-d_zero_uls_f32]

## CmMtrCurr_MtrCurr2OffDelta_VoltpVoltCnt_M_f32 = D_ZERO_ULS_F32 [cmmtrcurr_mtrcurr2offdelta_voltpvoltcnt_m_f32-d_zero_uls_f32]

## END [end]

##  [section-2]

LPF_KUpdate_f32_m(k_CurrCorrErrFiltFc_Hz_f32, D_2MS_SEC_F32,
&CmMtrCurr_CurrCorrDiagKSV_M_str)

## Periodic Functions

### Per: CmMtrCurr_Per1

#### Design Rationale

None

#### Program Flow Start

Rte_Call_CmMtrCurr_Per1_CP0_CheckpointReached()

#### Store Module Inputs to Local copies

*FiltCntrlTemp_DegC_T_f32=Rte_IRead_CmMtrCurr_Per1_FiltCntrlTemp_DegC_f32()*

#### Processing

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/CmMtrCurr/doc/mediax/media/image1.emf)

#### Store Local copy of outputs into Module Outputs

Rte_Iwrite_CmMtrCurr_Per1_MtrCurr1TempOffset_Volt_f32(MtrCurr1TempOffset_Volts_T_f32)

Rte_Iwrite_CmMtrCurr_Per1_MtrCurr2TempOffset_Volt_f32(MtrCurr2TempOffset_Volts_T_f32)

#### Program Flow End

Rte_Call_CmMtrCurr_Per1_CP1_CheckpointReached()

### Per: CmMtrCurr_Per2

#### Design Rationale

None

#### Program Flow Start

Rte_Call_CmMtrCurr_Per2_CP0_CheckpointReached()

#### Store Module Inputs to Local copies

MtrCurrAlpha_Rev_T_f32=Rte_Iread_CmMtrCurr_Per2_MtrCurrAngle\_ Rev_f32()

CorrMtrPosElec_Rev_T_f32=Rte_Iread_CmMtrCurr_Per2_CorrMtrCurrPosition_Rev_f32()

MtrCurrK1_Amps_T_f32=Rte_Iread_CmMtrCurr_Per2_MtrCurrK1_Amp_f32()

MtrCurrK2_Amps_T_f32=Rte_Iread_CmMtrCurr_Per2_MtrCurrK2_Amp_f32()

ADCMtrCurr1_Volts_T_f32=Rte_Iread_CmMtrCurr_Per2_ADCMtrCurr1_Volts_f32()

ADCMtrCurr2_Volts_T_f32=Rte_Iread_CmMtrCurr_Per2_ADCMtrCurr2_Volts_f32()

#### Processing

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/CmMtrCurr/doc/mediax/media/image2.emf)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

Rte_Call_CmMtrCurr_Per2_CP1_CheckpointReached()

### Per: CmMtrCurr_Per3

#### Design Rationale

None

#### Program Flow Start

Rte_Call_CmMtrCurr_Per3_CP0_CheckpointReached()

#### Store Module Inputs to Local copies

ADCMtrCurr1_Volts_T_f32=Rte_Iread_CmMtrCurr_Per3_ADCMtrCurr1_Volts_f32()

ADCMtrCurr2_Volts_T_f32=Rte_Iread_CmMtrCurr_Per3_ADCMtrCurr2_Volts_f32()

Vecu_Volt_T_f32=Rte_Iread_CmMtrCurr_Per3_Vecu_Volt_f32()

MtrVel_MtrRadpS_T_f32 = Rte_Iread_CmMtrCurr_Per3_MtrVel_MtrRadpS_f32()

VehSpd_Kph_T_f32= Rte_Iread_CmMtrCurr_Per3_VehSpd_Kph_f32()

VhSpdValid_Cnt_T_lgc= Rte_Iread_CmMtrCurr_Per3_VhSpdValid_Cnt_lgc()

SrlComSvcDft_Cnt_T_b32=Rte_Iread_CmMtrCurr_Per3_SrlComSvcDft_Cnt_b32()

CurroffProcessFlag_T_enum = CmMtrCurr_CurroffProcessFlag_M_enum

#### Processing

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/CmMtrCurr/doc/mediax/media/image3.emf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/CmMtrCurr/doc/mediax/media/image6.emf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/CmMtrCurr/doc/mediax/media/image7.emf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/CmMtrCurr/doc/mediax/media/image8.emf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/CmMtrCurr/doc/mediax/media/image9.emf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/CmMtrCurr/doc/mediax/media/image10.emf)

#### Store Local copy of outputs into Module Outputs

Rte_Iwrite_CmMtrCurr_Per3_ComOffset_Cnt_u16(ComOffset_Cnt_T_u16)

#### Program Flow End

Rte_Call_CmMtrCurr_Per3_CP1_CheckpointReached()

##  Fault Recovery Functions

None

## Shutdown Functions

None

## Interrupt Functions

### CurrDQPer1

#### Design Rationale

None

#### Program Flow Start

N/A

#### Store Module Inputs to Local Copies

CmMtrCurr_Read_MRFMtrVel_MtrRadpS_f32(&MRFMtrVel_MtrRadpS_T_f32)

CmMtrCurr_Read_Vecu_Volt_f32(&Vecu_Volt_T_f32)

CmMtrCurr_Read_Phs1Curr_Cnt_u16(&Phs1Curr_Cnt_T_u16)

CmMtrCurr_Read_Phs2Curr_Cnt_u16(&Phs2Curr_Cnt_T_u16)

CmMtrCurr_Read_MtrCurr1TempOffset_Volt_f32(&MtrCurr1TempOffset_Volt_T_f32)

CmMtrCurr_Read_MtrCurr2TempOffset_Volt_f32(&MtrCurr2TempOffset_Volt_T_f32)

CmMtrCurr_Read_MtrElecPol_Cnt_s08(&MtrElecPol_Cnt_T_s08)

CmMtrCurr_Read_MtrPosElec_Rev_u0p16(&MtrPosElec_Rev_T_u0p16)

CmMtrCurr_Read_ADC2OffsetComp_Cnt_u8p8(&ADC2OffsetComp_Cnt_T_u8p8)

Phs1Curr_Volts_T_f32 = D_ZERO_ULS_F32

Phs2Curr_Volts_T_f32 = D_ZERO_ULS_F32

#### Processing

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/CmMtrCurr/doc/mediax/media/image11.emf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/CmMtrCurr/doc/mediax/media/image12.emf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/CmMtrCurr/doc/mediax/media/image13.emf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/CmMtrCurr/doc/mediax/media/image14.emf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/CmMtrCurr/doc/mediax/media/image15.emf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/CmMtrCurr/doc/mediax/media/image16.emf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/CmMtrCurr/doc/mediax/media/image17.emf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/CmMtrCurr/doc/mediax/media/image18.emf)
![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/CmMtrCurr/doc/mediax/media/image19.emf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/CmMtrCurr/doc/mediax/media/image20.emf)

#### Store Local copy of outputs into Module Outputs

CmMtrCurr_Write_ElecPosDelayComp_Rad_f32(ElecPosDelayComp_Rad_T_f32)

CmMtrCurr_Write_MtrCurrQax_Amp_f32(MtrCurrFinalQax_Amps_T_f32)

CmMtrCurr_Write_MtrCurrDax_Amp_f32(MtrCurrFinalDax_Amps_T_f32)

CmMtrCurr_Write_CorrMtrPosElec_Rev_f32(CorrMtrPosElec_Rev_T_f32)

CmMtrCurr_Write_MtrCurrK1_Amps_f32(MtrCurrK1_Amps_T_f32)

CmMtrCurr_Write_MtrCurrK2_Amps_f32(MtrCurrK2_Amps_T_f32)

CmMtrCurr_Write_MtrCurr1_Volts_f32(Phs1Curr_Volts_T_f32)

CmMtrCurr_Write_MtrCurr2_Volts_f32(Phs2Curr_Volts_T_f32)

#### Program Flow End

N/A

## Serial Communication Functions

### Scomm: CmMtrCurrTempOffset_Scom_Get

<table>
<colgroup>
<col style="width: 19%" />
<col style="width: 39%" />
<col style="width: 19%" />
<col style="width: 8%" />
<col style="width: 7%" />
<col style="width: 6%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Function Name</strong></td>
<td><h3 id="cmmtrcurrtempoffset_scom_get"
class="unnumbered">CmMtrCurrTempOffset_Scom_Get</h3></td>
<td>Type</td>
<td>Min</td>
<td>Max</td>
<td>UTP Tol.</td>
</tr>
<tr class="even">
<td><strong>Arguments Passed</strong></td>
<td>CurrTempOffCal</td>
<td>CurrTempOffsetType *</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><strong>Return Value</strong></td>
<td>void</td>
<td>NA</td>
<td>NA</td>
<td>NA</td>
<td></td>
</tr>
</tbody>
</table>

#### Design Rationale

None

#### Program Flow Start

None

#### Store Module Inputs to Local copies

None

#### Processing

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/CmMtrCurr/doc/mediax/media/image21.emf)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

None

### Scomm: CmMtrCurrTempOffset_Scom_Set

|                      |                              |                       |     |     |          |
|--------------|---------------------------|--------------|-------|------|------|
| **Function Name**    | CmMtrCurrTempOffset_Scom_Set | Type                  | Min | Max | UTP Tol. |
| **Arguments Passed** | CurrTempOffCal               | CurrTempOffsetType \* |     |     |          |
| **Return Value**     | void                         | NA                    | NA  | NA  |          |

#### Design Rationale

None

#### Program Flow Start

None

#### Store Module Inputs to Local copies

None

#### Processing

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/CmMtrCurr/doc/mediax/media/image22.emf)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

None

### Scomm: CmMtrCurr_Scom_CalGain

|                      |                        |                |     |     |          |
|---------------|----------------------------|------------|-------|-------|------|
| **Function Name**    | CmMtrCurr_Scom_CalGain | Type           | Min | Max | UTP Tol. |
| **Arguments Passed** | None                   | None           |     |     |          |
| **Return Value**     | RetrunValue            | Std_ReturnType |     |     |          |

#### Design Rationale

None

#### Program Flow Start

None

#### Store Module Inputs to Local copies

Rte_Read_MtrVel_MtrRadpS_f32(&MtrVel_MtrRadpS_T_f32)

Rte_Read_VehSpd_Kph_f32(&VehSpd_Kph_T_f32)

Rte_Read_VhSpdValid_Cnt_lgc(&VhSpdValid_T_Cnt_lgc)

#### Processing

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/CmMtrCurr/doc/mediax/media/image23.emf)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

None

### Scomm: CmMtrCurr_Scom_CalOffset

|                      |                          |                |     |     |          |
|---------------|----------------------------|------------|-------|-------|------|
| **Function Name**    | CmMtrCurr_Scom_CalOffset | Type           | Min | Max | UTP Tol. |
| **Arguments Passed** | None                     | None           |     |     |          |
| **Return Value**     | RetrunValue              | Std_ReturnType |     |     |          |

#### Design Rationale

None

#### Program Flow Start

None

#### Store Module Inputs to Local copies

Rte_Read_MtrVel_MtrRadpS_f32(&MtrVel_MtrRadpS_T_f32)

Rte_Read_VehSpd_Kph_f32(&VehSpd_Kph_T_f32)

Rte_Read_VhSpdValid_Cnt_lgc(&VhSpdValid_T_Cnt_lgc)

#### Processing

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/CmMtrCurr/doc/mediax/media/image24.emf)

#### Store Local copy of outputs into Module Outputs

Rte_Write_CurrentGainSvc_Cnt_lgc(CmMtrCurr_CurrentGainSvc_Cnt_M_lgc)

#### Program Flow End

None

### Scomm: CmMtrCurr_Scom_MtrCurrOffReadStatus

|                      |                                     |                          |     |     |          |
|-------------|----------------------------|---------------|------|------|------|
| **Function Name**    | CmMtrCurr_Scom_MtrCurrOffReadStatus | Type                     | Min | Max | UTP Tol. |
| **Arguments Passed** | CurrOffStatus                       | MtrCurrOffProcessFlag \* |     |     |          |
| **Return Value**     | void                                | NA                       | NA  | NA  |          |

#### Design Rationale

None

#### Program Flow Start

None

#### Store Module Inputs to Local copies

None

#### Processing

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/CmMtrCurr/doc/mediax/media/image25.emf)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

None

### Scomm: CmMtrCurr_Scom_ReadMtrCurrCals

|                      |                                |                          |     |     |          |
|-------------|---------------------------|----------------|------|------|------|
| **Function Name**    | CmMtrCurr_Scom_ReadMtrCurrCals | Type                     | Min | Max | UTP Tol. |
| **Arguments Passed** | ShCurrCalPtr                   | PhaseCurrCal_DataType \* |     |     |          |
| **Return Value**     | void                           | NA                       | NA  | NA  |          |

#### Design Rationale

None

#### Program Flow Start

None

#### Store Module Inputs to Local copies

None

#### Processing

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/CmMtrCurr/doc/mediax/media/image26.emf)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

None

### Scomm: CmMtrCurr_Scom_SetMtrCurrCals

|                      |                               |                          |     |     |          |
|-------------|---------------------------|----------------|------|------|------|
| **Function Name**    | CmMtrCurr_Scom_SetMtrCurrCals | Type                     | Min | Max | UTP Tol. |
| **Arguments Passed** | ShCurrCalPtr                  | PhaseCurrCal_DataType \* |     |     |          |
| **Return Value**     | void                          | NA                       | NA  | NA  |          |

#### Design Rationale

None

#### Program Flow Start

None

#### Store Module Inputs to Local copies

None

#### Processing

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/CmMtrCurr/doc/mediax/media/image27.emf)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

None

##  

# Execution Requirements

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

| Function Name  | Calling Frequency   | System State(s) in which the function is called |
|--------------------------|-----------------|------------------------------|
| CmMtrCurr_Init | On Init             | Init                                            |
| CmMtrCurr_Per1 | 100ms               | All                                             |
| CmMtrCurr_Per2 | 2ms                 | Operate                                         |
| CmMtrCurr_Per3 | 2ms                 | Operate                                         |
| CurrDQPer1     | 125us (MtrCtrl ISR) | All                                             |

## Execution Requirements for Serial Communication Functions 

| Function Name                       | Sub-Module called by (Serial Comm Function Name) |
|-----------------------------|-------------------------------------------|
| CmMtrCurr_Scom_CalGain              |                                                  |
| CmMtrCurr_Scom_CalOffset            |                                                  |
| CmMtrCurr_Scom_MtrCurrOffReadStatus |                                                  |
| CmMtrCurr_Scom_ReadMtrCurrCals      |                                                  |
| CmMtrCurr_Scom_SetMtrCurrCals       |                                                  |
| CmMtrCurrTempOffset_Scom_Get        |                                                  |
| CmMtrCurrTempOffset_Scom_Set        |                                                  |
|                                     |                                                  |

#  [section-4]

#  Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

| Name of Sub Module                  | Software Segment                     |
|------------------------------------|------------------------------------|
| CmMtrCurr_Init                      | RTE_START_SEC_SA_CMMTRCURR_APPL_CODE |
| CmMtrCurr_Per1                      | RTE_START_SEC_SA_CMMTRCURR_APPL_CODE |
| CmMtrCurr_Per2                      | RTE_START_SEC_SA_CMMTRCURR_APPL_CODE |
| CmMtrCurr_Per3                      | RTE_START_SEC_SA_CMMTRCURR_APPL_CODE |
| CurrDQPer1                          |                                      |
| CmMtrCurr_Scom_CalGain              | RTE_START_SEC_SA_CMMTRCURR_APPL_CODE |
| CmMtrCurr_Scom_CalOffset            | RTE_START_SEC_SA_CMMTRCURR_APPL_CODE |
| CmMtrCurr_Scom_MtrCurrOffReadStatus | RTE_START_SEC_SA_CMMTRCURR_APPL_CODE |
| CmMtrCurr_Scom_ReadMtrCurrCals      | RTE_START_SEC_SA_CMMTRCURR_APPL_CODE |
| CmMtrCurr_Scom_SetMtrCurrCals       | RTE_START_SEC_SA_CMMTRCURR_APPL_CODE |
| CmMtrCurrTempOffset_Scom_Get        | RTE_START_SEC_SA_CMMTRCURR_APPL_CODE |
| CmMtrCurrTempOffset_Scom_Set        | RTE_START_SEC_SA_CMMTRCURR_APPL_CODE |

##  [section-5]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

| Name of Sub Module | Software Segment |
|--------------------|------------------|
|                    |                  |

#  [section-6]

#  Known Issues / Limitations With Design

1.  INLINE functions defined in GlobalMacro.h are not unit tested.

2.  ADC component outputs the ADC calibration compensation which is in
    turn used by Current Measurement to correct its offset volt . This
    is implementation done across two components. The measured currents
    from ADC conversion from counts to volts is done in this component
    instead of ADC component as described by the FDD

3.  

#  Revision Control Log

|            |                                                                                                                        |            |                     |
|------|-----------------------------------------------|---------|----------|
| **Rev \#** | **Change Description**                                                                                                 | **Date**   | **Author Initials** |
| 1.0        | Initial Version (FDD 01 C Ver 005)                                                                                     | 01-Dec-12  | Selva               |
| 2.0        | Configured global read/write macros for global data (anomaly 4696)                                                     | 23-Mar-13  | OT                  |
| 3.0        | Fixes for Anamoly 5561 and A5566 added                                                                                 | 4-Sep-13   | Selva               |
| 4.0        | Updated to FDD 01C Ver 006                                                                                             | 07-Oct-13  | VK                  |
| 5.0        | Anomaly 5967 and 5873                                                                                                  | 06-Nov-13  | SP                  |
| 6.0        | Range corrections for ‘MtrCurr1OffDelta_VoltpVoltCnts_M_f32’ and ‘MtrCurr2OffDelta_VoltpVoltCnts_M_f32’                | 9-Nov-13   | SR                  |
| 7.0        | Changed CurrCorrDiag filtering from fixed point to floating point to achieve specified range and resolution – CR 10895 | 20-Nov-13  | KMC                 |
| 8.0        | Updated for FDD 01C v007                                                                                               | 20-Apr-14  | Selva               |
| 9.0        | Updated for FDD 01C v008                                                                                               | 27-June-14 | Selva               |

{% endraw %}