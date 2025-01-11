---
layout: default
title: PullCmpActv_IntegrationManual
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**Active Pull Compensation**

**VERSION:2.0**

**DATE:** **22-DEC-2017**

**Prepared By:**

**Krishna Anne**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                 |              |             |            |
|-------------|-----------------|--------------|-------------|------------|
| **Sl. No.** | **Description** | **Author**   | **Version** | **Date**   |
| 1           | Initial version | TATA         | 1.0         | 10/16/2015 |
| 2           | Added FltInj    | Krishna Anne | 2.0         | 12/22/2017 |

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
7](#__RefHeading___Toc389222325)

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

[7.3 Non RTE NvM Blocks 10](#nvm-blocks)

[7.4 RTE NvM Blocks 10](#__RefHeading___Toc389222336)

[8 Compiler Settings 11](#compiler-settings)

[8.1 Preprocessor MACRO 11](#preprocessor-macro)

[8.2 Optimization Settings 11](#optimization-settings)

[9 Appendix 12](#appendix)

# Abbrevations And Acronyms

|                  |                                         |
|------------------|-----------------------------------------|
| **Abbreviation** | **Description**                         |
| DFD              | Design functional diagram               |
| MDD              | Module design Document                  |
|                  | \<ADD more to the table if applicable\> |
|                  |                                         |
|                  |                                         |

# References

This section lists the title & version of all the documents that are
referred for development of this document

|             |                                      |                                 |
|----------|----------------------------------------------|-----------------|
| **Sr. No.** | **Title**                            | **Version**                     |
| 1           | FDD : SF013A_PullCmpActv_Design      | See Synergy sub project version |
| 2           | Software Naming Conventions          | Process 4.02.00                 |
| 3           | Software Design and Coding Standards | Process 4.02.00                 |

# Dependencies

## SWCs

|            |                      |
|------------|----------------------|
| **Module** | **Required Feature** |
| **None**   | N/A                  |

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
referred. Developer should track the references.

## Global Functions(Non RTE) to be provided to Integration Project

None

# Configuration REQUIREMeNTS

## Build Time Config

|               |                                     |     |
|---------------|-------------------------------------|-----|
| **Modules**   | **Notes**                           |     |
| **FLTINJENA** | Set to ‘STD_ON’ for fault injection |     |

## Configuration Files to be provided by Integration Project

\<Configuration file that will generated from this components that will
require Da Vinci Config generation or manual generation. Describe each
parameter \>

## Da Vinci Parameter Configuration Changes

|               |           |         |
|---------------|-----------|---------|
| **Parameter** | **Notes** | **SWC** |
| **None**      |           |         |

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

Refer DataDict.m file.

## Required Global Data Outputs

Refer DataDict.m file.

## Specific Include Path present

No

# Runnable Scheduling 

This section specifies the required runnable scheduling.

|                      |                             |             |
|----------------------|-----------------------------|-------------|
| **Init**             | **Scheduling Requirements** | **Trigger** |
| **PullCmpActvInit1** | None                        | RTE(Init)   |

|                             |                             |              |
|-----------------------------|-----------------------------|--------------|
| **Runnable**                | **Scheduling Requirements** | **Trigger**  |
| **PullCmpActvPer1**         | None                        | RTE (2 ms)   |
| **PullCmpActvPer2**         | None                        | RTE (100 ms) |
| **GetPullCmpPrm_Oper**      | None                        | On event     |
| **SetPullCmpLongTerm_Oper** | None                        | On event     |
| **SetPullCmpShoTerm_Oper**  | None                        | On event     |
| **RstPullCmp_Oper**         | None                        | On event     |

# Memory Map REQUIREMENTS

## Mapping

|                    |              |           |
|--------------------|--------------|-----------|
| **Memory Section** | **Contents** | **Notes** |
| **None**           |              |           |
|                    |              |           |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

|             |         |         |
|-------------|---------|---------|
| **Feature** | **RAM** | **ROM** |
| **None**    |         |         |

Table 1: ARM Cortex R4 Memory Usage

## NvM Blocks

## RTE NvM Blocks

|                     |
|---------------------|
| **Block Name**      |
| **PullCmpLongTerm** |

# Compiler Settings

##  Preprocessor MACRO

None

## Optimization Settings

None

# Appendix

None

{% endraw %}