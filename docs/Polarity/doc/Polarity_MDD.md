---
layout: default
title: Polarity_MDD
nav_order: 2
parent: Polarity (Motor...)
---
{% raw %}
# Module --  [module---]

# High-Level Description

This module implements the polarity assignments for the EPS systems to
allow for various configurations of input and output signals for proper
alignment.

#  Figures

## Diagram – Component Diagram

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/Polarity/doc/mediax/media/image1.tiff"
style="width:4.02115in;height:3.08753in" alt="Polarity.tif" />

## Diagram – Function Data Sharing

No shared data.

#  Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

| Module Inputs                   | Module Outputs |                                    |
|-----------------------------------|--|------------------------------------|
| DiagHwTrqPolarity_Cnt_s08       |                | HwTrqPolarity_Cnt_s08              |
| DiagHwPosPolarity_Cnt_s08       |                | HwPosPolarity_Cnt_s08              |
| DiagMtrPosPolarity_Cnt_s08      |                | MtrPosPolarity_Cnt_s08             |
| DiagMtrVelPolarity_Cnt_s08      |                | MtrVelPolarity_Cnt_s08             |
| DiagMtrElecMechPolarity_Cnt_s08 |                | MtrElecMechPolarity_Cnt_s08        |
| DiagAssistAssyPolarity_Cnt_s08  |                | AssistAssyPolarity_Cnt_s08         |
|                                 |                | SysC\_ MtrElecMechPolarity_Cnt_s32 |

## Module Internal Variables

This section identifies the name, range and resolutions for module
specific data created by this module. If there are no range restrictions
on the variable, the term “FULL” is placed into the table for legal
range.

<table>
<colgroup>
<col style="width: 21%" />
<col style="width: 13%" />
<col style="width: 12%" />
<col style="width: 13%" />
<col style="width: 13%" />
<col style="width: 27%" />
</colgroup>
<thead>
<tr class="header">
<th>Variable Name</th>
<th>Data Type</th>
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
<td>Polarity_Cnt_Str</td>
<td>Polarity_DataType</td>
<td>N/A</td>
<td>See DataType</td>
<td>See DataType</td>
<td>**NvM/Per-Instance Memory**</td>
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
<td>Polarity_DataType</td>
<td>Polarity_Cnt_b08</td>
<td>uint8</td>
<td>Full</td>
<td>Full</td>
</tr>
<tr class="even">
<td></td>
<td>R_Polarity_Cnt_b08</td>
<td>uint8</td>
<td>Full</td>
<td>Full</td>
</tr>
</tbody>
</table>

# Constant Data Dictionary

## Calibration Constants

This section lists the calibrations used by the module. For details on
calibration constants, refer to the Data Dictionary for the application.

| Constant Name |
|---------------|
|               |

## Program(fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

| Constant Name            | Resolution | Units  | Value |
|--------------------------|------------|--------|-------|
|                          |            |        |       |
|                          |            |        |       |
| D_HWTRQPOL_CNT_B08       | 1          | Counts | 0x01  |
| D_HWPOSPOL_CNT_B08       | 1          | Counts | 0x02  |
| D_MTRPOSPOL_CNT_B08      | 1          | Counts | 0x04  |
| D_MTRVELPOL_CNT_B08      | 1          | Counts | 0x08  |
| D_ASSTASSEMPOL_CNT_B08   | 1          | Counts | 0x10  |
| D_MTRELECMECHPOL_CNT_B08 | 1          | Counts | 0x20  |
|                          |            |        |       |
|                          |            |        |       |
|                          |            |        |       |

####  [section]

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

| Constant Name   |
|-----------------|
| D_NEGONE_CNT_S8 |
| D_ONE_CNT_S8    |

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

1.  None

## Data Hiding Functions

1.  Rte_Pim_Polarity_Cnt_Str()

2.  Rte_Call_Polarity_WriteBlock()

## Global Functions/Macros Defined by this Module

N/A

## Local Functions/Macros Used by this MDD only

### GetPolarity

| **Function Name**    | GetPolarity            | Type  | Min  | Max  | UTP Tol. |
|----------------------|------------------------|-------|------|------|----------|
| **Arguments Passed** | Polarity_Cnt_T_b08     | uint8 | FULL | FULL |          |
|                      | PolarityMask_Cnt_T_b08 | uint8 | FULL | FULL |          |
| **Return Value**     | Polarity_Cnt_T_s08     | sint8 | -1   | 1    | 0        |

#### Description

# Software Module Implementation

## Runtime Environment (RTE) Initial Values

This section lists the initial values of data written by this module but
controlled by the RTE. After RTE initialization, the data in this table
will contain these values.

| Data                               | Value |
|------------------------------------|-------|
| AssistAssyPolarity_Cnt_s08         | 0     |
| HwPosPolarity_Cnt_s08              | 0     |
| HwTrqPolarity_Cnt_s08              | 0     |
| MtrElecMechPolarity_Cnt_s08        | 0     |
| MtrPosPolarity_Cnt_s08             | 0     |
| MtrVelPolarity_Cnt_s08             | 0     |
| SysC\_ MtrElecMechPolarity_Cnt_s32 | 0     |
| DiagHwTrqPolarity_Cnt_s08          | 0     |
| DiagHwPosPolarity_Cnt_s08          | 0     |
| DiagMtrPosPolarity_Cnt_s08         | 0     |
| DiagMtrVelPolarity_Cnt_s08         | 0     |
| DiagMtrElecMechPolarity_Cnt_s08    | 0     |
| DiagAssistAssyPolarity_Cnt_s08     | 0     |

## Initialization Functions

### Init: \_Init1

#### Design Rationale

During cold initialization, set all output ports to their values based
on the stored polarity calibration.

#### Program Flow Start

N/A

#### Store Module Inputs to Local Copies

N/A

#### Processing

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/Polarity/doc/mediax/media/image4.emf)

#### Store Local copy of outputs into Module Outputs

N/A

#### Program Flow End

N/A

## Periodic Functions

### Per: Polarity_Per1

#### Design Rationale

This function is checking the polarity signals sent out to the
application against the redundantly stored polarity bitfield. The
polarity outputs need to be fed back into this module as an input to
insure the check is done on the exact memory locations that are being
used during run-time to compute the polarity adjusted signals.

#### Program Flow Start

Rte_Call_Polarity_Per1_CP0_CheckpointReached()

#### Store Module Inputs to Local copies

*HwTrqPolarity_Cnt_T_s08* =
Rte_IRead_Polarity_Per1_DiagHwTrqPolarity_Cnt_s08()

*HwPosPolarity_Cnt_T_s08* =
Rte_IRead_Polarity_Per1_DiagHwPosPolarity_Cnt_s08()

*MtrPosPolarity_Cnt_T_s08* =
Rte_IRead_Polarity_Per1_DiagMtrPosPolarity_Cnt_s08()

*MtrVelPolarity_Cnt_T_s08* =
Rte_IRead_Polarity_Per1_DiagMtrVelPolarity_Cnt_s08()

*AssistAssyPolarity_Cnt_T_s08* =
Rte_IRead_Polarity_Per1_DiagAssistAssyPolarity_Cnt_s08()

*MtrElecMechPolarity_Cnt_T_s08* =
Rte_IRead_Polarity_Per1_DiagMtrElecMechPolarity_Cnt_s08()

#### Processing

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

Rte_Call_Polarity_Per1_CP1_CheckpointReached()

## Serial Communication Functions

## 

### SCom: Polarity_SCom_ReadPolarity

| **Function Name**    | Polarity_SCom_ReadPolarity | Type          | Min  | Max  |
|--------------|--------------------------------|----------|---------|---------|
| **Arguments Passed** | Polarity_Ptr_T_b08         | uint8 pointer | FULL | FULL |
| **Return Value**     | N/A                        |               |      |      |

#### Design Rationale

Read and return current polarity calibration to the testing tool.

#### Program Flow Start

N/A

#### Store Module Inputs to Local copies

N/A

#### (Processing of function)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/Polarity/doc/mediax/media/image7.emf)

#### Store Local copy of outputs into Module Outputs

N/A

#### Program Flow End

N/A

### SCom: Polarity_SCom_SetPolarity

| **Function Name**    | Polarity_SCom_SetPolarity | Type  | Min  | Max  |
|----------------------|---------------------------|-------|------|------|
| **Arguments Passed** | Polarity_Cnt_T_b08        | uint8 | FULL | FULL |
| **Return Value**     | N/A                       |       |      |      |

### Design Rationale

Suspend and Resume all interrupts are used around the updating of the
polarity outputs to prevent the function running the diagnostics (Per1)
from interrupting this function before all of the outputs are updated.

#### Program Flow Start

N/A

#### Store Module Inputs to Local copies

N/A

#### Processing

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/Polarity/doc/mediax/media/image8.emf)

#### Store Local copy of outputs into Module Outputs

N/A

#### Program Flow End

N/A

##  

# Execution Requirements

## Execution Sequence of the Module

N/A

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

| Function Name  | Calling Frequency                  | System State(s) in which the function is called |
|--------------------------|-----------------|------------------------------|
| Polarity_Init1 | Executed Once after RTE is started | ColdInit                                        |
| Polarity_Per1  | 10ms                               | All                                             |

## Execution Requirements for Serial Communication Functions 

| Function Name              | Sub-Module called by (Serial Comm Function Name) |
|-----------------------------|-------------------------------------------|
| Polarity_SCom_ReadPolarity |                                                  |
| Polarity_SCom_SetPolarity  |                                                  |

#  Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

| Name of Sub Module         | Software Segment |
|----------------------------|------------------|
| Polarity_Init1             |                  |
| Polarity_Per1              |                  |
| Polarity_SCom_ReadPolarity |                  |
| Polarity_SCom_SetPolarity  |                  |

##  [section-3]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

| Name of Sub Module | Software Segment             |
|--------------------|------------------------------|
| GetPolarity        | Inline with calling function |

#  [section-4]

#  Known Issues / Limitations With Design

#  Additional Comments

1.  The polarity bits for hand wheel torque, hand wheel position, motor
    position, and motor velocity (bits 0 - 4) are assumed to be used at
    the “sensor” level to place the signals in the proper orientation
    for use within the ECU. For example, hand wheel torque bit should be
    used to get the torque signals into the Nexteer CRF described in the
    polarity FDD-25.

2.  Porting a signal from CRF to MRF, or from MRF to CRF, shall be done
    with the assist assembly polarity bit (bit 5).

#  Revision Control Log

| **Item \#** | **Rev \#** | **Change Description**                                 | **Date**  | **Author Initials** |
|------|------|--------------------------------------------|---------|---------|
| 1           | 1          | Initial MDD                                            | 23May11   | NRAR                |
| 2           | 2          | Carried over from for component based design           | 14Nov11   | JWW                 |
| 3           | 3          | Updates and initial release for component based design | 21Apr2012 | KJS                 |
| 4           | 4          | Update for GSOD redundant output – FDDv006             | 22-Oct-12 | JWJ                 |
| 7           | 7          | Updated per FDD requirements                           | 19-Feb-13 | LWW                 |

{% endraw %}