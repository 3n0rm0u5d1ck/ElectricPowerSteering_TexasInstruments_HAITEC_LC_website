---
layout: default
title: Diagnostics_Manager_GeneratedCfg_MDD
nav_order: 6
parent: Diagnostic Manager
---
{% raw %}
# Module -- Core [module----core]

# High-Level Description

# Figures

## Component Diagram 

# Variable Data Dictionary

| Module Inputs | Module Outputs |     |
|---------------|----------------|-----|
|               |                |     |

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
<td>ResetNTCFlag_Cnt_M_u08</td>
<td>Uint8</td>
<td>1</td>
<td colspan="2"><p>0</p>
<p>FF</p></td>
<td>DIAGMGR#_START_SEC_VAR_CLEARED_8</td>
</tr>
<tr class="even">
<td>NTCQueueIndex#_Cnt_M_u08</td>
<td>Uint8</td>
<td>1</td>
<td colspan="2"><p>Range depends on size of
NTCInfoQueue#_Cnt_M_Str[SIZE]</p>
<p>Refer *</p></td>
<td>DIAGMGR#_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="odd">
<td>DiagMgrInitComp#_Cnt_M_lgc</td>
<td>Boolean</td>
<td>NA</td>
<td>False</td>
<td>True</td>
<td>DIAGMGR#_START_SEC_VAR_CLEARED_Unspecified</td>
</tr>
<tr class="even">
<td>DiagMgr_NTCInfo#_Cnt_M_str[SIZE]</td>
<td>NTCInfo_Str</td>
<td>NA</td>
<td>See section 3.1.1</td>
<td>See section 3.1.1</td>
<td>DIAGMGR#_START_SEC_VAR_CLEARED_Unspecified</td>
</tr>
<tr class="odd">
<td>NTCInfoQueue#_Cnt_M_str[SIZE]</td>
<td>NTCInfoQueue_Str</td>
<td>NA</td>
<td>See section 3.1.1</td>
<td>See section 3.1.1</td>
<td>DIAGMGR#_START_SEC_VAR_CLEARED_Unspecified</td>
</tr>
<tr class="even">
<td>ActDiagSts#_Cnt_M_u08</td>
<td>Uint8</td>
<td>1</td>
<td>0</td>
<td>1</td>
<td>DIAGMGR#_START_SEC_VAR_CLEARED_8</td>
</tr>
<tr class="odd">
<td>ResetNTCFlag#_Cnt_M_u08</td>
<td>Uint8</td>
<td>1</td>
<td colspan="2"><p>0</p>
<p>FF</p></td>
<td>DIAGMGR#_START_SEC_VAR_CLEARED_8</td>
</tr>
<tr class="even">
<td>DiagSts#_Cnt_M_b16[SIZE]</td>
<td>Uint16</td>
<td>1</td>
<td>0</td>
<td>FULL</td>
<td>DIAGMGR#_START_SEC_VAR_CLEARED_Unspecified</td>
</tr>
<tr class="odd">
<td>ActiveRmpRate#_UlspmS_M_f32[SIZE]</td>
<td>Float32</td>
<td>Single Precision float</td>
<td>0.0001</td>
<td>0.5</td>
<td>DIAGMGR#_START_SEC_VAR_CLEARED_32</td>
</tr>
</tbody>
</table>

Note: \*Refer: Size varies across projects. Check Configuration files
under UTP/Contract folder

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
<td rowspan="2"></td>
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
</tr>
<tr class="odd">
<td rowspan="3">typedef struct { } NTCInfo_Str</td>
<td>Param</td>
<td>uint8</td>
<td>0</td>
<td>FULL</td>
</tr>
<tr class="even">
<td>Status</td>
<td>uint8</td>
<td>0</td>
<td>FULL</td>
</tr>
<tr class="odd">
<td>AgingCounter</td>
<td>uint8</td>
<td>0</td>
<td>64</td>
</tr>
<tr class="even">
<td>typedef struct { } NTCInfoQueue_Str</td>
<td>NTC</td>
<td>NTCNumber</td>
<td>0</td>
<td>511</td>
</tr>
<tr class="odd">
<td></td>
<td>Param</td>
<td>Uint8</td>
<td>0</td>
<td>FULL</td>
</tr>
<tr class="even">
<td></td>
<td>Status</td>
<td>NxtrDiagMgrStatus</td>
<td>0</td>
<td>255</td>
</tr>
</tbody>
</table>

# Constant Data Dictionary

## Calibration Constants

| Constant Name               |
|-----------------------------|
| k_FltRspTbl_Cnt_str\[\]     |
| k_FltRmpRate_UlspmS_f32\[\] |

##  [section]

## Program(fixed) Constants

### Embedded Constants

#### Local

#### Global

| Constant Name            |
|--------------------------|
| \*\* DIAGMGR_NUMAPPS     |
| \*\* DIAGMGR_EVENTNUM\_# |
| \*\* DIAGMGR_APID\_#     |

### Note \*\*: Global const values varies across projects. Check configuration files under UTP/Contract folder. “#” denotes application number. [note-global-const-values-varies-across-projects.-check-configuration-files-under-utpcontract-folder.-denotes-application-number.]

### Module specific Lookup Tables Constants

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 11%" />
<col style="width: 48%" />
<col style="width: 15%" />
</colgroup>
<thead>
<tr class="header">
<th>Constant Name</th>
<th>Resolution</th>
<th>Value</th>
<th>Software Segment</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>T_NTCMapTbl#_Cnt_enum[SIZE]</td>
<td>N/A</td>
<td>{ ** }</td>
<td>AP_DIAGMGR_CONST</td>
</tr>
<tr class="even">
<td>T_DiagMgrNtcInfoPtr_Cnt_Str[SIZE]</td>
<td>N/A</td>
<td><p>** {&amp;DiagMgr_NTCInfo#_Cnt_M_str[0], #,</p>
<p>}</p></td>
<td>AP_DIAGMGR_CONST</td>
</tr>
<tr class="odd">
<td>T_DiagMgrNtcAppInfoMap_Cnt_Str[SIZE]</td>
<td>N/A</td>
<td><p>** {{ &amp;DiagMgr_NTCInfo#_Cnt_M_str[0], #},</p>
<p>…</p>
<p>}</p></td>
<td>AP_DIAGMGR_CONST</td>
</tr>
</tbody>
</table>

\*\*NOTE : Elements and Size of table are different across different
projects and applications. Check Configuration files under UTP/Contract
folder

#  Functions/Macros used by the Sub-Modules 

## Library Functions / Macros 

The library and functions / Macros that are called by the various sub
modules are identified below,

1.  TableSize_m()

2.  

## Data Hiding Functions

1.  \<None\>

2.  

## Global Functions/Macros Defined by this Module

### Diagnostic Manager Initialization

| **Function Name**    | DiagMgr#\_Init | Type | Min | Max |
|----------------------|----------------|------|-----|-----|
| **Arguments Passed** | None           |      |     |     |
| **Multiplicity**     |                |      |     |     |
| **Return Value**     | None           |      |     |     |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DiagMgr/doc/mediax/media/image1.emf)

### Diagnostic Manager Periodic Code

| **Function Name**    | DiagMgr#\_Per | Type | Min | Max |
|----------------------|---------------|------|-----|-----|
| **Arguments Passed** | None          |      |     |     |
| **Multiplicity**     |               |      |     |     |
| **Return Value**     | none          |      |     |     |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DiagMgr/doc/mediax/media/image2.emf)

### Diagnostic Manager Transition Core

| **Function Name**    | DiagMgr#\_Trns | Type | Min | Max |
|----------------------|----------------|------|-----|-----|
| **Arguments Passed** | None           |      |     |     |
| **Multiplicity**     |                |      |     |     |
| **Return Value**     | none           |      |     |     |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DiagMgr/doc/mediax/media/image3.emf)

### Diagnostic Manager Get NTC Failed

| **Function Name**    | NxtrDiagMgr#\_GetNTCFailed | Type                  | Min   | Max  |
|----------|---------------------|----------------------|----------|-----------|
| **Arguments Passed** | NTC_Cnt_T_enum             | NTCNumber             | 0     | 511  |
|                      | NTCFailed_Ptr_T_lgc        | const boolean pointer | False | True |
| **Multiplicity**     |                            |                       |       |      |
| **Return Value**     | RetVal                     | Std_ReturnType        | E_OK  |      |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DiagMgr/doc/mediax/media/image4.emf)

### Diagnostic Manager Get NTC Active

| **Function Name**    | NxtrDiagMgr#\_GetNTCActive_Core | Type                  | Min   | Max  |
|--------------|------------------------|-------------------|---------|-------|
| **Arguments Passed** | NTC_Cnt_T_enum                  | NTCNumber             | 0     | 511  |
|                      | NTCActive_Ptr_T_lgc             | const boolean pointer | FALSE | TRUE |
| **Multiplicity**     |                                 |                       |       |      |
| **Return Value**     | RetVal                          | Std_ReturnType        | E_OK  |      |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DiagMgr/doc/mediax/media/image5.emf)

### Diagnostic Manager Get NTC Status

| **Function Name**    | NxtrDiagMgr#\_GetNTCStatus | Type                  | Min   | Max  |
|----------|-------------------------|-------------|------------|-------------|
| **Arguments Passed** | NTC_Cnt_T_enum             | NTCNumber             | 0     | 511  |
|                      | Status_Ptr_T_u08           | const boolean pointer | FALSE | TRUE |
| **Multiplicity**     |                            |                       |       |      |
| **Return Value**     | RetVal                     | Std_ReturnType        | E_OK  |      |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DiagMgr/doc/mediax/media/image6.emf)

### Diagnostic Manager Set NTC Status

<table>
<colgroup>
<col style="width: 13%" />
<col style="width: 35%" />
<col style="width: 17%" />
<col style="width: 15%" />
<col style="width: 17%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Function Name</strong></th>
<th>NxtrDiagMgr#_SetNTCStatus</th>
<th>Type</th>
<th>Min</th>
<th>Max</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Arguments Passed</strong></td>
<td>NTC_Cnt_T_enum</td>
<td>NTCNumber</td>
<td>0</td>
<td>511</td>
</tr>
<tr class="even">
<td></td>
<td>Param_Cnt_T_u08</td>
<td>Uint8</td>
<td>0</td>
<td>FULL</td>
</tr>
<tr class="odd">
<td></td>
<td>Status_Cnt_T_enum</td>
<td>NxtrDiagMgrStatus</td>
<td colspan="2"><p>NTC_STATUS_PASSED</p>
<p>NTC_STATUS_FAILED</p>
<p>NTC_STATUS_PREPASSED</p>
<p>NTC_STATUS_PREFAILED</p></td>
</tr>
<tr class="even">
<td><strong>Multiplicity</strong></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><strong>Return Value</strong></td>
<td>RetVal</td>
<td>Std_ReturnType</td>
<td colspan="2"><p>E_OK</p>
<p>E_NOT_OK</p></td>
</tr>
</tbody>
</table>

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DiagMgr/doc/mediax/media/image7.emf)

### Diagnostic Manager Report NTC Status

<table style="width:100%;">
<colgroup>
<col style="width: 13%" />
<col style="width: 35%" />
<col style="width: 17%" />
<col style="width: 15%" />
<col style="width: 17%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Function Name</strong></th>
<th>NxtrDiagMgr#_ReportNTCStatus</th>
<th>Type</th>
<th>Min</th>
<th>Max</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Arguments Passed</strong></td>
<td>NTC_Cnt_T_enum</td>
<td>NTCNumber</td>
<td>0</td>
<td>511</td>
</tr>
<tr class="even">
<td></td>
<td>Param_Cnt_T_u08</td>
<td>Uint8</td>
<td>0</td>
<td>FULL</td>
</tr>
<tr class="odd">
<td></td>
<td>Status_Cnt_T_enum</td>
<td>NxtrDiagMgrStatus</td>
<td colspan="2"><p>NTC_STATUS_PASSED</p>
<p>NTC_STATUS_FAILED</p>
<p>NTC_STATUS_PREPASSED</p>
<p>NTC_STATUS_PREFAILED</p></td>
</tr>
<tr class="even">
<td><strong>Multiplicity</strong></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><strong>Return Value</strong></td>
<td>RetVal</td>
<td>Std_ReturnType</td>
<td colspan="2">E_OK</td>
</tr>
</tbody>
</table>

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DiagMgr/doc/mediax/media/image8.emf)

## Local Functions/Macros Used by this MDD only

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

#  [section-1]

#  Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

| Name of Sub Module            | Software Segment         |
|-------------------------------|--------------------------|
| DiagMgr#\_Init                | RTE_AP_DIAGMGR_APPL_CODE |
| DiagMgr#\_Per                 | RTE_AP_DIAGMGR_APPL_CODE |
| DiagMgr#\_Trns                | RTE_AP_DIAGMGR_APPL_CODE |
| NxtrDiagMgr#\_GetNTCFailed    | RTE_AP_DIAGMGR_APPL_CODE |
| NxtrDiagMgr#\_GetNTCActive    | RTE_AP_DIAGMGR_APPL_CODE |
| NxtrDiagMgr#\_GetNTCStatus    | RTE_AP_DIAGMGR_APPL_CODE |
| NxtrDiagMgr#\_SetNTCStatus    | RTE_AP_DIAGMGR_APPL_CODE |
| NxtrDiagMgr#\_ReportNTCStatus | RTE_AP_DIAGMGR_APPL_CODE |

##  [section-2]

## Global and Local Functions

This table identifies the software segments for local functions
identified in this module.

| Name of Sub Module | Software Segment |
|--------------------|------------------|
|                    |                  |

#  [section-3]

#  Known Issues / Limitations With Design

1.  (Item \#1)

# Revision Control Log

| **Rev \#** | **Change Description** | **Date**   | **Author Initials** |
|------------|------------------------|------------|---------------------|
| 1          | Initial MDD version    | 25-June-13 | NRAR                |

{% endraw %}