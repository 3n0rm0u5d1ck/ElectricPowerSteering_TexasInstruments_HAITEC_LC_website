---
layout: default
title: Battery_Voltage_MDD
nav_order: 2
parent: Battery Voltage
---
{% raw %}
# Module -- Battery Voltage66 [module----battery-voltage66]

# High-Level Description

This module is responsible for applying voltage and time based
hysteresis to the battery voltage to determine over voltage and low
voltage faults.

# Figures

## Diagram – Function Data Sharing

This diagram shows all data that is shared between functions within the
module.

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/BatteryVoltage/doc/mediax/media/image1.png"
style="width:3.54167in;height:3.54167in" />

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
| Batt_Volt_f32                        | VswitchClosed_Cnt_lgc                 |
| BattSwitched_Volt_f32                | Vecu_Volts_f32                        |
| SysCVSwitch_Volt_f32                 | SysC_Vecu_Volt_f32                    |

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
<td>Vecu_Volts_M_f32</td>
<td>N/A</td>
<td>Volts</td>
<td>5</td>
<td>31</td>
<td>BATTERYVOLTAGE_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>VswitchClosed_Cnt_M_lgc</td>
<td>N/A</td>
<td>Cnt</td>
<td>FALSE</td>
<td>TRUE</td>
<td>BATTERYVOLTAGE_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="even">
<td>VswitchCorrLimDiff_Volts_D_f32</td>
<td>N/A</td>
<td>Volts</td>
<td>0</td>
<td>26</td>
<td>BATTERYVOLTAGE_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>VecuVbatCorrLimDiff_Volts_D_f32</td>
<td>N/A</td>
<td>Volts</td>
<td>0</td>
<td>26</td>
<td>BATTERYVOLTAGE_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>VswitchCorrErrAcc_Cnt_M_u16</td>
<td>N/A</td>
<td>Cnt</td>
<td>0</td>
<td>255</td>
<td>BATTERYVOLTAGE_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="odd">
<td>VecuVbatCorrErrAcc_Cnt_M_u16</td>
<td>N/A</td>
<td>Cnt</td>
<td>0</td>
<td>255</td>
<td>BATTERYVOLTAGE_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td>Vbatt_Volts_M_f32</td>
<td>N/A</td>
<td>Volts</td>
<td>5</td>
<td>31</td>
<td>BATTERYVOLTAGE_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>OvervoltageFaultSet_Cnt_M_lgc</td>
<td>boolean</td>
<td>Cnt</td>
<td>FALSE</td>
<td>TRUE</td>
<td>BATTERYVOLTAGE_START_SEC_VAR_CLEARED_BOOLEAN</td>
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

|                             |
|-----------------------------|
| Constant Name               |
| k_MaxSwitchedVolt_Volts_f32 |
| k_MaxBattVoltDiff_Volts_f32 |
| k_VswitchCorrLim_Cnt_Str    |
| k_VecuCorrLim_Cnt_Str       |
| k_VecuVbatCorrLim_Volts_f32 |
| k_VswitchCorrLim_Volts_f32  |

## Program(fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

|                           |                                 |       |
|---------------------------|---------------------------------|-------|
| Constant Name             | Resolution                      | Value |
| D_VSWITCHEDTHRESH_ULS_F32 | Single precision floating point | 0.8   |
| D_VECUMAX_VOLTS_F32       | Single precision floating point | 31.0  |

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

|                                       |
|---------------------------------------|
| Constant Name                         |
| D_VECUMIN_VOLTS_F32                   |
| BC_BATTERYVOLTAGE_FAULTINJECTIONPOINT |
| FLTINJ_VECU_BATTERYVOLTAGE            |

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

2.  Rte_Call_Batt_Batt_V_f32()

3.  Rte_Call_BattSwitched_BattSwitched_V_f32

4.  Rte_Call_SysC_Vswitch_BattSwitched_V_f32

5.  Rte_Call_BatteryVoltage_Per1_CP0_CheckpointReached

6.  Rte_Call_BatteryVoltage_Per1_CP1_CheckpointReached

7.  Rte_Call_BatteryVoltage_Per2_CP0_CheckpointReached

8.  Rte_Call_BatteryVoltage_Per2_CP1_CheckpointReached

9.  Rte_Pim_OvervoltageData()

10. Rte_Call_OvervoltageData_SetRamBlockStatus()

## Local Functions/Macros Used by this MDD only

(Note if they are defined in another source file, then reference the
appropriate header file)

The local functions/macros in this module are identified below,

#   [section]

# Software Module Implementation

## Initialization Functions

Module state variables are initialized to 0 at start-up by RAM init.

### Init: BatteryVoltage_Init1

#### Design Rationale

None

#### Program Flow Start

None

#### Store Module Inputs to Local copies

None

###  [section-1]

###  [section-2]

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

None

## Periodic Functions

### Per: BatteryVoltage_Per1

#### Design Rationale

See FDD 08B.

#### Program Flow Start

Rte_Call_BatteryVoltage_Per1_CP0_CheckpointReached()

#### Store Module Inputs to Local copies

Vbatt_Volts_T_f32 = Rte_IRead_BatteryVoltage_Per2_Batt_Volt_f32()

Vswitched_Volts_T_f32 =
Rte_IRead_BatteryVoltage_Per1_BattSwitched_Volt_f32()

#### Perform Over and Low Voltage Diagnostics

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/BatteryVoltage/doc/mediax/media/image3.wmf)

#### Store Local copy of outputs into Module Outputs

Vecu_Volts_M_f32 = Vecu_Volts_T_f32

Vbatt_Volts_M_f32 = Vbatt_Volts_T_f32

Rte_IWrite_BatteryVoltage_Per1\_ VswitchClosed
\_Cnt_lgc(VswitchClosed_Cnt_T_lgc)

Rte_IWrite_BatteryVoltage_Per1\_ Vecu \_Volts_f32(Vecu_Volts_T_f32)

Rte_IWrite_BatteryVoltage_Per1_SysC_Vecu_Volt_f32(Vecu_Volts_M_f32)

#### Program Flow End

Rte_Call_BatteryVoltage_Per1_CP1_CheckpointReached()

### Per: BatteryVoltage_Per2

#### Design Rationale

None.

#### Program Flow Start

Rte_Call_BatteryVoltage_Per2_CP0_CheckpointReached()

#### Store Module Inputs to Local copies

VecuVbatCorrLimDiff_Volts_T_f32 =0

NTCSysFailCtrlV_T_lgc = FALSE

Vswitched_Volts_T_f32 =
Rte_IRead_BatteryVoltage_Per2_BattSwitched_Volt_f32()

SysCVswitch_Volts_T_f32 =
Rte_IRead_BatteryVoltage_Per2_SysCVSwitch_Volt_f32()

#### VSwitch and Vecu cross correlation diagnostics

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/BatteryVoltage/doc/mediax/media/image4.wmf)

#### Store Local copy of outputs into Module Outputs

VswitchCorrLimDiff_Volts_D_f32 = VswitchCorrLimDiff_Volts_T_f32

VecuVbatCorrLimDiff_Volts_D_f32 = VecuVbatCorrLimDiff_Volts_T_f32

#### Program Flow End

Rte_Call_BatteryVoltage_Per2_CP1_CheckpointReached()

## Fault Recovery Functions

None

## Shutdown Functions

None

## Interrupt Functions

### Isr: Isr_OvervoltThresh

#### Design Rationale

None

#### Description

####  [section-3]

#### Serial Communication Functions

### SCom: BatteryVoltage_SCom_ClearTransOvData

|                      |                                      |      |     |     |          |
|----------------|-----------------------------|-------|--------|-------|------|
| **Function Name**    | BatteryVoltage_SCom_ClearTransOvData | Type | Min | Max | UTP Tol. |
| **Arguments Passed** | N/A                                  |      |     |     |          |
| **Return Value**     | N/A                                  |      |     |     |          |

#### Design Rationale

None

#### Program Flow Start

None

#### Store Module Inputs to Local Copies

None

#### Clear Transient Overvoltage Data Service

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/BatteryVoltage/doc/mediax/media/image6.wmf)

#### Store Local Copy of outputs into Module Outputs

None

#### Program Flow End

None

### BatteryVoltage_SCom_ReadTransOvData

|                      |                                     |         |     |       |          |
|----------------|-----------------------------|-------|--------|-------|------|
| **Function Name**    | BatteryVoltage_SCom_ReadTransOvData | Type    | Min | Max   | UTP Tol. |
| **Arguments Passed** | \*OvervoltageCounter_Cnt_u16        | Uint16  | 0   | 65535 | 0        |
|                      | \*MaxBattVoltage_Volts_f32          | Float32 | 0   | 31    | 0        |
| **Return Value**     | N/A                                 |         |     |       |          |

#### Design Rationale

None

#### Program Flow Start

None

#### Store Module Inputs to Local Copies

None

#### Read Transient Overvoltage Data Service

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/BatteryVoltage/doc/mediax/media/image7.wmf)

#### Store Local Copy of outputs into Module Outputs

None

#### Program Flow End

None

## Local Function/Macro Definitions [local-functionmacro-definitions]

If these are numerous and defined in a separate source file then
reference the source file only.

# Execution Requirements

## Execution Sequence of the Module

(Describe in words relevant details about the execution sequence of the
different sub modules.)

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

|                      |           |                   |                                                 |
|--------------------------|----------------|----------------|----------------|
| Function Name        | Task List | Calling Frequency | System State(s) in which the function is called |
| BatteryVoltage_Init1 |           | On Init           | WARM INIT                                       |
| BatteryVoltage_Per1  |           | 2ms               | ALL                                             |
| BatteryVoltage_Per2  |           | 4ms               | OPERATE                                         |
| Isr_OvervoltThresh   |           | On Event          | ALL                                             |

## Execution Requirements for Serial Communication Functions 

|                                      |                                                  |
|------------------------------|------------------------------------------|
| Function Name                        | Sub-Module called by (Serial Comm Function Name) |
| BatteryVoltage_SCom_ClearTransOvData | EPS_DiagSrvc                                     |
| BatteryVoltage_SCom_ReadTransOvData  | EPS_DiagSrvc                                     |

#   [section-4]

# Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

|                                        |                                 |
|----------------------------------------|---------------------------------|
| Name of Sub Module                     | Software Segment                |
| BatteryVoltage_Init1                   | RTE_AP_BATTERYVOLTAGE_APPL_CODE |
| BatteryVoltage_Per1()                  | RTE_AP_BATTERYVOLTAGE_APPL_CODE |
| BatteryVoltage_Per2()                  | RTE_AP_BATTERYVOLTAGE_APPL_CODE |
| BatteryVoltage_SCom_ClearTransOvData() | RTE_AP_BATTERYVOLTAGE_APPL_CODE |
| BatteryVoltage_SCom_ReadTransOvData()  | RTE_AP_BATTERYVOLTAGE_APPL_CODE |
| Isr_OvervoltThresh                     |                                 |

## Local Functions

This table identifies the software segments for local functions
identified in this module.

|                    |                  |
|--------------------|------------------|
| Name of Sub Module | Software Segment |

#   [section-5]

# Known Issues / Limitations With Design

1.  None

# Revision Control Log

|             |            |                                                                        |            |                     |
|------|------|--------------------------------------------|---------|---------|
| **Item \#** | **Rev \#** | **Change Description**                                                 | **Date**   | **Author Initials** |
| 1           | 1.0        | Initial AutoSAR release.                                               | 07-Feb-11  | L.N.                |
| 2           | 2.0        | Updated to meet FDD 08B rev 02 Ecu Voltage                             | 28-Mar-11  | JJW                 |
| 3           | 3.0        | Updated to meet FDD 08B rev 02 Ecu Voltage                             | 30-Mar-11  | JJW                 |
| 4           | 4.0        | Corrected execution states for periodic                                | 07-Apr-11  | JJW                 |
| 5           | 5.0        | Updated NTC’s to global constants                                      | 02-Dec-11  | BG                  |
| 6           | 6          | Updated NTC’s global constants names per latest NTC definitions        | 11-Jan-12  | JJW                 |
| 7           | 7          | Updated as per FDD Ver 004                                             | 17-Oct-12  | NRAR                |
| 8           | 8          | changed from client server port type to Sender/Receiver port           | 29 -Oct-12 | NRAR                |
| 9           | 9          | MDD updates for UTP catchups                                           | 30-Jan-13  | NRAR                |
| 10          | 10         | Checked in the right version of the MDD into synergy                   | 28-Mar-13  | VK                  |
| 11          | 11         | Updated to FDD Ver 005                                                 | 16-APR-13  | Jared               |
| 12          | 12         | Updated to FDD Ver 006 and anomaly 5138 correction                     | 26-Jun-13  | SR                  |
| 13          | 13         | Added missing ISR function for overvoltage diagnostic (A5789)          | 3-Jan-14   | Jared               |
| 14          | 14         | Add BATTERYVOLTAGE_REPORTERRORSTATUS for program specific integration. | 8-Jan-14   | BDO                 |

{% endraw %}