---
layout: default
title: Fee_Interface_MDD
nav_order: 1
parent: Nvm Manager
---
{% raw %}
# Module --  [module---]

# High-Level Description

This module contains the specific interfacing functions that are needed
for TI’s Fee Driver. This includes an initialization routine and
configurable trusted function interfaces that allow compatibility with
the NvM/MemIf BSW.

# Figures

## Diagram – Function Data Sharing

N/A

### Diagram – Function (Name)

N/A

#  Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

| Module Inputs | Module Outputs |     |
|---------------|----------------|-----|
|               |                |     |
|               |                |     |

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

This section lists the calibrations used by the module. For details on
calibration constants, refer to the Data Dictionary for the application.

| Constant Name |
|---------------|
| \<None\>      |
|               |

## Program(fixed) Constants

### Embedded Constants

All embedded constants whose values are provided in Eng units will be
evaluated to the equivalent counts by using the FPM_InitFixedPoint_m()
macro within the \#define statement.

#### Local

| Constant Name | Resolution | Units | Value |
|---------------|------------|-------|-------|
| \<None\>      |            |       |       |
|               |            |       |       |

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

1.  \<None\>

2.  

## Data Hiding Functions

1.  \<None\>

2.  

## Global Functions/Macros Defined by this Module

### Global Functions Defined if BC_FEEIF_ECUSTARTUPTRUSTED == STD_OFF

#### TWrapC_FeeIf_Init

This is the client (non-trusted) side of the FeeIf_Init Trusted Function

|                      |                   |      |     |     |          |
|----------------------|-------------------|------|-----|-----|----------|
| **Function Name**    | TWrapC_FeeIf_Init | Type | Min | Max | UTP Tol. |
| **Arguments Passed** | None              |      |     |     |          |
|                      |                   |      |     |     |          |
| **Return Value**     | N/A               |      |     |     |          |

##### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/NvMMgr/doc/mediax/media/image1.emf)

#### TRUSTED_TWrapS_FeeIf_Init

This is the server (trusted) side of the FeeIf_Init Trusted Function

|                      |                           |                                 |     |     |          |
|------------|------------------------|---------------------|------|------|------|
| **Function Name**    | TRUSTED_TWrapS_FeeIf_Init | Type                            | Min | Max | UTP Tol. |
| **Arguments Passed** | FunctionIndex             | TrustedFunctionIndexType        |     |     |          |
|                      | FunctionParams            | TrustedFunctionParameterRefType |     |     |          |
| **Return Value**     | N/A                       |                                 |     |     |          |

##### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/NvMMgr/doc/mediax/media/image2.emf)

#### TWrapC_Fee_MainFunction

This is the client (non-trusted) side of the Fee_MainFunction Trusted
Function

|                      |                         |      |     |     |          |
|----------------------|-------------------------|------|-----|-----|----------|
| **Function Name**    | TWrapC_Fee_MainFunction | Type | Min | Max | UTP Tol. |
| **Arguments Passed** | None                    |      |     |     |          |
|                      |                         |      |     |     |          |
| **Return Value**     | N/A                     |      |     |     |          |

##### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/NvMMgr/doc/mediax/media/image3.emf)

#### TRUSTED_TWrapS_Fee_MainFunction

This is the server (trusted) side of the Fee_MainFunction Trusted
Function

|                      |                                 |                                 |     |     |          |
|-----------|-------------------------|---------------------|-----|------|------|
| **Function Name**    | TRUSTED_TWrapS_Fee_MainFunction | Type                            | Min | Max | UTP Tol. |
| **Arguments Passed** | FunctionIndex                   | TrustedFunctionIndexType        |     |     |          |
|                      | FunctionParams                  | TrustedFunctionParameterRefType |     |     |          |
| **Return Value**     | N/A                             |                                 |     |     |          |

##### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/NvMMgr/doc/mediax/media/image4.emf)

### Global Functions Defined if BC_FEEIF_NVMTRUSTED == STD_OFF

#### TWrapC_Fee_Read

This is the client (non-trusted) side of the Fee_Read Trusted Function

|                      |                                       |                |     |     |          |
|---------------|-----------------------------|-----------|------|------|------|
| **Function Name**    | TWrapC_Fee_Read                       | Type           | Min | Max | UTP Tol. |
| **Arguments Passed** | BlockNumber                           | uint16         |     |     |          |
|                      | BlockOffset                           | uint16         |     |     |          |
|                      | DataBufferPtr                         | uint8\*        |     |     |          |
|                      | Length                                | uint16         |     |     |          |
| **Return Value**     | myargs.TWrapS_Fee_Read_args.os_result | Std_ReturnType |     |     |          |

##### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/NvMMgr/doc/mediax/media/image5.emf)

#### TRUSTED_TWrapS_Fee_Read

This is the server (trusted) side of the Fee_Read Trusted Function

|                      |                         |                                 |     |     |          |
|------------|------------------------|---------------------|-----|------|------|
| **Function Name**    | TRUSTED_TWrapS_Fee_Read | Type                            | Min | Max | UTP Tol. |
| **Arguments Passed** | FunctionIndex           | TrustedFunctionIndexType        |     |     |          |
|                      | FunctionParams          | TrustedFunctionParameterRefType |     |     |          |
| **Return Value**     | N/A                     |                                 |     |     |          |

##### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/NvMMgr/doc/mediax/media/image6.emf)

#### TWrapC_Fee_Write

This is the client (non-trusted) side of the Fee_Write Trusted Function

|                      |                                        |                |     |     |          |
|---------------|-----------------------------|-----------|------|------|------|
| **Function Name**    | TWrapC_Fee_Write                       | Type           | Min | Max | UTP Tol. |
| **Arguments Passed** | BlockNumber                            | uint16         |     |     |          |
|                      | DataBufferPtr                          | uint8\*        |     |     |          |
| **Return Value**     | myargs.TWrapS_Fee_Write_args.os_result | Std_ReturnType |     |     |          |

##### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/NvMMgr/doc/mediax/media/image7.emf)

#### TRUSTED_TWrapS_Fee_Write

This is the server (trusted) side of the Fee_Write Trusted Function

|                      |                          |                                 |     |     |          |
|------------|------------------------|---------------------|-----|------|------|
| **Function Name**    | TRUSTED_TWrapS_Fee_Write | Type                            | Min | Max | UTP Tol. |
| **Arguments Passed** | FunctionIndex            | TrustedFunctionIndexType        |     |     |          |
|                      | FunctionParams           | TrustedFunctionParameterRefType |     |     |          |
| **Return Value**     | N/A                      |                                 |     |     |          |

##### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/NvMMgr/doc/mediax/media/image8.emf)

#### TWrapC_Fee_EraseImmediateBlock

This is the client (non-trusted) side of the Fee_EraseImmediateBlock
Trusted Function

|                      |                                                      |                |     |     |          |
|------------|----------------------------------|-----------|-----|------|------|
| **Function Name**    | TWrapC_Fee_EraseImmediateBlock                       | Type           | Min | Max | UTP Tol. |
| **Arguments Passed** | BlockNumber                                          | uint16         |     |     |          |
|                      |                                                      |                |     |     |          |
| **Return Value**     | myargs.TWrapS_Fee_EraseImmediateBlock_args.os_result | Std_ReturnType |     |     |          |

##### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/NvMMgr/doc/mediax/media/image9.emf)

#### TRUSTED_TWrapS_Fee_EraseImmediateBlock

This is the server (trusted) side of the Fee_EraseImmediateBlock Trusted
Function

|                      |                                        |                                 |     |     |          |
|----------|----------------------------|---------------------|-----|-----|-----|
| **Function Name**    | TRUSTED_TWrapS_Fee_EraseImmediateBlock | Type                            | Min | Max | UTP Tol. |
| **Arguments Passed** | FunctionIndex                          | TrustedFunctionIndexType        |     |     |          |
|                      | FunctionParams                         | TrustedFunctionParameterRefType |     |     |          |
| **Return Value**     | N/A                                    |                                 |     |     |          |

##### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/NvMMgr/doc/mediax/media/image10.emf)

#### TWrapC_Fee_InvalidateBlock

This is the client (non-trusted) side of the Fee_InvalidateBlock Trusted
Function

|                      |                                                       |                |     |     |          |
|-------------|---------------------------------|-----------|------|------|------|
| **Function Name**    | TWrapC_Fee_InvalidateBlock                            | Type           | Min | Max | UTP Tol. |
| **Arguments Passed** | BlockNumber                                           | uint16         |     |     |          |
|                      |                                                       |                |     |     |          |
| **Return Value**     | myargs.TWrapS_Fee_InvalidateBlock_args_args.os_result | Std_ReturnType |     |     |          |

##### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/NvMMgr/doc/mediax/media/image11.emf)

#### TRUSTED_TWrapS_Fee_InvalidateBlock

This is the server (trusted) side of the Fee_InvalidateBlock Trusted
Function

|                      |                                    |                                 |     |     |          |
|-----------|-------------------------|---------------------|-----|------|------|
| **Function Name**    | TRUSTED_TWrapS_Fee_InvalidateBlock | Type                            | Min | Max | UTP Tol. |
| **Arguments Passed** | FunctionIndex                      | TrustedFunctionIndexType        |     |     |          |
|                      | FunctionParams                     | TrustedFunctionParameterRefType |     |     |          |
| **Return Value**     | N/A                                |                                 |     |     |          |

##### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/NvMMgr/doc/mediax/media/image12.emf)

#### TWrapC_Fee_Cancel

This is the client (non-trusted) side of the Fee_Cancel Trusted Function

|                      |                   |      |     |     |          |
|----------------------|-------------------|------|-----|-----|----------|
| **Function Name**    | TWrapC_Fee_Cancel | Type | Min | Max | UTP Tol. |
| **Arguments Passed** | None              |      |     |     |          |
|                      |                   |      |     |     |          |
| **Return Value**     | N/A               |      |     |     |          |

##### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/NvMMgr/doc/mediax/media/image13.emf)

#### TRUSTED_TWrapS_Fee_Cancel

This is the server (trusted) side of the Fee_Cancel Trusted Function

|                      |                           |                                 |     |     |          |
|------------|------------------------|---------------------|-----|------|------|
| **Function Name**    | TRUSTED_TWrapS_Fee_Cancel | Type                            | Min | Max | UTP Tol. |
| **Arguments Passed** | FunctionIndex             | TrustedFunctionIndexType        |     |     |          |
|                      | FunctionParams            | TrustedFunctionParameterRefType |     |     |          |
| **Return Value**     | N/A                       |                                 |     |     |          |

##### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/NvMMgr/doc/mediax/media/image14.emf)

#### TWrapC_Fee_GetStatus

This is the client (non-trusted) side of the Fee_GetStatus Trusted
Function

|                      |                                            |       |     |     |          |
|----------------|------------------------------|----------|------|------|------|
| **Function Name**    | TWrapC_Fee_GetStatus                       | Type  | Min | Max | UTP Tol. |
| **Arguments Passed** | None                                       |       |     |     |          |
|                      |                                            |       |     |     |          |
| **Return Value**     | myargs.TWrapS_Fee_GetStatus_args.os_result | uint8 |     |     |          |

##### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/NvMMgr/doc/mediax/media/image15.emf)

#### TRUSTED_TWrapS_Fee_GetStatus

This is the server (trusted) side of the Fee_GetStatus Trusted Function

|                      |                              |                                 |     |     |          |
|-----------|-------------------------|---------------------|-----|------|------|
| **Function Name**    | TRUSTED_TWrapS_Fee_GetStatus | Type                            | Min | Max | UTP Tol. |
| **Arguments Passed** | FunctionIndex                | TrustedFunctionIndexType        |     |     |          |
|                      | FunctionParams               | TrustedFunctionParameterRefType |     |     |          |
| **Return Value**     | N/A                          |                                 |     |     |          |

##### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/NvMMgr/doc/mediax/media/image16.emf)

#### TWrapC_Fee_GetJobResult

This is the client (non-trusted) side of the Fee_GetJobResult Trusted
Function

|                      |                                               |       |     |     |          |
|----------------|------------------------------|----------|------|------|------|
| **Function Name**    | TWrapC_Fee_GetJobResult                       | Type  | Min | Max | UTP Tol. |
| **Arguments Passed** | None                                          |       |     |     |          |
|                      |                                               |       |     |     |          |
| **Return Value**     | myargs.TWrapS_Fee_GetJobResult_args.os_result | uint8 |     |     |          |

##### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/NvMMgr/doc/mediax/media/image17.emf)

#### TRUSTED_TWrapS_Fee_GetJobResult

This is the server (trusted) side of the Fee_GetJobResult Trusted
Function

|                      |                                 |                                 |     |     |          |
|-----------|-------------------------|---------------------|-----|------|------|
| **Function Name**    | TRUSTED_TWrapS_Fee_GetJobResult | Type                            | Min | Max | UTP Tol. |
| **Arguments Passed** | FunctionIndex                   | TrustedFunctionIndexType        |     |     |          |
|                      | FunctionParams                  | TrustedFunctionParameterRefType |     |     |          |
| **Return Value**     | N/A                             |                                 |     |     |          |

##### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/NvMMgr/doc/mediax/media/image18.emf)

#### TWrapC_TI_Fee_SuspendResumeErase

This is the client (non-trusted) side of the TI_Fee_SuspendResumeErase
Trusted Function

|                      |                                  |       |     |     |          |
|-----------|-------------------------|---------------------|-----|------|------|
| **Function Name**    | TWrapC_TI_Fee_SuspendResumeErase | Type  | Min | Max | UTP Tol. |
| **Arguments Passed** | Command                          | uint8 | 0   | 1   |          |
| **Return Value**     | N/A                              |       |     |     |          |

##### Description

While the command type is a uint8, the actual type is
TI_Fee_EraseCommandType.

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/NvMMgr/doc/mediax/media/image19.emf)

#### TRUSTED_TWrapS_TI_Fee_SuspendResumeErase

This is the server (trusted) side of the TI_Fee_SuspendResumeErase
Trusted Function

|                      |                                          |                                 |     |     |          |
|---------|-----------------------------|---------------------|-----|-----|-----|
| **Function Name**    | TRUSTED_TWrapS_TI_Fee_SuspendResumeErase | Type                            | Min | Max | UTP Tol. |
| **Arguments Passed** | FunctionIndex                            | TrustedFunctionIndexType        |     |     |          |
|                      | FunctionParams                           | TrustedFunctionParameterRefType |     |     |          |
| **Return Value**     | N/A                                      |                                 |     |     |          |

##### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/NvMMgr/doc/mediax/media/image20.emf)

## Local Functions/Macros Used by this MDD only

### Local Function \#1

|                      |      |      |     |     |          |
|----------------------|------|------|-----|-----|----------|
| **Function Name**    | None | Type | Min | Max | UTP Tol. |
| **Arguments Passed** |      |      |     |     |          |
|                      |      |      |     |     |          |
| **Return Value**     |      |      |     |     |          |

#### Description

N/A

# Software Module Implementation

## Runtime Environment (RTE) Initial Values

This section lists the initial values of data written by this module but
controlled by the RTE. After RTE initialization, the data in this table
will contain these values.

| Data     | Value |
|----------|-------|
| \<None\> |       |

## Initialization Functions

(Note: For multiple init functions, insert new headers at the “Header 2”
level – subset of “5.1 Initialization Functions” and follow the same
sub-section design shown below)

### Init: FeeIf_Init

#### Design Rationale

This function initializes the FEE driver. After the FEE BSW
initialization, the Fee_MainFunction is required to be called until the
FEE reports a status that is not busy. This is required because the
NvM/MemIf BSWs currently make the assumption that the FEE driver will
not be busy at initialization; however, the FEE driver may be busy if it
has to finish any virtual sector swapping that may have been interrupted
(i.e. the NvM currently can issue a new FEE command to the driver
without first checking the FEE internal status the very first time after
a new power cycle).

#### Module Outputs

None

#### Module Internal 

None

#### Processing

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/NvMMgr/doc/mediax/media/image21.emf)

##  Periodic Functions

None

##  Fault Recovery Functions

None

##  Shutdown Functions

None

##  Interrupt Functions

None

##  Serial Communication Functions

None

##  

# Execution Requirements

## Execution Sequence of the Module

See Integration Manual

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

| Function Name | Calling Frequency | System State(s) in which the function is called |
|--------------------------|-----------------|------------------------------|
| \<None\>      |                   |                                                 |

## Execution Requirements for Serial Communication Functions 

| Function Name | Sub-Module called by (Serial Comm Function Name) |
|---------------|--------------------------------------------------|
| \<None\>      |                                                  |

#  [section-2]

#  Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

| Name of Sub Module | Software Segment |
|--------------------|------------------|
|                    |                  |

##  [section-3]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

| Name of Sub Module | Software Segment |
|--------------------|------------------|
|                    |                  |

#  [section-4]

#  Known Issues / Limitations With Design

1.  FeeIf_Init currently does not implement any of the available error
    recovery mechanisms in the case of an issue with the FEE driver.
    Additionally, it doesn’t set any faults or report out any errors to
    the user if one of these FEE memory errors occur.

2.  For the provided trusted functions, there is currently neither
    checking on the passed parameters nor checking on the caller of the
    trusted function. It was unclear during the current design if either
    of these was necessary.

3.  This MDD is currently missing some datatype definition and ranges
    (specifically for the trusted function call wrappers). The
    assumption was that these would not need to be unit tested and were
    for design documentation only.

#  Revision Control Log

|             |            |                                                              |          |                     |
|------|------|--------------------------------------------|---------|---------|
| **Item \#** | **Rev \#** | **Change Description**                                       | **Date** | **Author Initials** |
| 1           | 1          | Initial version                                              | 07/15/13 | LWW                 |
| 2           | 1.1.1      | Added suspend/resume erase functions                         | 11/04/14 | KJS                 |
| 3           | 1.1.2      | Added FEE Single bit ECC correction                          | 12/15/14 | PS                  |
| 4           | 3.1.1      | Updated FEE component and removed Nexteer FEE ECC workaround | 1/27/15  | PS                  |

{% endraw %}