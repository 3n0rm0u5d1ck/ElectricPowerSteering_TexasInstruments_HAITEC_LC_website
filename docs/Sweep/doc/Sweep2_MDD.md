---
layout: default
title: Sweep2_MDD
nav_order: 3
parent: Sweep
---
{% raw %}
# Module – Sweep2 [module-sweep2]

# High-Level Description

# Figures

## Component Diagram 

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/Sweep/doc/mediax/media/image1.png"
style="width:1.95972in;height:1.42431in" />

# Variable Data Dictionary

| Module Inputs         | Module Outputs |                        |
|-----------------------|----------------|------------------------|
| InputMtrTrq_MtrNm_f32 |                | OutputMtrTrq_MtrNm_f32 |

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
<td>SweepModeEn_Cnt_M_lgc</td>
<td>Boolean</td>
<td>N/A</td>
<td>FALSE</td>
<td>TRUE</td>
<td></td>
</tr>
<tr class="even">
<td>SweepConfig_Cnt_M_u16</td>
<td>Uint16</td>
<td>1</td>
<td>0</td>
<td>FULL</td>
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

| Constant Name         | Resolution | Units  | Value |
|-----------------------|------------|--------|-------|
| D_SWEEPMTRTRQ_CNT_U16 | 1          | Uint16 | 1     |

#### Global

| Constant Name   |
|-----------------|
| D_FALSE_CNT_LGC |
| D_ZERO_ULS_F32  |

###  [section-1]

### Module specific Lookup Tables Constants

| Constant Name | Resolution | Value | Software Segment |
|---------------|------------|-------|------------------|
|               |            |       |                  |

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

| Data                  | Value |
|-----------------------|-------|
| InputMtrTrq_MtrNm_f32 | 0     |

## Initialization Functions

None

## Periodic Functions

#### Design Rationale

None

#### Store Module Inputs to Local copies Fault Recovery Functions

See below

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/Sweep/doc/mediax/media/image2.emf)

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
| Sweep2_Per1   | 2ms               | RTE_AP_SWEEP2_APPL_CODE                         |

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

| Name of Sub Module | Software Segment        |
|--------------------|-------------------------|
| Sweep2_Per1        | RTE_AP_SWEEP2_APPL_CODE |

#  [section-4]

#  Known Issues / Limitations With Design

1.  (Item \#1)

# Revision Control Log

| **Rev \#** | **Change Description** | **Date**  | **Author Initials** |
|------------|------------------------|-----------|---------------------|
| 1          | Initial MDD version    | 25-Mar-13 | VK                  |

{% endraw %}