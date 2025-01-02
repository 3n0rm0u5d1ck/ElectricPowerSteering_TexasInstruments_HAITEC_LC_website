---
layout: default
title: EOTDampingFirewall_MDD
nav_order: 3
parent: EtDmpFw
---
{% raw %}
# Module – EOTDampingFirewall [module-eotdampingfirewall]

# High-Level Description

This MDD describes the summation of all assist and limit terms used in
an Electric Power Steering application.

# Figures

## Diagram – Component Diagram

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/EtDmpFw/doc/mediax/media/image1.png"
style="width:4.0875in;height:3.47847in" />

# Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

|                             |                |                         |
|-----------------------------|----------------|-------------------------|
| Module Inputs               | Module Outputs |                         |
| AssistEOTDamping_MtrNm_f32  |                | EOTDampingLtd_MtrNm_f32 |
| CRFMtrVel_MtrRadpS_f32      |                |                         |
| HandwheelAuthority_Uls_f32  |                |                         |
| HandwheelPosition_HwDeg_f32 |                |                         |
| Vehicle_Speed_Kph_f32       |                |                         |
| EOTDisable_Cnt_lgc          |                |                         |
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
<td>EOTDmpFWActvLtd_MtrNm_D_f32</td>
<td>Single Precision Float</td>
<td>-16</td>
<td>16</td>
<td>ETDMPFW_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>EOTDmpFWInActvLtd_MtrNm_D_f32</td>
<td>Single Precision Float</td>
<td>-8.8</td>
<td>8.8</td>
<td>ETDMPFW_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>UprBndActive_MtrNm_D_f32</td>
<td>Single Precision Float</td>
<td>-16</td>
<td>16</td>
<td>ETDMPFW_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>LwrBndActive_MtrNm_D_f32</td>
<td>Single Precision Floating Point</td>
<td>-16</td>
<td>16</td>
<td>ETDMPFW_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>EOTDmpFWActvRegion_Cnt_D_lgc</td>
<td>n/a</td>
<td>FALSE</td>
<td>TRUE</td>
<td>ETDMPFW_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="odd">
<td>EOTDmpFWHWAuth_Cnt_D_lgc</td>
<td>n/a</td>
<td>FALSE</td>
<td>TRUE</td>
<td>ETDMPFW_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="even">
<td>EOTDmpFWMode_Cnt_M_u08</td>
<td>Uint8</td>
<td>0</td>
<td>2</td>
<td>ETDMPFW_START_SEC_VAR_CLEARED_08</td>
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
<tr class="odd">
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

|                                       |
|---------------------------------------|
| Constant Name                         |
| k_MinRackTrvl_HwDeg_u12p4             |
| t2_EOTPosDepDmpTblX_HwDeg_u12p4       |
| k_EOTDynConf_Uls_u8p8                 |
| t_EOTDmpFWActiveBoundX_MtrRadpS_s11p4 |
| t2_EOTDmpFWActiveBoundY_MtrNm_s7p8    |
| k_EOTDmpFWInactiveLim_MtrNm_f32       |
| t_EOTDmpFWVehSpd_Kph_u9p7             |

## Program(fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

|                             |            |          |       |
|-----------------------------|------------|----------|-------|
| Constant Name               | Resolution | Units    | Value |
| D_INACTIVEREGION_ULS_U08    | N/A        | Unitless | 0     |
| D_ACTIVEREGION_ULS_U08      | N/A        | Unitless | 1     |
| D_FIREWALLLDISABLED_ULS_U08 | N/A        | Unitless | 2     |
|                             |            |          |       |

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

|                                |
|--------------------------------|
| Constant Name                  |
| D_ZERO_ULS_F32                 |
|                                |
| D_MTRTRQCMDHILMT_MTRNM_F32     |
| D_MTRTRQCMDLOLMT_MTRNM_F32     |
| BC_ETDMPFW_FAULTINJECTIONPOINT |
| STD_ON                         |
| FLTINJ_EOTDAMPING_ETDMPFW      |
| D_NEGONE_CNT_S16               |
| D_FALSE_CNT_LGC                |

### Module specific Lookup Tables Constants

(This is for lookup tables (arrays) with fixed values, same name as
other tables)

|               |            |       |                  |
|---------------|------------|-------|------------------|
| Constant Name | Resolution | Value | Software Segment |
| None          |            |       |                  |

# Functions/Macros used by the Sub-Modules 

## Library Functions / Macros 

The library and functions / Macros that are called by the various sub
modules are identified below,

1.  Limit_m()

2.  

3.  

4.  

5.  Abs_f32_m()

6.  BilinearXYM_s16_s16Xs16YM_Cnt()

7.  FPM_FloatToFixed_m()

## Data Hiding Functions

1.  N/A

## Global Functions/Macros Defined by this Module

N/A

## Local Functions/Macros Used by this MDD only

N/A

# Software Module Implementation

## Runtime Environment (RTE) Initial Values

This section lists the initial values of data written by this module but
controlled by the RTE. After RTE initialization, the data in this table
will contain these values.

|                                           |       |
|-------------------------------------------|-------|
| Data                                      | Value |
| Rte_InitValue_AssistEOTDamping_MtrNm_f32  | 0     |
| Rte_InitValue_CRFMtrVel_MtrRadpS_f32      | 0     |
| Rte_InitValue_EOTDampingLtd_MtrNm_f32     | 0     |
| Rte_InitValue_HandwheelAuthority_Uls_f32  | 0     |
| Rte_InitValue_HandwheelPosition_HwDeg_f32 | 0     |

## Initialization Functions

N/A

## Periodic Functions

### Per: EtDmpFw_Per1

#### Design Rationale

#### Program Flow Start

Rte_Call_EtDmpFw_Per1_CP0_CheckpointReached()

#### Store Module Inputs to Local copies

|                               |                                                    |
|--------------------------|----------------------------------------------|
| Local Copy                    | Module Input Name                                  |
| AsstEOTDamping_MtrNm_T_f32    | Rte_IRead_EtDmpFw_Per1_AssistEOTDamping_MtrNm_f32  |
| HandwheelPosition_HwDeg_T_f32 | Rte_IRead_EtDmpFw_Per1_HandwheelPosition_HwDeg_f32 |
| HandwheelAuthority_Uls_T_f32  | Rte_IRead_EtDmpFw_Per1_HandwheelAuthority_Uls_f32  |
| CRFMtrVel_MtrRadpS_T_f32      | Rte_IRead_EtDmpFw_Per1_CRFMtrVel_MtrRadpS_f32      |
| VehicleSpeed_Kph_T_f32        | Rte_IRead_EtDmpFw_Per1_Vehicle_Speed_Kph_f32       |
| EOTDisable_Cnt_T_lgc          | Rte_IRead_EtDmpFw_Per1_EOTDisable_Cnt_lgc          |
| MECCounter_Cnt_T_enum         | Rte_IRead_EtDmpFw_Per1_MEC_Counter_Cnt_enum        |
|                               |                                                    |

####  (Processing of function)………

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/EtDmpFw/doc/mediax/media/image2.wmf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/EtDmpFw/doc/mediax/media/image3.wmf)

#### Store Local copy of outputs into Module Outputs

|                               |                                                 |
|----------------------------|--------------------------------------------|
| Local Copy                    | Module Output Name                              |
| LimitedEOTDamping_MtrNm_T_f32 | Rte_IWrite_EtDmpFw_Per1_EOTDampingLtd_MtrNm_f32 |

#### Program Flow End

Rte_Call_EtDmpFw_Per1_CP1_CheckpointReached()

#### Fault Recovery Functions

N/A

## Shutdown Functions

N/A

## Interrupt Functions

N/A

## Serial Communication Functions

N/A

# Execution Requirements

## Execution Sequence of the Module

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

|               |                   |                                                 |
|--------------------------|-----------------|------------------------------|
| Function Name | Calling Frequency | System State(s) in which the function is called |
| EtDmpFw_Per1  | 2ms               | All                                             |

## Execution Requirements for Serial Communication Functions 

|               |                                                  |
|---------------|--------------------------------------------------|
| Function Name | Sub-Module called by (Serial Comm Function Name) |
| None          |                                                  |

#   [section]

# Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

|                    |                                    |
|--------------------|------------------------------------|
| Name of Sub Module | Software Segment                   |
| EtDmpFw_Per1       | RTE_START_SEC_AP_ETDMPFW_APPL_CODE |

##  [section-1]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

|                    |                  |
|--------------------|------------------|
| Name of Sub Module | Software Segment |
| None               |                  |

# Known Issues / Limitations With Design

1.  INLINE functions defined in globalmacro.h are not unittested.

# Revision Control Log [revision-control-log]

|             |            |                                                                                          |            |                     |
|------|------|--------------------------------------------|---------|---------|
| **Item \#** | **Rev \#** | **Change Description**                                                                   | **Date**   | **Author Initials** |
| 1           | 1.0        | Document creation for component based design process                                     | 6-Sep-12   | NRAR                |
| 2           | 2.0        | Added watchdog checkpoints                                                               | 16-Sept-12 | BWL                 |
| 3           | 3.0        | Corrected for static variable software section                                           | 19 Sep 12  | Selva               |
| 4           | 4.0        | Updated as per FDDVer002, FaultInjectionPoint added to AsstEOTDamping_MtrNm_T_f32 signal | 29 Jan 13  | Selva               |
| 5           | 5.0        | Updated to SF-27 v003                                                                    | 16-May-13  | SP                  |
| 6           | 6.0        | Removed calibration k_EOTDmpFWInputLim_MtrNm_f32 per anomaly 6850                        | 21-Aug-14  | KJS                 |
| 7           | 7.0        | Updated as per Unit Test Findings                                                        | 27-Aug-14  | KPIT_SM             |

{% endraw %}