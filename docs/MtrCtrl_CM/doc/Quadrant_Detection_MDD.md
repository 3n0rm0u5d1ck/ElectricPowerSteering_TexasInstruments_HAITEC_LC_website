---
layout: default
title: Quadrant_Detection_MDD
nav_order: 8
parent: Motor Control
---
{% raw %}
# Module --  [module---]

# High-Level Description

This module takes the cumulative motor position and determines the motor
direction (using a previously saved state variable and a calibration
constant for hysteresis). It then computes the torque command sign from
the scaled torque command and uses both of these values to determine the
motor quadrant.

# Figures

## Component Diagram

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrCtrl_CM/doc/mediax/media/image1.png"
style="width:2.03472in;height:1.49306in" />

### Diagram – Function QuadDet_Per1

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrCtrl_CM/doc/mediax/media/image2.emf)

#  Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

| Module Inputs             | Module Outputs |                    |
|---------------------------|----------------|--------------------|
| MRFMtrTrqCmdScl_MtrNm_f32 |                | InstMtrDir_Cnt_s08 |
| MRFCumMtrPos_Deg_f32      |                | MtrQuad_Cnt_u08    |

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
<td>MtrTrqCmdSign_Cnt_D_s08</td>
<td>1</td>
<td colspan="2">-1, 1</td>
<td>AP_QUADRANTDETECT_VAR_NOINIT</td>
</tr>
<tr class="even">
<td>PrevCumMtrPos_Deg_M_f32</td>
<td>Single Precision Float</td>
<td>-1</td>
<td>1</td>
<td>AP_QUADRANTDETECT_VAR_INIT</td>
</tr>
<tr class="odd">
<td>PrevInstMtrDir_Cnt_M_s08</td>
<td>1</td>
<td>-1</td>
<td>1</td>
<td>AP_QUADRANTDETECT_VAR_INIT</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td colspan="2"></td>
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

| Constant Name            |
|--------------------------|
| k_InstMtrDirHyst_Deg_f32 |

## Program(fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

| Constant Name            | Resolution             | Units   | Value                             |
|-------------------------------|--------------|--------------|--------------|
| D_CUMMTRPOSLOLMT_DEG_F32 | Single Precision Float | Degrees | min value of MRFCumMtrPos_Deg_f32 |
| D_CUMMTRPOSHILMT_DEG_F32 | Single Precision Float | Degrees | max value of MRFCumMtrPos_Deg_f32 |
| D_MTRTRQCMDTOL_MTRNM_F32 | Single Precision Float | MtrNm   | 0.00390625                        |

####  [section]

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

| Constant Name      |
|--------------------|
| D_QUADRANT1_CNT_U8 |
| D_QUADRANT2_CNT_U8 |
| D_QUADRANT3_CNT_U8 |
| D_QUADRANT4_CNT_U8 |

### Module specific Lookup Tables Constants

| Constant Name | Resolution | Value | Software Segment |
|---------------|------------|-------|------------------|
| None          |            |       |                  |

#  Functions/Macros used by the Sub-Modules 

## Library Functions / Macros 

The library and functions / Macros that are called by the various sub
modules are identified below,

1.  Abs_f32_m()

2.  Sign_f32_m()

## Data Hiding Functions

1.  
2.  
3.  
4.  

None

## Global Functions/Macros Defined by this Module

None

# Software Module Implementation

## Runtime Environment (RTE) Initial Values

This section lists the initial values of data written by this module but
controlled by the RTE. After RTE initialization, the data in this table
will contain these values.

| Data                                    | Value |
|-----------------------------------------|-------|
| Rte_InitValue_InstMtrDir_Cnt_s08        | 0     |
| Rte_InitValue_MRFCumMtrPos_Deg_f32      | 0     |
| Rte_InitValue_MRFMtrTrqCmdScl_MtrNm_f32 | 0     |
| Rte_InitValue_MtrQuad_Cnt_u08           | 1     |

## Initialization Functions

None

##  Periodic Functions

### Per: \_Per1

#### Design Rationale

None

#### Program Flow Start

N/A

#### Store Module Inputs to Local copies

MtrTrqCmdScl_MtrNm_T_f32 =
Rte_IRead_QuadDet_Per1_MRFMtrTrqCmdScl_MtrNm_f32();

CumMtrPos_Deg_T_f32 = Rte_IRead_QuadDet_Per1_MRFCumMtrPos_Deg_f32();

#### Determine Motor Direction

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrCtrl_CM/doc/mediax/media/image3.emf)

#### Determine Instantaneous Torque Command Sign

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrCtrl_CM/doc/mediax/media/image4.emf)

#### Determine Motor Quadrant

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrCtrl_CM/doc/mediax/media/image5.emf)

#### Store Local copy of outputs into Module Outputs

Rte_IWrite_QuadDet_Per1_InstMtrDir_Cnt_s08(PrevInstMtrDir_Cnt_M_s08);

Rte_IWrite_QuadDet_Per1_MtrQuad_Cnt_u08(MtrQuad_Cnt_T_u08);

#### Program Flow End

N/A

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

QuadDet_Per1 executes every 2 milliseconds.

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

| Function Name | Calling Frequency | System State(s) in which the function is called |
|--------------------------|-----------------|------------------------------|
| QuadDet_Per1  | 2 ms              | WARM INIT, OPERATE, DISABLE, OFF                |

## Execution Requirements for Serial Communication Functions 

| Function Name | Sub-Module called by (Serial Comm Function Name) |
|---------------|--------------------------------------------------|
| \<None\>      |                                                  |

#  [section-2]

#  Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

| Name of Sub Module | Software Segment                   |
|--------------------|------------------------------------|
| QuadDet_Per1       | RTE_START_SEC_AP_QUADDET_APPL_CODE |

##  [section-3]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

| Name of Sub Module | Software Segment |
|--------------------|------------------|
| None               |                  |

#  [section-4]

#  Known Issues / Limitations With Design

1.  INLINE functions defined in globalmacro.h are not unit tested  
    Revision Control Log

| **Item \#** | **Rev \#** | **Change Description**                 | **Date**  | **Author Initials** |
|------|------|--------------------------------------------|---------|---------|
| 1           | 1          | Initial MDD for component based design | 23-Dec-11 | O.T.                |
| 2           | 2.0        | Fixed Inconsistencies, UTP issues      | 25-Jan-12 | OT                  |

{% endraw %}