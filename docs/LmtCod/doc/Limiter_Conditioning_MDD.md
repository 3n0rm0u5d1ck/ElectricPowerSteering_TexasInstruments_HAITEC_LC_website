---
layout: default
title: Limiter_Conditioning_MDD
nav_order: 2
parent: Component
---
{% raw %}
# Module – Limiter Conditioning [module-limiter-conditioning]

# High-Level Description

This MDD describes the summation of all assist and limit terms used in
an Electric Power Steering application.

# Figures

## Diagram – Component Diagram

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/LmtCod/doc/mediax/media/image1.png"
style="width:3.03056in;height:2.59375in" />

# Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

|                             |                |                           |
|-----------------------------|----------------|---------------------------|
| Module Inputs               | Module Outputs |                           |
| AssistEOTGain_Uls_f32       |                | EOTGainLtd_Uls_f32        |
| AssistEOTLimit_MtrNm_f32    |                | EOTLimitLtd_MtrNm_f32     |
| AssistStallLimit_MtrNm_f32  |                | OutputRampMultLtd_Uls_f32 |
| AssistVehSpdLimit_MtrNm_f32 |                | StallLimitLtd_MtrNm_f32   |
| OutputRampMult_Uls_f32      |                | ThermalLimitLtd_MtrNm_f32 |
| ThermalLimit_MtrNm_f32      |                | VehSpdLimitLtd_MtrNm_f32  |
| VehicleSpeed_Kph_f32        |                |                           |
| CCLTrqRamp_Uls_f32          |                |                           |

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
<td>CurrAssistEOTGain_Uls_M_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td>1</td>
<td>LMTCOD_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>CurrOutputRampMult_Uls_M_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td>1</td>
<td>LMTCOD_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>CurrAssistEOTLimit_MtrNm_M_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td>8.8</td>
<td>LMTCOD_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>CurrAssistStallLimit_MtrNm_M_f32</td>
<td>Single Precision Floating Point</td>
<td>0</td>
<td>8.8</td>
<td>LMTCOD_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>CurrAssistVehSpdLimit_MtrNm_M_f32</td>
<td>Single Precision Floating Point</td>
<td>0</td>
<td>8.8</td>
<td>LMTCOD_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>CurrThermalLimit_MtrNm_M_f32</td>
<td>Single Precision Floating Point</td>
<td>0</td>
<td>8.8</td>
<td>LMTCOD_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>CCLTrqRamp_Uls_M_f32</td>
<td>Single Precision Floating Point</td>
<td>0</td>
<td>1</td>
<td>LMTCOD_START_SEC_VAR_CLEARED_32</td>
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

|                                        |
|----------------------------------------|
| Constant Name                          |
| k_GainDecSlew_UlspS_f32                |
| k_TorqueDecSlew_MtrNmpS_f32            |
| t_GainIncSlewTblX_Kph_u9p7\[2\]        |
| t_GainIncSlewTblY_UlspS_u9p7\[2\]      |
| t_TorqueIncSlewTblX_Kph_u9p7\[2\]      |
| t_TorqueIncSlewTblY_MtrNmpS_u13p3\[2\] |
| k_CCLTrqRampIncSlew_UlspS_f32          |

## Program(fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

|               |            |       |       |
|---------------|------------|-------|-------|
| Constant Name | Resolution | Units | Value |
|               |            |       |       |
|               |            |       |       |
|               |            |       |       |
|               |            |       |       |

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

|                                  |
|----------------------------------|
| Constant Name                    |
|                                  |
|                                  |
| D_2MS_SEC_F32                    |
| FLTINJ_ASSTEOTGAIN_LMTCOD        |
| FLTINJ_OUTPUTRAMPMULT_LMTCOD     |
| FLTINJ_ASSTEOTLIMIT_LMTCOD       |
| BC_LMTRCONDN_FAULTINJECTIONPOINT |

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

2.  Sign_f32_m()

3.  Min_m()

4.  Max_m()

5.  Abs_f32_m()

6.  IntplVarXY_u16_u16Xu16Y_Cnt()

7.  FPM_FloatToFixed_m()

8.  FPM_FixedToFloat_m()

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
| Rte_InitValue_AssistEOTGain_Uls_f32       | 1     |
| Rte_InitValue_AssistEOTLimit_MtrNm_f32    | 8.8   |
| Rte_InitValue_AssistStallLimit_MtrNm_f32  | 8.8   |
| Rte_InitValue_AssistVehSpdLimit_MtrNm_f32 | 8.8   |
| Rte_InitValue_OutputRampMult_Uls_f32      | 0     |
| Rte_InitValue_ThermalLimit_MtrNm_f32      | 8.8   |
| Rte_InitValue_EOTGainLtd_Uls_f32          | 1     |
| Rte_InitValue_EOTLimitLtd_MtrNm_f32       | 8.8   |
| Rte_InitValue_OutputRampMultLtd_Uls_f32   | 0     |
| Rte_InitValue_StallLimitLtd_MtrNm_f32     | 8.8   |
| Rte_InitValue_ThermalLimitLtd_MtrNm_f32   | 8.8   |
| Rte_InitValue_VehSpdLimitLtd_MtrNm_f32    | 8.8   |
| Rte_InitValue_VehicleSpeed_Kph_f32        | 0.0   |
| Rte_InitValue_CCLTrqRamp_Uls \_f32        | 1.0   |

## Initialization Functions

N/A

## Periodic Functions

### Per: LmtCod_Per1

#### Design Rationale

This function provides a layer of protection from erroneous signals
feeding into SF-04 Sum & Limit. It is applied primarily to “Limiting”
signals that serve to reduce motor torque command under certain
operating conditions. This function can prevent step response or
“toggling” behavior that might cause undesirable vehicle feel. It
includes capability of fault injection at some inputs to facilate
tuning. See FDD SF-38 for more details.

#### Program Flow Start

Rte_Call_LmtCod_Per1_CP0_CheckpointReached()

#### Store Module Inputs to Local copies

|                               |                                                   |
|--------------------------|----------------------------------------------|
| Local Copy                    | Module Input Name                                 |
| AssistEOTGain_Uls_T_f32       | Rte_IRead_LmtCod_Per1_AssistEOTGain_Uls_f32       |
| AssistEOTLimit_MtrNm_T_f32    | Rte_IRead_LmtCod_Per1_AssistEOTLimit_MtrNm_f32    |
| AssistStallLimit_MtrNm_T_f32  | Rte_IRead_LmtCod_Per1_AssistStallLimit_MtrNm_f32  |
| AssistVehSpdLimit_MtrNm_T_f32 | Rte_IRead_LmtCod_Per1_AssistVehSpdLimit_MtrNm_f32 |
| OutputRampMult_Uls_T_f32      | Rte_IRead_LmtCod_Per1_OutputRampMult_Uls_f32      |
| ThermalLimit_MtrNm_T_f32      | Rte_IRead_LmtCod_Per1_ThermalLimit_MtrNm_f32      |
| VehicleSpeed_Kph_T_f32        | Rte_IRead_LmtCod_Per1_VehicleSpeed_Kph_f32        |
| \_CCLTrqRamp_Uls \_T_f32      | Rte_IRead_LmtCod_Per1_CCLTrqRamp_Uls \_f32        |

####  (Processing of function)………

\\

#### Store Local copy of outputs into Module Outputs

|                                   |                                                  |
|----------------------------------------|--------------------------------|
| Local Copy                        | Module Output Name                               |
| CurrAssistEOTGain_Uls_M_f32       | Rte_IWrite_LmtCod_Per1_EOTGainLtd_Uls_f32        |
| CurrAssistEOTLimit_MtrNm_M_f32    | Rte_IWrite_LmtCod_Per1_EOTLimitLtd_MtrNm_f32     |
| FinalCurrOutputRampMult_Uls_T_f32 | Rte_IWrite_LmtCod_Per1_OutputRampMultLtd_Uls_f32 |
| CurrAssistStallLimit_MtrNm_M_f32  | Rte_IWrite_LmtCod_Per1_StallLimitLtd_MtrNm_f32   |
| CurrThermalLimit_MtrNm_M_f32      | Rte_IWrite_LmtCod_Per1_ThermalLimitLtd_MtrNm_f32 |
| CurrAssistVehSpdLimit_MtrNm_M_f32 | Rte_IWrite_LmtCod_Per1_VehSpdLimitLtd_MtrNm_f32  |

#### Program Flow End

Rte_Call_LmtCod_Per1_CP1_CheckpointReached()

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
| LmtCod_Per1   | 2ms               | All                                             |

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

|                    |                                   |
|--------------------|-----------------------------------|
| Name of Sub Module | Software Segment                  |
| LmtCod_Per1()      | RTE_START_SEC_AP_LMTCOD_APPL_CODE |

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

|             |            |                                                        |            |                     |
|------|------|--------------------------------------------|---------|---------|
| **Item \#** | **Rev \#** | **Change Description**                                 | **Date**   | **Author Initials** |
| 1           | 1.0        | Document creation for component based design process   | 28-Aug-12  | NRAR                |
| 2           | 2.0        | Check points corrected                                 | 23-Sep-12  | Selva               |
| 3           | 3.0        | Update to FDD SF38 v002 – CR8292                       | 17-May-13  | BDO                 |
| 4           | 4.0        | Update to FDD SF38 v003                                | 09-July-13 | Selva               |
| 5           | 5.0        | Changed the init value of “CCLTrqSlew” from “0” to “1” |            |                     |

{% endraw %}