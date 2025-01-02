---
layout: default
title: Integration_Manual_ADC
nav_order: 6
parent: Adc Driver
---
{% raw %}
[1 Dependencies [2](#dependencies)](#dependencies)

[1.1 SWCs [2](#swcs)](#swcs)

[1.2 Global Functions(Non RTE) to be provided to Integration Project
[2](#global-functionsnon-rte-to-be-provided-to-integration-project)](#global-functionsnon-rte-to-be-provided-to-integration-project)

[2 Configuration [3](#configuration)](#configuration)

[2.1 Build Time Config [3](#build-time-config)](#build-time-config)

[2.2 Configuration Files to be provided by Integration Project
[3](#configuration-files-to-be-provided-by-integration-project)](#configuration-files-to-be-provided-by-integration-project)

[2.2.1 Da Vinci Parameter Configuration Changes
[3](#da-vinci-parameter-configuration-changes)](#da-vinci-parameter-configuration-changes)

[2.2.2 DaVinci Interrupt Configuration Changes
[3](#davinci-interrupt-configuration-changes)](#davinci-interrupt-configuration-changes)

[2.2.3 Manual Configuration Changes
[3](#manual-configuration-changes)](#manual-configuration-changes)

[3 Integration [6](#integration)](#integration)

[3.1 Required Global Data Inputs
[6](#required-global-data-inputs)](#required-global-data-inputs)

[3.2 Required Global Data Outputs
[6](#required-global-data-outputs)](#required-global-data-outputs)

[3.3 Specific Include Path present
[6](#specific-include-path-present)](#specific-include-path-present)

[4 Runnable Scheduling [7](#runnable-scheduling)](#runnable-scheduling)

[5 Memory Mapping [8](#memory-mapping)](#memory-mapping)

[5.1 Mapping [8](#mapping)](#mapping)

[5.2 Usage [8](#usage)](#usage)

[5.3 Non RTE NvM Blocks [8](#non-rte-nvm-blocks)](#non-rte-nvm-blocks)

[5.4 RTE NvM Blocks [8](#rte-nvm-blocks)](#rte-nvm-blocks)

[6 Compiler Settings [8](#compiler-settings)](#compiler-settings)

[6.1 Preprocessor MACRO [8](#preprocessor-macro)](#preprocessor-macro)

[6.2 Optimization Settings
[8](#optimization-settings)](#optimization-settings)

[7 Revision Control Log
[9](#revision-control-log)](#revision-control-log)

# Dependencies

## SWCs

<table>
<colgroup>
<col style="width: 30%" />
<col style="width: 69%" />
</colgroup>
<thead>
<tr class="header">
<th>Module</th>
<th>Required Feature</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>IoHwAbsUsr</td>
<td><p>Parts of the Adc FDDs (33C or 33E) are intended to be implemented
at the integration level and are typically included in IoHwAbsUsr. Note
that this includes implementation of NTC 0x32 and/or NTC 0x33 as needed
for the specific application.</p>
<p>NOTE that as of FDD33C rev 008 and FDD33E rev 002, DMA-related
updates are not included in the FDDs. The looping on group busy and
associated timeouts and NTC setting should not be implemented when using
with DMA; alternate means of getting the data when ready and associated
fault setting are outlined in the DMA FDD ES-52.</p></td>
</tr>
</tbody>
</table>

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
refered. Developer should track the references.

## Global Functions(Non RTE) to be provided to Integration Project

-   Adc_Init() NOTE this is a macro mapped to Adc_Init_FixedCfg for
    Autosar interface compatibility. The Adc_Init macro takes a
    parameter which is not used by the function.

-   FUNC(void, ADC_CODE) Adc_StartGroupConversion(Adc_GroupType Group)

-   FUNC(Std_ReturnType, ADC_CODE) Adc_ReadGroup(Adc_GroupType Group,
    Adc_ValueGroupRefType DataBufferPtr)

-   FUNC(Adc_StatusType, ADC_CODE) Adc_GetGroupStatus(Adc_GroupType
    Group)

-   inline uint16 Adc2_ReadConversion(uint16 ConvId) NOTE this function
    directly accesses Adc RAM and should not be used when using DMA to
    transfer Adc data

-   void Adc2_Init1(void)

-   void Adc2_StartGroupConversion(uint8 group)

# Configuration

## Build Time Config

| Modules | Notes |     |
|---------|-------|-----|
| None    |       |     |

## Configuration Files to be provided by Integration Project

##  [section]

Adc_Cfg.h and Adc2_Cfg.h. Configuration file templates are in the Tools
folder.

NOTE:

For Projects using 33E, make sure “D_ADC1CURRENTMODE_ULS_LGC” is defined
in Adc_Cfg.h file.

For Projects using 33C, make sure “D_ADC1CURRENTMODE_ULS_LGC” is **NOT**
defined in Adc_Cfg.h file.

### Da Vinci Parameter Configuration Changes

| Parameter                               | Notes | SWC |
|-----------------------------------------|-------|-----|
| \<Configurator Changes for parameters\> |       |     |

### DaVinci Interrupt Configuration Changes

| ISR Name                                | VIM \# | Priority Dependency | Notes |
|-------------|--------|---------------------------|-------------------------|
| \<Configurator Changes for Interrupts\> |        |                     |       |

### Manual Configuration Changes

<table style="width:100%;">
<colgroup>
<col style="width: 41%" />
<col style="width: 44%" />
<col style="width: 13%" />
</colgroup>
<thead>
<tr class="header">
<th>Constant</th>
<th>Notes</th>
<th>SWC</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>D_ADC1GEVTSRC_CNT_U32*</td>
<td>Initialization value for adcREG1-&gt;G0SRC</td>
<td>Adc_Cfg.h</td>
</tr>
<tr class="even">
<td>D_ADC1GEVTDMACR_CNT_U32*</td>
<td>Initialization value for adcREG1-&gt;G0DMACR</td>
<td>Adc_Cfg.h</td>
</tr>
<tr class="odd">
<td>D_ADC1G1SRC_CNT_U32*</td>
<td>Initialization value for adcREG1-&gt;G1SRC</td>
<td>Adc_Cfg.h</td>
</tr>
<tr class="even">
<td>D_ADC1G1DMACR_CNT_U32*</td>
<td>Initialization value for adcREG1-&gt;G1DMACR</td>
<td>Adc_Cfg.h</td>
</tr>
<tr class="odd">
<td>D_ADC1G2SRC_CNT_U32*</td>
<td>Initialization value for adcREG1-&gt;G2SRC</td>
<td>Adc_Cfg.h</td>
</tr>
<tr class="even">
<td>D_ADC1G2DMACR_CNT_U32*</td>
<td>Initialization value for adcREG1-&gt;G2DMACR</td>
<td>Adc_Cfg.h</td>
</tr>
<tr class="odd">
<td>D_ADC1USEDMA_CNT_LGC*</td>
<td>STD_ON if using DMA to transfer ADC1 data; otherwise STD_OFF</td>
<td>Adc_Cfg.h</td>
</tr>
<tr class="even">
<td>D_HWTRGADC1GEVT_CNT_LGC*</td>
<td>STD_ON to reconfigure ADC1 event group for hardware trigger after
initial reads; otherwise STD_OFF</td>
<td>Adc_Cfg.h</td>
</tr>
<tr class="odd">
<td>D_HWTRGADC1G1_CNT_LGC*</td>
<td>STD_ON to reconfigure ADC1 group 1 for hardware trigger after
initial reads; otherwise STD_OFF</td>
<td>Adc_Cfg.h</td>
</tr>
<tr class="even">
<td>D_HWTRGADC1G2_CNT_LGC*</td>
<td>STD_ON to reconfigure ADC1 group 2 for hardware trigger after
initial reads; otherwise STD_OFF</td>
<td>Adc_Cfg.h</td>
</tr>
<tr class="odd">
<td>D_ADC2EVINTENA_CNT_U32*</td>
<td>Initialization value for adcREG2-&gt;<br />
GxINTENA[D_GROUPEV_CNT_U8]</td>
<td>Adc2_Cfg.h</td>
</tr>
<tr class="even">
<td>D_ADC2EVSAMPDISEN_CNT_U32*</td>
<td>Initialization value for adcREG2-&gt;<br />
G0SAMPDISEN</td>
<td>Adc2_Cfg.h</td>
</tr>
<tr class="odd">
<td>D_ADC2EVFIFORESETCR_CNT_U32*</td>
<td>Initialization value for adcREG2-&gt;<br />
GxFIFORESETCR[D_GROUPEV_CNT_U8]</td>
<td>Adc2_Cfg.h</td>
</tr>
<tr class="even">
<td>D_ADC2EVDMACR_CNT_U32*</td>
<td>Initialization value for adcREG2-&gt;<br />
G0DMACR</td>
<td>Adc2_Cfg.h</td>
</tr>
<tr class="odd">
<td>D_ADC2G1INTENA_CNT_U32*</td>
<td>Initialization value for adcREG2-&gt;<br />
GxINTENA[D_GROUP1_CNT_U8]</td>
<td>Adc2_Cfg.h</td>
</tr>
<tr class="even">
<td>D_ADC2G1SAMPDISEN_CNT_U32*</td>
<td>Initialization value for adcREG2-&gt;<br />
G0SAMPDISEN</td>
<td>Adc2_Cfg.h</td>
</tr>
<tr class="odd">
<td>D_ADC2G1FIFORESETCR_CNT_U32*</td>
<td>Initialization value for adcREG2-&gt;<br />
GxFIFORESETCR[D_GROUP1_CNT_U8]</td>
<td>Adc2_Cfg.h</td>
</tr>
<tr class="even">
<td>D_ADC2G1DMACR_CNT_U32*</td>
<td>Initialization value for adcREG2-&gt;<br />
G0DMACR</td>
<td>Adc2_Cfg.h</td>
</tr>
<tr class="odd">
<td>D_ADC2G2INTENA_CNT_U32*</td>
<td>Initialization value for adcREG2-&gt;<br />
GxINTENA[D_GROUP2_CNT_U8]</td>
<td>Adc2_Cfg.h</td>
</tr>
<tr class="even">
<td>D_ADC2G2SAMPDISEN_CNT_U32*</td>
<td>Initialization value for adcREG2-&gt;<br />
G0SAMPDISEN</td>
<td>Adc2_Cfg.h</td>
</tr>
<tr class="odd">
<td>D_ADC2G2FIFORESETCR_CNT_U32*</td>
<td>Initialization value for adcREG2-&gt;<br />
GxFIFORESETCR[D_GROUP2_CNT_U8]</td>
<td>Adc2_Cfg.h</td>
</tr>
<tr class="even">
<td>D_ADC2G2DMACR_CNT_U32*</td>
<td>Initialization value for adcREG2-&gt;<br />
G0DMACR</td>
<td>Adc2_Cfg.h</td>
</tr>
<tr class="odd">
<td>D_HWTRGADC2GEVT_CNT_LGC*</td>
<td>STD_ON to reconfigure ADC2 event group for hardware trigger after
initial reads; otherwise STD_OFF</td>
<td>Adc2_Cfg.h</td>
</tr>
<tr class="even">
<td>D_HWTRGADC2G1_CNT_LGC*</td>
<td>STD_ON to reconfigure ADC2 group 1 for hardware trigger after
initial reads; otherwise STD_OFF</td>
<td>Adc2_Cfg.h</td>
</tr>
<tr class="odd">
<td>D_HWTRGADC2G2_CNT_LGC*</td>
<td>STD_ON to reconfigure ADC2 group 2 for hardware trigger after
initial reads; otherwise STD_OFF</td>
<td>Adc2_Cfg.h</td>
</tr>
<tr class="even">
<td>D_ADC2USEDMA_CNT_LGC*</td>
<td>STD_ON if using DMA to transfer ADC2 data; otherwise STD_OFF</td>
<td>Adc2_Cfg.h</td>
</tr>
</tbody>
</table>

\*NOTE: See template Adc_Cfg.h and Adc2_Cfg.h files in Tools folder for
settings to maintain pre-DMA (FDD33C rev008 and FDD33E rev002) behavior.

\*\*NOTE: Additional manual configuration constants are needed, and are
included in the template config header files, but are not listed here.
To be added in CR 11738 complete design review of this component.

# Integration

## Required Global Data Inputs

None

## Required Global Data Outputs

ADC1OffsetComp_Cnt_u8p8

ADC2OffsetComp_Cnt_u8p8 (From ADC2 to Current Measurement)

## Specific Include Path present

Yes

# Runnable Scheduling 

This section specifies the required runnable scheduling.

<table>
<colgroup>
<col style="width: 24%" />
<col style="width: 53%" />
<col style="width: 21%" />
</colgroup>
<thead>
<tr class="header">
<th>Init</th>
<th>Scheduling Requirements</th>
<th>Trigger</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Adc_Init()</td>
<td>Before <strong>Adc2_Init1</strong><br />
Before <strong>IoHwAb_Init</strong><br />
After <strong>SystemTime_Init<br />
</strong>After <strong>Dma_Init</strong></td>
<td>ECU Startup</td>
</tr>
<tr class="even">
<td>Adc2_Init1()</td>
<td>Before <strong>PWMCdd_Init</strong><br />
Before enabling Motor Control ISR<br />
After <strong>SystemTime_Init<br />
</strong>After <strong>Dma_Init</strong></td>
<td>ECU Startup</td>
</tr>
</tbody>
</table>

\*NOTE: Depending on configuration, some of the other listed init
functions may not be present. Other application-specific scheduling
requirements may exist.

| Runnable                  | Scheduling Requirements                              | Trigger |
|---------------------|-------------------------------------|---------------|
| Adc_StartGroupConversion  | As determined by application needs and configuration |         |
| Adc2_StartGroupConversion | As determined by application needs and configuration |         |

**.**

# Memory Mapping

## Mapping

| Memory Section          | Contents | Notes |
|-------------------------|----------|-------|
| ADC2_START_SEC_CODE     |          |       |
| ADC2_START_SEC_CONST_32 |          |       |
| ADC_START_SEC_CONST_32  |          |       |
| ADC_START_SEC_CODE      |          |       |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

| Feature                | RAM | ROM |
|------------------------|-----|-----|
| \<Memmap usuage info\> |     |     |

Table 1: ARM Cortex R4 Memory Usage

## Non RTE NvM Blocks

| Block Name                            |
|---------------------------------------|
| \<NVM block used Non RTE functions \> |

Note : Size of the NVM block if configured in developer

##  RTE NvM Blocks

| Block Name                           |
|--------------------------------------|
| \<NVM block used in RTE functions \> |

Note : Size of the NVM block if configured in developer

# Compiler Settings

##  Preprocessor MACRO

\<Define all the preprocessor Macros needed and conditions when
needed\>.

## Optimization Settings

\<Define Optimization levels that are needed and conditions when
needed\>.

##  [section-1]

# Revision Control Log

|            |                                                                                                                                                                                    |           |            |
|-------|--------------------------------------------------|----------|-------|
| **Rev \#** | **Change Description**                                                                                                                                                             | **Date**  | **Author** |
| 1          | Initial version                                                                                                                                                                    | 09-Apr-13 | Selva      |
| 2          | Updated to latest integration manual template. Updated per changes made for use with DMA. Added init function scheduling requirements that had previously been listed in the MDDs. | 11-Apr-14 | KMC        |
| 3          | Updated for ADC offset compensation                                                                                                                                                | 27-Jun-14 | Selva      |

{% endraw %}