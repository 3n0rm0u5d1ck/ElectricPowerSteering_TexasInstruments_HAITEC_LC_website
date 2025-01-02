---
layout: default
title: StabilityCompensation_MDD
nav_order: 4
parent: Component
---
{% raw %}
# Module -- Stability Compensation [module----stability-compensation]

# High-Level Description

This function provides in-vehicle stability of EPS behavior. To maximize
steering feel, the function blends between two different tunings based
on vehicle speed and low frequency handwheel torque. Because system
gains may get multiplied by various scale factors, either from serial
communications or from other software functions, this function provides
a second blending feature.

Some vehicle programs require a secondary, or "systematic", calculation
of stability compensation followed by a correlation check. The
systematic calculations usually must reside in a separate Memory
Partition Unit (MPU), and switching between MPUs negatively impacts
system throughput. This model is designed using the best-known
implementation at this time.

# Figures

## Component Diagram

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/StabilityComp/doc/mediax/media/image1.png"
style="width:3.58056in;height:3.28194in" />

## Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

| Module Inputs            | Module Outputs |                     |
|--------------------------|----------------|---------------------|
| AssistDDFactor_Uls_f32   |                | AssistCmd_MtrNm_f32 |
| SysAssistCmd_MtrNm_f32   |                |                     |
| HwTorque_HwNm_f32        |                |                     |
| VehicleSpeed_Kph_f32     |                |                     |
| CombinedAssist_MtrNm_f32 |                |                     |
| AsstFWActive_Uls_f32     |                |                     |

## Module Internal Variables

This section identifies the name, range and resolutions for module
specific data created by this module. If there are no range restrictions
on the variable, the term “FULL” is placed into the table for legal
range.

<table>
<colgroup>
<col style="width: 31%" />
<col style="width: 16%" />
<col style="width: 13%" />
<col style="width: 13%" />
<col style="width: 25%" />
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
<td>StCmpAsstFctrCmpBlnd_Uls_D_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td>1</td>
<td>STABILITYCOMP_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>StCmp12Blend_Uls_D_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td>1</td>
<td>STABILITYCOMP_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>StCmp34Blend_Uls_D_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td>1</td>
<td>STABILITYCOMP_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>StCmp02Blend_Uls_D_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td>1</td>
<td>STABILITYCOMP_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>StCmp04Blend_Uls_D_f32</td>
<td>Single Precision Float</td>
<td>0</td>
<td>1</td>
<td>STABILITYCOMP_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>StCmp1Out_MtrNm_D_f32</td>
<td>Single Precision Float</td>
<td>-2312</td>
<td>2312</td>
<td>STABILITYCOMP_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>StCmp2Out_MtrNm_D_f32</td>
<td>Single Precision Float</td>
<td>-2312</td>
<td>2312</td>
<td>STABILITYCOMP_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>StCmp3Out_MtrNm_D_f32</td>
<td>Single Precision Float</td>
<td>-2312</td>
<td>2312</td>
<td>STABILITYCOMP_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>StCmp4Out_MtrNm_D_f32</td>
<td>Single Precision Float</td>
<td>-2312</td>
<td>2312</td>
<td>STABILITYCOMP_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="even">
<td>AssistCmdSV_MtrNm_M_f32</td>
<td>Single Precision Float</td>
<td>-8.8</td>
<td>8.8</td>
<td>STABILITYCOMP_START_SEC_VAR_CLEARED_32</td>
</tr>
<tr class="odd">
<td>HwTrqSV_HwNm_M_Str</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>STABILITYCOMP_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="even">
<td>HwTrqSV_HwNm_M_Str.K_Uls_f32</td>
<td>Single Precision Floating Point</td>
<td>0.000125</td>
<td>0.4666</td>
<td></td>
</tr>
<tr class="odd">
<td>HwTrqSV_HwNm_M_Str.SV_Uls_f32</td>
<td>Single Precision Floating Point</td>
<td>0</td>
<td>10</td>
<td></td>
</tr>
<tr class="even">
<td>CombAstNFSV_Cnt_M_Str*</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>STABILITYCOMP_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="odd">
<td>CombAstNFSV_Cnt_M_Str[].SV1_Uls_f32</td>
<td>Single Precision Floating Point</td>
<td>-2077</td>
<td>2077</td>
<td></td>
</tr>
<tr class="even">
<td>CombAstNFSV_Cnt_M_Str[].SV2_Uls_f32</td>
<td>Single Precision Floating Point</td>
<td>-1981</td>
<td>1981</td>
<td></td>
</tr>
<tr class="odd">
<td>CombAstNFSV_Cnt_M_Str[].Out_Uls_f32</td>
<td>Single Precision Floating Point</td>
<td>-2312</td>
<td>2312</td>
<td></td>
</tr>
<tr class="even">
<td>CombAstNFSV_Cnt_M_Str[].KPtr_Cnt_Str-&gt;A1_Uls_f32</td>
<td>Single Precision Floating Point</td>
<td>-2</td>
<td>0</td>
<td></td>
</tr>
<tr class="odd">
<td>CombAstNFSV_Cnt_M_Str[].KPtr_Cnt_Str-&gt;A2_Uls_f32</td>
<td>Single Precision Floating Point</td>
<td>-1</td>
<td>1</td>
<td></td>
</tr>
<tr class="even">
<td>CombAstNFSV_Cnt_M_Str[].KPtr_Cnt_Str-&gt;B0_Uls_f32</td>
<td>Single Precision Floating Point</td>
<td>0</td>
<td>2300</td>
<td></td>
</tr>
<tr class="odd">
<td>CombAstNFSV_Cnt_M_Str[].KPtr_Cnt_Str-&gt;B1_Uls_f32</td>
<td>Single Precision Floating Point</td>
<td>-4500</td>
<td>0</td>
<td></td>
</tr>
<tr class="even">
<td>CombAstNFSV_Cnt_M_Str[].KPtr_Cnt_Str-&gt;B2_Uls_f32</td>
<td>Single Precision Floating Point</td>
<td>-4</td>
<td>2300</td>
<td></td>
</tr>
<tr class="odd">
<td>StabCompOverThresh_Cnt_D_lgc</td>
<td>Boolean</td>
<td>0</td>
<td>1</td>
<td>STABILITYCOMP_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="even">
<td>StCmpPNStatus_Cnt_M_lgc</td>
<td>Boolean</td>
<td>0</td>
<td>1</td>
<td>STABILITYCOMP_START_SEC_VAR_CLEARED_BOOLEAN</td>
</tr>
<tr class="odd">
<td>StCmpPNAccum_Cnt_M_u16</td>
<td>uint16</td>
<td>0</td>
<td>5000</td>
<td>STABILITYCOMP_START_SEC_VAR_CLEARED_16</td>
</tr>
</tbody>
</table>

\* See unit testing notes in section 2.3.1 for range considerations of
Notch Filter

###  [section]

### Notch filter Unit testing considerations

Since the notch filter implementation used in this module is dynamic in
nature, absolute ranges are difficult to determine without pre-defined
knowledge on the combination of coefficient values (A1, A2, B0, B1, B2).
Because of this, the systems group ran simulations on 10 different
combinations of coefficients (2 with defined default calibrations, 8
considered extreme cases of notch filters) and logged the ranges of the
filter state variables and outputs during a frequency sweep. The ranges
given throughout this module were taken as the worst case results of all
of the given test cases.

To provide useful cases for unit testing, the boundary checks tested
during unit testing should be altered to test the state variable minimum
and maximum for each of the 10 test cases with the given coefficients
set to the values given in that test case. In the case where the default
values of the coefficients are used in a vector, the unit tester should
not test the corresponding state variables with values over the range
defined for that set of coefficients. See attached simulation results.

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/StabilityComp/doc/mediax/media/image2.emf)

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

| Constant Name                           |
|-----------------------------------------|
| t_StCmpADDFBlendX_Uls_u2p14\[ \]        |
| t_StCmpADDFBlendY_Uls_u2p14\[ \]        |
| t_StCmpBlendSpdBS_Kph_u9p7\[ \]         |
| t_StCmpBlend12Trq_HwNm_u8p8\[ \]        |
| t2_StCmpBlend12TblY_Uls_u2p14\[ \]\[ \] |
| t2_StCmpBlend02TblY_Uls_u2p14\[ \]\[ \] |
| t_StCmpBlend34Trq_HwNm_u8p8\[ \]        |
| t2_StCmpBlend34TblY_Uls_u2p14\[ \]\[ \] |
| t2_StCmpBlend04TblY_Uls_u2p14\[ \]\[ \] |
| t_StCmpNFK_Str\[ \]                     |
| t_StCmpNFK_Str\[ \].A1_Uls_f32          |
| t_StCmpNFK_Str\[ \].A2_Uls_f32          |
| t_StCmpNFK_Str\[ \].B0_Uls_f32          |
| t_StCmpNFK_Str\[ \].B1_Uls_f32          |
| t_StCmpNFK_Str\[ \].B2_Uls_f32          |
| k_StCmpHwTrqLPFKn_Hz_f32                |
| k_StCmpSysCorrThresh_MtrNm_f32          |
| k_StCmpCrosChkEnbl_Uls_lgc              |
| k_StCmpStabCmpPstep_Cnt_u16             |
| k_StCmpStabCmpNstep_Cnt_u16             |
| k_StCmpStabCmpPNThresh_Cnt_u16          |

## Program (fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

| Constant Name           | Resolution                      | Units | Value                         |
|-------------------------------|--------------|--------------|--------------|
| D_COMPINLIMIT_MTRNM_F32 | Single Precision Floating Point | MtrNm | 10.275                        |
| D_NUMNOTCHFILT_CNT_U08  | UINT08                          | Cnt   | (TableSize_m(t_StCmpNFK_Str)) |
| D_NUMNFBLENDS_CNT_U08   | UINT08                          | Cnt   | 4                             |
| D_ASSISTINIT_MTRNM_F32  | Single Precision Floating Point | MtrNm | 0                             |
| D_COMPBLND12IDX_CNT_U08 | UINT08                          | Cnt   | 0                             |
| D_COMPBLND34IDX_CNT_U08 | UINT08                          | Cnt   | 1                             |
| D_COMPBLND02IDX_CNT_U08 | UINT08                          | Cnt   | 2                             |
| D_COMPBLND04IDX_CNT_U08 | UINT08                          | Cnt   | 3                             |
| D_ASSTSCLMT_MTRNM_F32   | Single Precision Floating Point | MtrNm | 8.8                           |

####  [section-1]

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

| Constant Name  |
|----------------|
| D_ZERO_ULS_F32 |
| D_2MS_SEC_F32  |

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

1.  FPM_FloatToFixed_m

2.  Limit_m

3.  NF_Init_f32

4.  FPM_FixedToFloat_m

5.  BilinearXYM_u16_u16Xu16YM_Cnt

6.  IntplVarXY_u16_u16Xu16Y_Cnt

7.  Blend_f32

8.  Abs_f32_m

## Data Hiding Functions

1.  \<None\>

## Global Functions/Macros Defined by this Module

None

## Local Functions/Macros Used by this MDD only

### ApplyStabilityComp

|                      |                            |                            |                            |         |        |          |
|------------|----|--------------------|---------------|-------|-------|--------|
| **Function Name**    | ApplyStabilityComp         |                            | Type                       | Min     | Max    | UTP Tol. |
| **Arguments Passed** | CombinedAssist_MtrNm_T_f32 |                            | float32                    | -10.275 | 10.275 |          |
|                      | FiltSVPtr_Uls_T_Str\*      |                            | Pointer to NotchFiltSV_Str |         |        |          |
|                      |                            | .SV1_Uls_f32               | float32                    | -2077   | 2077   | 0.000489 |
|                      |                            | .SV2_Uls_f32               | float32                    | -1981   | 1981   | 0.000489 |
|                      |                            | .Out_Uls_f32               | float32                    | -2312   | 2312   | 0.000489 |
|                      |                            | .KPtr_Cnt_Str-\>A1_Uls_f32 | float32                    | -2      | 0      | 0.00005  |
|                      |                            | .KPtr_Cnt_Str-\>A2_Uls_f32 | float32                    | -1      | 1      | 0.00005  |
|                      |                            | .KPtr_Cnt_Str-\>B0_Uls_f32 | float32                    | 0       | 2300   | 0.00005  |
|                      |                            | .KPtr_Cnt_Str-\>B1_Uls_f32 | float32                    | -4500   | 0      | 0.00005  |
|                      |                            | .KPtr_Cnt_Str-\>B2_Uls_f32 | float32                    | -4      | 2300   | 0.00005  |
|                      | CompBlnd_Uls_T_f32         |                            | Pointer to float32         | 0       | 1      |          |
|                      | ADDFBlend_Uls_T_f32        |                            | float32                    | 0       | 2      |          |
|                      | WriteDisplayVars_Cnt_T_lgc |                            | boolean                    | FALSE   | TRUE   |          |
| **Return Value**     | FilteredOutput_MtrNm_T_f32 |                            | float32                    | -8.8    | 8.8    | 4.89E-04 |

#### \* See unit testing notes in section 2.3.1 for range considerations of Notch Filter [see-unit-testing-notes-in-section-2.3.1-for-range-considerations-of-notch-filter]

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/StabilityComp/doc/mediax/media/image3.emf)

# Software Module Implementation

## Runtime Environment (RTE) Initial Values

This section lists the initial values of data written by this module but
controlled by the RTE. After RTE initialization, the data in this table
will contain these values.

| Data                     | Value |
|--------------------------|-------|
| AssistDDFactor_Uls_f32   | 1     |
| HwTorque_HwNm_f32        | 0     |
| CombinedAssist_MtrNm_f32 | 0     |
| AsstFWActive_Uls_f32     | 0     |
| VehicleSpeed_Kph_f32     | 0     |
| AssistCmd_MtrNm_f32      | 0     |
| SysAssistCmd_MtrNm_T_f32 | 0     |

## Initialization Functions

### Init: StabilityComp_Init1

#### Design Rationale

None

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/StabilityComp/doc/mediax/media/image4.emf)

## Periodic Functions

### Per: StabilityComp_Per1

#### Design Rationale

#### Program Flow Start

Rte_Call_StabilityComp_Per1_CP0_CheckpointReached()

#### Store Module Inputs to Local copies

N/A

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/StabilityComp/doc/mediax/media/image5.emf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/StabilityComp/doc/mediax/media/image6.emf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/StabilityComp/doc/mediax/media/image7.emf)

#### Store Local copy of outputs into Module Outputs

#### Rte_IWrite_StabilityComp_Per1_AssistCmd_MtrNm_f32(AssistCmd_MtrNm_T_f32)Program Flow End

Rte_Call_StabilityComp_Per1_CP1_CheckpointReached()

##  Fault Recovery Functions

## Shutdown Functions

## Interrupt Functions

## Serial Communication Functions

##  [section-2]

# Execution Requirements

## Execution Sequence of the Module

(Describe in words relevant details about the execution sequence of the
different sub modules.)

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

| Function Name       | Calling Frequency | System State(s) in which the function is called |
|--------------------------|-----------------|------------------------------|
| StabilityComp_Per1  | 2ms               | ALL STATES                                      |
| StabilityComp_Init1 | STARTUP           | COLD INIT                                       |

## Execution Requirements for Serial Communication Functions 

| Function Name | Sub-Module called by (Serial Comm Function Name) |
|---------------|--------------------------------------------------|
| \<None\>      |                                                  |

#  [section-3]

#  Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

| Name of Sub Module | Software Segment |
|--------------------|------------------|
| StabilityComp_Per1 |                  |

##  [section-4]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

| Name of Sub Module | Software Segment |
|--------------------|------------------|
| ApplyStabilityComp |                  |

#  [section-5]

#  Known Issues / Limitations With Design

1.  INLINE functions defined in GlobalMacro.h are not unit tested

#  Revision Control Log

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
<td>Initial MDD</td>
<td>30NOV11</td>
<td>VK</td>
</tr>
<tr class="odd">
<td>2</td>
<td>2.0</td>
<td>Anomaly 2852 Added limits to assist and baseassist outputs</td>
<td>02Feb12</td>
<td>M. Story</td>
</tr>
<tr class="even">
<td>3</td>
<td>3</td>
<td>Updated to SF-29 rev 3</td>
<td>02-May-12</td>
<td>OT</td>
</tr>
<tr class="odd">
<td>4</td>
<td>4</td>
<td>Added checkpoints and memmap software segment is updated for static
variables</td>
<td>24-Sep-12</td>
<td>Selva</td>
</tr>
<tr class="even">
<td>5</td>
<td>5</td>
<td><p>Updated to SF-29 rev 5</p>
<p>Addition of LPF of handwheel torque to the compensator blend
tables.</p>
<p>Added functionality to allow compensators 2 and 4 to blend to
zero</p></td>
<td>15Oct12</td>
<td>LN</td>
</tr>
<tr class="odd">
<td>6</td>
<td>6</td>
<td>Corrected Macro size of D_NUMNFBLENDS_CNT_U08 to 4</td>
<td>11Feb13</td>
<td>Selva</td>
</tr>
<tr class="even">
<td>7</td>
<td>7</td>
<td>Updated to SF-29 rev 006</td>
<td>27 Feb 13</td>
<td>SP</td>
</tr>
<tr class="odd">
<td>8</td>
<td>8</td>
<td>Anom 4609- Fixed correct function call for FaultInjection call</td>
<td>02 April 13</td>
<td>NRAR</td>
</tr>
<tr class="even">
<td>9</td>
<td>9</td>
<td>Anomaly 4791 fix</td>
<td>11 Apr 13</td>
<td>SP</td>
</tr>
<tr class="odd">
<td>10</td>
<td>10</td>
<td>Updated to SF-29 rev 007</td>
<td>13 Apr 13</td>
<td>SP</td>
</tr>
<tr class="even">
<td>11</td>
<td>11</td>
<td>Range updates and notes about unit testing the notch filter.
Corrected NTC name.</td>
<td>30 Apr 13</td>
<td>LWW</td>
</tr>
<tr class="odd">
<td>12</td>
<td>12</td>
<td>Range updates on HwTrq filter SV. Added tolerance for pointer values
on local function.</td>
<td>06 June 13</td>
<td>LWW</td>
</tr>
<tr class="even">
<td>13</td>
<td>13</td>
<td>Added cal ptr for parameter in function call to
NF_FullUpdate_f32</td>
<td>05-Dec-13</td>
<td>VT</td>
</tr>
</tbody>
</table>

{% endraw %}