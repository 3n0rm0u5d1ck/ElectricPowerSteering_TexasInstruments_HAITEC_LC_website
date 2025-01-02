---
layout: default
title: NxtrLib_Systemtime Integration_Manual
nav_order: 4
parent: Nexteer Library
---
{% raw %}
# Contents [contents]

[1 Dependencies [1](#dependencies)](#dependencies)

[2 Configuration [1](#configuration)](#configuration)

[2.1 Build Time Config [1](#build-time-config)](#build-time-config)

[2.2 Generator Config [1](#generator-config)](#generator-config)

[2.2.1 System [1](#system)](#system)

[2.2.2 NvMProxyBlock [2](#_Toc338318475)](#_Toc338318475)

[3 Integration [2](#integration)](#integration)

[4 Runnable Scheduling [2](#runnable-scheduling)](#runnable-scheduling)

[5 Memory Mapping [3](#memory-mapping)](#memory-mapping)

[5.1 Mapping [3](#mapping)](#mapping)

[5.2 Usage [3](#usage)](#usage)

[6 Revision Control Log
[4](#revision-control-log)](#revision-control-log)

# Dependencies

| Module | Required Feature |
|--------|------------------|
|        |                  |

# Configuration

## Build Time Config

| Constant | Notes | SWC |
|----------|-------|-----|
|          |       |     |

## Generator Config

### System

| Constant | Notes | SWC |
|----------|-------|-----|
|          |       |     |

# Integration

The following import steps must be completed:

1.  Place CBD project structure to appropriate integration folder

2.  Copy SystemTime_Cfg.h.tt into the Header folder and remove the .tt
    extension.

3.  Configure the constant D_TickRate_Cnt_u32 to the appropriate Os
    system tick time.

# Runnable Scheduling

This section specifies the required runnable scheduling.

| Runnable | Scheduling Requirements | Trigger |
|----------|-------------------------|---------|
|          |                         |         |

# Memory Mapping

## Mapping

| Constant | Notes |
|----------|-------|
|          |       |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

| Feature     | RAM | ROM |
|-------------|-----|-----|
| Full driver |     |     |

Table 1: ARM Cortex R4 Memory Usage

# Revision Control Log

| **Item \#** | **Rev \#** | **Change Description** | **Date** | **Author Initials** |
|------|------|--------------------------------------------|---------|---------|
| 1           |            | Initial version        | 26Jul13  | SAH                 |

{% endraw %}