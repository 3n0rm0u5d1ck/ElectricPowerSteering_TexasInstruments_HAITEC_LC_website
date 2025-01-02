---
layout: default
title: TMS570_Startup_BootStartup_MDD
nav_order: 4
parent: TMS570 Startup
---
{% raw %}
# Module --  [module---]

# High-Level Description

This module outlines the functionality of the system startup functions
of the TMS570. This code is intended to be run starting after the sys
startup routine in the boot project.

# Figures

## Diagram – Function Data Sharing

This diagram shows all data that is shared between functions within the
module.

No Shared Data

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

| Typedef Name | Element Name | Value |
|--------------|--------------|-------|
|              |              |       |

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
|               |            |       |       |

####  [section]

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

| Constant Name |
|---------------|
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

### Global Function \#1

| **Function Name**    | (Exact name used)                                  | Type | Min | Max | UTP Tol. |
|----------------|------------------------------|----------|------|------|------|
| **Arguments Passed** | (if none, write None)                              |      |     |     |          |
|                      | (Insert more rows for additional passed arguments) |      |     |     |          |
| **Return Value**     | (if no value returned, write N/A)                  |      |     |     |          |

#### Description

(Place flowchart/design for local function)

## Local Functions/Macros Used by this MDD only

### Local Function \#1

| **Function Name**    | (Exact name used)                                  | Type | Min | Max | UTP Tol. |
|-----------------|------------------------------|----------|------|------|------|
| **Arguments Passed** | (if none, write None)                              |      |     |     |          |
|                      | (Insert more rows for additional passed arguments) |      |     |     |          |
| **Return Value**     | (if no value returned, write N/A)                  |      |     |     |          |

#### Description

(Place flowchart/design for local function)

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

### Init: BootStartup

#### Design Rationale

This function is designed to be called at the end of the sys_startup
initialization routine. Note that most of this initialization code (for
initializing copy table, global variables, and constructors) was taken
from Texas Instruments’ startup code example implementation.

#### Processing

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/TMS570_Startup/doc/mediax/media/image1.emf)

##  Periodic Functions

None

## Fault Recovery Functions

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

## Execution Rates for sub-modules called by the Scheduler

This table serves as reference for the Scheduler design

| Function Name | Calling Frequency                         | System State(s) in which the function is called |
|--------------------------|-----------------|------------------------------|
| BootStartup() | called by sys_startup initialization code | N/A                                             |

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
| BootStartup()      |                  |

##  [section-3]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

| Name of Sub Module | Software Segment |
|--------------------|------------------|
|                    |                  |

#  [section-4]

#  Known Issues / Limitations With Design

1.  (Item \#1)

#  Revision Control Log

| **Item \#** | **Rev \#** | **Change Description** | **Date** | **Author Initials** |
|------|------|--------------------------------------------|---------|---------|
| 1           | 1          | Initial creation       | 05/14/12 | LWW                 |

{% endraw %}