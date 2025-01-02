---
layout: default
title: SignalConditioning_MDD
nav_order: 3
parent: Signal Conditionning
---
{% raw %}
# Module – Signal Conditioning [module-signal-conditioning]

# High-Level Description

This function conditions a signal received from SER prior to its
distribution to other functions. Typical conditioning methods may
include filters, slew rates, gain values or limits.

# Figures

## Diagram – Function Data Sharing

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SgnlCond/doc/mediax/media/image1.png"
style="width:3.50625in;height:1.64306in" />

###   [section]

# Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

(Note: Full variable names required in table.)

(Note: All global variables including End Of Line data used should be
shown here)

| Module Inputs (Global Variable Name) | Module Outputs (Global Variable Name) |
|----------------------------------|--------------------------------------|
| SrlComVehSpd_Kph_f32                 | VehicleSpeed_Kph_f32                  |
| SrlCom_VehicleLonAccel_KphpS_f32     | Vehicle_LonAccel_KphpS_f32            |

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
<td>SignlCondn_CurrSrlComVehSpd_Kph_M_f32</td>
<td>Single precision floating point</td>
<td>See DataDictionary</td>
<td>See DataDictionary</td>
<td>SIGNLCONDN_START_SEC_VAR_NOINIT_32</td>
</tr>
<tr class="even">
<td>SignlCondn_CurrSrlComVehLonAccel_KphpS_M_f32</td>
<td>Single precision floating point</td>
<td>See DataDictionary</td>
<td>See DataDictionary</td>
<td>SIGNLCONDN_START_SEC_VAR_NOINIT_32</td>
</tr>
</tbody>
</table>

### User defined typedef definition/declaration 

This section documents any user types uniquely used for the module.

<table>
<colgroup>
<col style="width: 34%" />
<col style="width: 31%" />
<col style="width: 13%" />
<col style="width: 9%" />
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
</tbody>
</table>

# Constant Data Dictionary

## Calibration Constants

This section lists the calibrations used by the module. For details on
calibration constants, refer to the Data Dictionary for the application.

| Constant Name                    |
|----------------------------------|
| k_VehSpdSlewRate_KphpSec_f32     |
| k_VehAccelSlewRate_KphpSecSq_f32 |

## Program(fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

| Constant Name                | Resolution             | Value   |
|------------------------------|------------------------|---------|
| D_VEHLONACCELGAIN_KPHPS_F32  | N/A                    | 3.6     |
| D_VEHSPDLOLMT_KPH_F32        | Single precision Float | 0.0     |
| D_VEHSPDHILMT_KPH_F32        | Single precision Float | 511.0   |
| D_VEHLONACCELLOLMT_KPHPS_F32 | Single precision Float | (-50.0) |
| D_VEHLONACCELHILMT_KPHPS_F32 | Single precision Float | 50.0    |

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

| Constant Name                     |
|-----------------------------------|
| D_2MS_SEC_F32                     |
| BC_SIGNLCONDN_FAULTINJECTIONPOINT |
| FLTINJ_SRLCOMVEHSPD_SGNLCOND      |
| FLTINJ_SRLCOMVEHLONACCEL_SGNLCOND |

###  Module specific Lookup Tables Constants

(This is for lookup tables (arrays) with fixed values, same name as
other tables)

| Constant Name | Resolution | Value | Software Segment |
|---------------|------------|-------|------------------|
| None          |            |       |                  |

## Lookup Table Definitions

# Software Module Implementation

## Initialization Functions

None

## Periodic Functions

### Per: SignlCondn \_Per1

#### Design Rationale

NOTE: For “starttime” calculations there is tendency for underflow and
this is expected in s/w design. So for unittesting, VBA model should be
implemented

such that it handles underflow and behaves like source code design.

#### Program Flow Start

#### Rte_Call_SignlCondn_Per1_CP0_CheckpointReached()Store Module Inputs to Local copies

SrlComVehSpd_Kph_T_f32 =
Rte_IRead_SignlCondn_Per1_SrlComVehSpeed_Kph_f32

SrlComVehLonAccel_KphpS_T_f32 =
Rte_IRead_SignlCondn_Per1_SrlCom_VehicleLonAccel_KphpS_f32()

#### Signal Conditioning

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SgnlCond/doc/mediax/media/image2.emf)

#### Store Local copy of outputs into Module Outputs

Rte_Iwrite_SignlCondn_Per1_VehicleSpeed_Kph_f32
(SignlCondn_CurrSrlComVehSpd_Kph_M_f32)

Rte_IWrite_SignlCondn_Per1_Vehicle_LonAccel_KphpS_f32(SignlCondn_CurrSrlComVehLonAccel_KphpS_M_f32)

#### Program Flow End

Rte_Call_SignlCondn_Per1_CP1_CheckpointReached()

## Fault Recovery Functions

None

## Shutdown Functions

None

## Interrupt Functions

None

## Serial Communication Functions

#  Requirements

## Execution Sequence of the Module

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

| Function Name   | Calling Frequency | System State(s) in which the function is called |
|---------------------------|----------------|-----------------------------|
| SignlCondn_Per1 | 2 ms              | ALL States                                      |
|                 |                   |                                                 |

##  [section-1]

## Execution Requirements for Serial Communication Functions 

| Function Name | Sub-Module called by (Serial Comm Function Name) |
|---------------|--------------------------------------------------|
| None          |                                                  |

#  [section-2]

#  Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

| Name of Sub Module | Software Segment            |
|--------------------|-----------------------------|
| SignlCondn_Per1    | RTE_AP_SIGNLCONDN_APPL_CODE |
|                    |                             |

##  [section-3]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

| Name of Sub Module | Software Segment |
|--------------------|------------------|

#  Known Issues / Limitations With Design

1.  INLINE functions defined in globalmacro.h are not unit tested

#  Revision Control Log

|             |            |                                                                               |           |                     |
|------|------|--------------------------------------------|---------|---------|
| **Item \#** | **Rev \#** | **Change Description**                                                        | **Date**  | **Author Initials** |
| 1           | 1.0        | Initial release                                                               | 14-May-12 | NRAR                |
| 2           | 2.0        | Updated as per FDDVer002, FaultInjectionPoint added to SrlComVehSpeed signal  | 20-Aug-12 | NRAR                |
| 3           | 3.0        | Corrected Fault Injection function call                                       | 05-Sep-12 | NRAR                |
| 4           | 4.0        | Added checkpoints and memmap software segment is updated for static variables | 25-Sep-12 | Selva               |
| 5           | 5.0        | Updated to SF-33 ver 003                                                      | 23-May-13 | SP                  |
| 6           | 6.0        | Anomaly 6343 – Limit Outputs                                                  | 02-Apr-14 | SB                  |
| 7           | 7.0        | Changed naming for module internal variables                                  | 09-May-14 | SB                  |
| 8           | 8.0        | UTP fixes 11915                                                               | 12-May-14 | SB                  |

{% endraw %}