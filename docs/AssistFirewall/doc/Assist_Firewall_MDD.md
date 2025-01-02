---
layout: default
title: Assist_Firewall_MDD
nav_order: 1
parent: Assist Firewall (Safety)
---
{% raw %}
# Module --  [module---]

# High-Level Description

This module limits the output from the Assist module according to safety
requirements.

# Figures

## Component Diagram

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/AssistFirewall/doc/mediax/media/image1.png"
style="width:3.56597in;height:3.37708in" />

#  Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

| Module Inputs                  | Module Outputs |                            |
|-----------------------------------|--|------------------------------------|
| BaseAssistCmd_MtrNm_f32        |                | AsstFirewallActive_Uls_f32 |
| HighFreqAssist_MtrNm_f32       |                | CombinedAssist_MtrNm_f32   |
| HwTorque_HwNm_f32              |                |                            |
| HysteresisComp_MtrNm_f32       |                |                            |
| VehicleSpeed_Kph_f32           |                |                            |
| Defeat_AsstTbl_Service_Cnt_lgc |                |                            |
| MEC_Counter_Cnt_enum           |                |                            |

## Module Internal Variables

This section identifies the name, range and resolutions for module
specific data created by this module. If there are no range restrictions
on the variable, the term “FULL” is placed into the table for legal
range.

<table>
<colgroup>
<col style="width: 27%" />
<col style="width: 16%" />
<col style="width: 13%" />
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
<td>UprBoundKSV_M_str</td>
<td></td>
<td></td>
<td></td>
<td>ASSISTFIREWALL_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="even">
<td>LwrBoundKSV_M_str</td>
<td></td>
<td></td>
<td></td>
<td>ASSISTFIREWALL_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="odd">
<td>HiFreqKSV_M_str</td>
<td></td>
<td></td>
<td></td>
<td>ASSISTFIREWALL_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="even">
<td>ActiveKSV_M_str</td>
<td></td>
<td></td>
<td></td>
<td>ASSISTFIREWALL_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="odd">
<td>ActiveRawAcc_Cnt_M_u16</td>
<td>1</td>
<td>FULL</td>
<td>FULL</td>
<td>ASSISTFIREWALL_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td>PNCountStatus_Cnt_M_lgc</td>
<td>n/a</td>
<td>FALSE</td>
<td>TRUE</td>
<td>ASSISTFIREWALL_START_SEC_VAR_CLEARED_ BOOLEAN</td>
</tr>
<tr class="odd">
<td>AsstFWUprBound_MtrNm_D_f32</td>
<td>Single Precision Floating Point</td>
<td>-8.8</td>
<td>8.8</td>
<td>ASSISTFIREWALL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>AsstFWLwrBound_MtrNm_D_f32</td>
<td>Single Precision Floating Point</td>
<td>-8.8</td>
<td>8.8</td>
<td>ASSISTFIREWALL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>AsstFWSumInput_MtrNm_D_f32</td>
<td>Single Precision Floating Point</td>
<td>-26.4</td>
<td>26.4</td>
<td>ASSISTFIREWALL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>AsstFWLowFreqInput_MtrNm_D_f32</td>
<td>Single Precision Floating Point</td>
<td>-26.4</td>
<td>26.4</td>
<td>ASSISTFIREWALL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>AsstFWLowFreqLimited_MtrNm_D_f32</td>
<td>Single Precision Floating Point</td>
<td>-8.8</td>
<td>8.8</td>
<td>ASSISTFIREWALL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>AsstFWActiveRaw_Uls_D_f32</td>
<td>Single Precision Floating Point</td>
<td>0</td>
<td>1</td>
<td>ASSISTFIREWALL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>AsstFWUprBoundFilt_MtrNm_D_f32</td>
<td>Single Precision Floating Point</td>
<td>-8.8</td>
<td>8.8</td>
<td>ASSISTFIREWALL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>AsstFWLwrBoundFilt_MtrNm_D_f32</td>
<td>Single Precision Floating Point</td>
<td>-8.8</td>
<td>8.8</td>
<td>ASSISTFIREWALL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>CombAsstSV_MtrNm_M_f32</td>
<td>Single Precision Floating Point</td>
<td>-8.8</td>
<td>8.8</td>
<td>ASSISTFIREWALL_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>AsstFWOverBound_Cnt_D_lgc</td>
<td>n/a</td>
<td>FALSE</td>
<td>TRUE</td>
<td>ASSISTFIREWALL_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="odd">
<td>AsstReducedPerfSV_Cnt_M_lgc</td>
<td>n/a</td>
<td>FALSE</td>
<td>TRUE</td>
<td>ASSISTFIREWALL_START_SEC_VAR_CLEARED_ BOOLEAN</td>
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

| Constant Name                              |
|--------------------------------------------|
| k_AsstFWInpLimitHysComp_MtrNm_f32          |
| k_AsstFWInpLimitHFA_MtrNm_f32              |
| k_AsstFWInpLimitBaseAsst_MtrNm_f32         |
| k\_AsstFWFiltKn_Hz_f32                     |
| k_AsstFWFWActiveLPF_Hz_f32                 |
| t_AsstFWVehSpd_Kph_u9p7\[12\]              |
| t2_AsstFWUprBoundX_HwNm_s4p11\[12\]\[11\]  |
| t2_AsstFWUprBoundY_MtrNm_s4p11\[12\]\[11\] |
|                                            |
|                                            |
| k_AsstFWPstep_Cnt_u16                      |
| k_AsstFWNstep_Cnt_u16                      |
| t_AsstFWPstepNstepThresh_Cnt_u16\[2\]      |
| t_AsstFWDefltAssistX_HwNm_u8p8\[20\]       |
| t_AsstFWDefltAssistY_MtrNm_s4p11\[20\]     |
| k_RestoreThresh_MtrNm_f32                  |

## Program(fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

| Constant Name | Resolution | Units | Value |
|---------------|------------|-------|-------|
| None          |            |       |       |

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

| Constant Name                         |
|---------------------------------------|
| D_ONE_ULS_F32                         |
| D_ZERO_ULS_F32                        |
| D_2MS_SEC_F32                         |
| BC_ASSISTFIREWALL_FAULTINJECTIONPOINT |
| STD_ON                                |
| FLTINJ_ASSTFIREWALL                   |
| D_MTRTRQCMDLOLMT_MTRNM_F32            |
| D_MTRTRQCMDHILMT_MTRNM_F32            |
| D_NEGONE_CNT_S16                      |
| D_FALSE_CNT_LGC                       |

### Module specific Lookup Tables Constants

| Constant Name | Resolution | Value | Software Segment |
|---------------|------------|-------|------------------|
| None          |            |       |                  |

#  Functions/Macros used by the Sub-Modules 

## Library Functions / Macros 

The library and functions / Macros that are called by the various sub
modules are identified below,

1.  LPF_KUpdate_f32_m

2.  LPF_OpUpdate_f32_m

3.  HPF_KUpdate_f32_m

4.  HPF_OpUpdate_f32_m

5.  BilinearXMYM_s16_s16XMs16YM_Cnt

6.  TableSize_m

7.  FPM_FloatToFixed_m

8.  FPM_FixedToFloat_m

9.  DiagPStep_m

10. DiagNStep_m

11. Rte_Call_NxtrDiagMgr_SetNTCStatus

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

| Data                                     | Value |
|------------------------------------------|-------|
| Rte_InitValue_AsstFirewallActive_Uls_f32 | 0     |
| Rte_InitValue_BaseAssistCmd_MtrNm_f32    | 0     |
| Rte_InitValue_CombinedAssist_MtrNm_f32   | 0     |
| Rte_InitValue_HighFreqAssist_MtrNm_f32   | 0     |
| Rte_InitValue_HwTorque_HwNm_f32          | 0     |
| Rte_InitValue_HysteresisComp_MtrNm_f32   | 0     |
| Rte_InitValue_VehicleSpeed_Kph_f32       | 0     |

## Initialization Functions

### Init: \_Init1

#### Design Rationale

An initialization function is required to initialize K for each of the
filters.

#### Module Outputs

None

#### Module Internal 

None

#### Initialize Filters

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/AssistFirewall/doc/mediax/media/image3.emf)

##  Periodic Functions

### Per: \_Per1

#### Design Rationale

None

#### Program Flow Start

#### Rte_Call_AssistFirewall_Per1_CP0_CheckpointReached()Store Module Inputs to Local copies

BaseAssistCmd_MtrNm_T_f32 =
Rte_IRead_AssistFirewall_Per1_BaseAssistCmd_MtrNm_f32()

HighFreqAssist_MtrNm_T_f32 =
Rte_IRead_AssistFirewall_Per1_HighFreqAssist_MtrNm_f32()

HwTorque_HwNm_T_f32 = Rte_IRead_AssistFirewall_Per1_HwTorque_HwNm_f32()

HysteresisComp_MtrNm_T_f32 =
Rte_IRead_AssistFirewall_Per1_HysteresisComp_MtrNm_f32()

VehicleSpeed_Kph_T_f32 =
Rte_IRead_AssistFirewall_Per1_VehicleSpeed_Kph_f32()

AsstFWPstepNstep_Cnt_T_str.PStep = k_AsstFWPstep_Cnt_u16

AsstFWPstepNstep_Cnt_T_str.NStep = k_AsstFWNstep_Cnt_u16

AsstFWPstepNstep_Cnt_T_str.Threshold =
t_AsstFWPstepNstepThresh_Cnt_u16\[1\]

AbsHwTrq_HwNm_T_u8p8 =
FPM_FloatToFixed_m(Abs_f32_m(HwTorque_HwNm_T_f32), u8p8_T)

DefeatAsstTblSvc_Cnt_T_lgc =
Rte_IRead_AssistFirewall_Per1_Defeat_AsstTbl_Service_Cnt_lgc()

MECCounter_Cnt_T_enum =
Rte_IRead_AssistFirewall_Per1_MEC_Counter_Cnt_enum()

#### Sum and Filter Inputs

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/AssistFirewall/doc/mediax/media/image4.emf)

#### Determine Saturation Bounds and Perform Limiting

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/AssistFirewall/doc/mediax/media/image5.emf)

#### Determine Active State and Output

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/AssistFirewall/doc/mediax/media/image6.emf)

#### Store Local copy of outputs into Module Outputs

AsstFWUprBound_MtrNm_D_f32 = UprBound_MtrNm_T_f32

AsstFWLwrBound_MtrNm_D_f32 = LwrBound_MtrNm_T_f32

AsstFWUprBoundFilt_MtrNm_D_f32 = UprBoundFilt_MtrNm_T_f32

AsstFWLwrBoundFilt_MtrNm_D_f32 = LwrBoundFilt_MtrNm_T_f32

AsstFWSumInput_MtrNm_D_f32 = SumInput_MtrNm_T_f32

AsstFWLowFreqInput_MtrNm_D_f32 = LowFreqInput_MtrNm_T_f32

AsstFWLowFreqLimited_MtrNm_D_f32 = LowFreqLimited_MtrNm_T_f32

AsstFWActiveRaw_Uls_D_f32 = AsstFWActiveRaw_Uls_T_f32

Rte_IWrite_AssistFirewall_Per1_CombinedAssist_MtrNm_f32(CombAsstSV_MtrNm_M_f32)

Rte_IWrite_AssistFirewall_Per1_AsstFirewallActive_Uls_f32(AsstFWActive_Uls_T_f32)

#### Program Flow End

Rte_Call_AssistFirewall_Per1_CP1_CheckpointReached()

##  Fault Recovery Functions

None

## Shutdown Functions

None

## Interrupt Functions

None

## Serial Communication Functions

##   [section]

# Execution Requirements

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

| Function Name        | Calling Frequency | System State(s) in which the function is called |
|--------------------------|-----------------|------------------------------|
| AssistFirewall_Init1 | On Event          | On Init                                         |
| AssistFirewall_Per1  | 2 ms              | ALL                                             |

## Execution Requirements for Serial Communication Functions 

| Function Name | Sub-Module called by (Serial Comm Function Name) |
|---------------|--------------------------------------------------|
| \<None\>      |                                                  |

#  [section-1]

#  Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

| Name of Sub Module   | Software Segment                          |
|----------------------|-------------------------------------------|
| AssistFirewall_Init1 | RTE_START_SEC_AP_ASSISTFIREWALL_APPL_CODE |
| AssistFirewall_Per1  | RTE_START_SEC_AP_ASSISTFIREWALL_APPL_CODE |

##  [section-2]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

| Name of Sub Module | Software Segment |
|--------------------|------------------|
|                    |                  |

#  [section-3]

#  Known Issues / Limitations With Design

1.  INLINE functions in GlobalMacro.h are not unit tested.

#  Revision Control Log

| **Item \#** | **Rev \#** | **Change Description**                                          | **Date**   | **Author Initials** |
|------|------|--------------------------------------------|---------|--------|
| 1           | 1.0        | Initial Version                                                 | 24-Apr-12  | OT                  |
| 2           | 2.0        | Fixed conflicting calibration names                             | 10-May-12  | OT                  |
| 3           | 3.0        | Added fault injection point                                     | 18-May-12  | OT                  |
| 4           | 4.0        | Updated to SF-34 v002, fixed conflicting display variable names | 31-May-12  | OT                  |
| 5           | 5.0        | Updated to SF-34 v003                                           | 08-Jun-12  | OT                  |
| 6           | 6.0        | Fixed threshold assignment anomaly                              | 11-Jun-12  | OT                  |
| 7           | 7.0        | Updated to SF-34 v004                                           | 20-Jun-12  | OT                  |
| 8           | 8.0        | Updated to SF-34 Ver 005 and Ver 006                            | 1-Aug-12   | NRAR                |
| 9           | 9.0        | Inserted safe watchdog checkpoints                              | 15-Sept-12 | BWL                 |
| 10          | 10.0       | Corrected Unspecified variable name to “Boolean”                | 18 –Sep-12 | SSK                 |
| 11          | 11.0       | Updates to meet SF-34 v007                                      | 01-Feb-13  | VK                  |
| 12          | 12.0       | MDD/ Src mismatch updates                                       | 22-Feb-13  | VK                  |
| 13          | 13.0       | Updates to meet SF-34 v008                                      | 15-May-13  | SP                  |

{% endraw %}