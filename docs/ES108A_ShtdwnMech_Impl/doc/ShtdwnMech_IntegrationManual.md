---
layout: default
title: ShtdwnMech_IntegrationManual
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**ShtdwnMech**

**VERSION: 1.0**

**DATE: 21-Mar-2017**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**  
Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                 |             |             |             |
|-------------|-----------------|-------------|-------------|-------------|
| **Sl. No.** | **Description** | **Author**  | **Version** | **Date**    |
| 1           | Initial version | M. Bartocha | 1.0         | 21-Mar-2017 |

: ARM Cortex R4 Memory Usage

**<u>  
Table of Contents</u>**

[1 Abbrevations And Acronyms
[4](#abbrevations-and-acronyms)](#abbrevations-and-acronyms)

[2 References [5](#references)](#references)

[3 Dependencies [6](#dependencies)](#dependencies)

[3.1 SWCs [6](#swcs)](#swcs)

[3.2 Global Functions(Non RTE) to be provided to Integration Project
[6](#global-functionsnon-rte-to-be-provided-to-integration-project)](#global-functionsnon-rte-to-be-provided-to-integration-project)

[4 Configuration REQUIREMeNTS
[7](#configuration-requirements)](#configuration-requirements)

[4.1 Build Time Config [7](#build-time-config)](#build-time-config)

[4.2 Configuration Files to be provided by Integration Project
[7](#configuration-files-to-be-provided-by-integration-project)](#configuration-files-to-be-provided-by-integration-project)

[4.3 Da Vinci Parameter Configuration Changes
[7](#da-vinci-parameter-configuration-changes)](#da-vinci-parameter-configuration-changes)

[4.4 DaVinci Interrupt Configuration Changes
[7](#davinci-interrupt-configuration-changes)](#davinci-interrupt-configuration-changes)

[4.5 Manual Configuration Changes
[7](#manual-configuration-changes)](#manual-configuration-changes)

[5 Integration DATAFLOW REQUIREMENTS
[8](#integration-dataflow-requirements)](#integration-dataflow-requirements)

[5.1 Required Global Data Inputs
[8](#required-global-data-inputs)](#required-global-data-inputs)

[5.2 Required Global Data Outputs [8](#_Toc389222329)](#_Toc389222329)

[5.3 Specific Include Path present [8](#_Toc357692829)](#_Toc357692829)

[6 Runnable Scheduling [9](#runnable-scheduling)](#runnable-scheduling)

[7 Memory Map REQUIREMENTS
[10](#memory-map-requirements)](#memory-map-requirements)

[7.1 Mapping [10](#mapping)](#mapping)

[7.2 Usage [10](#usage)](#usage)

[7.3 Non RTE NvM Blocks [10](#nvm-blocks)](#nvm-blocks)

[7.4 RTE NvM Blocks [10](#_Toc389222336)](#_Toc389222336)

[8 Compiler Settings [11](#_Toc357692835)](#_Toc357692835)

[8.1 Preprocessor MACRO [11](#preprocessor-macro)](#preprocessor-macro)

[8.2 Optimization Settings
[11](#optimization-settings)](#optimization-settings)

[9 Appendix [12](#appendix)](#appendix)

# Abbrevations And Acronyms

| **Abbreviation** | **Description**            |
|------------------|----------------------------|
| DFD              | Design functional diagram  |
| MDD              | Module design Document     |
| FDD              | Functional Design Document |

# References

This section lists the title & version of all the documents that are
referred for development of this document

| **Sr. No.** | **Title**                   | **Version**                    |
|-------------|-----------------------------|--------------------------------|
| 1           | FDD – ES108A ShtdwnMech     | See Synergy subproject version |
| 2           | Software Naming Conventions | Process 04.02.01               |
| 3           | Software Coding Standards   | Process 04.02.01               |

# Dependencies

## SWCs

| **Module**            | **Required Feature**          |
|-----------------------|-------------------------------|
| **ES999A_ElecGlbPrm** | StrtUpState Threshold defines |

## Global Functions(Non RTE) to be provided to Integration Project

*None*

# Configuration REQUIREMeNTS

## Build Time Config

| **Modules** | **Notes** |     |
|-------------|-----------|-----|
| **None**    |           |     |

## Configuration Files to be provided by Integration Project

*None*

## Da Vinci Parameter Configuration Changes

| **Parameter** | **Notes** | **SWC** |
|---------------|-----------|---------|
| **None**      |           |         |

## DaVinci Interrupt Configuration Changes

| **ISR Name** | **VIM \#** | **Priority Dependency** | **Notes** |
|--------------|------------|-------------------------|-----------|
| **None**     |            |                         |           |

## Manual Configuration Changes

| **Constant** | **Notes** | **SWC** |
|--------------|-----------|---------|
| **None**     |           |         |

# Integration DATAFLOW REQUIREMENTS

## Required Global Data Inputs

<span id="_Toc389222329" class="anchor"></span>Refer DataDict.m file

## Required Global Data Outputs

<span id="_Toc357692829" class="anchor"></span>Refer DataDict.m file

## Specific Include Path present

NO

# Runnable Scheduling 

This section specifies the required runnable scheduling.

| **Init**            | **Scheduling Requirements** | **Trigger** |
|---------------------|-----------------------------|-------------|
| **ShtdwnMechInit1** | None                        | RTE Init    |

| **Runnable**       | **Scheduling Requirements** | **Trigger** |
|--------------------|-----------------------------|-------------|
| **ShtdwnMechPer1** | None                        | RTE(2ms)    |

# Memory Map REQUIREMENTS

## Mapping

| **Memory Section**            | **Contents** | **Notes** |
|-------------------------------|--------------|-----------|
| **ShtdwnMech_START_SEC_CODE** |              |           |
|                               |              |           |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

| **Feature**                | **RAM** | **ROM** |
|----------------------------|---------|---------|
| **\<Memmap usuage info\>** |         |         |

## NvM Blocks

<span id="_Toc357692835" class="anchor"></span>*None*

#  Compiler Settings

##  Preprocessor MACRO

*None*

## Optimization Settings

*None*

# Appendix

*\<This section is for appendix\>*

{% endraw %}