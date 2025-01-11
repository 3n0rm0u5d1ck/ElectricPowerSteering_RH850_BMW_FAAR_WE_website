---
layout: default
title: BmwHwAgArbnAndEotPosn_IntegrationManual
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**BmwHwAgArbnAndEotPosn**

**VERSION: 3.0**

**DATE: 13-Jan-2018**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                                       |                  |             |             |
|-----|--------------------|--------------------|---------|--------------------|
| **Sl. No.** | **Description**                       | **Author**       | **Version** | **Date**    |
| 1           | Initial version                       | Krzysztof Byrski | 1.0         | 25-Oct-2017 |
| 2           | Configuration parameters              | Krzysztof Byrski | 2.0         | 30-Nov-2017 |
| 3           | Updated Configuration Parameters list | Matthew Leser    | 3.0         | 13-Jan-2018 |

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
7](#__RefHeading___Toc497472848)

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

# References

This section lists the title & version of all the documents that are
referred for development of this document

|             |                                      |                                 |
|----------|----------------------------------------------|-----------------|
| **Sr. No.** | **Title**                            | **Version**                     |
| 1           | EA4 Software Naming Conventions      | 01.01.00                        |
| 2           | Software Design and Coding Standards | 2.1                             |
| 3           | CF071A_BmwHwAgArbnAndEotPosn_Design  | See Synergy Sub Project Version |

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

None

# Configuration REQUIREMeNTS

## Build Time Config

|             |           |     |
|-------------|-----------|-----|
| **Modules** | **Notes** |     |
| **None**    |           |     |

## Configuration Files to be provided by Integration Project

BmwHwAgArbnAndEotPosn_Cfg.h

## Da Vinci Parameter Configuration Changes

<table>
<colgroup>
<col style="width: 66%" />
<col style="width: 23%" />
<col style="width: 9%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Parameter</strong></td>
<td><strong>Notes</strong></td>
<td><strong>SWC</strong></td>
</tr>
<tr class="even">
<td><p><strong>BMWHWAGARBNANDEOTPOSN_NTCHWAGSNSRNOTTRIM_CNT_ENUM</strong></p>
<p>(BmwHwAgArbnAndEotPosn\BmwHwAgArbnAndEotPosnGeneral\NTCHWAGSNSRNOTTRIM)</p></td>
<td>Ntc Handwheel Angle Sensor Not Trim</td>
<td>CF071A</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p><strong>BMWHWAGARBNANDEOTPOSN_NTCLOSSOFPINIOINAGZEROSPD_CNT_ENUM</strong></p>
<p>(BmwHwAgArbnAndEotPosn\BmwHwAgArbnAndEotPosnGeneral\NTCLOSSOFPINIOINAGZEROSPD)</p></td>
<td>Ntc Loss of Pinion Angle Zero Speed</td>
<td>CF071A</td>
</tr>
<tr class="even">
<td><p><strong>BMWHWAGARBNANDEOTPOSN_NTCLOSSOFPINIONAG_CNT_ENUM</strong></p>
<p>(BmwHwAgArbnAndEotPosn\BmwHwAgArbnAndEotPosnGeneral\NTCLOSSOFPINIONAG)</p></td>
<td>Ntc Loss of Pinion Angle</td>
<td>CF071A</td>
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

Refer FDD

## Required Global Data Outputs

Refer FDD

## Specific Include Path present

No

# Runnable Scheduling 

This section specifies the required runnable scheduling.

|                                |                             |             |
|--------------------------------|-----------------------------|-------------|
| **Init**                       | **Scheduling Requirements** | **Trigger** |
| **BmwHwAgArbnAndEotPosnInit1** | None                        | RTE (Init)  |

|                                        |                             |             |
|---------------------------|-------------------------------|--------------|
| **Runnable**                           | **Scheduling Requirements** | **Trigger** |
| **BmwHwAgArbnAndEotPosnPer1**          | None                        | RTE(2ms)    |
| **ClrBmwRackCentrToVehCentrOffs_Oper** | None                        | RTE(Event)  |
| **ClrVehCentrPosn_Oper**               | None                        | RTE(Event)  |
| **SetVehCentrPosn_Oper**               | None                        | RTE(Event)  |

# Memory Map REQUIREMENTS

## Mapping

|                                          |              |           |
|------------------------------------------|--------------|-----------|
| **Memory Section**                       | **Contents** | **Notes** |
| **BmwHwAgArbnAndEotPosn_START_SEC_CODE** | Code         | N/A       |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

|             |         |         |
|-------------|---------|---------|
| **Feature** | **RAM** | **ROM** |
| **N/A**     |         |         |

Table 1: ARM Cortex R4 Memory Usage

## NvM Blocks

\*See DataDict.m

# Compiler Settings

##  Preprocessor MACRO

None

## Optimization Settings

None

# Appendix

{% endraw %}