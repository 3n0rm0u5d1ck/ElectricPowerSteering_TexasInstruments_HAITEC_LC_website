---
layout: default
title: Hysteresis_Compensation_MDD
nav_order: 4
parent: Hysteresys Compensation
---
{% raw %}
# Module -- Hysteresis Compensation [module----hysteresis-compensation]

# High-Level Description

This module will calculate a motor torque command to add into the low
pass assist torque that will compensate for the hysteresis present in
the system.

# Figures

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/HystComp/doc/mediax/media/image1.png"
style="width:2.96875in;height:2.94792in" />

## Diagram – Function Data Sharing

This diagram shows all data that is shared between functions within the
module.

### Diagram – HystComp_Per1

This diagram describes the functional characteristics and data flow of a
given function.

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/HystComp/doc/mediax/media/image2.wmf)

# Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

(Note: Full variable names required in table.)

(Note: All global variables including End Of Line data used should be
shown here)

|                                      |                                       |
|----------------------------------|--------------------------------------|
| Module Inputs (Global Variable Name) | Module Outputs (Global Variable Name) |
| HwTorque_HwNm_f32                    | HysteresisComp_MtrNm_f32              |
| BaseAssistCmd_MtrNm_f32              |                                       |
| DefeatHystService_Cnt_lgc            |                                       |
| VehicleSpeed_Kph_f32                 |                                       |
| WIRCmdAmpBlnd_MtrNm_f32              |                                       |
| AssistMechTempEst_DegC_f32           |                                       |
| FricOffset_HwNm_f32                  |                                       |

## Module Internal Variables

This section identifies the name, range and resolutions for module
specific data created by this module. If there are no range restrictions
on the variable, the term “FULL” is placed into the table for legal
range.

<table>
<colgroup>
<col style="width: 36%" />
<col style="width: 14%" />
<col style="width: 12%" />
<col style="width: 13%" />
<col style="width: 21%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Variable Name</td>
<td>Resolution</td>
<td><p>Legal Range</p>
<p>(min)</p></td>
<td><p>Legal Range</p>
<p>(max)</p></td>
<td>Software Segment</td>
</tr>
<tr class="even">
<td>* AssistCmdLPFiltSV_HwNm_M_str</td>
<td>Multiple</td>
<td>Multiple</td>
<td>Multiple</td>
<td>HYSTCOMP_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="odd">
<td><ul>
<li><p>K_Uls_f32</p></li>
</ul></td>
<td>Single Precision Float</td>
<td>0.0124877435</td>
<td>0.4665119090</td>
<td></td>
</tr>
<tr class="even">
<td><ul>
<li><p>SV_HwNm_f32</p></li>
</ul></td>
<td>Single Precision Float</td>
<td>-440</td>
<td>440</td>
<td></td>
</tr>
<tr class="odd">
<td>* HwTrqLPFiltSV_HwNm_M_str</td>
<td>Multiple</td>
<td>Multiple</td>
<td>Multiple</td>
<td>HYSTCOMP_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="even">
<td><ul>
<li><p>K_Uls_f32</p></li>
</ul></td>
<td>Single Precision Float</td>
<td>0.0124877435</td>
<td>0.4665119090</td>
<td></td>
</tr>
<tr class="odd">
<td><ul>
<li><p>SV_HwNm_f32</p></li>
</ul></td>
<td>Single Precision Float</td>
<td>-10</td>
<td>10</td>
<td></td>
</tr>
<tr class="even">
<td>* RawHystCompLPFiltSV_HwNm_M_str</td>
<td>Multiple</td>
<td>Multiple</td>
<td>Multiple</td>
<td>HYSTCOMP_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="odd">
<td><ul>
<li><p>K_Uls_f32</p></li>
</ul></td>
<td>Single Precision Float</td>
<td>0.0124877435</td>
<td>0.4665119090</td>
<td></td>
</tr>
<tr class="even">
<td><ul>
<li><p>SV_HwNm_f32</p></li>
</ul></td>
<td>Single Precision Float</td>
<td>-15</td>
<td>15</td>
<td></td>
</tr>
<tr class="odd">
<td>HwTrqLastUsed_HwNm_M_f32</td>
<td>Single Precision Float</td>
<td>-10.0</td>
<td>10.0</td>
<td>HYSTCOMP_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>Fraction_Uls_M_f32</td>
<td>Single Precision Float</td>
<td>-1.0</td>
<td>1.0</td>
<td>HYSTCOMP_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>RawCalc_HwNm_M_f32</td>
<td>Single Precision Float</td>
<td>-15.0</td>
<td>15.0</td>
<td>HYSTCOMP_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>RiseX_HwNm_M_f32</td>
<td>Single Precision Float</td>
<td>-1.0</td>
<td>1.0</td>
<td>HYSTCOMP_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="odd">
<td>AstCmdLastUsed_HwNm_ M_s8p7</td>
<td>2<sup>-7</sup></td>
<td>-255.0</td>
<td>255.0</td>
<td>HYSTCOMP_START_SEC_VAR_CLEARED_16</td>
</tr>
<tr class="even">
<td>CompAvail_HwNm_D_f32</td>
<td>Single Precision Float</td>
<td>-15</td>
<td>15.0</td>
<td>HYSTCOMP_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>HwTrqFilt_HwNm_D_f32</td>
<td>Single Precision Float</td>
<td>-15.0</td>
<td>15.0</td>
<td>HYSTCOMP_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>CoulFric_HwNm_D_f32</td>
<td>Single Precision Float</td>
<td>-15.0</td>
<td>15.0</td>
<td>HYSTCOMP_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>PosAvail_HwNm_D_f32</td>
<td>Single Precision Float</td>
<td>-15.0</td>
<td>15.0</td>
<td>HYSTCOMP_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>NegAvail_HwNm_D_f32</td>
<td>Single Precision Float</td>
<td>-15.0</td>
<td>15.0</td>
<td>HYSTCOMP_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>EffCompTrq_HwNm_D_f32</td>
<td>Single Precision Float</td>
<td>-15.0</td>
<td>15.0</td>
<td>HYSTCOMP_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>AssistCmdFilt_HwNm_D_s8p7</td>
<td>2<sup>-7</sup></td>
<td>-15.0</td>
<td>15.0</td>
<td>HYSTCOMP_START_SEC_VAR_CLEARED_16</td>
</tr>
</tbody>
</table>

### User defined typedef definition/declaration 

This section documents any user types uniquely used for the module.

<table>
<colgroup>
<col style="width: 34%" />
<col style="width: 31%" />
<col style="width: 11%" />
<col style="width: 11%" />
<col style="width: 11%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Typedef Name</td>
<td>Element Name</td>
<td>User Defined Type</td>
<td><p>Legal Range</p>
<p>(min)</p></td>
<td><p>Legal Range</p>
<p>(max)</p></td>
</tr>
<tr class="even">
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

|                                        |
|----------------------------------------|
| Constant Name                          |
|                                        |
| k_CmnSysTrqRatio_HwNmpMtrNm_f32        |
| k_HysCmpLPAstLPFKn_Hz_f32              |
| k_HysCmpHwTrqLPFKn_Hz_f32              |
| k_HysFinalOutLPFKn_Hz_f32              |
| k_LpFricIpLim_HwNm_u9p7                |
| k_HysRevGain_InvHwNm_f32               |
| k_HysOutLIm_HwNm_f32                   |
| t_HysRiseTblX_HwNm_u2p14               |
| t_HysRiseTblY_Uls_u2p14                |
|                                        |
| t_CmnVehSpd_Kph_u9p7                   |
| t_EffOffTblY_HwNm_u9p7                 |
| t_EffLossTblY_Uls_u4p12                |
| t2_HysHwTrqBlndTblX_HwNm_u9p7          |
| t2_HysHwTrqBlndTblY_Uls_u4p12          |
| t_HysCompCoulFricY_HwNm_u9p7           |
| t_HysCompCoulFricTempScaleX_DegC_s14p1 |
| t_HysCompCoulFricTempScaleY_HwNm_u9p7  |
| t_HysCompHysSatY_HwNm_u9p7             |
| t_HysCompCoulFricWIRBlendX_MtrNm_u8p8  |
| t_HysCompCoulFricWIRBlendY_Uls_u2p14   |
| t_HysCompNegHysCompX_MtrNm_u8p8        |
| t_HysCompNegHysCompY_HwNm_u9p7         |
| t_HysCompNegHysBlendX_HwNm_u9p7        |
| t_HysCompNegHysBlendY_Uls_u2p14        |

## Program(fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

|                         |                                 |       |
|-------------------------|---------------------------------|-------|
| Constant Name           | Resolution                      | Value |
| D_HYSPOSLMT_ULS_F32     | Single Precision Floating Point | 1.0   |
| D_WIROFF_IDX_U16        | 1                               | 0     |
| D_WIRON_IDX_U16         | 1                               | 1     |
| D_WIRCMDBLNDFRC_ULS_F32 | Single Precision Floating Point | 1     |
| D_HYSSATLOWLMT_HWNM_F32 | Single Precision Floating Point | 0     |
| D_HYSOUTLMT_MTRNM_F32   | Single Precision Floating Point | 8.8   |

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

|                                 |
|---------------------------------|
| Constant Name                   |
| BC_HYSTCOMP_FAULTINJECTIONPOINT |
| STD_ON                          |
| FLTINJ_HYSTCOMP                 |
| D_2MS_SEC_F32                   |

### Module specific Lookup Tables Constants

(This is for lookup tables (arrays) with fixed values, same name as
other tables)

|               |            |       |                  |
|---------------|------------|-------|------------------|
| Constant Name | Resolution | Value | Software Segment |
| None          |            |       |                  |

# Functions/Macros used by the Sub-Modules 

## Library Functions / Macros 

The library functions / Macros that are called by the various sub
modules are identified below,

1.  FPM_FloatToFixed_m()

2.  FPM_FixedToFloat_m()

3.  LPF_OpUpdate_f32_m ()

4.  IntplVarXY_u16_u16Xu16Y_Cnt()

5.  IntplVarXY_u16_s16Xu16Y_Cnt()

6.  TableSize_m()

7.  Abs_s16_m()

8.  Abs_f32_m()

9.  Sign_s16_m()

10. Sign_f32_m()

11. Limit_m()

12. BilinearXMYM_u16_u16XMu16YM_Cnt

## Data Hiding Functions

The data hiding functions / macros used in this module are identified
below,

1.  None

## Local Functions/Macros Used by this MDD only

(Note if they are defined in another source file, then reference the
appropriate header file)

The local functions/macros in this module are identified below,

1.  MoreCompensation()

2.  LessCompensation()

3.  CalcAvailComp()

#   [section]

# Software Module Implementation

## Initialization Functions

(Note: For multiple init functions, insert new headers at the “Header 2”
level – subset of “5.1 Initialization Functions” and follow the same
sub-section design shown below)

### Init: HystComp_Init1()

#### Design Rationale

LPF_KUpdate_f32 is used to initialize the LPF filter instead of the full
LPF_Init_f32 macro as an optimization since the required initial state
of the filter is 0, which is the initialized value of the RAM, so there
is no need to explicitly initialize the state variables in this init
function.

#### Module Outputs

None

#### Module Internal 

None

#### Initialize Low Pass Filters

## ![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/HystComp/doc/mediax/media/image3.wmf) [section-1]

## Periodic Functions

### Per: HystComp_Per1

#### Design Rationale

None

#### Program Flow Start

#### Rte_Call_HystComp_Per1_CP0_CheckpointReached()Store Module Inputs to Local copies

DefeatHystService_Cnt_lgc as Boolean

VehSpd_Kph_T_f32 of type float32

AssistCmd_MtrNm_T_f32 as float32

HwTrq_HwNm_T_f32 of type float32

AssistCmd_HwNm_T_f32 of type float32

AssistCmdFilt_HwNm_T_s8p7 of type s8p7_T

AssistCmdFilt_HwNm_T_f32 of type float32

HwTrqFilt_HwNm_T_f32 of type float32

RawHysComp_HwNm_St_f32 of type float32

HysComp_HwNm_T_f32 as float32

HysComp_MtrNm_T_f32 as float32

Fraction_Uls_T_f32 as float32

CompAvail_HwNm_T_f32 as float32

TrqChange_HwNm_T_f32 as type float32

PrevRiseY_Uls_T_f32 as float32

RawHysCompZm1_HwNm_T_f32 as float32

PrevRiseY_Uls_T_f32 = Fraction_Uls_M_f32

RawHysCompZm1_HwNm_T_f32 = RawCalc_HwNm_M_f32

DefeatHystService_Cnt_lgc =
Rte_IRead_HystComp_Per1_DefeatHystService_Cnt_lgc();

VehSpd_Kph_T_u9p7 =
FPM_FloatToFixed_m(Rte_Iread_HystComp_Per1_VehicleSpeed_Kph_f32(),
u9p7_T)

AssistCmd_MtrNm_T_f32 = Rte_Iread_HystComp_Per1\_
BaseAssistCmd_MtrNm_f32 ()

HwTrq_HwNm_T_f32 =Rte_Iread_HystComp_Per1_HwTorque_HwNm_f32() Convert
Low Pass Assist Command to HwNm

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/HystComp/doc/mediax/media/image4.wmf)

#### Apply Filtering to Torque Inputs

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/HystComp/doc/mediax/media/image5.wmf)

#### Freeze Input Values if LP Assist Exceeds Threshold

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/HystComp/doc/mediax/media/image6.wmf)

#### Calculate Hysteresis Loop Position Based on Quadrant

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/HystComp/doc/mediax/media/image7.wmf)

#### Calculate Hysteresis and Limit Rate of Change

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/HystComp/doc/mediax/media/image8.wmf)

#### Store Local copy of outputs into Module Outputs

Rte_Iwrite_HystComp_Per1_HysteresisComp_MtrNm_f32(HysComp_MtrNm_T_f32)

AstCmdLastUsed_HwNm_M_s8p7 = AssistCmdFilt_HwNm_T_s8p7;

HwTrqLastUsed_HwNm_M_f32 = HwTrqFilt_HwNm_T_f32;

Fraction_Uls_M_f32 = Fraction_Uls_T_f32;/\*HysComp_Fraction\*/

RawCalc_HwNm_M_f32 = RawHysComp_HwNm_T_f32;/\*HysComp_RawCalc\*/

CompAvail_HwNm_D_f32 = CompAvail_HwNm_T_f32 ;/\*HysComp_Avail\*/

#### Program Flow End

Rte_Call_HystComp_Per1_CP1_CheckpointReached()

## Fault Recovery Functions

None

## Shutdown Functions

None

## Interrupt Functions

None

## Serial Communication Functions

None

## Local Function/Macro Definitions

If these are numerous and defined in a separate source file then
reference the source file only.

### MoreCompensation Calculation

|                      |                      |           |       |      |               |
|--------------|--------------------|------------|---------|---------|-----------|
| **Function Name**    | MoreCompensation     | Type      | Min   | Max  | UTP Tolerance |
| **Arguments Passed** | TrqChange_HwNm_T_f32 | float32   | -20.0 | 20.0 | N/A           |
|                      | RiseXPtr_HwNm_T_f32  | float32\* | -1.0  | 1.0  | 7.81E-03      |
| **Return Value**     | RiseY_Uls_T_s1p14    | s1p14_T   | -1.0  | 1.0  | 7.81E-03      |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/HystComp/doc/mediax/media/image9.wmf)

### LessCompensation Calculation

|                      |                      |           |        |       |               |
|--------------|---------------------|------------|---------|---------|---------|
| **Function Name**    | LessCompensation     | Type      | Min    | Max   | UTP Tolerance |
| **Arguments Passed** | TrqChange_HwNm_T_f32 | Float32   | -20.0  | 20.0  | N/A           |
|                      | PrevRiseY_Uls_T_f32  | Float32   | -1.0   | 1.0   | N/A           |
|                      | RiseXPtr_HwNm_T_f32  | float32\* | -1.0   | 1.0   | 7.81E-03      |
| **Return Value**     | RiseY_Uls_T_f32      | Float32   | -300.0 | 300.0 | 7.81E-03      |

#### Design Rationale

Two saturation blocks from the partial reversal block were omitted from
the design as they were redundant. The limiting of the RiseY happens
after the merge block and is redundant and the RiseX is implicitly
limited by the interpolation lookup.

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/HystComp/doc/mediax/media/image10.wmf)

### Calculate Available Compensation

|                      |                           |         |        |       |               |
|--------------|---------------------|-----------|---------|--------|-----------|
| **Function Name**    | CalcAvailComp             | Type    | Min    | Max   | UTP Tolerance |
| **Arguments Passed** | HwTrqFilt_HwNm_T_f32      | Float32 | -10.0  | 10.0  | N/A           |
|                      | AssistCmdFilt_HwNm_T_s8p7 | s8p7_T  | -255.0 | 255.0 | N/A           |
|                      | VehSpd_Kph_T_u9p7         | u9p7_T  | 0.0    | 511.0 | N/A           |
| **Return Value**     | CompAvail_HwNm_T_f32      | Float32 | -15.0  | 15.0  | 7.81E-03      |

#### Design Rationale

The limit function that bounds HysTrq_HwNm_T_f32 between ZERO and
FPSATHILMT was used to match the design in the FDD, however, the HIGH
bound of the limit is unreachable as the maximum possible value for the
input does not cause a limiting condition. An alternate design choice
would have been to use a max() function between HysTrq_HwNm_T_f32 and
ZERO as the only limiting factor is the LOWER bound.

#### Description

Localvariables:

EffOff_HwNm_T_f32

EffLoss_Uls_T_f32

HysTrq_HwNm_T_f32

HysBlend_Uls_T_f32

WIROffFric_HwNm_T_f32

WIROnFric_HwNm_T_f32

WIROffFric_HwNm_T_f32

CoulFricHysBlend_T_f32

HysNegBlend_Uls_T_f32

WIRFric_HwNm_T_f32

TempScale_HwNm_T_f32

CoulFric_HwNm_T_f32

HwTrqFilt_HwNm_T_s7p8

HysSat_HwNm_T_f32

HysNegBlndCmp_T_f32

WIRCmdAmpBlnd_MtrNm_u8p8

WIRCmdBlnd_Uls_T_f32

HysNegComp_Uls_T_f32

WIRFric_HwNm_T_f32

AssistMechTempEst_DegC_T_s14p1

AbsCombinedTrq_HwNm_T_f32

CompAvail_HwNm_T_f32

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/HystComp/doc/mediax/media/image11.wmf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/HystComp/doc/mediax/media/image12.wmf)

# Execution Requirements

## Execution Sequence of the Module

(Describe in words relevant details about the execution sequence of the
different sub modules.)

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

|                 |           |                   |                                                 |
|--------------------------|----------------|----------------|----------------|
| Function Name   | Task List | Calling Frequency | System State(s) in which the function is called |
| HystComp_Per1() |           | 2ms               | ALL                                             |

## Execution Requirements for Serial Communication Functions 

|               |                                                  |
|---------------|--------------------------------------------------|
| Function Name | Sub-Module called by (Serial Comm Function Name) |
| N/A           |                                                  |

#   [section-2]

# Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

|                    |                           |
|--------------------|---------------------------|
| Name of Sub Module | Software Segment          |
| HystComp_Init1()   | RTE_AP_HYSTCOMP_APPL_CODE |
| HystComp_Per1()    | RTE_AP_HYSTCOMP_APPL_CODE |

## Local Functions

This table identifies the software segments for local functions
identified in this module.

|                    |                  |
|--------------------|------------------|
| Name of Sub Module | Software Segment |
| MoreCompensation() | AP_HYSTCOMP_CODE |
| LowCompensation()  | AP_HYSTCOMP_CODE |
| CalcAvailComp()    | AP_HYSTCOMP_CODE |

#   [section-3]

# Known Issues / Limitations With Design

1.  INLINE Functions defined in globalmacro.h are not unittested

# Revision Control Log

<table style="width:100%;">
<colgroup>
<col style="width: 6%" />
<col style="width: 6%" />
<col style="width: 64%" />
<col style="width: 11%" />
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
<td>Initial AutoSAR version.</td>
<td>16Feb11</td>
<td>L.N.</td>
</tr>
<tr class="odd">
<td>2</td>
<td>2.0</td>
<td>Added negative hysteresis and ConstFric Blending interface</td>
<td>14Jul11</td>
<td>LWW</td>
</tr>
<tr class="even">
<td>3</td>
<td>3.0</td>
<td>Added ball screw temperature compensation</td>
<td>16Nov11</td>
<td>M. Story</td>
</tr>
<tr class="odd">
<td>4</td>
<td>4.0</td>
<td>Update section9 for INLINE functions</td>
<td>6Dec11</td>
<td>N.Reddy</td>
</tr>
<tr class="even">
<td>5</td>
<td>5.0</td>
<td>Removed Per1 no longer used</td>
<td>9Dec11</td>
<td>M. Story</td>
</tr>
<tr class="odd">
<td>6</td>
<td>6</td>
<td>Corrections per SWC interface requirements</td>
<td>12Dec11</td>
<td>JJW</td>
</tr>
<tr class="even">
<td>7</td>
<td>7</td>
<td>Corrected initialization of HwNmPerMtrNm_Uls_T_f32</td>
<td>13Jan12</td>
<td>M. Story</td>
</tr>
<tr class="odd">
<td>8</td>
<td>8</td>
<td>Anomaly Fixes and removed unused Module level variable
PrevRiseX_Uls_M_s8p7</td>
<td>6March12</td>
<td>NRAR</td>
</tr>
<tr class="even">
<td>9</td>
<td>9</td>
<td>Changes done as per FaultInjectionTechnique</td>
<td>1-May-12</td>
<td>NRAR</td>
</tr>
<tr class="odd">
<td>10</td>
<td>10</td>
<td>Changed component over to floating point</td>
<td>25May12</td>
<td>JWJ</td>
</tr>
<tr class="even">
<td>11</td>
<td>11</td>
<td>Added design rationale to CalcAvailComp to document unit test limit
path failure</td>
<td>20JUN12</td>
<td>JWJ</td>
</tr>
<tr class="odd">
<td>12</td>
<td>12</td>
<td>Updated to new Average Friction Learninput requirements</td>
<td>13JUL12</td>
<td>JWJ</td>
</tr>
<tr class="even">
<td>13</td>
<td>13</td>
<td><ol type="1">
<li><p>Removed SlewRate limit in 6.2.1.7 section</p></li>
<li><p>Replaced Limit with Max and removed D_FPSATHILMT_ULS_F32 in sec
6.7.3.2</p></li>
</ol></td>
<td>23JUL12</td>
<td>NRAR</td>
</tr>
<tr class="odd">
<td>14</td>
<td>14</td>
<td>Added checkpoints and memmap software segment is updated for static
variables</td>
<td>25-Sep-12</td>
<td>Selva</td>
</tr>
<tr class="even">
<td>15</td>
<td>15</td>
<td>Replaced 1-D AsstMagBlndTbl with 2D HwTrqBlnd Table.Six more Display
variables added</td>
<td>04-Nov-12</td>
<td>Selva</td>
</tr>
<tr class="odd">
<td>16</td>
<td>16</td>
<td>Changed precision of t_HysRiseTblY &amp; t_HysRiseTblX per Anom
6855.</td>
<td>12-Nov-12</td>
<td>BWL</td>
</tr>
<tr class="even">
<td>17</td>
<td>17</td>
<td>Anomaly 4110 correction</td>
<td>28-Nov-12</td>
<td>KJS</td>
</tr>
<tr class="odd">
<td>18</td>
<td>17.1.1</td>
<td>Anom 4937 correction</td>
<td>1-may-13</td>
<td>NRAR</td>
</tr>
<tr class="even">
<td>19</td>
<td>18</td>
<td>Update to FDD ver 007</td>
<td>2-May-13</td>
<td>Jared</td>
</tr>
</tbody>
</table>

{% endraw %}