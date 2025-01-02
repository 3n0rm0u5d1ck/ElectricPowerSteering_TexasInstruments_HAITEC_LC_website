---
layout: default
title: TorqueCmdScaling_MDD
nav_order: 9
parent: Motor Control
---
{% raw %}
# Module -- Torque Command Scaling4.04.0 [module----torque-command-scaling4.04.0]

# High-Level Description

The Torque Command Scale module multiplies the Torque_Command_MRF input
signal by a calibration which is set during a manufacturing EOL
calibration process. This calibration is provided to reduce overall
system output torque variation. This scaled version of the torque
command is used by all other sub functions within motor control which
have a torque dependent component.

# Figures

## Diagram – Function Data Sharing

This diagram shows all data that is shared between functions within the
module.

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrCtrl_CM/doc/mediax/media/image1.png"
style="width:3.91597in;height:2.04167in" />

### Diagram – Function (Name)

This diagram describes the functional characteristics and data flow of a
given function.

(Note – This is not mandatory, only used where a graphical
representation helps explain the function. It is left to the author’s
discretion. New headers of this level (Level 3) should be created for
each function.

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
| MRFMtrTrqCmd_MtrNm_f32               | MRFMtrTrqCmdScl_MtrNm_f32             |

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
<td>None</td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

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

|                           |
|---------------------------|
| Constant Name             |
| k_MinTrqCmdScl_Uls_f32    |
| k_MaxTrqCmdScl_Uls_f32    |
| TorqueCmdSF_Uls_f32 (NVM) |

## Program(fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

|               |            |       |
|---------------|------------|-------|
| Constant Name | Resolution | Value |
| None          |            |       |

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

|               |
|---------------|
| Constant Name |
| None          |
|               |
|               |

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

1.  Limit_m()

## Data Hiding Functions

The data hiding functions / macros used in this module are identified
below,

1.  Rte_Call_TrqCmdScl_WriteBlock()

2.  Rte_Pim_TorqueCmdSF_Uls_f32()

## Local Functions/Macros Used by this MDD only

(Note if they are defined in another source file, then reference the
appropriate header file)

The local functions/macros in this module are identified below,

# Software Module Implementation

## Periodic Functions

### Per: TrqCmdScl_Per1

#### Design Rationale

None

#### Program Flow Start

Rte_Call_TrqCmdScl_Per1_CP0_CheckpointReached()

#### Store Module Inputs to Local copies

MRFMtrTrqCmd_MtrNm_T_f32 =
Rte_IRead_TrqCmdScl_Per1_MRFMtrTrqCmd_MtrNm_f32()

TorqueCmdSF_Uls_T_f32 = \*Rte_Pim_TorqueCmdSF_Uls_f32()

#### Apply Torque Command Scaling

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrCtrl_CM/doc/mediax/media/image2.wmf)

#### Store Local copy of outputs into Module Outputs

Rte_IWrite_TrqCmdScl_Per1_MRFMtrTrqCmdScl_MtrNm_f32(MRFMtrTrqCmdScl_MtrNm_T_f32)

#### Program Flow End

#### Rte_Call_TrqCmdScl_Per1_CP1_CheckpointReached() [rte_call_trqcmdscl_per1_cp1_checkpointreached]

#### Flow End

N/A

### Scomm: TrqCmdScl_SCom_Get

#### Design Rationale

None

#### Program Flow Start

#### N/A [na]

#### Store Module Inputs to Local copies

None

#### Get Torque Command Scaling

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrCtrl_CM/doc/mediax/media/image3.wmf)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

### N/A [na-1]

###  Scomm: TrqCmdScl_SCom_Set

#### Design Rationale

None

#### Program Flow Start

N/A

#### Store Module Inputs to Local copies

None

#### Set Torque Command Scaling

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrCtrl_CM/doc/mediax/media/image4.wmf)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

N/A

## Local Function/Macro Definitions

If these are numerous and defined in a separate source file then
reference the source file only.

### Function

|                      |     |      |     |     |          |
|----------------------|-----|------|-----|-----|----------|
| **Function Name**    |     | Type | Min | Max | UTP Tol. |
| **Arguments Passed** |     |      |     |     |          |
| **Return Value**     |     |      |     |     |          |

# Execution Requirements

## Execution Sequence of the Module

TrqCmdScl_Per1 must be executed in the forward path before quadrant
detection, the voltage command numerator, phase advance, voltage command
denominator, and Modulation Index.

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

|                |                   |                 |
|----------------|-------------------|-----------------|
| Function Name  | Calling Frequency | System State(s) |
| TrqCmdScl_Per1 | 2ms               | ALL             |

## Execution Requirements for Serial Communication Functions 

|                      |                                                  |
|----------------------|--------------------------------------------------|
| Function Name        | Sub-Module called by (Serial Comm Function Name) |
| TrqCmdScl_Scom_Get() |                                                  |
| TrqCmdScl_Scom_Set() |                                                  |

#   [section]

# Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

|                    |                  |
|--------------------|------------------|
| Name of Sub Module | Software Segment |
| TrqCmdScl_Per1     |                  |

## Local Functions

This table identifies the software segments for local functions
identified in this module.

|                    |                  |
|--------------------|------------------|
| Name of Sub Module | Software Segment |
| None               |                  |

#   [section-1]

# Known Issues / Limitations With Design

1.  None

# Revision Control Log

|             |            |                                                                               |          |                     |
|------|------|--------------------------------------------|---------|---------|
| **Item \#** | **Rev \#** | **Change Description**                                                        | **Date** | **Author Initials** |
| 1           | 1.0        | Document creation and initial release for the component                       | 29NOV11  | VK                  |
| 2           | 1.1        | Corrections to assign EOL scaling factor to temporary variable                | 02DEC11  | VK                  |
| 3           | 3          | Added checkpoints and memmap software segment is updated for static variables | 26Sep12  | Selva               |
| 4           | 4          | Heading and format corrected                                                  | 21Nov12  | Selva               |

{% endraw %}