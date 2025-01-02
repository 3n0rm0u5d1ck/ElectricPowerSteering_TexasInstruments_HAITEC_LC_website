---
layout: default
title: Electric_Power_Consumption_MDD
nav_order: 2
parent: Electrical Power
---
{% raw %}
# Module -- Electric Power Consumption [module----electric-power-consumption]

# High-Level Description

This module estimates the instantaneous electric power at the input of
the control module and the supply current.

# Figures

## Diagram – Component Diagram

##  [section]

## <img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ElePwr/doc/mediax/media/image1.png"
style="width:2.97569in;height:2.54375in" />  [section-1]

#  Variable Data Dictionary

| Module Inputs       | Module Outputs         |
|---------------------|------------------------|
| Vecu_Volt_f32       | ElectricPower_Watt_f32 |
| MtrVoltDax_Volt_f32 | SupplyCurrent_Amp_f32  |
| MtrVoltQax_Volt_f32 |                        |
| MtrCurrDax_Amp_f32  |                        |
| MtrCurrQax_Amp_f32  |                        |

###  [section-2]

## Module Internal Variables

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
<td>ModInPower_Watt_D_f32</td>
<td>Single Precision Floating Point</td>
<td>-2000</td>
<td>2000</td>
<td>ELEPWR_START_SEC_VAR_CLEARED _32</td>
</tr>
<tr class="even">
<td>DropInPower_Watt_D_f32</td>
<td>Single Precision Floating Point</td>
<td>-200</td>
<td>200</td>
<td>ELEPWR_START_SEC_VAR_CLEARED _32</td>
</tr>
</tbody>
</table>

###  [section-3]

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

| Constant Name            |
|--------------------------|
| k_CntlrInResist_Ohm_f32  |
| k_PstcPowerLoss_Watt_f32 |

##  [section-4]

## Program(fixed) Constants

### Embedded Constants

#### Local

| Constant Name                | Resolution             | Units   | Value          |
|-------------------------------|--------------|--------------|--------------|
| D_SQRT3OVR2_ULS_F32          | Single precision Float | Float32 | 0.866025403784 |
| D_ELECPOWERLOLMT_WATT_F32    | Single precision Float | Watt    | (-2000.0)      |
| D_ELECPOWERHILMT_WATT_F32    | Single precision Float | Watt    | 2000.0         |
| D_SUPPLYCURRENTLOLMT_AMP_F32 | Single precision Float | Amp     | (-200.0)       |
| D_SUPPLYCURRENTHILMT_AMP_F32 | Single precision Float | Amp     | (200.0)        |

#### Global

| Constant Name       |
|---------------------|
| D_ZERO_ULS_F32      |
| D_VECUMIN_VOLTS_F32 |

### Module specific Lookup Tables Constants

| Constant Name | Resolution | Value | Software Segment |
|---------------|------------|-------|------------------|
| None          |            |       |                  |

# Functions/Macros used by the Sub-Modules 

## Library Functions / Macros 

The library functions / Macros that are called by the various sub
modules are identified below,

## Data Hiding Functions

None

## Local Functions/Macros Used by this MDD only

None

#  Software Module Implementation

## Initial Data Values

| Data                                 | Value |
|--------------------------------------|-------|
| Rte_InitValue_Vecu_Volt_f32          | 5.0   |
| Rte_InitValue_MtrVoltDax_Volt_f32    | 0.0   |
| Rte_InitValue_MtrVoltQax_Volt_f32    | 0.0   |
| Rte_InitValue_MtrCurrDax_Amp_f32     | 0.0   |
| Rte_InitValue_MtrCurrQax_Amp_f32     | 0.0   |
| Rte_InitValue_ElectricPower_Watt_f32 | 0.0   |

##  [section-5]

## Periodic Functions

### Per: ElePwr_Per1

#### Design Rationale

None

#### Program Flow Start

Rte_Call_ElePwr_Per1_CP0_CheckpointReached()

#### Store Module Inputs to Local copies

| Local Copy          | Module Input                                   |
|---------------------|------------------------------------------------|
| Vecu_Volt_f32       | Rte_IRead_ElePwr_Per1_Vecu_Volt_f32()          |
| MtrVoltDax_Volt_f32 | Rte_IRead_ElePwr_Per1\_ MtrVoltDax_Volt_f32 () |
| MtrVoltQax_Volt_f32 | Rte_IRead_ElePwr_Per1\_ MtrVoltQax_Volt_f32 () |
| MtrCurrDax_Amp_f32  | Rte_IRead_ElePwr_Per1\_ MtrCurrDax_Amp_f32     |
| MtrCurrQax_Amp_f32  | Rte_IRead_ElePwr_Per1\_ MtrCurrQax_Amp_f32 ()  |

####  [section-6]

#### Calculate Modulator Input Power

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/ElePwr/doc/mediax/media/image2.emf)

#### Store Local copy of outputs into Module Outputs

| Local Copy              | Module Output                                     |
|------------------------------|------------------------------------------|
| ElecPower_Watt_T_f32    | Rte_IWrite_ElePwr_Per1\_ ElectricPower_Watt_f32() |
| SupplyCurrent_Amp_T_f32 | Rte_IWrite_ElePwr_Per1_SupplyCurrent_Amp_f32 ()   |

#### Program Flow End

## Rte_Call_ElePwr_Per1_CP1_CheckpointReached() [rte_call_elepwr_per1_cp1_checkpointreached]

## Fault Recovery Functions

None

## Shutdown Functions

None

## Interrupt Functions

None

## Serial Communication Functions

None

# Execution Requirements

## Execution Rates for sub-modules called by the Scheduler

| Function Name | Calling Frequency | System State(s) in which the function is called |
|----------------------------|-----------------|----------------------------|
| ElePwr_Per1   | 10 ms             | All                                             |

##  [section-7]

## Execution Requirements for Serial Communication Functions 

| Function Name | Sub-Module called by (Serial Comm Function Name) |
|---------------|--------------------------------------------------|
| None          |                                                  |

#  [section-8]

#  Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

| Name of Sub Module | Software Segment        |
|--------------------|-------------------------|
| ElePwr_Per1        | RTE_AP_ELEPWR_APPL_CODE |

##  [section-9]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

| Name of Sub Module | Software Segment |
|--------------------|------------------|
| None               |                  |

#  [section-10]

#  Known Issues / Limitations With Design

1.  None

#  Revision Control Log

|            |                                                                                     |           |                     |
|--------|---------------------------------------|-------------|-------------|
| **Rev \#** | **Change Description**                                                              | **Date**  | **Author Initials** |
| 1          | Initial AUTOSAR version (SF08 v001).                                                | 1-Dec-12  | Selva               |
| 2          | Name changed from CmElecPwr to ElePwr                                               | 10-Dec-12 | Selva               |
| 3          | Anomaly 6242 Limit Outputs                                                          | 02-Apr-14 | SB                  |
| 4          | Changed Vecu Initial value from 0 to 5, Changed naming for module display variables | 08-May-14 | SB                  |

{% endraw %}