---
layout: default
title: BattRtnCurr_IntegrationManual
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**BattRtnCurr**

**VERSION: 2.0**

**DATE:** **11-Oct-2017**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                                               |                  |             |             |
|-----|----------------------|------------------|---------|--------------------|
| **Sl. No.** | **Description**                               | **Author**       | **Version** | **Date**    |
| 1           | Initial version                               | Krzysztof Byrski | 1.0         | 21-Jul-2017 |
| 2           | Updated DaVinci Configuration parameters list | Krzysztof Byrski | 2.0         | 11-Oct-2017 |

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

|                  |                            |
|------------------|----------------------------|
| **Abbreviation** | **Description**            |
| DFD              | Design functional diagram  |
| MDD              | Module design Document     |
| FDD              | Functional Design Document |

# References

This section lists the title & version of all the documents that are
referred for development of this document

|             |                                      |                                 |
|----------|----------------------------------------------|-----------------|
| **Sr. No.** | **Title**                            | **Version**                     |
| 1           | EA4 Software Naming Conventions      | 01.01.00                        |
| 2           | Software Design and Coding Standards | 2.1                             |
| 3           | ES251A_BattRtnCurr_Design            | See Synergy Sub Project Version |

# Dependencies

## SWCs

|            |                      |
|------------|----------------------|
| **Module** | **Required Feature** |
| **None**   | \-                   |

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
referred. Developer should track the references.

## Global Functions(Non RTE) to be provided to Integration Project

-   BattRtnCurrPer1

# Configuration REQUIREMeNTS

## Build Time Config

|                                       |                            |     |
|---------------------------------------|----------------------------|-----|
| **Modules**                           | **Notes**                  |     |
| **BATTRTNCURR_FASTLOOPPROC_CNT_LOGL** | Takes values TRUE or FALSE |     |

## Configuration Files to be provided by Integration Project

CDD_BattRtnCurr_Cfg.h

## Da Vinci Parameter Configuration Changes

|                                          |                       |                    |
|-----------------------------------|----------------------|---------------|
| **Parameter**                            | **Notes**             | **SWC**            |
| **BATTRTNCURR_CURRESTIMDIFTHD_AMPR_F32** | CDD_BattRtnCurr_Cfg.h | ES251A_BattRtnCurr |
| **BATTRTNCURR_FAILSTEP_CNT_U16**         | CDD_BattRtnCurr_Cfg.h | ES251A_BattRtnCurr |
| **BATTRTNCURR_PASSSTEP_CNT_U16**         | CDD_BattRtnCurr_Cfg.h | ES251A_BattRtnCurr |
| **BATTRTNCURR_FASTLOOPPROC_CNT_LOGL**    | CDD_BattRtnCurr_Cfg.h | ES251A_BattRtnCurr |
| **BATTRTNCURR_FILCUTFREQ_HZ_F32**        | CDD_BattRtnCurr_Cfg.h | ES251A_BattRtnCurr |
| **BATTRTNCURR_GAIN_AMPRPERVOLT_F32**     | CDD_BattRtnCurr_Cfg.h | ES251A_BattRtnCurr |
| **BATTRTNCURR_LOWRTHD_AMPR_F32**         | CDD_BattRtnCurr_Cfg.h | ES251A_BattRtnCurr |
| **BATTRTNCURR_OFFSET_VOLT_F32**          | CDD_BattRtnCurr_Cfg.h | ES251A_BattRtnCurr |
| **BATTRTNCURR_OUTPMAX_AMPR_F32**         | CDD_BattRtnCurr_Cfg.h | ES251A_BattRtnCurr |
| **BATTRTNCURR_OUTPMIN_AMPR_F32**         | CDD_BattRtnCurr_Cfg.h | ES251A_BattRtnCurr |
| **BATTRTNCURR_UPPRTHD_AMPR_F32**         | CDD_BattRtnCurr_Cfg.h | ES251A_BattRtnCurr |

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

See FDD DataDict.m

## Required Global Data Outputs

See FDD DataDict.m

## Specific Include Path present

Yes

# Runnable Scheduling 

This section specifies the required runnable scheduling.

|                      |                             |             |
|----------------------|-----------------------------|-------------|
| **Init**             | **Scheduling Requirements** | **Trigger** |
| **BattRtnCurrInit1** | None                        | RTE(Init)   |

|                     |                             |                      |
|---------------------|-----------------------------|----------------------|
| **Runnable**        | **Scheduling Requirements** | **Trigger**          |
| **BattRtnCurrPer1** | None                        | ISR(2 \* MtrCtrlISR) |
| **BattRtnCurrPer2** | None                        | RTE(2ms)             |

**.**

# Memory Map REQUIREMENTS

## Mapping

|                                            |              |           |
|--------------------------------------------|--------------|-----------|
| **Memory Section**                         | **Contents** | **Notes** |
| **CDD_BattRtnCurr_START_SEC_CODE**         | Code         |           |
| **CDD_BattRtnCurr_MotCtrl_START_SEC_CODE** | Code         |           |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

|             |         |         |
|-------------|---------|---------|
| **Feature** | **RAM** | **ROM** |
| **None**    |         |         |

Table 1: ARM Cortex R4 Memory Usage

## NvM Blocks

\*See DataDict.m

# Compiler Settings

##  Preprocessor MACRO

None

## Optimization Settings

None

# Appendix

None

{% endraw %}