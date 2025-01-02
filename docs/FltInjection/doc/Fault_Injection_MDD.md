---
layout: default
title: Fault_Injection_MDD
nav_order: 2
parent: FltInjection
---
{% raw %}
# Module –  [module]

# High-Level Description

This module manages the fault injection system. It receives parameters
through CANape-generated XCP signals (which write directly into memory),
and creates a fault injection signal at a specified location based on
these parameters.

# Figures

## Component Diagram

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/FltInjection/doc/mediax/media/image1.png"
style="width:2.22917in;height:1.31181in" />

#  Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

| Module Inputs            | Module Outputs |     |
|--------------------------|----------------|-----|
| MotorVelCRF_MtrRadpS_f32 |                |     |

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
<td>CanapeParameters_M_Str</td>
<td>CanapeParametersType</td>
<td></td>
<td></td>
<td>FLTINJECTION_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="even">
<td>FaultTrigger_Cnt_M_lgc</td>
<td>n/a</td>
<td>FALSE</td>
<td>TRUE</td>
<td>FLTINJECTION_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="odd">
<td>ManualTriggerHangover_Cnt_M_lgc</td>
<td>n/a</td>
<td>FALSE</td>
<td>TRUE</td>
<td>FLTINJECTION_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="even">
<td>FaultInjectionLocation_Cnt_M_enum</td>
<td>1</td>
<td>0</td>
<td>255</td>
<td>FLTINJECTION_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="odd">
<td>PathGain_Uls_M_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td>5</td>
<td>FLTINJECTION_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>FaultOffset_Uls_M_f32</td>
<td>Single Precision Float</td>
<td>-15</td>
<td>15</td>
<td>FLTINJECTION_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>SinewaveAmplitude_Uls_M_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td>15</td>
<td>FLTINJECTION_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>FaultDuration_mS_M_u32</td>
<td>1</td>
<td>0</td>
<td>10000</td>
<td>FLTINJECTION_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>FaultStartTime_mS_M_u32</td>
<td>1</td>
<td>FULL</td>
<td>FULL</td>
<td>FLTINJECTION_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>SineFactor_kHz_M_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td>0.125663706</td>
<td>FLTINJECTION_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>PathOffset_Uls_M_f32</td>
<td>Single Precision Float</td>
<td>-30</td>
<td>30</td>
<td>FLTINJECTION_START_SEC_VAR_CLEARED_32</td>
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
<td rowspan="9">CanapeParametersType</td>
<td>FaultInjectionLocation_Cnt_enum</td>
<td>FltInjectionLocType</td>
<td>0</td>
<td>255</td>
</tr>
<tr class="even">
<td>PathGain_Uls_f32</td>
<td>float32</td>
<td>0</td>
<td>5</td>
</tr>
<tr class="odd">
<td>FaultOffset_Uls_f32</td>
<td>float32</td>
<td>-15</td>
<td>15</td>
</tr>
<tr class="even">
<td>SinewaveFrequency_Hz_f32</td>
<td>float32</td>
<td>0</td>
<td>20</td>
</tr>
<tr class="odd">
<td>SinewaveAmplitude_Uls_f32</td>
<td>float32</td>
<td>0</td>
<td>15</td>
</tr>
<tr class="even">
<td>VelocityTriggerSetpoint_MtrRadpS_f32</td>
<td>float32</td>
<td>0</td>
<td>800</td>
</tr>
<tr class="odd">
<td>EnableManualTrigger_Cnt_lgc</td>
<td>boolean</td>
<td>FALSE</td>
<td>TRUE</td>
</tr>
<tr class="even">
<td>FaultDuration_mS_u32</td>
<td>uint32</td>
<td>0</td>
<td>10000</td>
</tr>
<tr class="odd">
<td>AssistDDFactor_Uls_f32</td>
<td>float32</td>
<td>1</td>
<td>2</td>
</tr>
</tbody>
</table>

# Constant Data Dictionary

## Calibration Constants

This section lists the calibrations used by the module. For details on
calibration constants, refer to the Data Dictionary for the application.

| Constant Name |
|---------------|
| None          |

## Program(fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

| Constant Name            | Resolution             | Units    | Value          |
|-----------------------------|---------------|--------------|--------------|
| D_FREQUENCYTOL_KHZ_F32   | Single Precision Float | kHz      | 0.0005         |
| D_AMPLITUDETOL_ULS_F32   | Single Precision Float | Unitless | 0.000244140625 |
| D_MTRVELTOL_MTRRADPS_F32 | Single Precision Float | MtrRadpS | 0.03125        |

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

| Constant Name                        |
|--------------------------------------|
| D_ZERO_ULS_F32                       |
| D_ONE_ULS_F32                        |
| D_ZERO_CNT_U32                       |
| D_2PI_ULS_F32                        |
| D_SFINVMILLI_ULS_F32                 |
| BC_FLTINJECTION_ENABLEFAULTINJECTION |
| STD_ON                               |

### Module specific Lookup Tables Constants

| Constant Name | Resolution | Value | Software Segment |
|---------------|------------|-------|------------------|
| None          |            |       |                  |

#  Functions/Macros used by the Sub-Modules 

## Library Functions / Macros 

The library and functions / Macros that are called by the various sub
modules are identified below,

1.  Abs_f32_m

2.  sinf

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

| Data                                   | Value |
|----------------------------------------|-------|
| Rte_InitValue_MotorVelCRF_MtrRadpS_f32 | 0     |

## Initialization Functions

None

##  Periodic Functions

### Per: \_Per1

#### Design Rationale

None

#### Program Flow Start

N/A

#### Store Module Inputs to Local copies

MotorVelCRF_MtrRadpS_T_f32 =
Rte_IRead_FltInjection_Per1_MotorVelCRF_MtrRadpS_f32()

AbsMotorVelCRF_MtrRadpS_T_f32 = Abs_f32_m(MotorVelCRF_MtrRadpS_T_f32)

#### Check If Active, Generate Waveform

#### Check for Armed and Enabled

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

N/A

##  Fault Recovery Functions

None

## Shutdown Functions

None

## Interrupt Functions

None

## Serial Communication Functions

### SCom: \_SCom_FltInjection

|                      |                      | Type                | Min  | Max | UTP Tol. |
|---------------|---------------------------|-------------|------|------|--------|
| **Arguments Passed** | SignalPath_Uls_f32   | Float \*            | -8.8 | 8.8 |          |
|                      | LocationKey_Cnt_enum | FltInjectionLocType | 0    | 255 |          |
| **Return Value**     | None                 |                     |      |     |          |

#### Design Rationale

This SCom function implements the “Fault Injection Waveform Generation”
section of DF-01.

#### Program Flow Start

N/A

#### Store Module Inputs to Local copies

None

#### Apply Generated Waveform

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/FltInjection/doc/mediax/media/image4.emf)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

N/A

# Execution Requirements

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

| Function Name     | Calling Frequency | System State(s) in which the function is called |
|--------------------------|-----------------|------------------------------|
| FltInjection_Per1 | 2 ms              | ALL                                             |

## Execution Requirements for Serial Communication Functions 

| Function Name                  | Sub-Module called by (Serial Comm Function Name) |
|-----------------------------|-------------------------------------------|
| FltInjection_SCom_FltInjection |                                                  |

#  [section]

#  Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

| Name of Sub Module             | Software Segment                        |
|--------------------------------|-----------------------------------------|
| FltInjection_Per1              | RTE_START_SEC_AP_FLTINJECTION_APPL_CODE |
| FltInjection_SCom_FltInjection | RTE_START_SEC_AP_FLTINJECTION_APPL_CODE |

##  [section-1]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

| Name of Sub Module | Software Segment |
|--------------------|------------------|
| None               |                  |

#  [section-2]

#  Known Issues / Limitations With Design

1.  INLINE functions defined in GlobalMacro.h are not unit tested.

#  Revision Control Log

| **Item \#** | **Rev \#** | **Change Description**                            | **Date**  | **Author Initials** |
|------|------|--------------------------------------------|---------|---------|
| 1           | 1.0        | Initial Version                                   | 01-May-12 | OT                  |
| 2           | 2.0        | Fixed fault injection timing issue (anomaly 3326) | 18-May-12 | OT                  |

{% endraw %}