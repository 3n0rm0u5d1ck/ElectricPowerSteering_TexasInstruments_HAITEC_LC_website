---
layout: default
title: MotorVelocity2_MDD
nav_order: 4
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

### Diagram – MtrVel

This diagram describes the functional characteristics and data flow of a
given function.

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrVel_Digi/doc/mediax/media/image1.png"
style="width:4.69861in;height:2.63542in" />

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
| AsstAssemblyPolarity \_Cnt_s08       | SysCDiagMtrVelMRF_MtrRadpS_f32        |
| HandwheelVel_HwRadpS_f32             | SysCDiagHwVel_HwRadpS_f32             |
| MotorVelMRF_MtrRadpS_f32             |                                       |
| CumMechMtrPosMRF_Deg_f32             |                                       |
| MechMtrPos1Timestamp_USec_u32        |                                       |

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
<td>MtrVel2_SysCMtrVelMRF_MtrRadpS_M_f32</td>
<td>Single Precision Floating Point</td>
<td>-1350</td>
<td>1350</td>
<td>MTRVEL2_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>MtrVel2_SysCHwVelCRF_HwRadpS_M_f32</td>
<td>Single Precision Floating Point</td>
<td>-42</td>
<td>42</td>
<td>MTRVEL2_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>MtrVel2_SysCMtrVelDiffAcc_Cnt_M_u16</td>
<td>1</td>
<td>0</td>
<td>255</td>
<td>MTRVEL2_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="odd">
<td>MtrVel2_SysCHwVelDiffAcc_Cnt_M_u16</td>
<td>1</td>
<td>0</td>
<td>255</td>
<td>MTRVEL2_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td><strong>MtrVel2_PrevSysCDiagCumMtrPos_Rad_M_f32</strong></td>
<td>Single Precision Floating Point</td>
<td>-6.283185307164</td>
<td>6.283185307164</td>
<td>MTRVEL2_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>MtrVel2_SysCMtrVelCorrLimDiff_MtrRadpS_D_f32</td>
<td>Single Precision Floating Point</td>
<td>0</td>
<td>2700</td>
<td>MTRVEL2_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>MtrVel2_SysCHwVelCorrLimDiff_HwRadpS_D_f32</td>
<td>Single Precision Floating Point</td>
<td>0</td>
<td>2700</td>
<td>MTRVEL2_START_SEC_VAR_CLEARED_32</td>
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

|                              |
|------------------------------|
| Constant Name                |
| k_GearRatio_Uls_f32          |
| k_MtrVelCorrLim_Cnt_Str      |
| k_HwVelCorrLim_Cnt_Str       |
| k_MtrVelCorrLim_MtrRadpS_f32 |
| k_HwVelCorrLim_HwRadpS_f32   |

## Program(fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

|                               |                        |          |
|-------------------------------|------------------------|----------|
| Constant Name                 | Resolution             | Value    |
| D_MICROSECTOSEC_f32           | Single Precision float | 0.000001 |
| D_MAXHANDWHEELVEL_HWRADPS_F32 | Single Precision float | +42      |
| D_MINHANDWHEELVEL_HWRADPS_F32 | Single Precision float | -42      |

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

|                      |
|----------------------|
| Constant Name        |
| D_MSECPERSEC_ULS_F32 |
| D_RADPERREV_ULS_F32  |
|                      |

### Module specific Lookup Tables Constants

(This is for lookup tables (arrays) with fixed values, same name as
other tables)

|               |            |       |                  |
|---------------|------------|-------|------------------|
| Constant Name | Resolution | Value | Software Segment |
| None          |            |       |                  |

# Functions/Macros used by the Sub-Modules 

## Library Functions / Macros 

The library functions / Macros that are called by the various sub
modules are identified below,

1.  Abs_f32_m()

2.  LPF_OpUpdate_f32_m ()

3.  LPF_KUpdate_f32_m

## Data Hiding Functions

The data hiding functions / macros used in this module are identified
below,

## Local Functions/Macros Used by this MDD only

(Note if they are defined in another source file, then reference the
appropriate header file)

The local functions/macros in this module are identified below,

# Software Module Implementation

## Initialization Functions

### Init: MtrVel2_Init1

#### Design Rationale

None

#### Module Outputs

#### Module Internal 

None

#### Design 

####  CumMtrPosMRF_Deg_T_f32= Rte_IRead_MtrVel2_Init_CumMechMtrPosMRF_Deg_f32() [cummtrposmrf_deg_t_f32-rte_iread_mtrvel2_init_cummechmtrposmrf_deg_f32]

#### SysCDiagCumMtrPos_Rad_T_f32 = (CumMtrPosMRF_Deg_T_f32) \* D_PIOVR180_ULS_F32 [syscdiagcummtrpos_rad_t_f32-cummtrposmrf_deg_t_f32-d_piovr180_uls_f32]

#### MtrVel2_PrevSysCDiagCumMtrPos_Rad_M_f32= SysCDiagCumMtrPos_Rad_T_f32 [mtrvel2_prevsyscdiagcummtrpos_rad_m_f32-syscdiagcummtrpos_rad_t_f32]

## Periodic Functions

### Per: MtrVel2_Per1

#### Design Rationale

#### Program Flow Start

Rte_Call_MtrVel2_Per1_CP0_CheckpointReached()

#### Store Module Inputs to Local copies

AsstAssemPol_Cnt_T_s8 =
Rte_IRead_MtrVel2_Per1_AsstAssemblyPolarity_Cnt_s08();

MechMtrPosTimeStamp_uSec_T_u32 =
Rte_IRead_MtrVel2_Per1_MechMtrPos1Timestamp_USec_u32();

CumMtrPosMRF_Deg_T_f32 =
Rte_IRead_MtrVel2_Per1_CumMechMtrPosMRF_Deg_f32();

#### Calculate SysC Motor Velocity

#### Store Local copy of outputs into Module Outputs

Rte_IWrite_MtrVel2_Per1_SysCDiagHandwheelVel_HwRadpS_f32
(SysCHwVelCRF_HwRadpS_M_f32)

Rte_IWrite_MtrVel2_Per1_SysCDiagMtrVelMRF_MtrRadpS_f32(SysCMtrVelRawMRF_MtrRadpS_T_f32)

MtrVel2_SysCMtrVelMRF_MtrRadpS_M_f32 = SysCMtrVelRawMRF_MtrRadpS_T_f32

#### Program Flow End

Rte_Call_MtrVel2_Per1_CP1_CheckpointReached()

## Periodic Functions

### Per: MtrVel2_Per2

#### Design Rationale

#### Program Flow Start

N/A

#### Store Module Inputs to Local copies

Rte_Call_MtrVel2_Per2_CP0_CheckpointReached()

HandwheelVel_HwRadpS_T_f32 =
Rte_IRead_MtrVel2_Per2_HandwheelVel_HwRadpS_f32 ()

MRFMotorVel_MtrRadpS_T_f32 =
Rte_IRead_MtrVel2_Per2_MotorVelMRF_MtrRadpS_f32 ()

#### Calculate Raw Motor Velocity

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrVel_Digi/doc/mediax/media/image7.wmf)

#### Program Flow End

Rte_Call_MtrVel2_Per2_CP1_CheckpointReached()

## Fault Recovery Functions

None

## Shutdown Functions

None

## Interrupt Functions

None

## Serial Communication Functions

None

## Local Function/Macro Definitions

None

# Execution Requirements

## Execution Sequence of the Module

(Describe in words relevant details about the execution sequence of the
different sub modules.)

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

|               |                   |                                                 |
|---------------------------|----------------|-----------------------------|
| Function Name | Calling Frequency | System State(s) in which the function is called |
| MtrVel2_Init1 | Once              | ALL STATES                                      |
| MtrVel2_Per1  | 2ms               | ALL STATES                                      |
| MtrVel2_Per2  | 2ms               | ALL STATES                                      |

## Execution Requirements for Serial Communication Functions 

|               |                                                  |
|---------------|--------------------------------------------------|
| Function Name | Sub-Module called by (Serial Comm Function Name) |
| N/A           |                                                  |

#   [section]

# Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

|                    |                                    |
|--------------------|------------------------------------|
| Name of Sub Module | Software Segment                   |
| MtrVel2_Per1       | RTE_START_SEC_SA_MTRVEL2_APPL_CODE |
| MtrVel2_Per2       | RTE_START_SEC_SA_MTRVEL2_APPL_CODE |
|                    |                                    |

## Local Functions

none

#   [section-1]

# Known Issues / Limitations With Design

# Revision Control Log

|             |            |                                                                                          |            |                     |
|------|------|--------------------------------------------|---------|---------|
| **Item \#** | **Rev \#** | **Change Description**                                                                   | **Date**   | **Author Initials** |
| 1           | 1.0        | Initial AutoSAR release.                                                                 | 5- June-13 | Selva               |
| 2           | 2.0        | Update the Input and output ports of Motor Velocity                                      | 30-July-13 | Selva               |
| 3           | 3.0        | Updated Port interface name to match the FDD                                             | 22-Aug-13  | Selva               |
| 4           | 4.0        | A-5749 fixes ie replacing MtrVel with raw cal values                                     | 06-Oct-13  | Selva               |
| 5           | 5.0        | Update Motor Velocity for A7136, A7138, A7385 (Section 6.2.4 , section 6.8.3 flow chart) | 12-Dec-14  | Selva               |
| 6           | 6.0        | Updated as per Unit Test Findings                                                        | 29-Dec-14  | KPIT-AB             |

{% endraw %}