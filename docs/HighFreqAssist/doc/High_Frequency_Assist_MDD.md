---
layout: default
title: High_Frequency_Assist_MDD
nav_order: 2
parent: High Frequency Assist
---
{% raw %}
# Module –  [module]

# High-Level Description

This module compensates for system inertia and road feedback. It puts
handwheel torque through a high-pass filter and multiplies it by a
tunable gain parameter to compensate for these factors.

# Figures

## Component Diagram

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/HighFreqAssist/doc/mediax/media/image1.png"
style="width:2.39444in;height:1.32083in" />

#  Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

| Module Inputs           | Module Outputs |                          |
|-------------------------|----------------|--------------------------|
| VehicleSpeed_Kph_f32    |                | HighFreqAssist_MtrNm_f32 |
| HwTorque_HwNm_f32       |                |                          |
| WIRCmdAmpBlnd_MtrNm_f32 |                |                          |

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
<col style="width: 13%" />
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
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td> HwTorqueHPFKSV_Cnt_M_str</td>
<td>Single Precision Float</td>
<td>-10</td>
<td>10</td>
<td>HYSTADD_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="odd">
<td>GainBlend_Uls_D_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td>1</td>
<td>HIGHFREQASSIST_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>GainWIRZero_MtrNmpHwNm_D_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td>10</td>
<td>HIGHFREQASSIST_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>GainVal_MtrNmpHwNm_D_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td>10</td>
<td>HIGHFREQASSIST_START_SEC_VAR_CLEARED_32</td>
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

| Constant Name                          |
|----------------------------------------|
|                                        |
|                                        |
|                                        |
|                                        |
|                                        |
|  t_LPFKnY_Hz_u7p9\[12\]                |
| t_CmnVehSpd_Kph_u9p7\[12\]             |
| t2_TorqX0_HwNm_u5p11\[12\]\[13\]       |
| t2_TorqX1_HwNm_u5p11\[12\]\[13\]       |
| t2_GainY0_MtrNmpHwNm_u3p13\[12\]\[13\] |
| t2_GainY1_MtrNmpHwNm_u3p13\[12\]\[13\] |
| t2_WIRBlendX_MtrNm_u4p12\[12\]\[5\]    |
| t2_WIRBlendY_Uls_u1p15\[12\]\[5\]      |

## Program(fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

| Constant Name | Resolution | Units | Value |
|---------------|------------|-------|-------|
| \<None\>      |            |       |       |
|               |            |       |       |

####  [section]

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

| Constant Name  |
|----------------|
| D_ZERO_ULS_F32 |
| D_2MS_SEC_F32  |

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

3.  Abs_s16_m

4.  IntplVarXY_u16_u16Xu16Y_Cnt

5.  BilinearXMYM_u16_u16XMu16YM_Cnt

6.  TableSize_m

7.  Blend_f32

8.  HPF_KUpdate_f32_m

9.  HPF_OpUpdate_f32_m

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

| Data                                   | Value |
|----------------------------------------|-------|
| Rte_InitValue_HighFreqAssist_MtrNm_f32 | 0     |
| Rte_InitValue_HwTorque_HwNm_f32        | 0     |
| Rte_InitValue_VehicleSpeed_Kph_f32     | 0     |
| Rte_InitValue_WIRCmdAmpBlnd_MtrNm_f32  | 0     |

## Initialization Functions

None

##  Periodic Functions

### Per: \_Per1

#### Design Rationale

None

#### Program Flow Start

Rte_Call_HighFreqAssist_Per1_CP0_CheckpointReached()

#### Store Module Inputs to Local copies

HwTorque_HwNm_T_f32 = Rte_IRead_HighFreqAssist_Per1_HwTorque_HwNm_f32()

VehicleSpeed_Kph_T_f32 =
Rte_IRead_HighFreqAssist_Per1_VehicleSpeed_Kph_f32()

WIRCmdAmpBlnd_MtrNm_T_f32 =
Rte_IRead_HighFreqAssist_Per1_WIRCmdAmpBlnd_MtrNm_f32()

HwTorque_HwNm_T_s4p11 = FPM_FloatToFixed_m(HwTorque_HwNm_T_f32, s4p11_T)

AbsHwTorque_HwNm_T_u5p11 = Abs_s16_m(HwTorque_HwNm_T_s4p11)

VehicleSpeed_Kph_T_u9p7 = FPM_FloatToFixed_m(VehicleSpeed_Kph_T_f32,
u9p7_T)

WIRCmdAmpBlnd_MtrNm_T_u4p12 =
FPM_FloatToFixed_m(WIRCmdAmpBlnd_MtrNm_T_f32, u4p12_T)

#### Determine Filter Frequency

#### Determine Gain

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/HighFreqAssist/doc/mediax/media/image5.emf)

#### Filter and Output

#### Store Local copy of outputs into Module Outputs

GainBlend_Uls_D_f32 = GainBlend_Uls_T_f32

GainWIRZero_MtrNmpHwNm_D_f32 = GainWIRZero_MtrNmpHwNm_T_f32

GainVal_MtrNmpHwNm_D_f32 = GainVal_MtrNmpHwNm_T_f32

Rte_IWrite_HighFreqAssist_Per1_HighFreqAssist_MtrNm_f32(HighFreqAssist_MtrNm_T_f32);

#### Program Flow End

Rte_Call_HighFreqAssist_Per1_CP1_CheckpointReached()

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

## Execution Sequence of the Module

The periodic function is called at a rate of 2ms in all states.

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

| Function Name       | Calling Frequency | System State(s) in which the function is called |
|--------------------------|-----------------|------------------------------|
| HighFreqAssist_Per1 | 2 ms              | ALL                                             |

## Execution Requirements for Serial Communication Functions 

| Function Name | Sub-Module called by (Serial Comm Function Name) |
|---------------|--------------------------------------------------|
| \<None\>      |                                                  |

#  [section-2]

#  Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

| Name of Sub Module  | Software Segment                          |
|---------------------|-------------------------------------------|
| HighFreqAssist_Per1 | RTE_START_SEC_AP_HIGHFREQASSIST_APPL_CODE |

##  [section-3]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

| Name of Sub Module | Software Segment |
|--------------------|------------------|
| None               |                  |

#  [section-4]

#  Known Issues / Limitations With Design

1.  INLINE functions in GlobalMacro.h are not unit tested

#  Revision Control Log

| **Item \#** | **Rev \#** | **Change Description**                          | **Date**  | **Author Initials** |
|------|------|--------------------------------------------|---------|--------|
| 1           | 1.0        | Initial Version                                 | 05-Apr-12 | OT                  |
| 2           | 2.0        | Check points added for the runnable executables | 21-Sep-12 | SSK                 |
| 3           | 3.0        | Updated to FDD ver 002                          | 2-May-13  | Jared               |

{% endraw %}