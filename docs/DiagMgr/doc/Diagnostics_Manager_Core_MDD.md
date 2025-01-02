---
layout: default
title: Diagnostics_Manager_Core_MDD
nav_order: 3
parent: Diagnostic Manager
---
{% raw %}
# Module -- Diagnostics Manager Core [module----diagnostics-manager-core]

# High-Level Description

# Figures

## Component Diagram 

# Variable Data Dictionary

| Module Inputs          | Module Outputs |     |
|------------------------|----------------|-----|
| MEC_Cnt_enum           |                |     |
| MfgDiagInhibit_Cnt_lgc |                |     |
| SystemState_Mode       |                |     |

## Module Internal Variables

<table>
<colgroup>
<col style="width: 27%" />
<col style="width: 9%" />
<col style="width: 9%" />
<col style="width: 10%" />
<col style="width: 10%" />
<col style="width: 10%" />
<col style="width: 22%" />
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
<th>Multiplicity</th>
<th><p>Software Segment</p>
<p>{Data Type}</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>NTCStrgArray_Cnt_str</td>
<td>NTCStrgArray</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>1:1</td>
<td>DIAGMGR_START_SEC_VAR_SAVED_ZONEHGS_UNSPECIFIED</td>
</tr>
<tr class="even">
<td>NTCBlackBoxData_Cnt_str</td>
<td>NTCBlkBoxData</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>1:1</td>
<td>DIAGMGR_START_SEC_VAR_SAVED_ZONEHGS_UNSPECIFIED</td>
</tr>
<tr class="odd">
<td>DEMEventActive_Cnt_M_lgc[D_NUMOFDEMEVENTS_CNT_U08+1]</td>
<td>Boolean</td>
<td>N/A</td>
<td>FALSE</td>
<td>TRUE</td>
<td>1:1</td>
<td>DIAGMGR_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="even">
<td>ResetNTCFlag_Cnt_M_u08</td>
<td>Refer *</td>
<td>Refer *</td>
<td>Refer *</td>
<td>Refer *</td>
<td>Refer *</td>
<td>Refer *</td>
</tr>
<tr class="odd">
<td>DiagMgr_NTCInfo#_Cnt_M_str</td>
<td>Refer *</td>
<td>Refer *</td>
<td>Refer *</td>
<td>Refer *</td>
<td>Refer *</td>
<td>Refer *</td>
</tr>
<tr class="even">
<td></td>
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
<td>NTCStrgArray</td>
<td></td>
<td>NTCStrg</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>NTCBlkBoxData</td>
<td></td>
<td>NTCBlkBoxType</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td rowspan="10">typedef struct { } NTCBlkBoxType</td>
<td>NTC_Cnt_u08</td>
<td>Uint8</td>
<td>1</td>
<td>FULL</td>
</tr>
<tr class="even">
<td>Param_Cnt_u08</td>
<td>Uint8</td>
<td>0</td>
<td>FULL</td>
</tr>
<tr class="odd">
<td>SystemState_Cnt_u08</td>
<td>Uint8</td>
<td>0</td>
<td>4</td>
</tr>
<tr class="even">
<td>VehSpd_Kph_u8p0</td>
<td>Uint8</td>
<td>0</td>
<td>FULL</td>
</tr>
<tr class="odd">
<td>BlkBoxCfgData1</td>
<td>Uint32</td>
<td>0</td>
<td>FULL</td>
</tr>
<tr class="even">
<td>BlkBoxCfgData2</td>
<td>Uint32</td>
<td>0</td>
<td>FULL</td>
</tr>
<tr class="odd">
<td>BlkBoxCfgData3</td>
<td>Uint32</td>
<td>0</td>
<td>FULL</td>
</tr>
<tr class="even">
<td>HwTrq_HwNm_s4p11</td>
<td>Sint16</td>
<td>-10</td>
<td>10</td>
</tr>
<tr class="odd">
<td>MtrTrq_MtrNm_s4p11</td>
<td>Sint16</td>
<td>-8.8</td>
<td>8.8</td>
</tr>
<tr class="even">
<td>IgnCtr_Cnt_u16</td>
<td>Uint16</td>
<td>0</td>
<td>FULL</td>
</tr>
<tr class="odd">
<td rowspan="5">typedef struct { } NTCStrg</td>
<td>NTC</td>
<td>NTCNumber</td>
<td>0</td>
<td>511</td>
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
<td>FULL</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
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

| Constant Name               |
|-----------------------------|
| k_FltRspTbl_Cnt_str\[\]     |
| k_FltRmpRate_UlspmS_f32\[\] |

##  [section]

## Program(fixed) Constants

### Embedded Constants

#### Local

| Constant Name                           | Resolution             | Units  | Value      |
|-----------------------------------|---------|--------|----------------------|
| D_FLTRSPNTCACTIVEBIT_CNT_B32            | N/A                    | Counts | 0x00800000 |
| D_FLTRSPRECOVERABLEBIT_CNT_B32          | N/A                    | Counts | 0x00400000 |
| D_FLTRSPHWASBSYSTMFLTBIT_CNT_B32        | N/A                    | Counts | 0x00200000 |
| D_FLTRSPDEFVEHSPDBIT_CNT_B32            | N/A                    | Counts | 0x00100000 |
| D_FLTRSPDEFTEMPBIT_CNT_B32              | N/A                    | Counts | 0x00080000 |
| D_FLTRSPSCOMHWANOTVALIDBIT_CNT_B32      | N/A                    | Counts | 0x00040000 |
| D_FLTRSPWIRDISABLEBIT_CNT_B32           | N/A                    | Counts | 0x00008000 |
| D_FLTRSPPWRCYCLTCHBIT_CNT_B32           | N/A                    | Counts | 0x00000010 |
| D_FLTRSPNTCINHIBITNOTOPERATEBIT_CNT_B32 | N/A                    | Counts | 0x00000020 |
| D_FLTRSPNTCINHIBITRUNBIT_CNT_B32        | N/A                    | Counts | 0x00000040 |
| D_FLTRSPRAMPBITS_CNT_B32                | N/A                    | Counts | 0x0000000F |
| D_FLTRSPBLKBOXBITS_CNT_B32              | N/A                    | Counts | 0x00003800 |
| D_BLKBOXBITOFFSET_CNT_U08               | N/A                    | Counts | 11         |
| D_RAMPNONE_CNT_U8                       | 1                      | Counts | 0x0F       |
| D_RAMPF2_CNT_U8                         | 1                      | Counts | 0x0E       |
| D_RAMPF1_CNT_U8                         | 1                      | Counts | 0x0D       |
|                                         |                        |        |            |
| D_DIAGRMPRTLOLMT_ULSPMS_F32             | Single precision float | Uls/mS | 0.0001     |
| D_DIAGRMPRTHILMT_ULSPMS_F32             | Single precision float | Uls/mS | 0.5        |

#### Global

| Constant Name          |
|------------------------|
| D_NTCACTIVEBITS_CNT_B8 |

###  [section-1]

### Module specific Lookup Tables Constants

| Constant Name                          | Resolution | Value    | Software Segment |
|-------------------|---------|----------------------------------|------------|
| T_NTCMapTbl#\_Cnt_enum\[SIZE\]         | N/A        | Refer \* | AP_DIAGMGR_CONST |
| T_DiagMgrNtcAppInfoMap_Cnt_Str\[SIZE\] | N/A        | Refer \* | AP_DIAGMGR_CONST |
| T_DiagMgrNtcInfoPtr_Cnt_Str\[SIZE\]    | N/A        | Refer \* | AP_DIAGMGR_CONST |

Note: “ Refer \*” - Refer to Diagnostics_Manager_GeneratedCfg_MDD

Note Size and elements of Table constants varies across projects. Check
project configuration files Under UTP/ Contract folder for data.

#  Functions/Macros used by the Sub-Modules 

## Library Functions / Macros 

The library and functions / Macros that are called by the various sub
modules are identified below,

1.  TableSize_m()

2.  

## Data Hiding Functions

1.  \<None\>

## Function Mapping

1.  DiagMgr_ReportDet(errorId) ↔ Det_ReportError(0,0,0,errorId)

## Global Functions/Macros Defined by this Module

### Diagnostic Manager Initialization

Note: \*doc in below table is Diagnostics_Manager_GeneratedCfg_MDD

|                      |                                    |                                                              |     |     |
|-------------|-------------------------------|-------------|--------|--------|
| **Function Name**    | DiagMgr_Init_Core                  | Type                                                         | Min | Max |
| **Arguments Passed** | NTCInfo_Cnt_T_str\[SIZE\]          | Refer Range of DiagMgr_NTCInfo#\_Cnt_M_str\[SIZE\] in \*doc  |     |     |
|                      | NumElements_Cnt_T_u08              | Refer Range of DIAGMGR_EVENTNUM\_# in \*doc                  |     |     |
|                      | CurrentAppIdx_Cnt_T_u08            | Refer Range of DIAGMGR_APID\_# in \*doc                      |     |     |
|                      | DiagMgrInitComp_Ptr_T_lgc          | Refer Range of DiagMgrInitComp#\_Cnt_M_lgc                   |     |     |
|                      | NTCInfoQueue_Cnt_T_str\[5\]        | Refer Range of NTCInfoQueue#\_Cnt_M_str\[SIZE\] in \*doc     |     |     |
|                      | NTCQueueIndex_Ptr_T_u08            | Refer Range of NTCQueueIndex#\_Cnt_M_u08 in \*doc            |     |     |
|                      | DiagSts_Cnt_T_b16\[SIZE\]          | Refer Range of DiagSts#\_Cnt_M_b16\[SIZE\] in \*doc          |     |     |
|                      | ActiveRmpRate_UlspmS_T_f32\[SIZE\] | Refer Range of ActiveRmpRate#\_UlspmS_M_f32\[SIZE\] in \*doc |     |     |
|                      | ActDiagSts_Ptr_T_u08               | Refer Range of ActDiagSts#\_Cnt_M_u08 in \*doc               |     |     |
| **Return Value**     | none                               |                                                              |     |     |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DiagMgr/doc/mediax/media/image1.emf)

### Diagnostic Manager Periodic Code

Note: \*doc in below table is Diagnostics_Manager_GeneratedCfg_MDD

|                      |                                    |                                                              |     |     |
|--------------|------------------------|---------------------|-------|-------|
| **Function Name**    | DiagMgr_Per_Core                   | Type                                                         | Min | Max |
| **Arguments Passed** | NTCInfo_Cnt_T_str\[SIZE\]          | Refer Range of DiagMgr_NTCInfo#\_Cnt_M_str\[SIZE\] in \*doc  |     |     |
|                      | NumElements_Cnt_T_u08              | Refer Range of DIAGMGR_EVENTNUM\_# in \*doc                  |     |     |
|                      | DiagSts_Cnt_T_b16\[SIZE\]          | Refer Range of DiagSts#\_Cnt_M_b16\[SIZE\] in \*doc          |     |     |
|                      | ActiveRmpRate_UlspmS_T_f32\[SIZE\] | Refer Range of ActiveRmpRate#\_UlspmS_M_f32\[SIZE\] in \*doc |     |     |
|                      | ActDiagStsIdx_Ptr_T_u08            | Refer Range of ActDiagSts#\_Cnt_M_u08 in \*doc               |     |     |
|                      | T_NTCMapTbl_Cnt_enum\[SIZE\]       | Refer range of T_NTCMapTbl#\_Cnt_enum\[SIZE\] in \*doc       |     |     |
|                      | PrevResetNTCFlag_Ptr_T_u08         | Refer Range of ResetNTCFlag#\_Cnt_M_u08 in \*doc             |     |     |
| **Return Value**     | none                               |                                                              |     |     |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DiagMgr/doc/mediax/media/image2.emf)

### Diagnostic Manager Transition Core

Note: \*doc in below table is Diagnostics_Manager_GeneratedCfg_MDD

|                      |                            |                                                             |     |     |
|--------------|-----------------------|--------------|-----------|-----------|
| **Function Name**    | DiagMgr_Trns_Core          | Type                                                        | Min | Max |
| **Arguments Passed** | NTCInfo_Cnt_T_str\[SIZE\]  | Refer Range of DiagMgr_NTCInfo#\_Cnt_M_str\[SIZE\] in \*doc |     |     |
|                      | NumElements_Cnt_T_u08      | Refer Range of DIAGMGR_EVENTNUM\_# in \*doc                 |     |     |
|                      | T_NTCMapTbl_Cnt_enum\[79\] | Refer range of T_NTCMapTbl#\_Cnt_enum\[SIZE\] in \*doc      |     |     |
| **Return Value**     | none                       |                                                             |     |     |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DiagMgr/doc/mediax/media/image3.emf)

### Diagnostic Manager Get NTC Failed

|                      |                               |                       |          |      |
|----------|---------------------|----------------------|----------|-----------|
| **Function Name**    | NxtrDiagMgr_GetNTCFailed_Core | Type                  | Min      | Max  |
| **Arguments Passed** | NTC_Cnt_T_enum                | NTCNumber             | 0        | 511  |
|                      | NTCFailed_Ptr_T_lgc           | const boolean pointer | False    | True |
| **Return Value**     | RetVal                        | Std_ReturnType        | E_NOT_OK | E_OK |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DiagMgr/doc/mediax/media/image4.emf)

### Diagnostic Manager Get NTC Active

|                      |                               |                       |          |      |
|--------------|------------------------|-------------------|---------|-------|
| **Function Name**    | NxtrDiagMgr_GetNTCActive_Core | Type                  | Min      | Max  |
| **Arguments Passed** | NTC_Cnt_T_enum                | NTCNumber             | 0        | 511  |
|                      | NTCActive_Ptr_T_lgc           | const boolean pointer | FALSE    | TRUE |
| **Return Value**     | RetVal                        | Std_ReturnType        | E_NOT_OK | E_OK |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DiagMgr/doc/mediax/media/image5.emf)

### Diagnostic Manager Get NTC Status

<table>
<colgroup>
<col style="width: 13%" />
<col style="width: 35%" />
<col style="width: 17%" />
<col style="width: 15%" />
<col style="width: 17%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Function Name</strong></td>
<td>NxtrDiagMgr_GetNTCStatus_Core</td>
<td>Type</td>
<td>Min</td>
<td>Max</td>
</tr>
<tr class="even">
<td><strong>Arguments Passed</strong></td>
<td>NTC_Cnt_T_enum</td>
<td>NTCNumber</td>
<td>0</td>
<td>511</td>
</tr>
<tr class="odd">
<td></td>
<td>Status_Ptr_T_u08</td>
<td>const boolean pointer</td>
<td>FALSE</td>
<td>TRUE</td>
</tr>
<tr class="even">
<td><strong>Return Value</strong></td>
<td>RetVal</td>
<td>Std_ReturnType</td>
<td colspan="2"><p>E_OK</p>
<p>E_NOT_OK</p></td>
</tr>
</tbody>
</table>

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DiagMgr/doc/mediax/media/image6.emf)

### Diagnostic Manager Set NTC Status

Note: \*doc in below table is Diagnostics_Manager_GeneratedCfg_MDD

<table>
<colgroup>
<col style="width: 13%" />
<col style="width: 35%" />
<col style="width: 17%" />
<col style="width: 15%" />
<col style="width: 17%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Function Name</strong></td>
<td>NxtrDiagMgr_SetNTCStatus_Core</td>
<td>Type</td>
<td>Min</td>
<td>Max</td>
</tr>
<tr class="even">
<td><strong>Arguments Passed</strong></td>
<td>NTC_Cnt_T_enum</td>
<td>NTCNumber</td>
<td>0</td>
<td>511</td>
</tr>
<tr class="odd">
<td></td>
<td>Param_Cnt_T_u08</td>
<td>Uint8</td>
<td>0</td>
<td>FULL</td>
</tr>
<tr class="even">
<td></td>
<td>Status_Cnt_T_enum</td>
<td>NxtrDiagMgrStatus</td>
<td colspan="2"><p>NTC_STATUS_PASSED</p>
<p>NTC_STATUS_FAILED</p>
<p>NTC_STATUS_PREPASSED</p>
<p>NTC_STATUS_PREFAILED</p></td>
</tr>
<tr class="odd">
<td></td>
<td>NTCInfo_Cnt_T_str[79]</td>
<td colspan="3">Refer Range of DiagMgr_NTCInfo#_Cnt_M_str[SIZE] in
*doc</td>
</tr>
<tr class="even">
<td></td>
<td>DiagSts_Cnt_T_b16[2]</td>
<td colspan="3">Refer Range of DiagSts#_Cnt_M_b16[SIZE] in *doc</td>
</tr>
<tr class="odd">
<td></td>
<td>ActiveRmpRate_Cnt_T_f32[2]</td>
<td colspan="3">Refer Range of ActiveRmpRate#_UlspmS_M_f32[SIZE] in
*doc</td>
</tr>
<tr class="even">
<td></td>
<td>ActDiagSts_Ptr_T_u08</td>
<td colspan="3">Refer Range of ActDiagSts#_Cnt_M_u08 in *doc</td>
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

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DiagMgr/doc/mediax/media/image8.emf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DiagMgr/doc/mediax/media/image9.emf)

### Diagnostic Manager Report NTC Status

> Note: \*doc in below table is Diagnostics_Manager_GeneratedCfg_MDD

<table style="width:100%;">
<colgroup>
<col style="width: 13%" />
<col style="width: 35%" />
<col style="width: 17%" />
<col style="width: 15%" />
<col style="width: 17%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Function Name</strong></td>
<td>NxtrDiagMgr_ReportNTCStatus_Core</td>
<td>Type</td>
<td>Min</td>
<td>Max</td>
</tr>
<tr class="even">
<td><strong>Arguments Passed</strong></td>
<td>NTC_Cnt_T_enum</td>
<td>NTCNumber</td>
<td>0</td>
<td>511</td>
</tr>
<tr class="odd">
<td></td>
<td>Param_Cnt_T_u08</td>
<td>Uint8</td>
<td>0</td>
<td>FULL</td>
</tr>
<tr class="even">
<td></td>
<td>Status_Cnt_T_enum</td>
<td>NxtrDiagMgrStatus</td>
<td colspan="2"><p>NTC_STATUS_PASSED</p>
<p>NTC_STATUS_FAILED</p>
<p>NTC_STATUS_PREPASSED</p>
<p>NTC_STATUS_PREFAILED</p></td>
</tr>
<tr class="odd">
<td></td>
<td>NTCInfoQueue_Cnt_T_str [5]</td>
<td colspan="3">Refer Range of NTCInfoQueue#_Cnt_M_str[SIZE] in
*doc</td>
</tr>
<tr class="even">
<td></td>
<td>NTCQueueIndex_Ptr_T_u08</td>
<td colspan="3">Refer Range of NTCQueueIndex#_Cnt_M_u08 in *doc</td>
</tr>
<tr class="odd">
<td><strong>Return Value</strong></td>
<td></td>
<td>Std_ReturnType</td>
<td colspan="2">E_OK</td>
</tr>
</tbody>
</table>

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DiagMgr/doc/mediax/media/image10.emf)

## Local Functions/Macros Used by this MDD only

### Set Bits

|                      |            |                     |     |     |
|----------------------|------------|---------------------|-----|-----|
| **Function Name**    | SetBits_u8 | Type                | Min | Max |
| **Arguments Passed** | Data       | const uint8 pointer | 0   | 255 |
|                      | BitMask    | uint8               | 0   | 255 |
| **Return Value**     | N/A        |                     |     |     |

#### Description

\*Data \|= BitMask

### Clear Bits

|                      |            |                     |     |     |
|----------------------|------------|---------------------|-----|-----|
| **Function Name**    | ClrBits_u8 | Type                | Min | Max |
| **Arguments Passed** | Data       | const uint8 pointer | 0   | 255 |
|                      | BitMask    | uint8               | 0   | 255 |
| **Return Value**     | N/A        |                     |     |     |

#### Description

\*Data &= \~BitMask

### Read Bit

|                      |             |         |      |      |
|----------------------|-------------|---------|------|------|
| **Function Name**    | ReadBit_u8  | Type    | Min  | Max  |
| **Arguments Passed** | Data        | uint8   | 0    | 255  |
|                      | BitMask     | uint8   | 0    | 255  |
| **Return Value**     | (anonymous) | boolean | FULL | FULL |

#### Description

IF 0 = (Data & BitMask) THEN

return FALSE

ELSE

return TRUE

ENDIF

### Set Bits

|                      |             |                      |      |      |
|----------------------|-------------|----------------------|------|------|
| **Function Name**    | SetBits_u16 | Type                 | Min  | Max  |
| **Arguments Passed** | Data        | const uint16 pointer | FULL | FULL |
|                      | BitMask     | uint16               | FULL | FULL |
| **Return Value**     | N/A         |                      |      |      |

#### Description

\*Data \|= BitMask

### Read Bit

|                      |             |         |          |          |
|----------------------|-------------|---------|----------|----------|
| **Function Name**    | ReadBit_u32 | Type    | Min      | Max      |
| **Arguments Passed** | Data        | uint32  | 0x000000 | 0xFFFFFF |
|                      | BitMask     | uint32  | 0x000000 | 0xFFFFFF |
| **Return Value**     | (anonymous) | boolean | FULL     | FULL     |

#### Description

IF 0 = (Data & BitMask) THEN

return FALSE

ELSE

return TRUE

ENDIF

### Process Diagnostic Status

|                      |                   |                      |     |      |
|----------------------|-------------------|----------------------|-----|------|
| **Function Name**    | ProcessDiagSts    | Type                 | Min | Max  |
| **Arguments Passed** | FltRsp_Cnt_T_u32  | Uint32               | 0   | FULL |
|                      | DiagSts_Ptr_T_b16 | const uint16 pointer | 0   | FULL |
| **Return Value**     | N/A               |                      |     |      |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DiagMgr/doc/mediax/media/image11.emf)

### Process Ramp Response

|                      |                         |                       |        |      |
|---------------|----------------------|-------------------|---------|---------|
| **Function Name**    | ProcessRampResponse     | Type                  | Min    | Max  |
| **Arguments Passed** | FltRsp_Cnt_T_u32        | Uint32                | 0      | FULL |
|                      | ActiveRmpRate_Ptr_T_f32 | Const float32 pointer | 0.0001 | 0.5  |
|                      | DiagSts_Ptr_T_b16       | Const uint16 pointer  | 0      | FULL |
| **Return Value**     | N/A                     |                       |        |      |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DiagMgr/doc/mediax/media/image12.emf)

### Failed Check and Processing

|                      |                          |                          |                   |                   |
|---------------|----------------------|-------------------|---------|---------|
| **Function Name**    | FailedCheckAndProcessing | Type                     | Min               | Max               |
| **Arguments Passed** | NTCInfo_Ptr_T_str        | const uint16 NTCInfo_Str | See section 3.1.1 | See section 3.1.1 |
|                      | DiagSts_Ptr_T_b16        | const uint16 pointer     | 0                 | FULL              |
|                      | MaxRampRate_Ptr_T_f32    | Const float32 pointer    | 0.0001            | 0.5               |
|                      | NTC_Cnt_T_enum           | NTCNumber                | 0                 | 511               |
| **Return Value**     | N/A                      |                          |                   |                   |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/DiagMgr/doc/mediax/media/image13.emf)

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

| Name of Sub Module       | Software Segment |
|--------------------------|------------------|
| FailedCheckAndProcessing | AP_DIAGMGR_CODE  |
| ProcessRampResponse      | AP_DIAGMGR_CODE  |
| ProcessDiagSts           | AP_DIAGMGR_CODE  |
| SetBits_u8               | AP_DIAGMGR_CODE  |
| ClrBits_u8               | AP_DIAGMGR_CODE  |
| ReadBit_u8               | AP_DIAGMGR_CODE  |
| ReadBit_u32              | AP_DIAGMGR_CODE  |
| SetBits_u16              | AP_DIAGMGR_CODE  |

#  [section-4]

#  Known Issues / Limitations With Design

1.  (Item \#1)

# Revision Control Log

|            |                                                      |              |                     |
|-------|-------------------------------------------|------------|------------|
| **Rev \#** | **Change Description**                               | **Date**     | **Author Initials** |
| 1          | Initial MDD version                                  | 14-Feb-13    | VK                  |
| 2          | MDD catch up to match latest SRC Ver 4               | 24- June- 13 | NRAR                |
| 3          | Updates/cleanup while adding latch active diagnostic | 5-OCT-13     | Jared               |

{% endraw %}