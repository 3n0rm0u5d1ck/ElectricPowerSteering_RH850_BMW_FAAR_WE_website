---
layout: default
title: XcpIf_Integration_Manual
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**XCP Interfrace (XcpIf)**

**VERSION: 1.00**

**DATE: 19-Jan-2018**

**Prepared By:**

**ESG Software,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**  
<u>Document Change History</u>**

|             |                          |               |                   |                 |                   |            |
|--------|----------------|-------------|---------|---------|---------|-----------|
| **Version** | **Description**          | **Author(s)** | **Revision Date** | **Approved By** | **Approved Date** | **Status** |
| 1.00        | Initial document release | K. Smith      | 19-Jan-2018       | K. Smith        | 19-Jan-2018       | Released   |

**Note:**

This version 1.00 was baselined without requirements or a design
finalized.

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

[7.3 Non RTE NvM Blocks [10](#nvm-blocks)](#nvm-blocks)

[7.4 RTE NvM Blocks [10](#_Toc389222336)](#_Toc389222336)

[8 Compiler Settings [11](#compiler-settings)](#compiler-settings)

[8.1 Preprocessor MACRO [11](#preprocessor-macro)](#preprocessor-macro)

[8.2 Optimization Settings
[11](#optimization-settings)](#optimization-settings)

[9 Appendix [12](#appendix)](#appendix)

# Abbrevations And Acronyms

| **Abbreviation** | **Description**           |
|------------------|---------------------------|
| DFD              | Design functional diagram |
| MDD              | Module design Document    |

# References

This section lists the title & version of all the documents that are
referred for development of this document

| **Sr. No.** | **Title**                            | **Version** |
|-------------|--------------------------------------|-------------|
| 1           | Software Naming Conventions          | 1.02        |
| 2           | Software Design and Coding Standards | 2.01        |

# Dependencies

## SWCs

| **Module**          | **Required Feature**                     |
|---------------------|------------------------------------------|
| **\<Name of SWC\>** | \<Addition of global data, function\>\*. |

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
referred. Developer should track the references.

## Global Functions(Non RTE) to be provided to Integration Project

The following functions need to be defined as non-trusted.

-   CopyCalPageReq_Oper

-   SetCalPageReq_Oper

-   Xcp_Event

The following function needs to be defined as trusted:

-   XcpAppl_CalibrationWriteTrustd

# Configuration REQUIREMeNTS

## Build Time Config

| **Modules** | **Notes** |     |
|-------------|-----------|-----|
| **None**    |           |     |

## Configuration Files to be provided by Integration Project

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

Yes

# Runnable Scheduling 

This section specifies the required runnable scheduling.

| **Init**           | **Scheduling Requirements** | **Trigger** |
|--------------------|-----------------------------|-------------|
| **CDD_XcpIfInit1** | None                        | RTE (Init)  |

| **Runnable**      | **Scheduling Requirements** | **Trigger** |
|-------------------|-----------------------------|-------------|
| **CDD_XcpIfPer1** | None                        | RTE (100ms) |

**.**

# Memory Map REQUIREMENTS

## Mapping

| **Memory Section** | **Contents** | **Notes** |
|--------------------|--------------|-----------|
| **None**           |              |           |
|                    |              |           |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

| **Feature** | **RAM** | **ROM** |
|-------------|---------|---------|
| **None**    |         |         |

Table 1: ARM Cortex R4 Memory Usage

## NvM Blocks

\*See DataDict.m

# Compiler Settings

##  Preprocessor MACRO

None

## Optimization Settings

None

# Appendix

## XCP Configuration

Below are the following options that need to be enabled for the
component to properly work.

\<\< ADD XCP NOTES \>\>\>

## XCP Configuration

Based on the XCP settings for the DAQ lists, components descriptions
(arxml), source files (.c), and m-files are created based on the
configuration. These compoents will also need to be imported into the
project.

Key items

-   DAQ runnables should be placed in the lowest priority task for a
    given runnable rate. This should be called before the checkpoint.
    This will ensure a good sample and avoid lag for a given runnable
    rate.

-   Multiple DAQs can be configured to run at different rates. Each DAQ
    list will have its own set of description, source, and m-files to be
    integrated.

## Integration Compatibility with ES400A

If this component is used with ES400A version 2.0.0 or earlier will
require a header file to be created to map constants that are defined in
ES400A to the values used by ES104B. These values are different then
where defined in ES104A. Below is a sample template that can be used:

File Name: CDD_XcpIf.h

File Contents:

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>#ifndef CDD_XCPIF_H</p>
<p>#define CDD_XCPIF_H</p>
<p>/* Included this private until ES400 is separated from ES104 */</p>
<p>#include "CDD_XcpIf_Cfg_private.h"</p>
<p>#define XCPIF_XCPCMDOK_CNT_U08 XCPIF_CMDOK_CNT_U08</p>
<p>#define XCPIF_SEGNOTVLD_CNT_U08 XCPIF_RTNSEGNOTVLD_CNT_U08</p>
<p>#define XCPIF_CRCPAGEMODNOTVLD_CNT_U08
XCPIF_RTNPAGEMODNOTVLD_CNT_U08</p>
<p>#define XCPIF_OUTOFRNG_CNT_U08 XCPIF_RTNOUTOFRNG_CNT_U08</p>
<p>#endif</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

# Template Change History

|             |                                                |                  |                   |                 |                   |            |
|--------|----------------|-------------|---------|---------|---------|-----------|
| **Version** | **Description**                                | **Author(s)**    | **Revision Date** | **Approved By** | **Approved Date** | **Status** |
| 1.00        | Initial version                                | S. Sengottaniyan | NA                | \-              | NA                | Released   |
| 1.01        | Rework on initial version                      | S. Sengottaniyan | 23-May-2014       | \-              | 23-May-2014       | Released   |
| 1.02        | Removed Config Id references from the document | M. Mehta         | 10-Jul-2014       | L. Newton       | 10-Jul-2014       | Released   |
| 1.03        | Modificaions for EA4                           | M. Story         | 06-May-2015       | SEPG            | 06-May-2015       | Released   |
| 1.04        | Aligned to portal version guideline            | Umesh Sambhari   | 21-Nov-2017       | NA              | NA                | Released   |

{% endraw %}