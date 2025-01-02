---
layout: default
title: GliwaT1_IntegrationManual
nav_order: 1
parent: GliwaT1
---
{% raw %}
**Module Design Document**

**For**

**GliwaT1**

**Note: Quick Start guide at end of document** **provides integration
overview.**

**Document Identifier: \<Project_id\>\_\<Config Id\>**

**VERSION: GliwaT1_01.00**

**DATE: May 19, 2014**

**Prepared By:**

**Core Software,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System and is uniquely identified by:
\<Project_ID\>\_\<Config Id\>

**Revision History**

|             |                                        |                 |             |               |
|------|---------------------------|-----------------|----------|-------------|
| **Sl. No.** | **Description**                        | **Author**      | **Version** | **Date**      |
| 1           | Initial Version                        | Blake Latchford | 1           | May 19, 2014  |
| 2           | Updates per review with Michale Story. | Blake Latchford | 2           | July 14, 2014 |

Table of Contents

[1 Abbrevations And Acronyms 4](#abbrevations-and-acronyms)

[2 References 5](#references)

[3 Dependencies 6](#dependencies)

[3.1 SWCs 6](#swcs)

[3.2 Global Functions(Non RTE) to be provided to Integration Project
6](#global-functionsnon-rte-to-be-provided-to-integration-project)

[4 Configuration 8](#configuration)

[4.1 Build Time Config 8](#build-time-config)

[4.2 Configuration Files to be provided by Integration Project
8](#config)

[4.3 Da Vinci Parameter Configuration Changes
8](#da-vinci-parameter-configuration-changes)

[4.4 DaVinci Interrupt Configuration Changes
8](#__RefHeading___Toc387219722)

[4.5 Manual Configuration Changes 8](#manual-configuration-changes)

[5 Integration 10](#integration)

[5.1 Required Global Data Inputs 10](#required-global-data-inputs)

[5.2 Required Global Data Outputs 10](#required-global-data-outputs)

[5.3 Specific Include Path present 10](#specific-include-path-present)

[6 Runnable Scheduling 12](#runnable-scheduling)

[7 Memory Mapping 14](#memory-mapping)

[7.1 Mapping 14](#mapping)

[7.2 Usage 14](#usage)

[7.3 Non RTE NvM Blocks 14](#non-rte-nvm-blocks)

[7.4 RTE NvM Blocks 14](#rte-nvm-blocks)

[8 Compiler Settings 15](#compiler-settings)

[8.1 Preprocessor MACRO 15](#preprocessor-macro)

[8.2 Optimization Settings 15](#optimization-settings)

[9 Appendix 16](#appendix)

# Abbrevations And Acronyms

|              |                           |
|--------------|---------------------------|
| Abbreviation | Description               |
| DFD          | Design functional diagram |
| MDD          | Module design Document    |

# References

This section Lists the title & version of all the documents that are
referred for development of this document

|         |                           |         |
|---------|---------------------------|---------|
| Sr. No. | Title                     | Version |
|         | \<Add if more available\> |         |

# Dependencies

## SWCs

|             |                                           |
|-------------|-------------------------------------------|
| **Module**  | **Required Feature**                      |
| **Metrics** | Must be removed from integration project. |

## Global Functions(Non RTE) to be provided to Integration Project

-   T1_TraceStartNoSusp – For use in motor control ISR.

-   T1_TraceStopNoSusp – For use in motor control ISR.

-   Metrics_TaskStart – Allows backwards compaitibilty with existing
    Metrics configuration. Also to be used when interrupt disabling is
    required.

-   Metrics_TaskStop – Same as Metrics_TaskStart, but for the end of the
    task.

# Configuration

## Build Time Config

|             |           |     |
|-------------|-----------|-----|
| **Modules** | **Notes** |     |
| **None**    |           |     |

## Configuration Files to be provided by Integration Project

Examples of the following configuration options can be found in the
GliwaT1\utp\Example_Tools_GliwaT1\config\\ folder. This folder contains
data intended to go in the project path Tools directory (not the
component).

## config

These files configure the Gliwa provided PERL scripts that generate
various files when integration is performed. Some of the values more
likely to change between projects are called out below.

-   T1_Cfg.inv

    -   txCycle – Time in ms between calls to T1_AppHandler.

    -   t1ScopeOverheadNs – Overhead to be filled in as called out in
        Overhead_Calculation.xlsx (Can be found in component tools
        directory) .

    -   t1FlexOverheadNs – Overhead to be filled in as called out in
        Overhead_Calculation.xlsx.

-   T1_OsCfg.inv

    -   Shouldn’t change per project.

-   T1_UserCfg.inv

    -   projectName – Name of the program (C1xx, LWR, UKL, etc.)

    -   traceBufferEntries – Size of the trace buffer. This number
        determines how much RAM is required to store trace events. A
        minimum for this number on a typical system would be in the
        range of 300-400 entries. If more space is added to this buffer
        then each trace download will be able to show a larger picture.
        If this buffer is made too small then data will be lost,
        resulting in errors and incomplete data collection.

## Da Vinci Parameter Configuration Changes

|               |           |         |
|---------------|-----------|---------|
| **Parameter** | **Notes** | **SWC** |
| **None**      |           |         |

## DaVinci Interrupt Configuration Changes

|                   |            |                         |                                                                                                                                                          |
|------------|--------|--------------------------|---------------------------|
| **ISR Name**      | **VIM \#** | **Priority Dependency** | **Notes**                                                                                                                                                |
| **Isr_MtrCtrl**   |            | None                    | Add T1_TraceStartNoSusp(T1_Isr_MtrCtrl_ID) and T1_TraceStopNoSusp(T1_Isr_MtrCtrl_ID) calls to the beginning and end of the ISR.                          |
| **Any other ISR** |            | None                    | Add Metrics_TaskStart(\<ID\>) and Metrics_TaskEnd(\<ID\>) to the beginning and end of each ISR. ID will be a symbol generated from the .ecuc.arxml file. |

## Manual Configuration Changes

|                                                 |           |         |
|-------------------------------------------------|-----------|---------|
| **Constant**                                    | **Notes** | **SWC** |
| **Messages need to be added to the .dbc file.** |           |         |
| **GENy must be updated.**                       |           |         |

Gliwa communicates on CAN via a custom protocol on the CAN bus. It uses
IDs that must be distinct from other IDs already in use. By default
these are 0x7FA and 0x7CB. They can be reconfigured if a program intends
to use these identifiers for a different purpose.

# Target to Host

The 0x7FA message is used to transmit data from the target (ECU) to the
host (PC). In the example provided this is done by use of the
CanMsgTransmit() API. If the program supports this API it will likely
need to be turned on via the Low Level Transmission.

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/GliwaT1/doc/mediax/media/image1.png"
style="width:6.50764in;height:5.43819in" />

If this API is unavailable, adding a spontaneous message to the database
may be used as an alternative. Once that is completed the standard
spontaneous message transmission methods for a SIP can be used. An
example of this spontaneous messages is shown below.

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/GliwaT1/doc/mediax/media/image2.png"
style="width:3.87639in;height:3.09375in" />

# Host To Target

The 0x7CB message is used by default to transmit data from the host (PC)
to the target (ECU). This message must be added to the database file to
ensure that the hardware doesn’t filter out the message. AN example of
the message configuration for this message is shown below.

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/GliwaT1/doc/mediax/media/image3.png"
style="width:3.92222in;height:3.09861in" />

# Integration

## Required Global Data Inputs

\<Mention any global variable that this component requires for other
components\>

## Required Global Data Outputs

\<Mention any global variable that this component requires for other
components\>

## Specific Include Path present

Yes

# Runnable Scheduling 

This section specifies the required runnable scheduling.

|                |                                                                     |             |
|-------------------|---------------------------------------|---------------|
| **Init**       | **Scheduling Requirements**                                         | **Trigger** |
| **T1_AppInit** | As early as possible. Recommend the beginning of the main function. | Init        |

|                     |                                                      |                     |
|-------------------|---------------------------------------|---------------|
| **Runnable**        | **Scheduling Requirements**                          | **Trigger**         |
| **T1_AppHandler**   | 10ms (alternatively, the time called out by txCycle) | Manually scheduled. |
| **T1_AppBgHandler** | Background                                           | Background task.    |

# Memory Mapping

Memory mapping for this component is performed directly through the
linker command file. The following sections must be defined.

-   .T1_bss

    -   This section should be placed somewhere in RAM. No assumptions
        are made about the initialization of this memory. This memory is
        only accessed from a trusted application.

-   .T1_traceBuffer

    -   This is similar to .T1_bss, but is sepearated for flexibility of
        placement due to its large size. It contains the ring buffer for
        logged trace events.

-   .T1_code

    -   Should be placed similarly to the existing .text section.
        Application flash is the recommended location.

-   .T1_const

    -   Expects to be initialized. Application flash is the recommended
        location.

-   .T1_codeFast

    -   Code that needs to execute quickly. It has been shown that
        execution from RAM has minimal impact, though for consistent
        overhead measurements the following sections should be aligned
        to a 16 byte flash boundary.

    -   .T1_codeFast:T1_TraceEventNoSusp\_

    -   .T1_codeFast:T1_GetTraceTime

    -   .T1_codeFast:T1_TraceEventFast\_

## Mapping

|                    |              |           |
|--------------------|--------------|-----------|
| **Memory Section** | **Contents** | **Notes** |
| **None**           |              |           |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

|             |         |         |
|-------------|---------|---------|
| **Feature** | **RAM** | **ROM** |
|             |         |         |

Table 1: ARM Cortex R4 Memory Usage

## Non RTE NvM Blocks

|                |
|----------------|
| **Block Name** |
| **None**       |

## RTE NvM Blocks

|                |
|----------------|
| **Block Name** |
| **None**       |

# Compiler Settings

##  Preprocessor MACRO

T1_ENABLE will be defined after the integration script is run. If this
does not occur then something went wrong in the overlay of
T1_AppInterface.h. This can be debugged by viewing the text output of
the PerformOverlay.bat file.

## Optimization Settings

N/A

## 

# Appendix

## Gliwa Repository

For updates to the Gliwa T1 library or any additional files Gliwa has
provided an Xfer server for access by Nexteer employees.

<https://gliwa.com/xfer>

Username: nexteer

Password: la7Feje7

## Files to be provided by the integration project

Examples of these files can be found in the folder
GliwaT1/utp/Example_Integration_Specific

## T1_Appinterface_Cfg.c

This file provides an interface for the reception and transmission of
messages on the CAN bus in order to communicate with the host PC. Since
messages are handled differently depending on the Vector SIP provided, a
wrapper must exist for this functionality.

On reception of a message from the host PC, the target ECU must call the
T1_RxCallback function. The buffer passed to this function is processed
in the T1_AppHandler call. Therefore the buffer most remain valid
constantly. A temporary buffer declared at the beginning of the fuction
is not sufficient. Furthermore the function must swtich to privldiged
mode to permit acces to T1 RAM.

T1_Trasmit is called by T1_AppHandler when T1 needs to transmit a
message. The application is responsible for ensuring that this data is
put on the bus in the correct order, and before the next call to
T1_AppHandler. Any switch to supervisor mode would be redundant as it is
already performed in the handler.

## T1_Appinterface_Cfg.h

This file contains several constants for backwards compatilbity.
D_I2CNXT_CNT_U08, D_SPINXT1_CNT_U08, and D_SPINXT2_CNT_U08 must be
included if either the SpiNxt or I2cNxt components are included. They
should be redefined to use the T1 generated constants rather than using
a literal. For example if the I2C component is included the following
can be used to alias the Identifier.

\#define D_I2CNXT_CNT_U08 T1_Isr_I2c_ID

The PollT1HostToTarget function like macro should be defined if the
application uses polling to handle messages. If any headers are required
to poll for the message they should be included in
T1_Appinterface_Cfg.h.

D_GLIWAT1_SWITCHTOPRIVMODE_CNT_LGC should be set to STD_ON if the target
application uses MPU regions. This puts all memory accesses by T1 into
privlidged mode, so its memory can be allocated anywhere.

D_GLIWAT1_SLOWWAITSTATES_CNT_LGC should be set to STD_ON if the standard
wait states of 3dws and 1aws are used. If seto STD_OFF it is assumed
that there are 2dws and 0aws. If this is set incorrectly there will be
an increase in measurement overhead.

## Executable Scripts

Two batch files are provided in the UTP/Example_Tools_GliwaT1 folder.
Perform integration copies the overlay onto the file system, and
perfroms the necessary generation steps. The remove integration batch
file removes the overlay from the working directory. They are both
intended to run from the projects Tools/GliwaT1 folder.

These scripts expect that Perl has been installed locally, and the
AsrToOil utility has been installed in the Tools folder of the
integration project. Active Perl has been used in the past, but any
windows implementation of Perl should work. No modules other than those
provided by Gliwa are required to run these scripts.

## Overlay

The point of the overlay is to change files that cannot be modified for
an official build. Examples of this include the OS, and vector provided
ISRs. The overlay should contain a duplicate of the files contained
which are intended to be changed. Since the many of the most important
files to be replaced are provided by the Vector SIP, different SIPs will
have to tailor their overlay folder to their project.

For ISRs that execute in an non-trusted application it is recommended
that the Metrics_TaskStart and Metrics_TaskEnd interface is used. This
interface ensures that the events are logged in a privlidged mode. The
ID provided should be the ID generated by the Gliwa Perl scripts.

## Basic Test Guidelines

## Minimum Conditions for a Valid Test

-   Merged with calibrations traceable to eCalNet

    -   Any modifications should be noted in the report comments.

-   Every serial communications message that EPS receives being
    transmitted on all busses.

-   Controller enters operate state without any defeats enabled.

-   Turn on all conditionally enabled functionality.

    -   Examples include Lane Keeping Assist on GM C1xx, and Black Box
        functionality on Ford S550.

## Gliwa T1 configuration

-   Overheads should be re-calculated using Overhead_Calculation.xlsx
    which is located in the component’s tools directory.

-   All ISRs must be instrumented, with the exception of any that do not
    return.

## Required Measurements

-   Overall average CPU usage

    -   Appears on report as average CPU use from T1.cont

-   Task core execution time

-   Task chain time

    -   Time from the activation of the first task executed at a
        periodic rate, to completion of the last task in that periodic
        rate.

## Additional Measurements

-   Motor Control ISR function execution times.

-   Task chain thresholds

    -   Add T1_Delay calls to the end of each task, and increase the
        delay until a failure occurs.

## Quick Start Guide

1.  Remove any existing traces of the old Metrics Component. This
    includes the component, and any configuration files (likely within
    the GenData directory).

2.  Add GliwaT1 component to Synergy

3.  Copy the contents of the Gliwa component’s utp/Example_Tools_GliwaT1
    directory to the project’s Tools directory in a new GliwaT1 folder.

4.  Modify the Overlay directory to conform to the expected layout of
    the project.

    1.  The GM_C1XX_EPS_TMS570 folder at the highest level in the
        Overlay directory will have to be renamed to the name of the
        project.

    2.  All interrupts must be instrumented. See section 4.4. If the OS
        has changed since integration int C1xx, the OS files will have
        to be updated appropriately. If significant changes to the OS
        have occurred then Gliwa support may be required.

5.  Add the two messages to allow the host (PC) software to communicate
    with the target (ECU).

    1.  See section 4.5.

{% endraw %}