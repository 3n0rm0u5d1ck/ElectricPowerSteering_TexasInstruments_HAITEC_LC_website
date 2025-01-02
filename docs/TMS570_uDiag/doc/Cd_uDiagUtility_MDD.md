---
layout: default
title: Cd_uDiagUtility_MDD
nav_order: 3
parent: TMS570 MCU Diag
---
{% raw %}
# High-Level Description

Cd_uDiagUtility provides utility assembly language functions needed by
the Cd_uDiag component.

# Figures

## Diagram – Function Data Sharing

No Shared Data

#  Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

(Note: Full variable names required in table.)

(Note: All global variables including End Of Line data used should be
shown here)

| Module Inputs | Module Outputs |          |
|---------------|----------------|----------|
| \<None\>      |                | \<None\> |
|               |                |          |

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
<td>&lt;None&gt;</td>
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
<td>&lt;None&gt;</td>
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

####  [section]

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

| Constant Name |
|---------------|
| \<None\>      |

### Module specific Lookup Tables Constants

(This is for lookup tables (arrays) with fixed values, same name as
other tables)

| Constant Name | Resolution | Value | Software Segment |
|---------------|------------|-------|------------------|
| \<None\>      |            |       |                  |

#  Functions/Macros used by the Sub-Modules 

## Library Functions / Macros 

The library and functions / Macros that are called by the various sub
modules are identified below,

1.  \<None\>

## Data Hiding Functions

1.  \<None\>

## Global Functions/Macros Defined by this Module

### Global Function \#1

|                      |                                                                     |        |      |      |      |          |
|----------------|-----------------------------|--------|-----|------|------|-----|
| **Function Name**    | \_uDiagGetLinkRegForFiqIsr\_()                                      | Type   | Dir. | Min  | Max  | UTP Tol. |
| **Arguments Passed** | None                                                                |        |      |      |      |          |
| **Return Value**     | Link Register as saved in top stack frame when executing an FIQ ISR | uint32 |      | FULL | FULL |          |

#### Description

The saved link register is at offset 0x5C from the top of the stack.
Load saved link register value to register R0 and return.

ldr r0, \[sp, \#0x5C\]

bx lr

## Local Functions/Macros Used by this MDD only

None

# Software Module Implementation

## Runtime Environment (RTE) Initial Values

This section lists the initial values of data written by this module but
controlled by the RTE. After RTE initialization, the data in this table
will contain these values.

| Data     | Value |
|----------|-------|
| \<None\> |       |

## Initialization Functions

None

## Periodic Functions

None

## Fault Recovery Functions

None

## Shutdown Functions

None

##  Interrupt Functions

None

## Serial Communication Functions

None

##  [section-1]

# Execution Requirements

## Execution Sequence of the Module

(Describe in words relevant details about the execution sequence of the
different sub modules.)

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

| Name of Sub Module           | Software Segment |
|------------------------------|------------------|
| \_uDiagGetLinkRegForFiqIsr\_ | N/A              |

##  [section-3]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

| Name of Local Function | Software Segment |
|------------------------|------------------|
| None                   |                  |
|                        |                  |

#  [section-4]

#  Known Issues / Limitations With Design

None

# Revision Control Log

|             |            |                        |          |                     |
|------|------|--------------------------------------------|---------|---------|
| **Item \#** | **Rev \#** | **Change Description** | **Date** | **Author Initials** |
| 1           | 1.0        | Initial Revision       | 6/6/2013 | KMC                 |

{% endraw %}