---
layout: default
title: Average_Friction_Learning_MDD
nav_order: 1
parent: Average Friction Learned
---
{% raw %}
# Module – Average Friction Learning [module-average-friction-learning]

# High-Level Description

This module estimates the gear friction changes from the baseline
friction and provides compensation. It is based on the column torque and
handwheel angle. It is primarily active at higher speeds.

# Figures

## Component Diagram

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/AvgFricLrn/doc/mediax/media/image1.jpeg"
style="width:1.9401in;height:3.05418in" alt="avgfric.jpg" />

#  Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

| Module Inputs              | Module Outputs |                     |
|----------------------------|----------------|---------------------|
| HwAng_HwDeg_f32            |                | EstFric_HwNm_f32    |
| HwPosAuthority_Uls_f32     |                | FricOffset_HwNm_f32 |
| HwTrq_HwNm_f32             |                | SatEstFric_HwNm_f32 |
| HwVel_HwRadpS_f32          |                |                     |
| LatAcc_g_f32               |                |                     |
| CRFMtrTrq_MtrNm_f32        |                |                     |
| Temperature_DegC_f32       |                |                     |
| VehicleSpeedValid_Cnt_lgc  |                |                     |
| VehSpd_Kph_f32             |                |                     |
| DefeatFricLearning_Cnt_lgc |                |                     |

## Module Internal Variables

This section identifies the name, range and resolutions for module
specific data created by this module. If there are no range restrictions
on the variable, the term “FULL” is placed into the table for legal
range.

<table>
<colgroup>
<col style="width: 31%" />
<col style="width: 16%" />
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
<td>AvgFricLrn_FiltAvgFric_HwNm_M_f32[4]</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>AVGFRICLRN_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>AvgFricLrn_SatAvgFric_HwNm_M_f32[4]</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>AVGFRICLRN_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>AvgFricLrn_VehBaselineFric_HwNm_M_f32[4]</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>AVGFRICLRN_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>AvgFricLrn_HwAngBuf_HwDeg_M_f32[12]</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>AVGFRICLRN_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>AvgFricLrn_HwVelBuf_HwDegpS_M_f32[12]</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>AVGFRICLRN_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>AvgFricLrn_ColTrqBuf_HwNm_M_f32[6]</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>AVGFRICLRN_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>AvgFricLrn_LearnConstTimer_mS_M_u32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>AVGFRICLRN_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>AvgFricLrn_HwVelKSV_M_str</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>AVGFRICLRN_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="odd">
<td>AvgFricLrn_LatAccKSV_M_str</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>AVGFRICLRN_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="even">
<td>AvgFricLrn_HwPosAuthorityKSV_M_str</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>AVGFRICLRN_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="odd">
<td>AvgFricLrn_VehSpdKSV_M_str</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>AVGFRICLRN_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="even">
<td>AvgFricLrn_TemperatureKSV_M_str</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>AVGFRICLRN_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="odd">
<td>AvgFricLrn_HwAngKSV_M_str</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>AVGFRICLRN_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="even">
<td>AvgFricLrn_ColTrqKSV_M_str</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>AVGFRICLRN_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="odd">
<td>AvgFricLrn_FiltAvgKSV_M_str[4]</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>AVGFRICLRN_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="even">
<td>AvgFricLrn_RawAvgFric_HwNm_M_f32[4]</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>AVGFRICLRN_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>AvgFricLrn_AvgFricChgKSV_M_str</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>AVGFRICLRN_START_SEC_VAR_SAVED_ZONEH_UNSPECIFIED</td>
</tr>
<tr class="even">
<td>Rte_Pim_AvgFricLrnData. AvgFricLrn_VehLearnedFric_HwNm_M_f32[4]</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td></td>
</tr>
<tr class="odd">
<td>Rte_Pim_AvgFricLrnData. AvgFricLrn_Theta_HwNm_M_f32[8][4]</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td></td>
</tr>
<tr class="even">
<td>AvgFricLrn_Rte_Pim_AvgFricLrnData.RangeCounter_Cnt_M_u16[8][3]</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td></td>
</tr>
<tr class="odd">
<td>Rte_Pim_AvgFricLrnData. AvgFricLrn_OpMode_Cnt_M_enum</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td></td>
</tr>
<tr class="even">
<td>Rte_Pim_AvgFricLrnData. AvgFricLrn_FricOffset_HwNm_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td></td>
</tr>
<tr class="odd">
<td>Rte_Pim_AvgFricLrnData. AvgFricLrn_EnableFricLearning_Cnt_lgc</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td></td>
</tr>
<tr class="even">
<td>Rte_Pim_AvgFricLrnData.
AvgFricLrn_EnableFricOffsetOutput_Cnt_lgc</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td></td>
</tr>
<tr class="odd">
<td>AvgFricLrn_DefeatFricOffsetOutput_Cnt_M_lgc</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td></td>
</tr>
<tr class="even">
<td>Rte_Pim_AvgFricLrnData.EOLFric_HwNm_f32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td></td>
</tr>
<tr class="odd">
<td>AvgFricLrn_RunOnce_Cnt_M_lgc</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>AP_AVGFRICLRN_VAR</td>
</tr>
<tr class="even">
<td>AvgFricLrn_FrictionDiagThreshTimer_mS_M_u32</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>See Data Dictionary</td>
<td>AVGFRICLRN_START_SEC_VAR_CLEARED_32</td>
</tr>
</tbody>
</table>

### User defined typedef definition/declaration 

This section documents any user types uniquely used for the module.

<table>
<colgroup>
<col style="width: 29%" />
<col style="width: 32%" />
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
<td>FricLrnModeType</td>
<td><p>FRICLRN_CALIBRATION = 0</p>
<p>FRICLRN_NORMAL = 1</p>
<p>FRICLRN_CLEAR = 2</p>
<p>FRICLRN_IDLE = 3</p>
<p>FRICLRN_BASELINE = 4</p></td>
<td>uint8</td>
<td>0</td>
<td>4</td>
</tr>
</tbody>
</table>

# Constant Data Dictionary

## Calibration Constants

This section lists the calibrations used by the module. For details on
calibration constants, refer to the Data Dictionary for the application.

| Constant Name                           |
|-----------------------------------------|
| t_FrHystHwAPts_HwDeg_f32\[\]            |
| t2_VehSpd_Kph_f32\[\]\[\]               |
| t_MskVehSpd_Cnt_lgc\[\]                 |
| t_FricChgWeight_Uls_f32\[\]             |
| t_InvRatioX_HwDeg_u11p5\[\]             |
| t_InvRatioY_HwNmpMtrNm_u6p10\[\]        |
| k_LearningGain_Uls_f32                  |
| k_LearningThreshold_Cnt_u32             |
| k_RangeCounterLimit_Cnt_u16             |
| k_AvgFricLPFKn_Hz_f32                   |
| k_HwPosAuthMin_Uls_f32                  |
| k_HwVelConstLimit_HwDegpS_f32           |
| k_HwVelMax_HwDegpS_f32                  |
| k_HwVelMin_HwDegpS_f32                  |
| k_LatAccMax_MpSecSqrd_f32               |
| k_LatAccMin_MpSecSqrd_f32               |
| k_SatFricChgLim_HwNm_f32                |
| k_FricOffsetLPFKn_Hz_f32                |
| k_TempMin_DegC_f32                      |
| k_TempMax_DegC_f32                      |
| k_DataPrepLPFKn_Hz_f32                  |
| k_IgnCycleFricChgLim_HwNm_f32           |
| k_FricOffsetLimitLow_HwNm_f32           |
| k_FricOffsetLimitHigh_HwNm_f32          |
| t2_BaselineTheta_HwNm_f32\[\]\[\]       |
| t2_BaselineRangeCounter_Cnt_u16\[\]\[\] |
| t_BaselineFric_HwNm_f32\[\]             |
| k_BaselineEOLFric_HwNm_f32              |
| k_EOLFricDiffScalingFactor_Uls_f32      |
| k_EOLFricDiffLimitLow_HwNm_f32          |
| k_EOLFricDiffLimitHigh_HwNm_f32         |
| k_FrictionDiagTimer_mS_u32              |
| k_FrictionDiagThreshold_HwNm_f32        |

## Program(fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

| Constant Name                 | Resolution             | Units     | Value                                 |
|-----------------------|----------------|----------|------------------------|
| D_10MS_SEC_F32                | Single Precision Float | S         | 0.01                                  |
| D_FRICOFFSETOUTLOLIM_HWNM_F32 | Single Precision Float | HwNm      | -5.0                                  |
| D_FRICOFFSETOUTHILIM_HWNM_F32 | Single Precision Float | HwNm      | 5.0                                   |
| D_ESTFRICLOLIM_HWNM_F32       | Single Precision Float | HwNm      | 0.0                                   |
| D_ESTFRICHILIM_HWNM_F32       | Single Precision Float | HwNm      | 20.0                                  |
| D_SATESTFRICLOLIM_HWNM_F32    | Single Precision Float | HwNm      | 0.0                                   |
| D_SATESTFRICHILIM_HWNM_F32    | Single Precision Float | HwNm      | 20.0                                  |
| D_LRNCNSTRTIME_MS_U32         | 1                      | mS        | 120                                   |
| D_VEHSPDPTNUMX2_CNT_U16       | 1                      | Counts    | D_VEHSPDPTNUM_CNT_U16\*2              |
| D_VEHSPDPTNUM_CNT_U16         | 1                      | Counts    | TableSize_m(t2_VehSpd_Kph_f32)        |
| D_HWPTNUM_CNT_U16             | 1                      | Counts    | TableSize_m(t_FrHystHwAPts_HwDeg_f32) |
| D_HWPTNUMSUB1_CNT_U16         | 1                      | Counts    | D_HWPTNUM_CNT_U16 - D_ONE_CNT_U16     |
| D_BUFSIZE_CNT_U16             | 1                      | Counts    | 12                                    |
| D_PHASESHIFTCNT_CNT_U16       | 1                      | Counts    | 6                                     |
| D_TWO_CNT_U16                 | 1                      | Counts    | 2                                     |
| D_TEN_CNT_U16                 | 1                      | Counts    | 10                                    |
| D_QUARTER_CNT_f32             | Single Precision Float | Counts    | 0.25                                  |
| D_VEHSPDLOIDX_CNT_U16         | 1                      | Counts    | 0                                     |
| D_VEHSPDHIIDX_CNT_U16         | 1                      | Counts    | 1                                     |
| D_ONEG_MPSECSQRD_F32          | Single Precision Float | MpSecSqrd | 9.81                                  |

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

| Constant Name      |
|--------------------|
| D_ONE_CNT_U16      |
| D_ZERO_CNT_U16     |
| D_ONE_ULS_F32      |
| D_ZERO_CNT_U32     |
| D_180OVRPI_ULS_F32 |
| D_FALSE_CNT_LGC    |
| D_TRUE_CNT_LGC     |

###  [section]

### Module specific Lookup Tables Constants

| Constant Name | Resolution | Value | Software Segment |
|---------------|------------|-------|------------------|
| None          |            |       |                  |

# Functions/Macros used by the Sub-Modules 

## Library Functions / Macros 

The library and functions / Macros that are called by the various sub
modules are identified below,

1.  TableSize_m

2.  LPF_Init_f32_m

3.  LPF_KUpdate_f32_m

4.  LPF_OpUpdate_f32_m

5.  FPM_FloatToFixed_m

6.  FPM_FixedToFloat_m

7.  IntplVarXY_u16_u16Xu16Y_Cnt

8.  Abs_f32_m

9.  Limit_m

10. Min_m

11. Max_m

## Data Hiding Functions

1.  Rte_Pim_AvgFricLrnData()

2.  Rte_Call_AvgFricLrnData_WriteBlock()

## Global Functions/Macros Defined by this Module

None

## Local Functions/Macros Used by this MDD only

### Load Buffer

|                      |                      |            |      |      |          |
|-----------------|------------------------------|----------|------|------|------|
| **Function Name**    | LoadBuffer           | Type       | Min  | Max  | UTP Tol. |
| **Arguments Passed** | Input_Uls_T_f32      | float32    | FULL | FULL |          |
|                      | Buffer_Uls_T_f32     | float32 \* | FULL | FULL |          |
|                      | BufferSize_Cnt_T_u16 | uint16     | FULL | FULL |          |
| **Return Value**     | N/A                  |            |      |      |          |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/AvgFricLrn/doc/mediax/media/image2.emf)

### Handwheel Angle Constraint

|                      |                      |            |          |         |          |
|----------------|----------------------------|---------|--------|-------|------|
| **Function Name**    | HwAngConstraint      | Type       | Min      | Max     | UTP Tol. |
| **Arguments Passed** | HwAng_HwDeg_T_f32    | float32    | -1440.11 | 1440.11 |          |
|                      | HwAngOK_Cnt_T_lgc    | boolean \* | FULL     | FULL    |          |
|                      | SelHwAng_HwDeg_T_f32 | float32 \* | -1440.11 | 1440.11 |          |
| **Return Value**     | N/A                  |            |          |         |          |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/AvgFricLrn/doc/mediax/media/image3.emf)

### Handwheel Velocity Constraint

|                      |                     |            |       |      |          |
|-----------------|------------------------------|----------|------|------|------|
| **Function Name**    | HwVelConstraint     | Type       | Min   | Max  | UTP Tol. |
| **Arguments Passed** | HwVel_HwDegpS_T_f32 | float32    | -1833 | 1833 |          |
|                      | HwVelOK_Cnt_T_lgc   | boolean \* | FULL  | FULL |          |
|                      | Direction_Cnt_T_u16 | uint16 \*  | 0     | 1    |          |
| **Return Value**     | N/A                 |            |       |      |          |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/AvgFricLrn/doc/mediax/media/image4.emf)

### Vehicle Speed Constraint

|                      |                       |            |      |      |          |
|-----------------|------------------------------|----------|------|------|------|
| **Function Name**    | VehSpdConstraint      | Type       | Min  | Max  | UTP Tol. |
| **Arguments Passed** | VehSpd_Kph_T_f32      | float32    | 0    | 511  |          |
|                      | VehSpdOK_Cnt_T_lgc    | boolean \* | FULL | FULL |          |
|                      | VehSpdIndex_Cnt_T_u16 | uint16 \*  | 0    | 3    |          |
| **Return Value**     | N/A                   |            |      |      |          |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/AvgFricLrn/doc/mediax/media/image5.emf)

### Friction Learning

|                      |                       |         |          |         |          |
|----------------|-----------------------------|-------|--------|-------|------|
| **Function Name**    | FricLearning          | Type    | Min      | Max     | UTP Tol. |
| **Arguments Passed** | HwAng_HwDeg_T_f32     | float32 | -1440.11 | 1440.11 |          |
|                      | ColTrq_HwNm_T_f32     | float32 | -20      | 20      |          |
|                      | VehSpdIndex_Cnt_T_u16 | uint16  | 0        | 3       |          |
|                      | Direction_Cnt_T_u16   | uint16  | 0        | 1       |          |
| **Return Value**     | N/A                   |         |          |         |          |

#### Friction Learning

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/AvgFricLrn/doc/mediax/media/image6.emf)

#### Range Counter Manager

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/AvgFricLrn/doc/mediax/media/image7.emf)

#### Calculate Average Friction

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/AvgFricLrn/doc/mediax/media/image8.emf)

### Baseline Mode (reset to baseline)

|                      |              |      |     |     |          |
|----------------------|--------------|------|-----|-----|----------|
| **Function Name**    | BaselineMode | Type | Min | Max | UTP Tol. |
| **Arguments Passed** | N/A          |      |     |     |          |
| **Return Value**     | N/A          |      |     |     |          |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/AvgFricLrn/doc/mediax/media/image9.emf)

### Clear Mode (reset to zero)

|                      |           |      |     |     |          |
|----------------------|-----------|------|-----|-----|----------|
| **Function Name**    | ClearMode | Type | Min | Max | UTP Tol. |
| **Arguments Passed** | N/A       |      |     |     |          |
| **Return Value**     | N/A       |      |     |     |          |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/AvgFricLrn/doc/mediax/media/image10.emf)

# Software Module Implementation

## Runtime Environment (RTE) Initial Values

This section lists the initial values of data written by this module but
controlled by the RTE. After RTE initialization, the data in this table
will contain these values.

| Data                                         | Value |
|----------------------------------------------|-------|
| Rte_InitValue_EstFric_HwNm_f32               | 0     |
| Rte_InitValue_FricOffset_HwNm_f32            | 0     |
| Rte_InitValue_HwAng_HwDeg_f32                | 0     |
| Rte_InitValue_HwPosAuthority_Uls_f32         | 0     |
| Rte_InitValue_HwTrq_HwNm_f32                 | 0     |
| Rte_InitValue_HwVel_HwRadpS_f32              | 0     |
| Rte_InitValue_LatAcc_g_f32                   | 0     |
| Rte_InitValue_CRFMtrTrq_MtrNm_f32            | 0     |
| Rte_InitValue_SatEstFric_HwNm_f32            | 0     |
| Rte_InitValue_Temperature_DegC_f32           | 0     |
| Rte_InitValue_VehicleSpeedValid_Cnt_lgc      | FALSE |
| Rte_InitValue_VehSpd_Kph_f32                 | 0     |
| Rte_InitValue_DefeatFrictionLearning_cnt_lgc | FALSE |

## Initialization Functions

### Init: AvgFricLrn_Init1

#### Design Rationale

None

#### Module Outputs

None

#### Module Internal 

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/AvgFricLrn/doc/mediax/media/image11.emf)

##  Periodic Functions

### Per: AvgFricLrn_Per1

#### Design Rationale

None

#### Program Flow Start

#### Rte_Call_AvgFricLrn_Per1_CP0_CheckpointReached()Store Module Inputs to Local copies

HwAngUnfilt_HwDeg_T_f32 = Rte_IRead_AvgFricLrn_Per1_HwAng_HwDeg_f32()

HwPosAuthorityUnfilt_Uls_T_f32 =
Rte_IRead_AvgFricLrn_Per1_HwPosAuthority_Uls_f32()

HwTrq_HwNm_T_f32 = Rte_IRead_AvgFricLrn_Per1_HwTrq_HwNm_f32()

HwVelUnfilt_HwRadpS_T_f32 =
Rte_IRead_AvgFricLrn_Per1_HwVel_HwRadpS_f32()

LatAccUnfilt_g_T_f32 = Rte_IRead_AvgFricLrn_Per1_LatAcc_g_f32()

MtrTrq_MtrNm_T_f32 = Rte_IRead_AvgFricLrn_Per1_CRFMtrTrq_MtrNm_f32()

TemperatureUnfilt_DegC_T_f32 =
Rte_IRead_AvgFricLrn_Per1_Temperature_DegC_f32()

VehSpdUnfilt_Kph_T_f32 = Rte_IRead_AvgFricLrn_Per1_VehSpd_Kph_f32()

VehicleSpeedValid_Cnt_T_lgc =
Rte_IRead_AvgFricLrn_Per1_VehicleSpeedValid_Cnt_lgc()

LatAccUnfilt_MpSecSqrd_T_f32 = LatAccUnfilt_g_T_f32 \*
D_ONEG_MPSECSQRD_F32

HwVelUnfilt_HwDegpS_T_f32 = HwVelUnfilt_HwRadpS_T_f32 \*
D_180OVRPI_ULS_F32

OpMode_Cnt_T_enum = Rte_Pim_AvgFricLrnData()-\>OpMode_Cnt_enum

#### DefeatFricLearning_Cnt_T_lgc = Rte_IRead_AvgFricLrn_Per1_DefeatFricLearning_Cnt_lgc()Determine Mode

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/AvgFricLrn/doc/mediax/media/image12.emf)

#### Prep Data

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/AvgFricLrn/doc/mediax/media/image13.emf)

#### Learning Constraint

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/AvgFricLrn/doc/mediax/media/image14.emf)

#### Calibration/Running Modes

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/AvgFricLrn/doc/mediax/media/image15.emf)

#### Fault Injection

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/AvgFricLrn/doc/mediax/media/image16.emf)

#### Store Local copy of outputs into Module Outputs

Rte_IWrite_AvgFricLrn_Per1_FricOffset_HwNm_f32(FricOffsetOut_HwNm_T_f32)

Rte_IWrite_AvgFricLrn_Per1_EstFric_HwNm_f32(AvgFricLrn_EstFric_HwNm_M_f32)

Rte_IWrite_AvgFricLrn_Per1_SatEstFric_HwNm_f32(AvgFricLrn_SatEstFric_HwNm_M_f32)

#### Program Flow End

Rte_Call_AvgFricLrn_Per1_CP1_CheckpointReached()

##  Fault Recovery Functions

None

## Shutdown Functions

None

## Interrupt Functions

None

## Serial Communication Functions

### SCom: AvgFricLrn_SCom_GetEOLFric

|                      |                            |         |     |     |          |
|----------------|-----------------------------|-------|--------|-------|------|
| **Function Name**    | AvgFricLrn_SCom_GetEOLFric | Type    | Min | Max | UTP Tol. |
| **Arguments Passed** | \*EOLFric_HwNm_f32         | uint8\* | 0   | 127 | N/A      |
| **Return Value**     | N/A                        |         |     |     |          |

#### Design Rationale

None

#### Program Flow Start

N/A

#### Store Module Inputs to Local copies

None

#### Read EOLFric Service

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/AvgFricLrn/doc/mediax/media/image17.emf)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

None

### SCom: AvgFricLrn_SCom\_ GetOffsetOutputDefeat

|                      |                                         |           |       |      |          |
|----------------|-----------------------------|--------|--------|-------|------|
| **Function Name**    | AvgFricLrn_SCom\_ GetOffsetOutputDefeat | Type      | Min   | Max  | UTP Tol. |
| **Arguments Passed** | \* DefeatOffsetOutput_Cnt_lgc           | boolean\* | FALSE | TRUE | 0        |
| **Return Value**     | N/A                                     |           |       |      |          |

#### Design Rationale

None

#### Program Flow Start

N/A

#### Store Module Inputs to Local copies

None

#### Read Offset Output Defeat Service

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/AvgFricLrn/doc/mediax/media/image18.emf)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

None

### SCom: AvgFricLrn_SCom\_ GetSelect

|                      |                               |           |       |      |          |
|----------------|-----------------------------|--------|--------|-------|------|
| **Function Name**    | AvgFricLrn_SCom\_ GetSelect   | Type      | Min   | Max  | UTP Tol. |
| **Arguments Passed** | \* EnableFricLearning_Cnt_lgc | boolean\* | FALSE | TRUE | 0        |
|                      | \*EnableOffsetOutput_Cnt_lgc  | boolean\* | FALSE | TRUE | 0        |
|                      | \*OpMode_Uls_u08              | uint8\*   | 0     | 4    | 0        |
| **Return Value**     | N/A                           |           |       |      |          |

#### Design Rationale

None

#### Program Flow Start

N/A

#### Store Module Inputs to Local copies

None

#### Read Select Service

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/AvgFricLrn/doc/mediax/media/image19.emf)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

None

### SCom: AvgFricLrn_SCom_InitLearnedTables

|                      |                                   |      |     |     |          |
|----------------|-----------------------------|-------|--------|-------|------|
| **Function Name**    | AvgFricLrn_SCom_InitLearnedTables | Type | Min | Max | UTP Tol. |
| **Arguments Passed** | N/A                               |      |     |     |          |
| **Return Value**     | N/A                               |      |     |     |          |

#### Design Rationale

None

#### Program Flow Start

N/A

#### Store Module Inputs to Local copies

None

#### Restore Tables to Baseline Values Service

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/AvgFricLrn/doc/mediax/media/image20.emf)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

None

### SCOM: AvgFricLrn_SCom_ResetToZero

|                      |                             |      |     |     |          |
|----------------------|-----------------------------|------|-----|-----|----------|
| **Function Name**    | AvgFricLrn_SCom_ResetToZero | Type | Min | Max | UTP Tol. |
| **Arguments Passed** | N/A                         |      |     |     |          |
| **Return Value**     | N/A                         |      |     |     |          |

#### Design Rationale

None

#### Program Flow Start

N/A

#### Store Module Inputs to Local copies

None

#### Reset Tables to Zero Service

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/AvgFricLrn/doc/mediax/media/image21.emf)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

None

### SCom: AvgFricLrn_SCom_SetEOLFric

|                      |                            |       |     |     |          |
|----------------------|----------------------------|-------|-----|-----|----------|
| **Function Name**    | AvgFricLrn_SCom_SetEOLFric | Type  | Min | Max | UTP Tol. |
| **Arguments Passed** | EOLFric_HwNm_u08           | uint8 | 0   | 127 |          |
| **Return Value**     | N/A                        |       |     |     |          |

#### Design Rationale

None

#### Program Flow Start

N/A

#### Store Module Inputs to Local copies

None

#### Store EOL Friction Service

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/AvgFricLrn/doc/mediax/media/image22.emf)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

None

### SCom: AvgFricLrn_SCom_SetOffsetOutputDefeat

|                      |                                       |         |       |      |          |
|----------------|-----------------------------|-------|--------|-------|------|
| **Function Name**    | AvgFricLrn_SCom_SetOffsetOutputDefeat | Type    | Min   | Max  | UTP Tol. |
| **Arguments Passed** | DefeatOffsetOutput_Cnt_lgc            | Boolean | FALSE | TRUE |          |
| **Return Value**     | N/A                                   |         |       |      |          |

#### Design Rationale

None

#### Program Flow Start

N/A

#### Store Module Inputs to Local copies

None

#### Defeat Offset Output Service

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/AvgFricLrn/doc/mediax/media/image23.emf)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

None

### SCom: AvgFricLrn_SCom_SetSelect

|                      |                            |         |       |      |          |
|----------------|-----------------------------|-------|--------|-------|------|
| **Function Name**    | AvgFricLrn_SCom_SetSelect  | Type    | Min   | Max  | UTP Tol. |
| **Arguments Passed** | EnableFricLearning_Cnt_lgc | Boolean | FALSE | TRUE |          |
|                      | EnableOffsetOutput_Cnt_lgc | Boolean | FALSE | TRUE |          |
|                      | OpMode_Uls_u08             | Uint8   | 0     | 4    |          |
| **Return Value**     | N/A                        |         |       |      |          |

#### Design Rationale

None

#### Program Flow Start

N/A

#### Store Module Inputs to Local copies

None

#### Select Mode and Enable Service

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/AvgFricLrn/doc/mediax/media/image24.emf)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

None

## Transition Functions

### Trns: AvgFricLrn_Trns1

#### Design Rationale

This function implements the Power Off functions defined in the FDD
model.

#### Program Flow Start

N/A

#### Store Module Inputs to Local copies

None

#### Save Learned Friction to NvM

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/AvgFricLrn/doc/mediax/media/image25.emf)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

N/A

##  

# Execution Requirements

## Execution Sequence of the Module

AvgFricLrn_Per1 executes at a rate of 10 ms. AvgFricLrn_Trns1 executes
on power down.

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

| Function Name    | Calling Frequency | System State(s) in which the function is called |
|--------------------------|-----------------|------------------------------|
| AvgFricLrn_Init1 | On Event          | On Init                                         |
| AvgFricLrn_Per1  | 10 ms             | OPERATE                                         |
| AvgFricLrn_Trns1 | On Event          | On Entering OFF                                 |

## Execution Requirements for Serial Communication Functions 

| Function Name | Sub-Module called by (Serial Comm Function Name) |
|---------------|--------------------------------------------------|
| None          |                                                  |

#  [section-2]

#  Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

| Name of Sub Module | Software Segment                      |
|--------------------|---------------------------------------|
| AvgFricLrn_Init1   | RTE_START_SEC_AP_AVGFRICLRN_APPL_CODE |
| AvgFricLrn_Per1    | RTE_START_SEC_AP_AVGFRICLRN_APPL_CODE |
| AvgFricLrn_Trns1   | RTE_START_SEC_AP_AVGFRICLRN_APPL_CODE |

##  [section-3]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

| Name of Sub Module | Software Segment            |
|--------------------|-----------------------------|
| LoadBuffer         | RTE_AP_AVGFRICLRN_APPL_CODE |
| HwAngConstraint    | RTE_AP_AVGFRICLRN_APPL_CODE |
| HwVelConstraint    | RTE_AP_AVGFRICLRN_APPL_CODE |
| VehSpdConstraint   | RTE_AP_AVGFRICLRN_APPL_CODE |
| FricLearning       | RTE_AP_AVGFRICLRN_APPL_CODE |
| BaselineMode       | RTE_AP_AVGFRICLRN_APPL_CODE |
| ClearMode          | RTE_AP_AVGFRICLRN_APPL_CODE |

#  [section-4]

#  Known Issues / Limitations With Design

1.  INLINE functions defined in GlobalMacro.h are not unit tested.

#  Revision Control Log

|             |            |                                                                    |            |                     |
|------|------|--------------------------------------------|---------|---------|
| **Item \#** | **Rev \#** | **Change Description**                                             | **Date**   | **Author Initials** |
| 1           | 1.0        | Initial Version                                                    | 24-May-12  | OT                  |
| 2           | 2.0        | Fixed FPM type for calibration causing overflow                    | 08-Jun-12  | OT                  |
| 3           | 3.0        | Fixed anomaly 3399 and initialization issue                        | 26-Jun-12  | OT                  |
| 4           | 4.0        | Fixed integration issues                                           | 24-Jul-12  | OT                  |
| 5           | 5.0        | Fixed UTP Issue                                                    | 30-Jul-12  | OT                  |
| 6           | 6.0        | Updated to SF-07 version 002                                       | 13-Sep-12  | JWJ                 |
| 7           | 7.0        | Added watchdog checkpoints                                         | 24-Sept-12 | BWL                 |
| 8           | 8.0        | Corrected code typographical mismatches and corrected anomaly 3872 | 27-Sep-12  | JWJ                 |
| 9           | 9.0        | Added SCom get functions to return written values                  | 24-Oct-12  | JWJ                 |
| 10          | 10.0       | Updated MDD for UTP Catchups                                       | 28-Jan-13  | NRAR                |
| 11          | 11.0       | Set PrevOpMode in SetSelect per anom 4679                          | 08-July-13 | BWL                 |
| 12          | 12.0       | Updated to SF-07 version 003                                       | 25-Oct-13  | VK                  |
| 13          | 13.0       | Anomaly 4634                                                       | 10-Dec-13  | RM                  |
| 14          | 14.0       | Anomaly 6297 Limit Outputs                                         | 02-Apr-14  | SB                  |
| 15          | 15.0       | Updated per Design Review, QAC fixes                               | 12-May-14  | SB                  |

{% endraw %}