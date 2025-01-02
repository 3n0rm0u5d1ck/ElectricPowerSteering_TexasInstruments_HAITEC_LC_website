---
layout: default
title: Tuning_Select_Authority_MDD
nav_order: 2
parent: Tuning Select Authority
---
{% raw %}
# Module – Tuning Select Authority [module-tuning-select-authority]

# High-Level Description

This function broadcasts an authority to allow switching between
calibration subsets while driving. It compares handwheel torque and
vehicle speed to calibratable thresholds and outputs either a zero or a
one.

# Figures

## Component Diagram

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/TuningSelAuth/doc/mediax/media/image1.jpeg"
style="width:2.77895in;height:2.29172in" alt="TunSelAuth.jpg" />

#  Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

| Module Inputs               | Module Outputs |                       |
|-----------------------------|----------------|-----------------------|
| HwTorque_HwNm_f32           |                | ActiveTunPers_Cnt_u16 |
| VehicleSpeed_Kph_f32        |                | ActiveTunSet_Cnt_u16  |
| DesiredTunPers_Cnt_u16      |                | TunPer_Ptr_Str \*     |
| DesiredTunSet_Cnt_u16       |                | TunSet_Ptr_Str \*     |
| ActiveTunOvrPtrAddr_Cnt_u32 |                |                       |
| TuningSessionActPtr_Cnt_u8  |                |                       |

*\* Note: For unit testing purposes these inputs are defined as pointers
to uint16 (as opposed to pointers to tuning structures) for simplicity.*

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
<td>*HwTrqLPFiltSV_HwNm_M_str</td>
<td>Multiple</td>
<td>Multiple</td>
<td>Multiple</td>
<td>TUNINGSELAUTH_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="even">
<td><ul>
<li><p>K_Uls_f32</p></li>
</ul></td>
<td>Single Precision Float</td>
<td>0.0124877435</td>
<td>0.4665119090</td>
<td></td>
</tr>
<tr class="odd">
<td><ul>
<li><p>SV_HwNm_f32</p></li>
</ul></td>
<td>Single Precision Float</td>
<td>-10</td>
<td>10</td>
<td></td>
</tr>
<tr class="even">
<td>PrevTunSet_Cnt_M_u16</td>
<td>1</td>
<td>0</td>
<td>100</td>
<td>TUNINGSELAUTH_START_SEC_VAR_CLEARED _16</td>
</tr>
<tr class="odd">
<td>PrevTunPers_Cnt_M_u16</td>
<td>1</td>
<td>0</td>
<td>100</td>
<td>TUNINGSELAUTH_START_SEC_VAR_CLEARED _16</td>
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

| Constant Name                |
|------------------------------|
| k_TunSelHwTrqThresh_HwNm_f32 |
| k_TunSelVehSpdThresh_Kph_f32 |
| k_TunSelHwTrqLPFKn_Hz_f32    |

## Program(fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

| Constant Name  | Resolution             | Units | Value |
|----------------|------------------------|-------|-------|
| D_10MS_SEC_F32 | Single Precision Float | Sec   | 0.010 |

####  [section]

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

| Constant Name                            |
|------------------------------------------|
| D_TRUE_CNT_LGC                           |
| D_FALSE_CNT_LGC                          |
| T_TunSetSelectionTbl_Ptr_Str\[\] \*      |
| T_TunPersSelectionTbl_Ptr_Str\[\]\[\] \* |

*\* Note: For unit testing purposes, these arrays of pointers are of
size \[3\] and \[3\]\[5\] respectively and are defined as pointers to
uint16 (as opposed to pointers to tuning structures) for simplicity.*

### Module specific Lookup Tables Constants

| Constant Name | Resolution | Value | Software Segment |
|---------------|------------|-------|------------------|
| None          |            |       |                  |

#  Functions/Macros used by the Sub-Modules 

## Library Functions / Macros 

The library and functions / Macros that are called by the various sub
modules are identified below,

1.  Abs_f32_m

2.  LPF_OpUpdate_f32_m

3.  LPF_KUpdate_f32_m

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

| Data                        | Value |
|-----------------------------|-------|
| HwTorque_HwNm_f32           | 0     |
| VehicleSpeed_Kph_f32        | 0     |
| DesiredTunPers_Cnt_u16      | 0     |
| DesiredTunSet_Cnt_u16       | 0     |
| ActiveTunPers_Cnt_u16       | 0     |
| ActiveTunSet_Cnt_u16        | 0     |
| ActiveTunOvrPtrAddr_Cnt_u32 | 0     |
| TuningSessionActPtr_Cnt_u8  | 255   |

## Initialization Functions

### Init: TuningSelAuth_Init1

#### Design Rationale

LPF_KUpdate_f32 is used to initialize the LPF filter instead of the full
LPF_Init_f32 macro as an optimization since the required initial state
of the filter is 0, which is the initialized value of the RAM, so there
is no need to explicitly initialize the state variables in this init
function.

#### Initialize Low Pass Filters

#### ![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/TuningSelAuth/doc/mediax/media/image3.emf) [section-1]

### Periodic Functions

#### Per: TuningSelAuth_Per1

#### Design Rationale

#### Program Flow Start

#### Rte_Call_TuningSelAuth_Per1_CP0_CheckpointReached() Store Module Inputs to Local copies

See below section

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/TuningSelAuth/doc/mediax/media/image4.emf)

#### Store Local copy of outputs into Module Outputs

See above section

#### Program Flow End

Rte_Call_TuningSelAuth_Per1_CP1_CheckpointReached()

##  Fault Recovery Functions

None

## Shutdown Functions

None

## Interrupt Functions

None

## Serial Communication Function

None

## Transition Functions

None

##  

# Execution Requirements

## Execution Sequence of the Module

> If something besides the defaults of “0” for desired tuning set and
> desired personality are required at poweron, Init1 must run after the
> init function that provides these initial values.

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

| Function Name       | Calling Frequency | System State(s) in which the function is called |
|--------------------------|-----------------|------------------------------|
| TuningSelAuth_Init1 | Once at Startup   | COLDINIT                                        |
| TuningSelAuth_Per1  | 10 ms             | ALL                                             |

## Execution Requirements for Serial Communication Functions 

| Function Name | Sub-Module called by (Serial Comm Function Name) |
|---------------|--------------------------------------------------|
| None          |                                                  |

#  [section-3]

#  Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

| Name of Sub Module    | Software Segment                         |
|-----------------------|------------------------------------------|
| TuningSelAuth \_Init1 | RTE_START_SEC_AP_TUNINGSELAUTH_APPL_CODE |
| TuningSelAuth_Per1    | RTE_START_SEC_AP_TUNINGSELAUTH_APPL_CODE |

##  [section-4]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

| Name of Sub Module | Software Segment |
|--------------------|------------------|
|                    |                  |

#  [section-5]

#  Known Issues / Limitations With Design

1.  INLINE functions defined in “GlobalMacro.h” are not unit tested

2.  The FDD indicates that this module will store the EEPROM value for
    tuning set, however, this implementation doesn’t provide this block.
    Instead, it is assumed that some other module will contain the
    tuning selection block. This was done to enable programs that don’t
    have multiple tuning sets to just use the default “0” without having
    to manage an EEPROM block.

#  Revision Control Log

| **Item \#** | **Rev \#** | **Change Description**                                                        | **Date**  | **Author Initials** |
|------|------|-------------------------------------------|---------|---------|
| 1           | 1.0        | Initial MDD implementing FDD SF-23 v001                                       | 03Jul12   | VK                  |
| 1           | 2.0        | Updates to provide the switching of tuning sets and personalities             | 03/08/12  | LWW                 |
| 2           | 3.0        | Added checkpoints and memmap software segment is updated for static variables | 24-Sep-12 | Selva               |
| 3           | 4.0        | Updated trigger rate for Per1                                                 | 24-Oct-12 | BWL                 |
| 4           | 5.0        | Updated per1 for tune-on-the-fly phase 1 support.                             | 30-Jul-13 | KJS                 |

{% endraw %}