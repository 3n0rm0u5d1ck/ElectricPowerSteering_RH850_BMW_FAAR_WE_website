---
layout: default
title: HwTq4Meas_IntegrationManual
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**HwTq4Meas**

**VERSION:** **2.0**

**DATE: 01-DEC-2016**

**Prepared By:**

**Avinash James,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Revision History**

|             |                         |               |             |            |
|--------|-----------------|--------------------|---------|--------------------|
| **Sl. No.** | **Description**         | **Author**    | **Version** | **Date**   |
| 1           | Initial version         | Krishna Anne  | 1.0         | 06/10/2016 |
| 2           | Added a server runnable | Avinash James | 2.0         | 12/01/2016 |

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
7](#__RefHeading___Toc389222324)

[4.4 DaVinci Interrupt Configuration Changes
7](#__RefHeading___Toc389222325)

[4.5 Manual Configuration Changes 7](#__RefHeading___Toc389222326)

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

|                  |                           |
|------------------|---------------------------|
| **Abbreviation** | **Description**           |
| DFD              | Design functional diagram |
| MDD              | Module design Document    |

# References

This section lists the title & version of all the documents that are
referred for development of this document

|             |                             |                                   |
|----------|----------------------------------------------|-----------------|
| **Sr. No.** | **Title**                   | **Version**                       |
| 1           | MDD Guidelines              | Software Process Release 04.02.01 |
| 1           | Software Naming Conventions | Software Process Release 04.02.01 |
| 3           | Design and Coding Standards | Software Process Release 04.02.01 |
| 4           | ES220A_HwTq4Meas_Design     | See Synergy subproject version    |

# Dependencies

## SWCs

|            |                      |
|------------|----------------------|
| **Module** | **Required Feature** |
| HwTq4Meas  | None.                |

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
referred. Developer should track the references.

## Global Functions(Non RTE) to be provided to Integration Project

Please refer to the FDD.

# Configuration REQUIREMeNTS

## Build Time Config

|             |           |     |
|-------------|-----------|-----|
| **Modules** | **Notes** |     |
| **None**    |           |     |

## Configuration Files to be provided by Integration Project

CDD_HwTq4Meas_Cfg.h

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

<table>
<colgroup>
<col style="width: 39%" />
<col style="width: 47%" />
<col style="width: 12%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Constant</strong></td>
<td><strong>Notes</strong></td>
<td><strong>SWC</strong></td>
</tr>
<tr class="even">
<td><p><em>Note: Temporarily</em> CDD_HwTq4Meas_Cfg.h</p>
<p><em>file can be copied from the contract folder. Later revision will
have the Davinci configuration parameter to generate the
file.</em></p></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

# Integration DATAFLOW REQUIREMENTS

## Required Global Data Inputs

> Please refer to the FDD.

## Required Global Data Outputs

Please refer to the FDD.

## Specific Include Path present

Yes

# Runnable Scheduling 

This section specifies the required runnable scheduling.

|                    |                             |             |
|--------------------|-----------------------------|-------------|
| **Init**           | **Scheduling Requirements** | **Trigger** |
| **HwTq4MeasInit1** | None                        | RTE/ Init   |

|                               |                             |                        |
|------------------------------|-----------------------------|-------------|
| **Runnable**                  | **Scheduling Requirements** | **Trigger**            |
| **HwTq4MeasPer1**             | None                        | Motor control runnable |
| **HwTq4MeasPer2**             | None                        | RTE/2 ms               |
| **HwTq4MeasPer3**             | None                        | RTE/100 ms             |
| **HwTq4MeasPer4**             | None                        | RTE/100 ms             |
| **HwTq4AutTrim_Oper**         | None                        | On event               |
| **HwTq4ClrSnsrSca_Oper**      | None                        | On event               |
| **HwTq4ClrTrim_Oper**         | None                        | On event               |
| **HwTq4ReadSnsrSca_Oper**     | None                        | On event               |
| **HwTq4ReadTrim_Oper**        | None                        | On event               |
| **HwTq4TrimPrfmdSts_Oper**    | None                        | On event               |
| **HwTq4WrSnsrSca_Oper**       | None                        | On event               |
| **HwTq4WrTrim_Oper**          | None                        | On event               |
| **HwTq4SnsrScaPrfmdSts_Oper** | None                        | On event               |

# Memory Map REQUIREMENTS

## Mapping

|                                          |                         |           |
|--------------------------------|-------------------|---------------------|
| **Memory Section**                       | **Contents**            | **Notes** |
| **CDD_HwTq4Meas_MotCtrl_START_SEC_CODE** | Motor Control runnables |           |
|                                          |                         |           |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

|             |         |         |
|-------------|---------|---------|
| **Feature** | **RAM** | **ROM** |
| **None**    |         |         |

Table 1: ARM Cortex R4 Memory Usage

## NvM Blocks

HwTq4Offs and HwTq4Sca (See DataDict.m)

# Compiler Settings

##  Preprocessor MACRO

> None

## Optimization Settings

None

# Appendix

None

{% endraw %}