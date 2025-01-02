---
layout: default
title: CurrCmd_MDD
nav_order: 1
parent: Motor Control
---
{% raw %}
# Module -- CurrCmd [module----currcmd]

# High-Level Description [high-level-description]

This Module generates the current command and the voltage reference for
the current control.

## Diagram – Function Data Sharing

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrCtrl_CM/doc/mediax/media/image1.png"
style="width:2.57292in;height:3.43681in" />

### Diagram – Function (Name)

# Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

|                                  |                |                                |
|-----------------------------------|--|------------------------------------|
| Module Inputs                    | Module Outputs |                                |
| MRFTrqCmdScl_MtrNm_f32           |                | DaxIntegralGain_Uls_f32        |
| MRFMtrVel_MtrRadpS_f32           |                | DaxPropotionalGain_Uls_f32     |
| EstKe_VpRadpS_f32                |                | QaxIntegralGain_Uls_f32        |
| EstR_Ohm_f32                     |                | QaxPropotionalGain_Uls_f32     |
| EstLd_Henry_f32                  |                | MtrCurrDaxRef_Amp_f32          |
| EstLq_Henry_f32                  |                | MtrCurrQaxRef_Amp_f32          |
| VehSpd_Kph_f32                   |                | MtrVoltDaxFF_Volt_f32          |
| MtrQuad_Cnt_u08                  |                | MtrVoltQaxFF_Volt_f32          |
| FastDataAccessBufIndex_Cnt_M_u16 |                | MtrCurrAngle_Rev_f32           |
| CurrentGainSvc_Cnt_lgc           |                | MtrTrqCmdSign_Cnt_s16          |
|                                  |                | MtrPosComputationDelay_Rad_f32 |

##  [section]

##  [section-1]

## Module Internal Variables

This section identifies the name, range and resolutions for module
specific data created by this module. If there are no range restrictions
on the variable, the term “FULL” is placed into the table for legal
range.

<table>
<colgroup>
<col style="width: 34%" />
<col style="width: 14%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 19%" />
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
<td>MtrVelFiltFFSV_MtrRadpS_M_s11p20</td>
<td>0.00000095367431640625</td>
<td>-1118</td>
<td>1118</td>
<td>CURRCMD_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>MtrVelFiltPISV_MtrRadpS_M_s11p20</td>
<td>0.00000095367431640625</td>
<td>-1118</td>
<td>1118</td>
<td>CURRCMD_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>MtrVelFilt_RadpSec_D_f32</td>
<td>Single Precision Float</td>
<td>-1118</td>
<td>1118</td>
<td>CURRCMD_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>MtrMaxCurrDaxRef_Amps_D_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td>200</td>
<td>CURRCMD_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>MtrCurrQaxRef_Amp_D_f32</td>
<td>Single Precision Float</td>
<td>-220</td>
<td>220</td>
<td>CURRCMD_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>MtrCurrDaxRef_Amp_D_f32</td>
<td>Single Precision Float</td>
<td>-220</td>
<td>220</td>
<td>CURRCMD_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>PeakTorque_MtrNm_D_f32</td>
<td>Single Precision Float</td>
<td>-8.8</td>
<td>8.8</td>
<td>CURRCMD_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>MRFMtrVelFiltPI_MtrRadpS_D_f32</td>
<td>Single Precision Float</td>
<td>-1118</td>
<td>1118</td>
<td>CURRCMD_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>ElecPosDelayComp_Rad_D_f32</td>
<td>Single Precision Float</td>
<td>-2*pi</td>
<td>2*pi</td>
<td>CURRCMD_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>KpqGain_Uls_D_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td>100</td>
<td>CURRCMD_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>KiqGain_Uls_D_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td>100</td>
<td>CURRCMD_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>KpdGain_Uls_D_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td>100</td>
<td>CURRCMD_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>KidGain_Uls_D_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td>100</td>
<td>CURRCMD_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>IdMin_Amp_D_f32</td>
<td>Single Precision Float</td>
<td>-220</td>
<td>220</td>
<td>CURRCMD_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>IqMin_Amp_D_f32</td>
<td>Single Precision Float</td>
<td>-220</td>
<td>220</td>
<td>CURRCMD_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>IqMax_Amp_D_f32</td>
<td>Single Precision Float</td>
<td>-220</td>
<td>220</td>
<td>CURRCMD_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>IdMax_Amp_D_f32</td>
<td>Single Precision Float</td>
<td>-220</td>
<td>220</td>
<td>CURRCMD_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>ImSqMin_AmpSq_D_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td>\96800</td>
<td>CURRCMD_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>LimitedMRFMtrTrqCmd_MtrNm_D_f32</td>
<td>Single Precision Float</td>
<td>-8.8</td>
<td>8.8</td>
<td>CURRCMD_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>PhsAdvPeak_Rad_D_f32</td>
<td>Single Precision Float</td>
<td>-2*pi</td>
<td>2*pi</td>
<td>CURRCMD_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>CosDelta_Cnt_M_f32</td>
<td>Single Precision Float</td>
<td>-1</td>
<td>1</td>
<td>CURRCMD_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>SinDelta_Cnt_M_f32</td>
<td>Single Precision Float</td>
<td>-1</td>
<td>1</td>
<td>CURRCMD_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>EstKe_VpRadpS_M_f32</td>
<td>Single Precision Float</td>
<td>0.025</td>
<td>0.075</td>
<td>CURRCMD_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>TermXq_Uls_M_f32</td>
<td>Single Precision Float</td>
<td>-90</td>
<td>90</td>
<td>CURRCMD_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>TermXd_Uls_M_f32</td>
<td>Single Precision Float</td>
<td>-60</td>
<td>60</td>
<td>CURRCMD_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>TermEgR_Amp_M_f32</td>
<td>Single Precision Float</td>
<td>-4050</td>
<td>4050</td>
<td>CURRCMD_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>TermVR2_AmpSq_M_f32</td>
<td>Single Precision Float</td>
<td>14400</td>
<td>810000</td>
<td>CURRCMD_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>TermEgRZ_Amp_M_f32</td>
<td>Single Precision Float</td>
<td>-5</td>
<td>5</td>
<td>CURRCMD_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>TermVRZ_Amp_M_f32</td>
<td>Single Precision Float</td>
<td>0.02</td>
<td>900</td>
<td>CURRCMD_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>TermVR_Amp_M_f32</td>
<td>Single Precision Float</td>
<td>120</td>
<td>900</td>
<td>CURRCMD_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>Reluctance_Henry_M_f32</td>
<td>Single Precision Float</td>
<td><strong>0.0002</strong></td>
<td><strong>0.0005</strong></td>
<td>CURRCMD_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>LocateMinImNIter_Cnt_D_u16</td>
<td>1</td>
<td>0</td>
<td>5</td>
<td>CURRCMD_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td>LocateTrqExNIter_Cnt_D_u16</td>
<td>1</td>
<td>0</td>
<td>5</td>
<td>CURRCMD_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="odd">
<td>CurrCmd_IdBoostAmount_Amp_D_f32</td>
<td>Single Precision Float</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>CURRCMD_START_SEC_VAR_CLEARED_32</td>
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

## Program(fixed) Constants

|                                         |
|-----------------------------------------|
| Constant Name                           |
| k_a0IdSlope_Uls_f32                     |
| k_a1IdSlope_Uls_f32                     |
| k_a2IdSlope_Uls_f32                     |
| k_MtrVelFiltFFKn_Cnt_u16                |
| k_MtrVelFiltPIKn_Cnt_u16                |
| k_MtrMaxCurr_AmpsSq_f32                 |
| k_IdrefMtrVelOffset_RadpSec_f32         |
| k_K2Slope_RadpSecpNm_f32                |
| k_K3VelIntercep_RadpSec_f32             |
| k_NoofPoles_Uls_f32                     |
| k_PIGainVspdCutoff_kph_f32              |
| t_KpqGainX_MtrRadpSec_u12p4\[8\]        |
| t_KpqGainY_Uls_u6p10\[8\]               |
| t_KiqGainX_MtrRadpSec_u12p4\[8\]        |
| t_KpdGainX_MtrRadpSec_u12p4\[8\]        |
| t_KpdGainY_Uls_u6p10\[8\]               |
| t_KidGainX_MtrRadpSec_u12p4\[8\]        |
| t_KidGainY_Uls_u10p6\[8\]               |
| t_RefDeltaPoints_Rad_f32\[8\]           |
| t_Q13VltgSchedXTbl_MtrRadpS_u12p4\[10\] |
| t_Q13VltgSchedYTbl_Volt_u5p11\[10\]     |
| t_Q24VltgSchedXTbl_MtrRadpS_u12p4\[10\] |
| t_Q24VltgSchedYTbl_Volt_u5p11\[10\]     |
| k_IdqRefTrqTol_Rad_f32                  |
| k_IdqRefTrqNIter_Cnt_u16                |
| k_IdqRefIminTol_Amp_f32                 |
| k_IdqRefLocateRefNIter_Cnt_u16          |
| k_deadtimeVScale_Uls_f32                |
| k_IdBoostGain_Uls_f32                   |
| k_IdBoostVRThreshScl_Uls_f32            |
| t_IdBoostTrqCmdX_MtrNm_u4p12            |
| t_IdBoostTrqCharSclY_Uls_u1p15          |

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

|                              |                        |       |                                       |
|-------------------------------|--------------|-----------|-----------------|
| Constant Name                | Resolution             | Units | Value                                 |
| D_SQRT3OVR2_ULS_F32          | Single Precision Float | Uls   | 0.866025403784                        |
| D_MTRPOLESDIV2_CNT_F32       | Single Precision Float | Cnt   | 3.0                                   |
| D_2OVRSQRT3_ULS_F32          | Single Precision Float | Uls   | 1.15470053837925                      |
| D_NEG2OVRSQRT3_ULS_F32       | Single Precision Float | Uls   | -1.15470053837925F                    |
| D_ROUND_ULS_F32              | Single Precision Float | Uls   | 0.5                                   |
| D_NEGROUND_ULS_F32           | Single Precision Float | Uls   | -0.5                                  |
| D_NEG_ULS_F32                | Single Precision Float | Uls   | \- 1                                  |
| D_MAXCURRENT_AMP_F32         | Single Precision Float | Amp   | 220                                   |
| D_SIZERDLTAPOINTS_CNT_U16    | 1                      | Cnt   | TableSize_m(t_RefDeltaPoints_Rad_f32) |
| D_MAXDELTAPOINTSSIZE_CNT_U16 | 1                      | Cnt   | D_SIZERDLTAPOINTS_CNT_U16 – 1U)       |
| D_PIPLUSPIOVER4_ULS_F32      | Single Precision Float | ULS   | D_PI_ULS_F32+( D_2PI_ULS_F32/4)       |
| D_VECUMAX_VOLTS_F32          | Single Precision Float | Volts | 31.0F                                 |

####  [section-2]

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

|                     |
|---------------------|
| Constant Name       |
| D_ZERO_ULS_F32      |
| D_180OVRPI_ULS_F32  |
| D_ONE_ULS_F32       |
| D_QUADRANT3_CNT_U8  |
| D_QUADRANT1_CNT_U8  |
| D_2PI_ULS_F32       |
| D_ZERO_CNT_U16      |
| D_VECUMIN_VOLTS_F32 |

### Module specific Lookup Tables Constants

(This is for lookup tables (arrays) with fixed values, same name as
other tables)

|               |            |       |                  |
|---------------|------------|-------|------------------|
| Constant Name | Resolution | Value | Software Segment |
| None          |            |       |                  |

# Functions/Macros used by the Sub-Modules 

## Library Functions / Macros 

The library and functions / Macros that are called by the various sub
modules are identified below,

1.  FPM_FloatToFixed_m

2.  LPF_SvUpdate_s16InFixKTrunc_m

3.  LPF_OpUpdate_s16InFixKTrunc_m

4.  FPM_FixedToFloat_m

5.  Sqrtf

6.  Abs_f32_m

7.  atan2f

8.  IntplVarXY_u16_u16Xu16Y_Cnt

9.  Sinf

10. Cosf

11. 

## Data Hiding Functions

1.  
2.  

## Global Functions/Macros Defined by this Module

None

## Local Functions/Macros Used by this MDD only

### Local Function \#1

|                      |                             |         |     |     |          |
|----------------|-----------------------------|---------|-------|-------|------|
| **Function Name**    | ParabolicInterpolation      | Type    | Min | Max | UTP Tol. |
| **Arguments Passed** | IntpolPoints_Uls_T_f32\[6\] | Float32 | \-  | \-  |          |
| **Return Value**     | ParaIntpol_Uls_T_f32        | Float32 | N/A | N/A |          |

#### Description

### ![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrCtrl_CM/doc/mediax/media/image2.wmf) [section-3]

### Local Function \#2

|                      |                     |         |      |       |          |
|----------------------|---------------------|---------|------|-------|----------|
| **Function Name**    | CalculateImVSIdq    | Type    | Min  | Max   | UTP Tol. |
| **Arguments Passed** | IdRef_Amp_T_f32     | Float32 | -220 | +220- |          |
|                      | IqRef_Amp_T_f32     | Float32 | -220 | +220- |          |
| **Return Value**     | ImVSIdq_AmpSq_T_f32 | Float32 | 0    | 96800 |          |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrCtrl_CM/doc/mediax/media/image3.wmf)

### Local Function \#3

|                      |                       |         |      |     |          |
|----------------------|-----------------------|---------|------|-----|----------|
| **Function Name**    | CalculateIq           | Type    | Min  | Max | UTP Tol. |
| **Arguments Passed** | Torquecmd_MtrNm_T_f32 | Float32 | -8.8 | 8.8 |          |
|                      | IdRef_Amp_T_f32       | Float32 | -220 | 220 |          |
|                      |                       |         |      |     |          |
| **Return Value**     | IqRefTmp_Amp_T_f32    | Float32 | -220 | 220 |          |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrCtrl_CM/doc/mediax/media/image4.wmf)

### Local Function \#4

|                      |                    |         |       |      |          |
|----------------------|--------------------|---------|-------|------|----------|
| **Function Name**    | CurrtoVoltTest     | Type    | Min   | Max  | UTP Tol. |
| **Arguments Passed** | IqRef_Amp_T_f32    | Float32 | -220  | 220  |          |
|                      | IdRef_Amp_T_f32    | Float32 | -220  | 220  |          |
|                      | \*VqR_Amp_T_f32    | Float32 | -220  | 220  |          |
|                      | \*VdR_Amp_T_f32    | Float32 | -220  | 220  |          |
| **Return Value**     | VoltTest_Uls_T_lgc | Boolean | False | True |          |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrCtrl_CM/doc/mediax/media/image5.wmf)

### Local Function \#5

|                      |                        |         |      |     |          |
|----------------------|------------------------|---------|------|-----|----------|
| **Function Name**    | CalcTorque             | Type    | Min  | Max | UTP Tol. |
| **Arguments Passed** | CosDelta_Cnt_T_f32     | Float32 | 0    | 1   |          |
|                      | SinDelta_Cnt_T_f32     | Float32 | 0    | 1   |          |
|                      | \*IdMax_Amp_T_f32      | Float32 | -220 | 220 |          |
| **Return Value**     | TorqueCalc_MtrNm_T_f32 | Float32 | -8.8 | 8.8 |          |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrCtrl_CM/doc/mediax/media/image6.wmf)

### Local Function \#6

|                      |                         |         |        |        |          |
|----------------|-----------------------------|---------|-------|-------|------|
| **Function Name**    | LocateTrqExtremese      | Type    | Min    | Max    | UTP Tol. |
| **Arguments Passed** | MtrTrqCmd_MtrNm_T_f32   | Float32 | -8.8   | 8.8    |          |
|                      | \*IdMax_Amp_T_f32       | Float32 | -220   | 220    |          |
|                      | \*PhsAdvPeak_Rad_T_f32  | Float32 | -2\*pi | +2\*pi |          |
| **Return Value**     | TorqueState_MtrNm_T_f32 | Float32 | -8.8   | 8.8    |          |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrCtrl_CM/doc/mediax/media/image7.wmf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrCtrl_CM/doc/mediax/media/image8.wmf)

### Local Function \#7

|                      |                       |         |      |       |          |
|----------------------|-----------------------|---------|------|-------|----------|
| **Function Name**    | LocateMinimumIm       | Type    | Min  | Max   | UTP Tol. |
| **Arguments Passed** | MtrTrqCmd_MtrNm_T_f32 | Float32 | -8.8 | 8.8   |          |
|                      | \* IdMin_Amp_T_f32    | Float32 | -220 | 220   |          |
|                      | \* IqMin_Amp_T_f32    | Float32 | -220 | 220   |          |
| **Return Value**     | ImSqrMin_AmpSq_T_f32  | Float32 | 0    | 96800 |          |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrCtrl_CM/doc/mediax/media/image9.wmf)

# Software Module Implementation

## Runtime Environment (RTE) Initial Values

This section lists the initial values of data written by this module but
controlled by the RTE. After RTE initialization, the data in this table
will contain these values.

|                                              |       |
|----------------------------------------------|-------|
| Data                                         | Value |
| Rte_InitValue_DaxIntegralGain_Uls_f32        | 0     |
| Rte_InitValue_DaxPropotionalGain_Uls_f32     | 0     |
| Rte_InitValue_EstKe_VpRadpS_f32              | 0     |
| Rte_InitValue_EstLd_Henry_f32                | 0     |
| Rte_InitValue_EstLq_Henry_f32                | 0     |
| Rte_InitValue_EstR_Ohm_f32                   | 0     |
| Rte_InitValue_MRFMtrVel_MtrRadpS_f32         | 0     |
| Rte_InitValue_MRFTrqCmdScl_MtrNm_f32         | 0     |
| Rte_InitValue_MtrCurrAngle_Rev_f32           | 0     |
| Rte_InitValue_MtrCurrDaxRef_Amp_f32          | 0     |
| Rte_InitValue_MtrCurrQaxRef_Amp_f32          | 0     |
| Rte_InitValue_MtrPosComputationDelay_Deg_f32 | 0     |
| Rte_InitValue_MtrTrqCmdSign_Cnt_s16          | 0     |
| Rte_InitValue_MtrVoltDaxFF_Volt_f32          | 0     |
| Rte_InitValue_MtrVoltQaxFF_Volt_f32          | 0     |
| Rte_InitValue_QaxIntegralGain_Uls_f32        | 0     |
| Rte_InitValue_QaxPropotionalGain_Uls_f32     | 0     |
| Rte_InitValue_VehSpd_Kph_f32                 | 0     |
| FastDataAccessBufIndex                       | 0     |

## Initialization Functions

### CurrCmd_Init

#### Program Flow Start

Rte_Call_CurrCmd_Per1_CP0_CheckpointReached()

#### Processing

### ![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrCtrl_CM/doc/mediax/media/image10.wmf)  [section-4]

## Periodic Functions

### Per: CurrCmd_Per1

#### Design Rationale

None

#### Program Flow Start

Rte_Call_CurrCmd_Per1_CP0_CheckpointReached()

#### Store Module Inputs to Local copies

WriteAccessBufIndex_Cnt_T_u16= (FastDataAccessBufIndex_Cnt_M_u16&1)\^1;

MRFMtrTrqCmd_MtrNm_T_f32=Rte_Iread_CurrCmd_Per1_MRFTrqCmdScl_MtrNm_f32

MRFMtrVel_MtrRadpS_T_f32=Rte_Iread_CurrCmd_Per1_MRFMtrVel_MtrRadpS_f32

EstKe_VpRadpS_T_f32=Rte_Iread_CurrCmd_Per1_EstKe_VpRadpS_f32

EstR_Ohm_T_f32=Rte_Iread_CurrCmd_Per1_EstR_Ohm_f32

EstLd_Henry_T_f32=Rte_Iread_CurrCmd_Per1_EstLd_Henry_f32

EstLq_Henry_T_f32=Rte_Iread_CurrCmd_Per1_EstLq_Henry_f32

VehSpd_Kph_T_f32=Rte_Iread_CurrCmd_Per1_VehSpd_Kph_f32

MtrQuad_Cnt_T_u8 = Rte_Iread_CurrCmd_Per1_MtrQuad_Cnt_u08

CurrentGainSvc_Cnt_T_lgc =
Rte_IRead_CurrCmd_Per1_CurrentGainSvc_Cnt_lgc()

Vecu_Volt_T_f32 = Limit_m(Vecu_Volt_T_f32, D_VECUMIN_VOLTS_F32,
D_VECUMAX_VOLTS_F32)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrCtrl_CM/doc/mediax/media/image11.wmf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrCtrl_CM/doc/mediax/media/image12.wmf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrCtrl_CM/doc/mediax/media/image13.wmf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrCtrl_CM/doc/mediax/media/image14.wmf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrCtrl_CM/doc/mediax/media/image16.wmf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrCtrl_CM/doc/mediax/media/image17.wmf)

#### Store Local copy of outputs into Module Outputs

MtrDaxIntegralGain_Uls_M_f32\[WriteAccessBufIndex_Cnt_T_u16\] =
KidGain_Uls_T_f32

MtrDaxPropotionalGain_Uls_M_f32\[WriteAccessBufIndex_Cnt_T_u16\] =
KpdGain_Uls_T_f32

MtrQaxIntegralGain_Uls_M_f32\[WriteAccessBufIndex_Cnt_T_u16\] =
KiqGain_Uls_T_f32

MtrQaxPropotionalGain_Uls_M_f32\[WriteAccessBufIndex_Cnt_T_u16\] =
KpqGain_Uls_T_f32

MtrCurrQaxRef_Amp_M_f32\[WriteAccessBufIndex_Cnt_T_u16\] =
MtrCurrQaxRef_Amp_T_f32

MtrCurrDaxRef_Amp_M_f32\[WriteAccessBufIndex_Cnt_T_u16\] =
MtrCurrDaxRef_Amp_T_f32

Rte_Iwrite_CurrCmd_Per1_MtrCurrDaxRef_Amp_f32(MtrCurrDaxRef_Amp_T_f32)

Rte_Iwrite_CurrCmd_Per1_MtrCurrQaxRef_Amp_f32(MtrCurrQaxRef_Amp_T_f32)

MtrVoltDaxFF_Volt_M_f32\[WriteAccessBufIndex_Cnt_T_u16\]=MtrVoltDaxFF_Volt_T_f32

MtrVoltQaxFF_Volt_M_f32\[WriteAccessBufIndex_Cnt_T_u16\]=MtrVoltQaxFF_Volt_T_f32

Rte_Iwrite_CurrCmd_Per1_MtrVoltDaxFF_Volt_f32(MtrVoltDaxFF_Volt_T_f32)

Rte_Iwrite_CurrCmd_Per1_MtrVoltQaxFF_Volt_f32(MtrVoltQaxFF_Volt_T_f32)

Rte_Iwrite_CurrCmd_Per1_MtrCurrAngle_Rev_f32(MtrCurrElecAngle_Rev_T_f32)

Rte_Iwrite_CurrCmd_Per1_MtrTrqCmdSign_Cnt_s16(Sign_f32_m(MRFMtrTrqCmd_MtrNm_T_f32))

MtrPosComputationDelay_Rad_M_f32\[WriteAccessBufIndex_Cnt_T_u16\] =
ElecPosDelayComp_Rad_T_f32

#### Program Flow End

Rte_Call_CurrCmd_Per1_CP1_CheckpointReached()

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

(Describe in words relevant details about the execution sequence of the
different sub modules.)

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

|               |                   |                                                 |
|--------------------------|-----------------|------------------------------|
| Function Name | Calling Frequency | System State(s) in which the function is called |
| CurrCmd_Per1  | 2ms               | ALL                                             |
| CurrCmd_Init  | At init           | ALL                                             |
|               |                   |                                                 |

## Execution Requirements for Serial Communication Functions 

|               |                                                  |
|---------------|--------------------------------------------------|
| Function Name | Sub-Module called by (Serial Comm Function Name) |
| None          |                                                  |
|               |                                                  |

#   [section-6]

# Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

|                    |                                    |
|--------------------|------------------------------------|
| Name of Sub Module | Software Segment                   |
| CurrCmd_Per1       | RTE_START_SEC_AP_CURRCMD_APPL_CODE |
| CurrCmd_Init       | RTE_START_SEC_AP_CURRCMD_APPL_CODE |
|                    |                                    |

##  [section-7]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

|                        |                                    |
|------------------------|------------------------------------|
| Name of Sub Module     | Software Segment                   |
| ParabolicInterpolation | RTE_START_SEC_AP_CURRCMD_APPL_CODE |
| CalculateIq            | RTE_START_SEC_AP_CURRCMD_APPL_CODE |
| CalculateImVSIdq       | RTE_START_SEC_AP_CURRCMD_APPL_CODE |
| CurrtoVoltTest         | RTE_START_SEC_AP_CURRCMD_APPL_CODE |
| CalcTorque             | RTE_START_SEC_AP_CURRCMD_APPL_CODE |
| LocateTrqExtremes      | RTE_START_SEC_AP_CURRCMD_APPL_CODE |
| LocateMinimumIm        | RTE_START_SEC_AP_CURRCMD_APPL_CODE |

# Known Issues / Limitations With Design

1.  Global Macro’s are not unit tested.

# Revision Control Log

<table>
<colgroup>
<col style="width: 6%" />
<col style="width: 7%" />
<col style="width: 63%" />
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
<td>Initial version</td>
<td>15<sup>th</sup>-May-12</td>
<td>KPIT-RT</td>
</tr>
<tr class="odd">
<td>2</td>
<td>2.0</td>
<td>Partial implementation of SF-99B v004</td>
<td>20-Sep-12</td>
<td>OT</td>
</tr>
<tr class="even">
<td>3</td>
<td>3.0</td>
<td>Checkpoints and memmap statements added</td>
<td>20-Nov-12</td>
<td>Selva</td>
</tr>
<tr class="odd">
<td>4</td>
<td>4.0,5.0</td>
<td>Implementation of SF99 v8</td>
<td><p>23-Mar-13</p>
<p>19-Apr-13</p></td>
<td>Selva</td>
</tr>
<tr class="even">
<td>6</td>
<td>6.0</td>
<td>Corrected for A5883. Corrected LocateMinimumIm</td>
<td>21-Oct-13</td>
<td>Selva</td>
</tr>
<tr class="odd">
<td>7</td>
<td>7.0</td>
<td>Updated for v11 FDD99B</td>
<td>6-Nov-13</td>
<td>Selva</td>
</tr>
<tr class="even">
<td>8</td>
<td>8,0</td>
<td>Corrected for NewDelta calculation / Updated for v11 FDD99B UTP
fixes</td>
<td>8-Nov-13</td>
<td>Selva</td>
</tr>
<tr class="odd">
<td>9</td>
<td>9.0</td>
<td>Updated for V12 of FDD SF99</td>
<td>26-Nov-13</td>
<td>Selva</td>
</tr>
</tbody>
</table>

{% endraw %}