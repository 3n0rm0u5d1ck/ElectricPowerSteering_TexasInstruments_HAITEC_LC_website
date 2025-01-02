---
layout: default
title: Spi_Nexteer_Integration_Manual
nav_order: 1
parent: SpiNxt
---
{% raw %}
# Contents [contents]

[1 Dependencies [1](#_Toc363214774)](#_Toc363214774)

[1.1 SWCs [1](#swcs)](#swcs)

[1.2 Global Functions(Non RTE) to be provided to Integration Project
[2](#global-functionsnon-rte-to-be-provided-to-integration-project)](#global-functionsnon-rte-to-be-provided-to-integration-project)

[2 Configuration [2](#configuration)](#configuration)

[2.1 Build Time Config [2](#build-time-config)](#build-time-config)

[2.2 Configuration Files to be provided by Integration Project
[2](#configuration-files-to-be-provided-by-integration-project)](#configuration-files-to-be-provided-by-integration-project)

[2.2.1 Da Vinci Parameter Configuration Changes
[2](#da-vinci-parameter-configuration-changes)](#da-vinci-parameter-configuration-changes)

[2.2.2 Da Vinci Interrupt Configuration Changes
[3](#da-vinci-interrupt-configuration-changes)](#da-vinci-interrupt-configuration-changes)

[2.2.3 Manual Configuration Changes
[3](#manual-configuration-changes)](#manual-configuration-changes)

[3 Integration [4](#integration)](#integration)

[3.1 Required Global Data Inputs
[4](#required-global-data-inputs)](#required-global-data-inputs)

[3.2 Required Global Data Outputs
[4](#required-global-data-outputs)](#required-global-data-outputs)

[3.3 Specific Include Path present
[4](#specific-include-path-present)](#specific-include-path-present)

[4 Runnable Scheduling [5](#runnable-scheduling)](#runnable-scheduling)

[5 Memory Mapping [5](#memory-mapping)](#memory-mapping)

[5.1 Mapping [5](#mapping)](#mapping)

[5.2 Usage [5](#usage)](#usage)

[5.3 Non RTE NvM Blocks [5](#non-rte-nvm-blocks)](#non-rte-nvm-blocks)

[5.4 RTE NvM Blocks [5](#rte-nvm-blocks)](#rte-nvm-blocks)

[6 Compiler Settings [5](#_Toc357692835)](#_Toc357692835)

[6.1 Preprocessor MACRO [5](#preprocessor-macro)](#preprocessor-macro)

[6.2 Optimization Settings
[6](#optimization-settings)](#optimization-settings)

<span id="_Toc363214774" class="anchor"></span>

# Dependencies

## SWCs

<table>
<colgroup>
<col style="width: 36%" />
<col style="width: 63%" />
</colgroup>
<thead>
<tr class="header">
<th>Module</th>
<th>Required Feature</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Dio</td>
<td>Dio_WriteChannel() when SpiNxt used with Turns Counter</td>
</tr>
<tr class="even">
<td>TMS570 MIBSPI3 and MIBSPI5 peripheral</td>
<td><p>Exclusive access to the MIBSPI3 and MIBSPI5 peripheral
registers.</p>
<p>MIBSPI3 CS3 provided as a No Connect pin on CCA design when SpiNxt
used with Turns Counter</p></td>
</tr>
<tr class="odd">
<td>Os</td>
<td>Category 2 ISR mapping for MIBSPI3 IRQ sources when SpiNxt used with
Turns Counter</td>
</tr>
<tr class="even">
<td>TurnsCounter</td>
<td>TurnsCounter_TxConfirmation() when SpiNxt used with Turns
Counter</td>
</tr>
<tr class="odd">
<td>ePWM</td>
<td>Must provide SPI transmit trigger on N2HET1[14] for mibspi3, and
N2HET1[18] for mibspi5, when SpiNxt used with Digital MSB.</td>
</tr>
</tbody>
</table>

## Global Functions(Non RTE) to be provided to Integration Project

void **SpiNxt_Init**(void);

Std_ReturnType **SpiNxt_AsyncTransmit**( Spi_SequenceType Sequence );  
NOTE that this function is hardcoded for use with the Turns Counter
component and returns E_NOT_OK when SpiNxt not configured for use with
Turns Counter (see section 2.2.1).

Spi_SeqResultType **SpiNxt_GetSequenceResult**( Spi_SequenceType
Sequence );

Std_ReturnType **SpiNxt_SetupEB**( Spi_ChannelType Channel,  
P2CONST(Spi_DataType, AUTOMATIC, SPI_APPL_DATA) SrcDataBufferPtr,  
P2VAR(Spi_DataType, AUTOMATIC, SPI_APPL_DATA) DesDataBufferPtr,  
Spi_NumberOfDataType Length);  
NOTE that this function is hardcoded for use with the Turns Counter
component and returns E_NOT_OK when SpiNxt not configured for use with
Turns Counter (see section 2.2.1).

void **mibspiSetData**(const mibspiBASE_t \*mibspi, uint32 group, const
uint16 data\[\]);

void **mibspiSetCtrlData**(const mibspiBASE_t \*mibspi, uint32 group,
const uint32 data\[\]);

uint32 **mibspiGetData**(const mibspiBASE_t \*mibspi, uint32 group,
uint16 data\[\]);  
NOTE this function is optimized for use by the Digital MSB component
when SpiNxt is configured for use with Digital MSB (see section 2.2.1).
In that configuration, the mibspi argument must be equal to the base
register address of mibspi3 or mibspi5, the length of all transfer
groups is assumed to be the constant D_TGSIZE_CNT_U16 (defined in
SpiNxt.h), the function always returns zero, and the data argument must
be the receive data buffer for the caller.

void **mibspiTransfer**(mibspiBASE_t \*mibspi, uint32 group);

NOTE that this function enables the specified transfer group for the
specified mibspi (with base address equal to the mibspi argument).
Depending on the configuration of the transfer group, it will either
enable a single transfer on the next trigger (if the transfer group is
configured for oneshot) or will enable ongoing transfers as triggered
((if the transfer group is **not** configured for oneshot).

# Configuration

## Build Time Config

| Modules | Notes |
|---------|-------|
| None    |       |

## Configuration Files to be provided by Integration Project

SpiNxt_Cfg.h as generated by SpiNxt_cfg.h.tt

### Da Vinci Parameter Configuration Changes

<table>
<colgroup>
<col style="width: 39%" />
<col style="width: 48%" />
<col style="width: 11%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Notes</th>
<th>SWC</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Dio Channel Name: “SPI_TCCS”</td>
<td>Chip Select DIO output mapped to the turns counter chip select pin
when used with Turns Counter</td>
<td>Dio</td>
</tr>
<tr class="even">
<td>All MIBSPI3 and MIBSPI5 configuration</td>
<td>The third party Spi driver shall be configured such that it does not
read/write any of the MIBSPI3 or MIBSPI5 control registers.</td>
<td>Spi</td>
</tr>
<tr class="odd">
<td>Port pin SPI3CLK: SPI Output</td>
<td></td>
<td>Port</td>
</tr>
<tr class="even">
<td>Port pin SPI3NCS3: SPI Output</td>
<td>When used with Turns Counter</td>
<td>Port</td>
</tr>
<tr class="odd">
<td>Port pin SPI3NCS0: SPI Output</td>
<td>When used with Digital MSB</td>
<td>Port</td>
</tr>
<tr class="even">
<td>Port pin SPI3SIMO: SPI Output</td>
<td></td>
<td>Port</td>
</tr>
<tr class="odd">
<td>Port pin SPI3SOMI: SPI Input</td>
<td></td>
<td>Port</td>
</tr>
<tr class="even">
<td>Port pin SPI5CLK: SPI Output</td>
<td></td>
<td>Port</td>
</tr>
<tr class="odd">
<td>Port pin SPI5NCS0: SPI Output</td>
<td>When used with Digital MSB</td>
<td>Port</td>
</tr>
<tr class="even">
<td>Port pin SPI5SIMO: SPI Output</td>
<td></td>
<td>Port</td>
</tr>
<tr class="odd">
<td>Port pin SPI5SOMI: SPI Input</td>
<td>When used with Digital MSB</td>
<td>Port</td>
</tr>
<tr class="even">
<td>SPINXT_EXCLUSIVE_AREA_0</td>
<td>This exclusive area covers the events that need to be synchronized
to minimize jitter on the CS to SCLK delay specified by the TurnsCounter
FDD 20C (when used with Turns Counter)</td>
<td>SchM</td>
</tr>
<tr class="odd">
<td>SpiNxtGeneral\ SpiNxtUseWith</td>
<td><p>This parameter controls generation of D_SPINXTUSEWITH_CNT_ENUM in
the SpiNxt_Cfg.h file. Set to D_SPINXT_USEWITHTC for use with the PIC
Turns Counter, or set to D_SPINXT_USEWITHDIGMSB for use with the Digital
MSB.</p>
<p>When this parameter is set to D_SPINXT_USEWITHTC, the SpiNxt.h file
provides the following constants which previously were manually
configured: SPI_TCDATA_CH, SPI_TCDATA_SEQ, D_SPINXTNUMCHAN_CNT_U16, and
CALL_MIBSPI3_NOTIFFCN().</p></td>
<td>SpiNxt</td>
</tr>
<tr class="even">
<td>SpiNxtGeneral\ SpiNxtUseDMA</td>
<td>This parameter controls generation of BC_SPINXT_USEDMA in the
SpiNxt_Cfg.h file. Set to STD_ON when using DMA with SPI.</td>
<td>SpiNxt</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

### Da Vinci Interrupt Configuration Changes

| ISR Name                                          | Notes                                                                                           | SWC |
|---------------------------|--------------------------------------|--------|
| SpiNxt_IrqUnit2TxRx: MIBSPI3 level 0 interrupt    | Category 2 interrupt mapped to Mibspi3 RxTx interrupt source when used with Turns Counter       | Os  |
| SpiNxt_IrqUnit2TxRxERR: MIBSPI3 level 1 interrupt | Category 2 interrupt mapped to Mibspi3 RxTx error interrupt source when used with Turns Counter | Os  |

### Manual Configuration Changes

| Constant | Notes | SWC |
|----------|-------|-----|
| None     |       |     |

# Integration

## Required Global Data Inputs

\<None\>

## Required Global Data Outputs

\<None\>

## Specific Include Path present

\<Yes\>

# Runnable Scheduling

This section specifies the required runnable scheduling.

| Init          | Scheduling Requirements                                    | Trigger |
|--------------------------|--------------------------------------|--------|
| SpiNxt_Init() | Must be executed prior to using any of the module C/S API. | Init    |

| Runnable              | Scheduling Requirements                                                  | Trigger |
|--------------------------|--------------------------------------|--------|
| SpiNxt_MainFunction() | Dummy runnable used for assigning the SpiNxt component to an application | N/A     |

# Memory Mapping

## Mapping

| Constant                                 | Notes |
|------------------------------------------|-------|
| SPINXT_START_SEC_VAR_CLEARED_UNSPECIFIED |       |
| SPINXT_START_SEC_CODE                    |       |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

| Feature     | RAM | ROM |
|-------------|-----|-----|
| Full driver |     |     |

Table 1: ARM Cortex R4 Memory Usage

## Non RTE NvM Blocks

| Block Name |
|------------|
| \<None \>  |

Note : Size of the NVM block if configured in developer

##  RTE NvM Blocks

| Block Name |
|------------|
| \<None \>  |

Note : Size of the NVM block if configured in developer

<span id="_Toc357692835" class="anchor"></span>

# Compiler Settings

##  Preprocessor MACRO

\<Define all the preprocessor Macros needed and conditions when
needed\>.

## Optimization Settings

\<Define Optimization levels that are needed and conditions when
needed\>.

##  [section]

#  Revision Control Log

|             |            |                                                                                                                                       |          |                     |
|------|------|--------------------------------------------|---------|---------|
| **Item \#** | **Rev \#** | **Change Description**                                                                                                                | **Date** | **Author Initials** |
| 1           | 1          | Initial version                                                                                                                       |          | JJW                 |
| 2           | 2          | Added exclusive area configuration and Category 2 interrupt configuration                                                             |          | JJW                 |
| 3           | 3          | Added ISR MIBSPI level configuration requirement                                                                                      |          | JJW                 |
| 4           | 4          | New Notification build configuration parameter                                                                                        |          | JJW                 |
| 5           | 5          | Changes and additions for configurability of SpiNxt to be used with PIC Turns Counter or with Digital MSB.                            | 8/2/13   | KMC                 |
| 6           | 6          | Updated information on Halcogen API functions and added configuration parameter for use of DMA with SPI as needed for ES-50A rev 005. | 4/1/14   | KMC                 |

{% endraw %}