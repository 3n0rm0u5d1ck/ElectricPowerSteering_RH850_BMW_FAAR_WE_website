---
layout: default
title: MicroCtrlrSuprt Integration Manual
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**MicroCtrlrSuprt**

**VERSION: 1**

**DATE: 07/19/17**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                 |                |             |          |
|-------------|-----------------|----------------|-------------|----------|
| **Sl. No.** | **Description** | **Author**     | **Version** | **Date** |
| 1           | Initial version | Lucas Wendling | 1           | 07/19/17 |

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

|                  |                 |
|------------------|-----------------|
| **Abbreviation** | **Description** |
|                  |                 |
|                  |                 |
|                  |                 |

# References

This section lists the title & version of all the documents that are
referred for development of this document

|             |           |             |
|-------------|-----------|-------------|
| **Sr. No.** | **Title** | **Version** |
|             |           |             |

# Dependencies

This component is dependant on the v800_ghs.h compiler header file for
definition of some compiler intrinsic functions.

## SWCs

|            |                      |
|------------|----------------------|
| **Module** | **Required Feature** |
|            |                      |

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
referred. Developer should track the references.

## Global Functions(Non RTE) to be provided to Integration Project

This component provides the following inline functions in
NxtrMcuSuprtLib.h for use as needed in components and integration
project. Note that the exact API for usage can be found in the header
file.

For P1M devices:

|                            |                                                                                              |
|-----------------------|-------------------------------------------------|
| **Function Name**          | **Description**                                                                              |
| **WrProtdRegPortJ_u32**    | Protected Register write sequence for 32bit PortJ peripheral registers                       |
| **WrProtdRegPort0_u32**    | Protected Register write sequence for 32bit Port0 peripheral registers                       |
| **WrProtdRegPort1_u32**    | Protected Register write sequence for 32bit Port1 peripheral registers                       |
| **WrProtdRegPort2_u32**    | Protected Register write sequence for 32bit Port2 peripheral registers                       |
| **WrProtdRegPort3_u32**    | Protected Register write sequence for 32bit Port3 peripheral registers                       |
| **WrProtdRegPort4_u32**    | Protected Register write sequence for 32bit Port4 peripheral registers                       |
| **WrProtdRegPort5_u32**    | Protected Register write sequence for 32bit Port5 peripheral registers                       |
| **WrProtdRegSys_u08**      | Protected Register write sequence for 8bit Sys peripheral registers                          |
| **WrProtdRegSys_u32**      | Protected Register write sequence for 32bit Sys peripheral registers                         |
| **WrProtdRegSysClmac_u32** | Protected Register write sequence for 32bit Clmac peripheral registers                       |
| **WrProtdRegClma0_u08**    | Protected Register write sequence for 8bit Clma0 peripheral registers                        |
| **WrProtdRegClma1_u08**    | Protected Register write sequence for 8bit Clma1 peripheral registers                        |
| **WrProtdRegClma2_u08**    | Protected Register write sequence for 8bit Clma2 peripheral registers                        |
| **WrProtdRegClma3_u08**    | Protected Register write sequence for 8bit Clma3 peripheral registers                        |
| **WrProtdRegEcmm_u08**     | Protected Register write sequence for 8bit Ecmm peripheral registers                         |
| **WrProtdRegEcmc_u08**     | Protected Register write sequence for 8bit Ecmc peripheral registers                         |
| **WrProtdRegEcm_u08**      | Protected Register write sequence for 8bit Ecm peripheral registers                          |
| **WrProtdRegEcm_u16**      | Protected Register write sequence for 16bit Ecm peripheral registers                         |
| **WrProtdRegEcm_u32**      | Protected Register write sequence for 32bit Ecm peripheral registers                         |
| **WrProtdRegFlmd_u32**     | Protected Register write sequence for 32bit Flmd peripheral registers                        |
| **NxtrSwRst**              | API to issue a Nexteer Defined Software Reset                                                |
| **NxtrSwRstFromExcpn**     | API to issue a Nexteer Defined Software Reset for resetting from a hardware exception source |

For P1XC devices:

|                         |                                                                                              |
|-----------------------|-------------------------------------------------|
| **Function Name**       | **Description**                                                                              |
| **WrProtdRegEcmm0_u32** | Protected Register write sequence for 32bit Ecmm0 peripheral registers                       |
| **WrProtdRegEcmc0_u32** | Protected Register write sequence for 32bit Ecmc0 peripheral registers                       |
| **WrProtdRegEcm0_u32**  | Protected Register write sequence for 32bit Ecm0 peripheral registers                        |
| **WrProtdRegFlmd_u32**  | Protected Register write sequence for 32bit Flmd peripheral registers                        |
| **NxtrSwRst**           | API to issue a Nexteer Defined Software Reset                                                |
| **NxtrSwRstFromExcpn**  | API to issue a Nexteer Defined Software Reset for resetting from a hardware exception source |

# Configuration REQUIREMeNTS

None

## Build Time Config

|             |           |     |
|-------------|-----------|-----|
| **Modules** | **Notes** |     |
|             |           |     |

## Configuration Files to be provided by Integration Project

N/A

## Da Vinci Parameter Configuration Changes

|               |           |         |
|---------------|-----------|---------|
| **Parameter** | **Notes** | **SWC** |
|               |           |         |

## DaVinci Interrupt Configuration Changes

|              |           |
|--------------|-----------|
| **ISR Name** | **Notes** |
|              |           |

## Manual Configuration Changes

|              |           |         |
|--------------|-----------|---------|
| **Constant** | **Notes** | **SWC** |
|              |           |         |

# Integration DATAFLOW REQUIREMENTS

## Required Global Data Inputs

## Required Global Data Outputs

## Specific Include Path present

Yes – Integrator must properly choose the correct include search path in
this component in the integration .gpj file. The path chosen must align
with the correct micro family (e.g. P1M vs P1MC) as well as the correct
specific micro derivative that is being used in the integration project
(e.g. R7F701373A). Additionally, the integration .gpj should only
include the correct subproject .gpj file (again aligning to the correct
micro family as well as correct micro derivative). Please note that two
include paths are required in the integration project for use of this
component, one to the base family being used (e.g.
“-I..\\.\AR202A_MicroCtrlrSuprt_Impl\include\P1XC\\) and one to the
exact micro derivative (e.g.
“-I..\\.\AR202A_MicroCtrlrSuprt_Impl\include\P1XC\R7F701373A\\).

# Runnable Scheduling 

None.

|          |                             |             |
|----------|-----------------------------|-------------|
| **Init** | **Scheduling Requirements** | **Trigger** |
|          |                             |             |

|              |                             |             |
|--------------|-----------------------------|-------------|
| **Runnable** | **Scheduling Requirements** | **Trigger** |
|              |                             |             |

**.**

# Memory Map REQUIREMENTS

## Mapping

|                    |              |           |
|--------------------|--------------|-----------|
| **Memory Section** | **Contents** | **Notes** |
|                    |              |           |
|                    |              |           |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

|             |         |         |
|-------------|---------|---------|
| **Feature** | **RAM** | **ROM** |
|             |         |         |

## NvM Blocks

# Compiler Settings

## Preprocessor MACRO

## Optimization Settings

# Appendix

*\<This section is for appendix\>*

{% endraw %}