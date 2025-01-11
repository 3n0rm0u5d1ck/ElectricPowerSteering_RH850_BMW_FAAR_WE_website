---
layout: default
title: TmplMonr_IntegrationManual
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**TmplMonr**

**VERSION: 2.0**

**DATE: 27-Mar-2017**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Revision History**

|             |                                         |              |             |             |
|-----|------------------------------------|------------|---------|-----------|
| **Sl. No.** | **Description**                         | **Author**   | **Version** | **Date**    |
| 1           | Initial version                         | Krishna Anne | 1.0         | 24-Mar-2017 |
| 2           | Modified runnable scheduling statements | Krishna Anne | 2.0         | 27-Mar-2017 |

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

[7.3 NvM Blocks 10](#nvm-blocks)

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
|                  |                            |
|                  |                            |

# References

This section lists the title & version of all the documents that are
referred for development of this document

|             |                             |                                |
|-------------|-----------------------------|--------------------------------|
| **Sr. No.** | **Title**                   | **Version**                    |
| 1           | FDD – ES005C TmplMonr       | See Synergy subproject version |
| 2           | Software Naming Conventions | Process 04.02.00               |
| 3           | Software Coding Standards   | Process 04.02.00               |

# Dependencies

## SWCs

|                                    |                                                                                                                                          |
|-------------------------|-----------------------------------------------|
| **Module**                         | **Required Feature**                                                                                                                     |
| **Spi_Renesas_Ar4.0.3_01.06.05_0** |                                                                                                                                          |
| **CM600A_CSIG0CfgAndUse_Design**   | Channel and Sequence definitions and API requirements.                                                                                   |
| **CDD_EcmOutpAndDiagc**            | Needed for enumeration type definition. CDD_EcmOutpAndDiagc.h is required to be included in Rte_UserTypes.h file in integration project. |

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

\<Configuration file that will generated from this components that will
require Da Vinci Config generation or manual generation. Describe each
parameter \>

## Da Vinci Parameter Configuration Changes

|                                                    |           |         |
|----------------------------------------------------|-----------|---------|
| **Parameter**                                      | **Notes** | **SWC** |
| **See CM600A_CSIG0CfgAndUse_Design requirements.** |           |         |

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

Refer DataDict.m file

## Required Global Data Outputs

Refer DataDict.m file

## Specific Include Path present

No

# Runnable Scheduling 

This section specifies the required runnable scheduling.

|                   |                             |             |
|-------------------|-----------------------------|-------------|
| **Init**          | **Scheduling Requirements** | **Trigger** |
| **TmplMonrInit1** | None                        | RTE (init)  |

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 54%" />
<col style="width: 20%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Runnable</strong></td>
<td><strong>Scheduling Requirements</strong></td>
<td><strong>Trigger</strong></td>
</tr>
<tr class="even">
<td><strong>TmplMonrPer1</strong></td>
<td><p>At the start of Higher priority 2ms task group</p>
<p>(Higher priority 2ms tasks run in all system states)</p></td>
<td>RTE 2ms</td>
</tr>
<tr class="odd">
<td><strong>TmplMonrPer2</strong></td>
<td><p>At the end of Lower priority 2ms task group. This runnable should
be scheduled before states and modes computes a new system state.</p>
<p>(The task group that Per2 is running is assumed to be blocked from
execution during the shutdown process).  </p></td>
<td>RTE 2ms</td>
</tr>
<tr class="even">
<td><strong>TmplMonrPer3</strong></td>
<td><p>After TmplMonrPer1 in Higher priority 2ms task group</p>
<p>(Higher priority 2ms tasks run in all system states)</p></td>
<td>RTE 2ms</td>
</tr>
</tbody>
</table>

# Memory Map REQUIREMENTS

## Mapping

|                             |              |           |
|-----------------------------|--------------|-----------|
| **Memory Section**          | **Contents** | **Notes** |
| **TmplMonr_START_SEC_CODE** |              |           |
|                             |              |           |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

|             |         |         |
|-------------|---------|---------|
| **Feature** | **RAM** | **ROM** |
| **None**    |         |         |

Table 1: ARM Cortex R4 Memory Usage

## NvM Blocks

None.

# Compiler Settings

##  Preprocessor MACRO

None

## Optimization Settings

None

# Appendix

*None*

{% endraw %}