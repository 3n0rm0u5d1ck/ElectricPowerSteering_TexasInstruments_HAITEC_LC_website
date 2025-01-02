---
layout: default
title: VehSpdLmt_MDD
nav_order: 2
parent: Component
---
{% raw %}
# Module --  [module---]

# High-Level Description

The Vehicle Speed Limiting Function determines a limited assist torque
command value as a function of vehicle speed and handwheel position to
manage mechanical fatigue near end-of-travel positions.

# Figures

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/VehSpdLmt/doc/mediax/media/image1.tiff"
style="width:3.14583in;height:3.14583in" alt="VehSpdLmt.tif" />

## Diagram – Function Data Sharing

No Shared Data

### Diagram – Function

None

#  Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

(Note: Full variable names required in table.)

(Note: All global variables including End Of Line data used should be
shown here)

| Module Inputs         | Module Outputs |                          |
|-----------------------|----------------|--------------------------|
| VehSpd_Kph_f32        |                | AstVehSpdLimit_MtrNm_f32 |
| HwPos_HwDeg_f32       |                |                          |
| HwPosAuth_Uls_f32     |                |                          |
| CWPosition_HwDeg_f32  |                |                          |
| CCWPosition_HwDeg_f32 |                |                          |

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
<td>ZeroVehSpd_MtrNm_D_u5p11</td>
<td>2^-11</td>
<td>0</td>
<td>8.8</td>
<td>VEHSPDLMT_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td>LimitTerm_MtrNm_D_u5p11</td>
<td>2^-11</td>
<td>0</td>
<td>8.8</td>
<td>VEHSPDLMT_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="odd">
<td>BkPtOne_HwDeg_D_u12p4</td>
<td>2^-4</td>
<td>0</td>
<td>900</td>
<td>VEHSPDLMT_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td>BkPtTwo_HwDeg_D_u12p4</td>
<td>2^-4</td>
<td>0</td>
<td>900</td>
<td>VEHSPDLMT_START_SEC_VAR_CLEARED_16</td>
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

| Constant Name                  |
|--------------------------------|
| k_PosMaxOfstOne_HwDeg_u12p4    |
| k_PosMaxOfstTwo_HwDeg_u12p4    |
| t_MaxAsstTblX_Kph_u9p7\[\]     |
| t_MaxAsstTblY_MtrNm_u5p11\[5\] |

## Program(fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

| Constant Name                 | Resolution             | Units    | Value |
|-------------------------------|------------------------|----------|-------|
| D_MAXCONF_ULS_F32             | single precision float | Unitless | 1.0   |
| D_ASTVEHSPDLMTLOLMT_MTRNM_F32 | single precision float | MtrNm    | 0.0   |
| D_ASTVEHSPDLMTHILMT_MTRNM_F32 | single precision float | MtrNm    | 8.8   |

####  [section]

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

| Constant Name |
|---------------|
| \<None\>      |
|               |

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

1.  IntplVarXY_u16_u16Xu16Y_Cnt()

2.  Abs_s16_m()

3.  FPM_FloatToFixed_m()

4.  FPM_FixedToFloat_m()

5.  Limit_m()

## Data Hiding Functions

1.  \<None\>

2.  

## Global Functions/Macros Defined by this Module

### Global Function \#1

| **Function Name**    |     | Type | Min | Max | UTP Tol. |
|----------------------|-----|------|-----|-----|----------|
| **Arguments Passed** |     |      |     |     |          |
|                      |     |      |     |     |          |
| **Return Value**     |     |      |     |     |          |

#### Description

## Local Functions/Macros Used by this MDD only

### Local Function \#1

| **Function Name**    |     | Type | Min | Max | UTP Tol. |
|----------------------|-----|------|-----|-----|----------|
| **Arguments Passed** |     |      |     |     |          |
|                      |     |      |     |     |          |
| **Return Value**     |     |      |     |     |          |

#### Description

# Software Module Implementation

## Runtime Environment (RTE) Initial Values

This section lists the initial values of data written by this module but
controlled by the RTE. After RTE initialization, the data in this table
will contain these values.

| Data                     | Value |
|--------------------------|-------|
| VehSpd_Kph_f32           | 0.0   |
| HwPos_HwDeg_f32          | 0.0   |
| HwPosAuth_Uls_f32        | 0.0   |
| CWPosition_HwDeg_f32     | 0.0   |
| CCWPosition_HwDeg_f32    | 0.0   |
| AstVehSpdLimit_MtrNm_f32 | 8.8   |

## Initialization Functions

None

##  Periodic Functions

### Per: \_Per1

#### Design Rationale

None

#### Program Flow Start

#### Store Module Inputs to Local copies

Rte_Call_VehSpdLmt_Per1_CP0_CheckpointReached() HwPosAuth_Uls_T_f32 =
Rte_IRead_VehSpdLmt_Per1_HwPosAuth_Uls_f32()

HwPos_HwDeg_T_f32 = Rte_IRead_VehSpdLmt_Per1_HwPos_HwDeg_f32()

VehSpd_Kph_T_f32 = Rte_IRead_VehSpdLmt_Per1_VehSpd_Kph_f32()

CCWEOTPos_HwDeg_T_f32 = Rte_IRead_VehSpdLmt_Per1_CCWPosition_HwDeg_f32()

CWEOTPos_HwDeg_T_f32 = Rte_IRead_VehSpdLmt_Per1_CWPosition_HwDeg_f32()

#### Processing

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/VehSpdLmt/doc/mediax/media/image2.emf)

#### Store Local copy of outputs into Module Outputs

Rte_IWrite_VehSpdLmt_Per1_AstVehSpdLimit_MtrNm_f32(AstVehSpdLimit_MtrNm_f32)

#### Program Flow End

Rte_Call_VehSpdLmt_Per1_CP1_CheckpointReached()

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

Per1 is required to be run in the forward path

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

| Function Name  | Calling Frequency | System State(s) in which the function is called |
|--------------------------|-----------------|------------------------------|
| VehSpdLmt_Per1 | 2ms               | All                                             |

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
| VehSpdLmt_Per1     |                  |

##  [section-3]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

| Name of Sub Module | Software Segment |
|--------------------|------------------|
|                    |                  |

#  [section-4]

#  Known Issues / Limitations With Design

1.  (Item \#1)

#  Revision Control Log

| **Item \#** | **Rev \#** | **Change Description**                                                        | **Date**  | **Author Initials** |
|------|------|--------------------------------------------|---------|---------|
| 1           | 1          | Initial component design                                                      | 11/15/11  | LWW                 |
| 2           | 2          | Added checkpoints and memmap software segment is updated for static variables | 23-Sep-12 | Selva               |

{% endraw %}