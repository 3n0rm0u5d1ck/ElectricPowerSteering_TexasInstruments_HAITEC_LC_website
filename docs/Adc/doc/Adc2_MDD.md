---
layout: default
title: Adc2_MDD
nav_order: 1
parent: Adc Driver
---
{% raw %}
# Module – ADC2 [module-adc2]

# High-Level Description

The ADC2 module shall control sampling and conversion of voltages from
the hardware layer into digital signals.

# Figures

## Component Diagram

#  Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

| Module Inputs | Module Outputs          |
|---------------|-------------------------|
| None          | ADC2OffsetComp_Cnt_u8p8 |

## Module Internal Variables

This section identifies the name, range and resolutions for module
specific data created by this module. If there are no range restrictions
on the variable, the term “FULL” is placed into the table for legal
range.

<table>
<colgroup>
<col style="width: 32%" />
<col style="width: 15%" />
<col style="width: 13%" />
<col style="width: 12%" />
<col style="width: 26%" />
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
<tr class="odd">
<td>See Adc_MDD.doc for Adc subsystem types</td>
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

| Constant Name |
|---------------|
| None          |

## Program(fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

| Constant Name               | Resolution | Units  | Value                   |
|-----------------------------|------------|--------|-------------------------|
| D_GROUPEV_CNT_U8            | 1          | Counts | 0                       |
| D_GROUP1_CNT_U8             | 1          | Counts | 1                       |
| D_GROUP2_CNT_U8             | 1          | Counts | 2                       |
| D_NTCPARMBIT1_CNT_U8        | 1          | Counts | 2                       |
| D_ADC2EVTBUFSZ_CNT_U08      | 1          | Counts | Generated in Adc2_Cfg.h |
| D_ADC2G1BUFSZ_CNT_U08       | 1          | Counts | Generated in Adc2_Cfg.h |
| D_ADC2G2BUFSZ_CNT_U08       | 1          | Counts | Generated in Adc2_Cfg.h |
| D_ADC2EVSRC_CNT_U32         | 1          | Counts | Generated in Adc2_Cfg.h |
| D_ADC2G1SRC_CNT_U32         | 1          | Counts | Generated in Adc2_Cfg.h |
| D_ADC2G2SRC_CNT_U32         | 1          | Counts | Generated in Adc2_Cfg.h |
| D_ADC2NUMEVTCH_CNT_U08      | 1          | Counts | Generated in Adc2_Cfg.h |
| D_ADC2EVTCH_CNT_U32         | 1          | Counts | Generated in Adc2_Cfg.h |
| D_ADC2NUMG1CH_CNT_U08       | 1          | Counts | Generated in Adc2_Cfg.h |
| D_ADC2G1CH_CNT_U32          | 1          | Counts | Generated in Adc2_Cfg.h |
| D_ADC2NUMG2CH_CNT_U08       | 1          | Counts | Generated in Adc2_Cfg.h |
| D_ADC2G2CH_CNT_U32          | 1          | Counts | Generated in Adc2_Cfg.h |
| D_ADC2RSLTBASEADR_CNT_U32   | 1          | Counts | Generated in Adc2_Cfg.h |
| D_ADC2EVINTENA_CNT_U32      | 1          | Counts | Generated in Adc2_Cfg.h |
| D_ADC2EVSAMPDISEN_CNT_U32   | 1          | Counts | Generated in Adc2_Cfg.h |
| D_ADC2EVFIFORESETCR_CNT_U32 | 1          | Counts | Generated in Adc2_Cfg.h |
| D_ADC2EVDMACR_CNT_U32       | 1          | Counts | Generated in Adc2_Cfg.h |
| D_ADC2G1INTENA_CNT_U32      | 1          | Counts | Generated in Adc2_Cfg.h |
| D_ADC2G1SAMPDISEN_CNT_U32   | 1          | Counts | Generated in Adc2_Cfg.h |
| D_ADC2G1FIFORESETCR_CNT_U32 | 1          | Counts | Generated in Adc2_Cfg.h |
| D_ADC2G1DMACR_CNT_U32       | 1          | Counts | Generated in Adc2_Cfg.h |
| D_ADC2G2INTENA_CNT_U32      | 1          | Counts | Generated in Adc2_Cfg.h |
| D_ADC2G2SAMPDISEN_CNT_U32   | 1          | Counts | Generated in Adc2_Cfg.h |
| D_ADC2G2FIFORESETCR_CNT_U32 | 1          | Counts | Generated in Adc2_Cfg.h |
| D_ADC2G2DMACR_CNT_U32       | 1          | Counts | Generated in Adc2_Cfg.h |
| D_HWTRGADC2GEVT_CNT_LGC     | 1          | Counts | Generated in Adc2_Cfg.h |
| D_HWTRGADC2G1_CNT_LGC       | 1          | Counts | Generated in Adc2_Cfg.h |
| D_HWTRGADC2G2_CNT_LGC       | 1          | Counts | Generated in Adc2_Cfg.h |
| D_ADC2USEDMA_CNT_LGC        | 1          | Counts | Generated in Adc2_Cfg.h |
| D_ISRGROUP_CNT_U8           | 1          | Counts | Generated in Adc2_Cfg.h |

####  [section]

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

| Constant Name |
|---------------|
| None          |

### Module specific Lookup Tables Constants

<table style="width:100%;">
<colgroup>
<col style="width: 32%" />
<col style="width: 11%" />
<col style="width: 40%" />
<col style="width: 16%" />
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
<td>T_Adc2GroupConfigData_Cnt_Str[3]</td>
<td>Adc_GroupConfigDataType</td>
<td><p>{</p>
<p>D_ADC2NUMEVTCH_CNT_U08,</p>
<p>D_ADC2EVTCH_CNT_U32,</p>
<p>&amp;(((uint32*)D_ADC2RSLTBASEADR_CNT_U32)[0]),</p>
<p>},</p>
<p>{</p>
<p>D_ADC2NUMG1CH_CNT_U08,</p>
<p>D_ADC2G1CH_CNT_U32,</p>
<p>&amp;(((uint32*)D_ADC2RSLTBASEADR_CNT_U32)[D_ADC2EVTBUFSZ_CNT_U08]),</p>
<p>},</p>
<p>{</p>
<p>D_ADC2NUMG2CH_CNT_U08,</p>
<p>D_ADC2G2CH_CNT_U32,</p>
<p>&amp;(((uint32*)D_ADC2RSLTBASEADR_CNT_U32)[D_ADC2EVTBUFSZ_CNT_U08 +
D_ADC2G1BUFSZ_CNT_U08]),</p>
<p>}</p></td>
<td>CONST_32</td>
</tr>
</tbody>
</table>

#  Functions/Macros used by the Sub-Modules 

## Library Functions / Macros 

The library and functions / Macros that are called by the various sub
modules are identified below,

1.  None

## Data Hiding Functions

> None

## Global Functions/Macros Defined by this Module

### ADC2 Init

|                      |            |                  |     |     |          |
|----------------------|------------|------------------|-----|-----|----------|
| **Function Name**    | Adc2_init1 | Type             | Min | Max | UTP Tol. |
| **Arguments Passed** | ConfigPtr  | Adc_ConfigType\* | N/A | N/A |          |
| **Return Value**     | N/A        |                  |     |     |          |

This function is used to initialize each of the ADC2 Groups (Event,
Group1, and Group2).

#### Initialize Module Internal Variables

None

#### Register Configuration

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/Adc/doc/mediax/media/image1.emf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/Adc/doc/mediax/media/image2.emf)

Adc2_Write_ADC2OffsetComp_Cnt_u8p8_Cnt_T_u8p8(Adcoffset_Cnt_T_u8p8)

####  Start Initial Conversions

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/Adc/doc/mediax/media/image3.emf)

### Start Group Conversion

|                      |                           |       |     |     |          |
|----------------------|---------------------------|-------|-----|-----|----------|
| **Function Name**    | Adc2_StartGroupConversion | Type  | Min | Max | UTP Tol. |
| **Arguments Passed** | group                     | uint8 | 0   | 2   |          |
| **Return Value**     | N/A                       |       |     |     |          |

This function starts a software triggered conversion of all channels of
the requested Adc channel group.

#### Start Conversions

> ![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/Adc/doc/mediax/media/image4.emf)

### Enable Group Notification

|                      |                                                         |       |     |     |          |
|--------------|--------------------------|----------------|------|------|------|
| **Function Name**    | <span class="mark">Adc2\_</span>EnableGroupNotification | Type  | Min | Max | UTP Tol. |
| **Arguments Passed** | group                                                   | uint8 | 0   | 15  |          |
| **Return Value**     | N/A                                                     |       |     |     |          |

This inline function reads and returns the individual channel conversion
result.

#### Enable Notification Conditions

> ![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/Adc/doc/mediax/media/image5.emf)

## Local Functions/Macros Used by this MDD only

### Read Channel Conversions

|                      |                                               |        |     |      |          |
|--------------|--------------------------|----------------|------|------|------|
| **Function Name**    | <span class="mark">Adc2_ReadConversion</span> | Type   | Min | Max  | UTP Tol. |
| **Arguments Passed** | ConvId                                        | uint16 | 0   | 15   |          |
| **Return Value**     | conversion result                             | uint16 | 0   | 4095 | 0        |

This inline function reads and returns the individual channel conversion
result.

#### Read Group

> ![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/Adc/doc/mediax/media/image6.emf)

# Software Module Implementation

## Runtime Environment (RTE) Initial Values

None

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

## Serial Communication Functions

None

## Transition Functions

None

##  

# Execution Requirements

## Execution Sequence of the Module

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

| Function Name | Calling Frequency        | System State(s) in which the function is called |
|--------------------------|-----------------|------------------------------|
| Adc2_Init     | Once (at initialization) | STARTUP                                         |

## Execution Requirements for Serial Communication Functions 

| Function Name | Sub-Module called by (Serial Comm Function Name) |
|---------------|--------------------------------------------------|
| N/A           |                                                  |

#  [section-2]

#  Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

| Name of Sub Module           | Software Segment    |
|------------------------------|---------------------|
| Adc2_Init                    | ADC2_START_SEC_CODE |
| Adc2_StartGroupConversion    | ADC2_START_SEC_CODE |
| Adc2_EnableGroupNotification | ADC2_START_SEC_CODE |
| Adc2_ReadConversion          | inline              |

##  [section-3]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

| Name of Sub Module | Software Segment |
|--------------------|------------------|
| None               |                  |

#  [section-4]

#  Known Limitations With Design

1.  INLINE functions defined in “GlobalMacro.h” are not unit tested

2.  Buffer pointer initialization could hang if adc conversion did not
    complete. Consider adding a timeout and possible setting of NTC 0x33
    bit 1.

3.  ADC component outputs the ADC calibration compensation which is in
    turn used by Current Measurement to correct its offset volt . This
    is implementation done across two components. The measured currents
    from ADC and conversion from counts to volts is not done in this
    component as described by the FDD but current measurement component.

4.  

#  Revision Control Log

|            |                                                                                                                                                                |          |                     |
|------|-----------------------------------------------|----------|----------|
| **Rev \#** | **Change Description**                                                                                                                                         | **Date** | **Author Initials** |
| 1.0        | Initial version based on FDD 33C rev 006                                                                                                                       | 05Nov12  | LN                  |
| 2.0        | Design updates to meet FDD and simplify configuration                                                                                                          | 24APR13  | Selva               |
| 3.0        | Fixed typo in flowchart                                                                                                                                        | 22MAY13  | LWW                 |
| 4.0        | Updated for use with DMA. Moved init function scheduling requirements to integration manual. Added design limitation note about buffer pointer initialization. | 10APR14  | KMC                 |
| 5.0        | Updated for ADC offset compensation                                                                                                                            | 27JUN14  | Selva               |

{% endraw %}