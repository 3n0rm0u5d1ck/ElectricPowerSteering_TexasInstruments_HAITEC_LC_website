---
layout: default
title: Spi_Nexteer_MDD
nav_order: 2
parent: SpiNxt
---
{% raw %}
# Module -- Spi Driver [module----spi-driver]

# High-Level Description

This module provides the following Autosar API:

1.  Spi_SetupEB()

2.  Spi_Init()

3.  Spi_AsyncTransmit()

4.  Spi_GetSequenceResult()

This module provides the following TI Halcogen API:

1.  mibspiSetCtrlData() – *Note: this is a modified form of the standard
    mibspiSetData() API*

2.  mibspiTransfer()

3.  mibspiGetData()

4.  mibspiSetData()

The Autosar API naming has been altered from the Autosar standard to
allow co-existence of this module and a Third Party Spi driver
implementation in the same project. SWC’s operating within the Rte can
be mapped to either the Spi service ports offered by this BSW or the
Third Parties Spi driver service ports by only changing the Rte service
port mapping.

This driver exists to provide configurations/use cases that cannot
provided by the third party Spi driver due to limitations in the design
of the module.

The subset of the Texas Instruments Halcogen mibspi API is provided
specifically to support the Turns Counter Flash Programming SWC and the
Digital MSB SWC. If the Turns Counter Flash Programming SWC design and
the Digital MSB design changed to use the standard Autosar API, then the
provided mibspi API could be changed to module internal functions or
removed. However, the requirements of the Digital MSB component are such
that its SPI usage does not fit easily into the Autosar API definition
(more detail provided in section 9).

## References

1.  PIC16(L)F1847 Data Sheet – DS41453B (41453B.pdf)

2.  Turns Counter Column Position Sensor FDD 20C ([FDD 20C Turns Counter
    Column Position Sensor (BMW EA3) Rev
    03.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_138945/FDD%2020C%20Turns%20Counter%20Column%20Position%20Sensor%20(BMW-EA3)%20Rev%20003.doc))

3.  TMS570LS31x/21x 16/32-Bit RISC Flash Microcontroller Technical
    Reference Manual – September 2011 (spnu499.pdf)

4.  Specification of the SPI Handler/Driver v3.0.0
    (AUTOSAR_SWS_SPIHandlerDriver.pdf)

5.  Turns Counter Flash Programming FDD 98 Rev 002

6.  Digital MSB FDD ES50ARev005 7-Feb-14

7.  Allegro A1331 Data Sheet Addendum – Programming Reference A1331-ADD1

# Figures

## Diagram – Function Data Sharing

This diagram shows all data that is shared between functions within the
module.

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SpiNxt/doc/mediax/media/image1.emf)

### Diagram – Function (Name)

This diagram describes the functional characteristics and data flow of a
given function.

(Note – This is not mandatory, only used where a graphical
representation helps explain the function. It is left to the author’s
discretion. New headers of this level (Level 3) should be created for
each function.

#  Variable Data Dictionary

For details on module input / output variable, refer to the Data
Dictionary for the application. Input / output variable names are listed
here for reference.

(Note: Full variable names required in table.)

(Note: All global variables including End Of Line data used should be
shown here)

| Module Inputs | Module Outputs |      |
|---------------|----------------|------|
| None          |                | None |

## Module Internal Variables

This section identifies the name, range and resolutions for module
specific data created by this module. If there are no range restrictions
on the variable, the term “FULL” is placed into the table for legal
range.

<table>
<colgroup>
<col style="width: 30%" />
<col style="width: 17%" />
<col style="width: 14%" />
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
<td><p>ExtBufCfg_Str</p>
<p>[D_SPINXTNUMCHAN_CNT_U16]</p></td>
<td>See structure definition</td>
<td>See structure definition</td>
<td>See structure definition</td>
<td>SPINXT_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
<tr class="even">
<td><p>SeqResult_Enum</p>
<p>[D_SPINXTNUMSEQ_CNT_U16]</p></td>
<td>Enum</td>
<td>SPI_SEQ_OK (= 0)</td>
<td>SPI_SEQ_CANCELLED (=4)</td>
<td>SPINXT_START_SEC_VAR_CLEARED_UNSPECIFIED</td>
</tr>
</tbody>
</table>

### User defined typedef definition/declaration 

This section documents any user types uniquely used for the module.

<table>
<colgroup>
<col style="width: 29%" />
<col style="width: 22%" />
<col style="width: 26%" />
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
<td>EbCfg_Type</td>
<td>SrcDataBufferPtr</td>
<td>Spi_DataType</td>
<td>N/A</td>
<td>N/A</td>
</tr>
<tr class="even">
<td></td>
<td>DesDataBufferPtr</td>
<td>Spi_DataType</td>
<td>N/A</td>
<td>N/A</td>
</tr>
<tr class="odd">
<td></td>
<td>Length</td>
<td>Spi_NumberOfDataType</td>
<td>N/A</td>
<td>N/A</td>
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

| Constant Name            | Resolution | Units    | Value when D_SPINXTUSEWITH_CNT_ENUM == D_SPINXTUSEWITHTC | Value when D_SPINXTUSEWITH_CNT_ENUM == D_SPINXTUSEWITHDIGMSB    |
|--------------------|-------|--------|-------------------|--------------------|
| D_SPINXTUSEWITHTC        | Count      | Unitless | 0                                                        | 0                                                               |
| D_SPINXTUSEWITHDIGMSB    | Count      | Unitless | 1                                                        | 1                                                               |
| D_SPINXTUSEWITH_CNT_ENUM | Count      | Unitless | 0                                                        | 1                                                               |
| SPI_TCDATA_CH            | Count      | Unitless | 0                                                        | Not Defined                                                     |
| SPI_TCDATA_SEQ           | Count      | Unitless | 0                                                        | Not Defined                                                     |
| SPI_DIE1DATA_CH          | Count      | Unitless | Not Defined                                              | 0                                                               |
| SPI_DIE2DATA_CH          | Count      | Unitless | Not Defined                                              | 1                                                               |
| SPI_DIE1DATA_SEQ         | Count      | Unitless | Not Defined                                              | 0                                                               |
| SPI_DIE2DATA_SEQ         | Count      | Unitless | Not Defined                                              | 1                                                               |
| D_SPINXTNUMCHAN_CNT_U16  | Count      | Unitless | 1                                                        | 2                                                               |
| D_SPINXTNUMSEQ_CNT_U16   | Count      | Unitless | 1                                                        | 2                                                               |
| D_TGSIZE_CNT_U16         | Count      | Unitless | Not Defined                                              | 3                                                               |
| MIBSPI3_GCR1             | Count      | Unitless | 3                                                        | 3                                                               |
| MIBSPI5_GCR1             | Count      | Unitless | 3                                                        | 3                                                               |
| MIBSPI3_DELAY            | Count      | Unitless | 0xFFFF0000                                               | 0x04010000                                                      |
| MIBSPI5_DELAY            | Count      | Unitless | 0                                                        | 0x04010000                                                      |
| MIBSPI3_FMT0             | Count      | Unitless | 0xFF00FF08                                               | 0x04020710                                                      |
| MIBSPI5_FMT0             | Count      | Unitless | 0x5E148206                                               | 0x04020710                                                      |
| MIBSPI5_FMT1             | Count      | Unitless | 0x5E148210                                               | Not Defined                                                     |
| MIBSPI5_FMT2             | Count      | Unitless | 0x0014820B                                               | Not Defined                                                     |
| MIBSPI3_TGCNTRL0         | Count      | Unitless | 0x403F0000                                               | 0x001C0000                                                      |
| MIBSPI3_TGCNTRL1         | Count      | Unitless | 0x00000A00                                               | 0x402C0300                                                      |
| MIBSPI3_TGCTRL2          | Count      | Unitless | Not Defined                                              | 0x00700600                                                      |
| MIBSPI3_TOTALTGLENGTH    | Count      | Unitless | 10                                                       | 6                                                               |
| MIBSPI5_TGCNTRL0         | Count      | Unitless | 0x40700000                                               | 0x001E0000                                                      |
| MIBSPI5_TGCNTRL1         | Count      | Unitless | 0x40700300                                               | 0x402E0300                                                      |
| MIBSPI5_TGCNTRL2         | Count      | Unitless | 0x40700600                                               | 0x00700600                                                      |
| MIBSPI5_TGCNTRL3         | Count      | Unitless | 0x40701000                                               | Not Defined                                                     |
| MIBSPI5_TGCNTRL4         | Count      | Unitless | 0x40701400                                               | Not Defined                                                     |
| MIBSPI5_TGCNTRL5         | Count      | Unitless | 0x40707500                                               | Not Defined                                                     |
| MIBSPI5_TOTALTGLENGTH    | Count      | Unitless | 117                                                      | 6                                                               |
| MIBSPI3_BUFRAMCTRLINIT   | Count      | Unitless | 0x84F7                                                   | 0x8CFE                                                          |
| MIBSPI5_BUFRAMCTRLINIT   | Count      | Unitless | Not Defined                                              | 0x8CFE                                                          |
| MIBSPI3_INTCFG           | Count      | Unitless | Defined                                                  | Not Defined                                                     |
| MIBSPI3_LVL              | Count      | Unitless | 0                                                        | Not Defined                                                     |
| MIBSPI3_INT0             | Count      | Unitless | 0                                                        | Not Defined                                                     |
| MIBSPI3_TICKCNT          | Count      | Unitless | 0x80000010                                               | 0                                                               |
| MIBSPI5_TICKCNT          | Count      | Unitless | Not Defined                                              | 0                                                               |
| MIBSPI3_TG0_NOTIF        | Count      | Unitless | Defined                                                  | Not Defined                                                     |
| MIBSPI3_DMACTRL0         | Count      | Unitless | Not Defined                                              | 0x02108000 when BC_SPINXT_USEDMA is STD_ON; otherwise undefined |
| MIBSPI5_DMACTRL0         | Count      | Unitless | Not Defined                                              | 0x02108000 when BC_SPINXT_USEDMA is STD_ON; otherwise undefined |

####  [section]

#### Global

This section lists the global constants used by the module. For details
on global constants, refer to the Data Dictionary for the application.

| Constant Name |
|---------------|
|               |
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

1.  CALL_MIBSPI3_NOTIFFCN()

2.  

## Data Hiding Functions

1.  \<None\>

2.  

## Global Functions/Macros Defined by this Module

### Spi Setup External Buffer

|                      |                  |                      |      |          |          |
|--------------|------------------------|----------------|------|---------|------|
| **Function Name**    | SpiNxt_SetupEB   | Type                 | Min  | Max      | UTP Tol. |
| **Arguments Passed** | Channel          | Spi_ChannelType      | 0    | 255      |          |
|                      | SrcDataBufferPtr | Spi_DataType         | NA   | NA       |          |
|                      | DesDataBufferPtr | Spi_DataType         | NA   | NA       |          |
|                      | Length           | Spi_NumberOfDataType | 0    | 65535    |          |
| **Return Value**     |                  | Std_ReturnType       | E_OK | E_NOT_OK |          |

#### Description

This driver function is a minimalist implementation intended for use
with the Turns Counter component. Additionally this function does not
provide any error detection at this time. The function body is
conditionally compiled such that the SetupEB functionality is provided
when D_SPINXTUSEWITH_CNT_ENUM == D_SPINXT_USEWITHTC, and the function
simply returns E_NOT_OK when D_SPINXTUSEWITH_CNT_ENUM has any other
value.

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SpiNxt/doc/mediax/media/image2.emf)

### Spi Get Sequence Result

|                      |                          |                   |            |                   |          |
|----------|-------------------|-------------|----------|---------------|-----|
| **Function Name**    | SpiNxt_GetSequenceResult | Type              | Min        | Max               | UTP Tol. |
| **Arguments Passed** | Sequence                 | Spi_SequenceType  | 0          | 255               |          |
| **Return Value**     |                          | Spi_SeqResultType | SPI_SEQ_OK | SPI_SEQ_CANCELLED |          |

#### Description

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SpiNxt/doc/mediax/media/image3.emf)

### MIBSPI Transfer

|                      |                |                 |      |      |          |
|----------------------|----------------|-----------------|------|------|----------|
| **Function Name**    | mibspiTransfer | Type            | Min  | Max  | UTP Tol. |
| **Arguments Passed** | mibspi         | mibspiBASE_t \* | FULL | FULL |          |
|                      | group          | uint32          | 0    | 7    |          |
| **Return Value**     | N/A            |                 |      |      |          |

#### Description

Set the Enable Transfer Group bit in the appropriate register to enable
the transfer (when triggered) of the mibspi transfer group defined by
the arguments:

mibspi-\>TGCTRL\[group\] \|= 0x80000000UL

### Spi Asynchronous Transmit

|                      |                      |                  |      |          |          |
|---------------|-------------------------|-------------|------|---------|------|
| **Function Name**    | SpiNxt_AsyncTransmit | Type             | Min  | Max      | UTP Tol. |
| **Arguments Passed** | Sequence             | Spi_SequenceType | 0    | 255      |          |
| **Return Value**     | result_T_Cnt         | Std_ReturnType   | E_OK | E_NOT_OK |          |

#### Description

This driver function is a minimalist implementation intended for use
with the Turns Counter component. It assumes one-to-one
channel-to-sequence correspondence. The function body is conditionally
compiled such that the Turns Counter-specific Asynchrounous Transmit
functionality is provided when D_SPINXTUSEWITH_CNT_ENUM ==
D_SPINXT_USEWITHTC, and the function simply returns E_NOT_OK when
D_SPINXTUSEWITH_CNT_ENUM has any other value.

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SpiNxt/doc/mediax/media/image4.emf)

### MIBSPI Set Data

|                      |               |                |      |      |          |
|----------------------|---------------|----------------|------|------|----------|
| **Function Name**    | mibspiSetData | Type           | Min  | Max  | UTP Tol. |
| **Arguments Passed** | mibspi        | mibspiBASE_t\* | FULL | FULL |          |
|                      | group         | uint32         | 0    | 7    |          |
|                      | data          | uint16\[\]     | FULL | FULL |          |
| **Return Value**     | N/A           |                |      |      |          |

#### Description

This function copies transmit data from the data\[\] argument into the
appropriate mibspi ram transmit buffer, as selected by the mibspi and
group arguments. It is based on the Halcogen function of the same name.

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SpiNxt/doc/mediax/media/image5.emf)

### MIBSPI Set Control and Data

|                      |                   |                |      |      |          |
|----------------|-----------------------------|-----------|------|------|------|
| **Function Name**    | mibspiSetCtrlData | Type           | Min  | Max  | UTP Tol. |
| **Arguments Passed** | mibspi            | mibspiBASE_t\* | FULL | FULL |          |
|                      | group             | uint32         | 0    | 7    |          |
|                      | data              | Uint32\[\]     | FULL | FULL |          |
| **Return Value**     | N/A               |                |      |      |          |

#### Description

This function copies transmit control and data words from the data\[\]
argument into the appropriate mibspi ram transmit buffer, as selected by
the mibspi and group arguments. It is based on the Halcogen function
mibspiSetData, modified to copy the complete transmit buffer including
both control and data

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SpiNxt/doc/mediax/media/image6.emf)

### MIBSPI Get Data

|                      |                 |                |      |      |          |
|----------------------|-----------------|----------------|------|------|----------|
| **Function Name**    | mibspiGetData   | Type           | Min  | Max  | UTP Tol. |
| **Arguments Passed** | mibspi          | mibspiBASE_t\* | FULL | FULL |          |
|                      | group           | uint32         | 0    | 7    |          |
|                      | data            | uint16\[\]     | FULL | FULL |          |
| **Return Value**     | \[error flags\] | uint32         | 0    | 0x5F |          |

#### Description

This function copies receive data from the appropriate mibspi ram
receive buffer, as selected by the mibspi and group arguments, into the
data\[\] argument. It is based on the Halcogen function of the same
name, modified to optimize for use with the Digital MSB since it will be
called from the Motor Control ISR. The function is conditionally
compiled such that optimized Digital MSB specific functionality is
provided when D_SPINXTUSEWITH_CNT_ENUM == D_SPINXT_USEWITHDIGMSB, and
the original Halcogen functionality is provided when
D_SPINXTUSEWITH_CNT_ENUM has any other value.

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SpiNxt/doc/mediax/media/image7.emf)

## Local Functions/Macros Used by this MDD only

### MIBSPI Set Data 8 Bit

|                      |                |                |      |      |          |
|----------------------|----------------|----------------|------|------|----------|
| **Function Name**    | mibspiSetData8 | Type           | Min  | Max  | UTP Tol. |
| **Arguments Passed** | mibspi         | mibspiBASE_t\* | FULL | FULL |          |
|                      | group          | uint32         | 0    | 7    |          |
|                      | data           | uint8\[\]      | FULL | FULL |          |
| **Return Value**     | N/A            |                |      |      |          |

#### Description

This function copies transmit data from the data\[\] argument into the
appropriate mibspi ram transmit buffer, as selected by the mibspi and
group arguments. It is based on the Halcogen function mibspiSetData,
modified to copy from a uint8 buffer rather than uint16.
![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SpiNxt/doc/mediax/media/image8.emf)

### MIBSPI Get Data 8 Bit

|                      |                 |                |      |      |          |
|----------------------|-----------------|----------------|------|------|----------|
| **Function Name**    | mibspiSetData8  | Type           | Min  | Max  | UTP Tol. |
| **Arguments Passed** | mibspi          | mibspiBASE_t\* | FULL | FULL |          |
|                      | group           | uint32         | 0    | 7    |          |
|                      | data            | uint8\[\]      | FULL | FULL |          |
| **Return Value**     | \[error flags\] | uint32         | 0    | 0x5F |          |

#### Description

This function copies receive data from the appropriate mibspi ram
transmit buffer, as selected by the mibspi and group arguments, into the
data\[\] argument. It is based on the Halcogen function mibspiGetData,
modified to copy to a uint8 buffer rather than uint16.
![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SpiNxt/doc/mediax/media/image9.emf)

### MIBSPI Enable Group Notification

|                      |                               |                 |      |      |          |
|--------------|---------------------|----------------|---------|--------|------|
| **Function Name**    | mibspiEnableGroupNotification | Type            | Min  | Max  | UTP Tol. |
| **Arguments Passed** | mibspi                        | mibspiBASE_t \* | FULL | FULL |          |
|                      | group                         | uint32          | 0    | 7    |          |
|                      | level                         | uint32          | 0    | 1    |          |
| **Return Value**     | N/A                           |                 |      |      |          |

#### Description

This function enables the transfer group interrupt for the mibspi,
transfer group, and interrupt level defined by the arguments.

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SpiNxt/doc/mediax/media/image10.emf)

### MIBSPI Notification

|                      |                    |                    |     |     |     |          |
|----------------|----------------------------|------------|-----|--|------|------|
| **Function Name**    | mibspiNotification | Type               | Min | Max |     | UTP Tol. |
| **Arguments Passed** | **mibspi**         | **mibspiBASE_t\*** |     |     |     |          |
|                      | flags              | uint32             |     |     |     |          |
| **Return Value**     | N/A                |                    |     |     |     |          |

#### Description

This is an error callback that is provided by the application and is
called on an error interrupt. The parameter passed to the callback is a
copy of the error interrupt flag register. It is hardcoded for channel
0/sequence 0 and the Turns Counter application. Because it is hardcoded
for the Turns Counter application, it is conditionally compiled such
that it provides the Turns Counter error callback functionality when
compiled with D_SPINXTUSEWITH_CNT_ENUM == D_SPINXT_USEWITHTC, and
returns without doing anything when compiled with
D_SPINXTUSEWITH_CNT_ENUM set to any other value.

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SpiNxt/doc/mediax/media/image11.emf)

### MIBSPI Group Notification

|                      |                         |                |      |      |          |
|----------------|-----------------------------|-----------|------|------|------|
| **Function Name**    | mibspiGroupNotification | Type           | Min  | Max  | UTP Tol. |
| **Arguments Passed** | mibspi                  | mibspiBASE_t\* | FULL | FULL |          |
|                      | group                   | uint32         | 0    | 7    |          |
| **Return Value**     | N/A                     |                |      |      |          |

#### Description

This is a callback function provided by the application. It is called
when a transfer is complete. The parameter is the transfer group that
triggered the interrupt. This driver is designed to only receive data on
mibspi3 group 0 for the Turns Counter communication function. Because it
is hardcoded for the Turns Counter application, it is conditionally
compiled such that it provides the Turns Counter error callback
functionality when compiled with D_SPINXTUSEWITH_CNT_ENUM ==
D_SPINXT_USEWITHTC, and returns without doing anything when compiled
with D_SPINXTUSEWITH_CNT_ENUM set to any other value.

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SpiNxt/doc/mediax/media/image12.emf)

# Software Module Implementation

## Runtime Environment (RTE) Initial Values

This section lists the initial values of data written by this module but
controlled by the RTE. After RTE initialization, the data in this table
will contain these values.

| Data     | Value |
|----------|-------|
| \<None\> |       |

## Initialization Functions

### Init: SpiNxt_Init

#### Design Rationale

The initialization function initializes mibspi3 and mibspi5 registers as
needed by the Turns Counter and Turns Counter Flash Programming
components, or by the Digital MSB component, controlled by a SpiNxt
configuration parameter (see Integration Manual) which controls a
constant value in the generated SpiNxt_Cfg.h file. The initialization
values are hardcoded in the SpiNxt.h file and are specified by the Turns
Counter (FDD20C), Turns Counter Reflash (FDD98) and Digital MSB (ES-50A)
FDDs.

Additional information regarding initialization of MIBSPI3 when used by
Turns Counter (per FDD20C):

The actual chip select for the PIC Turns Counter SPI transfers on
MIBSPI3 uses a Dio channel, configured by the Dio and Port components as
SPI_TCCS. The required chip select hold time before SPI clocking begins
is controlled by the use of the MIBSPI3 tick counter triggering the SPI
transfer. (See SpiNxt_AsyncTransmit and the value of MIBSPI3_TICKCNT.)

The Dio chip select must remain low throughout the 10 byte transfer,
with a minimum 9.5 usec delay between bytes. It is desired to implement
the 9.5 usec delay in hardware. In order to accomplish this with the
TMS570 SPI peripheral, it is necessary to use the C2TDELAY, the
T2CDELAY, and WDELAY as the sum of all three is needed to reach the
desired delay time at an 80MHz VCLK rate. More details provided in the
C2TDELAY, T2CDELAY, and WDELAY sections of the tables below, to explain
the values of MIBSPI3_DELAY and MIBSPI3_FMT0.

However, use of C2TDELAY and T2CDELAY requires transmit control words
configured to use a MIBSPI3 chip select pin and to release the chip
select between transfers. Therefore a “dummy” SPI chip select is used in
the control words in the transmit buffer (see value of
MIBSPI3_BUFRAMCTRLINIT). This chip select is toggled during the SPI
transfer but only to accomplish the delay timing; it is not toggling a
pin on the PIC Turns Counter.

<table>
<colgroup>
<col style="width: 13%" />
<col style="width: 16%" />
<col style="width: 70%" />
</colgroup>
<tbody>
<tr class="odd">
<td colspan="3"><strong>MIBSPI 3 SPI Delay Register
(SPIDELAY)</strong></td>
</tr>
<tr class="even">
<td>Position</td>
<td>Desired Value</td>
<td>Description</td>
</tr>
<tr class="odd">
<td>bit 31-24</td>
<td>255</td>
<td><p><strong>C2TDELAY:</strong> Chip-select-active to transmit-start
delay</p>
<p>t C2TDELAY= (C2TDELAY + 2) <strong>*</strong>VCLK Period</p>
<ul>
<li><p>Per §8.5.3 of [2] parameter 3 specifies a 9.5 uS clock idle time
between bytes.</p></li>
<li><p>It is desired to implement the delay in hardware. In order to
accomplish this with the TMS570 SPI peripheral, the Spi to CS CLK start
delay is used.</p></li>
<li><p>Per [2] the FDD design desires to maximize the clock idle time
between bytes using the hardware delays available.</p></li>
<li><p>Table 24-26 of [3] indicates the C2TDELAY has a max of 1FFh,
however, the field is 8 bits wide so this is considered a typo in the
data sheet and the actual max is FFh (255). With an 80MHz VCLK, using
the equation in the table yields a maximum delay of 3.2125 uS.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>bit 23-16</td>
<td>255</td>
<td><p><strong>T2CDELAY:</strong>
Transmit-end-to-chip-select-inactive-delay</p>
<p>t T2CDELAY= (T2CDELAY +1) <strong>*</strong>VCLK Period</p>
<ul>
<li><p>Per §8.5.3 of [2] parameter 4 specifies a minimum 1.5 uS
delay.</p></li>
<li><p>Per [2] the FDD design desires to maximize the clock idle time
between bytes using the hardware delays available.</p></li>
<li><p>Table 24-26 of [3] indicates the T2CDELAY has a max of 1FFh,
however, the field is 8 bits wide so this is considered a typo in the
data sheet and the actual max is FFh (255). With an 80MHz VCLK, using
the equation in the table yields a maximum delay of 3.2 uS.</p></li>
<li><p>The maximum delay of 3.2 uS is achieved by setting this parameter
to 255.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>bit 15-8</td>
<td>0</td>
<td><p><strong>T2EDELAY:</strong> Transmit-data-finished to
ENA-pin-inactive time-out</p>
<p>ENA pin functionality is disabled, so this parameter has no effect.
It is set arbitrarily set to 0.</p></td>
</tr>
<tr class="even">
<td>bit 7-0</td>
<td>0</td>
<td><p><strong>C2EDELAY:</strong> Chip-select-active to
ENA-signal-active time-out</p>
<p>ENA pin functionality is disabled, so this parameter has no effect.
It is set arbitrarily set to 0.</p></td>
</tr>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 13%" />
<col style="width: 16%" />
<col style="width: 70%" />
</colgroup>
<tbody>
<tr class="odd">
<td colspan="3"><strong>MIBSPI 3 SPI Data Format 0 Register
(SPIFMT0)</strong></td>
</tr>
<tr class="even">
<td>Position</td>
<td>Desired Value</td>
<td>Description</td>
</tr>
<tr class="odd">
<td>bit 31-24</td>
<td>255</td>
<td><p><strong>WDELAY:</strong> Delay in between transmissions for
data</p>
<p>WDELAY * PVCLK + 2 * PVCLK</p>
<ul>
<li><p>The inter-byte delay is accomplished via a combination of the CS
activation and deactivation delays and this parameter. The other 2
delays are 3.212uS + 3.200uS = 6.412uS. Per [2] the FDD design desires
to maximize the clock idle time between bytes using the hardware delays
available.</p></li>
<li><p>Table 24-28 of [3] indicates the WDELAY has a max of 63, which is
an error in the data sheet, 254 is the actual max reported by Eric Best,
TI FAE. With an 80MHz VCLK, using the equation in the table yields a
maximum delay of 3.2 uS.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>bit 23</td>
<td>0</td>
<td><p><strong>PARPOL:</strong> Parity polarity: even or odd</p>
<p>Parity not enabled, so this has parameter has no effect. Arbitrarily
se to 0.</p></td>
</tr>
<tr class="odd">
<td>bit 22</td>
<td>0</td>
<td><p><strong>PARITYENA:</strong> Parity enable for data</p>
<blockquote>
<p>Per §8.5.3 of [2], Data Format specifies Parity to be disabled, so
this parameter is set to 0.</p>
</blockquote></td>
</tr>
<tr class="even">
<td>bit 21</td>
<td>0</td>
<td><p><strong>WAITENA:</strong></p>
<blockquote>
<p>Per §8.5.3 of [2], Data Format specifies WAITENA to be disabled, so
this parameter is set to 0.</p>
</blockquote></td>
</tr>
<tr class="odd">
<td>bit 20</td>
<td>0</td>
<td><p><strong>SHIFTDIR:</strong> Shift direction for data</p>
<blockquote>
<p>Per §8.5.3 of [2], Data Format specifies MSB shifted out first, so
this parameter is set to 0.</p>
</blockquote></td>
</tr>
<tr class="even">
<td>bit 19</td>
<td>0</td>
<td><strong>Reserved:</strong></td>
</tr>
<tr class="odd">
<td>bit 18</td>
<td>0</td>
<td><p><strong>DIS CS TIMERS:</strong> Disable chip-select timers for
this format.</p>
<p>Delays specified by C2TDELAY and T2CDELAY are required for creating
the inter byte delay specified in §8.5.3 of [2], so this is set to 0 to
enable the delays.</p></td>
</tr>
<tr class="even">
<td>bit 17</td>
<td>0</td>
<td><p><strong>POLARITY:</strong> SPI data clock polarity</p>
<blockquote>
<p>§8.5.3 of [2], Clock settings specify the polarity to be
Inactive-Low, so this is set to 0. (Note that the Active-High,
requirement is not understood and is ignored in the configuration in
this module. When the clock is active it is toggling states to provide
edges, thus specifying the active state as a constant level has an
unknown meaning)</p>
</blockquote></td>
</tr>
<tr class="odd">
<td>bit 16</td>
<td>0</td>
<td><p><strong>PHASE:</strong> SPI data clock delay</p>
<blockquote>
<p>§8.5.3 of [2], Clock settings specify the SCLK edges to be
synchronized with the data stream, so this is set to 0.</p>
</blockquote></td>
</tr>
<tr class="even">
<td>bit 15-8</td>
<td>255</td>
<td><p><strong>PRESCALE:</strong> PRESCALE is use to derive SPICLK from
VCLK</p>
<p>BRFormat = VBUSPCLK / (PRESCALEx ÷ 1)</p>
<ul>
<li><p>Turns Counter function in [2]§8.5.3 requires a clock source
frequency of 300 kHz, however this is not an actual requirement as
discussed with the FDD owner, but rather a documentation of the
implementation choice at the time of FDD release. The physical maximum
for SPI clock is specified in [1]Table 30-15 by SP71 and SP72
parameters. With the 8MHz PIC clock the time parameters = 1/(8MHz/4) +
20ns = 250ns + 20ns = 270 ns. This results in an overall period of 540ns
= 1.85 MHz</p></li>
<li><p>Table 24-28 of [3] indicates the PRESCALE is 8 bits wide
providing a max of 255. With an 80MHz VCLK, this results in a minimum of
baud rate of approx. 314 baud.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>bit 7-5</td>
<td>0</td>
<td><strong>Reserved:</strong></td>
</tr>
<tr class="even">
<td>bit 4-0</td>
<td>8</td>
<td><p><strong>CHARLEN:</strong> SPI data data-word length.</p>
<blockquote>
<p>Per §8.5.3 of [2], Data Format specifies a value of 8 for this
parameter.</p>
</blockquote></td>
</tr>
</tbody>
</table>

#### Module Outputs

None

#### Module Internal 

#### ![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SpiNxt/doc/mediax/media/image13.emf)  [section-1]

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SpiNxt/doc/mediax/media/image14.emf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SpiNxt/doc/mediax/media/image15.emf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SpiNxt/doc/mediax/media/image16.emf)![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SpiNxt/doc/mediax/media/image17.emf)

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SpiNxt/doc/mediax/media/image18.emf)

## Periodic Functions

None

## Fault Recovery Functions

None

## Shutdown Functions

None

## Interrupt Functions

### Isr: \_IrqUnit2TxRx

#### Design Rationale

None

#### Program Flow Start

None

#### SpiNxt_IrqUnit2TxRx

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SpiNxt/doc/mediax/media/image19.wmf)

#### Program Flow End

None

### Isr: \_IrqUnit2TxRxERR

None

#### Program Flow Start

None

#### SpiNxt_IrqUnit2TxRxERR

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/SpiNxt/doc/mediax/media/image20.wmf)

#### Program Flow End

None

##  Serial Communication Functions

None

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

| Name of Sub Module      | Software Segment      |
|-------------------------|-----------------------|
| Spi_SetupEB()           | SPINXT_START_SEC_CODE |
| Spi_GetSequenceResult() | SPINXT_START_SEC_CODE |
| Spi_AsyncTransmit()     | SPINXT_START_SEC_CODE |
| Spi_Init()              | SPINXT_START_SEC_CODE |
| mibspiSetData()         | SPINXT_START_SEC_CODE |
| mibspiSetCtrlData()     | SPINXT_START_SEC_CODE |
| mibspiGetData()         | SPINXT_START_SEC_CODE |
| mibspiTransfer()        | SPINXT_START_SEC_CODE |

##  [section-3]

## Local Functions

This table identifies the software segments for local functions
identified in this module.

| Name of Sub Module              | Software Segment      |
|---------------------------------|-----------------------|
| mibspiSetData8()                | SPINXT_START_SEC_CODE |
| mibspiGetData8()                | SPINXT_START_SEC_CODE |
| mibspiEnableGroupNotification() | SPINXT_START_SEC_CODE |
| mibspiNotification()            | SPINXT_START_SEC_CODE |
| mibspiGroupNotification()       | SPINXT_START_SEC_CODE |

#  [section-4]

#  Known Issues / Limitations With Design

1.  Driver has several functions and all initializations hardcoded for
    what is needed by the Turns Counter , the Turns Counter Reflash, or
    the Digital MSB. Future modifications of the SPI interface of those
    components will probably require changes to this driver. New uses of
    the SPI driver would also require driver changes. Currently the only
    configurability is through the configuration parameter
    SpiNxt/SpiNxtGeneral/SpiNxtUseWith which selects either Turns
    Counter or Digital MSB functionality.

2.  The Autosar API was not implemented for use by the Digital MSB for
    the following reasons:  
    a) The digital MSB triggers SPI transfers external to the SPI
    driver, through the NHET as set up in the ePWM component. This means
    the SpiNxt_AsyncTransmit () function (if implemented for use by
    digital MSB) could not follow the Autosar requirement to initiate
    the transfer and set the driver/handler status accordingly.  
    b) The digital MSB transfers require chip select to be released
    after each word transferred. This means the four words would have to
    be defined as four channels/four jobs. Each channel requires its own
    buffer (internal or external). Because the SPI data reads and writes
    occur in the motor control ISR, they need to be very efficient and
    cannot afford the overhead of four calls to SpiNxt_SetupEB() that
    would be needed to implement the double buffering being done on the
    read data. Use of a possible SpiNxt_ReadIB() would have this same
    issue even without the double buffering.

3.  Several of the initialization constants (delay fields in the delay
    registers and data format registers, and the baudrate prescale field
    in the data format registers) have values that depend on the VCLK
    frequency. These are currently hardcoded for 80 MHz VCLK for Digital
    MSB, and have values that will work for both 75MHz and 80MHz VCLK
    for Turns Counter / Turns Counter Reflash (see spreadsheet attached
    to Turns Counter Reflash FDD). A future improvement would be to
    calculate these values based on a VCLK configuration parameter.

#  Revision Control Log

<table style="width:100%;">
<colgroup>
<col style="width: 6%" />
<col style="width: 6%" />
<col style="width: 64%" />
<col style="width: 11%" />
<col style="width: 11%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Item #</strong></td>
<td><strong>Rev #</strong></td>
<td><strong>Change Description</strong></td>
<td><strong>Date</strong></td>
<td><strong>Author Initials</strong></td>
</tr>
<tr class="even">
<td>1</td>
<td>1</td>
<td>Initial versiond</td>
<td></td>
<td>JJW</td>
</tr>
<tr class="odd">
<td>2</td>
<td>2</td>
<td><p>AsyncTransmit design improvement using exclusive areas and
message transmit state check to ensure proper management of data
transmission.</p>
<p>Added setting DIO CS channels to inactive during init</p>
<p>Added mibspi unit check around Error notification processing</p></td>
<td>15-Mar-12</td>
<td>JJW</td>
</tr>
<tr class="even">
<td>3</td>
<td>3</td>
<td>Added Notification function hook for end of sequence
notification</td>
<td>23-Mar-12</td>
<td>JJW</td>
</tr>
<tr class="odd">
<td>4</td>
<td>4</td>
<td>Increased WDELAY and T2CDELAY to meet updated FDD 20C
requirements</td>
<td>27-Mar-12</td>
<td>JJW</td>
</tr>
<tr class="even">
<td>5</td>
<td>5</td>
<td>Added metrics hooks to interrupt service routines.</td>
<td>22-Mar-13</td>
<td>BWL</td>
</tr>
<tr class="odd">
<td>6</td>
<td>6</td>
<td>Completed documentation of all functions in the module, along with
changes required for the Digital MSB and the fix for anomaly 4713.</td>
<td>05-Aug-13</td>
<td>KMC</td>
</tr>
<tr class="even">
<td>7</td>
<td>7</td>
<td>Removed conditionally-compiled mibspiSetData() functionality for
digital MSB; modified conditionally-compiled mibspiGetData()
functionality for digital MSB per ES-50A v005,changed initialization
constant values, and added DMA control initialization, all per ES-50A
v005 and fix for anomaly 5929.</td>
<td>01-Apr-14</td>
<td>KMC</td>
</tr>
</tbody>
</table>

{% endraw %}