---
layout: default
title: McuErrInj Integration Manual
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**McuErrInj**

**VERSION:** **2.0**

**DATE:** **24-Jul-2017**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**  
Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                                        |               |             |             |
|-----|------------------------------------|------------|---------|-----------|
| **Sl. No.** | **Description**                        | **Author**    | **Version** | **Date**    |
| 1           | Initial version                        | Avinash James | 1.0         | 15-Mar-2017 |
| 2           | Update to include the tursted function | Avinash James | 2.0         | 24-Jul-2017 |

: ARM Cortex R4 Memory Usage

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
|                  |                            |
|                  |                            |

# References

This section lists the title & version of all the documents that are
referred for development of this document

| **Sr. No.** | **Title**                   | **Version**                    |
|-------------|-----------------------------|--------------------------------|
| 1           | FDD – DF003A McuDiagc       | See Synergy subproject version |
| 2           | Software Naming Conventions | Process 04.04.02               |
| 3           | Software Coding Standards   | Process 04.04.02               |

# Dependencies

## SWCs

| **Module** | **Required Feature** |
|------------|----------------------|
| **None**   |                      |
|            |                      |
|            |                      |
|            |                      |

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
referred. Developer should track the references.

## Global Functions(Non RTE) to be provided to Integration Project

InjVrfyCritRegErr() – Function to Inject micro diagnostic error in
Critical Registers

InjMcuVltgMonrErr() – Function to Inject micro diagnostic error in Core
voltage monitor

InjClkMonrErr() – Function to Inject micro diagnostic error in Clock
Monitors

InjOsTmpGenericRtErr () – Function to Inject Temporary Run time error in
Operating System

InjOsPrmntGenericRtErr () – Function to Inject Permanent Run time error
in Operating System

InjWdgErr () – Function to Watchdog errors

InjFpuErr () – Function to Inject floating point exceptions

InjMemProtnErr () – Function to Inject Memory protection errors

InjModErr () – Function to Inject mode errors

InjMcuRtErr () – Function to Inject Mcu Run Time errors

InjCodFlsEccErr() – Function to Inject Code flash ECC errors

InjRamMemErr( ) – Function to Inject peripheral and local RAM ECC errors

InjEcmMstChkrRtErr(void) () – Function to Inject micro diagnostic error
in ECM Master and Slave

InjUkwnStrtUpDetdErr(void) -() – Function to Inject unknown startup

InjIpgRtErr(void) () – Function to Inject Run time IPG errors

InjRtPegErr(void) – Function to Inject Run time Peg errors

InjDataParErr() – Function to Inject Data Parity errors

InjDmaErr() – Function Dma errors

InjMcuDiagcErr() – Function to Inject loss ofmotor control ISR errors

InjAdcErr() – Function to Inject ADC errors

InjProgSeqErr () – Function to inject program sequence errors

InjPbgRtErr () - Function to inject PBG run time errors

InjSwFpuErr () – Function to inject software Floating point error

McuDiagcTestTrustd() – Trusted function call from OS

# Configuration REQUIREMeNTS

## Build Time Config

<table style="width:100%;">
<colgroup>
<col style="width: 36%" />
<col style="width: 53%" />
<col style="width: 9%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Modules</strong></th>
<th><strong>Notes</strong></th>
<th></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>MCUDIAGCERRINJ</strong></td>
<td><p>STD_OFF for other builds</p>
<p>STD_ON for uDiag test builds</p></td>
<td></td>
</tr>
</tbody>
</table>

## Configuration Files to be provided by Integration Project

*None*

## Da Vinci Parameter Configuration Changes

| **Parameter** | **Notes** | **SWC** |
|---------------|-----------|---------|
| **None**      |           |         |

## DaVinci Interrupt Configuration Changes

| **ISR Name** | **VIM \#** | **Priority Dependency** | **Notes** |
|--------------|------------|-------------------------|-----------|
| **None**     |            |                         |           |

## Manual Configuration Changes

| **Constant**                                                                                                                                                            | **Notes** | **SWC** |
|-----------------------------|----------------------------------|----------|
| **OS Memory protection has to be extended to include the reserved RAM & invalid memory area .Also execution from RAM need to be enabled too as per the settings below** |           |         |

**(osuint32)0x0100a000UL, /\* MPU region 3 \*/**

**(osuint32)0x0100bffcUL,**

**(osuint32)0x03ff00edUL,**

**(osuint32)0x10020000UL, /\* MPU region 4 \*/**

**(osuint32)0x10020848UL,**

**(osuint32)0x03ff00dbUL,**

**(osuint32)0xfb000000UL, /\* MPU region 5 \*/**

**(osuint32)0xfebdfffcUL,**

**(osuint32)0x03ff00d9UL,**

**(osuint32)** **0xF3000000UUL, /\* MPU region 6 \*/**

**(osuint32)** **0xF4000000UL,**

**(osuint32)0x03ff00dbUL,**

**(osuint32)&osGlobalShared_StartAddr, /\* MPU region Global shared\*/**

**(osuint32)&osGlobalShared_EndAddr,**

**(osuint32)0x03ff00fbUL,**

# Integration DATAFLOW REQUIREMENTS

## Required Global Data Inputs

Refer DataDict.m file

## Required Global Data Outputs

Refer DataDict.m file

## Specific Include Path present

Yes

# Runnable Scheduling 

This section specifies the required runnable scheduling.

| **Init**          | **Scheduling Requirements** | **Trigger**    |
|-------------------|-----------------------------|----------------|
| **McuDiagcInit1** | **None**                    | **RTE (Init)** |

| **Runnable**            | **Scheduling Requirements** | **Trigger**       |
|-------------------------|-----------------------------|-------------------|
| **McuDiagcPer1**        | **None**                    | **RTE (2 ms)**    |
| **ClrErrInjReg_Oper**   | **None**                    | **On invocation** |
| **ReadErrInjReg_Oper**  | **None**                    | **On invocation** |
| **StrtErrInjCntr_Oper** | **None**                    | **On invocation** |
| **UpdErrInjReg_Oper**   | **None**                    | **On invocation** |
|                         |                             |                   |
|                         |                             |                   |
|                         |                             |                   |

# Memory Map REQUIREMENTS

## Mapping

| **Memory Section**                                 | **Contents**               | **Notes** |
|------------------------------------|------------------|------------------|
| **McuErrInj_START_SEC_VAR_INIT_128**               | Data section for DMA write |           |
| **McuErrInjGlobalShared_START_SEC_VAR_CLEARED_32** | Global shared data access  |           |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

| **Feature** | **RAM** | **ROM** |
|-------------|---------|---------|
| **None**    |         |         |

## NvM Blocks

None

# Compiler Settings

##  Preprocessor MACRO

None

## Optimization Settings

None

# Appendix

*None*

{% endraw %}