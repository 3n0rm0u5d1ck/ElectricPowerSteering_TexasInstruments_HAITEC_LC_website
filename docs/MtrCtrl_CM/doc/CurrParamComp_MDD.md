---
layout: default
title: CurrParamComp_MDD
nav_order: 2
parent: Motor Control
---
{% raw %}
# Module -- Parameter Compensation [module----parameter-compensation]

# High-Level Description

# Figures

## Diagram – Function Data Sharing

None

### Diagram – Function (Name)

None

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrCtrl_CM/doc/mediax/media/image1.png"
style="width:2.55208in;height:2.91806in" />

#  Variable Data Dictionary [variable-data-dictionary]

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

| Module Inputs                    | Module Outputs |                   |
|----------------------------------|----------------|-------------------|
| MtrCurrDaxRef \_Amp_f32          |                | EstKe_VpRadpS_f32 |
| MtrCurrQaxRef\_ Amp_f32          |                | EstR_Ohm_f32      |
| CuTempEst_DegC_f32               |                | EstLq_Henry_f32   |
| MagTempEst_DegC_f32              |                | EstLd_Henry_f32   |
| SiTempEst_DegC_f32               |                |                   |
| FastDataAccessBufIndex_Cnt_M_u16 |                |                   |
|                                  |                |                   |
|                                  |                |                   |
|                                  |                |                   |
|                                  |                |                   |
|                                  |                |                   |

## Module Internal Variables

This section identifies the name, range and resolutions for module
specific data created by this module. If there are no range restrictions
on the variable, the term “FULL” is placed into the table for legal
range.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 14%" />
<col style="width: 13%" />
<col style="width: 10%" />
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
<td>EstKeFF_VpRadpS_M_f32</td>
<td>single precision float</td>
<td>0.025</td>
<td>0.075</td>
<td>CURRPARAMCOMP_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>EstRFF_Ohm_M_f32</td>
<td>single precision float</td>
<td>0.005</td>
<td>0.12565</td>
<td>CURRPARAMCOMP_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>KeSatSclFac_Uls_D_f32</td>
<td>single precision float</td>
<td>0</td>
<td>1</td>
<td>CURRPARAMCOMP_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>LqSatSclFac_Uls_D_f32</td>
<td>single precision float</td>
<td>0</td>
<td>2</td>
<td>CURRPARAMCOMP_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>LdSatSclFac_Uls_D_f32</td>
<td>single precision float</td>
<td>0</td>
<td>2</td>
<td>CURRPARAMCOMP_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>EstRfetFF_Ohm_D_f32</td>
<td>single precision float</td>
<td>0.005</td>
<td>0.12565</td>
<td>CURRPARAMCOMP_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>EstRmtrFF_Ohm_D_f32</td>
<td>single precision float</td>
<td>0.005</td>
<td>0.12565</td>
<td>CURRPARAMCOMP_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>PreLmtEstKe_VpRadpS_D_f32</td>
<td>single precision float</td>
<td>0.25</td>
<td>0.075</td>
<td>CURRPARAMCOMP_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>PreLmtEstLq_Henry_D_f32</td>
<td>single precision float</td>
<td>0.00003</td>
<td>0.00041</td>
<td>CURRPARAMCOMP_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>PreLmtEstLd_Henry_D_f32</td>
<td>single precision float</td>
<td>0.00003</td>
<td>0.00041</td>
<td>CURRPARAMCOMP_START_SEC_VAR_CLEARED_32</td>
</tr>
</tbody>
</table>

### User defined typedef definition/declaration 

This section documents any user types uniquely used for the module.

# Constant Data Dictionary

## Calibration Constants

This section lists the calibrations used by the module. For details on
calibration constants, refer to the Data Dictionary for the application.

| Constant Name                    |
|----------------------------------|
| t_KeSatTblX_Amp_u9p7             |
| t_KeSatTblY_Uls_u2p14            |
| t_KeSatTblX_Amp_u12p4            |
| t_CurrParamCompDaxRef_Amp_u9p7   |
| t_CurrParamCompQaxRef_Amp_u9p7   |
| t_CurrParamLqSatSclFac_Uls_u2p14 |
| k_MinKeRngLmt_VpRadpS_f32        |
| k_MaxKeRngLmt_VpRadpS_f32        |
| k_MinRRngLmt_Ohm_f32             |
| k_MaxRRngLmt_Ohm_f32             |
| k_MinLqRngLmt_Henry_f32          |
| k_MaxLqRngLmt_Henry_f32          |
| k_MinLdRngLmt_Henry_f32          |
| k_MaxLdRngLmt_Henry_f32          |
| k_NomTemp_DegC_f32               |
| k_MagThrC_VpRadpSpDegC_f32       |
| k_SiThermCoeff_OhmpDegC_f32      |
| k_NomRfet_Ohm_f32                |
| k_CuThermCoeff_OhmpDegC_f32      |
|                                  |
| k_NomLq_Henry_f32                |
| k_NomLd_Henry_f32                |
|                                  |

##  [section]

## Program(fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

| Constant Name              | Resolution             | Units    | Value          |
|-------------------------------|--------------|--------------|--------------|
| D_SQRT3OVR2_ULS_F32        | single precision float | Unitless | 0.866025403784 |
| D_MINRRANGE_OHM_F32        | single precision float | Ohm      | 0.005f         |
| D_MAXRRANGE_OHM_F32        | single precision float | Ohm      | 0.12565f       |
| D_MINKERANGE_VPRADPS_F32   | single precision float | VpRadpS  | 0.025f         |
| D_MAXKERANGE_VPRADPS_F32   | single precision float | VpRadpS  | 0.075f         |
| D_CUTEMPESTLOLMT_DEGC_F32  | single precision float | DegC     | (-50.0f)       |
| D_CUTEMPESTHILMT_DEGC_F32  | single precision float | DegC     | 300.0f         |
| D_MAGTEMPESTLOLMT_DEGC_F32 | single precision float | DegC     | (-50.0f)       |
| D_MAGTEMPESTHILMT_DEGC_F32 | single precision float | DegC     | 200.0f         |
| D_SITEMPESTLOLMT_DEGC_F32  | single precision float | DegC     | (-50.0f)       |
| D_SITEMPESTHILMT_DEGC_F32  | single precision float | DegC     | 150.0f         |

####  [section-1]

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

| Constant Name |
|---------------|
|               |
|               |

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

1.  FPM_InitFixedPoint_m

2.  Abs_f32_m

3.  Limit_m

4.  FPM_FloatToFixed_m

5.  TableSize_m

6.  FPM_FixedToFloat_m

7.  IntplVarXY_u16_u16Xu16Y_Cnt

8.  BilinearXYM_u16_u16Xu16YM_Cnt

## Data Hiding Functions

1.  \<None\>

2.  

## Global Functions/Macros Defined by this Module

None

## Local Functions/Macros Used by this MDD only

### Local Function \#1

|                      |      |      |     |     |          |
|----------------------|------|------|-----|-----|----------|
| **Function Name**    | None | Type | Min | Max | UTP Tol. |
| **Arguments Passed** |      |      |     |     |          |
| **Return Value**     |      |      |     |     |          |

#### Description

# Software Module Implementation

## Runtime Environment (RTE) Initial Values

This section lists the initial values of data written by this module but
controlled by the RTE. After RTE initialization, the data in this table
will contain these values.

| Data                                            | Value                                        |
|---------------------------------------|---------------------------------|
| Rte_IWrite_CurrParamComp_Init_EstR_Ohm_f32      | Rte_Pim_EOLNomMtrParam()-\>NomRmtr_Ohm_f32   |
| Rte_IWrite_CurrParamComp_Init_EstLd_Henry_f32   | k_NomLd_Henry_f32                            |
| Rte_IWrite_CurrParamComp_Init_EstLq_Henry_f32   | k_NomLq_Henry_f32                            |
| Rte_IWrite_CurrParamComp_Init_EstKe_VpRadpS_f32 | Rte_Pim_EOLNomMtrParam()-\>NomKe_VpRadpS_f32 |

## Initialization Functions

### Init: ParamComp_Init1

#### Design Rationale

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrCtrl_CM/doc/mediax/media/image2.emf)

#### Module Outputs

Rte_IWrite_CurrParamComp_Init_EstR_Ohm_f32(NomRmtr_Ohm_T_f32)

Rte_IWrite_CurrParamComp_Init_EstLd_Henry_f32(k_NomLd_Henry_f32)

Rte_IWrite_CurrParamComp_Init_EstLq_Henry_f32(k_NomLq_Henry_f32)

Rte_IWrite_CurrParamComp_Init_EstKe_VpRadpS_f32(NomKe_VpRadpS_T_f32)
MtrEstKe_VpRadpS_M_f32\[0\] = NomKe_VpRadpS_T_f32

MtrEstKe_VpRadpS_M_f32\[1\] = NomKe_VpRadpS_T_f32

#### Module Internal 

##  Periodic Functions

### Per: ParamComp_Per1

#### Design Rationale

FastDataAccessBufIndex allows the buffer synchronization between data
calculated on slower periodic loop time(2 milli seconds) and are read by
faster periodic run time (ie 0.125ms)

#### Program Flow Start

Rte_Call_CurrParamComp_Per1_CP0_CheckpointReached()

#### Store Module Inputs to Local copies

IqRef_Amp_T_f32=Rte_IRead_CurrParamComp_Per1_MtrCurrQaxRef_Amp_f32()

IdRef_Amp_T_f32=Rte_IRead_CurrParamComp_Per1_MtrCurrDaxRef_Amp_f32()

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrCtrl_CM/doc/mediax/media/image3.emf)

#### Processing

#### Store Local copy of outputs into Module Outputs

MtrEstKe_VpRadpS_M_f32\[(ActFaseDataAccBufIndex_Cnt_M_u16&1)\^1\]=EstKe_VpRadpS_T_f32

ActFaseDataAccBufIndex_Cnt_M_u16= (ActFaseDataAccBufIndex_Cnt_M_u16&
1)\^1

Rte_IWrite_CurrParamComp_Per1_EstKe_VpRadpS_f32(EstKe_VpRadpS_T_f32)

Rte_IWrite_CurrParamComp_Per1_EstR_Ohm_f32(EstR_Ohm_T_f32)

Rte_IWrite_CurrParamComp_Per1_EstLq_Henry_f32(EstLq_Henry_T_f32)

Rte_IWrite_CurrParamComp_Per1_EstLd_Henry_f32(EstLd_Henry_T_f32)

#### Program Flow End

Rte_Call_CurrParamComp_Per1_CP1_CheckpointReached()

### Per: ParamComp_Per2

#### Design Rationale

None

#### Program Flow Start

Rte_Call_CurrParamComp_Per2_CP0_CheckpointReached()

#### Store Module Inputs to Local copies

NomKe_VpRadpS_T_f32 = Rte_Pim_EOLNomMtrParam()-\>NomKe_VpRadpS_f32

NomRmtr_Ohm_T_f32 = Rte_Pim_EOLNomMtrParam()-\>NomRmtr_Ohm_f32

CuTempEst_DegC_T_f32 = Rte_IRead_CurrParamComp_Per2_CuTempEst_DegC_f32()

MagTempEst_DegC_T_f32 =
Rte_IRead_CurrParamComp_Per2_MagTempEst_DegC_f32()

SiTempEst_DegC_T_f32 = Rte_IRead_CurrParamComp_Per2_SiTempEst_DegC_f32()

NomRmtr_Ohm_T_f32 = Limit_m( NomRmtr_Ohm_T_f32, D_MINRRANGE_OHM_F32,
D_MAXRRANGE_OHM_F32)

NomKe_VpRadpS_T_f32 =
Limit_m(NomKe_VpRadpS_T_f32,D_MINKERANGE_VPRADPS_F32,D_MAXKERANGE_VPRADPS_F32)

CuTempEst_DegC_T_f32 =
Limit_m(CuTempEst_DegC_T_f32,D_CUTEMPESTLOLMT_DEGC_F32,
D_CUTEMPESTHILMT_DEGC_F32)

MagTempEst_DegC_T_f32 = Limit_m(MagTempEst_DegC_T_f32,
D_MAGTEMPESTLOLMT_DEGC_F32, D_MAGTEMPESTHILMT_DEGC_F32 )

SiTempEst_DegC_T_f32 = Limit_m(SiTempEst_DegC_T_f32,
D_SITEMPESTLOLMT_DEGC_F32, D_SITEMPESTHILMT_DEGC_F32)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrCtrl_CM/doc/mediax/media/image4.emf)

#### Processing

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

Rte_Call_CurrParamComp_Per2_CP1_CheckpointReached()

## Fault Recovery Functions

None

## Shutdown Functions

None

## Interrupt Functions

None

##  [section-2]

##  Serial Communication Functions

### SComm: SCom_EOLNomMtrParam_Get

#### Design Rationale

None

#### Program Flow Start

None

#### Store Module Inputs to Local copies

None

#### Processing

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrCtrl_CM/doc/mediax/media/image5.emf)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

None

### SComm: SCom_EOLNomMtrParam_Set

#### Design Rationale

None

#### Program Flow Start

None

#### Store Module Inputs to Local copies

None

#### Processing

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/MtrCtrl_CM/doc/mediax/media/image6.emf)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

None

##  

# Execution Requirements

## Execution Sequence of the Module

(Describe in words relevant details about the execution sequence of the
different sub modules.)

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

| Function Name  | Calling Frequency | System State(s) in which the function is called |
|--------------------------|-----------------|------------------------------|
| ParamComp_Per1 | 2 ms              | ALL                                             |
| ParamComp_Per2 | 100 ms            | ALL                                             |

## Execution Requirements for Serial Communication Functions 

| Function Name           | Sub-Module called by (Serial Comm Function Name) |
|-----------------------------|-------------------------------------------|
| SCom_EOLNomMtrParam_Get | EPS_DiagSrvc                                     |
| SCom_EOLNomMtrParam_Set | EPS_DiagSrvc                                     |

#  [section-4]

#  Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

| Name of Sub Module      | Software Segment               |
|-------------------------|--------------------------------|
| ParamComp_Per1          | RTE_AP_CURRPARAMCOMP_APPL_CODE |
| ParamComp_Per2          | RTE_AP_CURRPARAMCOMP_APPL_CODE |
| SCom_EOLNomMtrParam_Get | RTE_AP_CURRPARAMCOMP_APPL_CODE |
| SCom_EOLNomMtrParam_Set | RTE_AP_CURRPARAMCOMP_APPL_CODE |

##  [section-5]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

| Name of Sub Module | Software Segment |
|--------------------|------------------|
|                    |                  |

#  [section-6]

#  Known Issues / Limitations With Design

1.  (Item \#1)

#  Revision Control Log

<table style="width:100%;">
<colgroup>
<col style="width: 6%" />
<col style="width: 6%" />
<col style="width: 56%" />
<col style="width: 18%" />
<col style="width: 11%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Item #</strong></td>
<td><strong>Rev #</strong></td>
<td><strong>Change Description</strong></td>
<td><strong>Date</strong></td>
<td><strong>Author Initials</strong></td>
</tr>
<tr class="even">
<td>1</td>
<td>1.0</td>
<td>Initial Version</td>
<td>25-May-12</td>
<td>SK</td>
</tr>
<tr class="odd">
<td>2</td>
<td>2.0</td>
<td>Added checkpoints and memmap statements</td>
<td>20-Nov-12</td>
<td>Selva</td>
</tr>
<tr class="even">
<td>3</td>
<td>3.0</td>
<td><table>
<colgroup>
<col style="width: 1%" />
<col style="width: 98%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>Update the input value to the interpolations by using the
following:<br />
IqRef_Amp_T_u9p7=
FPM_FloatToFixed_m(Abs_f32_m(IqRef_Amp_T_f32,u9p7_T));</th>
</tr>
</thead>
<tbody>
</tbody>
</table></td>
<td>11-Jan-13</td>
<td>Selva</td>
</tr>
<tr class="odd">
<td>4</td>
<td>4.0</td>
<td>Updated to version 8 of the Sf99 Mtrlcntrl</td>
<td>21-Mar-13</td>
<td>Selva</td>
</tr>
<tr class="even">
<td>5</td>
<td>5.0</td>
<td>Updated to version 10 FDD SF99 B. Divide by zero fixed</td>
<td>21-Oct-13</td>
<td>Selva</td>
</tr>
<tr class="odd">
<td>6</td>
<td>6.0</td>
<td>Updated to version 11 FDD SF99 B. Limiting EEPROM Read</td>
<td>7-Nov-13</td>
<td>Selva</td>
</tr>
</tbody>
</table>

{% endraw %}