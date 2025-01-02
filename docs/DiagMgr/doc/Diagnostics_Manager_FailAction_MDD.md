---
layout: default
title: Diagnostics_Manager_FailAction_MDD
nav_order: 5
parent: Diagnostic Manager
---
{% raw %}
# Module -- Fail Action [module----fail-action]

# High-Level Description

# Figures

## Component Diagram 

# Variable Data Dictionary

| Module Inputs | Module Outputs |                                       |
|---------------|----------------|---------------------------------------|
|               |                | DiagStsNonRecRmpToZeroFltPres_Cnt_lgc |
|               |                | DiagStsCtrldDisRmpPres_Cnt_lgc        |
|               |                | DiagStsRecRmpToZeroFltPres_Cnt_lgc    |
|               |                | DiagStsHWASbSystmFltPres_Cnt_lgc      |
|               |                | DiagStsDefVehSpd_Cnt_lgc              |
|               |                | DiagStsDefTemp_Cnt_lgc                |
|               |                | DiagStsScomHWANotValid_Cnt_lgc        |
|               |                | DiagStsWIRDisable_Cnt_lgc             |
|               |                | DiagRampRate_XpmS_f32                 |
|               |                | DiagRampValue_Uls_f32                 |
|               |                | DiagRmpToZeroActive_Cnt_lgc           |

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
<td>DiagSts#_Cnt_M_b16[2]</td>
<td colspan="5">Refer to Diagnostics_Manager_GeneratedCfg_MDD.docx</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>ActiveRmpRate#_UlspmS_M_f32[2]</td>
<td colspan="5">Refer to Diagnostics_Manager_GeneratedCfg_MDD.docx</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
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
|               |

##  [section]

## Program(fixed) Constants

### Embedded Constants

#### Local

| Constant Name | Resolution | Units | Value |
|---------------|------------|-------|-------|
|               |            |       |       |

#### Global

| Constant Name                       |
|-------------------------------------|
| DIAGMGR_NUMAPPS                     |
| D_DIAGSTSNONRECRMPTOZEROBIT_CNT_B16 |
| D_DIAGSTSRECRMPTOZEROBIT_CNT_B16    |
| D_DIAGSTSCTRLDDISRMPBIT_CNT_B16     |
| D_DIAGSTSHWASBSYSTMFLTBIT_CNT_B16   |
| D_DIAGSTSDEFVEHSPDBIT_CNT_B16       |
| D_DIAGSTSDEFTEMPBIT_CNT_B16         |
| D_DIAGSTSSCOMHWANOTVALIDBIT_CNT_B16 |
| D_DIAGSTSWIRDISABLEBIT_CNT_B16      |

###  [section-1]

### Module specific Lookup Tables Constants

| Constant Name                    | Resolution | Value    | Software Segment |
|----------------------------------|------------|----------|------------------|
| T_DiagMgrDiagSts_Ptr_b16\[SIZE\] | N/A        | Refer \* | AP_DIAGMGR_CONST |
| T_DiagMgrRmpRate_Ptr_f32\[SIZE\] | N/A        | Refer \* | AP_DIAGMGR_CONST |
|                                  |            |          |                  |

Note: “ Refer \*” - Refer to Diagnostics_Manager_GeneratedCfg_MDD

Note Size and elements of Table constants varies across projects. Check
project configuration files Under UTP/ Contract folder for data.

#  Functions/Macros used by the Sub-Modules 

## Library Functions / Macros 

The library and functions / Macros that are called by the various sub
modules are identified below,

1.  TableSize_m()

## Data Hiding Functions

1.  \<None\>

## Global Functions/Macros Defined by this Module

### Diagnostic Manager Periodic 1

| **Function Name**    | DiagMgr_Per1 | Type | Min | Max |
|----------------------|--------------|------|-----|-----|
| **Arguments Passed** | none         |      |     |     |
| **Return Value**     | none         |      |     |     |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DiagMgr/doc/mediax/media/image1.emf)

## Local Functions/Macros Used by this MDD only

### Read Bits

| **Function Name**    | ReadBit_u16 | Type    | Min   | Max  |
|----------------------|-------------|---------|-------|------|
| **Arguments Passed** | Data        | Uint16  | 0     | FULL |
|                      | BitMask     | Uint16  | 0     | FULL |
| **Return Value**     |             | Boolean | FALSE | TRUE |

#### Description

IF (Data & BitMask) = 0

Return (FALSE)

ELSE  
Return(TRUE)

END IF

# Software Module Implementation

## Runtime Environment (RTE) Initial Values

| Data | Value |
|------|-------|
|      |       |

## Initialization Functions

None

## Periodic Functions

None

## Fault Recovery Functions

None

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
|               |                   |                                                 |

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

| Name of Sub Module | Software Segment |
|--------------------|------------------|
| DiagMgr_Per1       | AP_DIAGMGR_CODE  |
| ReadBit_u16        | AP_DIAGMGR_CODE  |

#  [section-4]

#  Known Issues / Limitations With Design

1.  (Item \#1)

# Revision Control Log

| **Rev \#** | **Change Description**                                | **Date**   | **Author Initials** |
|-------|-------------------------------------------|------------|------------|
| 1          | Initial MDD version                                   | 14-Feb-13  | VK                  |
| 2          | Changes made to make it more generic for all projects | 24-June-13 | NRAR                |

{% endraw %}