---
layout: default
title: MotorVelocity_MDD
nav_order: 6
parent: MtrVel_Digi
---
{% raw %}
# Module -- Motor Velocity [module----motor-velocity]

# High-Level Description

# Figures

## Diagram – Function Data Sharing

This diagram shows all data that is shared between functions within the
module.

No Shared Data

### Diagram – MtrVel_Per1

This diagram describes the functional characteristics and data flow of a
given function.

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrVel_Digi/doc/mediax/media/image1.png"
style="width:3.74028in;height:3.44861in" />

# Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

(Note: Full variable names required in table.)

(Note: All global variables including End Of Line data used should be
shown here)

|                                      |                                       |
|----------------------------------|--------------------------------------|
| Module Inputs (Global Variable Name) | Module Outputs (Global Variable Name) |
| AsstAssemblyPolarity_Cnt_s08         | SysCMotorVelMRF_MtrRadpS_f32          |
| SysCDiagHandwheelVel_HwRadpS_f32     | SysCHandwheelVel_HwRadpS_f32          |
| SysCDiagMtrVelMRF_MtrRadpS_f32       | MotorVelCRF_MtrRadpS_f32              |
| MechMtrPos2_Rev_u0p16                | MotorVelMRF_MtrRadpS_f32              |
| MechMtrPos1Timestamp_USec_u32        | HandWheelVel_HwRadpS_f32              |
| MechMtrPos1_Rev_u0p16                | HwVelValid_Cnt_lgc                    |
| MechMtrPos2Timestamp_USec_u32        |                                       |
| SysCDiagHwVel_HwRadpS_f32            |                                       |
|                                      |                                       |

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
<td>MtrVel_WestBlendedMtrVel_MtrRadpS_D_f32</td>
<td>Single Precision Floating Point</td>
<td>-1350</td>
<td>1350</td>
<td>MTRVEL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>MtrVel_PrevMtrPosMechMtrPos2_Rad_M_f32</td>
<td>Single Precision Floating Point</td>
<td>-2*pi</td>
<td>2*pi</td>
<td>MTRVEL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>MtrVel_CrsMtrVel_MtrRadpS_D_f32</td>
<td>Single Precision Floating Point</td>
<td>-1350</td>
<td>1350</td>
<td>MTRVEL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>MtrVel_PriMtrVel_MtrRadpS_D_f32</td>
<td>Single Precision Floating Point</td>
<td>-1350</td>
<td>1350</td>
<td>MTRVEL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>MtrVel_HwVel_HwRadpS_M_f32</td>
<td>Single Precision Floating Point</td>
<td>-42</td>
<td>42</td>
<td>MTRVEL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>MtrVel_MtrVelCorrLimDiff_MtrRadpS_D_f32</td>
<td>Single Precision Floating Point</td>
<td>0</td>
<td>2700</td>
<td>MTRVEL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>MtrVel_HwVelCorrLimDiff_HwRadpS_D_f32</td>
<td>Single Precision Floating Point</td>
<td>0</td>
<td>84</td>
<td>MTRVEL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>MtrVel_DiffAcc_Cnt_M_u16</td>
<td>1</td>
<td>0</td>
<td>255</td>
<td>MTRVEL_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td>MtrVel_HwVelDiffAcc_Cnt_M_u16</td>
<td>1</td>
<td>0</td>
<td>255</td>
<td>MTRVEL_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="odd">
<td>MtrVel_OsBufSelect_Cnt_M_u08</td>
<td>1</td>
<td>0</td>
<td>4</td>
<td>MTRVEL_START_SEC_VAR_CLEARED_8</td>
</tr>
<tr class="even">
<td>MtrVel_OldPosBuf_Cnt_M_u08</td>
<td>1</td>
<td>0</td>
<td>7</td>
<td>MTRVEL_START_SEC_VAR_CLEARED_8</td>
</tr>
<tr class="odd">
<td>MtrVel_PrevMtrPosSampleTime2_uS_M_u32</td>
<td>1</td>
<td>0</td>
<td>4294965495</td>
<td>MTRVEL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>MtrVel_MtrVelMRF_MtrRadpS_M_f32</td>
<td>Single Precision Floating Point</td>
<td>-1350</td>
<td>1350</td>
<td>MTRVEL_START_SEC_VAR_CLEARED_32</td>
</tr>
</tbody>
</table>

\* Note: These ranges are based on the range of the normalized sine and
cosine global inputs, which in turn are based on the maximum amount of
signal variation that can be caused by temperature changes on the MSB
signals.

### User defined typedef definition/declaration 

This section documents any user types uniquely used for the module.

<table>
<colgroup>
<col style="width: 34%" />
<col style="width: 31%" />
<col style="width: 11%" />
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
<td><p>(Name given for the user defined typdef of type struct/union)</p>
<p>(Variable name qualified similar to all other variables)</p></td>
<td>(Variable name qualified similar to all other variables)</td>
<td>as other variables</td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

# Constant Data Dictionary

## Calibration Constants

This section lists the calibrations used by the module. For details on
calibration constants, refer to the Data Dictionary for the application.

|                                  |
|----------------------------------|
| Constant Name                    |
| t_MtrVelBlendTblX_MtrRadpS_u12p4 |
| k_GearRatio_Uls_f32              |
| k_MtrVelCorrLim_Cnt_Str          |
| k_HwVelCorrLim_Cnt_Str           |
| k_MtrVelCorrLim_MtrRadpS_f32     |
| k_HwVelCorrLim_HwRadpS_f32       |

## Program(fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

|                                  |                                 |           |
|--------------------------------|---------------|--------------------------|
| Constant Name                    | Resolution                      | Value     |
| D_USECPERSEC_ULS_F32             | Single Precision Floating Point | 1000000.0 |
| D_MTRVELOSBUFNUM_CNT_U08         | 1                               | 4         |
| D_SNAPSHOTBUF_CNT_U08            | 1                               | 2         |
| D_MTRVELLOLMT_MTRRADPS_F32       | Single Precision Floating Point | -1350     |
| D_MTRVELHILMT_MTRRADPS_F32       | Single Precision Floating Point | 1350      |
| T_MtrVelBlendTblY_Uls_u2p14\[2\] | Single Precision Floating Point | {0.1}     |
| D_MAXHANDWHEELVEL_HWRADPS_F32    | Single Precision Floating Point | 42        |
| D_MINHANDWHEELVEL_HWRADPS_F32    | Single Precision Floating Point | -42       |

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

|                                             |
|---------------------------------------------|
| Constant Name                               |
| D_RADPERREV_ULS_F32                         |
| D_ZERO_CNT_U8                               |
| D_MTRVELOSBUFSZ_CNT_U08 (from MtrVel_Cfg.h) |

### Module specific Lookup Tables Constants

(This is for lookup tables (arrays) with fixed values, same name as
other tables)

|                             |            |        |                  |
|-----------------------------|------------|--------|------------------|
| Constant Name               | Resolution | Value  | Software Segment |
| T_MtrVelBlendTblY_Uls_u2p14 | 2\^-14     | {0, 1} |                  |

# Functions/Macros used by the Sub-Modules 

## Library Functions / Macros 

The library functions / Macros that are called by the various sub
modules are identified below,

1.  FPM_FixedToFloat_m()

2.  FPM_FloatToFixed_m()

3.  FMP_Fix_m()

4.  Max_m()

5.  Abs_s16_m()

6.  Abs_f32_m()

7.  IntplVarXY_u16_u16Xu16Y_Cnt()

8.  LPF_SvUpdate_s16InFixKTrunc_m()

9.  LPF_OpUpdate_s16InFixKTrunc_m()

10. Rte_Call_NxtrDiagMgr_GetNTCFailed

11. Rte_Call_NxtrDiagMgr_SetNTCStatus

12. TableSize_m()

## Data Hiding Functions

The data hiding functions / macros used in this module are identified
below,

## Local Functions/Macros Used by this MDD only

(Note if they are defined in another source file, then reference the
appropriate header file)

The local functions/macros in this module are identified below,

1.  CalcCoarseVel()

2.  MtrVelBlend()

3.  RegressionFit()

# Software Module Implementation

## Initialization Functions

### Init: MtrVel_Init1

#### Design Rationale

None

#### Module Outputs

None

#### Module Internal 

None

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrVel_Digi/doc/mediax/media/image2.wmf)

## Periodic Functions

### Per: MtrVel_Per1

#### Design Rationale

#### Program Flow Start

Rte_Call_MtrVel_Per1_CP0_CheckpointReached()

#### Store Module Inputs to Local copies

AsstAssemPol_Cnt_T_s8 =
Rte_IRead_MtrVel_Per1_AsstAssemblyPolarity_Cnt_s08()

MtrPos_SampleTime2_uS_T_u32=
Rte_IRead_MtrVel_Per1_MechMtrPos2Timestamp_USec_u32()

MtrPos_MechMtrPos2_Rev_T_u0p16 =
Rte_IRead_MtrVel_Per1_MechMtrPos2_Rev_u0p16()

#### Calculate Raw Motor Velocity

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrVel_Digi/doc/mediax/media/image3.wmf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrVel_Digi/doc/mediax/media/image4.wmf)

#### Store Local copy of outputs into Module Outputs

(void)Rte_IWrite_MtrVel_Per1_SysCMotorVelMRF_MtrRadpS_f32(MtrVel_MtrVelMRF_MtrRadpS_M_f32)

(void)Rte_IWrite_MtrVel_Per1_SysCHandwheelVel_HwRadpS_f32(MtrVel_HwVel_HwRadpS_M_f32);

(void)Rte_IWrite_MtrVel_Per1_MotorVelCRF_MtrRadpS_f32(MtrVelCRF_MtrRadpS_T_f32)

(void)Rte_IWrite_MtrVel_Per1_MotorVelMRF_MtrRadpS_f32(MtrVel_MtrVelMRF_MtrRadpS_M_f32)

#### (void)Rte_IWrite_MtrVel_Per1_HandwheelVel_HwRadpS_f32(MtrVel_HwVel_HwRadpS_M_f32) [voidrte_iwrite_mtrvel_per1_handwheelvel_hwradps_f32mtrvel_hwvel_hwradps_m_f32]

#### Program Flow End

Rte_Call_MtrVel_Per1_CP1_CheckpointReached()

## Periodic Functions

### Per: MtrVel_Per2

#### Design Rationale

#### Program Flow Start

Rte_Call_MtrVel_Per2_CP0_CheckpointReached()

#### Store Module Inputs to Local copies

SysCDiagMtrVelMRF_MtrRadpS_T_f32 =
Rte_IRead_MtrVel_Per2_SysCDiagMtrVelMRF_MtrRadpS_f32()

SysCDiagHandWheelVel_HwRadpS_T_f32 =
Rte_IRead_MtrVel_Per2_SysCDiagHwVel_HwRadpS_f32()

(void)Rte_Call_NxtrDiagMgr_GetNTCFailed(NTC_Num_PriMSB_SinCosCorr,&MtrPosFault1_Cnt_T_lgc)

(void)Rte_Call_NxtrDiagMgr_GetNTCFailed(NTC_Num_PriVsSec_SinCosCorr,
&MtrPosFault2_Cnt_T_lgc)

#### Calculate Raw Motor Velocity ![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrVel_Digi/doc/mediax/media/image5.wmf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrVel_Digi/doc/mediax/media/image6.wmf)

#### Program Flow End

Rte_Call_MtrVel_Per2_CP1_CheckpointReached()

## Fault Recovery Functions

None

## Shutdown Functions

None

## Interrupt Functions

None

## Serial Communication Functions

None

## Local Function/Macro Definitions

If these are numerous and defined in a separate source file then
reference the source file only.

### Calculation Coarse Velocity

|                      |                       |                                 |        |       |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | CalcCoarseVel         | Type                            | Min    | Max   |
| **Arguments Passed** | DeltaPos_Rad_T_f32    | Single Precision Floating Point | -2\*pi | 2\*pi |
|                      | DeltaTime_uS_T_f32    | Single Precision Floating Point | 1800   | 2200  |
| **Return Value**     | MtrVel_MtrRadpS_T_f32 | Single Precision Floating Point | -1350  | 1350  |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrVel_Digi/doc/mediax/media/image7.wmf)

### Motor Velocity Blend

|                      |                          |                                 |       |      |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | MtrVelBlend              | Type                            | Min   | Max  |
| **Arguments Passed** | FinMtrVel_MtrRadpS_T_f32 | Single Precision Floating Point | -1350 | 1350 |
|                      | CrsMtrVel_MtrRadpS_T_f32 | Single Precision Floating Point | -1350 | 1350 |
| **Return Value**     | MtrVel_MtrRadpS_T_f32    | Single Precision Floating Point | -1350 | 1350 |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrVel_Digi/doc/mediax/media/image8.wmf)

### Regression Fit

|                      |                       |         |       |      |
|----------------------|-----------------------|---------|-------|------|
| **Function Name**    | Regression Fit        | Type    | Min   | Max  |
| **Arguments Passed** |                       |         |       |      |
|                      |                       |         |       |      |
|                      |                       |         |       |      |
|                      |                       |         |       |      |
| **Return**           | MtrVel_MtrRadpS_T_f32 | Float32 | -1350 | 1350 |

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrVel_Digi/doc/mediax/media/image9.wmf)

# ![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrVel_Digi/doc/mediax/media/image10.wmf)  [section]

# Execution Requirements

## Execution Sequence of the Module

(Describe in words relevant details about the execution sequence of the
different sub modules.)

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

|               |                   |                                                 |
|---------------------------|----------------|-----------------------------|
| Function Name | Calling Frequency | System State(s) in which the function is called |
| MtrVel_Init1  | Once              | ALL STATES                                      |
| MtrVel_Per1   | 2ms               | ALL STATES                                      |
| MtrVel_Per2   | 2ms               | ALL STATES                                      |

## Execution Requirements for Serial Communication Functions 

|               |                                                  |
|---------------|--------------------------------------------------|
| Function Name | Sub-Module called by (Serial Comm Function Name) |
| N/A           |                                                  |

#   [section-1]

# Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

|                    |                         |
|--------------------|-------------------------|
| Name of Sub Module | Software Segment        |
| MtrVel_Per1        | RTE_SA_MTRVEL_APPL_CODE |
| MtrVel_Per2        | RTE_SA_MTRVEL_APPL_CODE |

## Local Functions

This table identifies the software segments for local functions
identified in this module.

|                    |                  |
|--------------------|------------------|
| Name of Sub Module | Software Segment |
| CalcCoarseVel      | AP_MTRVEL_CODE   |
| MtrVelBlend        | AP_MTRVEL_CODE   |
| RegressionFit      | AP_MTRVEL_CODE   |

#   [section-2]

# Known Issues / Limitations With Design

1.  In this design, MtrVel3_TimeBuffer_uS_M_u16p0\[\]\[\] represents a
    set of independent circular buffers. Each buffer contains a set of
    continuous timestamps with the most recent timestamp index of each
    sample set stored in the associated index of
    MtrVel3_OsBufPos_Cnt_M_u08\[\] . The design requires monotonically
    increasing timestamps relative to the starting index value in
    MtrVel3_OsBufPos_Cnt_M_u08\[\]. Due to the modulo 65536 behavior of
    the timestamp, a single timestamp rollover within the active sample
    set pair is correctly handled by the design. Simultaneous sample
    points (e.g. ∆t = 0 for consecutive timestamps) are invalid and will
    result in a divide by zero in the current design. Unit Test vectors
    for functions which have MtrVel3_TimeBuffer_uS_M_u16p0\[4\]\[8\] as
    an input (MtrVel_Per1 and RegressionFit) must provide an input
    vector value set which conforms to the set of rules in the following
    table:

<table>
<colgroup>
<col style="width: 34%" />
<col style="width: 10%" />
<col style="width: 10%" />
<col style="width: 44%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Parameter</td>
<td>Min</td>
<td>Max</td>
<td>Notes</td>
</tr>
<tr class="even">
<td><p>Buffer consecutive timestamp value ∆</p>
<p>i.e. MtrVel3_TimeBuffer_uS_M_u16p0 [i][k] -
MtrVel3_TimeBuffer_uS_M_u16p0 [i][k+1]</p></td>
<td>10 uS</td>
<td>125 uS</td>
<td><p>Monotonically increasing in a modulo 65536 fashion (e.g. testing
of the 16 bit rollover point allows for a single rollover point within
the data buffer that is not monotonically increasing).</p>
<p>The UTP MUST provide at least 1 test vector that provides a data set
with a time stamp rollover (See Table 2).</p>
<p>10 uS is the worst case minimum sampling period based on the MtrCtrl
ISR runtime.</p>
<p>125uS is twice the nominal execution rate for MtrCtrl ISR. This is to
account for a worst case delay scenario.</p></td>
</tr>
<tr class="odd">
<td><p>Cross buffer set timestamp pair ∆</p>
<p>(e.g the ∆ between the oldest samples in each buffer, the ∆ between
the second oldest oldest samples in each buffer, etc)</p>
<p>i.e. MtrVel3_TimeBuffer_uS_M_u16p0 [MtrVel_OsBufSelect_M_u08][i] -
MtrVel3_TimeBuffer_uS_M_u16p0 [MtrVel_OldPosBuf_M_u08][k]</p>
<p>where k = i + (MtrVel3_OsBufPos_Cnt_M_u08[MtrVel_OldPosBuf_M_u08] -
MtrVel3_OsBufPos_Cnt_M_u08[MtrVel_OsBufSelect_M_u08]) modulo 8</p></td>
<td>250 uS</td>
<td>4000 uS</td>
<td><p>250 uS is the minimum required time to guarantee 8 samples at a
nominal 62.5 uS sample rate have been completed.</p>
<p>4000 uS is twice the execution rate for MtrVel_Per1. This is to
account for a worst case delay scenario.</p>
<p>When computing the delta it is necessary to perform modulo 65536 math
compensation to account for rollover situations (e.g. Table 2 [z-7]
samples depict a rollover case where the natural delta is 1764 – 65300 =
-63536, however this is not the correct delta result for the strictly
increasing modulo 65536 accumulator. Since the natural result is
negative, 65536 must be added to obtain the actual delta, -63536 + 65536
= 2000.</p>
<p>See Table 2 for a complete example conforming to this rule.</p></td>
</tr>
</tbody>
</table>

Table 1: Time Buffer UTP Constraints

The following \*.bas is a VBA function to validate the timestamp data
sets.

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrVel_Digi/doc/mediax/media/image11.wmf)

**<u>EXAMPLE TimeStamp Buffer Data Set:</u>**

The following buffer timestamp data set provides an example when buffers
0 and 1 are active. Values for buffers 2 and 3 are don’t care values for
this example and shown as “X” or “Don’t Care”. The samples within the
buffers have subscripts which describe the samples order relative to the
newest sample in the buffer (e.g. z-1 indicates that the sample is 1
sample period old, z-2 indicates the sample is 2 sample periods old,
etc). Samples of the same relative order within each buffer have the
same cell shading applied to aid the reader in locating cross buffer
sample pairs.

MtrVel_OldPosBuf_M_u08 = 0

MtrVel_OsBufSelect_M_u08 = 1

MtrVel3_OsBufPos_Cnt_M_u08\[0\] = 0

MtrVel3_OsBufPos_Cnt_M_u08\[1\] = 2

MtrVel3_OsBufPos_Cnt_M_u08\[2\] = Don’t Care

MtrVel3_OsBufPos_Cnt_M_u08\[3\] = Don’t Care

|       |           |            |            |            |            |           |           |           |
|-------|---------|---------|---------|---------|---------|---------|---------|---------|
| Index | 0         | 1          | 2          | 3          | 4          | 5         | 6         | 7         |
| 0     | 198       | 65300~z-7~ | 65362~z-6~ | 65424~z-5~ | 65486~z-4~ | 12~z-3~   | 74~z-2~   | 136~z-1~  |
| 1     | 2074~z-2~ | 2136~z-1~  | 2198       | 1764~z-7~  | 1826~z-6~  | 1888~z-5~ | 1950~z-4~ | 2012~z-3~ |
| 2     | X         | X          | X          | X          | X          | X         | X         | X         |
| 3     | X         | X          | X          | X          | X          | X         | X         | X         |

Table 2: Example UTP TimeBuffer Roll-Over Sample Set

1.  The state variables MtrVel_OldPosBuf_M_u08 and
    MtrVel_OsBufSelect_Cnt_M_u08 have a relationship that is maintained
    by logic that is executed after their use in RegressionFit(). The
    RegressionFit() function design requires a valid set of state
    variables to function properly. Therefore, it is possible to provide
    an illegal value set for the related state variables in a unit
    testing environment that will cause an illegal execution of
    RegressionFit(). All unit test vectors must ensure that
    MtrVel_OldPosBuf_M_u08 ≠ MtrVel_OsBufSelect_Cnt_M_u08. Failure to do
    so will result in a divide by 0 exception.

2.  “D_MTRVELOSBUFSZ_CNT_U08” is defined as Cal “k_BufferSize” in
    SF40AB. Since the size of the array is based on the Calibration, the
    calibration is changed to configurable constant.

> This allow s integrater to modify the constant before compilation.
> This saves memory wastage.

# Revision Control Log

|             |            |                                                                                                        |            |                     |
|------|------|--------------------------------------------|---------|---------|
| **Item \#** | **Rev \#** | **Change Description**                                                                                 | **Date**   | **Author Initials** |
| 1           | 1.0        | Initial AutoSAR release.                                                                               | 3-Jun-13   | Selva               |
| 2           | 2.0        | Updated the input and the output through RTE ports                                                     | 30-July-13 | Selva               |
| 3           | 3.0        | Updated the Ports names to match the FDD                                                               | 22-Aug-13  | Selva               |
| 4           | 4.0        | Updated the Buffer Index in Regression fit A-5803                                                      | 06-Oct-13  | Selva               |
| 5           | 5.0        | Update Motor Velocity for A7136, A7138, A7385 (Section 6.2.4 , section 6.8.3 flow chart)               | 12-Dec-14  | Selva               |
| 6           | 6.0        | Updated sections 3.1 ,4.2.1.1,6.2.1.4,6.3.1.4,6.8.1.4,6.8.2.1,6.8.3.3 according to Unit Test findings. | 24-Dec-14  | KPIT_SK             |

{% endraw %}