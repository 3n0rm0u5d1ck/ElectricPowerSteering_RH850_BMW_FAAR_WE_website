---
layout: default
title: McalErrHndlg_IntegrationManual
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**McalErrHndlg**

**VERSION: 1**

**DATE: 5-30-2017**

**Prepared By:**

**Jared Julien,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**  
Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                 |            |             |          |                 |
|----|---------------|---------------|-------|----------------|----------------|
| **Sl. No.** | **Description** | **Author** | **Version** | **Date** | **Approved By** |
| 1           | Initial version | J. Julien  | 1.0         | \-       | \-              |

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

[5.2 Required Global Data Outputs
[8](#required-global-data-outputs)](#required-global-data-outputs)

[5.3 Specific Include Path present
[8](#specific-include-path-present)](#specific-include-path-present)

[6 Runnable Scheduling [9](#runnable-scheduling)](#runnable-scheduling)

[7 Memory Map REQUIREMENTS
[10](#memory-map-requirements)](#memory-map-requirements)

[7.1 Mapping [10](#mapping)](#mapping)

[7.2 NvM Blocks [10](#nvm-blocks)](#nvm-blocks)

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
| 4           | AR099A_McalErrHndlg_Design  | See Synergy subproject version |

# Dependencies

## SWCs

| **Module** | **Required Feature** |
|------------|----------------------|
| **None**   | N/A                  |

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
referred. Developer should track the references.

## Global Functions(Non RTE) to be provided to Integration Project

HndlMcalWrVrfyErr

Fls_CallSwitchBFlashErrorNotification

HndlMcalDemErr

# Configuration REQUIREMeNTS

## Build Time Config

| **Modules** | **Notes** |     |
|-------------|-----------|-----|
| **None**    |           |     |

## Configuration Files to be provided by Integration Project

## Da Vinci Parameter Configuration Changes

| **Parameter**                                                            | **Value**         | **SWC** |
|--------------------------------------------------|----------------|------|
| /Renesas/EcucDefs_Dio/Dio/DioGeneral/DioWriteVerifyErrorInterface        | HndlMcalWrVrfyErr | Dio     |
| /Renesas/EcucDefs_Fls/Fls/FlsGeneral/FlsWriteVerifyErrorInterface        | HndlMcalWrVrfyErr | Fls     |
| /Renesas/EcucDefs_Mcu/Mcu/McuGeneralConfiguration/McuWVErrorNotification | HndlMcalWrVrfyErr | Mcu     |
| /Renesas/EcucDefs_Port/Port/PortGeneral/PortWriteVerifyErrorInterface    | HndlMcalWrVrfyErr | Port    |
| /Renesas/EcucDefs_Spi/Spi/SpiGeneral/SpiWriteVerifyErrorInterface        | HndlMcalWrVrfyErr | Spi     |
| /Renesas/DriverA/Wdg/WdgGeneral/WdgWriteVerifyErrorInterface             | HndlMcalWrVrfyErr | Wdg     |

## DaVinci Interrupt Configuration Changes

| **ISR Name** | **VIM \#** | **Priority Dependency** | **Notes** |
|--------------|------------|-------------------------|-----------|
| **N/A**      |            |                         |           |

## Manual Configuration Changes

| **Constant** | **Notes** | **SWC** |
|--------------|-----------|---------|
| **N/A**      |           |         |

# Integration DATAFLOW REQUIREMENTS

## Required Global Data Inputs

None

## Required Global Data Outputs

None

## Specific Include Path present

Yes

# Runnable Scheduling 

This section specifies the required runnable scheduling.

| **Init**              | **Scheduling Requirements** | **Trigger** |
|-----------------------|-----------------------------|-------------|
| **McalErrHndlgInit1** | None                        | RTE         |

| **Runnable**         | **Scheduling Requirements** | **Trigger** |
|----------------------|-----------------------------|-------------|
| **McalErrHndlgPer1** | None                        | 10 ms       |

**.**

# Memory Map REQUIREMENTS

## Mapping

| **Memory Section**                 | **Contents** | **Notes**                              |
|--------------------------------|------------|-----------------------------|
| **McalErrHndlg_START_SEC_RAMCODE** | Functions    | Must be mapped to executable **RAM\*** |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

\*See Fls module integration manual for more information on setting up
this special RAM section.

## NvM Blocks

\*See DataDict.m

# Compiler Settings

##  Preprocessor MACRO

None

## Optimization Settings

N/A

# Appendix

## Memory Mapping Changes for MCAL DEM error reporting redirect [memory-mapping-changes-for-mcal-dem-error-reporting-redirect]

The MemMap.h of the integration project needs to include some special
definitions for capture the error reporting from the MCAL components
Fls, Mcu, and Spi to the DEM. This is accomplished by adding the
following definition into the MemMap section definitions for the module.

\#include "McalErrHndlg.h"

\#define Dem_ReportErrorStatus HndlMcalDemErr

The sections into which the above definition must be placed are listed
below:

-   MCU_START_SEC_PRIVATE_CODE

-   SPI_START_SEC_CODE_FAST

-   FLS_START_SEC_PRIVATE_CODE

And a corresponding undefine needs to be placed in the corresponding
STOP sections as follows:

\#undef Dem_ReportErrorStatus

In the following sections:

-   MCU_STOP_SEC_PRIVATE_CODE

-   SPI_STOP_SEC_CODE_FAST

-   FLS_STOP_SEC_PRIVATE_CODE

{% endraw %}