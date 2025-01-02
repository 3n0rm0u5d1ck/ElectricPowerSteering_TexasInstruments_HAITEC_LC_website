---
layout: default
title: Bulk_Cap_Precharge_MDD
nav_order: 2
parent: Component
---
{% raw %}
# Module –  [module]

# High-Level Description

This module handles precharging of the bulk capacitor during
initialization. It is part of a larger initialization sequence, along
with motor driver diagnostics and temporal monitor.

# Figures

## Component Diagram

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/BkCpPc/doc/mediax/media/image1.png"
style="width:2.94583in;height:3.17569in" />

#  Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

| Module Inputs                           | Module Outputs |                              |
|-----------------------------------|--|------------------------------------|
| OVERRIDESIGDIAGADC_Volt_f32             |                | PwrDiscClosed_Cnt_lgc        |
| PMOSDIAGADC_Volt_f32                    |                | PwrDiscATestComplete_Cnt_lgc |
| MotorVelocityMRFUnfiltered_MtrRadpS_f32 |                | PwrDiscBTestComplete_Cnt_lgc |
| Batt_Volt_f32                           |                |                              |
| BattSwitched_Volt_f32                   |                |                              |
| PwrDiscATestStart_Cnt_lgc               |                |                              |
| PwrDiscBTestStart_Cnt_lgc               |                |                              |

## Module Internal Variables

This section identifies the name, range and resolutions for module
specific data created by this module. If there are no range restrictions
on the variable, the term “FULL” is placed into the table for legal
range.

<table>
<colgroup>
<col style="width: 34%" />
<col style="width: 14%" />
<col style="width: 12%" />
<col style="width: 12%" />
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
<td>FirstRunComplete_Cnt_M_lgc</td>
<td>n/a</td>
<td>FALSE</td>
<td>TRUE</td>
<td>BKCPPC_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="even">
<td>PowerRelayInitFltFailed_Cnt_M_lgc</td>
<td>n/a</td>
<td>FALSE</td>
<td>TRUE</td>
<td>BKCPPC_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="odd">
<td>PwrDiscATestComplete_Cnt_M_lgc</td>
<td>n/a</td>
<td>FALSE</td>
<td>TRUE</td>
<td>BKCPPC_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="even">
<td>PwrDiscBTestComplete_Cnt_M_lgc</td>
<td>n/a</td>
<td>FALSE</td>
<td>TRUE</td>
<td>BKCPPC_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="odd">
<td>PwrDiscClosed_Cnt_M_lgc</td>
<td>n/a</td>
<td>FALSE</td>
<td>TRUE</td>
<td>BKCPPC_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="even">
<td>BulkCapPrechargeState_Cnt_M_enum</td>
<td>1</td>
<td>0</td>
<td>7</td>
<td>BKCPPC_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="odd">
<td>RunTimeFaultAcc_Cnt_M_u16</td>
<td>1</td>
<td>FULL</td>
<td>FULL</td>
<td>BKCPPC_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td>VerifyDiscOpenDiagTimer_mS_M_u32</td>
<td>1</td>
<td>FULL</td>
<td>FULL</td>
<td>BKCPPC_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>WaitForSqrWaveDiagTimer_mS_M_u32</td>
<td>1</td>
<td>FULL</td>
<td>FULL</td>
<td>BKCPPC_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>PrechargeDiagTimer_mS_M_u32</td>
<td>1</td>
<td>FULL</td>
<td>FULL</td>
<td>BKCPPC_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>PostCloseDiagTimer_mS_M_u32</td>
<td>1</td>
<td>FULL</td>
<td>FULL</td>
<td>BKCPPC_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>VerifyCloseDiagTimer_mS_M_u32</td>
<td>1</td>
<td>FULL</td>
<td>FULL</td>
<td>BKCPPC_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>VdischMax_Volts_M_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td>21</td>
<td>BKCPPC_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>VdischMin_Volts_M_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td>19</td>
<td>BKCPPC_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>VbattStart_Volts_M_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td>30</td>
<td>BKCPPC_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>VswitchStart_Volts_M_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td>20</td>
<td>BKCPPC_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>MotionDetected_Cnt_D_lgc</td>
<td>n/a</td>
<td>FALSE</td>
<td>TRUE</td>
<td>BKCPPC_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="even">
<td>DeltaV_Volts_D_f32</td>
<td>Single Precision Float</td>
<td>-20</td>
<td>30</td>
<td>BKCPPC_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>VerifyPwrDiscCloseErrAcc_Cnt_M_u16</td>
<td>1</td>
<td>0</td>
<td>1000</td>
<td>BKCPPC_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td>VswitchCorrected_Volts_D_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td>120</td>
<td>BKCPPC_START_SEC_VAR_CLEARED_32</td>
</tr>
</tbody>
</table>

### User defined typedef definition/declaration 

This section documents any user types uniquely used for the module.

<table>
<colgroup>
<col style="width: 31%" />
<col style="width: 32%" />
<col style="width: 14%" />
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
<td>BulkCapPrechargeSequenceType</td>
<td><p>BULKCAP_WAITFORSTARTA = 0</p>
<p>BULKCAP_VERIFYDISCOPEN = 1</p>
<p>BULKCAP_WAITFORSQRWAVE = 2</p>
<p>BULKCAP_PRECHARGE = 3</p>
<p>BULKCAP_WAITFORSTARTB = 4</p>
<p>BULKCAP_POSTCLOSE = 5</p>
<p>BULKCAP_VERIFYCLOSE = 6</p>
<p>BULKCAP_RUNTIMEDIAG = 7</p></td>
<td>uint8</td>
<td>0</td>
<td>7</td>
</tr>
</tbody>
</table>

# Constant Data Dictionary

## Calibration Constants

This section lists the calibrations used by the module. For details on
calibration constants, refer to the Data Dictionary for the application.

| Constant Name                         |
|---------------------------------------|
| k_MtrMotionThresh_MtrRadpS_f32        |
| k_MaxSwitchedVolt_Volts_f32           |
| k_PwrDiscOpenThresh_Volts_f32         |
| k_PMOSDIAGOpenThresh_Volts_f32        |
| k_OVERRIDESIGDIAGOpenThresh_Volts_f32 |
| k_VerifyPwrDiscOpenThresh_mS_u16      |
| k_WaitForSqrWaveThresh_mS_u16         |
| k_PwrDiscCloseThresh_Volts_f32        |
| k_PrechargeThresh_mS_u16              |
| k_PMOSVError_Volts_f32                |
| k_PMOSTError_mS_u16                   |
| k_MaxDischEst_Uls_f32                 |
| k_MinDischEst_Uls_f32                 |
| k_VswitchDeltaThresh_Volts_f32        |
| k_VerifyPwrDiscCloseThresh_mS_u16     |
| k_ChargeMinDelta_Volts_f32            |
| k_VbattSwitchThreshNonExt_Volt_f32    |
| k_VbattSwitchThreshExNorm_Volt_f32    |
| k_ChargeMinDeltaNonOp_Volt_f32        |
| k_ChargeMinDeltaExtOp_Volt_f32        |
| k_ChargeMinDeltaNormlOp_Volt_f32      |
| k_ChargePumpDiag_Cnt_str              |
| k_VerifyPwrDiscCloseDiag_Cnt_str      |

## Program(fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

| Constant Name             | Resolution             | Units    | Value |
|---------------------------|------------------------|----------|-------|
| D_VDISCHMAXFACTOR_ULS_F32 | Single Precision Float | Unitless | 1.05  |
| D_VDISCHMINFACTOR_ULS_F32 | Single Precision Float | Unitless | 0.95  |
| D_PWRDISCCONFIGB_CNT_U08  | 1                      | Count    | 2     |

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

| Constant Name                                        |
|------------------------------------------------------|
| STD_LOW                                              |
| STD_HIGH                                             |
| D_ZERO_CNT_U16                                       |
| RTE_E_OK (0) - see Data Dictionary                   |
| D_PWRDISCCONFIGURATION_CNT_U08 - see Data Dictionary |

### Module specific Lookup Tables Constants

| Constant Name | Resolution | Value | Software Segment |
|---------------|------------|-------|------------------|
| None          |            |       |                  |

#  Functions/Macros used by the Sub-Modules 

## Library Functions / Macros 

The library and functions / Macros that are called by the various sub
modules are identified below,

1.  Abs_f32_m

2.  Min_m

3.  DiagPStep_m

4.  DiagNStep_m

5.  DiagFailed_m

## Data Hiding Functions

1.  Rte_Call_SystemTime_GetSystemTime_mS_u32

2.  Rte_Call_SystemTime_DtrmnElapsedTime_mS_u16

3.  Rte_Call_NxtrDiagMgr_SetNTCStatus

4.  Rte_Call_Vbatt_Batt_V_f32

5.  Rte_Call_Vswitch_BattSwitched_V_f32

6.  Rte_Call_PhyCapPrecharge_OP_SET

7.  Rte_Call_PhyCapDischarge_OP_SET

## Global Functions/Macros Defined by this Module

None

# Software Module Implementation

## Runtime Environment (RTE) Initial Values

This section lists the initial values of data written by this module but
controlled by the RTE. After RTE initialization, the data in this table
will contain these values.

| Data                                                  | Value |
|-------------------------------------------------------|-------|
| Rte_InitValue_MotorVelocityMRFUnfiltered_MtrRadpS_f32 | 0     |
| Rte_InitValue_OVERRIDESIGDIAGADC_Volt_f32             | 0     |
| Rte_InitValue_PMOSDIAGADC_Volt_f32                    | 0     |
| Rte_InitValue_PwrDiscATestComplete_Cnt_lgc            | FALSE |
| Rte_InitValue_PwrDiscATestStart_Cnt_lgc               | FALSE |
| Rte_InitValue_PwrDiscBTestComplete_Cnt_lgc            | FALSE |
| Rte_InitValue_PwrDiscBTestStart_Cnt_lgc               | FALSE |
| Rte_InitValue_PwrDiscClosed_Cnt_lgc                   | FALSE |

## Initialization Functions

None

##  Periodic Functions

### Per: BkCpPc_Per1

#### Design Rationale

##### Threshold Cal for setting NTC by PN Stepping logic was not defined in the FDD 11B. Only Pstep and Nstep cals were defined. Threshold cal was added as k_VerifyPwrDiscCloseDiag_Cnt_str.Threshold and defined in Data Dictionary.

##### No information in FDD for clearing NTCs. But code has the logic for example in switch case BULKCAP_VERIFYCLOSE to clear the NTCs if PowerRelayInitFltFailed_Cnt_M_lgc = False.

#### Program Flow Start

Rte_Call_BkCpPc_Per1_CP0_CheckpointReached()

#### Store Module Inputs to Local copies

MotorVelocityMRFUnfiltered_MtrRadpS_T_f32 =
Rte_IRead_BkCpPc_Per1_MotorVelocityMRFUnfiltered_MtrRadpS_f32()

OVERRIDESIGDIAGADC_Volt_T_f32 =
Rte_IRead_BkCpPc_Per1_OVERRIDESIGDIAGADC_Volt_f32()

PMOSDIAGADC_Volt_T_f32 = Rte_IRead_BkCpPc_Per1_PMOSDIAGADC_Volt_f32()

PwrDiscATestStart_Cnt_T_lgc =
Rte_IRead_BkCpPc_Per1_PwrDiscATestStart_Cnt_lgc()

PwrDiscBTestStart_Cnt_T_lgc =
Rte_IRead_BkCpPc_Per1_PwrDiscBTestStart_Cnt_lgc()

Vbatt_Volts_T_f32 = Rte_IRead_BkCpPc_Per1_Batt_Volt_f32()

Vswitch_Volts_T_f32 = Rte_IRead_BkCpPc_Per1_BattSwitched_Volt_f32()

#### Motor Motion Check, Calculate Delta Voltage

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/BkCpPc/doc/mediax/media/image2.emf)

#### Determine State

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/BkCpPc/doc/mediax/media/image3.emf)

#### State – Wait for Start A

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/BkCpPc/doc/mediax/media/image4.emf)

#### State – Verify Disconnect Open

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/BkCpPc/doc/mediax/media/image5.emf)

#### State – Wait for Square Wave

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/BkCpPc/doc/mediax/media/image6.emf)

#### State – Bulk Capacitor Precharge

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/BkCpPc/doc/mediax/media/image7.emf)

#### State – Wait for Start B

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/BkCpPc/doc/mediax/media/image8.emf)

#### State – Post Close Power Disconnect

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/BkCpPc/doc/mediax/media/image9.emf)

#### State – Verify Power Disconnect Closed

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/BkCpPc/doc/mediax/media/image10.emf)

#### State – Run Time Diagnostics

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/BkCpPc/doc/mediax/media/image11.emf)

#### Store Local copy of outputs into Module Outputs

Rte_IWrite_BkCpPc_Per1_PwrDiscATestComplete_Cnt_lgc(PwrDiscATestComplete_Cnt_M_lgc)

Rte_IWrite_BkCpPc_Per1_PwrDiscBTestComplete_Cnt_lgc(PwrDiscBTestComplete_Cnt_M_lgc)

Rte_IWrite_BkCpPc_Per1_PwrDiscClosed_Cnt_lgc(PwrDiscClosed_Cnt_M_lgc)

#### Program Flow End

Rte_Call_BkCpPc_Per1_CP1_CheckpointReached()

##  Fault Recovery Functions

None

## Shutdown Functions

None

## Interrupt Functions

None

## Serial Communication Functions

None

## Server Functions

### OP_SET: CapPcDcStub

#### Design Rationale

The digital output ports PhyCapDischarge_OP_SET and
PhyCapPrecharge_OP_SET that are applicable only to Configuration B
require a client/server port in Davinci Developer. However, for programs
that only supports Configuration A, where these physical capacitor pins
are NOT available, the Developer tool flags an error during integration
of the component, since the client server ports are not connected. This
server function stub will be connected to both the Client/Server ports,
PhyCapDischarge_OP_SET and PhyCapPrecharge_OP_SET, to avoid the
configuration error flaged by the Davinci Developer tool during
integration.

#### Program Flow Start

N/A

#### Store Module Inputs to Local copies

None

#### Capacitor Discharge/Precharge server stub – for Configuration A

<table>
<colgroup>
<col style="width: 21%" />
<col style="width: 37%" />
<col style="width: 14%" />
<col style="width: 7%" />
<col style="width: 11%" />
<col style="width: 6%" />
</colgroup>
<tbody>
<tr class="odd">
<td>CapPcDcStub_OP_SET</td>
<td></td>
<td>Type</td>
<td>Min</td>
<td>Max</td>
<td>UTP Tol.</td>
</tr>
<tr class="even">
<td><strong>Arguments Passed</strong></td>
<td>signal</td>
<td><p>Uint8</p>
<p>(<mark>IoHwAb_BoolType</mark> is a <strong>uint8</strong>)</p></td>
<td>0</td>
<td>1</td>
<td>0</td>
</tr>
<tr class="odd">
<td><strong>Return Value</strong></td>
<td>RTE_E_OK</td>
<td>Uint8</td>
<td>0</td>
<td>0</td>
<td>0</td>
</tr>
</tbody>
</table>

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/BkCpPc/doc/mediax/media/image12.emf)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

N/A

## Transition Functions

### Trns: BkCpPc_Trns1

#### Design Rationale

None

#### Program Flow Start

N/A

#### Store Module Inputs to Local copies

None

#### Set Outputs to Safe Conditions

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/BkCpPc/doc/mediax/media/image13.emf)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

N/A

### Trns: BkCpPc_Trns2

#### Design Rationale

None

#### Program Flow Start

N/A

#### Store Module Inputs to Local copies

None

#### Initialize Outputs

None

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/BkCpPc/doc/mediax/media/image14.emf)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

N/A

##  

# Execution Requirements

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

| Function Name      | Calling Frequency | System State(s) in which the function is called |
|--------------------------|-----------------|------------------------------|
| BkCpPc_Per1        | 2 ms              | WARMINIT, OPERATE                               |
| BkCpPc_Trns1       | On Event          | On Entering DISABLE                             |
| BkCpPc_Trns2       | On Event          | On Entering WARMINIT                            |
| CapPcDcStub_OP_SET | N/A – stub only   | N/A – stub only                                 |

## Execution Requirements for Serial Communication Functions 

| Function Name | Sub-Module called by (Serial Comm Function Name) |
|---------------|--------------------------------------------------|
| None          |                                                  |

#  [section-1]

#  Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

| Name of Sub Module | Software Segment                  |
|--------------------|-----------------------------------|
| BkCpPc_Per1        | RTE_START_SEC_SA_BKCPPC_APPL_CODE |
| BkCpPc_Trns1       | RTE_START_SEC_SA_BKCPPC_APPL_CODE |
| BkCpPc_Trns2       | RTE_START_SEC_SA_BKCPPC_APPL_CODE |
| CapPcDcStub_OP_SET | RTE_START_SEC_SA_BKCPPC_APPL_CODE |

##  [section-2]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

| Name of Sub Module | Software Segment |
|--------------------|------------------|
| None               |                  |

#  [section-3]

#  Known Issues / Limitations With Design

1.  INLINE functions defined in GlobalMacro.h are not unit tested.

#  Revision Control Log

|             |            |                                                                         |            |                     |
|------|------|--------------------------------------------|---------|---------|
| **Item \#** | **Rev \#** | **Change Description**                                                  | **Date**   | **Author Initials** |
| 1           | 1.0        | Initial Version (FDD 11B v001)                                          | 13-Sep-12  | OT                  |
| 2           | 2.0        | UTP Updates                                                             | 20-Sep-12  | OT                  |
| 3           | 3.0        | Added Trns2 function to initialize startup sequence                     | 27-Sep-12  | OT                  |
| 4           | 4.0        | Anomaly 3912 – write outputs in all branches                            | 24-Oct-12  | OT                  |
| 5           | 5.0        | Added checkpoint statements                                             | 21-Nov-12  | OT                  |
| 6           | 6.0        | Updated to version 3 FDD 11B                                            | 28-Feb-13  | Selva               |
| 7           | 7.0        | Set RunTimeFaultAcc_Cnt_M_u16 to zero in tans 2                         | 1-Mar-13   | Selva               |
| 8           | 8.0        | Anomaly 5092 – add power disconnect configurable parameter              | 29-May-13  | BDO                 |
| 9           | 9.0        | Anomaly 5122 – updates to address integration issues                    | 04-June-13 | BDO                 |
| 10          | 10.0       | Set PwrDiscATestComplete in BULKCAP_PRECHARGE state for Configuration A | 05-June-13 | BDO                 |
| 11          | 11.0       | Updated to add clarification for unit testing.                          | 21-June-13 | BDO                 |
| 12          | 12.0       | Flowcharts updated to show fixes for anomalies 5150 and 5763            | 1-Nov-13   | KMC                 |
| 13          | 13.0       | Updated flowcharts to remove trailing if else statements                | 7-Jan-14   | LK                  |
| 14          | 14.0       | Updated flowcharts to meet rev 05 of the FDD 11B                        | 19-Mar-14  | LK                  |

{% endraw %}