---
layout: default
title: OsErrCallouts_MDD
nav_order: 7
parent: TMS570 MCU Diag
---
{% raw %}
# High-Level Description

OsErrCallouts provides the error hook functions ErrorHook() and
ProtectionHook() to provide diagnostic information for certain errors
that result in calls to these hooks.

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

| Module Inputs | Module Outputs |     |
|---------------|----------------|-----|
| None          |                |     |
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
<td>None</td>
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
| None          |            |       |       |

####  [section]

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

| Constant Name              |
|----------------------------|
| UNUSEDINTERRUPT            |
| STACKOVERWRITE             |
| MPUVIOLATION               |
| osdErrSOStackOverflow      |
| osdErrYOStackOverflow      |
| osdErrUEUnhandledException |

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

1.  RednRpdShtdn()

## Data Hiding Functions

1.  OSErrorGetosCANError()

## Global Functions/Macros Defined by this Module

### Global Function \#1

|                      |           |            |      |     |     |          |
|----------------------|-----------|------------|------|-----|-----|----------|
| **Function Name**    | ErrorHook | Type       | Dir. | Min | Max | UTP Tol. |
| **Arguments Passed** | ErrorCode | StatusType |      | N/A | N/A |          |
| **Return Value**     | N/A       |            |      |     |     |          |

#### Design Rationale

When the error was an unhandled exception, reset with a reset cause
indicating unexpected interrupt. Currently does no handling of other
errors.

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/TMS570_uDiag/doc/mediax/media/image1.emf)

### Global Function \#2

|                      |                                                           |                      |      |              |     |          |
|----------------|--------------------|--------------|-----|--------|------|-----|
| **Function Name**    | ProtectionHook                                            | Type                 | Dir. | Min          | Max | UTP Tol. |
| **Arguments Passed** | ErrorCode                                                 | StatusType           |      | N/A          | N/A |          |
| **Return Value**     | \<has return value defined but function does not return\> | ProtectionReturnType |      | PRO_SHUTDOWN |     |          |

#### Design Rationale

When the protection violation was a stack fault, reset with a reset
cause of STACKOVERWRITE. For any other protection violation, reset with
a reset cause of MPUVIOLATION.

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/TMS570_uDiag/doc/mediax/media/image2.emf)

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

None.

# Memory Map Definition Requirements

## Sub Modules (Functions)

This table identifies the software segments for functions identified in
this module.

| Name of Sub Module | Software Segment |
|--------------------|------------------|
| ErrorHook          | APPLCB_CODE      |
| ProtectionHook     | APPLCB_CODE      |

##  [section-2]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

| Name of Local Function | Software Segment |
|------------------------|------------------|
| None                   |                  |
|                        |                  |

#  [section-3]

#  Known Issues / Limitations With Design

None

#  Revision Control Log

|             |            |                        |           |                     |
|------|------|--------------------------------------------|---------|---------|
| **Item \#** | **Rev \#** | **Change Description** | **Date**  | **Author Initials** |
| 1           | 1.0        | Initial Revision       | 6/26/2013 | KMC                 |

{% endraw %}