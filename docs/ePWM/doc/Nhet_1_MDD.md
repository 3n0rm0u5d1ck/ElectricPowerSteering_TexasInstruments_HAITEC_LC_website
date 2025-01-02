---
layout: default
title: Nhet_1_MDD
nav_order: 7
parent: Enhanced Pwm (TMS570)
---
{% raw %}
# Module – NHET [module-nhet]

# High-Level Description

This module implements NHET1 and HTU1 initialization per ES-34B NHET1
subfunctions, and NHET2 initialization, currently not documented in an
FDD.

# Figures

None

#  Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

| Module Inputs             | Module Outputs |                            |
|---------------------------|----------------|----------------------------|
| HET_INIT1_PST             |                | Nhet_Htu1RstFail_Cnt_G_lgc |
| HET_INIT0_PST             |                |                            |
| Nhet_HtuDataTrq_Cnt_G_str |                |                            |

## Module Internal Variables

This section identifies the name, range and resolutions for module
specific data created by this module. If there are no range restrictions
on the variable, the term “FULL” is placed into the table for legal
range.

<table>
<colgroup>
<col style="width: 24%" />
<col style="width: 21%" />
<col style="width: 13%" />
<col style="width: 13%" />
<col style="width: 28%" />
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
<td>Nhet_HtuDataTrq_Cnt_G_str</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>NHET_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
</tbody>
</table>

### User defined typedef definition/declaration 

This section documents any user types uniquely used for the module.

(Refer the included ref for more details of register)

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
<td>HtuDataTrq_Str</td>
<td>HtuDataTrq1_Cnt_u32 [8]</td>
<td>Uint32</td>
<td>0</td>
<td>FULL</td>
</tr>
<tr class="even">
<td></td>
<td>HtuDataTrq2_Cnt_u32 [8]</td>
<td>Uint32</td>
<td>0</td>
<td>FULL</td>
</tr>
</tbody>
</table>

# Constant Data Dictionary

## Calibration Constants

This section lists the calibrations used by the module. For details on
calibration constants, refer to the Data Dictionary for the application.

| Constant Name            |
|--------------------------|
| k_SENTSyncDelay_Cnt_u32  |
| k_SENTSyncTrgMin_Cnt_u32 |
| k_SPI50UOff_Cnt_u16      |
| k_SPI1mOff_Cnt_u16       |

## Program(fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

<table>
<colgroup>
<col style="width: 28%" />
<col style="width: 24%" />
<col style="width: 15%" />
<col style="width: 32%" />
</colgroup>
<thead>
<tr class="header">
<th>Variable Name</th>
<th>Resolution</th>
<th><p>Legal Range</p>
<p>(min)</p></th>
<th><p>Legal Range</p>
<p>(max)</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>D_INSTTODATARATIO_CNT_U16</td>
<td>1</td>
<td>Counts</td>
<td>4</td>
</tr>
<tr class="even">
<td>D_DATAFLDOFFSET_CNT_U16</td>
<td>1</td>
<td>Counts</td>
<td>8</td>
</tr>
<tr class="odd">
<td>D_BASEADDNHETRAM_CNT_U32</td>
<td>1</td>
<td>Counts</td>
<td>0xFF460000UL</td>
</tr>
<tr class="even">
<td>D_WCAPHTUADDR1_CNT_U32</td>
<td>1</td>
<td>Counts</td>
<td>D_BASEADDNHETRAM_CNT_U32 + (16U*pHET_T1MSGCNTST_0) + 8UL</td>
</tr>
<tr class="odd">
<td>D_WCAPHTUADDR2_CNT_U32</td>
<td>1</td>
<td>Counts</td>
<td>D_BASEADDNHETRAM_CNT_U32 + (16U*pHET_T2MSGCNTST_0) + 8UL</td>
</tr>
<tr class="even">
<td>D_CELEMENT_CNT_U16</td>
<td>1</td>
<td>Counts</td>
<td>8</td>
</tr>
<tr class="odd">
<td>D_CBUFLEN_CNT_U16</td>
<td>1</td>
<td>Counts</td>
<td>8</td>
</tr>
<tr class="even">
<td>D_CONFIGHETREGDMA_CNT_U32</td>
<td>1</td>
<td>Counts</td>
<td>Configurable. 0UL if no DMA needs to be enabled and 1UL if using
DMA</td>
</tr>
<tr class="odd">
<td>D_CFRAME_CNT_U16</td>
<td>1</td>
<td>Counts</td>
<td>(D_CBUFLEN_CNT_U16/D_CELEMENT_CNT_U16)</td>
</tr>
</tbody>
</table>

####  [section]

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

| Constant Name |
|---------------|
| None          |

### Module specific Lookup Tables Constants

| Constant Name | Resolution | Value | Software Segment |
|---------------|------------|-------|------------------|
| None          |            |       |                  |

#  Functions/Macros used by the Sub-Modules 

## Library Functions / Macros 

The library and functions / Macros that are called by the various sub
modules are identified below,

1.  HET Macros

2.  HTU MACROS

3.  Memcpy

## Data Hiding Functions

1.  None

## Global Functions/Macros Defined by this Module

### Global Functions \#1 (For detailed info regarding values assigned to registers refer Reference Pdf attached below)

|                      |            |      |     |     |          |
|----------------------|------------|------|-----|-----|----------|
| **Function Name**    | NHET_Init1 | Type | Min | Max | UTP Tol. |
| **Arguments Passed** | None       |      |     |     |          |
|                      |            |      |     |     |          |
| **Return Value**     | None       |      |     |     |          |

#### Design Rationale

All NHET1 initialization, including HTU1 initialization, is done before
enabling NHET1. All NHET2 initialization is done before enabling NHET2.
(NOTE that flowcharts are not accurate as of Rev 7 of this document; to
be updated as part of CR 12943.)

#### Description

**<u>NHET1 (called NHET1 in TI documentation and in FDDs; uses registers
named NHET0):</u>**

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ePWM/doc/mediax/media/image1.emf)

**<u>NHET2 (called NHET2 in TI documentation and in FDDs; uses registers
named NHET1):</u>**

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ePWM/doc/mediax/media/image2.emf)

## Local Functions/Macros Used by this MDD only

### Local Functions \#1 

###  [section-1]

|                      |           |      |     |     |          |
|----------------------|-----------|------|-----|-----|----------|
| **Function Name**    | HTU1_Init | Type | Min | Max | UTP Tol. |
| **Arguments Passed** | None      |      |     |     |          |
|                      |           |      |     |     |          |
| **Return Value**     | None      |      |     |     |          |

#### Design Rationale

Only one memory protection region is enabled; per TI documentation
updates, HTU access to NHET memory is independent of the HTU memory
protection and therefore the HTU memory protection only needs to be
configured to allow access to the R4 main memory region used by the HTU.

A global variable, Nhet_Htu1RstFail_Cnt_G_lgc, is used for the HTU1
Reset Test Fail flag, because the HTU1_Init function is called from ECU
Startup before the RTE is running.

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ePWM/doc/mediax/media/image3.emf)

# Software Module Implementation

## Runtime Environment (RTE) Initial Values

This section lists the initial values of data written by this module but
controlled by the RTE. After RTE initialization, the data in this table
will contain these values.

| Data | Value |
|------|-------|
| None |       |

## Initialization Functions

### Init: 

#### Design Rationale

This component does not have an RTE Init function, however NHET
direction register settings are configured in the integration project
and initialized in generated code. See the integration manual.

#### Module Outputs

None

#### Module Internal 

None

#### Initialize NHET Direction Register

## Periodic Functions

None

## Fault Recovery Functions

None

## Shutdown Functions

None

## Interrupt Functions

None

## Serial Communication Functions

None

## Transition Functions

None

##  

# Execution Requirements

## Execution Rates for sub-modules called by the Subroutine

This table serves as reference for the Scheduler design

| Global Function Name | Calling Frequency | Function in which the function is called |
|--------------------------|-----------------|------------------------------|
| NHET_Init1           | On Event          | ECU start up                             |
|                      |                   |                                          |

## Execution Requirements for Serial Communication Functions 

| Function Name | Sub-Module called by (Serial Comm Function Name) |
|---------------|--------------------------------------------------|
| None          |                                                  |

#  [section-3]

#  Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

| Name of Sub Module | Software Segment             |
|--------------------|------------------------------|
| NHET_Init1         | \#define NHET_START_SEC_CODE |
|                    |                              |

##  [section-4]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

| Name of Sub Module | Software Segment |
|--------------------|------------------|
| None               |                  |

#  [section-5]

#  Known Issues / Limitations With Design

1.  NOTE that the flowcharts have not been updated for the Rev 7 change.
    Flowcharts to be updated under CR 12943.

2.  

#  [section-6]

#  Reference 

Register Reference

# ![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ePWM/doc/mediax/media/image4.emf) [section-7]

#  [section-8]

# Revision Control Log

|            |                                                                               |           |                     |
|------|-----------------------------------------------|----------|---------|
| **Rev \#** | **Change Description**                                                        | **Date**  | **Author Initials** |
| 1.0        | Initial Version ( FDD 34B)                                                    |           | Selva               |
| 2.0        | Updated to FDD 34B v003                                                       | 19-Jun-13 | OT/SELVA            |
| 3.0        | Removed “NHETPINDIS” in Nhet1                                                 | 01-Aug-13 | Selva               |
| 4.0        | Updated to FDD34B v004                                                        | 4-Apr-14  | Selva               |
| 5.0        | Anomaly fix 6589 - Correct the value for the HTU MP0E register CR 11799       | 23-Apr-14 | SB                  |
| 6.0        | Anomaly fix 6844 - ePWM/ES34B: HTU is enabled before HTU MPU config is set up | 26-Nov-14 | VT                  |
| 7.0        | Updated per ES-34B v008                                                       | 28-Jan-15 | KMC                 |

{% endraw %}