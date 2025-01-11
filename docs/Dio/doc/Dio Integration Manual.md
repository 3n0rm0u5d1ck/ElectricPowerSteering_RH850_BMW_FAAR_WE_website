---
layout: default
title: Dio Integration Manual
nav_order: 1
parent: DIO Driver
---
{% raw %}
**Integration Manual**

**For**

**Dio**

**VERSION: 1**

**DATE: 05/08/17**

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
| 1           | Initial version | Lucas Wendling | 1           | 05/08/17 |

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

## SWCs

|            |                      |
|------------|----------------------|
| **Module** | **Required Feature** |
|            |                      |

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
referred. Developer should track the references.

## Global Functions(Non RTE) to be provided to Integration Project

API usage and scheduling of BSW components expected to be captured at a
project architectural level and is beyond the scope of this document.
Third party documentation can be referenced as needed.

# Configuration REQUIREMeNTS

Configuration of BSW components expected to be captured at a project
architectural level and is beyond the scope of this document. Third
party documentation can be referenced as needed.

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

Yes

# Runnable Scheduling 

API usage and scheduling of BSW components expected to be captured at a
project architectural level and is beyond the scope of this document.
Third party documentation can be referenced as needed.

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

The MCAL related files require specific compiler toolchain settings to
be used to match what the MCAL was developed and tested to. This is the
following:

-c -Osize -g -cpu=rh850g3m -gsize -prepare_dispose -inline_prologue
-sda=all -Wundef -no_callt -reserve_r2 --short_enum --prototype_errors
--diag_error 193 -dual_debug -large_sda --no_commons -shorten_loads
-shorten_moves -Wshadow -nofloatio -ignore_callt_state_in_interrupts
-delete

This component’s .gpj file has been adapted to provide these options for
the static files of this component. **NOTE: The dynamic, generated files
from this component need to be compiled with these options as well, and
therefore the integration project will need to be adapted to provide
these settings to the generated files in the integration project.**

The following snippet can be adapted/added to the a batch file which
creates the generate.gpj project for integration project usage:

> *for %%F in
> (../generate/**<span class="mark">\<MCAL_Component\></span>**/src/\*.c)
> do (*
>
> *ECHO
> ..\generate/**<span class="mark">\<MCAL_Component\></span>**/src\\%F
> \>\> generate.gpj*
>
> *ECHO \# MCAL BUILD OPTIONS \# \>\> generate.gpj*
>
> *ECHO -c \>\> generate.gpj*
>
> *ECHO -Osize \>\> generate.gpj*
>
> *ECHO -g \>\> generate.gpj*
>
> *ECHO -cpu=rh850g3m \>\> generate.gpj*
>
> *ECHO -gsize \>\> generate.gpj*
>
> *ECHO -prepare_dispose \>\> generate.gpj*
>
> *ECHO -inline_prologue \>\> generate.gpj*
>
> *ECHO -sda=all \>\> generate.gpj*
>
> *ECHO -Wundef \>\> generate.gpj*
>
> *ECHO -no_callt \>\> generate.gpj*
>
> *ECHO -reserve_r2 \>\> generate.gpj*
>
> *ECHO --short_enum \>\> generate.gpj*
>
> *ECHO --prototype_errors \>\> generate.gpj*
>
> *ECHO --diag_error 193 \>\> generate.gpj*
>
> *ECHO -dual_debug \>\> generate.gpj*
>
> *ECHO -large_sda \>\> generate.gpj*
>
> *ECHO --no_commons \>\> generate.gpj*
>
> *ECHO -shorten_loads \>\> generate.gpj*
>
> *ECHO -shorten_moves \>\> generate.gpj*
>
> *ECHO -Wshadow \>\> generate.gpj*
>
> *ECHO -nofloatio \>\> generate.gpj*
>
> *ECHO -ignore_callt_state_in_interrupts \>\> generate.gpj*
>
> *ECHO -delete \>\> generate.gpj*
>
> *)*

##  Preprocessor MACRO

## Optimization Settings

# Appendix

*\<This section is for appendix\>*

{% endraw %}