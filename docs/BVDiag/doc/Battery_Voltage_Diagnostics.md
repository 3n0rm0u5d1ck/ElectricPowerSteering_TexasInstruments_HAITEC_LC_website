---
layout: default
title: Battery_Voltage_Diagnostics
nav_order: 1
parent: Battery Voltage Diagnostics
---
{% raw %}
# Module -- Battery Voltage66 [module----battery-voltage66]

# High-Level Description

This module is responsible for applying voltage and time based
hysteresis to the battery voltage to determine over voltage(B5) and low
voltage faults(B0). Requirements for all these faults are detailed in
SER. Also customer specific B1diagnostic is implemented.

# Figures

## Diagram – Function Data Sharing

This diagram shows all data that is shared between functions within the
module.

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/BVDiag/doc/mediax/media/image2.png"
style="width:2.9375in;height:2.72917in" />

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
| Batt_Volt_f32                        |                                       |
| CCLMSAActive_Cnt_lgc                 |                                       |
| NTCB1Enbl_Cnt_lgc                    |                                       |
| NTCB0Enbl_Cnt_lgc                    |                                       |

## Module Internal Variables

This section identifies the name, range and resolutions for module
specific data created by this module. If there are no range restrictions
on the variable, the term “FULL” is placed into the table for legal
range.

<table>
<colgroup>
<col style="width: 38%" />
<col style="width: 12%" />
<col style="width: 11%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Variable Name</td>
<td>User Defined Type</td>
<td>Resolution</td>
<td><p>Legal Range</p>
<p>(min)</p></td>
<td><p>Legal Range</p>
<p>(max)</p></td>
<td>Software Segment</td>
</tr>
<tr class="even">
<td>BVDiag_LowSetInitBD_ms_M_u32p0</td>
<td>N/A</td>
<td>1ms/Cnt</td>
<td>FULL</td>
<td>FULL</td>
<td></td>
</tr>
<tr class="odd">
<td>BVDiag_LowClrInitBD_ms_M_u32p0</td>
<td>N/A</td>
<td>1ms/Cnt</td>
<td>FULL</td>
<td>FULL</td>
<td></td>
</tr>
<tr class="even">
<td>BVDiag_OvSetInitBD_ms_M_u32p0</td>
<td>N/A</td>
<td>1ms/Cnt</td>
<td>FULL</td>
<td>FULL</td>
<td></td>
</tr>
<tr class="odd">
<td>BVDiag_OvClrInitBD_ms_M_u32p0</td>
<td>N/A</td>
<td>1ms/Cnt</td>
<td>FULL</td>
<td>FULL</td>
<td></td>
</tr>
<tr class="even">
<td>BVDiag_UvSetInitBD_ms_M_u32p0</td>
<td>N/A</td>
<td>1ms/Cnt</td>
<td>FULL</td>
<td>FULL</td>
<td></td>
</tr>
<tr class="odd">
<td>BVDiag_UvClrInitBD_ms_M_u32p0</td>
<td>N/A</td>
<td>1ms/Cnt</td>
<td>FULL</td>
<td>FULL</td>
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

|                               |
|-------------------------------|
| Constant Name                 |
| k_OvDetect_Volts_u10p6        |
| k_OvNotDetect_Volts_u10p6     |
| k_OvDetect_ms_u16p0           |
| k_OvNotDetect_ms_u16p0        |
| k_LowNotDetect_Volts_u10p6    |
| k_LowDetect_Volts_u10p6       |
| k_LowDetect_ms_u16p0          |
| k_LowNotDetect_ms_u16p0       |
| k_MSALowNotDetect_Volts_u10p6 |
| k_MSALowDetect_Volts_u10p6    |
| k_MSALowDetect_ms_u16p0       |
| k_MSALowNotDetect_ms_u16p0    |
| k_BattDiagUvMax_Volt_u10p6    |
| k_BattDiagUvMin_Volt_u10p6    |
| k_UvNotDetect_ms_u16p0        |
| k_UvDetect_ms_u16p0           |
| k_BattUvRecMax_Volt_u10p6     |

## Program(fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

|                      |            |       |
|----------------------|------------|-------|
| Constant Name        | Resolution | Value |
| D_ABOVEMAX_CNT_U16   | 1          | 0x11  |
| D_BELOWMIN_CNT_U16   | 1          | 0x22  |
| D_INDEADBAND_CNT_U16 | 1          | 0x33  |
| D_DIAGOV_CNT_U16     | 1          | 1     |
| D_DIAGLOW_CNT_U16    | 1          | 2     |

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

|                         |
|-------------------------|
| Constant Name           |
| NTC_Num_OpVoltage       |
| NTC_Num_OpVoltageOvrMax |

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

1.  FPM_FloatToFixed_m()

## Data Hiding Functions

The data hiding functions / macros used in this module are identified
below,

1.  Rte_Call_NxtrDiagMgr_SetNTCStatus()

2.  Rte_Call_BVDiag_Per1_CP0_CheckpointReached()

3.  Rte_Call_BVDiag_Per1_CP1_CheckpointReached()

4.  Rte_IRead_BVDiag_Per1_CCLMSAActive_Cnt_lgc()

5.  Rte_Call_SystemTime_GetSystemTime_mS_u32()

6.  Rte_Call_SystemTime_DtrmnElapsedTime_mS_u16()

7.  Rte_Call_SystemTime_GetSystemTime_mS_u32()

8.  Rte_Call_SystemTime_DtrmnElapsedTime_mS_u16()

## Local Functions/Macros Used by this MDD only

(Note if they are defined in another source file, then reference the
appropriate header file)

The local functions/macros in this module are identified below,

1.  ApplyHysteresis()

2.  ControlTimers()

#   [section]

# Software Module Implementation

## Initialization Functions

Module state variables are initialized to 0 at start-up by RAM init.

###   [section-1]

## Periodic Functions [periodic-functions]

### Per: BVDiag_Per1

#### Design Rationale

All customer SER’s describes same functionality for B0,B5.

B1 NTC is only for Chrysler.

#### Program Flow Start

Rte_Call_BVDiag_Per1_CP0_CheckpointReached()

#### Store Module Inputs to Local copies

BattVoltage_Volts_T_f32 = Rte_IRead_BVDiag_Per1_Batt_Volt_f32()

MSAActive_T_lgc = Rte_IRead_BVDiag_Per1_CCLMSAActive_Cnt_lgc()

NTCB1Enbl_Cnt_T_lgc = Rte_IRead_BVDiag_Per1_NTCB1Enbl_Cnt_lgc()

NTCB0Enbl_Cnt_T_lgc = Rte_IRead_BVDiag_Per1_NTCB0Enbl_Cnt_lgc()

#### Perform Over and Low Voltage Diagnostics

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/BVDiag/doc/mediax/media/image3.wmf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/BVDiag/doc/mediax/media/image4.wmf)

#### Store Local copy of outputs into Module Outputs

None.

#### Program Flow End

Rte_Call_BVDiag_Per1_CP1_CheckpointReached()

## Fault Recovery Functions

None

## Shutdown Functions

None

## Interrupt Functions

None

## Serial Communication Functions

None

## Local Function/Macro Definitions

If these are numerous and defined in a separate source file then
reference the source file only.

### Control Timers

|                      |                           |           |           |           |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | ControlTimers             | Type      | Min       | Max       |
| **Arguments Passed** | BattVoltage_Volts_T_u10p6 | u10p6_T   | See DD^1^ | See DD^1^ |
|                      | CompareType_T_u16         | UINT16    | 0x0011    | 0x0022    |
|                      | UpperCal_T_u10p6          | u10p6_T   | See DD^1^ | See DD^1^ |
|                      | LowerCal_T_u10p6          | u10p6_T   | See DD^1^ | See DD^1^ |
|                      | SetTimer_T_ptr            | u32p0_T\* | FULL      | FULL      |
|                      | ClrTimer_T_ptr            | u32p0_T\* | FULL      | FULL      |
|                      | SetTimer_ms_T_u16p0       | u16p0_T   | FULL      | FULL      |
|                      | ClrTimer_ms_T_u16p0       | u16p0_T   | FULL      | FULL      |
|                      | Option_T_u16              | UINT16    | 0x0001    | 0x0002    |
| **Return Value**     | N/A                       |           |           |           |

#### Note 1 – See data dictionary for input which corresponds to a calibration or global variable [note-1-see-data-dictionary-for-input-which-corresponds-to-a-calibration-or-global-variable]

#### Description

This generic local function is used to control set and clear timers for
the diagnostic functions as well as control flags used to indicate
battery voltage is “Ok” for the application. Data is passed to indicate
the following:

> CompareType_T_u16: Passed data to indicate the type of comparison to
> be made internally to the function (Above Max or Below Min). Used in a
> decision block within the function. Essentially, reverses the logic
> between an over voltage test (where below min is a normal operating
> point) and low voltage test (where above max is a normal operating
> point)

UpperCal_T_u10p6: Voltage level calibration of the hysteresis (upper
threshold).

> LowerCal_T_u10p6: Voltage level calibration of the hysteresis (lower
> threshold). Note: Lower cal must be \<= Upper Cal.
>
> SetTimer_T_ptr: Pointer to the appropriate module specific 32-bit set
> timer under test (examples are set timer for over voltage, low
> voltage, battery Ok, etc.)
>
> ClrTimer_T_ptr: Pointer to the appropriate module specific 32-bit
> clear timer under test (examples are set timer for over voltage, low
> voltage, battery Ok, etc.)
>
> SetTimer_ms_T_u16p0: Calibration used for the time based hysteresis to
> set the condition. Note that the calibrations will differ for set
> timers for over voltage, low voltage, etc.
>
> ClrTimer_ms_T_u16p0: Calibration used for the time based hysteresis to
> clear the condition. Note that the calibrations will differ for set
> timers for over voltage, low voltage, etc.
>
> Option_T_u16: Identifies which function is being used to identify
> which set fault, clear fault functions to call, which battery voltage
> OK state is being checked, etc.

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/BVDiag/doc/mediax/media/image5.wmf)

### Apply Hysteresis

|                      |                  |         |           |           |
|----------------------|------------------|---------|-----------|-----------|
| **Function Name**    | ApplyHysteresis  | Type    | Min       | Max       |
| **Arguments Passed** | BattIn_T_u10p6   | u10p6_T | See DD^1^ | See DD^1^ |
|                      | HighCal_T_u10p6  | u10p6_T | See DD^1^ | See DD^1^ |
|                      | LowCal_T_u10p6   | u10p6_T | See DD^1^ | See DD^1^ |
| **Return Value**     | OutputZone_T_u16 | UINT16  | 0x0011    | 0x0033    |

#### Note 1 – See data dictionary for input which corresponds to a calibration or global variable [note-1-see-data-dictionary-for-input-which-corresponds-to-a-calibration-or-global-variable-1]

#### Description

This local function is used to determine the next state for a voltage
based hysteresis as applied to the battery voltage level. Data is passed
to include the battery voltage, upper calibration and a lower
calibration. The function returns the state of the battery voltage
relative to the cals (either “Above Max”, “Below Min” or “In Deadband”).
Note that the design requires the upper cal to be larger than the lower
cal for proper operation.

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/BVDiag/doc/mediax/media/image6.wmf)

# Execution Requirements

## Execution Sequence of the Module

(Describe in words relevant details about the execution sequence of the
different sub modules.)

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

|               |           |                   |                                                 |
|--------------------------|----------------|----------------|----------------|
| Function Name | Task List | Calling Frequency | System State(s) in which the function is called |
| BVDiag_Per1   |           | 10ms              | ALL                                             |

## Execution Requirements for Serial Communication Functions 

|               |                                                  |
|---------------|--------------------------------------------------|
| Function Name | Sub-Module called by (Serial Comm Function Name) |
| None          |                                                  |

#   [section-2]

# Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

|                    |                         |
|--------------------|-------------------------|
| Name of Sub Module | Software Segment        |
| BVDiag_Per1()      | RTE_AP_BVDIAG_APPL_CODE |

## Local Functions

This table identifies the software segments for local functions
identified in this module.

|                    |                  |
|--------------------|------------------|
| Name of Sub Module | Software Segment |
| ControlTimers()    | AP_BVDIAG_CODE   |
| ApplyHysteresis()  | AP_BVDIAG_CODE   |

#   [section-3]

# Known Issues / Limitations With Design

1.  B1,B4 faults are removed from BMW,K2XX SER.

Revision Control Log

|             |            |                                                                             |             |                     |
|------|------|--------------------------------------------|---------|---------|
| **Item \#** | **Rev \#** | **Change Description**                                                      | **Date**    | **Author Initials** |
| 1           | 1.0        | Initial AutoSAR release.                                                    | 19-Oct-12   | NRAR                |
| 2           | 2.0        | Updated to SER Rev BMW SER EPS24102912 Rev 011C (CUSTOMER VERSION).docx     | 18-Mar-2013 | SP                  |
| 4           | 4.0        | Updated to Implement B1 as per Chrysler LWR SER Ver 5G                      | 11-Sep-13   | NRAR                |
| 5           | 5          | Corrected anomaly allowing configurable enable of B1 fault from SrlComInput | 14-Nov-13   | Jared               |
| 6           | 6          | Configurable enable of B0 fault from SrlComInput                            | 19-Aug-14   | M. Story            |

{% endraw %}