---
layout: default
title: RvsBattProtn_IntegrationManual
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**RvsBattProtn**

**VERSION: 1.0**

**DATE: 16-OCT-2017**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                 |                  |             |             |
|-------------|-----------------|------------------|-------------|-------------|
| **Sl. No.** | **Description** | **Author**       | **Version** | **Date**    |
| 1           | Initial version | Krzysztof Byrski | 1.0         | 16-Oct-2017 |

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
7](#__RefHeading___Toc489010056)

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
| 3           | ES252A_RvsBattProtn_Design           | See Synergy Sub Project Version |

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

|             |           |     |
|-------------|-----------|-----|
| **Modules** | **Notes** |     |
| **None**    |           |     |

## Configuration Files to be provided by Integration Project

RvsBattProtn_Cfg.h

## Da Vinci Parameter Configuration Changes

<table>
<colgroup>
<col style="width: 53%" />
<col style="width: 33%" />
<col style="width: 13%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Parameter</strong></td>
<td><strong>Notes</strong></td>
<td><strong>SWC</strong></td>
</tr>
<tr class="even">
<td><p><strong>RVSBATTPROTN_FAILSTEP_CNT_U16</strong></p>
<p>(/Nexteer/ RvsBattProtn/ RvsBattProtnGeneral/ FAILSTEP)</p></td>
<td>Debounce NTC set strategy step towards FAIL status</td>
<td>RvsBattProtn</td>
</tr>
<tr class="odd">
<td><p><strong>RVSBATTPROTN_GNDMEASDVLTGHILIMN_VOLT_F32</strong></p>
<p>(/Nexteer/ RvsBattProtn/ RvsBattProtnGeneral/
GNDMEASDVLTGHILIMN)</p></td>
<td>Maximum allowed signal level for ground related measures</td>
<td>RvsBattProtn</td>
</tr>
<tr class="even">
<td><p><strong>RVSBATTPROTN_GNDMEASDVLTGLOLIMN_VOLT_F32</strong></p>
<p>(/Nexteer/ RvsBattProtn/ RvsBattProtnGeneral/
GNDMEASDVLTGLOLIMN)</p></td>
<td>Minimum allowed signal level for ground related measures</td>
<td>RvsBattProtn</td>
</tr>
<tr class="odd">
<td><p><strong>RVSBATTPROTN_PASSSTEP_CNT_U16</strong></p>
<p>(/Nexteer/ RvsBattProtn/ RvsBattProtnGeneral/ PASSSTEP)</p></td>
<td>Debounce NTC set strategy step towards PASS status</td>
<td>RvsBattProtn</td>
</tr>
<tr class="even">
<td><p><strong>RVSBATTPROTN_RTNMEASDVLTGHILIMN_VOLT_F32</strong></p>
<p>(/Nexteer/ RvsBattProtn/ RvsBattProtnGeneral/
RTNMEASDVLTGHILIMN)</p></td>
<td>Maximum allowed signal level for battery return related
measures</td>
<td>RvsBattProtn</td>
</tr>
<tr class="odd">
<td><p><strong>RVSBATTPROTN_RTNMEASDVLTGLOLIMN_VOLT_F32</strong></p>
<p>(/Nexteer/ RvsBattProtn/ RvsBattProtnGeneral/
RTNMEASDVLTGLOLIMN)</p></td>
<td>Minimum allowed signal level for battery return related
measures</td>
<td>RvsBattProtn</td>
</tr>
<tr class="even">
<td><p><strong>RVSBATTPROTN_RVSFLTTHD_VOLT_F32</strong></p>
<p>(/Nexteer/ RvsBattProtn/ RvsBattProtnGeneral/ RVSFLTTHD)</p></td>
<td>Threshold level for detection of MOSFET malfunction</td>
<td>RvsBattProtn</td>
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

Refer DataDict.m file

## Required Global Data Outputs

Refer DataDict.m file

## Specific Include Path present

No

# Runnable Scheduling 

This section specifies the required runnable scheduling.

|                       |                             |             |
|-----------------------|-----------------------------|-------------|
| **Init**              | **Scheduling Requirements** | **Trigger** |
| **RvsBattProtnInit1** | None                        | RTE (Init)  |

|                      |                             |             |
|----------------------|-----------------------------|-------------|
| **Runnable**         | **Scheduling Requirements** | **Trigger** |
| **RvsBattProtnPer1** | None                        | RTE(10ms)   |

**.**

# Memory Map REQUIREMENTS

## Mapping

|                                 |              |           |
|---------------------------------|--------------|-----------|
| **Memory Section**              | **Contents** | **Notes** |
| **RvsBattProtn_START_SEC_CODE** | Code         |           |

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

None

{% endraw %}