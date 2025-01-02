---
layout: default
title: DigPhsReasDiag_MDD
nav_order: 2
parent: Component
---
{% raw %}
# Module -- Digital Phase Reasonableness Diagnostic [module----digital-phase-reasonableness-diagnostic]

# High-Level Description

This module compares the commanded duty cycle to each phase with the
feedback from the NHET module. The values are compared, compensated with
a previously defined fixed value, filtered, and compared against a valid
threshold.

# Figures

## Component Diagram

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SVDiag/doc/mediax/media/image2.png"
style="width:2.27778in;height:2.06145in" />

## Diagram – Function Data Sharing

No Shared Data.

#  Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

| Module Inputs                         | Module Outputs |     |
|---------------------------------------|----------------|-----|
| ExpectedOnTimeA_Cnt_u32               |                |     |
| ExpectedOnTimeB_Cnt_u32               |                |     |
| ExpectedOnTimeC_Cnt_u32               |                |     |
| MeasuredOnTimeA_Cnt_u32               |                |     |
| MeasuredOnTimeB_Cnt_u32               |                |     |
| MeasuredOnTimeC_Cnt_u32               |                |     |
| LRPRCorrectedMtrPosCaptured_rev_u0p16 |                |     |
| LRPRPhaseadvanceCaptured_Cnt_s16      |                |     |
| LRPRModulationIndexCaptured_Uls_f32   |                |     |
| MotorVelMRFUnfiltered_MtrRadpS_f32    |                |     |
| ElecMechPolarity_Cnt_s08              |                |     |
| PDActivateTest_Cnt_lgc                |                |     |
| GateDriveResetActive_Cnt_lgc          |                |     |

## Module Internal Variables

This section identifies the name, range and resolutions for module
specific data created by this module. If there are no range restrictions
on the variable, the term “FULL” is placed into the table for legal
range.

<table>
<colgroup>
<col style="width: 37%" />
<col style="width: 10%" />
<col style="width: 12%" />
<col style="width: 15%" />
<col style="width: 25%" />
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
<td>SVDiag_FilterSV_Cnt_M_s18p13[3]</td>
<td>2<sup>-13</sup></td>
<td>-210000</td>
<td>210000</td>
<td>DIGPHSREASDIAG_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>SVDiag_PrevLRPRHighSector_Cnt_M_lgc</td>
<td>N/A</td>
<td>FALSE</td>
<td>TRUE</td>
<td>DIGPHSREASDIAG_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="odd">
<td>SVDiag_LRPRHighSector_Cnt_M_lgc</td>
<td>N/A</td>
<td>FALSE</td>
<td>TRUE</td>
<td>DIGPHSREASDIAG_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="even">
<td>SVDiag_PrevLRPRLowSector_Cnt_M_lgc</td>
<td>N/A</td>
<td>FALSE</td>
<td>TRUE</td>
<td>DIGPHSREASDIAG_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="odd">
<td>SVDiag_LRPRLowSector_Cnt_M_lgc</td>
<td>N/A</td>
<td>FALSE</td>
<td>TRUE</td>
<td>DIGPHSREASDIAG_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="even">
<td>SVDiag_LRPRAdjModldAComp_Cnt_M_f32</td>
<td>Single precision float</td>
<td>0</td>
<td>1</td>
<td>DIGPHSREASDIAG_START_SEC_VAR_CLEARED_FLOAT32</td>
</tr>
<tr class="odd">
<td>SVDiag_PrevLRPRAdjModldComp_Cnt_M_f32</td>
<td>Single precision float</td>
<td>0</td>
<td>1</td>
<td>DIGPHSREASDIAG_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>SVDiag_PrevLRPRPhsAdvComp_Cnt_M_u16</td>
<td>1</td>
<td>0</td>
<td>6144</td>
<td>DIGPHSREASDIAG_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="odd">
<td>SVDiag_LRPRPhsAdvComp_Cnt_M_u16</td>
<td>1</td>
<td>0</td>
<td>6144</td>
<td>DIGPHSREASDIAG_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td>SVDiag_PhaseOffset_Rev_M_u0p16</td>
<td>2<sup>-16</sup></td>
<td>0</td>
<td>1</td>
<td>DIGPHSREASDIAG_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="odd">
<td>SVDiag_LowPhReasErrorAcc_Cnt_M_u16</td>
<td>1</td>
<td>0</td>
<td>1000</td>
<td>DIGPHSREASDIAG_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td>SVDiag_HighResPhsReasDisable_M_u8</td>
<td>1</td>
<td>0</td>
<td>100</td>
<td>DIGPHSREASDIAG_START_SEC_VAR_CLEARED_8</td>
</tr>
<tr class="odd">
<td>SVDiag_LowResPhsReasDisable_M_u8</td>
<td>1</td>
<td>0</td>
<td>100</td>
<td>DIGPHSREASDIAG_START_SEC_VAR_CLEARED_8</td>
</tr>
<tr class="even">
<td>SVDiag_MaxNrCommOffVltg_Cnt_M_f32</td>
<td>Single precision float</td>
<td>0</td>
<td>86400</td>
<td>DIGPHSREASDIAG_START_SEC_VAR_CLEARED_FLOAT32</td>
</tr>
<tr class="odd">
<td>SVDiag_LRPRHighLimit_Cnt_D_f32[3]</td>
<td>Single precision float</td>
<td>0</td>
<td>160000</td>
<td>DIGPHSREASDIAG_START_SEC_VAR_CLEARED_FLOAT32</td>
</tr>
<tr class="even">
<td>SVDiag_LRPRLowLimit_Cnt_D_f32[3]</td>
<td>Single precision float</td>
<td>0</td>
<td>160000</td>
<td>DIGPHSREASDIAG_START_SEC_VAR_CLEARED_FLOAT32</td>
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

| Constant Name                         |
|---------------------------------------|
| k_PhsReasErrorTerm_Cnt_s16            |
| k_ErrorFiltKn_Cnt_u16                 |
| k_ErrorThresh_Cnt_u32                 |
| k_PhsReasEnableThresh_Cnt_u32         |
| k_LRPRMtrVelDiagEnable_MtrRadpS_T_f32 |
| k_LowResPhsReas_Cnt_str               |
| k_LowResPhsReasMinTol_Uls_f32         |
| k_LowResPhsReasMaxTol_Uls_f32         |
| t_CommOffsetTblY_Cnt_u16              |
| k_LRPRCommOffsetMargin_Uls_f32        |

The time constant for the filter is analyzed in the following filter
analysis workbook:

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SVDiag/doc/mediax/media/image3.emf)

## Program(fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

| Constant Name                | Resolution             | Units  | Value                                                                              |
|-------------------------------|--------------|-----------|------------------|
| D_ERRORLIMIT_CNT_S32         | 8                      | Counts | 262136                                                                             |
| D_PHASEA_CNT_U16             | 1                      | Counts | 0                                                                                  |
| D_PHASEB_CNT_U16             | 1                      | Counts | 1                                                                                  |
| D_PHASEC_CNT_U16             | 1                      | Counts | 2                                                                                  |
| D_RESETDIGDIAGACTIVE_CNT_U08 | 1                      | Counts | 0x00U                                                                              |
| D_LRPHSREASLOOPRATE_CNT_F32  | 1                      | Counts | 0.002F                                                                             |
| D_ERRORLIMIT_CNT_S32         | 1                      | Counts | 262136L/\*2\^18-8==262136\*/                                                       |
| D_PHASEA_CNT_U16             | 1                      | Counts | 0U                                                                                 |
| D_PHASEB_CNT_U16             | 1                      | Counts | 1U                                                                                 |
| D_PHASEC_CNT_U16             | 1                      | Counts | 2U                                                                                 |
| D_NHETFREQUENCY_HZ_F32       | Single precision float | Counts | 80000000.0F                                                                        |
| D_NHETCTSPERLRPRLOOP_CNT_F32 | Single precision float | Counts | (D_NHETFREQUENCY_HZ_F32\*D_LRPHSREASLOOPRATE_CNT_F32)                              |
| D_MAXPWMFREQ_HZ_U32          | Single precision float | Counts | 18000                                                                              |
| D_MAXNRCOMMOFFVLTG_CNT_F32   | Single precision float | Counts | (D_LRPHSREASLOOPRATE_CNT_F32\*D_MAXPWMFREQ_CNT_F32\*t_CommOffsetTblY_Cnt_u16\[0\]) |
| D_PHSADVCNTSPERREV_CNT_U16   | 1                      | Counts | 6144U                                                                              |
| D_PHSADVCNTS180DEG_CNT_U16   | 1                      | Counts | 3072U/\*(D_PHSADVCNTSPERREV_CNT_S16/2U)\*/                                         |
| D_PHSPOSADVCNTS90DEG_CNT_U16 | 1                      | Counts | 1536U/\*(D_PHSADVCNTSPERREV_CNT_S16/4U)\*/                                         |
| D_PHSNEGADVCNTS90DEG_CNT_S16 | 1                      | Counts | -1536/\*(-D_PHSADVCNTSPERREV_CNT_S16/4U)\*/                                        |
| D_0DEG_REV_U0P16             | 1                      | rev    | (FPM_InitFixedPoint_m(0.0,u0p16_T))                                                |
| D_30DEG_REV_U0P16            | 1                      | rev    | (FPM_InitFixedPoint_m(0.0833333333,u0p16_T))                                       |
| D_60DEG_REV_U0P16            | 1                      | rev    | (FPM_InitFixedPoint_m(0.1666666666,u0p16_T))                                       |
| D_240DEG_REV_U0P16           | 1                      | rev    | (FPM_InitFixedPoint_m(0.6666666666,u0p16_T))                                       |
| D_120DEG_REV_U0P16           | 1                      | rev    | (FPM_InitFixedPoint_m(0.3333333333,u0p16_T))                                       |
| D_180DEG_REV_U0P16           | 1                      | rev    | (FPM_InitFixedPoint_m(0.5,u0p16_T))                                                |
| D_PHASEAOFFSETNRM_REV_U0P16  | 2-16                   | rev    | D_0DEG_REV_U0P16                                                                   |
| D_PHASEBOFFSETNRM_REV_U0P16  | 2-16                   | rev    | ((uint16)(D_PHASEAOFFSETNRM_REV_U0P16-D_120DEG_REV_U0P16))                         |
| D_PHASECOFFSETNRM_REV_U0P16  | 2-16                   | rev    | (D_PHASEAOFFSETNRM_REV_U0P16+D_120DEG_REV_U0P16)                                   |
| D_PHASEAOFFSETINV_REV_U0P16  | 2-16                   | rev    | D_60DEG_REV_U0P16                                                                  |
| D_PHASEBOFFSETINV_REV_U0P16  | 2-16                   | rev    | (D_PHASEAOFFSETINV_REV_U0P16+D_120DEG_REV_U0P16)                                   |
| D_PHASECOFFSETINV_REV_U0P16  | 2-16                   | rev    | ((uint16)(D_PHASEAOFFSETINV_REV_U0P16-D_120DEG_REV_U0P16))                         |
| D_REVPCNT_ULS_U0P32          | 1                      | Uls    | 699051UL/\*(FPM_InitFixedPoint_m(1/D_PACNTSPREV_ULS_U16P0,u0p32_T))\*/             |
| D_PACNTSPREV_ULS_U16P0       | 1                      | Uls    | 6144U                                                                              |
| D_SCALER16_CNT_U16           | 1                      | cnt    | 16U                                                                                |
| D_35DEG_REV_U0P16            | 1                      | rev    | (FPM_InitFixedPoint_m(0.0972222222,u0p16_T))                                       |
| D_205DEG_REV_U0P16           | 1                      | rev    | (FPM_InitFixedPoint_m(0.5972222222,u0p16_T))                                       |
| D_245DEG_REV_U0P16           | 1                      | rev    | (FPM_InitFixedPoint_m(0.6805555555,u0p16_T))                                       |
| D_355DEG_REV_U0P16           | 1                      | rev    | (FPM_InitFixedPoint_m(0.9861111111,u0p16_T))                                       |
| D_POSITIVEONE_CNT_S8         | 1                      | cnt    | 1                                                                                  |

####  [section]

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

| Constant Name |
|---------------|
| \<None\>      |

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

1.  Limit_m

2.  FPM_Fix_m

3.  LPF_SvUpdate_s16InFixKTrunc_m

4.  LPF_OpUpdate_s16InFixKTrunc_m

5.  Max_m

6.  Min_M

7.  Abs_s16_m

8.  Abs_f16_m

9.  

## Data Hiding Functions

1.  \<None\>

2.  

## Global Functions/Macros Defined by this Module

None

## Local Functions/Macros Used by this MDD only

### Local Function \#1

|                      |                            |       |     |     |          |
|----------------------|----------------------------|-------|-----|-----|----------|
| **Function Name**    | PhaseGroundTabLookupoffset | Type  | Min | Max | UTP Tol. |
| **Arguments Passed** | MtrElecMechPol_Cnt_s8      | Sint8 | -1  | 1   |          |
|                      |                            |       |     |     |          |
| **Return Value**     | None                       |       |     |     |          |

#### Description

### Generates the phase offset ![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SVDiag/doc/mediax/media/image4.emf)Local Function \#2

|                      |                      |        |     |      |          |
|----------------------|----------------------|--------|-----|------|----------|
| **Function Name**    | Read_CountToRev      | Type   | Min | Max  | UTP Tol. |
| **Arguments Passed** | Var_Cnt_T_u16        | Unit16 | 0   | 6144 |          |
|                      |                      |        |     |      |          |
| **Return Value**     | CountToRev_Rev_T_u16 | Unit16 | 0   | 1    |          |

#### Description

Converts Var_Cnt_T_u16 to Unit16 with range of 0 to 1 and precision of
2^-16^. It coverts Electrical degree(Count) to Rev

# Software Module Implementation

## Runtime Environment (RTE) Initial Values

This section lists the initial values of data written by this module but
controlled by the RTE. After RTE initialization, the data in this table
will contain these values.

| Data                                              | Value |
|---------------------------------------------------|-------|
| Rte_InitValue_ExpectedOnTimeA_Cnt_u32             | 0     |
| Rte_InitValue_ExpectedOnTimeB_Cnt_u32             | 0     |
| Rte_InitValue_ExpectedOnTimeC_Cnt_u32             | 0     |
| Rte_InitValue_MeasuredOnTimeA_Cnt_u32             | 0     |
| Rte_InitValue_MeasuredOnTimeB_Cnt_u32             | 0     |
| Rte_InitValue_MeasuredOnTimeC_Cnt_u32             | 0     |
| Rte_InitValue_LRPRCorrectedMtrPosCaptured_Rev_f32 |       |
| Rte_InitValue_LRPRModulationIndexCaptured_Uls_f32 | 0     |
| Rte_InitValue_LRPRPhaseadvanceCaptured_Cnt_s16    | 0     |
| Rte_InitValue_MotorVelMRFUnfiltered_MtrRadpS_f32  |       |
| Rte_InitValue_MtrElecMechPolarity_Cnt_s08         | 0     |
| Rte\_ InitValue\_ PDActivateTest_Cnt_lgc          | 0     |
| Rte\_ InitValue\_ GateDriveResetActive_Cnt_lgc    | 0     |

## Initialization Functions

### DigPhsReasDiag_Init

## ![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SVDiag/doc/mediax/media/image5.emf) Periodic Functions

### Per: DigPhsReasDiag\_ Per1

#### Design Rationale

The ParamBits_Cnt_T_u08 variable used in this function, which is passed
when calling NxtrDiagMgr_SetNTCStatus, is set according to the following
table (derived from the DTC Outline Structure document):

| Bit 0 | Phase A: measured less than expected    |
|-------|-----------------------------------------|
| Bit 1 | Phase A: measured greater than expected |
| Bit 2 | Phase B: measured less than expected    |
| Bit 3 | Phase B: measured greater than expected |
| Bit 4 | Phase C: measured less than expected    |
| Bit 5 | Phase C: measured greater than expected |
| Bit6  | Systematic diagnostics LRPR Active      |

#### Program Flow Start

Rte_Call_DigPhsReasDiag_Per1_CP0_CheckpointReached()

#### Store Module Inputs to Local copies

MeasuredOnTime_Cnt_T_u32\[D_PHASEA_CNT_U16\] =
Rte_IRead_DigPhsReasDiag_Per1_MeasuredOnTimeA_Cnt_u32();

MeasuredOnTime_Cnt_T_u32\[D_PHASEB_CNT_U16\] =
Rte_Iread_DigPhsReasDiag_Per1_MeasuredOnTimeB_Cnt_u32();

MeasuredOnTime_Cnt_T_u32\[D_PHASEC_CNT_U16\] =
Rte_Iread_DigPhsReasDiag_Per1_MeasuredOnTimeC_Cnt_u32();

ExpectedOnTime_Cnt_T_u32\[D_PHASEA_CNT_U16\] =
Rte_Iread_DigPhsReasDiag_Per1_ExpectedOnTimeA_Cnt_u32();

ExpectedOnTime_Cnt_T_u32\[D_PHASEB_CNT_U16\] =
Rte_Iread_DigPhsReasDiag_Per1_ExpectedOnTimeB_Cnt_u32();

ExpectedOnTime_Cnt_T_u32\[D_PHASEC_CNT_U16\] =
Rte_Iread_DigPhsReasDiag_Per1_ExpectedOnTimeC_Cnt_u32();

LRPRMtrPosCaptured_Rev_T_f32=Rte_IRead_DigPhsReasDiag_Per1_LRPRCorrectedMtrPosCaptured_Rev_f32();

LRPRPhaseadvanceCaptured_Cnt_T_s16
=Rte_IRead_DigPhsReasDiag_Per1_LRPRPhaseadvanceCaptured_Cnt_s16();

LRPRModIdx_Uls_T_f32 =
Rte_IRead_DigPhsReasDiag_Per1_LRPRModulationIndexCaptured_Uls_f32();

MotorVelMRFUnfilt_MtrRadpS_T_f32 =
Rte_IRead_DigPhsReasDiag_Per1_MotorVelMRFUnfiltered_MtrRadpS_f32();

MtrElecMechPolarity_Cnt_T_s08=Rte_IRead_DigPhsReasDiag_Per1_ElecMechPolarity_Cnt_s08();

PDActivateTest_Cnt_T_lgc =
Rte_IRead_DigPhsReasDiag_Per1_PDActivateTest_Cnt_lgc();

GateDriveResetActive_Cnt_T_lgc =
Rte_IRead_DigPhsReasDiag_Per1_GateDriveResetActive_Cnt_lgc();

#### Subfunction Execution

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SVDiag/doc/mediax/media/image6.emf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SVDiag/doc/mediax/media/image7.emf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SVDiag/doc/mediax/media/image8.emf)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

Rte_Call_DigPhsReasDiag_Per1_CP1_CheckpointReached()

### Per: DigPhsReasDiag_Trans1

#### Design Rationale

Reset the HighRes Phase Reasonableness and LowRes Phase Reasonableness
delay counter to 0 upon entering in Operate mode

#### Program Flow Start

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SVDiag/doc/mediax/media/image9.emf)

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

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

| Function Name         | Calling Frequency | System State(s) in which the function is called |
|--------------------------|-----------------|------------------------------|
| DigPhsReasDiag_Per1   | 2 ms              | Operate                                         |
| DigPhsReasDiag_Trans1 | Upon Transition   | Upon entering in Operate                        |

## Execution Requirements for Serial Communication Functions 

| Function Name | Sub-Module called by (Serial Comm Function Name) |
|---------------|--------------------------------------------------|
| \<None\>      |                                                  |

#  [section-2]

#  Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

| Name of Sub Module | Software Segment |
|--------------------|------------------|
|                    |                  |

##  [section-3]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

| Name of Sub Module | Software Segment |
|--------------------|------------------|
|                    |                  |

#  [section-4]

#  Known Issues / Limitations With Design

1.  INLINE functions defined in globalmacro.h are not unit tested

#  Revision Control Log

|             |            |                                                                               |           |                     |
|------|------|--------------------------------------------|---------|---------|
| **Item \#** | **Rev \#** | **Change Description**                                                        | **Date**  | **Author Initials** |
| 1           | 1.0        | Initial Version                                                               | 25-Jan-12 | OT                  |
| 2           | 2.0        | Changed Input Names to Match FDD                                              | 27-Jan-12 | OT                  |
| 3           | 3.0        | Updated Operation states to show only runs in Operate                         | 27Jan12   | SMW                 |
| 4           | 4.0        | Updated to latest FDD changes (rev 002-G), consolidated common processing     | 31-Jan-12 | OT                  |
| 5           | 5          | Added checkpoints and memmap software segment is updated for static variables | 26-Sep-12 | Selva               |
| 6           | 6          | Updated for Changes for LRPR                                                  | 26 Oct 12 | Selva               |
| 7           | 7.0        | Updated to FDD V007                                                           | 15 Mar 13 | SP                  |
| 8           | 8          | Anamoly 4968,4953 changes                                                     | 7-May-13  | Selva               |
| 9           | 9          | Anamoly 5000 changes                                                          | 13-May-13 | Selva               |
| 10          | 10         | Fixing Ranges and Data type for unit test results                             | 16-May-13 | Selva               |
| 11          | 11         | Added Cal “k_LRPRCommOffsetMargin_Uls_f32” for FDD v4                         | 26-Jun-13 | Selva               |
| 12          | 12         | Corrected anomaly 5174                                                        | 30-Jul-13 | VT                  |
| 13          | 13         | Update range per unit test results                                            | 12-Aug-13 | VT                  |
| 14          | 14         | Update module and display variables with SVDiag                               | 3-Oct-13  | VT                  |
| 15          | 15         | Updated to FDD V008                                                           | 1-Dec-14  | Rijvi               |

{% endraw %}