---
layout: default
title: OverVoltageMonitor_MDD
nav_order: 3
parent: Over Voltage Monitoring
---
{% raw %}
# Module -- OverVoltageMonitor [module----overvoltagemonitor]

Overvoltage monitor function operates so that when an overvoltage
condition occurs on any of the CPU supply voltages the motor inverter
operation is shutdown before the CPU can respond.

# High-Level Description

# Figures

## Diagram – Function Data Sharing

### Diagram – Function (Name)

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/OvrVoltMon/doc/mediax/media/image2.png"
style="width:3.44028in;height:2.38403in" />

#  Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

(Note: Full variable names required in table.)

(Note: All global variables including End Of Line data used should be
shown here)

| Module Inputs             | Module Outputs |     |
|---------------------------|----------------|-----|
| PwrDiscBTestStart_Cnt_lgc |                |     |
| phyOvrVoltFdbk_OP_GET     |                |     |

## Module Internal Variables

This section identifies the name, range and resolutions for module
specific data created by this module. If there are no range restrictions
on the variable, the term “FULL” is placed into the table for legal
range.

<table>
<colgroup>
<col style="width: 34%" />
<col style="width: 13%" />
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
<td>OvrVoltMon_OverVoltAcc_Cnt_M_u16</td>
<td>1</td>
<td>1</td>
<td>512</td>
<td>OVRVOLTMON_START_SEC_VAR_CLEARED_16</td>
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
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
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

| Constant Name         |
|-----------------------|
| k_CPUSupplyOV_Cnt_Str |

## Program(fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

| Constant Name | Resolution | Units | Value |
|---------------|------------|-------|-------|
| None          |            |       |       |

####  [section]

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

| Constant Name |
|---------------|
| None          |

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

## Data Hiding Functions

1.  Rte_Call_NxtrDiagMgr_SetNTCStatus

2.  Rte_Mode_SystemState_Mode()

## Global Functions/Macros Defined by this Module

### Global Function \#1

|                      |                           |                         |     |     |
|------------|----------------------------|-------------------|-------|-------|
| **Function Name**    | Rte_Mode_SystemState_Mode | Type                    | Min | Max |
| **Arguments Passed** | None                      |                         |     |     |
|                      |                           |                         |     |     |
| **Return Value**     | SysState_Cnt_T_Enum       | Rte_ModeType_StaMd_Mode | N/A | N/A |

#### Description

## Local Functions/Macros Used by this MDD only

##  [section-1]

# Software Module Implementation

## Runtime Environment (RTE) Initial Values

This section lists the initial values of data written by this module but
controlled by the RTE. After RTE initialization, the data in this table
will contain these values.

| Data | Value |
|------|-------|
|      |       |

## Initialization Functions

(Note: For multiple init functions, insert new headers at the “Header 2”
level – subset of “5.1 Initialization Functions” and follow the same
sub-section design shown below)

### None

##  Periodic Functions

### Per: OvrVoltMon_Per1

#### Design Rationale

#### Program Flow Start

Rte_Call_OvrVoltMon_Per1_CP0_CheckpointReached()

#### Store Module Inputs to Local copies

Rte_Call_phyOvrVoltFdbk_OP_GET(&phyOvrVltFdbk_Cnt_T_lgc)

PwrDiscBTestStart_Cnt_T_lgc =
Rte_IRead_OvrVoltMon_Per1_PwrDiscBTestStart_Cnt_lgc()

/\* Read the system state\*/

SysState_Cnt_T_Enum = Rte_Mode_SystemState_Mode()

####  Processing

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/OvrVoltMon/doc/mediax/media/image3.emf)

#### Store Local copy of outputs into Module Outputs

N/A

#### Program Flow End

Rte_Call_OvrVoltMon_Per1_CP1_CheckpointReached()

## Fault Recovery Functions

## Shutdown Functions

## Interrupt Functions

## Serial Communication Functions

# Execution Requirements

## Execution Sequence of the Module

(Describe in words relevant details about the execution sequence of the
different sub modules.)

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

| Function Name   | Calling Frequency | System State(s) in which the function is called |
|--------------------------|-----------------|------------------------------|
| OvrVoltMon_Per1 | 2ms               | OPERATE,WARMINIT                                |

## Execution Requirements for Serial Communication Functions 

| Function Name | Sub-Module called by (Serial Comm Function Name) |
|---------------|--------------------------------------------------|
| N/A           |                                                  |

#  [section-2]

#  Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

| Name of Sub Module | Software Segment            |
|--------------------|-----------------------------|
| OvrVoltMon_per1    | RTE_SA_OVRVOLTMON_APPL_CODE |

##  [section-3]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

#  [section-4]

#  Known Issues / Limitations With Design

#  Revision Control Log [revision-control-log]

|             |            |                                                |            |                     |
|------|------|--------------------------------------------|---------|---------|
| **Item \#** | **Rev \#** | **Change Description**                         | **Date**   | **Author Initials** |
| 1           | 1.0        | Initial AutoSAR Release                        | 10-July-12 | NRAR                |
| 2           | 2.0        | Changed from PSTEP to NSTEP when no fault      | 29-July-12 | NRAR                |
| 3           | 3.0        | MDD version update                             | 30-July-12 | NRAR                |
| 4           | 4          | Updated states diagnostic is run in            | 07-Aug-12  | LWW                 |
| 5           | 5          | Checkpoints added and mempmap macros corrected | 27-sep-12  | Selva               |
| 6           | 6          | Matched FDD v3                                 | 01-Feb-13  | Selva               |

{% endraw %}