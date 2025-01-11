---
layout: default
title: CmnMfgSrvIf_IntegrationManual
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**CmnMfgSrvIf**

**VERSION: 1.0**

**DATE: 5-Jan-2018**

**Prepared By:**

**Jared Julien,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                 |              |             |            |
|-------------|-----------------|--------------|-------------|------------|
| **Sl. No.** | **Description** | **Author**   | **Version** | **Date**   |
| 1           | Initial version | Jared Julien | 1.0         | 2-Feb-2018 |

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

[7.2 Usage [10](#usage)](#usage)

[7.3 NvM Blocks [10](#nvm-blocks)](#nvm-blocks)

[8 Compiler Settings [11](#compiler-settings)](#compiler-settings)

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

| **Sr. No.** | **Title**                      | **Version**                       |
|----------|----------------------------------------------|-----------------|
| 1           | MDD Guidelines                 | Software Process Release 04.02.01 |
| 2           | Software Naming Conventions    | Software Process Release 04.02.01 |
| 3           | Design and Coding Standards    | Software Process Release 04.02.01 |
| 4           | FDD: NM002C_CmnMfgSrvIf_Design | See Synergy subproject version    |

# Dependencies

## SWCs

| **Module** | **Required Feature** |
|------------|----------------------|
| **None**   |                      |

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
referred. Developer should track the references.

## Global Functions(Non RTE) to be provided to Integration Project

> Many global functions are generated by this component during
> integration, however, none of them are prodided by static code within
> this component. See appendix for additional information.

# Configuration REQUIREMeNTS

## Build Time Config

| **Modules** | **Notes** |     |
|-------------|-----------|-----|
| **None**    |           |     |

## Configuration Files to be provided by Integration Project

> None

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

None

## Required Global Data Outputs

None

## Specific Include Path present

No

# Runnable Scheduling 

This section specifies the required runnable scheduling.

| **Init** | **Scheduling Requirements** | **Trigger** |
|----------|-----------------------------|-------------|
| **None** | None                        | N/A         |

| **Runnable** | **Scheduling Requirements** | **Trigger** |
|--------------|-----------------------------|-------------|
| **None**     | None                        | N/A         |

# Memory Map REQUIREMENTS

## Mapping

| **Memory Section**             | **Contents** | **Notes** |
|--------------------------------|--------------|-----------|
| **CmnMfgSrvIf_START_SEC_CODE** |              |           |
|                                |              |           |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

| **Feature** | **RAM** | **ROM** |
|-------------|---------|---------|
| **None**    |         |         |

Table 1: ARM Cortex R4 Memory Usage

## NvM Blocks

None

# Compiler Settings

##  Preprocessor MACRO

None

## Optimization Settings

None

# Appendix

This component is primarily used to generate a configuration source file
that provides all of it’s functionality. The purpose of this component
is to bridge the gap between the AUTOSAR DCM and NM001A (common
manufacturing services). To accomplish this, the component produces
two[^1] outputs when generation is invoked through Configurator by an
integrator, a .c source file and an .arxml config file, both located in
the generate folder of the integration project.

The .arxml file is titled CmnMfgSrvIf_DemCfg.arxml. The file contains
the necessary DCM settings for Nexteer services **only**. The integrator
must manually merge these settings with their DCM settings being sure to
include any additional or changed services with CmnMfgSrvIf in the name
while retaining all of their exisiting customer service configurations.
The integrator should be especially careful with the removal section as
Configurator will suggest “removal” of any setting that is not defined
in the generated ARXML file but is present in the project. This includes
customer services as well as general DCM settings. As a general rule of
thumb it is safe to remove anything with CmnMfgSrvIf in the name.

The .c file requires nothing from the integrator. During the initial
integration it must be added to the corresponding generate.gpj file for
the project but once that is complete and on every subsequent update no
action needs to be taken.

This component takes only a single input in the form of an ODX file
containing a list of all Nexteer manufacturing services that are enabled
for the program. This file, titled EnadMfgSrv.odx-d, is expected to be
located in the typical location in the generate folder of the
integration project. Because this component uses this file and the file
is generated during the integration of NM001A of NM010x this component
**should be regenerated AFTER making changes to NM001A or NM010x.**

A DataDict.m file is generated in addition to the source and ARXML
files. This file is not needed by the integration project or integrator.
It is generated to be provided to the software architecture team for use
with creating a system architecture specific to the project.

[^1]: Additionally, a DataDict.m file is also generated but for purposes
    of integration is not considered “functional”.

{% endraw %}