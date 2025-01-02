---
layout: default
title: TMS570_Startup_FiqIntVect_MDD
nav_order: 5
parent: TMS570 Startup
---
{% raw %}
# High-Level Description

fiqintvect provides the assembly language fiq handling function. The
function loads the program counter with the value of the FIQ Interrupt
Vector Register, which contains the address of the ISR with the highest
priority pending FIQ request.

# Figures

## Diagram – Function Data Sharing

No Shared Data

# Variable Data Dictionary

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

NOTE that all global functions in this module must be assembled in ARM
mode. Therefore the .asm source file includes the .arm directive at the
beginning of the file, applying the directive to all functions in the
file.

### Global Function \#1

|                      |              |      |      |     |     |          |
|----------------------|--------------|------|------|-----|-----|----------|
| **Function Name**    | \_fiqhandler | Type | Dir. | Min | Max | UTP Tol. |
| **Arguments Passed** | None         |      |      |     |     |          |
| **Return Value**     | None         |      |      |     |     |          |

#### Design Rationale

This function is required when more than one FIQ is configured in the
system. When only one FIQ is configured, its ISR can be directly
configured in DaVinci as the FIQ Handler. (Alternatively, the
\_fiqhandler function could be configured and its code changed to branch
to the one FIQ ISR.) When there are multiple FIQs, the \_fiqhandler
function is needed so that the one handler configured in DaVinci will go
to the correct ISR address as found in the processor FIQ Interrupt
Vector Register.

#### Description

Loads the program counter with the value of the FIQ Interrupt Vector
Register, which contains the address of the ISR with the highest
priority pending FIQ request.

**.def \_fiqhandler**

**.asmfunc**

**\_fiqhandler**

**ldr r8, fiqvectreg**

**ldr pc, \[r8\]**

**fiqvectreg .word 0xFFFFFE74**

**.endasmfunc**

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

## Interrupt Functions

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

# Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

| Name of Sub Module | Software Segment |
|--------------------|------------------|
| \_fiqhandler       | N/A              |

##  [section-3]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

| Name of Local Function | Software Segment |
|------------------------|------------------|
| None                   |                  |
|                        |                  |

#  [section-4]

# Known Issues / Limitations With Design

None

# Revision Control Log

|             |            |                         |           |                     |
|------|------|--------------------------------------------|---------|---------|
| **Item \#** | **Rev \#** | **Change Description**  | **Date**  | **Author Initials** |
| 1           | 1.0        | Initial Revision of MDD | 6/10/2013 | KMC                 |

{% endraw %}