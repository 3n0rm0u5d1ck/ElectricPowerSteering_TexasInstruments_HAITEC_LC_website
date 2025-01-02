---
layout: default
title: Dma_MDD
nav_order: 4
parent: Dma
---
{% raw %}
**Module Design Document**

**For**

**DMA**

**Document Identifier: \<Project_id\>\_\<Config Id\>**

**VERSION:** **4**

**DATE:** **31-Jan-2015**

**  
Location:** The official version of this document is stored in the
Nexteer Configuration Management System and is uniquely identified by:
\<Project_ID\>\_\<Config Id\>

**Revision History**

|             |                       |                  |             |             |
|-----|------------------------------|-----------------|---------|------------|
| **Sl. No.** | **Description**       | **Author**       | **Version** | **Date**    |
| 1           | Initial version       | Owen Tosh        | 1           | 04-Apr-2014 |
| 2           | Updated to FDD52 v001 | Owen Tosh        | 2           | 29-Apr-2014 |
| 3           | Updated to FDD52 v002 | Owen Tosh        | 3           | 02-May-2014 |
| 4           | Updated to ES-52 v004 | Kathleen Creager | 4           | 31-Jan-2015 |

**<u>  
Table of Contents</u>**

[1 Abbrevations And Acronyms
[5](#abbrevations-and-acronyms)](#abbrevations-and-acronyms)

[2 References [6](#references)](#references)

[3 DMA & High-Level Description
[7](#dma-high-level-description)](#dma-high-level-description)

[4 Design details of software module
[8](#design-details-of-software-module)](#design-details-of-software-module)

[4.1 Graphical representation of DMA
[8](#graphical-representation-of-dma)](#graphical-representation-of-dma)

[5 Variable Data Dictionary
[9](#variable-data-dictionary)](#variable-data-dictionary)

[5.1 User defined typedef definition/declaration
[9](#user-defined-typedef-definitiondeclaration)](#user-defined-typedef-definitiondeclaration)

[5.2 Variable definition for enumerated types
[9](#_Toc338170478)](#_Toc338170478)

[6 Constant Data Dictionary
[10](#constant-data-dictionary)](#constant-data-dictionary)

[6.1 Program(fixed) Constants
[10](#programfixed-constants)](#programfixed-constants)

[6.1.1 Embedded Constants
[10](#embedded-constants)](#embedded-constants)

[6.1.1.1 Local [10](#local)](#local)

[6.1.1.2 Global [10](#global)](#global)

[6.1.2 Module specific Lookup Tables Constants
[10](#module-specific-lookup-tables-constants)](#module-specific-lookup-tables-constants)

[6.1.3 Library Functions / Macros
[10](#library-functions-macros)](#library-functions-macros)

[6.1.4 Data Hiding Functions
[11](#data-hiding-functions)](#data-hiding-functions)

[7 Software Module Implementation
[12](#software-module-implementation)](#software-module-implementation)

[7.1 Initialization Functions
[12](#initialization-functions)](#initialization-functions)

[7.1.1 Init: Dma \_Init [12](#init-dma_init)](#init-dma_init)

[7.1.1.1 Design Rationale [12](#design-rationale)](#design-rationale)

[7.1.1.1.1 MPU Settings [12](#mpu-settings)](#mpu-settings)

[7.1.1.1.2 Priority Assignments
[12](#priority-assignments)](#priority-assignments)

[7.1.1.1.3 FlsTst Group (Channels 0 and 1)
[12](#_Toc384116599)](#_Toc384116599)

[7.1.1.2 Initialize DMA Registers
[12](#initialize-dma-registers)](#initialize-dma-registers)

[7.1.1.3 Module Outputs [12](#module-outputs)](#module-outputs)

[7.1.1.4 Module Internal [13](#module-internal)](#module-internal)

[7.2 PERIODIC FUNCTIONS [13](#periodic-functions)](#periodic-functions)

[7.2.1 Per: Dma \_Per1 [13](#_Toc384116604)](#_Toc384116604)

[7.2.1.1 Design Rationale [13](#_Toc384116605)](#_Toc384116605)

[7.2.1.2 Store Module Inputs to Local copies
[13](#_Toc384116606)](#_Toc384116606)

[7.2.1.3 Clear DMA RAM Buffers [13](#_Toc384116607)](#_Toc384116607)

[7.2.1.4 Store Local copy of outputs into Module Outputs
[13](#_Toc384116608)](#_Toc384116608)

[7.3 Interrupt Functions
[13](#interrupt-functions)](#interrupt-functions)

[7.4 TRANSIENT FUNCTIONS
[13](#transient-functions)](#transient-functions)

[7.5 Serial Communication Functions
[13](#serial-communication-functions)](#serial-communication-functions)

[7.6 Local Function/Macro Definitions
[13](#local-functionmacro-definitions)](#local-functionmacro-definitions)

[7.7 GLObAL Function/Macro Definitions
[13](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[7.7.1 Setup MtrCtrl Groups
[13](#setup-mtrctrl-groups)](#setup-mtrctrl-groups)

[7.7.1.1 Description [13](#description-2)](#description-2)

[7.7.2 Setup FlsTst Blocks
[14](#setup-flstst-blocks)](#setup-flstst-blocks)

[7.7.2.1 Description [14](#description-3)](#description-3)

[7.7.3 Enable FlsTst Block
[14](#enable-flstst-block)](#enable-flstst-block)

[7.7.3.1 Description [14](#description-4)](#description-4)

[7.7.4 Disable FlsTst Block
[14](#disable-flstst-block)](#disable-flstst-block)

[7.7.4.1 Description [14](#description-5)](#description-5)

[7.7.5 Report DMA MPU Error [14](#_Toc384116622)](#_Toc384116622)

[7.7.5.1 Description [14](#_Toc384116623)](#_Toc384116623)

[8 Known Limitations With Design
[15](#known-limitations-with-design)](#known-limitations-with-design)

[9 UNIT TEST CONSIDERATION
[16](#unit-test-consideration)](#unit-test-consideration)

[10 Appendix A – Configuration Schemes
[17](#appendix-a-configuration-schemes)](#appendix-a-configuration-schemes)

# Abbrevations And Acronyms

| Abbreviation | Description                                                                                               |
|---------------------|---------------------------------------------------|
| MDD          | Module design Document                                                                                    |
| MtrCtrl ISR  | Motor Control Interrupt Service Routine. This is the “fast” code loop that controls the main PWM signals. |

# References

This section Lists the title & version of all the documents that are
referred for development of this document

| Sr. No. | Title                       | Version |
|---------|-----------------------------|---------|
| 1       | MDD Guidelines              | 1       |
| 2       | Software Naming Conventions | 1       |
| 3       | Coding Standands            | 1       |
| 4       | ES 52 – DMA                 | 004     |

# DMA & High-Level Description

DMA is a driver level module that performs flash, RAM, and peripheral
reads and writes in the background, freeing up the CPU to do other work
in parallel. It is equipped with parity checking and an MPU, but timing
and data consistency must be considered with respect to CPU execution.

# Design details of software module

## Graphical representation of DMA

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/Dma/doc/mediax/media/image1.emf)

# Variable Data Dictionary

## User defined typedef definition/declaration 

<table>
<colgroup>
<col style="width: 16%" />
<col style="width: 48%" />
<col style="width: 11%" />
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
<td rowspan="7">DMADataType_Str *</td>
<td>DummyVarForAlignment_Uls_f64**</td>
<td>float64</td>
<td>FULL</td>
<td>FULL</td>
</tr>
<tr class="even">
<td>FastSPI_Cnt_u16[D_NUMFASTSPIWORDS_CNT_U16]</td>
<td>uint16</td>
<td>0</td>
<td>2<sup>16</sup> - 1</td>
</tr>
<tr class="odd">
<td>SlowSPI_Cnt_u16[D_NUMSLOWSPIWORDS_CNT_U16]</td>
<td>uint16</td>
<td>0</td>
<td>2<sup>16</sup> - 1</td>
</tr>
<tr class="even">
<td>SlowADC_Cnt_u16[D_NUMFASTADCCHANNELS_CNT_U16]</td>
<td>uint16</td>
<td>0</td>
<td>2<sup>16</sup> - 1</td>
</tr>
<tr class="odd">
<td>FastADC_Cnt_u16[D_NUMSLOWADCCHANNELS_CNT_U16]</td>
<td>uint16</td>
<td>0</td>
<td>2<sup>16</sup> - 1</td>
</tr>
<tr class="even">
<td>PWMCmp_Cnt_u16[4][2]</td>
<td>uint16</td>
<td>0</td>
<td>2<sup>16</sup> - 1</td>
</tr>
<tr class="odd">
<td>PWMPeriod_Cnt_u32</td>
<td>uint32</td>
<td>0</td>
<td>2<sup>32</sup> - 1</td>
</tr>
</tbody>
</table>

<span id="_Toc338170478" class="anchor"></span>\* Note that the elements
of this structure are dependent on whether the respective peripherals
are configured to use DMA. In the case that none of the ADC, SPI, or PWM
groups are enabled in DMA, the type will not be defined.

\*\* Note that the boundaries of this struct type must be 64-bit aligned
due to TMS570 DMA MPU operation, which in some cases allows access
outside of configured MPU region boundaries up to a 64-bit boundary if
the region boundaries are not 64-bit aligned. A float64 is used to force
the alignment; per section 6.2.1.6 of SPNU151G–August 2011 (ARM
Optimizing C/C++ Compiler v 4.9 User’s Guide) “Structures are aligned
according to the member with the most restrictive alignment requirement.
Structures are padded so that the size of the structure is a multiple of
its alignment.”

## Variable definition for enumerated types

| Enum Name | Element Name | Value |
|-----------|--------------|-------|
| None      |              |       |

# Constant Data Dictionary

## Program(fixed) Constants

## Embedded Constants

## Local

| Constant Name                  | Resolution | Units | Value                                                                          |
|-------------------------|---------|---------|------------------------------|
| D_DMAFLSTSTENABLED_CNT_ENUM    | enum       | Count | configurable                                                                   |
| D_FASTSPIGROUPENABLED_CNT_ENUM | enum       | Count | configurable                                                                   |
| D_FASTADCGROUPENABLED_CNT_ENUM | enum       | Count | configurable                                                                   |
| D_FASTPWMGROUPENABLED_CNT_ENUM | enum       | Count | configurable                                                                   |
| D_SLOWADCGROUPENABLED_CNT_ENUM | enum       | Count | configurable                                                                   |
| D_CRCCTRLREGSTART_CNT_U32      | 1          | Count | &(CRCCTRLREG-\>CRC_REGL1)                                                      |
| D_CRCPSASIGREGSTART_CNT_U32    | 1          | Count | &(CRCCTRLREG-\>PSA_SIGREGL1)                                                   |
| D_NUMFASTSPIWORDS_CNT_U16      | 1          | Count | D_TGSIZE_CNT_U16                                                               |
| D_FASTSPISTARTADDR_CNT_U32     | 1          | Count | &(mibspiRAM3-\>rx\[0\].data)                                                   |
| D_NUMFASTADCCHANNELS_CNT_U16   | 1          | Count | D_ADC2G1BUFSZ_CNT_U08                                                          |
| D_FASTADCSTARTADDR_CNT_U32     | 1          | Count | (D_ADC2RSLTBASEADR_CNT_U32 + (4u \* D_ADC2EVTBUFSZ_CNT_U08) + 2u)              |
| D_DMANHETPERIODADDR_CNT_U32    | 1          | Count | &(HET_PRD_BUF1_0.memory.data_word)                                             |
| D_EPWMSTARTADDR_CNT_U32        | 1          | Count | &(ePWM1-\>CMPA)                                                                |
| D_NUMSLOWADCCHANNELS_CNT_U16   | 1          | Count | D_ADC1G2BUFSZ_CNT_U08                                                          |
| D_SLOWADCSTARTADDR_CNT_U32     | 1          | Count | (0xFF3E0000ul + (4u \* (D_ADC1EVTBUFSZ_CNT_U08 + D_ADC1G1BUFSZ_CNT_U08)) + 2u) |
| D_NUMSLOWSPIWORDS_CNT_U16      | 1          | Count | D_TGSIZE_CNT_U16                                                               |
| D_SLOWSPISTARTADDR_CNT_U32     | 1          | Count | &(mibspiRAM5-\>rx\[0\].data)                                                   |

## Global

| Constant Name             |
|---------------------------|
| STD_OFF                   |
| STD_ON                    |
| CRCCTRLREG                |
| D_TGSIZE_CNT_U16          |
| mibspiRAM3                |
| D_ADC2G1BUFSZ_CNT_U08     |
| D_ADC2RSLTBASEADR_CNT_U32 |
| D_ADC2EVTBUFSZ_CNT_U08    |
| HET_PRD_BUF1_0            |
| ePWM1                     |
| D_ADC1G2BUFSZ_CNT_U08     |
| D_ADC1EVTBUFSZ_CNT_U08    |
| D_ADC1G1BUFSZ_CNT_U08     |
| mibspiRAM5                |
| DMA_PARITY_ENABLE         |

## Module specific Lookup Tables Constants

| Constant Name | Resolution | Value | Software Segment |
|---------------|------------|-------|------------------|
| None          |            |       |                  |

## Library Functions / Macros 

The library and functions / Macros that are called by the various sub
modules shall be identified in this section

None

## Data Hiding Functions

The Data hiding functions that’s uses RTE interface or other macro
interfaces shall be listed in this section.

DMA_REPORTERRORSTATUS(event, param, status)

# Software Module Implementation

## Initialization Functions

## Init: Dma_Init

## Design Rationale

The DMA module must encapsulate many possible configurations. These
configurations can be enabled or disabled per the configuration header
file. All programs use DMA for the Flash CRC Test (part of the TMS570 uC
diagnostics); some programs configure additional uses.

The DMA peripheral is reset by a system reset and can also be reset by a
control register bit. The latest version of TMS_570 Startup includes a
test of DMA MPU functionality; at the conclusion of this test it sets
the DMA peripheral reset bit. Per discussion with TI and draft updates
to TI documentation, the reset bit should be checked to ensure the
peripheral is out of reset before configuring registers.

This init function checks the reset bit; whether the peripheral was last
reset by a system reset (when used with older versions of TMS_570
Startup) or by the reset at the end of the startup test, the peripheral
is expected to be out of reset by the time this init function executes.
If the reset bit indicates the peripheral is not out of reset, a global
variable flag is used to indicate a DMA reset failure. This flag is used
in the TMS570_uDiag component which controls the Peripheral Startup
Fault NTC (0x037).

DMA is enabled at the end of the function. Once this is done, DMA will
remain active for the remainder of the ignition cycle. Individual
channels can be enabled or disabled as needed, however.

## MPU Settings

The nature of the DMA MPU is different from that of the CPU. The DMA has
four configurable memory regions; anything outside of the declared
regions is considered full access. The regions may overlap, however, and
are treated by “priority” – that is, for addresses included in multiple
regions, the settings in the lowest-numbered region are used. In light
of this, the final memory region is used to cover the majority of the
memory map. The other three regions are configured to allow access to
specific regions. The following table shows the memory region
allocations:

| **Region** | **Access** | **Purpose**          | **Start Address** | **End Address**                            |
|---------|------------|---------------|-----------------|---------------------|
| 0          | Read/Write | SPI, ADC, NHET       | 0xFF0A0000        | 0xFF473FFF                                 |
| 1          | Read/Write | ePWM, CRC            | 0xFCF78C00        | 0xFE0001FF                                 |
| 2          | Read/Write | RAM                  | &DMAData_G_str    | &DMAData_G_str + sizeof(DMAData_G_str) - 1 |
| 3          | No Access  | Everything but Flash | 0x00200000        | 0xFFFFFFFF                                 |

This configuration is based on safety analysis (included in FDD 52) and
the DMA MPU limitations.

Per discussion with TI and draft TI documentation updates, in some cases
(depending on element size being transferred), the DMA MPU may allow
access beyond the end of a DMA MPU region to the next 64-bit boundary if
the region boundary is not 64-bit aligned (start address is 64-bit
aligned, end address is the last byte of a 64-bit aligned space, i.e.
end address is a 64-bit aligned address minus one). For this reason, a
dummy 64-bit variable is included at the beginning of the
DMADataType_Str type.

When DMA is used for Flash CRC Test only, the DMA MPU settings are more
restrictive, providing only the access needed by the Flash CRC test:

| **Region** | **Access**         | **Purpose**                  | **Start Address**                    | **End Address**                                  |
|--------|------------|--------------|-------------------|--------------------|
| 0          | Write only         | CRC                          | Address of first CRC register needed | Address of last byte of last CRC register needed |
| 1          | No access          | Peripheral RAM and registers | 0xF0800000UL                         | 0xFFFFFFFFUL                                     |
| 2          | Read only          | Entire address space         | 0x00000000UL                         | 0xFFFFFFFFUL                                     |
| 3          | Region not enabled | N/A                          | N/A                                  | N/A                                              |

## Priority Assignments

Channels 0 and 1 are assigned low priority, while the other channels are
assigned as high priority. As channels 0 and 1 are used for FlsTst
functionality, they are designed to be run “in the background”, while
the other channels need high priority to ensure the MtrCtrl ISR is run
on schedule. Any unused channel is left at a default of low priority.

## Initialize DMA Registers

\<flow chart\>

## Module Outputs

None

## Module Internal 

None

##  PERIODIC FUNCTIONS 

None

## Interrupt Functions

None

## TRANSIENT FUNCTIONS

None

## Serial Communication Functions

None

## Local Function/Macro Definitions

None

## GLObAL Function/Macro Definitions

## Check Validity of Slow ADC Group

|                      |                          |         |       |      |
|----------------------|--------------------------|---------|-------|------|
| **Function Name**    | Dma_SlowADCGroupValidity | Type    | Min   | Max  |
| **Arguments Passed** | None                     |         |       |      |
| **Return Value**     | RetValue_Cnt_T_lgc       | boolean | FALSE | TRUE |

## Design Rationale

This function is provided as one part of the data integrity scheme. The
FDD requires that the DMA buffer be checked before the data is read, and
cleared after the data is read. This function is designed to be called
before the ADC data is read, and returns FALSE if the data is invalid.
The FDD specifies that the data be copied if it is valid; for throughput
and memory reasons, this is left as the responsibility of the caller.

## Description

\<flow chart\>

## Invalidate Slow ADC Group Buffers

|                      |                            |      |     |     |
|----------------------|----------------------------|------|-----|-----|
| **Function Name**    | Dma_InvalidateSlowADCGroup | Type | Min | Max |
| **Arguments Passed** | None                       |      |     |     |
| **Return Value**     | N/A                        |      |     |     |

## Design Rationale

To ensure that the DMA is running, this function is provided to be run
after the DMA data is collected by the 2ms IoHwAbstraction component.
The buffers are cleared to 0xFFFF with the expectation that the DMA will
fill them with proper data before the data is collected again. If the
DMA fails to do so, the cleared buffers will trigger the internal DMA
diagnostic (implemented in Dma_SlowADCGroupValidity).

This is intended to be used as part of a larger data consistency scheme.
See Appendix A for more information on how this is designed to be used.

## Description

\<flow chart\>

## Setup MtrCtrl Groups

|                      |                        |      |     |     |
|----------------------|------------------------|------|-----|-----|
| **Function Name**    | Dma_SetupMtrCtrlGroups | Type | Min | Max |
| **Arguments Passed** | None                   |      |     |     |
| **Return Value**     | N/A                    |      |     |     |

## Description

\<flow chart\>

## Setup FlsTst Blocks

|                      |                           |        |     |           |
|----------------------|---------------------------|--------|-----|-----------|
| **Function Name**    | Dma_SetupFlsTstBlock      | Type   | Min | Max       |
| **Arguments Passed** | CRCAddr_Cnt_T_u32         | uint32 | 0   | 2^32^ - 1 |
|                      | FlsAddr_Cnt_T_u32         | uint32 | 0   | 2^32^ - 1 |
|                      | DmaFrameCount_Cnt_T_u16   | uint16 | 0   | 2^16^ - 1 |
|                      | DmaElementCount_Cnt_T_u16 | uint16 | 0   | 2^16^ - 1 |
| **Return Value**     | N/A                       |        |     |           |

## Description

\<flow chart\>

## Enable FlsTst Block

|                      |                       |      |     |     |
|----------------------|-----------------------|------|-----|-----|
| **Function Name**    | Dma_EnableFlsTstBlock | Type | Min | Max |
| **Arguments Passed** | None                  |      |     |     |
| **Return Value**     | N/A                   |      |     |     |

## Description

\<flow chart\>

## Disable FlsTst Block

|                      |                        |      |     |     |
|----------------------|------------------------|------|-----|-----|
| **Function Name**    | Dma_DisableFlsTstBlock | Type | Min | Max |
| **Arguments Passed** | None                   |      |     |     |
| **Return Value**     | N/A                    |      |     |     |

## Description

\<flow chart\>

# Known Limitations With Design

1.  This design only considers DMA transfers for a specific sensor
    configuration. Older or newer programs may have other DMA needs that
    are not considered, and the design will need to be updated to
    accommodate those sensor configurations in time.

2.  This design has only been verified on Champion hardware. It would
    need to be validated on Gladiator hardware before use.

# UNIT TEST CONSIDERATION

None

# Appendix A – Configuration Schemes

The DMA module is intended to be configurable for any number of use
cases. While each channel is specifically assigned, each channel can be
enabled or disabled per program.

The following diagram shows the MtrCtrl ISR groups and where they are
designed to run. The trigger points for each group, as well as
non-configurable data formats and lengths, are based on this data and
the corresponding peripherals.

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/Dma/doc/mediax/media/image2.emf)

{% endraw %}