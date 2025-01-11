---
layout: default
title: EcuTMeas_IntegrationManual
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**EcuTMeas**

**VERSION:** **3.0**

**DATE: 09-AUG-2017**

**Prepared By:**

**Shruthi Raghavan,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                              |                  |             |             |
|-----|--------------------|--------------------|---------|--------------------|
| **Sl. No.** | **Description**              | **Author**       | **Version** | **Date**    |
| 1           | Initial version              | Spandana Balani  | 1.0         | 23-Mar-2015 |
| 2           | ADC Hooks are added as input | KK               | 2.0         | 21-Mar-2016 |
| 3           | Added config params          | Shruthi Raghavan | 3.0         | 09-AUG-2017 |

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

[7.3 Non RTE NvM Blocks 10](#non-rte-nvm-blocks)

[7.4 RTE NvM Blocks 10](#rte-nvm-blocks)

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

|             |                                          |                                            |
|----------|----------------------------------------------|-----------------|
| **Sr. No.** | **Title**                                | **Version**                                |
| 1           | FDD - ES210A ECU Temperature Measurement | (See project group sub-version in synergy) |

# Dependencies

## SWCs

|            |                      |
|------------|----------------------|
| **Module** | **Required Feature** |
| **None**   | N/A                  |

## Global Functions(Non RTE) to be provided to Integration Project

None

# Configuration REQUIREMeNTS

## Build Time Config

|             |           |     |
|-------------|-----------|-----|
| **Modules** | **Notes** |     |
| **None**    |           |     |

## Configuration Files to be provided by Integration Project

## Da Vinci Parameter Configuration Changes

<table style="width:100%;">
<colgroup>
<col style="width: 52%" />
<col style="width: 35%" />
<col style="width: 11%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Parameter</strong></td>
<td><strong>Notes</strong></td>
<td><strong>SWC</strong></td>
</tr>
<tr class="even">
<td>ECUTMEAS_ECUTX_VOLT_U3P13
<strong>(</strong>/Nexteer/EcuTMeas/EcuTMeasConversionTables/EcuTx)</td>
<td>Give the values of the interpolation X table from project settings
in order starting from the first element. Values should be single
precision floating point type.</td>
<td>EcuTMeas</td>
</tr>
<tr class="odd">
<td>ECUTMEAS_ECUTY_DEGCGRD_S8P7
(/Nexteer/EcuTMeas/EcuTMeasConversionTables/EcuTy)</td>
<td>Give the values of the interpolation Y table from project settings
in order starting from the first element. Values should be single
precision floating point type.</td>
<td>EcuTMeas</td>
</tr>
<tr class="even">
<td><p>ECUTMEAS_RNGDIAGCMAX_DEGCGRD_F32</p>
<p>(/Nexteer/EcuTMeas/EcuTMeasDiagc/MaxTLim)</p></td>
<td>Identifies the max temperature allowed to accumulate a diagnostic
error</td>
<td>EcuTMeas</td>
</tr>
<tr class="odd">
<td><p>ECUTMEAS_RNGDIAGCMIN_DEGCGRD_F32</p>
<p>(/Nexteer/EcuTMeas/EcuTMeasDiagc/MinTLim)</p></td>
<td>Identifies the min temperature allowed to accumulate a diagnostic
error</td>
<td>EcuTMeas</td>
</tr>
<tr class="even">
<td><p>ECUTMEAS_NTC0X045FAILSTEP_CNT_U16</p>
<p>(/Nexteer/EcuTMeas/EcuTMeasDiagc/Ntc0x045FailStep)</p></td>
<td>Error Accumulator Test Step Size for Failed Ecu Temperature
Test</td>
<td>EcuTMeas</td>
</tr>
<tr class="odd">
<td><p>ECUTMEAS_NTC0X045PASSSTEP_CNT_U16</p>
<p>(/Nexteer/EcuTMeas/EcuTMeasDiagc/Ntc0x045PassStep)</p></td>
<td>Error Accumulator Test Step Size for Pass Ecu Temperature Test</td>
<td>EcuTMeas</td>
</tr>
<tr class="even">
<td><p>ECUTMEAS_DFTT_DEGCGRD_F32</p>
<p>(/Nexteer/EcuTMeas/EcuTMeasGeneral/DftTemp)</p></td>
<td>Default Temperature used under Fault Conditions</td>
<td>EcuTMeas</td>
</tr>
<tr class="odd">
<td><p>ECUTMEAS_FILTAU_HZ_F32</p>
<p>(/Nexteer/EcuTMeas/EcuTMeasGeneral/FilTau)</p></td>
<td>Sets the time constant for filtering the temperature
measurement</td>
<td>EcuTMeas</td>
</tr>
</tbody>
</table>

\*Also see descriptions in the DaVinci configurator

## DaVinci Interrupt Configuration Changes

|              |            |                         |           |
|--------------|------------|-------------------------|-----------|
| **ISR Name** | **VIM \#** | **Priority Dependency** | **Notes** |
| **N/A**      |            |                         |           |

## Manual Configuration Changes

|              |           |         |
|--------------|-----------|---------|
| **Constant** | **Notes** | **SWC** |
| **N/A**      |           |         |

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
| **EcuTMeasInit1** | On Init                     | RTE(Init)   |
|                   |                             |             |

|                  |                             |             |
|------------------|-----------------------------|-------------|
| **Runnable**     | **Scheduling Requirements** | **Trigger** |
| **EcuTMeasPer1** | None                        | RTE(100ms)  |

# Memory Map REQUIREMENTS

## Mapping

|                    |              |           |
|--------------------|--------------|-----------|
| **Memory Section** | **Contents** | **Notes** |
| **None**           |              |           |
|                    |              |           |

> \* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
> specified in the AUTOSAR Memory Mapping requirements.

## Usage

|             |         |         |
|-------------|---------|---------|
| **Feature** | **RAM** | **ROM** |
| **None**    |         |         |

Table 1: ARM Cortex R4 Memory Usage

## Non RTE NvM Blocks

|                |
|----------------|
| **Block Name** |
| **None**       |

Note : Size of the NVM block if configured in developer

##  RTE NvM Blocks

|                |
|----------------|
| **Block Name** |
| **None**       |

Note : Size of the NVM block if configured in developer

# Compiler Settings

##  Preprocessor MACRO

None

## Optimization Settings

None

# Appendix

> None

{% endraw %}