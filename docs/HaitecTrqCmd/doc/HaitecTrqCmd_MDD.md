---
layout: default
title: HaitecTrqCmd_MDD
nav_order: 4
parent: HaitecTrqCmd
---
{% raw %}
**Module Design Document**

**For**

**Haitec Torque Command**

**Sep 08, 2015**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**SEPG,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                 |                |             |             |                 |
|-----------------|----------------|-------------|-------------|-----------------|
| **Description** | **Author**     | **Version** | **Date**    | **Approved By** |
| Initial Version | Jayakrishnan T | 1.0         | 08-SEP-2015 | SEPG            |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [4](#introduction)](#introduction)

[1.1 Purpose [4](#purpose)](#purpose)

[2 HaitecTrqCmd & High-Level Description
[5](#haitectrqcmd-high-level-description)](#haitectrqcmd-high-level-description)

[3 Design details of software module
[6](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of \<MDD Name\>
[6](#graphical-representation-of-mdd-name)](#graphical-representation-of-mdd-name)

[3.2 Data Flow Diagram [6](#data-flow-diagram)](#data-flow-diagram)

[3.2.1 Module level DFD [6](#module-level-dfd)](#module-level-dfd)

[3.2.2 Sub-Module level DFD
[6](#sub-module-level-dfd)](#sub-module-level-dfd)

[3.3 Component diagram [6](#component-diagram)](#component-diagram)

[3.4 Variable Data Dictionary
[6](#variable-data-dictionary)](#variable-data-dictionary)

[3.4.1 User defined ‘typedef’ definition/declaration
[6](#user-defined-typedef-definitiondeclaration)](#user-defined-typedef-definitiondeclaration)

[3.4.2 Variable definition for enumerated types
[6](#variable-definition-for-enumerated-types)](#variable-definition-for-enumerated-types)

[3.5 Constant Data Dictionary
[7](#constant-data-dictionary)](#constant-data-dictionary)

[3.5.1 Program Constants [7](#program-constants)](#program-constants)

[3.5.2 Module Specific Lookup Tables
[7](#module-specific-lookup-tables)](#module-specific-lookup-tables)

[3.6 Software Module Implementation
[7](#software-module-implementation)](#software-module-implementation)

[3.6.1 Sub-Module Functions
[7](#sub-module-functions)](#sub-module-functions)

[3.6.2 Interrupt Service Routines
[7](#interrupt-service-routines)](#interrupt-service-routines)

[3.6.3 \_SCOMM () Functions [7](#scomm-functions)](#scomm-functions)

[3.6.4 Module Internal (Local) Functions
[8](#module-internal-local-functions)](#module-internal-local-functions)

[3.6.5 Transition Functions
[8](#transition-functions)](#transition-functions)

[4 Known Limitations with Design
[9](#known-limitations-with-design)](#known-limitations-with-design)

[5 UNIT TEST CONSIDERATION
[10](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[11](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [12](#glossary)](#glossary)

[Appendix C References [13](#references)](#references)

# Introduction

## Purpose

MDD for Haitec Torque Command component.

# HaitecTrqCmd & High-Level Description

This component provides a motor torque command from diagnostic service
that is manipulated by a damping curve based on motor velocity. This is
intended to help provide system stability when the part is being
operated via torque over CAN messages on a test stand or bench.

# Design details of software module

None

## Graphical representation of \<MDD Name\>

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/HaitecTrqCmd/doc/mediax/media/image1.png"
style="width:3in;height:2.66944in" />

## Data Flow Diagram

### Module level DFD

None

### Sub-Module level DFD

None

## Component diagram

None

## Variable Data Dictionary

### User defined ‘typedef’ definition/declaration

None

### Variable definition for enumerated types

None

## Constant Data Dictionary

### Program Constants

#### Local Constants

| Constant Name       | Resolution | Units | Value  |
|---------------------|------------|-------|--------|
| D_VEHSPDTHD_KPH_F32 | 1          | KPH   | 0.001F |

#### Global Constants

None

### Module Specific Lookup Tables

None

## Software Module Implementation

### Sub-Module Functions

#### Initialization sub-module {\_Init()}

Refer to FDD

#### Periodic sub-module {\_Per()}

Refer to FDD

#### Non Periodic sub-module {\_NONPer()}

None

### Interrupt Service Routines

None

### \_SCOMM () Functions

|                      |                             |         |       |      |
|----------------------|-----------------------------|---------|-------|------|
| **Function Name**    | HaitecTrqCmd_SCom_StartCtrl | Type    | Min   | Max  |
| **Arguments Passed** | Param_ManTrqCmd_MtrNm_f32   | Float32 | -8.8f | 8.8f |
|                      | Param_DefeatHwTrq_Cnt_lgc   | boolean | FALSE | TRUE |
|                      | Param_DefeatTemp_Cnt_lgc    | boolean | FALSE | TRUE |
| **Return Value**     | None                        |         |       |      |

|                      |                            |      |     |     |
|----------------------|----------------------------|------|-----|-----|
| **Function Name**    | HaitecTrqCmd_SCom_StopCtrl | Type | Min | Max |
| **Arguments Passed** | None                       |      |     |     |
| **Return Value**     | None                       |      |     |     |

### Module Internal (Local) Functions

None

### Transition Functions

None

# Known Limitations with Design

None

# UNIT TEST CONSIDERATION

None

####### Abbreviations and Acronyms

| **Abbreviation or Acronym** | **Description** |
|-----------------------------|-----------------|
|                             |                 |
|                             |                 |

####### Glossary

**Note**: Terms and definitions from the source “Nexteer Automotive”
take precedence over all other definitions of the same term. Terms and
definitions from the source “Nexteer Automotive” are formulated from
multiple sources, including the following:

-   ISO 9000

-   ISO/IEC 12207

-   ISO/IEC 15504

-   Automotive SPICE® Process Reference Model (PRM)

-   Automotive SPICE® Process Assessment Model (PAM)

-   ISO/IEC 15288

-   ISO 26262

-   IEEE Standards

-   SWEBOK

-   PMBOK

-   Existing Nexteer Automotive documentation

| **Term** | **Definition**         | **Source** |
|----------|------------------------|------------|
| MDD      | Module Design Document |            |
| DFD      | Data Flow Diagram      |            |

####### References

| **Ref. \#** | **Title**                                                                                                                                                             | **Version**       |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                    | v1.3.0 R4.0 Rev 2 |
| 2           | MDD Guideline                                                                                                                                                         | EA3 01.04.00      |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 1.0               |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.0               |
| 5           | FDD - CF015A_HaitecTrqCmd                                                                                                                                             | V_0.0.1           |

{% endraw %}