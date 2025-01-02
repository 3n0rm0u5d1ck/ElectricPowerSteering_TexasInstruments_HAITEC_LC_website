---
layout: default
title: Damping_Firewall_MDD
nav_order: 1
parent: Damping Firewall (Safety)
---
{% raw %}
# Module – Damping Firewall [module-damping-firewall]

# High-Level Description

This module regulates the damping command according to safety
specifications.

# Figures

## Component Diagram

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DampingFirewall/doc/mediax/media/image1.png"
style="width:3.89514in;height:4.22847in" />

# Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

|                                |                |                           |
|-----------------------------------|--|------------------------------------|
| Module Inputs                  | Module Outputs |                           |
| AsstFirewallActive_Uls_f32     |                | CombinedDamping_MtrNm_f32 |
| DampingCmd_MtrNm_f32           |                |                           |
| HwTorque_HwNm_f32              |                |                           |
| InertiaComp_MtrNm_f32          |                |                           |
| MtrVelCRF_MtrRadpS_f32         |                |                           |
| VehicleSpeed_Kph_f32           |                |                           |
| BaseAssistCmd_MtrNm_f32        |                |                           |
| WIRCmdAmpBlnd_MtrNm_f32        |                |                           |
| FreqDepDmpSrlComSvcDft_Cnt_lgc |                |                           |
| VehicleLonAccel_KphpS_f32      |                |                           |
| Defeat_Damping_Svc_Cnt_lgc     |                |                           |
| MEC_Counter_Cnt_enum           |                |                           |

## Module Internal Variables

This section identifies the name, range and resolutions for module
specific data created by this module. If there are no range restrictions
on the variable, the term “FULL” is placed into the table for legal
range.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 15%" />
<col style="width: 13%" />
<col style="width: 13%" />
<col style="width: 25%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Variable Name</td>
<td>Resolution</td>
<td><p>Legal Range</p>
<p>(min)</p></td>
<td><p>Legal Range</p>
<p>(max)</p></td>
<td>Software Segment</td>
</tr>
<tr class="even">
<td>DampFWVBICErrFiltSv_M_str</td>
<td>LPF32KSV_Str</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="odd">
<td>DampFWActiveKSV_M_str</td>
<td>LPF32KSV_Str</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="even">
<td>DampFWUprBoundKSV_M_str</td>
<td>LPF32KSV_Str</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="odd">
<td>DampFWLwrBoundKSV_M_str</td>
<td>LPF32KSV_Str</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="even">
<td>DampFWUprBoundFilt_MtrNm_D_f32</td>
<td>Single Precision Float</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>DampFWLwrBoundFilt_MtrNm_D_f32</td>
<td>Single Precision Float</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>DampFWUprBound_MtrNm_D_f32</td>
<td>Single Precision Float</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>DampFWLwrBound_MtrNm_D_f32</td>
<td>Single Precision Float</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>DampFWAddedDamp_MtrNm_D_f32</td>
<td>Single Precision Float</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>DampFWAddedDampAFW_MtrNm_D_f32</td>
<td>Single Precision Float</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>DampFWAddedDampDFW_MtrNm_D_f32</td>
<td>Single Precision Float</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>DampFWTbarVelFiltSv_M_str</td>
<td>LPF32KSV_Str</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="even">
<td>DampFWSatDamp_MtrNm_D_f32</td>
<td>Single Precision Floating Point</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>DampFWPrevTbarAng_HwDeg_M_s6p9</td>
<td>2^-9</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td>DampFWPrev1SclDrvVel_MtrRadpS_M_s14p1</td>
<td>2^-1</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="odd">
<td>DampFWPrev2SclDrvVel_MtrRadpS_M_s14p1</td>
<td>2^-1</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td>DampFWPrev1PreAttnComp_MtrNm_M_s9p6</td>
<td>2^-6</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="odd">
<td>DampFWPrev2PreAttnComp_MtrNm_M_s9p6</td>
<td>2^-6</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td>DampFWOverBound_Uls_D_lgc</td>
<td>N/A</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="odd">
<td>ReducedPerfSV_Cnt_M_lgc</td>
<td>N/A</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="even">
<td>DampFWVBICOverThresh_Cnt_D_lgc</td>
<td>N/A</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="odd">
<td>DampFWVBICReducedPerfSV_Cnt_M_lgc</td>
<td>N/A</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="even">
<td>DampFWDiverseVBIC_MtrNm_D_f32</td>
<td>Single Precision Floating Point</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>DampFWDefltDamp_MtrNm_D_f32</td>
<td>Single Precision Floating Point</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>DampFWDampActive_Uls_D_f32</td>
<td>Single Precision Floating Point</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>DampFWLimitedVBIC_MtrNm_D_f32</td>
<td>Single Precision Floating Point</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>DampFWInrtCmpPNStatus_Cnt_M_lgc</td>
<td>N/A</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="odd">
<td>DampFWPNCountStatus_Cnt_M_lgc</td>
<td>N/A</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="even">
<td>InrtCmpPNAccum_Cnt_M_u16</td>
<td>UINT16</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="odd">
<td>DampPNAcc_Cnt_M_u16</td>
<td>UNIT16</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td>PNAcc_Cnt_M_u16</td>
<td>1</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="odd">
<td>DampFWOverBound_Cnt_D_lgc</td>
<td>N/A</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="even">
<td>LimitedDamp_MtrNm_D_f32</td>
<td>Single Precision Floating Point</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>DriverVel_MtrRadpSec_D_s24p7</td>
<td>2^-7</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>PrevDecelGain_Uls_M_u5p11</td>
<td>2^-11</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="odd">
<td>PrevRawDecelGain_Uls_M_u5p11</td>
<td>2^-11</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td>FiltFreq_RadpS_D_s10p5</td>
<td>2^-5</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="odd">
<td>ScaledDriverVel_MtrRadpS_D_s14p1</td>
<td>2^-1</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td>OutputAtten_Uls_D_u8p8</td>
<td>2^-8</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="odd">
<td>RawDecelGain_Uls_D_u5p11</td>
<td>2^-11</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td>DecelGain_Uls_D_u5p11</td>
<td>2^-11</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="odd">
<td>ADDCoefCalc_MtrNmSpRad_D_u0p16</td>
<td>2^-16</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td>InertiaCompCalc_MtrNm_D_u9p7</td>
<td>2^-7</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="odd">
<td>PreFiltVBICError_MtrNm_D_f32</td>
<td>0</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>PostFiltVBICError_MtrNm_D_f32</td>
<td>0</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>DampFWPrev1PreAttnComp_MtrNm_M_s20p11</td>
<td>2^-11</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>DampFWPrev2PreAttnComp_MtrNm_M_s20p11</td>
<td>2^-11</td>
<td>see Data Dictionary</td>
<td>see Data Dictionary</td>
<td>DAMPINGFIREWALL_START_SEC_VAR_CLEARED_32</td>
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
<tbody>
<tr class="odd">
<td>Typedef Name</td>
<td>Element Name</td>
<td>User Defined Type</td>
<td><p>Legal Range</p>
<p>(min)</p></td>
<td><p>Legal Range</p>
<p>(max)</p></td>
</tr>
<tr class="even">
<td></td>
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

|                                                   |
|---------------------------------------------------|
| Constant Name                                     |
| k_DampFWInpLimitDamp_MtrNm_f32                    |
| k_DampFWVBICLPF_Hz_f32                            |
| k_DampFWFWActiveLPF_Hz_f32                        |
| k_DampFWTbarVelLPFKn_Hz_f32                       |
| k_DmpBoundLPFKn_Hz_f32                            |
| k_DampFWMtrVelScale_Uls_f32                       |
| t_DampFWEstCompTblX_Kph_u9p7\[\]                  |
| t_DampFWTbarVelScaleY_Uls_u2p14\[\]               |
| k_DampFWFilkKn_Hz_f32                             |
| t_DampFWEstCompHPF_Hz_u7p9\[\]                    |
| t_DampFWEstCompGain_MtrNmpMtrRadpS_u1p15\[\]      |
| t_DampFWVehSpd_Kph_u9p7\[\]                       |
| t2_DampFWUprBoundX_MtrRadpS_s10p5\[\]\[\]         |
| t2_DampFWUprBoundY_MtrNm_s4p11\[\]\[\]            |
| t_DampFWAddDampX_MtrRadpS_u11p5\[\]               |
| t_DampFWAddDampY_MtrNm_u5p11\[\]                  |
| t_DampFWDefltDampX_MtrRadpS_u11p5\[\]             |
| t_DampFWDefltDampY_MtrNm_u5p11\[\]                |
| k_DampFWErrThresh_MtrNm_f32                       |
| t_DampFWDampInrtCmpPNThesh_Cnt_u16\[\]            |
| k_DampFWInCmpPStep_Cnt_u16                        |
| k_DampFWInCmpNStep_Cnt_u16                        |
| k_InrtCmp_TBarVelLPFKn_Hz_f32                     |
| k_DampFWPstep_Cnt_u16                             |
| k_DampFWNstep_Cnt_u16                             |
| t_DampFWPNstepThresh_Cnt_u16\[\]                  |
| k_InrtCmp_MtrInertia_KgmSq_f32                    |
| t_InrtCmp_ScaleFactorTblY_Uls_u9p7\[\]            |
| t_InrtCmp_TBarVel_ScaleFactorTblY_Uls_u9p7\[\]    |
| k_InrtCmp_MtrVel_ScaleFactor_Uls_f32              |
| t_InrtCmp_VehSpdTblX_Kph_u15p1\[\]                |
| t_FDD_ADDStaticTblY_MtrNmpRadpS_um1p17\[\]        |
| t2_FDD_ADDRollingTblYM_MtrNmpRadpS_um1p17\[\]\[\] |
| t_FDD_BlendTblY_Uls_u8p8\[\]                      |
| t_FDD_FreqTblYM_Hz_u12p4\[\]                      |
| t_FDD_AttenTblX_MtrRadpS_u12p4\[\]                |
| t_FDD_AttenTblY_Uls_u8p8\[\]                      |
| t_WIRBlndTblX_MtrNm_u8p8\[\]                      |
| t_RIAstWIRBlndTblY_Uls_u2p14\[\]                  |
| t_DmpFiltKpWIRBlndY_Uls_u2p14\[\]                 |
| k_CmnTbarStiff_NmpDeg_f32                         |
| t_DmpADDCoefX_MtrNm_u4p12\[10\]                   |
| k_DmpGainOnThresh_KphpS_f32                       |
| k_DmpGainOffThresh_KphpS_f32                      |
| k_DmpDecelGain_Uls_f32                            |
| k_DmpDecelGainFSlew_UlspS_f32                     |
| t_DmpDecelGainSlewX_MtrRadpS_f32\[\]              |
| t_DmpDecelGainSlewY_UlspS_f32\[\]                 |
| k_CmnSysKinRatio_MtrDegpHwDeg_f32                 |

## Program (fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

|                                       |            |            |                 |
|-------------------------------|--------------|--------------|--------------|
| Constant Name                         | Resolution | Units      | Value           |
| D_ONEOVR2MS_SEC_U9P7                  | 2\^-7      | Sec        | 500.0           |
| D_2MS_SEC_U0P16                       | 2\^-16     | Sec        | 0.002           |
| D_2MS_SEC_U2P14                       | 2\^-14     | Sec        | 0.002           |
| D_PIOVR180_ULS_S4P11                  | 2\^-11     | Unitless   | 0.0174532925199 |
| D_ONE_ULS_U2P14                       | 2\^-14     | Unitless   | 1.0             |
| D_ONE_ULS_U8P8                        | 2\^-8      | Unitless   | 1.0             |
| D_ONE_ULS_U5P11                       | 2\^-11     | Unitless   | 1.0             |
| D_TWO_ULS_S2P13                       | 2\^-13     | Unitless   | 2.0             |
| D_2PI_ULS_U2P13                       | 2\^-13     | Unitless   | 6.2831853071796 |
| D_TBARVELFILTVAL_HWDEGPSEC_S15P16     | 2\^-16     | HwDegpSec  | 1024.0          |
| D_TBARVELFILTVAL_HWDEGPSEC_S15P16     | 2\^-16     | HwDegpSec  | 2047.9375       |
| D_TERMA_MTRRADPSEC_S20P11             | 2\^-11     | MtrRadpS   | 4095.875        |
| D_EIGHT_ULS_U10P6                     | 2\^-6      | Unitless   | 8.0             |
| D_SCALEDDRIVERVEL_MTRRADPS_S17P14     | 2\^-14     | MtrRadpS   | 10000.0         |
| D_COMPENSATIONLIMIT_MTRNM_S11P20      | 2\^-20     | MtrNm      | 8.8             |
| D_INERTIACOMPCALCLIMIT_MTRNM_U15P1    | 2\^-1      | MtrNm      | 8.8             |
| D_FOUR_ULS_S3P12                      | 2\^-12     | Unitless   | 4.0             |
| D_ADDCOEFCALCHILIMIT_MTRNMSPRAD_U1P15 | 2\^-15     | MtrNmSpRad | 0.05            |
| D_ADDCOEFCALCHILIMIT_MTRNMSPRAD_U3P13 | 2\^-13     | MtrNmSpRad | 0.05            |
| D_ABSSCALEDRIVERVELHI_MTRRADPS_U15P1  | 2\^-1      | MtrNmSpRad | 4095\. 5        |
| VEHICLELONACCEL_MIN_F32               | Float32    | KphpS      | -64.0           |
| VEHICLELONACCEL_MAX_F32               | Float32    | KphpS      | 63.99804        |
| D_ONE_ULS_U11P21                      | Uint32     | Unitless   | 1               |

####  [section]

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

|                            |
|----------------------------|
| Constant Name              |
| D_2MS_SEC_F32              |
| D_PIOVR180_ULS_F32         |
| D_ZERO_ULS_F32             |
| D_FALSE_CNT_LGC            |
| D_2PI_ULS_F32              |
| D_MTRTRQCMDHILMT_MTRNM_F32 |
| D_ONE_ULS_F32              |

### Module specific Lookup Tables Constants

|               |            |       |                  |
|---------------|------------|-------|------------------|
| Constant Name | Resolution | Value | Software Segment |
| None          |            |       |                  |

# Functions/Macros Used By the Sub-Modules

## Library Functions / Macros 

The library and functions / Macros that are called by the various sub
modules are identified below,

1.  LPF_KUpdate_f32_m

2.  LPF_OpUpdate_f32_m

3.  HPF_KUpdate_f32_m

4.  HPF_OpUpdate_f32_m

5.  FPM_FloatToFixed_m

6.  FPM_FixedToFloat_m

7.  IntplVarXY_u16_u16Xu16Y_Cnt

8.  BilinearXYM_s16_s16Xs16YM_Cnt

9.  TableSize_m

10. Limit_m

11. Sign_f32_m

12. Rte_Call_NxtrDiagMgr_SetNTCStatus

13. FPM_Fix_m

14. Abs_s32_m

## Data Hiding Functions

1.  None

## Global Functions/Macros Defined by this Module

None

## Local Functions/Macros Used by this MDD only

### Local Function \#1

|                      |                                    |         |        |       |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | DriverVelCalc                      | Type    | Min    | Max   |
| **Arguments Passed** | HwTorque_HwNm_T_f32                | float32 | -10    | 10    |
|                      | CRFMotorVel_MtrRadpS_T_f32         | float32 | -1350  | 1350  |
|                      | VehicleSpeed_Kph_T_f32             | float32 | 0      | 511   |
| **Return Value**     | ScaledDriverVel_MtrRadpS_T\_ s14p1 | float32 | -10000 | 10000 |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DampingFirewall/doc/mediax/media/image2.wmf)

### Calculate ADD Coefficient

|                      |                                  |         |       |      |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | ADDCoefCalc                      | Type    | Min   | Max  |
| **Arguments Passed** | BaseAssistCmd_MtrNm_T_f32        | float32 | -8.8  | 8.8  |
|                      | WIRCmdAmpBlnd_MtrNm_T_f32        | float32 | 0     | 8.8  |
|                      | VehicleSpeed_Kph_T_f32           | float32 | 0     | 511  |
|                      | CRFMotorVel_MtrRadpS_T_f32       | Float32 | -1350 | 1350 |
|                      | VehicleLonAccel_KphpS_T_f32      | Float32 | -50   | 50   |
| **Return Value**     | ADDCoefCalc_MtrNmSpRad_T\_ u0p16 | uint16  | 0.0   | 0.05 |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DampingFirewall/doc/mediax/media/image3.wmf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DampingFirewall/doc/mediax/media/image4.wmf)

### Calculate Filter Coefficients

|                                     |                                     |                |               |               |
|----------|-----------------------|----------|---------------|----------------|
| **Function Name**                   | FilterCoefCalc                      | Type           | Min           | Max           |
| **Arguments Passed**                | ADDCoefCalc_MtrNmSpRad_T\_ u0p16    | uint16         | 0.0           | 0.05          |
| <span class="mark"></span>          | WIRCmdAmpBlnd_MtrNm_T_f32           | float32        | 0             | 8.8           |
|                                     | VehicleSpeed_Kph_T_f32              | float32        | 0             | 511           |
|                                     | filtCoef_Uls_T_Str                  | filterCoef_T\* | N/A (address) | N/A (address) |
| **Outputs Returned (by reference)** |                                     |                |               |               |
|                                     | filtCoef_Uls_T_Str-\>b0_Uls\_ s0p15 | sint16         | -0.975097656  | 0.0           |
|                                     | filtCoef_Uls_T_Str-\>b1_Uls\_ u0p16 | uint16         | 0.0           | 0.400024414   |
|                                     | filtCoef_Uls_T_Str-\>b2_Uls\_ s0p15 | sint16         | -0.322692871  | 0.575073242   |
|                                     | filtCoef_Uls_T_Str-\>a0_Uls\_ u2p14 | uint16         | 0.539428711   | 3.949829102   |
|                                     | filtCoef_Uls_T_Str-\>a1_Uls_s4p11   | sint16         | -8            | -4.797363281  |
|                                     | filtCoef_Uls_T_Str-\>a2_Uls_u5p11   | uint16         | 4.050292969   | 10.66308594   |
| **Return Value**                    | none                                |                |               |               |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DampingFirewall/doc/mediax/media/image5.wmf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DampingFirewall/doc/mediax/media/image6.wmf)

### Generate Command

|                      |                                    |                |        |              |              |
|--------------|-----------------|-------------|---------|-----------|-----------|
| **Function Name**    | GenFddIcCmd                        |                | Type   | Min          | Max          |
| **Arguments Passed** | ScaledDriverVel_MtrRadpS_T\_ s14p1 |                | sint16 | -10000       | 10000        |
|                      | \*FilterCoefStr                    | b0_Uls\_ s0p15 | sint16 | -0.975097656 | 0.0          |
|                      |                                    | b1_Uls\_ u0p16 | uint16 | 0.0          | 0.400024414  |
|                      |                                    | b2_Uls\_ s0p15 | sint16 | -0.322692871 | 0.575073242  |
|                      |                                    | a0_Uls\_ u2p14 | uint16 | 0.539428711  | 3.949829102  |
|                      |                                    | a1_Uls_s4p11   | sint16 | -8           | -4.797363281 |
|                      |                                    | a2_Uls_u5p11   | uint16 | 4.050292969  | 10.66308594  |
| **Return Value**     | Compenstation_MtrNm_T\_ s11p20     |                | Sint32 | -8.8         | 8.8          |

#### Unit Testing Considerations

This function is designed to work with argument values from the calling
function as used with the other functions in the module, and outputs may
be out of the expected range if tested with arbitrary combinations of
input values. Unit testing of this function should use only passed
argument value combinations coming from the calling function.

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DampingFirewall/doc/mediax/media/image7.wmf)

# Software Module Implementation

## Runtime Environment (RTE) Initial Values

This section lists the initial values of data written by this module but
controlled by the RTE. After RTE initialization, the data in this table
will contain these values.

|                                                 |       |
|-------------------------------------------------|-------|
| Data                                            | Value |
| Rte_InitValue_AsstFirewallActive_Uls_f32        | 0     |
| Rte_InitValue_CombinedDamping_MtrNm_f32         | 0     |
| Rte_InitValue_DampingCmd_MtrNm_f32              | 0     |
| Rte_InitValue_HwTorque_HwNm_f32                 | 0     |
| Rte_InitValue_InertiaComp_MtrNm_f32             | 0     |
| Rte_InitValue_MtrVelCRF_MtrRadpS_f32            | 0     |
| Rte_InitValue_VehicleSpeed_Kph_f32              | 0     |
| Rte_InitValue\_ BaseAssistCmd_MtrNm_f32         | 0     |
| Rte_InitValue \_WIRCmdAmpBlnd_MtrNm_f32         | 0     |
| Rte_InitValue \_ VehicleLonAccel_KphpS_f32      | 0     |
| Rte_InitValue \_ FreqDepDmpSrlComSvcDft_Cnt_lgc | FALSE |

## Initialization Functions

### Init: DampingFirewall_Init1

#### Design Rationale

None

#### Module Outputs

None

#### Module Internal 

None

#### Initialize Filters

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DampingFirewall/doc/mediax/media/image8.wmf)

## Periodic Functions

### Per: DampingFirewall_Per1

#### Design Rationale

None

#### Program Flow Start

#### Rte_Call_ActivePull_Per1_CP0_CheckpointReached() [rte_call_activepull_per1_cp0_checkpointreached]

#### Store Module Inputs to Local copies

DefeatDampingSvc_Cnt_T_lgc =
Rte_IRead_DampingFirewall_Per1_Defeat_Damping_Svc_Cnt_lgc()

MECCounter_Cnt_T_enum =
Rte_IRead_DampingFirewall_Per1_MEC_Counter_Cnt_enum()

AsstFirewallActive_Uls_T_f32 =
Rte_IRead_DampingFirewall_Per1_AsstFirewallActive_Uls_f32()

DampingCmd_MtrNm_T_f32 =
Rte_IRead_DampingFirewall_Per1_DampingCmd_MtrNm_f32()

HwTorque_HwNm_T_f32 = Rte_IRead_DampingFirewall_Per1_HwTorque_HwNm_f32()

InertiaComp_MtrNm_T_f32 =
Rte_IRead_DampingFirewall_Per1_InertiaComp_MtrNm_f32()

MtrVelCRF_MtrRadpS_T_f32 =
Rte_IRead_DampingFirewall_Per1_MtrVelCRF_MtrRadpS_f32()

VehicleSpeed_Kph_T_f32 =
Rte_IRead_DampingFirewall_Per1_VehicleSpeed_Kph_f32()

BaseAsstCmd_MtrNm_T_f32 =
Rte_IRead_DampingFirewall_Per1_BaseAssistCmd_MtrNm_f32()

WIRCmdAmpBlnd_MtrNm_T_f32 =
Rte_IRead_DampingFirewall_Per1_WIRCmdAmpBlnd_MtrNm_f32()

FDDDefSrvFlg_Cnt_T_lgc =
Rte_IRead_DampingFirewall_Per1_FreqDepDmpSrlComSvcDft_Cnt_lgc()

VehicleLonAccel_KphpS_T_f32 =
Rte_IRead_DampingFirewall_Per1_VehicleLonAccel_KphpS_f32()

VehicleSpeed_Kph_T_u9p7 = FPM_FloatToFixed_m(VehicleSpeed_Kph_T_f32,
u9p7_T)

MtrVelCRF_MtrRadpS_T_s11p4 =
FPM_FloatToFixed_m(MtrVelCRF_MtrRadpS_T_f32, s11p4_T)

AbsMtrVelCRF_MtrRadpS_T_u11p5 =
FPM_FloatToFixed_m(Abs_f32_m(MtrVelCRF_MtrRadpS_T_f32), u11p5_T)

DampFWPstepNstep_Cnt_T_str.PStep = k_DampFWPstep_Cnt_u16

DampFWPstepNstep_Cnt_T_str.NStep = k_DampFWNstep_Cnt_u16

DampFWPstepNstep_Cnt_T_str.Threshold = t_DampFWPNstepThresh_Cnt_u16\[1\]

DampFWInrtCmpPstepNstep_Cnt_T_str.PStep = k_DampFWInCmpPStep_Cnt_u16

DampFWInrtCmpPstepNstep_Cnt_T_str.NStep = k_DampFWInCmpNStep_Cnt_u16

DampFWInrtCmpPstepNstep_Cnt_T_str.Threshold =
t_DampFWDampInrtCmpPNThesh_Cnt_u16\[1\]

#### Damping Limiter – Interpolate and Filter Boundaries

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DampingFirewall/doc/mediax/media/image9.wmf)

#### PNCounter

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DampingFirewall/doc/mediax/media/image10.wmf)

#### Additional Damping

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DampingFirewall/doc/mediax/media/image11.wmf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DampingFirewall/doc/mediax/media/image12.wmf)

#### ![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DampingFirewall/doc/mediax/media/image13.wmf)Store Local copy of outputs into Module Outputs

DampFWUprBound_MtrNm_D_f32 = UprBoundRaw_MtrNm_T_f32

DampFWUprBoundFilt_MtrNm_D_f32 = UprBoundFilt_MtrNm_T_f32

DampFWLwrBound_MtrNm_D_f32 = LwrBoundRaw_MtrNm_T_f32

DampFWLwrBoundFilt_MtrNm_D_f32 = LwrBoundFilt_MtrNm_T_f32

DampFWAddedDamp_MtrNm_D_f32 = AddedDamp_MtrNm_T_f32

DampFWAddedDampAFW_MtrNm_D_f32 = AFWAddDamping_MtrNm_T_f32

DampFWAddedDampDFW_MtrNm_D_f32 = DFWAddDamping_MtrNm_T_f32

Rte_IWrite_DampingFirewall_Per1_CombinedDamping_MtrNm_f32(CombinedDamping_MtrNm_T_f32)

#### Program Flow End

Rte_Call_ActivePull_Per1_CP1_CheckpointReached()

## Fault Recovery Functions

None

## Shutdown Functions

None

## Interrupt Functions

None

## Serial Communication Functions

None

## 

# Execution Requirements

## Execution Sequence of the Module

DampingFirewall_Per1 is called at a rate of 2 ms.

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

|                       |                   |                                                 |
|--------------------------|-----------------|------------------------------|
| Function Name         | Calling Frequency | System State(s) in which the function is called |
| DampingFirewall_Init1 | On Event          | On Init                                         |
| DampingFirewall_Per1  | 2 ms              | ALL                                             |

## Execution Requirements for Serial Communication Functions 

|               |                                                  |
|---------------|--------------------------------------------------|
| Function Name | Sub-Module called by (Serial Comm Function Name) |
|               |                                                  |

#   [section-2]

# Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

|                       |                                            |
|-----------------------|--------------------------------------------|
| Name of Sub Module    | Software Segment                           |
| DampingFirewall_Init1 | RTE_START_SEC_AP_DAMPINGFIREWALL_APPL_CODE |
| DampingFirewall_Per1  | RTE_START_SEC_AP_DAMPINGFIREWALL_APPL_CODE |

##  [section-3]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

|                    |                         |
|--------------------|-------------------------|
| Name of Sub Module | Software Segment        |
| DriverVelCalc      | AP_DAMPINGFIREWALL_CODE |
| ADDCoefCalc        | AP_DAMPINGFIREWALL_CODE |
| FilterCoefCalc     | AP_DAMPINGFIREWALL_CODE |
| GenFddIcCmd        | AP_DAMPINGFIREWALL_CODE |

#   [section-4]

# Known Issues / Limitations With Design

1.  INLINE functions defined in GlobalMacro.h are not unit tested.

2.  Due to the requirement to use fixed point arithmetic in the “diverse
    implementation” of SF-14 (VBIC), precision of some calculations,
    especially of the filter coefficients and especially at the extremes
    of the input ranges, is significantly less than the resolution of
    the data types of the variables. For example, the a0 coefficient is
    stored in a variable with 2\^-14 resolution, but the a0 min value is
    accurate to approximately 2\^-6 as compared to the expected results
    of the same calculation using Excel. This is an inherent limitation
    of using fixed point arithmetic on the widely differing magnitudes
    of the inputs to the calculations and the resulting rescaling that
    reduces the precision of the result; the scaling currently in use
    was determined through informal testing during initial development.
    The ranges given for the filter coefficients for unit test purposes
    are the actual expected ranges given the fixed point calculations
    being used, and some are wider than the expected ranges that would
    be calculated using another method such as an Excel spreadsheet. Per
    conversations with Michael Hales, this function is working and no
    changes should be made at this time.

# Revision Control Log

|            |                                                                                                                                                                                   |            |                     |
|---------|---------------------------------------------|---------|----------|
| **Rev \#** | **Change Description**                                                                                                                                                            | **Date**   | **Author Initials** |
| 1.0        | Initial Version                                                                                                                                                                   | 27-Apr-12  | OT                  |
| 2.0        | Fixed UTP Issues (naming consistency)                                                                                                                                             | 08-May-12  | OT                  |
| 3.0        | Fixed calibration naming conflict                                                                                                                                                 | 10-May-12  | OT                  |
| 4.0        | Anomaly 3324 (using wrong value for boundary calc), fixed units in names                                                                                                          | 18-May-12  | OT                  |
| 5.0        | Updated to SF-35 v002 (anomaly 3325)                                                                                                                                              | 22-May-12  | OT                  |
| 6.0        | Updated to SF-35 v003                                                                                                                                                             | 29-May-12  | JW                  |
| 7.0        | Updated to SF-35 v004                                                                                                                                                             | 31-May-12  | OT                  |
| 8.0        | Updated to SF-35 V005                                                                                                                                                             | 7-Aug-12   | NRAR                |
| 9.0        | Updated to SF-35 V006. Removed input limit on inertia comp input for VBIC limiter. Added multiple display variables. Variable name changes for state variables for filter.        | 28-Aug-12  | KJS                 |
| 10.0       | Added watchdog checkpoints                                                                                                                                                        | 16-Sept-12 | BWLs                |
| 11.0       | Corrected software segments of internal variables                                                                                                                                 | 19-Sep-12  | SSK                 |
| 12.0       | MDD updates based on UTP catch up                                                                                                                                                 | 23-oct-12  | NRAR                |
| 13.0       | Anom 3957- VBICFaultmode is not set                                                                                                                                               | 25-Oct-12  | NRAR                |
| 14.0       | Updates as per the implementation of v007 of the FDD                                                                                                                              | 10-Feb-13  | VK                  |
| 13.1.1     | Updates for anomaly 4407                                                                                                                                                          | 12-Apr-13  | SP                  |
| 13.1.2     | Updates for anomaly 4809                                                                                                                                                          | 16-Apr-13  | LN                  |
| 14.0       | Anomaly 4913 fixes                                                                                                                                                                | 30-Apr-13  | SP                  |
| 14.1.1     | VBIC Error filter robustness change                                                                                                                                               | 07-Jun-13  | JJW                 |
| 15.0       | Updated to SF-35 Ver 008, Generate Cmd calculations changed to fixed point                                                                                                        | 15-May-13  | SP                  |
| 16.0       | Updated to SF-35 Ver 009, undone Generate Cmd fixed point changes and merged 14.1.1 changes                                                                                       | 18-Jun-13  | SP                  |
| 17.0       | Updated to SF-35 Ver 010 – add filtering on LwrBound and UprBound                                                                                                                 | 03-Oct-13  | KMC                 |
| 18.0       | A5206 anomaly fix                                                                                                                                                                 | 18-Nov-13  | SP                  |
| 19.0       | Corrections for issues found in UTP                                                                                                                                               | 17-Dec-13  | KMC                 |
| 20.0       | Additional corrections for issues found in unit test                                                                                                                              | 4-Feb-14   | KMC                 |
| 21.0       | Changed ranges of filter coefficients to account for fixed point math and worst case inputs, and added design limitation regarding resolution of filter coefficient calculations. | 24-Feb-14  | KMC                 |
| 22.0       | A6259 anomaly fix                                                                                                                                                                 | 29-Aug-14  | SB                  |

{% endraw %}