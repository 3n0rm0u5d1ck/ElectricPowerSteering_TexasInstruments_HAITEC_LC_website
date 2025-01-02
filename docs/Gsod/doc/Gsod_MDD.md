---
layout: default
title: Gsod_MDD
nav_order: 2
parent: Component
---
{% raw %}
# Module --  [module---]

# High-Level Description

Key system inputs including handwheel torque, motor position, motor and
handwheel velocity are widely distributed and used by command path and
other safety critical system functions. The safety strategy for these
“global” input signals is a dual channel diverse calculation with cross
check to detect a systematic design fault that would propagate to the
receiving functions. However, since the dual channel diversity does not
continue along the command path out to the motor command output, this
strategy cannot fully cover a potential systematic overwrite of the
global signals after the cross checks are performed and downstream
functions are then executed and use the primary path global signals.
Therefore, an additional safety function has been defined to check for
software over-write by co-existing software within the software memory
partition where the primary global signals are calculated.

Each of the functions that generate a global input signal has been
defined to store a copy of the output. The purpose of this function is
to perform a comparison check of the primary signal (that was
subsequently used by various system functions) and it’s redundantly
stored copy. Any detected miscompare will generate an overwrite fault
flag from this function to be evaluated by the diagnostics manager and
result in performing an F1 shutdown response.

**Design rationale note:**

This module uses direct input reads instead of buffered reads to disable
interrupts around data collection of the inputs to ensure that the data
set is consistent. The limitation of this method is that it is only
possible if inputs are being written from a task at the same or higher
priority with the same or faster loop execution time; which is the case
at the time of this implementation.

# Figures

## Component Diagram

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/Gsod/doc/mediax/media/image2.png"
style="width:3.02222in;height:3.99236in" />

#  Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

| Module Inputs                     | Module Outputs |     |
|-----------------------------------|----------------|-----|
| Corrected_MtrPos_Rev_f32          |                |     |
|                                   |                |     |
|                                   |                |     |
| Ana_Hw_Torque_HwNm_f32            |                |     |
| Vecu_Volt_f32                     |                |     |
| Torque_Cmd_CRF_MtrNm_f32          |                |     |
| Torque_Cmd_MRF_MtrNm_f32          |                |     |
| Cum_Mtr_Pos_CRF_Deg_f32           |                |     |
|                                   |                |     |
| MtrElecMech_Polarity_Cnt_s08      |                |     |
| SysC_Corrected_MtrPos_Rev_f32     |                |     |
|                                   |                |     |
|                                   |                |     |
| SysC_Ana_Hw_Torque_HwNm_f32       |                |     |
| SysC_Vecu_Volt_f32                |                |     |
| SysC_Torque_Cmd_CRF_MtrNm_f32     |                |     |
| SysC_Torque_Cmd_MRF_MtrNm_f32     |                |     |
| SysC_Cum_Mtr_Pos_CRF_Deg_f32      |                |     |
|                                   |                |     |
| SysC_MtrElecMech_Polarity_Cnt_s32 |                |     |

## Module Internal Variables

This section identifies the name, range and resolutions for module
specific data created by this module. If there are no range restrictions
on the variable, the term “FULL” is placed into the table for legal
range.

<table>
<colgroup>
<col style="width: 35%" />
<col style="width: 11%" />
<col style="width: 9%" />
<col style="width: 8%" />
<col style="width: 36%" />
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
<td>MtrPos_OverwriteFlt_Cnt_D_lgc</td>
<td>Boolean</td>
<td>FALSE</td>
<td>TRUE</td>
<td>GSOD_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>TorqCmd_CRF_OverwriteFlt_Cnt_D_lgc</td>
<td>Boolean</td>
<td>FALSE</td>
<td>TRUE</td>
<td>GSOD_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>HwTorque_OverwriteFlt_Cnt_D_lgc</td>
<td>Boolean</td>
<td>FALSE</td>
<td>TRUE</td>
<td>GSOD_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="even">
<td>TorqCmd_MRF_OverwriteFlt_Cnt_D_lgc</td>
<td>Boolean</td>
<td>FALSE</td>
<td>TRUE</td>
<td>GSOD_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>Vecu_OverwriteFlt_Cnt_D_lgc</td>
<td>Boolean</td>
<td>FALSE</td>
<td>TRUE</td>
<td>GSOD_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="odd">
<td>CumMtrPos_CRF_OverwriteFlt_Cnt_D_lgc</td>
<td>Boolean</td>
<td>FALSE</td>
<td>TRUE</td>
<td>GSOD_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="even">
<td>MtrElecMech_Polarity_OverwriteFlt_Cnt_D_lgc</td>
<td>Boolean</td>
<td>FALSE</td>
<td>TRUE</td>
<td>GSOD_START_SEC_VAR_CLEARED_BOOLEAN</td>
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
<td>&lt;none&gt;</td>
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
</tbody>
</table>

# Constant Data Dictionary

## Calibration Constants

This section lists the calibrations used by the module. For details on
calibration constants, refer to the Data Dictionary for the application.

| Constant Name |
|---------------|
| \<None\>      |
|               |

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

| Constant Name   |
|-----------------|
| D_TRUE_CNT_LGC  |
| D_FALSE_CNT_LGC |

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

None

## Data Hiding Functions

None

## Global Functions/Macros Defined by this Module

None

## Local Functions/Macros Used by this MDD only

None

# Software Module Implementation

## Runtime Environment (RTE) Initial Values

This section lists the initial values of data written by this module but
controlled by the RTE. After RTE initialization, the data in this table
will contain these values.

| Data     | Value |
|----------|-------|
| \<None\> |       |

## Initialization Functions

## None Periodic Functions [none-periodic-functions]

### Per: Gsod_Per1

#### Design Rationale

This module uses direct input reads instead of buffered reads to disable
interrupts around data collection of the inputs to ensure that the data
set is consistent. The limitation of this method is that it is only
possible if inputs are being written from a task at the same or higher
priority with the same or faster loop execution time; which is the case
at the time of this implementation.

#### Program Flow Start

Rte_Call_Gsod_Per1_CP0_CheckpointReached()

#### Store Module Inputs to Local copies

SuspendAllInterrupts()

Rte_Read_Corrected_MtrPos_Rev_f32(&Corrected_MtrPos_Rev_T_f32)

Rte_Read_SysC_Corrected_MtrPos_Rev_f32(&SysC_Corrected_MtrPos_Rev_T_f32)

Rte_Read_Ana_Hw_Torque_HwNm_f32(&Ana_Hw_Torque_HwNm_T_f32)

Rte_Read_SysC_Ana_Hw_Torque_HwNm_f32(&SysC_Ana_Hw_Torque_HwNm_T_f32)

Rte_Read_Vecu_Volt_f32(&Vecu_Volt_T_f32)

Rte_Read_SysC_Vecu_Volt_f32(&SysC_Vecu_Volt_T_f32)

Rte_Read_Torque_Cmd_CRF_MtrNm_f32(&Torque_Cmd_CRF_MtrNm_T_f32)

Rte_Read_SysC_Torque_Cmd_CRF_MtrNm_f32(&SysC_Torque_Cmd_CRF_MtrNm_T_f32)

Rte_Read_Torque_Cmd_MRF_MtrNm_f32(&Torque_Cmd_MRF_MtrNm_T_f32)

Rte_Read_SysC_Torque_Cmd_MRF_MtrNm_f32(&SysC_Torque_Cmd_MRF_MtrNm_T_f32)

Rte_Read_Cum_Mtr_Pos_CRF_Deg_f32(&Cum_Mtr_Pos_CRF_Deg_T_f32)

Rte_Read_SysC_Cum_Mtr_Pos_CRF_Deg_f32(&SysC_Cum_Mtr_Pos_CRF_Deg_T_f32)

Rte_Read_MtrElecMech_Polarity_Cnt_s08(&MtrElecMech_Polarity_Cnt_T_s08)

Rte_Read_SysC_MtrElecMech_Polarity_Cnt_s32(&SysC_MtrElecMech_Polarity_Cnt_T_s32)

ResumeAllInterrupts()

#### Processing

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/Gsod/doc/mediax/media/image5.emf)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

Rte_Call_Gsod_Per1_CP1_CheckpointReached()

##  Fault Recovery Functions

None

## Shutdown Functions

None

##  Interrupt Functions

None

##  Serial Communication Functions

None

##  

# Execution Requirements

## Execution Sequence of the Module

Gsod_per1 must execute at the **end** of the 2ms loop after all other
modules using global inputs are called. This is to verify the integrity
of the global input signals after all cases that use them have
completed.

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

| Function Name | Calling Frequency | System State(s) in which the function is called |
|--------------------------|-----------------|------------------------------|
| Gsod_Per1     | 2 ms              | WARM INIT, OPERATE, DISABLE                     |

## Execution Requirements for Serial Communication Functions 

| Function Name | Sub-Module called by (Serial Comm Function Name) |
|---------------|--------------------------------------------------|
| \<None\>      |                                                  |

#  [section-2]

#  Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

| Name of Sub Module | Software Segment                |
|--------------------|---------------------------------|
| Gsod_Per1          | RTE_START_SEC_AP_GSOD_APPL_CODE |

##  [section-3]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

| Name of Sub Module | Software Segment |
|--------------------|------------------|
| None               |                  |

#  [section-4]

#  Known Issues / Limitations With Design

1.  None

#  Revision Control Log

| **Item \#** | **Rev \#** | **Change Description**                    | **Date**  | **Author Initials** |
|------|------|--------------------------------------------|---------|---------|
| 1           | 1          | Initial Component Creation                | 22-Oct-12 | JWJ                 |
| 2           | 2          | Corrected incompatible input signal units | 14-Nov-12 | JWJ                 |
| 3           | 3          | Removed typecasts from flowcharts         | 21-Mar-13 | LWW                 |
| 4           | 4          | Update per anomaly 5035 and FDD SF37 v002 | 21-May-13 | BDO                 |

{% endraw %}