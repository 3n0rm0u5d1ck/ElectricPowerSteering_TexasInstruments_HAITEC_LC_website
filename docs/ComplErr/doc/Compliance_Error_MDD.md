---
layout: default
title: Compliance_Error_MDD
nav_order: 2
parent: ComplErr
---
{% raw %}
# Module – Compliance Error [module-compliance-error]

# High-Level Description

This function calculates the compliance error that can be used to
compensate for stiffness in the torque path between the motor position
sensor and column axis.

# Figures

## Component Diagram

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ComplErr/doc/mediax/media/image1.png"
style="width:2.90972in;height:1.8125in" />

#  Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

| Module Inputs          | Module Outputs |                    |
|------------------------|----------------|--------------------|
| TorqueCmdCRF_MtrNm_f32 |                | ComplErr_HwDeg_f32 |
|                        |                |                    |

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
<td>-</td>
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
<td>-</td>
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

| Constant Name                                          |
|--------------------------------------------------------|
| t_CompErrMtrPosNonLinComplDepTbl_HwDegpMtrNm_u8p8\[6\] |
| t_ComplErrMtrPosNonLinComplIndTbl_MtrNm_u5p11\[6\]     |
|                                                        |
|                                                        |

## Program (fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

| Constant Name | Resolution | Units | Value |
|---------------|------------|-------|-------|
| \-            |            |       |       |

####  [section]

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

| Constant Name  |
|----------------|
| D_ZERO_ULS_F32 |

### Module specific Lookup Tables Constants

| Constant Name | Resolution | Value | Software Segment |
|---------------|------------|-------|------------------|
| None          |            |       |                  |

#  Functions/Macros used by the Sub-Modules 

## Library Functions / Macros 

The library and functions / Macros that are called by the various sub
modules are identified below,

1.  IntplVarXY_u16_u16Xu16Y_Cnt

2.  FPM_FloatToFixed_m

3.  TableSize_m

4.  Abs_s16_m

5.  FPM_FixedToFloat_m

## Data Hiding Functions

1.  None

## Global Functions/Macros Defined by this Module

None

## Local Functions/Macros Used by this MDD only

None

# Software Module Implementation

## Runtime Environment (RTE) Initial Values

This section lists the initial values of data written by this module but
controlled by the RTE. After RTE initialization, the data in this table
will contain these values.

| Data | Value |
|------|-------|
|      |       |

## Initialization Functions

### Init: 

#### Design Rationale

None

#### Module Outputs

None

#### Module Internal 

## Periodic Functions

### Per: ComplErr_Per1

#### Design Rationale

None

#### Program Flow Start

Rte_Call_ComplErr_Per1_CP0_CheckpointReached

#### Store Module Inputs to Local copies

TrqCmdcrf_MtrNm_T_f32 = Rte_IRead_ComplErr_Per1_TorqueCmdCRF_MtrNm_f32()

#### Compliance Error Flowchart

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ComplErr/doc/mediax/media/image2.emf)

#### Store Local copy of outputs into Module Outputs

Rte_IWrite_ComplErr_Per1_ComplErr_HwDeg_f32(ComplErr_HwDeg_T_f32)

#### Program Flow End

Rte_Call_ComplErr_Per1_CP1_CheckpointReached

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

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

| Function Name | Calling Frequency | System State(s) in which the function is called |
|--------------------------|-----------------|------------------------------|
| ComplErr_Per1 | 2 ms              | ALL                                             |

## Execution Requirements for Serial Communication Functions 

| Function Name | Sub-Module called by (Serial Comm Function Name) |
|---------------|--------------------------------------------------|
| None          |                                                  |

#  [section-2]

#  Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

| Name of Sub Module | Software Segment                    |
|--------------------|-------------------------------------|
| PwrLmtFuncCr_Per1  | RTE_START_SEC_AP_COMPLERR_APPL_CODE |

##  [section-3]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

| Name of Sub Module | Software Segment |
|--------------------|------------------|
| None               |                  |

#  [section-4]

#  Known Issues / Limitations with Design

1.  INLINE functions defined in GlobalMacro.h are not unit tested.

#  Revision Control Log

|             |            |                                        |           |                     |
|------|------|--------------------------------------------|---------|---------|
| **Item \#** | **Rev \#** | **Change Description**                 | **Date**  | **Author Initials** |
| 1           | 1.0        | Initial Version (SF-41 v001)           | 22-Aug-13 | SP                  |
| 2           | 2.0        | Updated the Cal Dimensions per CR 9874 | 04-Nov-13 | SP                  |

{% endraw %}