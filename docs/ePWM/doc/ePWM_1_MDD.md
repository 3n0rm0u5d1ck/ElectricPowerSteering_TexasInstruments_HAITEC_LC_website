---
layout: default
title: ePWM_1_MDD
nav_order: 3
parent: Enhanced Pwm (TMS570)
---
{% raw %}
# Module –  [module]

# High-Level Description

This module implements functionality with respect to ES-34B ePWM. This
module implements the ePWM-related register initialization and the motor
control and ADC SOCA configuration update subfunctions.

# Figures

## Component Diagram

#  Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

| Module Inputs      | Module Outputs |                   |
|--------------------|----------------|-------------------|
| PWMPeriod_Cnt_u16  |                | ePWM1CMPA_Cnt_u16 |
| DCPhsAComp_Cnt_u16 |                | ePWM1CMPB_Cnt_u16 |
| DCPhsBComp_Cnt_u16 |                | ePWM2CMPA_Cnt_u16 |
| DCPhsCComp_Cnt_u16 |                | ePWM2CMPB_Cnt_u16 |
| ePWM4CMPB_Cnt_u16  |                | ePWM3CMPA_Cnt_u16 |
|                    |                | ePWM3CMPB_Cnt_u16 |
|                    |                | ePWM4CMPA_Cnt_u16 |
|                    |                | ePWM4CMPB_Cnt_u16 |
|                    |                |                   |

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
<td>None</td>
<td></td>
<td></td>
<td></td>
<td></td>
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
</tbody>
</table>

# Constant Data Dictionary

## Calibration Constants

This section lists the calibrations used by the module. For details on
calibration constants, refer to the Data Dictionary for the application.

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th>Constant Name</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>k_ADCTrig1Offset_Cnt_s16</td>
</tr>
<tr class="even">
<td><p>k_PwmDeadBand_Cnt_u16</p>
<p>k_PwmRelay_Cnt_u16</p></td>
</tr>
</tbody>
</table>

## Program(fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

<table>
<colgroup>
<col style="width: 22%" />
<col style="width: 19%" />
<col style="width: 11%" />
<col style="width: 11%" />
<col style="width: 34%" />
</colgroup>
<thead>
<tr class="header">
<th>Constant Name</th>
<th>Resolution</th>
<th><p>Legal Range</p>
<p>(min)</p></th>
<th><p>Legal Range</p>
<p>(max)</p></th>
<th>Value</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>D_DUTYCYCLESHIFT_CNT_U16</td>
<td>1</td>
<td>535U</td>
<td>535U</td>
<td>535U</td>
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

1.  ePWM_Read_PWMPeriod_u16

2.  ePWM_Read_DCPhsAComp_u16

3.  ePWM_Read_DCPhsBComp_u16

4.  ePWM_Read_DCPhsCComp_u16

5.  ePWM_Write_ePWM1CMPA_Cnt_u16

6.  ePWM_Write_ePWM1CMPB_Cnt_u16

7.  ePWM_Write_ePWM2CMPA_Cnt_u16

8.  ePWM_Write_ePWM2CMPB_Cnt_u16

9.  ePWM_Write_ePWM3CMPA_Cnt_u16

10. ePWM_Write_ePWM3CMPB_Cnt_u16

11. ePWM_Write_ePWM4CMPA_Cnt_u16

12. ePWM_Write_ePWM4CMPB_Cnt_u16

13. 

## Data Hiding Functions

1.  None

## Global Functions/Macros Defined by this Module

### Global Functions \#1

(For detailed info regarding values assigned to registers refer
Reference Pdf attached below)

|                      |            |      |     |     |          |
|----------------------|------------|------|-----|-----|----------|
| **Function Name**    | ePWM_Init1 | Type | Min | Max | UTP Tol. |
| **Arguments Passed** | None       |      |     |     |          |
|                      |            |      |     |     |          |
| **Return Value**     | None       |      |     |     |          |

#### Description

**<u>EPWM1</u>**

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ePWM/doc/mediax/media/image1.emf)

**<u>EPWM2</u>**

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ePWM/doc/mediax/media/image2.emf)

**<u>EPWM3</u>**

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ePWM/doc/mediax/media/image3.emf)

**<u>EPWM4</u>**

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ePWM/doc/mediax/media/image4.emf)

**<u>EPWM7</u>**

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ePWM/doc/mediax/media/image5.emf)

### Global Functions \#2

|                      |           |      |     |     |          |
|----------------------|-----------|------|-----|-----|----------|
| **Function Name**    | ePWM_Per1 | Type | Min | Max | UTP Tol. |
| **Arguments Passed** | None      |      |     |     |          |
|                      |           |      |     |     |          |
| **Return Value**     | None      |      |     |     |          |

#### Design Rationale

PWM Period computed by Pwm_Cdd is read and adjusted. Adjusted value is
used for computations of the motor control PWM CMPA and CMPB values, and
for the ADC SOCA update (ePWM4CMPA).

ADC SOCB update is done in the 2ms loop (see integration manual) then
value (ePWM4CMPB) is read by this function and written to the
appropriate buffer.

This function is called by the motor control ISR and so data cannot be
transferred via the RTE; therefore data is read and written via macros
and global variables.

Due to timing constraints of the motor control ISR processing, outputs
are not limited to their defined ranges before writing.

#### Store Module Inputs to Local copies

ePWM_Read_PWMPeriod_u16(&PWMPeriod_Cnt_T_u16)

ePWM_Read_DCPhsAComp_u16(&DCPhsAComp_Cnt_T_u16)

ePWM_Read_DCPhsBComp_u16(&DCPhsBComp_Cnt_T_u16)

ePWM_Read_DCPhsCComp_u16(&DCPhsCComp_Cnt_T_u16)

ePWM_Read_ePWM4CMPB_Cnt_u16(&ePWM4CMPB_Cnt_T_u16)

#### Processing

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ePWM/doc/mediax/media/image6.emf)

####  Store Local copy of outputs into Module Outputs

ePWM_Write_ePWM1CMPA_Cnt_u16(ePWM1CompA_Cnt_T_u16);

ePWM_Write_ePWM1CMPB_Cnt_u16(ePWM1CompB_Cnt_T_u16);

ePWM_Write_ePWM2CMPA_Cnt_u16(ePWM2CompA_Cnt_T_u16);

ePWM_Write_ePWM2CMPB_Cnt_u16(ePWM2CompB_Cnt_T_u16);

ePWM_Write_ePWM3CMPA_Cnt_u16(ePWM3CompA_Cnt_T_u16);

ePWM_Write_ePWM3CMPB_Cnt_u16(ePWM3CompB_Cnt_T_u16);

ePWM_Write_ePWM4CMPA_Cnt_u16((uint16)(((sint16)halfPWMPeriod_Cnt_T_u16) -
k_ADCTrig1Offset_Cnt_s16 - D_DUTYCYCLESHIFT_CNT_U16));

ePWM_Write_ePWM4CMPB_Cnt_u16(ePWM4CMPB_Cnt_T_u16);

## Local Functions/Macros Used by this MDD only

### Local Macro \#1

|                      |                     |      |     |     |          |
|----------------------|---------------------|------|-----|-----|----------|
| **Function Name**    | ePWM_DisableOutputs | Type | Min | Max | UTP Tol. |
| **Arguments Passed** | None                |      |     |     |          |
|                      |                     |      |     |     |          |
| **Return Value**     | None                |      |     |     |          |

#### Description

Disables the motor control EPWM outputs; forces A and B outputs low on
all three motor control ePWMs (ePWM1, ePWM2, ePWM3) (Refer the included
register reference for more details of register)

ePWM1-\>AQCSFRC = 5U

ePWM1-\>DBCTL &= 0xFFFFFFFCU

ePWM2-\>AQCSFRC = 5U

ePWM2-\>DBCTL &= 0xFFFFFFFCU

ePWM3-\>AQCSFRC = 5U

ePWM3-\>DBCTL &= 0xFFFFFFFCU

### Local Macro \#2

|                      |                    |      |     |     |          |
|----------------------|--------------------|------|-----|-----|----------|
| **Function Name**    | ePWM_EnableOutputs | Type | Min | Max | UTP Tol. |
| **Arguments Passed** | None               |      |     |     |          |
|                      |                    |      |     |     |          |
| **Return Value**     | None               |      |     |     |          |

#### Description

Enables the motor control EPWM outputs; allows A and B outputs to be
driven high/low as configured in register initialization (core
initialization subfunction) and using the CMPA and CMPB values computed
in the motor control configuration subfunction. (Refer the included
register reference for more details of register)

ePWM1-\>AQCSFRC = 0U;

ePWM1-\>DBCTL \|= 3U;

ePWM2-\>AQCSFRC = 0U;

ePWM2-\>DBCTL \|= 3U;

ePWM3-\>AQCSFRC = 0U;

ePWM3-\>DBCTL \|= 3U;

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

This component does not have an RTE Init function, however ePWM pin mux
settings are configured in the integration project and initialized in
(patched) generated code. See the integration manual.

#### Module Outputs

None

#### Module Internal 

None

#### Initialize EPWM Direction Register

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
| ePWM_Init1           | On Event          | ECU start up                             |
| ePWM_Per1            | On Event          | Motor Control ISR subroutine             |

## Execution Requirements for Serial Communication Functions 

| Function Name | Sub-Module called by (Serial Comm Function Name) |
|---------------|--------------------------------------------------|
| None          |                                                  |

#  [section-2]

#  Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

| Name of Sub Module | Software Segment    |
|--------------------|---------------------|
| ePWM_Init1         | EPWM_START_SEC_CODE |
| ePWM_Per1          | EPWM_START_SEC_CODE |

##  [section-3]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

| Name of Sub Module | Software Segment |
|--------------------|------------------|
| None               |                  |

#  [section-4]

#  Known Issues / Limitations With Design

1.  QAC for the generated files not corrected.

2.  

3.  In the FDD DataDictionary full range is used for the signals
    ‘PWMDutyCycleA_Cnts’, ‘PWMDutyCycleB_Cnts’ and ‘PWMDutyCycleC_Cnts’
    which is not correct. Corrected range (i.e. 0 to 6000 given by the
    FDD author) is used in the software DataDictionary.

4.  In the FDD DataDictionary the max value used for signal ’PWM_Period
    ‘ is not correct. Corrected max value (i.e. 6000 given by the FDD
    author) is uded in the software DataDictionary.

5.  Unit test consideration: Don’t use any combination of the input
    signals where the value of
    ‘PWMDutyCycleA_Cnts’/’PWMDutyCycleB_Cnts’/’ PWMDutyCycleC_Cnts’ is
    greater than the signal ‘PWM_Period’.

#  [section-5]

#  Reference 

Register Reference

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ePWM/doc/mediax/media/image7.emf)

#  Revision Control Log

|            |                                                         |           |                     |
|------|-----------------------------------------------|----------|----------|
| **Rev \#** | **Change Description**                                  | **Date**  | **Author Initials** |
| 1.0        | Initial Version ( FDD 34B) –Shutdown Mech not included  | 18-Feb-13 | Selva               |
| 2          | Anomaly 4605 – changed active state of ePWM modules 1-3 | 11-Mar-13 | OT                  |
| 3          | Updated to FDD 34B v003                                 | 18-Jun-13 | OT/Selva            |
| 4          | Updated to FDD 34B v005                                 | 07-Apr-14 | Selva               |
| 5          | Updated to ES-34B v008                                  | 25-Jan-15 | KMC                 |
| 6          | Updated to ES-34B v009                                  | 25-Nov-15 | Rijvi               |

{% endraw %}