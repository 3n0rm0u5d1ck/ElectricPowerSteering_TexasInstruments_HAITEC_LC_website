---
layout: default
title: Return_Firewall_MDD
nav_order: 2
parent: Return Firewall (Safety)
---
{% raw %}
# Module –  [module]

# High-Level Description

This module limits the return command according to safety requirements.

# Figures

## Component Diagram

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ReturnFirewall/doc/mediax/media/image1.png"
style="width:3.58264in;height:2.33056in" />

#  Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

| Module Inputs               | Module Outputs |                         |
|-----------------------------|----------------|-------------------------|
| HandwheelPosition_HwDeg_f32 |                | LimitedReturn_MtrNm_f32 |
| ReturnCmd_MtrNm_f32         |                |                         |
| VehicleSpeed_Kph_f32        |                |                         |
| Defeat_Return_Svc_Cnt_lgc   |                |                         |
| MEC_Counter_Cnt_enum        |                |                         |

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
<td>UprBound_MtrNm_D_f32</td>
<td>Single Precision Float</td>
<td>-8.8</td>
<td>8.8</td>
<td>RETURNFIREWALL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>LwrBound_MtrNm_D_f32</td>
<td>Single Precision Float</td>
<td>-8.8</td>
<td>8.8</td>
<td>RETURNFIREWALL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>OverBound_Cnt_D_lgc</td>
<td>N/A</td>
<td>FALSE</td>
<td>TRUE</td>
<td>RETURNFIREWALL_START_SEC_VAR_CLEARED_BOOLEAN</td>
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
| t_RtrnFWVehSpd_Kph_u9p7\[\]            |
| t_RtrnFWUprBoundX_HwDeg_s11p4\[\]      |
| t2_RtrnFWUprBoundY_MtrNm_s4p11\[\]\[\] |
|                                        |
|                                        |

## Program(fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

| Constant Name | Resolution | Units | Value |
|---------------|------------|-------|-------|
| None          |            |       |       |
|               |            |       |       |

####  [section]

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

| Constant Name    |
|------------------|
| D_ONE_ULS_F32    |
| D_ZERO_ULS_F32   |
| D_NEGONE_CNT_S16 |
| D_FALSE_CNT_LGC  |

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

3.  BilinearXMYM_s16_s16XMs16YM_Cnt

4.  TableSize_m

5.  Limit_m

6.  Rte_Call_NxtrDiagMgr_SetNTCStatus

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

| Data                                      | Value |
|-------------------------------------------|-------|
| Rte_InitValue_HandwheelPosition_HwDeg_f32 | 0     |
| Rte_InitValue_LimitedReturn_MtrNm_f32     | 0     |
| Rte_InitValue_ReturnCmd_MtrNm_f32         | 0     |
| Rte_InitValue_VehicleSpeed_Kph_f32        | 0     |

## Initialization Functions

None

##  Periodic Functions

### Per: \_Per1

#### Design Rationale

None

#### Program Flow Start

#### Rte_Call_ReturnFirewall_Per1_CP0_CheckpointReachedStore Module Inputs to Local copies

HandwheelPosition_HwDeg_T_f32 =
Rte_IRead_ReturnFirewall_Per1_HandwheelPosition_HwDeg_f32()

ReturnCmd_MtrNm_T_f32 =
Rte_Iread_ReturnFirewall_Per1_ReturnCmd_MtrNm_f32()

VehicleSpeed_Kph_T_f32 =
Rte_Iread_ReturnFirewall_Per1_VehicleSpeed_Kph_f32()

VehicleSpeed_Kph_T_u9p7 = FPM_FloatToFixed_m(VehicleSpeed_Kph_T_f32,
u9p7_T)

HandwheelPosition_HwDeg_T_s11p4 =
FPM_FloatToFixed_m(HandwheelPosition_HwDeg_T_f32, s11p4_T)

DefeatReturnSvc_Cnt_T_lgc =
Rte_IRead_ReturnFirewall_Per1_Defeat_Return_Svc_Cnt_lgc

MECCounter_Cnt_T_enum =
Rte_IRead_ReturnFirewall_Per1_MEC_Counter_Cnt_enum

#### Perform Boundary Lookups and Limiting

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ReturnFirewall/doc/mediax/media/image3.emf)

#### Store Local copy of outputs into Module Outputs

UprBound_MtrNm_D_f32 = UprBound_MtrNm_T_f32

LwrBound_MtrNm_D_f32 = LwrBound_MtrNm_T_f32

#### Program Flow End

Rte_Call_ReturnFirewall_Per1_CP1_CheckpointReached

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

ReturnFirewall_Per1 is executed at a rate of 2 ms.

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

| Function Name       | Calling Frequency | System State(s) in which the function is called |
|--------------------------|-----------------|------------------------------|
| ReturnFirewall_Per1 | 2 ms              | ALL                                             |

## Execution Requirements for Serial Communication Functions 

| Function Name | Sub-Module called by (Serial Comm Function Name) |
|---------------|--------------------------------------------------|
| None          |                                                  |

#  [section-2]

#  Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

| Name of Sub Module  | Software Segment                          |
|---------------------|-------------------------------------------|
| ReturnFirewall_Per1 | RTE_START_SEC_AP_RETURNFIREWALL_APPL_CODE |

##  [section-3]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

| Name of Sub Module | Software Segment |
|--------------------|------------------|
| None               |                  |

#  [section-4]

#  Known Issues / Limitations With Design

1.  INLINE functions defined in GlobalMacro.h are not unit tested.

#  Revision Control Log

| **Item \#** | **Rev \#** | **Change Description**                                                        | **Date**   | **Author Initials** |
|------|------|--------------------------------------------|---------|---------|
| 1           | 1.0        | Initial Version                                                               | 27-Apr-12  | OT                  |
| 2           | 2.0        | Fixed calibration naming conflict                                             | 10-May-12  | OT                  |
| 3           | 3.0        | Added IF block in per1 to check if the signal touches boundary- Ver 002       | 30-July-12 | NRAR                |
| 4           | 4.0        | NTC is set when ReturnCmd reaches boundaries based on SER                     | 6-Aug-12   | NRAR                |
| 5           | 5.0        | Added checkpoints and memmap software segment is updated for static variables | 23-Sep-12  | Selva               |
| 6           | 6.0        | Updates to meet v003 of the FDD                                               | 01-Feb-13  | VK                  |
| 7           | 7.0        | Updates to fix mismatches b/w src and MDD                                     | 18-Feb-13  | VK                  |
| 8           | 8.0        | Updates to meet v004 of the FDD                                               | 13-May-13  | SP                  |

{% endraw %}