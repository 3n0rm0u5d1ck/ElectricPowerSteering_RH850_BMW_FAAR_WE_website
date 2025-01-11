---
layout: default
title: MotAg1Meas_IntegrationManual
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**MotAg1Meas**

**VERSION: 3.0**

**DATE: 25-Apr-2018**

**Prepared By:**

**Krzysztof Byrski,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                                     |                  |             |             |
|-----|--------------------|--------------------|---------|--------------------|
| **Sl. No.** | **Description**                     | **Author**       | **Version** | **Date**    |
| 1           | Initial version                     | Avinash James    | 1.0         | 07-Jun-2016 |
| 2           | Update location of cfg.h template   | Brendon Binder   | 2.0         | 25-Aug-2017 |
| 3           | Updated as per Design version 5.0.0 | Krzysztof Byrski | 3.0         | 25-Apr-2018 |

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
7](#__RefHeading___Toc491431322)

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

|             |                               |                                   |
|----------|----------------------------------------------|-----------------|
| **Sr. No.** | **Title**                     | **Version**                       |
| 1           | MDD Guidelines                | Software Process Release 04.02.01 |
| 1           | Software Naming Conventions   | Software Process Release 04.02.01 |
| 3           | Design and Coding Standards   | Software Process Release 04.02.01 |
| 4           | FDD: CM640B_MotAg1Meas_Design | See Synergy subproject version    |

# Dependencies

## SWCs

|                        |                      |
|------------------------|----------------------|
| **Module**             | **Required Feature** |
| CM515A_MotAg4Meas_Impl | CDD_MotAg4Meas.h     |

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
referred. Developer should track the references.

## Global Functions(Non RTE) to be provided to Integration Project

-   MotAg1MeasPer1

-   MotAg1CfgLoPwrMod

See FDD – CM640B_MotAg1Meas_DataDict.m file for more details.

# Configuration REQUIREMeNTS

## Build Time Config

|                            |                                         |     |
|----------------------------|-----------------------------------------|-----|
| **Modules**                | **Notes**                               |     |
| **CM640B_MotAg1Meas_Impl** | ConfigParam MOTAG1MEAS_DIQEPIF_CNT_LOGL |     |

## Configuration Files to be provided by Integration Project

CDD_MotAg1Meas_Cfg.h

## Da Vinci Parameter Configuration Changes

<table style="width:100%;">
<colgroup>
<col style="width: 51%" />
<col style="width: 30%" />
<col style="width: 18%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Parameter</strong></td>
<td><strong>Notes</strong></td>
<td><strong>SWC</strong></td>
</tr>
<tr class="even">
<td><p><strong>MOTAG1MEAS_DIQEPIF_CNT_LOGL</strong></p>
<p>(MotAg1Meas\MotAg1MeasGeneral\ DIQEPIF)</p></td>
<td>Motor Angle 1 Measure Disable QEP Interface</td>
<td>CM640B_MotAg1Meas_Impl</td>
</tr>
<tr class="odd">
<td><p><strong>MOTAG1MEAS_MOTAG1PRTCLFLTNTCNR_CNT_ENUM</strong></p>
<p>(MotAg1Meas\MotAg1MeasGeneral\ MOTAG1PRTCLFLTNTCNR)</p></td>
<td>Motor Angle 1 Protocol Fault NTC Number</td>
<td>CM640B_MotAg1Meas_Impl</td>
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

See FDD – CM640B_MotAg1Meas_DataDict.m file

## Required Global Data Outputs

See FDD – CM640B_MotAg1Meas_DataDict.m file

## Specific Include Path present

Yes

# Runnable Scheduling 

This section specifies the required runnable scheduling.

|                     |                             |             |
|---------------------|-----------------------------|-------------|
| **Init**            | **Scheduling Requirements** | **Trigger** |
| **MotAg1MeasInit1** |                             | RTE/ Init   |

|                                       |                             |                        |
|------------------------------|----------------------------|--------------|
| **Runnable**                          | **Scheduling Requirements** | **Trigger**            |
| **MotAg1MeasPer1**                    | None                        | Motor control runnable |
| **MotAg1MeasPer2**                    | None                        | RTE/2 ms               |
| **MotAg1MeasMotAg1CoeffTblRead_Oper** | None                        | On event               |
| **MotAg1MeasMotAg1CoeffTblWr_Oper**   | None                        | On event               |
| **MotAg1CfgLoPwrMod**                 | None                        | On event, NonRte       |

# Memory Map REQUIREMENTS

## Mapping

|                                           |                         |           |
|---------------------------------|-------------------|--------------------|
| **Memory Section**                        | **Contents**            | **Notes** |
| **CDD_MotAg1Meas_MotCtrl_START_SEC_CODE** | Motor Control runnables |           |
|                                           |                         |           |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

|             |         |         |
|-------------|---------|---------|
| **Feature** | **RAM** | **ROM** |
| **None**    |         |         |

Table 1: ARM Cortex R4 Memory Usage

## NvM Blocks

-   MotAg1CoeffTbl

# Compiler Settings

##  Preprocessor MACRO

> *None*

## Optimization Settings

> *None*

# Appendix

*None*

{% endraw %}