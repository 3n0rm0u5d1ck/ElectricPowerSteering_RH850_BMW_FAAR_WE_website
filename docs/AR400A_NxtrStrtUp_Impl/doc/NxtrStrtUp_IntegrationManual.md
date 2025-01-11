---
layout: default
title: NxtrStrtUp_IntegrationManual
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**NxtrStrtUp**

**VERSION: 1**

**DATE: 06/01/17**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**  
Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                 |              |             |          |
|-------------|-----------------|--------------|-------------|----------|
| **Sl. No.** | **Description** | **Author**   | **Version** | **Date** |
| 1           | Initial version | Jared Julien | 1           | 06/01/17 |
|             |                 |              |             |          |
|             |                 |              |             |          |

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

[4.3 DaVinci Parameter Configuration Changes
[7](#davinci-parameter-configuration-changes)](#davinci-parameter-configuration-changes)

[4.4 DaVinci Interrupt Configuration Changes
[7](#davinci-interrupt-configuration-changes)](#davinci-interrupt-configuration-changes)

[4.5 Manual Configuration Changes
[7](#manual-configuration-changes)](#manual-configuration-changes)

[5 Integration DATAFLOW REQUIREMENTS
[8](#integration-dataflow-requirements)](#integration-dataflow-requirements)

[5.1 Required Global Data Inputs
[8](#required-global-data-inputs)](#required-global-data-inputs)

[5.2 Required Global Data Outputs
[8](#required-global-data-outputs)](#required-global-data-outputs)

[5.3 Specific Include Path present
[8](#specific-include-path-present)](#specific-include-path-present)

[6 Runnable Scheduling [9](#runnable-scheduling)](#runnable-scheduling)

[7 Memory Map REQUIREMENTS
[10](#memory-map-requirements)](#memory-map-requirements)

[7.1 Mapping [10](#mapping)](#mapping)

[7.2 Usage [10](#usage)](#usage)

[7.3 NvM Blocks [10](#nvm-blocks)](#nvm-blocks)

[8 Compiler Settings [11](#compiler-settings)](#compiler-settings)

[8.1 Preprocessor MACRO [11](#preprocessor-macro)](#preprocessor-macro)

[8.2 Optimization Settings
[11](#optimization-settings)](#optimization-settings)

[9 Appendix [12](#appendix)](#appendix)

# Abbrevations And Acronyms

| **Abbreviation** | **Description**                         |
|------------------|-----------------------------------------|
| DFD              | Design functional diagram               |
| MDD              | Module design Document                  |
|                  | \<ADD more to the table if applicable\> |
|                  |                                         |
|                  |                                         |

# References

This section lists the title & version of all the documents that are
referred for development of this document

| **Sr. No.** | **Title**                   | **Version**                    |
|-------------|-----------------------------|--------------------------------|
| 1           | MDD Guidelines              | Process 04.00.00               |
| 2           | Software Naming Conventions | Process 04.00.00               |
| 3           | Software Coding Standards   | Process 04.00.00               |
| 4           | AR400A_NxtrStrtUp_Design    | See Synergy subproject version |

# Dependencies

## SWCs

| **Module** | **Required Feature** |
|------------|----------------------|
| **None**   | N/A                  |

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
referred. Developer should track the references.

## Global Functions(Non RTE) to be provided to Integration Project

None

# Configuration REQUIREMeNTS

## Build Time Config

| **Modules** | **Notes** |     |
|-------------|-----------|-----|
| **None**    |           |     |

## Configuration Files to be provided by Integration Project

None

## DaVinci Parameter Configuration Changes

| **Parameter** | **Notes** | **SWC** |
|---------------|-----------|---------|
| **N/A**       |           |         |

## DaVinci Interrupt Configuration Changes

| **ISR Name** | **Interrupt Category (FE/EI)** | **Interrupt Channel Number** | **Priority Dependency** | **Notes** |
|------------|---------|-----------------|--------------------|-----------------|
| **N/A**      |                                |                              |                         |           |

## Manual Configuration Changes

|         | **Notes** | **SWC** |
|---------|-----------|---------|
| **N/A** |           |         |

# Integration DATAFLOW REQUIREMENTS

## Required Global Data Inputs

None

## Required Global Data Outputs

None

## Specific Include Path present

Yes

# Runnable Scheduling 

This section specifies the required runnable scheduling.

| **Init** | **Scheduling Requirements** | **Trigger** |
|----------|-----------------------------|-------------|
| **N/A**  |                             |             |

| **Runnable** | **Scheduling Requirements** | **Trigger** |
|--------------|-----------------------------|-------------|
| **N/A**      |                             |             |

**.**

# Memory Map REQUIREMENTS

## Mapping

| **Memory Section** | **Contents**               | **Notes**                                                                                          |
|---------------|-------------------|--------------------------------------|
| .appstrtvect       | Entry point to application | Must be placed at the location that the bootloader is expected to jump to via linker command file. |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

| **Feature** | **RAM** | **ROM** |
|-------------|---------|---------|
| **N/A**     |         |         |

## NvM Blocks

None

# Compiler Settings

##  Preprocessor MACRO

None

## Optimization Settings

The following option must be specified in the main .gpj project file:

-nostartfiles

This change prevents the use of the Green Hills startup library which
this component replaces.

# Appendix

The following symbols need to be defined in the linker command file for
the project surrounding RAM sections that are to be cleared at init.

| Symbol          | Notes                                                                                                                         |
|--------------|----------------------------------------------------------|
| clearedRamStart | To be placed near the top of RAM, before any \*bss or \*sbss section have been included by the application or OS.             |
| clearedRamEnd   | To be placed near the end of RAM but before the definition of any heap memory and after any and all \*bss or \*sbss sections. |

These symbols are used by the library to denote the beginning and end of
RAM that will be cleared during application init. The intent is to keep
the range as small as possible to optimize startup timing while
including all RAM that is guaranteed to be cleared at init. Due to the
way Nexteer structures their memory map the cleared section may contain
initialized sections (\*data and \*sdata) as well. This will not cause
any functional issues but will hinder performance slightly.

**Caution**: if a variable is outside of the range between these two
symbols its value at init cannot be assured. It is recommended that the
.map file be analyzed once the changes have been integrated and the
project compiles to ensure that there are no variables that fall outside
of this range.

{% endraw %}