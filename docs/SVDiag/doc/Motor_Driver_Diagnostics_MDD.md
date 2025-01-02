---
layout: default
title: Motor_Driver_Diagnostics_MDD
nav_order: 3
parent: Component
---
{% raw %}
# Module -- Motor Driver Diagnostics [module----motor-driver-diagnostics]

# High-Level Description

This function operates as a reporting mechanism for all Gate Drive
faults.

# Figures

## Component Diagram

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SVDiag/doc/mediax/media/image2.png"
style="width:2.43056in;height:2.11439in" />

#  Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

| Module Inputs            | Module Outputs |                              |
|--------------------------|----------------|------------------------------|
|                          |                | FETFaultPhase_Cnt_enum       |
| MtrDrvrInitStart_Cnt_lgc |                | FETFaultType_Cnt_enum        |
|                          |                | MtrDrvrInitComplete_Cnt_lgc  |
|                          |                | GateDriveResetActive_Cnt_lgc |

## Module Internal Variables

This section identifies the name, range and resolutions for module
specific data created by this module. If there are no range restrictions
on the variable, the term “FULL” is placed into the table for legal
range.

<table>
<colgroup>
<col style="width: 30%" />
<col style="width: 11%" />
<col style="width: 15%" />
<col style="width: 13%" />
<col style="width: 30%" />
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
<td>SVDiag_MtrDrvInitStartTime_mS_M_u32p0</td>
<td>uint32</td>
<td>FULL</td>
<td>FULL</td>
<td>MTRDRVDIAG_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>SVDiag_ResetWaitLoop_Cnt_M_lgc</td>
<td>boolean</td>
<td>FALSE</td>
<td>TRUE</td>
<td>MTRDRVDIAG_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="odd">
<td>SVDiag_GateDrvFltSts_Cnt_D_b16</td>
<td>uint16</td>
<td>FULL</td>
<td>FULL</td>
<td>MTRDRVDIAG_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td>SVDiag_MtrDrvInitActive_Cnt_M_lgc</td>
<td>boolean</td>
<td>FALSE</td>
<td>TRUE</td>
<td>MTRDRVDIAG_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="odd">
<td>SVDiag_FETFaultType_Cnt_M_enum</td>
<td>FETFAULTTYPE_ENUM</td>
<td colspan="2">NOFAULT , LOWER , UPPER</td>
<td>MTRDRVDIAG_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="even">
<td>SVDiag_FETFaultPhase_Cnt_M_enum</td>
<td>FETPHASETYPE_ENUM</td>
<td colspan="2">NOPHASE, PHASEA , PHASEB , PHASEC</td>
<td>MTRDRVDIAG_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="odd">
<td>SVDiag_GateDriveFltAcc_Cnt_M_u16</td>
<td>uint16</td>
<td>FULL</td>
<td>FULL</td>
<td>MTRDRVDIAG_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td>SVDiag_GenGateDriveFltAcc_Cnt_M_u16</td>
<td>uint16</td>
<td>0</td>
<td>200</td>
<td>MTRDRVDIAG_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="odd">
<td>SVDiag_MtrDrvInitComp_Cnt_M_lgc</td>
<td>boolean</td>
<td>FALSE</td>
<td>TRUE</td>
<td>MTRDRVDIAG_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="even">
<td>SVDiag_OnStateFltAcc_Cnt_M_u16</td>
<td>uint16</td>
<td>FULL</td>
<td>FULL</td>
<td>MTRDRVDIAG_START_SEC_VAR_CLEARED_16</td>
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
<td>&lt;None&gt;</td>
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

| Constant Name           |
|-------------------------|
| k_GateDriveDiag_Cnt_str |
|                         |
|                         |
| k_OnStateDiag_Cnt_str   |

## Program(fixed) Constants

### Embedded Constants

#### Local

| Constant Name                    | Resolution | Units        | Value   |
|----------------------------------|------------|--------------|---------|
| D_PHASEALOWER_CNT_U16            | uint16     | Counts       | 0U      |
| D_PHASEBLOWER_CNT_U16            | uint16     | Counts       | 1U      |
| D_PHASECLOWER_CNT_U16            | uint16     | Counts       | 2U      |
| D_PHASEAUPPER_CNT_U16            | uint16     | Counts       | 3U      |
| D_PHASEBUPPER_CNT_U16            | uint16     | Counts       | 4U      |
| D_PHASECUPPER_CNT_U16            | uint16     | Counts       | 5U      |
| D_VREGUV_CNT_U16                 | uint16     | Counts       | 6U      |
| D_BTSTRPAUV_CNT_U16              | uint16     | Counts       | 7U      |
| D_BTSTRPBUV_CNT_U16              | uint16     | Counts       | 8U      |
| D_BTSTRPCUV_CNT_U16              | uint16     | Counts       | 9U      |
| D_NUMOFGDSTATUSBITS_CNT_U16      | uint16     | Counts       | 10U     |
| D_STATUSALOWER_CNT_B16           | uint16     | Counts       | 0x0001U |
| D_STATUSBLOWER_CNT_B16           | uint16     | Counts       | 0x0002U |
| D_STATUSCLOWER_CNT_B16           | uint16     | Counts       | 0x0004U |
| D_STATUSAUPPER_CNT_B16           | uint16     | Counts       | 0x0008U |
| D_STATUSBUPPER_CNT_B16           | uint16     | Counts       | 0x0010U |
| D_STATUSCUPPER_CNT_B16           | uint16     | Counts       | 0x0020U |
| D_STATUSVREGUV_CNT_B16           | uint16     | Counts       | 0x0040U |
| D_STATUSBTSTRPAUV_CNT_B16        | uint16     | Counts       | 0x0080U |
| D_STATUSBTSTRPBUV_CNT_B16        | uint16     | Counts       | 0x0100U |
| D_STATUSBTSTRPCUV_CNT_B16        | uint16     | Counts       | 0x0200U |
| D_STATUSVDDUV_CNT_B16            | uint16     | Counts       | 0x0400U |
| D_STATUSOVERTEMP_CNT_B16         | uint16     | Counts       | 0x8000U |
| D_FFDATACLKTIME_US_U16P0         | uint16     | Microseconds | 4.0     |
| D_GDRESETTIME_US_U16P0           | uint16     | Microseconds | 2.0     |
| D_MTRDRVINITDELAY_MS_U08         | Uint8      | Milliseconds | 10U     |
| D_GATEDRVCOMMLOSSACCTHRS_CNT_U16 | uint16     | Milliseconds | 100U    |

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

1.  FPM_InitFixedPoint_m

2.  DiagNStep_m

3.  DiagPStep_m

4.  DiagFailed_m

## Data Hiding Functions

1.  Rte_Call_FetDrvReset_OP_SET

2.  Rte_Call_FetFlt1Data_OP_GET

3.  Rte_Call_FetFlt2Clk_OP_GET

4.  Rte_Call_FetFlt2Clk_OP_SET

5.  Rte_Call_IoHwAbPortConfig_SetFetFlt2ToOutput

6.  Rte_Call_NxtrDiagMgr_GetEventFailed

7.  Rte_Call_NxtrDiagMgr_SetNTCStatus

8.  Rte_Call_SystemTime_DtrmnElapsedTime_mS_u16

9.  Rte_Call_SystemTime_DtrmnElapsedTime_uS_u16

10. Rte_Call_SystemTime_GetSystemTime_mS_u32

11. Rte_Call_SystemTime_GetSystemTime_uS_u32

12. SuspendAllInterrupts

13. ResumeAllInterrupts

## Global Functions/Macros Defined by this Module

\<None\>

## Local Functions/Macros Used by this MDD only

### MotorDriverInit

|                      |                          |         |       |      |
|----------------------|--------------------------|---------|-------|------|
| **Function Name**    | MotorDriverInit          | Type    | Min   | Max  |
| **Arguments Passed** | void                     | N/A     | N/A   | N/A  |
| **Return Value**     | MtrDrvInitComp_Cnt_T_lgc | boolean | FALSE | TRUE |

#### Design Rationale

On gate drive startup there is the possibility of its fault register
logging fault bits related to startup. In order to clear these bits the
gate drive is reset. Once called, this operation shall wait a time
period defined by k_GateDrvInitDwellTime_mS_u16p0. Once elapsed, the
operation will pulse the Reset line low for nominally 1 uSec. Once done
this operation will return MtrDrvInitComp_Cnt_T_lgc = TRUE.

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SVDiag/doc/mediax/media/image3.emf)

###  ProcGateDriveFlt

|                      |                              |                        |       |      |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | ProcGateDriveFlt             | Type                   | Min   | Max  |
| **Arguments Passed** | GateDriveFltAccPtr_Cnt_T_u16 | pointer to type uint16 | FULL  | FULL |
|                      | FF2Set_Cnt_T_lgc             | Boolean                | FALSE | TRUE |
| **Return Value**     | Void                         | N/A                    | N/A   | N/A  |

#### Design Rationale

This function processes gate drive fault.

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SVDiag/doc/mediax/media/image4.emf)

### ProcBridgeFlt

|                      |                                 |                        |      |      |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | ProcBridgeFlt                   | Type                   | Min  | Max  |
| **Arguments Passed** | OnStateFltAccPtr_Cnt_T_u16      | pointer to type uint16 | FULL | FULL |
|                      | GenGateDriveFltAccPtr_Cnt_T_u16 | pointer to type uint16 | 0    | 200  |
| **Return Value**     | Void                            | N/A                    | N/A  | N/A  |

#### Design Rationale

This function processes bridge fault.

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SVDiag/doc/mediax/media/image5.emf)

### ReadMtrDrvFltData

|                      |                         |                        |      |      |
|---------------|--------------------------|---------------|---------|---------|
| **Function Name**    | ReadMtrDrvFltData       | Type                   | Min  | Max  |
| **Arguments Passed** | StatusPtr_Cnt_T_b16     | pointer to type uint16 | FULL | FULL |
| **Return Value**     | FaultedPhases_Cnt_T_u16 | uint16                 | FULL | FULL |

#### Design Rationale

#### The gate drive IC’s fault register is read serially through the fault flag lines. This is done by clocking the *FetFlt2* line and reading in the data on *FetFlt1* .  [the-gate-drive-ics-fault-register-is-read-serially-through-the-fault-flag-lines.-this-is-done-by-clocking-the-fetflt2-line-and-reading-in-the-data-on-fetflt1-.]

#### The clock signal will have a 500 kHz max frequency. At that clock frequency the interface circuit shall ensure a minimum positive and negative pulse width at the gate drive input of 750 nSec minimum. Data is clocked out on the gate drive on the falling edge of its clock input. This data is to be present at the DSP input for 250 nSec prior to the rising edge of the clock. [the-clock-signal-will-have-a-500-khz-max-frequency.-at-that-clock-frequency-the-interface-circuit-shall-ensure-a-minimum-positive-and-negative-pulse-width-at-the-gate-drive-input-of-750-nsec-minimum.-data-is-clocked-out-on-the-gate-drive-on-the-falling-edge-of-its-clock-input.-this-data-is-to-be-present-at-the-dsp-input-for-250-nsec-prior-to-the-rising-edge-of-the-clock.]

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SVDiag/doc/mediax/media/image6.emf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SVDiag/doc/mediax/media/image7.emf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SVDiag/doc/mediax/media/image8.emf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SVDiag/doc/mediax/media/image9.emf)

**  
**

### ResetGateDrive

|                      |                |      |     |     |
|----------------------|----------------|------|-----|-----|
| **Function Name**    | ResetGateDrive | Type | Min | Max |
| **Arguments Passed** | void           | N/A  | N/A | N/A |
| **Return Value**     | void           | N/A  | N/A | N/A |

#### Design Rationale

This function will pulse the Reset line low for nominally 1 uSec. This
will clear the fault logging register fault bits. An exclusive area is
used around this timing to prevent this function from being interrupted
during the wait period, as a pulse for longer than 3.5uSec will put the
gate drive chip into a sleep mode.

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SVDiag/doc/mediax/media/image10.emf)

### GateDrvWaitTime

|                      |                       |        |      |      |
|----------------------|-----------------------|--------|------|------|
| **Function Name**    | GateDrvWaitTime       | Type   | Min  | Max  |
| **Arguments Passed** | TimeToWait_uS_T_u16p0 | uint16 | FULL | FULL |
| **Return Value**     | void                  | N/A    | N/A  | N/A  |

#### Design Rationale

The purpose of this function is to provide the delay times required for
the bit manipulation used in this module. This function will wait the
amount of time in uS of the variable passed into the function.

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SVDiag/doc/mediax/media/image11.emf)

# Software Module Implementation

## Runtime Environment (RTE) Initial Values

This section lists the initial values of data written by this module but
controlled by the RTE. After RTE initialization, the data in this table
will contain these values.

| Data                                      | Value |
|-------------------------------------------|-------|
|                                           |       |
| FETFaultPhase_Cnt_enum                    | 0     |
| FETFaultType_Cnt_enum                     | 0     |
| Rte_InitValue_MtrDrvrInitComplete_Cnt_lgc | FALSE |
| Rte_InitValue_MtrDrvrInitStart_Cnt_lgc    | FALSE |
| GateDriveResetActive_Cnt_lgc              | FALSE |

## Initialization Functions

None

##  Periodic Functions

### Per: MtrDrvDiag_Per1

#### Design Rationale

The Motor Driver Diagnostic Periodic Processing operation systematically
deals with the motor driver diagnostics. Each failure diagnosed by the
gate drive IC has to be fully qualified by the DSP before a fault is
considered present. The qualification process used in this design is the
typical PStep/Nstep fault accumulator method. This design uses an
assumption that each of the individual faults detected by the gate drive
IC rarely occurs. Therefore it is not necessary to track through
individual fault accumulators for each of the fault indications provided
by the gate drive. Instead the faults will be placed into two groups,
gate drive faults and FET faults each with their own fault accumulator.
For gate drive faults there is no need to identify the exact failure
mode. For FET faults the exact FET failure mode is to be learned but is
not required until the FET fault has been fully qualified by the DSP.
This function will read in the gate drive fault register. Fault
conditions detected by gate drive IC are communicated through two dual
purpose fault flag lines, FF1 and FF2. The first purpose of the fault
flag lines is to indicate a fault is present. The second purpose is to
serially transfer an internal fault register indicating which fault was
present.

#### Program Flow Start

Rte_Call_MtrDrvDiag_Per1_CP0_CheckpointReached()

#### Store Module Inputs to Local copies

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SVDiag/doc/mediax/media/image12.emf)

####  Processing of function

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SVDiag/doc/mediax/media/image13.emf)

#### Store Local copy of outputs into Module Outputs

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SVDiag/doc/mediax/media/image14.emf)

#### Program Flow End

Rte_Call_MtrDrvDiag_Per1_CP1_CheckpointReached()

### Per: MtrDrvDiag_Per2

#### Design Rationale

Configurable checkpoints were not added to this periodic since it
doesn’t run in all system states and the current requirements for
program flow check require the checkpoint to be called in all system
states if it is to be used.

#### Program Flow Start

None

#### Store Module Inputs to Local copies

N/A

#### Processing

Rte_Call_FetDrvReset_OP_SET(STD_LOW)

#### Store Local copy of outputs into Module Outputs

#### Program Flow End

N/A

### Per: MtrDrvDiag_Trns1

#### Design Rationale

This function reinitializes variables on entering WARMINIT state.

#### Program Flow Start

None

#### Processing of function

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SVDiag/doc/mediax/media/image15.emf)

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

## Execution Rates for sub-modules called by the Scheduler

| Function Name    | Calling Frequency             | System State(s) in which the function is called |
|--------------------------|-----------------|------------------------------|
| MtrDrvDiag_Per1  | 2mS                           | OPERATE, WARMINIT                               |
| MtrDrvDiag_Per2  | 2mS                           | DISABLE, OFF                                    |
| MtrDrvDiag_Trns1 | Triggered on state transition | On entering WARMINIT                            |

## Execution Requirements for Serial Communication Functions 

| Function Name | Sub-Module called by (Serial Comm Function Name) |
|---------------|--------------------------------------------------|
| \<None\>      |                                                  |

#  [section-1]

#  Memory Map Definition Requirements

## Sub Modules (Functions)

| Name of Sub Module | Software Segment |
|--------------------|------------------|
| MtrDrvDiag_Per1    |                  |
| MtrDrvDiag_Per2    |                  |
| MtrDrvDiag_Trns1   |                  |

##  [section-2]

## Local Functions

| Name of Sub Module | Software Segment   |
|--------------------|--------------------|
| ProcGateDriveFlt   | SA_MTRDRVDIAG_CODE |
| ProcBridgeFlt      | SA_MTRDRVDIAG_CODE |
| ReadMtrDrvFltData  | SA_MTRDRVDIAG_CODE |
| ResetGateDrive     | SA_MTRDRVDIAG_CODE |
| GateDrvWaitTime    | SA_MTRDRVDIAG_CODE |
| MotorDriverInit    | SA_MTRDRVDIAG_CODE |

#  [section-3]

#  Known Issues / Limitations With Design

1.  ReadMtrDrvFltData needs to be updated to support manual control of
    the NHET outputs when a faulted FET is detected.

#  Revision Control Log

|             |            |                                                                               |            |                     |
|------|------|--------------------------------------------|---------|---------|
| **Item \#** | **Rev \#** | **Change Description**                                                        | **Date**   | **Author Initials** |
| 1           | 1.0        | Initial MDD                                                                   | 24-May-11  | BG                  |
| 2           | 2.0        | Replaced exclusive area with suspend and resume interrupts                    | 20-June-11 | LWW                 |
| 3           | 3          | Corrected Rte Call to GetEventFailed server in ProcBridgeFlt local function   | 02-Dec-11  | JJW                 |
| 4           | 4          | Added functionality for Hardware Power Up                                     | 19-Sep-12  | OT                  |
| 5           | 5          | UTP Update (hard-coded NTC numbers)                                           | 20-Sep-12  | OT                  |
| 6           | 6          | Added checkpoints and memmap software segment is updated for static variables | 28-Sep-12  | Selva               |
| 7           | 7          | Added Per2 per anomaly 4578                                                   | 25-Apr-13  | LWW                 |
| 8           | 8          | Updated range on GenGateDrv fault accumulator                                 | 17-May-13  | LWW                 |
| 9           | 9          | Fixed A4155 . Changes made to ReadMtrDrvFltData                               | 28-aug-13  | Selva               |
| 10          | 10         | Updated module and display variables with SVDiag                              | 8-Oct-13   | VT                  |
| 11          | 11         | Updated to FDD V008                                                           | 1-Dec-14   | Rijvi               |

{% endraw %}