---
layout: default
title: PeakCurrEst_MDD
nav_order: 6
parent: Motor Control
---
{% raw %}
# Module – PeakCurrEst [module-peakcurrest]

# High-Level Description

# Figures

## Component Diagram

#   [section]

#  <img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrCtrl_CM/doc/mediax/media/image1.png"
style="width:2.40625in;height:1.69792in" />  [section-1]

##  Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

| Module Inputs      | Module Outputs |                         |
|--------------------|----------------|-------------------------|
| MtrCurrQax_Amp_f32 |                | EstPkCurr_AmpSq_f32     |
| MtrCurrDax_Amp_f32 |                | FiltEstPkCurr_AmpSq_f32 |

## Module Internal Variables

This section identifies the name, range and resolutions for module
specific data created by this module. If there are no range restrictions
on the variable, the term “FULL” is placed into the table for legal
range.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 11%" />
<col style="width: 14%" />
<col style="width: 13%" />
<col style="width: 27%" />
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
<td>QaxCurrFiltSV_Amp_M_u12p20</td>
<td>Single Precision Float</td>
<td>-220</td>
<td>220</td>
<td>PEAKCURREST_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>DaxCurrFiltSV_Amp_M_s11p20</td>
<td>Single Precision Float</td>
<td>-220</td>
<td>220</td>
<td>PEAKCURREST_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>EstPkCurr_AmpSq_M_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td>48400</td>
<td>PEAKCURREST_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>EstPkCurrFiltSV_AmpSq_M_u16p16</td>
<td>Single Precision Float</td>
<td>0</td>
<td>48400</td>
<td>PEAKCURREST_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>FiltMtrCurEst_Id_Amp_D_f32</td>
<td>Single Precision Float</td>
<td>-220</td>
<td>220</td>
<td>PEAKCURREST_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>MtrCurEst_Iq_AmpSq_D_f32</td>
<td>Single Precision Float</td>
<td>-220</td>
<td>220</td>
<td>PEAKCURREST_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>MtrCurEst_Id_AmpSq_D_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td>48400</td>
<td>PEAKCURREST_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>FiltMtrCurEst_Iq_Amp_D_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td>48400</td>
<td>PEAKCURREST_START_SEC_VAR_CLEARED_32</td>
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

| Constant Name                    |
|----------------------------------|
| k_EstPkCurr2msLPFKn_Uls_u16      |
| k_EstPkCurrSlowLoopLPFKn_Uls_u16 |

## Program(fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

| Constant Name | Resolution | Units | Value |
|---------------|------------|-------|-------|
| None          |            |       |       |
|               |            |       |       |

####  [section-2]

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

| Constant Name              |
|----------------------------|
| D_ESTPKCURRLOLMT_AMPSQ_F32 |
| D_ESTPKCURRHILMT_AMPSQ_F32 |

### Module specific Lookup Tables Constants

| Constant Name | Resolution | Value | Software Segment |
|---------------|------------|-------|------------------|
| None          |            |       |                  |

#  Functions/Macros used by the Sub-Modules 

## Library Functions / Macros 

The library and functions / Macros that are called by the various sub
modules are identified below,

1.  LPF_SvUpdate_u16InFixKTrunc_m

2.  LPF_OpUpdate_u16InFixKTrunc_m

3.  LPF_SvUpdate_s16InFixKTrunc_m

4.  LPF_OpUpdate_s16InFixKTrunc_m

5.  FPM_FloatToFixed_m

6.  FPM_FixedToFloat_m

7.  Limit_m

## Data Hiding Functions

1.  None

## Global Functions/Macros Defined by this Module

None

## Local Functions/Macros Used by this MDD only

None

# Software Module Implementation

## Runtime Environment (RTE) Initial Values

None

## Initialization Functions

None

##  Periodic Functions

### Per: PeakCurrEst_Per1

#### Design Rationale

None

#### Program Flow Start

Rte_Call_PeakCurrEst_Per1_CP0_CheckpointReached

#### Store Module Inputs to Local copies

EstMtrCurrQax_Amp_T_f32=Rte_IRead_PeakCurrEst_Per1_MtrCurrQax_Amp_f32()

EstMtrCurrDax_Amp_T_f32=Rte_IRead_PeakCurrEst_Per1_MtrCurrDax_Amp_f32()

#### Module Design

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrCtrl_CM/doc/mediax/media/image3.emf)

#### Store Local copy of outputs into Module Outputs

Rte_IWrite_PeakCurrEst_Per1_EstPkCurr_AmpSq_f32(EstPkCurr_AmpSq_T_f32)

#### Program Flow End

Rte_Call_PeakCurrEst_Per1_CP1_CheckpointReached

### Per: PeakCurrEst_Per2

#### Design Rationale

#### Program Flow Start

Rte_Call_PeakCurrEst_Per2_CP0_CheckpointReached()

#### Module Design

#### ![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrCtrl_CM/doc/mediax/media/image4.emf) [section-3]

##  [section-4]

#### Store Local copy of outputs into Module Outputs

Rte_IWrite_PeakCurrEst_Per2_FiltEstPkCurr_AmpSq_f32(FiltEstPkCurr_AmpSq_T_f32)

#### Program Flow End

####  [section-5]

#### Rte_Call_PeakCurrEst_Per2_CP1_CheckpointReached() [rte_call_peakcurrest_per2_cp1_checkpointreached]

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

## Execution Sequence of the Module

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

| Function Name    | Calling Frequency | System State(s) in which the function is called |
|--------------------------|-----------------|------------------------------|
| PeakCurrEst_Per1 | 2ms               | OFF,DISABLE,OPERATE                             |
| PeakCurrEst_Per2 | 100ms             | OFF,DISABLE,OPERATE                             |

## Execution Requirements for Serial Communication Functions 

| Function Name | Sub-Module called by (Serial Comm Function Name) |
|---------------|--------------------------------------------------|
|               |                                                  |

#  [section-7]

#  Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

| Name of Sub Module | Software Segment             |
|--------------------|------------------------------|
| PeakCurrEst_Per1   | RTE_AP_PEAKCURREST_APPL_CODE |
| PeakCurrEst_Per2   | RTE_AP_PEAKCURREST_APPL_CODE |

##  [section-8]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

| Name of Sub Module | Software Segment |
|--------------------|------------------|
|                    |                  |

#  [section-9]

#  Known Issues / Limitations With Design

1.  INLINE functions defined in GlobalMacro.h are not unit tested.

#  Revision Control Log

| **Item \#** | **Rev \#** | **Change Description**                        | **Date**  | **Author Initials** |
|------|------|--------------------------------------------|---------|---------|
| 1           | 1.0        | Initial Version                               | 5/15/2012 | KPIT-RD             |
| 2           | 2.0        | Addition of checkpoints and memmap statements | 20-Nov-12 | Selva               |
| 3           | 3.0        | Updated to version 8 FDD SF99 B               | 20-Mar-12 | Selva               |

{% endraw %}