---
layout: default
title: Temporal_Monitor_MDD
nav_order: 4
parent: Temporal Monitoring
---
{% raw %}
# Module --  [module---]

# High-Level Description

This module helps ensure valid execution time for the forward path. It
generates the rising edge of the monitor signal used by an external
processor to determine execution time, performs an initialization
routine for the external TMF processor, and performs run time
diagnostics for the TMF processor.

# Figures

## Component Diagram

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/TmprlMon/doc/mediax/media/image1.png"
style="width:2.24375in;height:2.24375in" />

#  Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

| Module Inputs        | Module Outputs |                         |
|----------------------|----------------|-------------------------|
| TMFTestStart_Cnt_lgc |                | TMFTestComplete_Cnt_lgc |

## Module Internal Variables

This section identifies the name, range and resolutions for module
specific data created by this module. If there are no range restrictions
on the variable, the term “FULL” is placed into the table for legal
range.

<table>
<colgroup>
<col style="width: 27%" />
<col style="width: 20%" />
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
<td>TmprlMonSt_Cnt_M_enum</td>
<td>DT_TmprlMonSt</td>
<td>n/a</td>
<td>n/a</td>
<td>TMPRLMON_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="even">
<td>InitTestStatus_Cnt_M_enum</td>
<td>NxtrDiagMgrStatus</td>
<td>n/a</td>
<td>n/a</td>
<td>TMPRLMON_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="odd">
<td>NTCStatusByte_Cnt_M_u08</td>
<td>1</td>
<td>0</td>
<td>13</td>
<td>TMPRLMON_START_SEC_VAR_CLEARED_8</td>
</tr>
<tr class="even">
<td>InitialTime_mS_M_u32</td>
<td>1</td>
<td>0</td>
<td>2<sup>32</sup> - 1</td>
<td>TMPRLMON_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>TMFTestComplete_Cnt_M_lgc</td>
<td>1</td>
<td>FALSE</td>
<td>TRUE</td>
<td>TMPRLMON_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="even">
<td>TMFPrepCheckFlag_Cnt_M_lgc</td>
<td>1</td>
<td>FALSE</td>
<td>TRUE</td>
<td>TMPRLMON_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>TmprlMonPNAccum_Cnt_M_u16</td>
<td>1</td>
<td>0</td>
<td>1000</td>
<td>TMPRLMON_START_SEC_VAR_CLEARED_16</td>
</tr>
</tbody>
</table>

### User defined typedef definition/declaration 

This section documents any user types uniquely used for the module.

<table>
<colgroup>
<col style="width: 29%" />
<col style="width: 30%" />
<col style="width: 20%" />
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
<tr class="odd">
<td>DT_TmprlMonSt</td>
<td><p>TMPMON_RESET1 (0U)</p>
<p>TMPMON_INIT_ALLOFF1 (1U)</p>
<p>TMPMON_INIT_TMOFF1 (2U)</p>
<p>TMPMON_INIT_PICINIT1 (3U)</p>
<p>TMPMON_INIT_SF2OFF (4U)</p>
<p>TMPMON_INIT_ALLON2 (5U)</p>
<p>TMPMON_INIT_SF3OFF (6U)</p>
<p>TMPMON_INIT_ALLON3 (7U)</p>
<p>TMPMON_INIT_TMOFF2 (8U)</p>
<p>TMPMON_RESET2 (9U)</p>
<p>TMPMON_INIT_ALLOFF2 (10U)</p>
<p>TMPMON_INIT_SF23OFF (11U)</p>
<p>TMPMON_INIT_PICINIT2 (12U)</p>
<p>TMPMON_OPERATE (13U)</p>
<p>TMPMON_PREPCHECK (14U)</p></td>
<td>uint8</td>
<td>0</td>
<td>14</td>
</tr>
<tr class="even">
<td rowspan="7">TmprlMonState_Str</td>
<td>SysFault3Cmd_lgc</td>
<td>IoHwAb_BoolType</td>
<td>0</td>
<td>1</td>
</tr>
<tr class="odd">
<td>SysFault2Cmd_lgc</td>
<td>IoHwAb_BoolType</td>
<td>0</td>
<td>1</td>
</tr>
<tr class="even">
<td>WdMonitorCmd_lgc</td>
<td>IoHwAb_BoolType</td>
<td>0</td>
<td>1</td>
</tr>
<tr class="odd">
<td>WdResetCmd_lgc</td>
<td>IoHwAb_BoolType</td>
<td>0</td>
<td>1</td>
</tr>
<tr class="even">
<td>FetDrvCntlFdbk_lgc</td>
<td>IoHwAb_BoolType</td>
<td>0</td>
<td>1</td>
</tr>
<tr class="odd">
<td>PwrSwitchEnFdbk_lgc</td>
<td>IoHwAb_BoolType</td>
<td>0</td>
<td>1</td>
</tr>
<tr class="even">
<td>StepTime_mS_u16</td>
<td>uint16</td>
<td>0</td>
<td>2<sup>16</sup> - 1</td>
</tr>
</tbody>
</table>

# Constant Data Dictionary

## Calibration Constants

This section lists the calibrations used by the module. For details on
calibration constants, refer to the Data Dictionary for the application.

| Constant Name |
|---------------|
| \<None\>      |

## Program(fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

| Constant Name    | Resolution | Units  | Value |
|------------------|------------|--------|-------|
| TMPMON_NUMSTATES | 1          | Counts | 14U   |

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

| Constant Name |
|---------------|
| STD_LOW       |
| STD_HIGH      |

### Module specific Lookup Tables Constants

<table>
<colgroup>
<col style="width: 27%" />
<col style="width: 57%" />
<col style="width: 14%" />
</colgroup>
<thead>
<tr class="header">
<th>Constant Name</th>
<th>Value</th>
<th>Software Segment</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>TmprlMonStateTbl_Cnt_M_Str[TMPMON_NUMSTATES]</td>
<td><p>{{STD_LOW, STD_LOW, STD_LOW, STD_LOW, STD_LOW, STD_LOW, 4U},</p>
<p>{STD_LOW, STD_LOW, STD_LOW, STD_HIGH, STD_LOW, STD_LOW, 31U},</p>
<p>{STD_HIGH, STD_HIGH, STD_LOW, STD_HIGH, STD_LOW, STD_LOW, 1U},</p>
<p>{STD_HIGH, STD_HIGH, STD_HIGH, STD_HIGH, STD_HIGH, STD_HIGH,
40U},</p>
<p>{STD_HIGH, STD_LOW, STD_HIGH, STD_HIGH, STD_LOW, STD_LOW, 1U},</p>
<p>{STD_HIGH, STD_HIGH, STD_HIGH, STD_HIGH, STD_HIGH, STD_HIGH, 1U},</p>
<p>{STD_LOW, STD_HIGH, STD_HIGH, STD_HIGH, STD_LOW, STD_LOW, 1U},</p>
<p>{STD_HIGH, STD_HIGH, STD_HIGH, STD_HIGH, STD_HIGH, STD_HIGH, 1U},</p>
<p>{STD_HIGH, STD_HIGH, STD_LOW, STD_HIGH, STD_LOW, STD_LOW, 24U},</p>
<p>{STD_LOW, STD_LOW, STD_LOW, STD_LOW, STD_LOW, STD_LOW, 1U},</p>
<p>{STD_LOW, STD_LOW, STD_LOW, STD_HIGH, STD_LOW, STD_LOW, 31U},</p>
<p>{STD_LOW, STD_LOW, STD_HIGH, STD_HIGH, STD_LOW, STD_LOW, 24U},</p>
<p>{STD_HIGH, STD_HIGH, STD_HIGH, STD_HIGH, STD_HIGH, STD_HIGH,
16U},</p>
<p>{STD_HIGH, STD_HIGH, STD_HIGH, STD_HIGH, STD_HIGH, STD_HIGH, 0U},</p>
<p>{STD_LOW, STD_LOW, STD_LOW, STD_LOW, STD_HIGH, STD_LOW, 0U}}</p></td>
<td>TMPRLMON_START_SEC_CONST_UNSPECIFIED</td>
</tr>
</tbody>
</table>

#  Functions/Macros used by the Sub-Modules 

## Library Functions / Macros 

The library and functions / Macros that are called by the various sub
modules are identified below,

1.  \<None\>

## Data Hiding Functions

1.  \<None\>

## Global Functions/Macros Defined by this Module

None

## Local Functions/Macros Used by this MDD only

None

# Software Module Implementation

## Runtime Environment (RTE) Initial Values

This section lists the initial values of data written by this module but
controlled by the RTE. After RTE initialization, the data in this table
will contain these values.

| Data                                  | Value |
|---------------------------------------|-------|
| Rte_InitValue_TMFTestComplete_Cnt_lgc | FALSE |
| Rte_InitValue_TMFTestStart_Cnt_lgc    | FALSE |

## Initialization Functions

None

##  Periodic Functions

### Per: \_Per1

#### Design Rationale

This function generates the rising edge of the WdMonitor signal. ***It
must be mapped in the forward path*** after the ADC sampling, and before
the rest of the forward path calculations.

The FDD requires that a lookup should be performed based on the current
TMF state to determine whether to set the WdMonitor signal to a high
state. Then, if this is true, the signal is set high. Otherwise, it is
not set.

Instead, the WdMonitor signal is set to the lookup value itself. This
way, when the WdMonitor signal is enabled, it will be set high (and set
low when disabled). Functionally, this fulfills the FDD requirements
(with the assumption that TmprlMon_Per1 and TmprlMon_Per2 are the only
functions that affect the state of the WdMonitor signal).

#### Program Flow Start

Rte_Call_TmprlMon_Per1_CP0_CheckpointReached()

#### Store Module Inputs to Local copies

None

#### Set WdMonitor High (depending on state)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/TmprlMon/doc/mediax/media/image2.emf)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

Rte_Call_TmprlMon_Per1_CP1_CheckpointReached()

### Per: \_Per2

#### Design Rationale

The WdMonitor signal is not set at the end of this function (as
specified in the FDD). This is per the design specified in TmprlMon_Per1
(see section for more information).

#### Program Flow Start

#### Rte_Call_TmprlMon_Per2_CP0_CheckpointReached()

#### Store Module Inputs to Local copies

TMFTestStart_Cnt_T_lgc = Rte_IRead_TmprlMon_Per2_TMFTestStart_Cnt_lgc()

TmprlMonSt_Cnt_T_enum = TmprlMonSt_Cnt_M_enum

Rte_Call_FetDrvCntl_OP_GET(&FetDrvCntlFdbk_Cnt_T_lgc)

Rte_Call_PwrSwitchEn_OP_GET(&PwrSwitchEnFdbk_Cnt_T_lgc)

#### Temporal Monitor Control Circuit Fault

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/TmprlMon/doc/mediax/media/image3.emf)

#### Release WARMINIT Request when OPERATE State is Reached

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/TmprlMon/doc/mediax/media/image4.emf)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

Rte_Call_TmprlMon_Per3_CP1_CheckpointReached()

### Per: \_Per3

#### Design Rationale

None

#### Program Flow Start

Rte_Call_TmprlMon_Per3_CP0_CheckpointReached()

#### Store Module Inputs to Local copies

Rte_Call_SysFault2_OP_GET(&SysFault2_Cnt_T_lgc)

Rte_Call_SysFault3_OP_GET(&SysFault3_Cnt_T_lgc)

Rte_Call_PwrSwitchEn_OP_GET(&PwrSwitchEn_Cnt_T_lgc)

Rte_Call_FetDrvCntl_OP_GET(&FetDrvCntl_Cnt_T_lgc)

#### TMF Run Time Control Circuit Fault

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/TmprlMon/doc/mediax/media/image5.emf)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

Rte_Call_TmprlMon_Per3_CP1_CheckpointReached()

##  Fault Recovery Functions

None

## Shutdown Functions

None

## Interrupt Functions

None

## Serial Communication Functions

None

## Transition Functions

### Trns: \_Trns1

#### Design Rationale

This function is run upon entering the WARMINIT state. This is done (as
opposed to an initialization function) because of the possibility of
entering the DISABLE state before the TMF initialization process is
complete.

#### Reset Values

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/TmprlMon/doc/mediax/media/image6.emf)

###  Trns: \_Trns2

#### Design Rationale

This function is run upon entering the DISABLE state.

## ![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/TmprlMon/doc/mediax/media/image7.emf) [section]

# Execution Requirements

## Execution Sequence of the Module

The TmprlMon_Per1 function is executed at the beginning of the forward
path (after ADC calculations). TmprlMon2_Per1 is executed at the end of
the forward path. This will provide a “pulse” on WdMonitor for the
duration of the forward path calculations. TmprlMon_Per2 is run outside
of the forward path, in order to advance the TMF initialization process.
TmprlMon_Per3 is run at 8ms intervals, and is only run during the system
OPERATE and DISABLE states. In this way, TmprlMon_Per3 should only be
run once the TMF initialization is complete (as the completion of this
process is a prerequisite to leaving the WARMINIT state).

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

| Function Name  | Calling Frequency | System State(s) in which the function is called |
|--------------------------|-----------------|------------------------------|
| TmprlMon_Per1  | 2 ms              | ALL                                             |
| TmprlMon_Per2  | 2 ms              | WARMINIT                                        |
| TmprlMon_Per3  | 4 ms              | OPERATE, DISABLE                                |
| TmprlMon_Trns1 | Transition        | Entering WARMINIT                               |
| TmprlMon_Trns2 | Transition        | Entering DISABLE                                |

## Execution Requirements for Serial Communication Functions 

| Function Name | Sub-Module called by (Serial Comm Function Name) |
|---------------|--------------------------------------------------|
| \<None\>      |                                                  |

#  [section-1]

#  Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

| Name of Sub Module | Software Segment                    |
|--------------------|-------------------------------------|
| TmprlMon_Per1      | RTE_START_SEC_SA_TMPRLMON_APPL_CODE |
| TmprlMon_Per2      | RTE_START_SEC_SA_TMPRLMON_APPL_CODE |
| TmprlMon_Per3      | RTE_START_SEC_SA_TMPRLMON_APPL_CODE |
| TmprlMon_Trns1     | RTE_START_SEC_SA_TMPRLMON_APPL_CODE |
| TmprlMon_Trns2     | RTE_START_SEC_SA_TMPRLMON_APPL_CODE |

##  [section-2]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

| Name of Sub Module | Software Segment |
|--------------------|------------------|
|                    |                  |

#  [section-3]

#  Known Issues / Limitations With Design

1.  None

#  Revision Control Log

<table style="width:100%;">
<colgroup>
<col style="width: 6%" />
<col style="width: 6%" />
<col style="width: 64%" />
<col style="width: 11%" />
<col style="width: 11%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Item #</strong></th>
<th><strong>Rev #</strong></th>
<th><strong>Change Description</strong></th>
<th><strong>Date</strong></th>
<th><strong>Author Initials</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>1</td>
<td>1.0</td>
<td>Initial MDD</td>
<td>25-May-11</td>
<td>BG</td>
</tr>
<tr class="even">
<td>2</td>
<td>2</td>
<td>Updated NTCs with global constants</td>
<td>02-Dec-11</td>
<td>OT</td>
</tr>
<tr class="odd">
<td>3</td>
<td>3.0</td>
<td>Initial Component MDD (started from scratch)</td>
<td>21-Mar-12</td>
<td>OT</td>
</tr>
<tr class="even">
<td>4</td>
<td>4</td>
<td>Correction to move STD_LOW and STD_HIGH to global constant
definitions since they are AUTOSAR defined constants</td>
<td>28-Mar-12</td>
<td>JJW</td>
</tr>
<tr class="odd">
<td>5</td>
<td>5</td>
<td>Changed NTC Status byte to STATIC, updated state times</td>
<td>01-Apr-12</td>
<td>OT</td>
</tr>
<tr class="even">
<td>6</td>
<td>6</td>
<td>Updated to FDD 19B v002B (state times, NTC parameter info)</td>
<td>19-Jun-12</td>
<td>OT</td>
</tr>
<tr class="odd">
<td>7</td>
<td>7</td>
<td>Changed Per3 running states (to avoid conflict with ShtdnMech)</td>
<td>25-Jul-12</td>
<td>OT</td>
</tr>
<tr class="even">
<td>8</td>
<td>8</td>
<td>Added functionality for Hardware Power Up, removed Trns2 (obsolete
with change in Per3 running states)</td>
<td>19-Sep-12</td>
<td>OT</td>
</tr>
<tr class="odd">
<td>9</td>
<td>9</td>
<td>Addition of checkpoints in the program flow</td>
<td>27-Sep-12</td>
<td>Selva</td>
</tr>
<tr class="even">
<td>10</td>
<td>10</td>
<td><p>Updated to FDD Ver005</p>
<ol type="1">
<li><p>DISABLE and ESMDIABLE steps are removed. Added ALLON2
Step.</p></li>
<li><p>Transition times of ALLON1,ALLON2 and OPERATE changed</p></li>
</ol>
<p>Transition2 added for Shutdown operation</p></td>
<td>28-SEP-12</td>
<td>NRAR</td>
</tr>
<tr class="odd">
<td>11</td>
<td>11</td>
<td>Fix for anomaly #3912</td>
<td>24-Oct-12</td>
<td>BWL</td>
</tr>
<tr class="even">
<td>12</td>
<td>12</td>
<td>Update execution rate for Per1</td>
<td>24-Oct-12</td>
<td>BWL</td>
</tr>
<tr class="odd">
<td>13</td>
<td>13</td>
<td>Multi-app support. Removed Per2</td>
<td>12-Nov-12</td>
<td>JJW</td>
</tr>
<tr class="even">
<td>14</td>
<td>14</td>
<td>Updated to FDD ver 009</td>
<td>14-Apr-13</td>
<td>SP</td>
</tr>
<tr class="odd">
<td>15</td>
<td>15</td>
<td>Updates for NTS param anomalies 5113 &amp; 5280</td>
<td>26-Jul-13</td>
<td>Jared</td>
</tr>
</tbody>
</table>

{% endraw %}