---
layout: default
title: GateDrv0Ctrl_IntegrationManual
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**Gate Drive 0 Control**

**VERSION:** **3**

**DATE:** **11-Sep-2017**

**Prepared By:**

**Shruthi Raghavan,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                                           |                  |              |
|---------|------------------------------------|-----------------|------------|
| **Version** | **Description**                           | **Author**       | **Date**     |
| 1           | Initial version                           | Rijvi Ahmed      | 08-July-2016 |
| 2           | Updated for SPI MCAL update in FDD v2.2.0 | Shruthi Raghavan | 15-Mar-2017  |
| 3           | Details of new config parameter added.    | Shruthi Raghavan | 11-Sep-2017  |

Table of Contents

[1 Abbrevations And Acronyms 4](#abbrevations-and-acronyms)

[2 References 5](#references)

[3 Dependencies 6](#dependencies)

[3.1 SWCs 6](#swcs)

[3.2 Global Functions(Non RTE) to be provided to Integration Project
6](#global-functionsnon-rte-to-be-provided-to-integration-project)

[4 Configuration REQUIREMeNTS 7](#configuration-requirements)

[4.1 Build Time Config 7](#build-time-config)

[4.2 Configuration Files to be provided by Integration Project
7](#configuration-files-to-be-provided-by-integration-project)

[4.3 Da Vinci Parameter Configuration Changes
7](#da-vinci-parameter-configuration-changes)

[4.4 DaVinci Interrupt Configuration Changes
7](#davinci-interrupt-configuration-changes)

[4.5 Manual Configuration Changes 7](#manual-configuration-changes)

[5 Integration DATAFLOW REQUIREMENTS
8](#integration-dataflow-requirements)

[5.1 Required Global Data Inputs 8](#required-global-data-inputs)

[5.2 Required Global Data Outputs 8](#required-global-data-outputs)

[5.3 Specific Include Path present 8](#specific-include-path-present)

[6 Runnable Scheduling 9](#runnable-scheduling)

[7 Memory Map REQUIREMENTS 10](#memory-map-requirements)

[7.1 Mapping 10](#mapping)

[7.2 Usage 10](#usage)

[7.3 Non RTE NvM Blocks 10](#non-rte-nvm-blocks)

[7.4 RTE NvM Blocks 10](#rte-nvm-blocks)

[8 Compiler Settings 11](#compiler-settings)

[8.1 Preprocessor MACRO 11](#preprocessor-macro)

[8.2 Optimization Settings 11](#optimization-settings)

# Abbrevations And Acronyms

|                  |                           |
|------------------|---------------------------|
| **Abbreviation** | **Description**           |
| DFD              | Design functional diagram |
| MDD              | Module design Document    |

# References

This section lists the title & version of all the documents that are
referred for development of this document

|             |                             |                                 |
|----------|----------------------------------------------|-----------------|
| **Sr. No.** | **Title**                   | **Version**                     |
| 1           | Software Naming Conventions | Process 04.04.02                |
| 2           | Software Coding Standards   | Process 04.04.02                |
| 3           | FDD – ES311A GateDrv0Ctrl   | See synergy sub project version |

# Dependencies

## SWCs

|                                     |                      |
|-------------------------------------|----------------------|
| **Module**                          | **Required Feature** |
| **Spi_Renesas_Ar4.0.3_01.06.05_HF** |                      |

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
referred. Developer should track the references.

## Global Functions(Non RTE) to be provided to Integration Project

None

# Configuration REQUIREMeNTS

## Build Time Config

|             |           |     |
|-------------|-----------|-----|
| **Modules** | **Notes** |     |
| **None**    |           |     |

## Configuration Files to be provided by Integration Project

None

## Da Vinci Parameter Configuration Changes

<table style="width:100%;">
<colgroup>
<col style="width: 42%" />
<col style="width: 43%" />
<col style="width: 14%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Parameter</strong></td>
<td><strong>Notes</strong></td>
<td><strong>SWC</strong></td>
</tr>
<tr class="even">
<td><p>/Nexteer/GateDrv0Ctrl/GateDrv0CtrlGenCfg/</p>
<p>GateDrv0FetFltMtgtnEna</p></td>
<td><p>GATEDRV0FETFLTMTGTNENA_ULS_LOGL:</p>
<p>Field effect transistor fault mitigation enable.</p>
<p>If TRUE, the gate drive component will notify the system when a FET
fault is detected.</p></td>
<td>GateDrv0Ctrl</td>
</tr>
</tbody>
</table>

## DaVinci Interrupt Configuration Changes

|              |            |                         |           |
|--------------|------------|-------------------------|-----------|
| **ISR Name** | **VIM \#** | **Priority Dependency** | **Notes** |
| **None**     |            |                         |           |

## Manual Configuration Changes

|              |           |         |
|--------------|-----------|---------|
| **Constant** | **Notes** | **SWC** |
| **None**     |           |         |

# Integration DATAFLOW REQUIREMENTS

## Required Global Data Inputs

See FDD DataDict.m.

## Required Global Data Outputs

See FDD DataDict.m.

## Specific Include Path present

No

# Runnable Scheduling 

This section specifies the required runnable scheduling.

|                       |                             |             |
|-----------------------|-----------------------------|-------------|
| **Init**              | **Scheduling Requirements** | **Trigger** |
| **GateDrv0CtrlInit1** | None                        | RTE (Init)  |

|                      |                                                        |             |
|-------------------|---------------------------------------|---------------|
| **Runnable**         | **Scheduling Requirements**                            | **Trigger** |
| **GateDrv0CtrlPer1** | At the beginning of all 2ms Tasks as close as possible | RTE (2 ms)  |
| **GateDrv0CtrlPer2** | At the end of all 2ms Tasks as close as possible       | RTE (2 ms)  |

# Memory Map REQUIREMENTS

## Mapping

|                       |              |           |
|-----------------------|--------------|-----------|
| **Memory Section \*** | **Contents** | **Notes** |
| **None**              |              |           |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

|             |         |         |
|-------------|---------|---------|
| **Feature** | **RAM** | **ROM** |
| **None**    |         |         |

## Non RTE NvM Blocks

|                |
|----------------|
| **Block Name** |
| **None**       |

Note : Size of the NVM block if configured in configurator

##  RTE NvM Blocks

|                |
|----------------|
| **Block Name** |
| **None**       |

Note : Size of the NVM block if configured in developer

# Compiler Settings

##  Preprocessor MACRO

None

## Optimization Settings

None

{% endraw %}