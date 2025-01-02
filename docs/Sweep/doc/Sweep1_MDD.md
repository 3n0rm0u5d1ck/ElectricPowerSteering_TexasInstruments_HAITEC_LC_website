---
layout: default
title: Sweep1_MDD
nav_order: 2
parent: Sweep
---
{% raw %}
# Module – Sweep [module-sweep]

# High-Level Description

# Figures

## Component Diagram 

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/Sweep/doc/mediax/media/image1.png"
style="width:2in;height:1.69583in" />

# Variable Data Dictionary

| Module Inputs       | Module Outputs |                      |
|---------------------|----------------|----------------------|
| InputHwTrq_HwNm_f32 |                | OutputHwTrq_HwNm_f32 |
| VehSpdValid_Cnt_lgc |                |                      |
| VehSpd_Kph_f32      |                |                      |

## Module Internal Variables

<table>
<colgroup>
<col style="width: 29%" />
<col style="width: 9%" />
<col style="width: 9%" />
<col style="width: 10%" />
<col style="width: 10%" />
<col style="width: 30%" />
</colgroup>
<thead>
<tr class="header">
<th>Variable Name</th>
<th>Datatype</th>
<th>Resolution</th>
<th><p>Legal Range</p>
<p>(min)</p></th>
<th><p>Legal Range</p>
<p>(max)</p></th>
<th><p>Software Segment</p>
<p>{Data Type}</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>HwTrqQuantization_Uls_M_f32</td>
<td>Float32</td>
<td></td>
<td></td>
<td></td>
<td>SWEEP_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>CosSweepTorque_HwNm_M_f32</td>
<td>Float32</td>
<td></td>
<td></td>
<td></td>
<td>SWEEP_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>SweepVehSpdMax_Kph_M_f32</td>
<td>Float32</td>
<td></td>
<td></td>
<td></td>
<td>SWEEP_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>DwellStartTime_mS_M_u32p0</td>
<td>Uint32</td>
<td></td>
<td></td>
<td></td>
<td>SWEEP_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>LastStateSinArg_Uls_M_f32</td>
<td>Float32</td>
<td></td>
<td></td>
<td></td>
<td>SWEEP_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>TransStartTime_mS_M_u32p0</td>
<td>Uint32</td>
<td></td>
<td></td>
<td></td>
<td>SWEEP_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>MtrTrqQuantization_Uls_M_f32</td>
<td>Float32</td>
<td></td>
<td></td>
<td></td>
<td>SWEEP_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>SweepTorque_HwNm_M_f32</td>
<td>Float32</td>
<td></td>
<td></td>
<td></td>
<td>SWEEP_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>SweepAmplitude_HwNm_M_u5p11</td>
<td>Uint16</td>
<td></td>
<td></td>
<td></td>
<td>SWEEP_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td>SweepOffset_HwNm_M_s4p11</td>
<td>Sint16</td>
<td></td>
<td></td>
<td></td>
<td>SWEEP_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="odd">
<td>SweepState_Cnt_M_u16</td>
<td>Uint16</td>
<td></td>
<td></td>
<td></td>
<td>SWEEP_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td>FreqIndex_Cnt_M_u16</td>
<td>Uint16</td>
<td></td>
<td></td>
<td></td>
<td>SWEEP_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="odd">
<td>k_N_SweepConfig_Cnt_u16</td>
<td>Uint16</td>
<td></td>
<td></td>
<td></td>
<td>SWEEP_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td>k_N_SweepGain_MtrNmpHwNm_u1p15</td>
<td>Uint16</td>
<td></td>
<td></td>
<td></td>
<td>SWEEP_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="odd">
<td>L5_N_SweepOffset_HwNm_M_s4p11</td>
<td>Sint16</td>
<td></td>
<td></td>
<td></td>
<td>SWEEP_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td>L5_N_SweepAmplitude_HwNm_M_u5p11</td>
<td>Uint16</td>
<td></td>
<td></td>
<td></td>
<td>SWEEP_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="odd">
<td>L5_N_CosSweepTorque_HwNm_M_s10p5</td>
<td>Sint16</td>
<td></td>
<td></td>
<td></td>
<td>SWEEP_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td>L5_N_RespTorque_HwNm_G_s10p5</td>
<td>Sint16</td>
<td></td>
<td></td>
<td></td>
<td>SWEEP_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="odd">
<td>L5_N_SweepState_Cnt_M_u16</td>
<td>Uint16</td>
<td></td>
<td></td>
<td></td>
<td>SWEEP_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td>L5_N_SweepTorque_HwNm_G_s10p5</td>
<td>Sint16</td>
<td></td>
<td></td>
<td></td>
<td>SWEEP_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="odd">
<td>L5_N_InstFrequency_Hz_G_u7p9</td>
<td>Uint16</td>
<td></td>
<td></td>
<td></td>
<td>SWEEP_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td>SweepConfig_Cnt_M_u16</td>
<td>Uint16</td>
<td></td>
<td></td>
<td></td>
<td>SWEEP_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="odd">
<td>SweepGain_MtrNmpHwNm_M_u1p15</td>
<td>Uint16</td>
<td></td>
<td></td>
<td></td>
<td>SWEEP_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td>L5_N_GenHwTrq_Cnt_M_lgc</td>
<td>boolean</td>
<td>N/A</td>
<td>FALSE</td>
<td>TRUE</td>
<td>SWEEP_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="odd">
<td>k_N_EnVehSpdCheck_Cnt_lgc</td>
<td>boolean</td>
<td>N/A</td>
<td>FALSE</td>
<td>TRUE</td>
<td>SWEEP_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="even">
<td>k_N_SweepModeEn_Cnt_lgc</td>
<td>boolean</td>
<td>N/A</td>
<td>FALSE</td>
<td>TRUE</td>
<td>SWEEP_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="odd">
<td>EnVehSpdCheck_Cnt_M_lgc</td>
<td>boolean</td>
<td>N/A</td>
<td>FALSE</td>
<td>TRUE</td>
<td>SWEEP_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="even">
<td>GenHwTrq_Cnt_M_lgc</td>
<td>boolean</td>
<td>N/A</td>
<td>FALSE</td>
<td>TRUE</td>
<td>SWEEP_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="odd">
<td>SweepModeEn_Cnt_M_lgc</td>
<td>boolean</td>
<td>N/A</td>
<td>FALSE</td>
<td>TRUE</td>
<td></td>
</tr>
</tbody>
</table>

### User defined typedef definition/declaration 

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
</tbody>
</table>

# Constant Data Dictionary

## Calibration Constants

| Constant Name |
|---------------|
|               |

##  [section]

## Program(fixed) Constants

### Embedded Constants

#### Local

| Constant Name             | Resolution | Units  | Value |
|---------------------------|------------|--------|-------|
| D_SWEEPHWTRQ_CNT_U16      | 1          | Uint16 | 2     |
| D_SWEEPMTRTRQ_CNT_U16     | 1          | Uint16 | 1     |
| D_SWEEPSTART_CNT_U16      | 1          | Uint16 | 0     |
| D_SWEEPTRANSITION_CNT_U16 | 1          | Uint16 | 1     |
| D_SWEEPDWELL_CNT_U16      | 1          | Uint16 | 2     |
| D_SWEEPSTOP_CNT_U16       | 1          | Uint16 | 3     |
| D_SWEEPRAMP_CNT_U16       | 1          | Uint16 | 4     |
| D_SWEEPDONE_CNT_U16       | 1          | Uint16 | 5     |

#### Global

| Constant Name   |
|-----------------|
| D_FALSE_CNT_LGC |
| D_ZERO_ULS_F32  |

###  [section-1]

### Module specific Lookup Tables Constants

| Constant Name               | Resolution | Value                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | Software Segment |
|-------------------|---------|----------------------------------|------------|
| T_SweepFreq_Hz_f32\[100\]   | N/A        | {0.0F, 1.0F, 1.2F, 1.4F, 1.6F, 1.8F, 2.0F, 2.25F, 2.5F, 2.75F, 3.0F, 3.25F, 3.5F, 3.75F, 4.0F, 4.25F, 4.5F, 4.75F, 5.0F, 5.25F, 5.5F, 5.75F, 6.0F, 6.25F, 6.5F, 6.75F, 7.0F, 7.25F, 7.5F, 7.75F, 8.0F, 8.25F, 8.5F, 8.75F, 9.0F, 9.25F, 9.5F, 9.75F, 10.0F, 10.25F, 10.5F, 10.75F, 11.0F, 11.25F, 11.5F, 11.75F, 12.0F, 12.25F, 12.5F, 12.75F, 13.0F, 13.25F, 13.5F, 13.75F, 14.0F, 14.25F, 14.5F, 14.75F, 15.0F, 15.5F, 16.0F, 16.5F, 17.0F, 17.5F, 18.0F, 18.5F, 19.0F, 19.5F, 20.0F, 21.0F, 22.0F, 23.0F, 24.0F, 25.0F, 26.0F, 27.0F, 28.0F, 29.0F, 30.0F, 32.0F, 34.0F, 36.0F, 38.0F, 40.0F, 42.0F, 44.0F, 46.0F, 48.0F, 50.0F, 55.0F, 60.0F, 65.0F, 70.0F, 75.0F, 80.0F, 85.0F, 90.0F, 95.0F, 100.0F, 105.0F}           | AUTOMATIC        |
| T_TransTime_mS_u16p0\[100\] | N/A        | {2000U, 500U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 250U, 1000U}                                                                                                   | AUTOMATIC        |
| T_DwellTime_mS_u16p0\[100\] | N/A        | {0U, 32000U, 18333U, 10714U, 9375U, 8333U, 7500U, 6667U, 6000U, 5455U, 4667U, 4308U, 3714U, 3467U, 3000U, 2824U, 2667U, 2526U, 2400U, 2286U, 2182U, 2087U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U, 2000U} | AUTOMATIC        |

#  Functions/Macros used by the Sub-Modules 

## Library Functions / Macros 

The library and functions / Macros that are called by the various sub
modules are identified below,

## Data Hiding Functions

1.  \<None\>

## Global Functions/Macros Defined by this Module

none

## Local Functions/Macros Used by this MDD only

none

# Software Module Implementation

## Runtime Environment (RTE) Initial Values

| Data                | Value |
|---------------------|-------|
| InputHwTrq_HwNm_f32 | 0     |
| VehSpdValid_Cnt_lgc | FALSE |
| VehSpd_Kph_f32      | 0     |

## Initialization Functions

#### Design Rationale

None

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/Sweep/doc/mediax/media/image2.emf)

## Periodic Functions

#### Design Rationale

None

#### Description

#### Store Module Inputs to Local copies Fault Recovery Functions

See below

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/Sweep/doc/mediax/media/image3.emf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/Sweep/doc/mediax/media/image4.emf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/Sweep/doc/mediax/media/image5.emf)

#### Store Local copy of outputs into Module Outputs

See above

## Shutdown Functions

None

## Interrupt Functions

None

## Fault Recovery Functions

None

## Shutdown Functions

None

## Interrupt Functions

None

## Serial Communication Functions

None

# Execution Requirements

## Execution Sequence of the Module

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

| Function Name | Calling Frequency | System State(s) in which the function is called |
|--------------------------|-----------------|------------------------------|
| Sweep_Per1    | 2ms               | RTE_AP_SWEEP_APPL_CODE                          |

## Execution Requirements for Serial Communication Functions 

| Function Name | Sub-Module called by (Serial Comm Function Name) |
|---------------|--------------------------------------------------|
|               |                                                  |

#  [section-2]

#  Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

| Name of Sub Module | Software Segment |
|--------------------|------------------|
|                    |                  |

##  [section-3]

## Global and Local Functions

This table identifies the software segments for local functions
identified in this module.

| Name of Sub Module | Software Segment       |
|--------------------|------------------------|
| Sweep_Per1         | RTE_AP_SWEEP_APPL_CODE |

#  [section-4]

#  Known Issues / Limitations With Design

1.  (Item \#1)

# Revision Control Log

| **Rev \#** | **Change Description** | **Date**  | **Author Initials** |
|------------|------------------------|-----------|---------------------|
| 1          | Initial MDD version    | 25-Mar-13 | VK                  |

{% endraw %}