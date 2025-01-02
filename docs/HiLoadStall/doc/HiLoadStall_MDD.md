---
layout: default
title: HiLoadStall_MDD
nav_order: 3
parent: Component
---
{% raw %}
# Module -- HiLoadStall [module----hiloadstall]

# High-Level Description

The High Load Stall Thermal Management algorithm protects the system
from prolonged intervals of high assist torque at near-stall conditions.

# Figures

## Diagram – Function Data Sharing

This diagram shows all data that is shared between functions within the
module.

None

### Diagram – Ret HiLoadStall \_Per1

This diagram describes the functional characteristics and data flow of a
given function.

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/HiLoadStall/doc/mediax/media/image1.png"
style="width:2.01679in;height:1.7762in" />

#  Module Inputs and Outputs

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

(Note: Full variable names required in table.)

(Note: All global variables including End Of Line data used should be
shown here)

| Module Inputs (Global Variable Name) | Module Outputs (Global Variable Name) |
|----------------------------------|--------------------------------------|
| MtrVelCRF_MtrRadpS_f32               | AssistStallLimit_MtrNm_f32            |
| PreLimitForStall_MtrNm_f32           |                                       |
| DftStallLimit_Cnt_lgc                |                                       |
|                                      |                                       |

## Module Internal Variables

This section identifies the name, range and resolutions for module
specific data created by this module. If there are no range restrictions
on the variable, the term “FULL” is placed into the table for legal
range.

(Note: If no module specific variables are used by the design, place the
text “None” in the first Variable Name cell in the table)

<table style="width:100%;">
<colgroup>
<col style="width: 35%" />
<col style="width: 13%" />
<col style="width: 13%" />
<col style="width: 12%" />
<col style="width: 24%" />
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
<td>PrevAssistStallLimit_MtrNm_M_f32</td>
<td>Single Precision Floating Point</td>
<td>0</td>
<td>8.8</td>
<td>HILOADSTALL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>ModPreLimitFiltSV_MtrNm_M_u8p24</td>
<td>2^-24</td>
<td>0</td>
<td>8.8</td>
<td>HILOADSTALL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>ModPreLimit_MtrNm_D_u8p8</td>
<td>0.00390625</td>
<td>0</td>
<td>8.8</td>
<td>HILOADSTALL_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td>FiltModPreLimit_MtrNm_D_u8p8</td>
<td>0.00390625</td>
<td>0</td>
<td>8.8</td>
<td>HILOADSTALL_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="odd">
<td>StallLimit_MtrNm_D_u8p8</td>
<td>0.00390625</td>
<td>0</td>
<td>8.8</td>
<td>HILOADSTALL_START_SEC_VAR_CLEARED_16</td>
</tr>
</tbody>
</table>

###  [section]

### User defined typedef definition/declaration 

This section documents any user types uniquely used for the module.

| Variable Name | Typedef Name | Storage Type | Safety Critical Classification |
|---------------|--------------|--------------|--------------------------------|
| None          |              |              |                                |

# Constant Data Dictionary

## Calibration Constants

This section lists the calibrations used by the module. For details on
calibration constants, refer to the Data Dictionary for the application.

(Note: If no calibrations are used by the design, place the text “None”
in the first location in the table)

| Constant Name                |
|------------------------------|
| k_AbsMtrVelBkt_MtrRadps_f32  |
| k_EOTThrmPrtLPFKn_Cnt_u16    |
| t_EOTThrmIndptTbl_MtrNm_u8p8 |
| t_EOTThrmDpntTbl_MtrNm_u8p8  |
| k_EOTThrmSlwLmtStp_MtrNm_f32 |

##  [section-1]

## Program(fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

| Constant Name | Resolution | Value |
|---------------|------------|-------|
|               |            |       |

#### Note: RtnLoopTime depends on the rate of the periodic function. [note-rtnlooptime-depends-on-the-rate-of-the-periodic-function.]

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

| Constant Name              |
|----------------------------|
| D_MTRTRQCMDHILMT_MTRNM_F32 |
| D_ZERO_ULS_F32             |

### Module specific Lookup Tables Constants

(This is for lookup tables (arrays) with fixed values, same name as
other tables)

| Constant Name | Resolution | Value | Software Segment |
|---------------|------------|-------|------------------|
|               |            |       |                  |

# Software Module Implementation

## Initialization Functions

### Init: HiLoadStall_Init()

#### Design Rationale

None

#### Module Outputs

None

#### Module Internal 

None

##  Periodic Functions

### Per: HiLoadStall_Per1

#### Design Rationale

None

#### Program Flow Start

Rte_Call_HiLoadStall_Per1_CP0_CheckpointReached()

#### Store Module Inputs to Local copies

MtrVelCRF_MtrRadpS_T_f32 = Rte_IRead_HiLoadStall_Per1_HighStallLmt
\_MtrVelCRF_MtrRadpS_f32()

PreLimitForStall_MtrNm_T_f32 = Rte_Iread_HiLoadStall_Per1_HighStallLmt
\_ PreLimitForStall_MtrNm_f32()

DftStallLimit_Cnt_T_lgc = Rte_Iread_HiLoadStall_Per1_HighStallLmt
\_DftStallLimit_Cnt_lgc()

PreLimitForStall_MtrNm_T_u8p8 =
FPM_FloatToFixed_m(PreLimitForStall_MtrNm_T_f32, u8p8_T)

SatPreLimitForStall_MtrNm_T_u8p8 =
Limit_m(PreLimitForStall_MtrNm_T_u8p8, 0U,
t_EOTThrmDpntTbl_MtrNm_u8p8\[0\]);

#### Determine EOT Thermal Limiting

##### EOT Thermal Algorithm Enable

##### ![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/HiLoadStall/doc/mediax/media/image2.emf) [section-2]

#####  [section-3]

##### Low Pass Filter

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/HiLoadStall/doc/mediax/media/image3.emf)

##### EOT Thermal Protection Limit Table

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/HiLoadStall/doc/mediax/media/image4.emf)

##### Slew Limiting

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/HiLoadStall/doc/mediax/media/image5.emf)

##### Serial Comm Defeat Sub-Function

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/HiLoadStall/doc/mediax/media/image6.emf)

#### Store Local copy of outputs into Module Outputs

#### Rte_IWrite_HiLoadStall_Per1_AssistStallLimit_MtrNm_f32(PrevAssistStallLimit_MtrNm_M_f32) [rte_iwrite_hiloadstall_per1_assiststalllimit_mtrnm_f32prevassiststalllimit_mtrnm_m_f32]

#### Program Flow End

Rte_Call_HiLoadStall_Per1_CP1_CheckpointReached()

##  Fault Recovery Functions

None

## Shutdown Functions

None

## Interrupt Functions

None

## Serial Communication Functions

None

## Local Function/Macro Definitions

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/HiLoadStall/doc/mediax/media/image7.emf)![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/HiLoadStall/doc/mediax/media/image8.emf)

#  Execution Requirements

## Execution Sequence of the Module

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

| Function Name      | Task List | Calling Frequency | System State(s) in which the function is called |
|------------------|------------------|------------------|------------------|
| HiLoadStall \_Per1 |           | 2ms               | All                                             |

## Execution Requirements for Serial Communication Functions 

| Function Name | Sub-Module called by (Serial Comm Function Name) |
|---------------|--------------------------------------------------|
| None          |                                                  |

#  [section-4]

#  Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

| Name of Sub Module | Software Segment                       |
|--------------------|----------------------------------------|
| HiLoadStall_Per1() | RTE_START_SEC_AP_HILOADSTALL_APPL_CODE |

## Local Functions

This table identifies the software segments for local functions
identified in this module.

| Name of Sub Module | Software Segment |
|--------------------|------------------|
| None               |                  |

#  [section-5]

#  Known Issues / Limitations With Design

1.  Inline functions in globalmacros.h are not unit tested.

#  Revision Control Log

|             |            |                                                                                                                                                                                                            |             |                     |
|------|--------|------------------------------------------|----------|---------|
| **Item \#** | **Rev \#** | **Change Description**                                                                                                                                                                                     | **Date**    | **Author Initials** |
| 1           | 1.0        | Initial release                                                                                                                                                                                            | 15DEC11     | M. Story            |
| 2           | 2.0        | Changed ranges on M variables for unsigned. Made ModPreLimitFiltSV_Cnt_M_u16 name match code.                                                                                                              | 07Jan12     | M. Story            |
| 3           | 3.0        | Changes to correct state variable issue found during review. Updated slew limit logic and replaced local constants with use of global constants. Variable name updates and added output legal range limit. | 27Jan12     | LWW                 |
| 4           | 4.0        | Check Point added for Periodic program flow                                                                                                                                                                | 21-Sep-2012 | Selva               |
| 5           | 5.0        | Added saturation to the PreLimit input described in revision 4 of the SF document. ICR 4452                                                                                                                | 28-Jan-14   | KJS                 |

{% endraw %}