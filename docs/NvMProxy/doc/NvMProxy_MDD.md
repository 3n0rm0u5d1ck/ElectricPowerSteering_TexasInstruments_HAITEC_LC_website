---
layout: default
title: NvMProxy_MDD
nav_order: 3
parent: Nvm Proxy
---
{% raw %}
# Module -- NvM Proxy [module----nvm-proxy]

# High-Level Description

(Description must be within 8-10 lines.)

# Figures

## Diagram – Function Data Sharing

This diagram depicts the physical memory allocation for the various
parts of the NvM Proxy system. 3 application RAM areas are shown for
illustrative purposes, however, this module can handle any number of
application RAM areas.

The memory stack components below the NvM are not shown in this diagram
to promote clarity.

The NvMProxy_CmdQueue is required to be allocated to global shared
memory to provide write access to the Proxy server function that is
designed to be called from any application.

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/NvMProxy/doc/mediax/media/image1.emf"
style="width:6in;height:2.87318in" />

### Diagram – NvM Data Initialization

Depiction of the Nv Data initialization sequence from the perspective of
which application is active (i.e. MPU configuration at the time of
operation execution)

Only pertinent initialization functions and steps are shown to promote
clarity.

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/NvMProxy/doc/mediax/media/image2.emf"
style="width:6in;height:4.3625in" />

### Diagram – NvM Runtime

Following is a depiction of the write Motor Position EOL calibrations
via diagnostic service request. The MtrPos component is assumed to be
running in the ASIL D application and its server runnable for processing
an EOL motor cal write request is assumed to invoke the NvM_WriteBlock
operation.

The lifelines in this diagram represent execution within the Os or an
application. The details of the diagnostic service request are omitted
from this diagram for clarity purposes.

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/NvMProxy/doc/mediax/media/image3.emf"
style="width:6in;height:3.281in" />

#  Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

| Module Inputs             | Module Outputs |      |
|---------------------------|----------------|------|
| Configured by NvMProxyCfg |                | None |
|                           |                |      |

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
<td>NvMPWriteRqst_Cnt_M_Str[D_NUMPRXYBLOCKS_CNT_U16]</td>
<td>See NvMPWriteBuff_Type</td>
<td>See NvMPWriteBuff_Type</td>
<td>See NvMPWriteBuff_Type</td>
<td>NVMPROXY_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="even">
<td>NvMPSetRBSRqst_Cnt_M_Str[D_NUMPRXYBLOCKS_CNT_U16]</td>
<td>See NvMPSetRBSBuff_Type</td>
<td>See NvMPSetRBSBuff_Type</td>
<td>See NvMPSetRBSBuff_Type</td>
<td>NVMPROXY_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
</tbody>
</table>

### User defined typedef definition/declaration 

This section documents any user types uniquely used for the module.

<table>
<colgroup>
<col style="width: 30%" />
<col style="width: 26%" />
<col style="width: 21%" />
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
<td>NvMProxyCfg_Type</td>
<td>NvMBlock</td>
<td>NvM_BlockIdType</td>
<td>0</td>
<td>FULL</td>
</tr>
<tr class="even">
<td></td>
<td>unsecurePtr</td>
<td>constant uint8* to variable data</td>
<td>NA</td>
<td>NA</td>
</tr>
<tr class="odd">
<td></td>
<td>securePtr</td>
<td>constant uint8* to variable data</td>
<td>NA</td>
<td>NA</td>
</tr>
<tr class="even">
<td></td>
<td>secureSize</td>
<td>uint16</td>
<td>0</td>
<td>FULL</td>
</tr>
<tr class="odd">
<td></td>
<td>initHandling</td>
<td>NvMProxy_InitHandling</td>
<td>See Datatype</td>
<td>See Datatype</td>
</tr>
<tr class="even">
<td></td>
<td>failResponse</td>
<td>NvMProxy_FailResponse</td>
<td>See Datatype</td>
<td>See Datatype</td>
</tr>
<tr class="odd">
<td></td>
<td>failActData</td>
<td>NvMP_FailActionDataType</td>
<td>See Datatype</td>
<td>See Datatype</td>
</tr>
<tr class="even">
<td></td>
<td>failActFunc</td>
<td>NvMP_FailActionFuncType</td>
<td>See Datatype</td>
<td>See Datatype</td>
</tr>
<tr class="odd">
<td>NvMProxy_InitHandling</td>
<td>NVMPROXY_NONE</td>
<td>uint8</td>
<td>0</td>
<td>0</td>
</tr>
<tr class="even">
<td></td>
<td>NVMPROXY_CRC16</td>
<td>uint8</td>
<td>1</td>
<td>1</td>
</tr>
<tr class="odd">
<td></td>
<td>NVMPROXY_REDUNDANT</td>
<td>uint8</td>
<td>2</td>
<td>2</td>
</tr>
<tr class="even">
<td></td>
<td>NVMPROXY_ZERODATA</td>
<td>uint8</td>
<td>3</td>
<td>3</td>
</tr>
<tr class="odd">
<td>NvMProxy_FailResponse</td>
<td>NVMPROXY_NOTAPPLICABLE</td>
<td>uint8</td>
<td>0</td>
<td>0</td>
</tr>
<tr class="even">
<td></td>
<td>NVMPROXY_NTC_0A</td>
<td>uint8</td>
<td>1</td>
<td>1</td>
</tr>
<tr class="odd">
<td></td>
<td>NVMPROXY_NTC_08_ROMDEF</td>
<td>uint8</td>
<td>2</td>
<td>2</td>
</tr>
<tr class="even">
<td></td>
<td>NVMPROXY_NTC_08_NOTIFFUNC</td>
<td>uint8</td>
<td>3</td>
<td>3</td>
</tr>
<tr class="odd">
<td></td>
<td>NVMPROXY_NTC_07_ROMDEF</td>
<td>uint8</td>
<td>4</td>
<td>4</td>
</tr>
<tr class="even">
<td></td>
<td>NVMPROXY_NTC_07_NOTIFFUNC</td>
<td>uint8</td>
<td>5</td>
<td>5</td>
</tr>
<tr class="odd">
<td></td>
<td>NVMPROXY_NTC_06_ROMDEF</td>
<td>uint8</td>
<td>6</td>
<td>6</td>
</tr>
<tr class="even">
<td></td>
<td>NVMPROXY_NTC_06_NOTIFFUNC</td>
<td>uint8</td>
<td>7</td>
<td>7</td>
</tr>
<tr class="odd">
<td>NvMP_FailActFuncType</td>
<td>Pointer to void function</td>
<td>pointer</td>
<td>N/A</td>
<td>N/A</td>
</tr>
<tr class="even">
<td>NvMP_FailActionDataType</td>
<td>Pointer to uint8</td>
<td>pointer</td>
<td>N/A</td>
<td>N/A</td>
</tr>
<tr class="odd">
<td>NvMPWriteBuff_Type</td>
<td>Pend</td>
<td>boolean</td>
<td>0</td>
<td>FULL</td>
</tr>
<tr class="even">
<td></td>
<td>BlkStatus</td>
<td>NvM_RequestResultType</td>
<td>0</td>
<td>FULL</td>
</tr>
<tr class="odd">
<td></td>
<td>SrcPtr</td>
<td>uint8*</td>
<td>NA</td>
<td>NA</td>
</tr>
<tr class="even">
<td>NvMPSetRBSBuff_Type</td>
<td>Pend</td>
<td>boolean</td>
<td>0</td>
<td>FULL</td>
</tr>
<tr class="odd">
<td></td>
<td>BlockChanged</td>
<td>boolean</td>
<td>NA</td>
<td>NA</td>
</tr>
</tbody>
</table>

# Constant Data Dictionary

## Calibration Constants

This section lists the calibrations used by the module. For details on
calibration constants, refer to the Data Dictionary for the application.

| Constant Name |
|---------------|
| \<None\>      |
|               |

## Configuration Constants

This section lists the configuration constants used by the module. For
details on configuration constants, refer to the Module User Guide. The
values are set by the integration project specific configuration files
Cd_NvMProxy_Cfg.h and Cd_NvMProxy_PBcfg.c

| Constant Name                           | Type             |
|-----------------------------------------|------------------|
| NvMProxyCfg \[D_NUMPRXYBLOCKS_CNT_U16\] | NvMProxyCfg_Type |

## Program(fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

| Constant Name             | Resolution | Units | Value                             |
|-------------------------------|--------------|--------------|--------------|
| D_NUMPRXYBLOCKS_CNT_U16   | 1          | Count | Configured in integration project |
| NVMPROXY_EXCLUSIVE_AREA_0 | NA         | NA    | Generated by SchM                 |
| D_CRC16SIZE_CNT_U16       | 1          | Count | 2                                 |

####  [section]

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

| Constant Name |
|---------------|
| \<None\>      |
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

1.  

## Data Hiding Functions

1.  NvM_WriteAll()

2.  NvM_WriteBlock()

3.  NvM_SetRamBlockStatus()

4.  NvM_GetErrorStatus()

5.  SchM_Enter_NvMProxy()

6.  SchM_Exit_NvMProxy()

## Global Functions/Macros Defined by this Module

### NvMProxy_WriteAll

|                      |                   |      |     |     |          |
|----------------------|-------------------|------|-----|-----|----------|
| **Function Name**    | NvMProxy_WriteAll | Type | Min | Max | UTP Tol. |
| **Arguments Passed** | None              |      |     |     |          |
| **Return Value**     | N one             |      |     |     |          |

#### Description

This function implements the AUTOSAR standard API for the NvM BSW
WriteAll service. The interface must adhere to the AUTOSAR standard to
allow mapping service port needs of SWC’s located in outside the QM
application to this component’s service interface via the Rte.

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/NvMProxy/doc/mediax/media/image4.emf)

### NvMProxy_WriteBlock

|                      |                     |                 |     |     |          |
|---------------|----------------------------|------------|------|------|------|
| **Function Name**    | NvMProxy_WriteBlock | Type            | Min | Max | UTP Tol. |
| **Arguments Passed** | Block               | NvM_BlockIdType |     |     |          |
|                      | SrcPtr              | uint8           |     |     |          |
| **Return Value**     | result              | Std_ReturnType  |     |     |          |

#### Description

This function implements the AUTOSAR standard API for the NvM BSW
WriteBlock service. The interface must adhere to the AUTOSAR standard to
allow mapping service port needs of SWC’s located in outside the QM
application to this component’s service interface via the Rte.

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/NvMProxy/doc/mediax/media/image5.emf)

### NvMProxy_GetErrorStatus

|                      |                         |                 |     |     |          |
|---------------|----------------------------|------------|------|------|------|
| **Function Name**    | NvMProxy_GetErrorStatus | Type            | Min | Max | UTP Tol. |
| **Arguments Passed** | Block                   | NvM_BlockIdType |     |     |          |
|                      | RequestResultPtr        | uint8\*         |     |     |          |
| **Return Value**     | N one                   |                 |     |     |          |

#### Description

This function implements the AUTOSAR standard API for the NvM BSW
GetErrorStatus service. The interface must adhere to the AUTOSAR
standard to allow mapping service port needs of SWC’s located in outside
the QM application to this component’s service interface via the Rte.

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/NvMProxy/doc/mediax/media/image6.emf)

### NvMProxy_SetRamBlockStatus

|                      |                            |                 |     |     |          |
|---------------|----------------------------|------------|------|------|------|
| **Function Name**    | NvMProxy_SetRamBlockStatus | Type            | Min | Max | UTP Tol. |
| **Arguments Passed** | Block                      | NvM_BlockIdType |     |     |          |
|                      | BlockChanged               | boolean         |     |     |          |
| **Return Value**     | N one                      |                 |     |     |          |

#### Description

This function implements the AUTOSAR standard API for the NvM BSW
SetRamBlockStatus service. The interface must adhere to the AUTOSAR
standard to allow mapping service port needs of SWC’s located in outside
the QM application to this component’s service interface via the Rte.

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/NvMProxy/doc/mediax/media/image7.emf)

## Local Functions/Macros Used by this MDD only

# Software Module Implementation

## Runtime Environment (RTE) Initial Values

This section lists the initial values of data written by this module but
controlled by the RTE. After RTE initialization, the data in this table
will contain these values.

| Data     | Value |
|----------|-------|
| \<None\> |       |

## Initialization Functions

### Init: NvMProxy_Init

#### Design Rationale

Transfer the data from the unsecured Nv Data memory buffer to the
secured Nv Data memory buffer and initialize the block status shadow to
the values returned by the NvM API.

#### Module Outputs

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/NvMProxy/doc/mediax/media/image8.emf)

#### Module Internal 

NvMPWriteRqst_Cnt_M_Str = 0\*

NvMPSetRBSRqst_Cnt_M_Str = 0\*

*\* Cleared by memory clear function and not explicitly cleared in this
init function*

##  Periodic Functions

### Per: NvMProxy_MainFunction

#### Design Rationale

This function is responsible for forwarding the queued NvM requests to
the NvM driver in a SchM task running the NvM BSW.

This function copies the secured data area to the unsecured data area.

#### Program Flow Start

None

#### Store Module Inputs to Local copies

None

#### Processing of function

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/NvMProxy/doc/mediax/media/image9.emf)

#### Store Local copy of outputs into Module Outputs

None

#### Program Flow End

None

##  Fault Recovery Functions

None

## Shutdown Functions

None

## Interrupt Functions

None

## Serial Communication Functions

None

##  

# Execution Requirements

## Execution Sequence of the Module

NvMProxy_Init must be scheduled after to NvM_ReadAll is completed.
Additionaly NvMProxy_Init must be executed as a trusted function to
grant rights for initializing the secured memory. This would typically
be accomplished via an Os trusted function call API.

NvMProxy_MainFunction should be scheduled prior to NvM_MainFunction.
This provides the minimal amount of lag in forwarding and processing NvM
service requests.

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

| Function Name         | Calling Frequency        | System State(s) in which the function is called |
|---------------------|----------------------|------------------------------|
| NvMProxy_Init         | Once during startup      | COLD INIT                                       |
| NvMProxy_MainFunction | Same as NvM_MainFunction | Same as NvM_MainFunction                        |

## Execution Requirements for Serial Communication Functions 

| Function Name | Sub-Module called by (Serial Comm Function Name) |
|---------------|--------------------------------------------------|
| \<None\>      |                                                  |

#  [section-2]

#  Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

| Name of Sub Module         | Software Segment        |
|----------------------------|-------------------------|
| NvMProxy_Init              | NVMPROXY_START_SEC_CODE |
| NvMProxy_MainFunction      | NVMPROXY_START_SEC_CODE |
| NvMProxy_WriteAll          | NVMPROXY_START_SEC_CODE |
| NvMProxy_WriteBlock        | NVMPROXY_START_SEC_CODE |
| NvMProxy_SetRamBlockStatus | NVMPROXY_START_SEC_CODE |
| NvMProxy_GetErrorStatus    | NVMPROXY_START_SEC_CODE |

##  [section-3]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

| Name of Sub Module | Software Segment |
|--------------------|------------------|
| None               |                  |

#  [section-4]

#  Known Issues / Limitations With Design

1.  

#  Revision Control Log

|             |            |                                                 |           |                     |
|------|------|--------------------------------------------|---------|---------|
| **Item \#** | **Rev \#** | **Change Description**                          | **Date**  | **Author Initials** |
| 1           |            | Initial creation                                | 21-Mar-12 | JJW                 |
| 2           |            | Corrected anomaly 4437 in NvMProxy init routine | 01-Mar-13 | KJS                 |
| 3           |            |                                                 | 30-May-13 | JJW                 |
| 4           |            | Added CRC and Redundant block checking ability  | 22-Nov-13 | LWW                 |

{% endraw %}