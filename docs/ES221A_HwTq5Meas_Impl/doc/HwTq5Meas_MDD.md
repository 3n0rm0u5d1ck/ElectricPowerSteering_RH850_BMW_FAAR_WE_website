---
layout: default
title: HwTq5Meas_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**HwTq5Meas**

**Oct** **30, 2017**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**TATA ELXSI,**

**TRIVANDRUM, INDIA**

**  
<u>Change History</u>**

|                                    |               |             |             |
|------------------------|---------------------|--------------|--------------|
| **Description**                    | **Author**    | **Version** | **Date**    |
| Initial Version                    | Krishna Anne  | 1.0         | 10-Jun-2016 |
| Added a new server runnable        | Avinash James | 2.0         | 01-Dec-2016 |
| Updated as per FDD revision 1.10.0 | TATA          | 3.0         | 30-10-2017  |

**  
**

<u>Table of Contents</u>

[1 Introduction [5](#introduction)](#introduction)

[1.1 Purpose [5](#purpose)](#purpose)

[2 HwTq5Meas & High-Level Description
[6](#hwtq5meas-high-level-description)](#hwtq5meas-high-level-description)

[3 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of HwTq5Meas
[7](#graphical-representation-of-hwtq5meas)](#graphical-representation-of-hwtq5meas)

[3.2 Data Flow Diagram [7](#data-flow-diagram)](#data-flow-diagram)

[3.2.1 Component level DFD
[7](#component-level-dfd)](#component-level-dfd)

[3.2.2 Function level DFD [7](#function-level-dfd)](#function-level-dfd)

[4 Constant Data Dictionary
[8](#constant-data-dictionary)](#constant-data-dictionary)

[4.1 Program (fixed) Constants
[8](#program-fixed-constants)](#program-fixed-constants)

[4.1.1 Embedded Constants [8](#embedded-constants)](#embedded-constants)

[5 Software Component Implementation
[9](#software-component-implementation)](#software-component-implementation)

[5.1.1 Init: HwTq5Meas_Init1
[9](#init-hwtq5meas_init1)](#init-hwtq5meas_init1)

[5.1.1.1 Design Rationale [9](#design-rationale)](#design-rationale)

[5.1.1.2 Module Outputs [9](#module-outputs)](#module-outputs)

[5.1.2 Per: HwTq5Meas_Per1
[9](#per-hwtq5meas_per1)](#per-hwtq5meas_per1)

[5.1.2.1 Design Rationale [9](#design-rationale-1)](#design-rationale-1)

[5.1.3 Per: HwTq5Meas_Per2
[9](#per-hwtq5meas_per2)](#per-hwtq5meas_per2)

[5.1.3.1 Design Rationale [9](#design-rationale-2)](#design-rationale-2)

[5.1.4 Per: HwTq5Meas_Per3
[9](#per-hwtq5meas_per3)](#per-hwtq5meas_per3)

[5.1.4.1 Design Rationale [9](#design-rationale-3)](#design-rationale-3)

[5.1.5 Per: HwTq5Meas_Per4
[9](#per-hwtq5meas_per4)](#per-hwtq5meas_per4)

[5.1.5.1 Design Rationale [9](#design-rationale-4)](#design-rationale-4)

[5.2 Server Runables [9](#server-runables)](#server-runables)

[5.2.1 HwTq5AutTrim_Oper [9](#hwtq5auttrim_oper)](#hwtq5auttrim_oper)

[5.2.1.1 Design Rationale [9](#design-rationale-5)](#design-rationale-5)

[5.2.2 HwTq5ClrSnsrSca_Oper
[9](#hwtq5clrsnsrsca_oper)](#hwtq5clrsnsrsca_oper)

[5.2.2.1 Design Rationale [9](#design-rationale-6)](#design-rationale-6)

[5.2.3 HwTq5ClrTrim_Oper [10](#hwtq5clrtrim_oper)](#hwtq5clrtrim_oper)

[5.2.3.1 Design Rationale
[10](#design-rationale-7)](#design-rationale-7)

[5.2.4 HwTq5ReadSnsrSca_Oper
[10](#hwtq5readsnsrsca_oper)](#hwtq5readsnsrsca_oper)

[5.2.4.1 Design Rationale
[10](#design-rationale-8)](#design-rationale-8)

[5.2.5 HwTq5ReadTrim_Oper
[10](#hwtq5readtrim_oper)](#hwtq5readtrim_oper)

[5.2.5.1 Design Rationale
[10](#design-rationale-9)](#design-rationale-9)

[5.2.6 HwTq5TrimPrfmdSts_Oper
[10](#hwtq5trimprfmdsts_oper)](#hwtq5trimprfmdsts_oper)

[5.2.6.1 Design Rationale
[10](#design-rationale-10)](#design-rationale-10)

[5.2.7 HwTq5WrSnsrSca_Oper
[10](#hwtq5wrsnsrsca_oper)](#hwtq5wrsnsrsca_oper)

[5.2.7.1 Design Rationale
[10](#design-rationale-11)](#design-rationale-11)

[5.2.8 HwTq5WrTrim_Oper [10](#hwtq5wrtrim_oper)](#hwtq5wrtrim_oper)

[5.2.8.1 Design Rationale
[10](#design-rationale-12)](#design-rationale-12)

[5.2.9 HwTq5SnsrScaPrfmdSts_Oper
[10](#hwtq5snsrscaprfmdsts_oper)](#hwtq5snsrscaprfmdsts_oper)

[5.2.9.1 Design Rationale
[10](#design-rationale-13)](#design-rationale-13)

[5.3 Module Internal (Local) Functions
[10](#module-internal-local-functions)](#module-internal-local-functions)

[5.3.1 Local Function \#1 [10](#local-function-1)](#local-function-1)

[5.3.1.1 Design Rationale
[11](#design-rationale-14)](#design-rationale-14)

[5.3.1.2 Processing [11](#processing)](#processing)

[6 Known Limitations with Design
[12](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[13](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[14](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [15](#glossary)](#glossary)

[Appendix C References [16](#references)](#references)

# Introduction

## Purpose

MDD for HwTq5Meas.

# HwTq5Meas & High-Level Description

# Design details of software module

Please refer to the FDD.

## Graphical representation of HwTq5Meas

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/ES221A_HwTq5Meas_Impl/doc/mediax/media/image2.png"
style="width:5.30208in;height:5.5in" />

## Data Flow Diagram

### Component level DFD

### Function level DFD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name           | Resolution | Units | Value |
|-------------------------|------------|-------|-------|
| Please refer to the FDD |            |       |       |

# Software Component Implementation

## Init: HwTq5Meas_Init1

## Design Rationale

None

## Module Outputs

None

## Per: HwTq5Meas_Per1

## Design Rationale

Rte_Pim_HwTq5RawFastAdcIdxCntr is used in this periodic as a counter
that increments from 0 to 7 and is used to write to an output buffer
MotCtrlHwTq5RawFastAdcBuf accessed by Motor Control Manager. Whereas the
FDD describes this counter as 1 based indexing that increments from 1
till 8. Effective they are same in terms of functionality.

## Per: HwTq5Meas_Per2

## Design Rationale

None

## Per: HwTq5Meas_Per3

## Design Rationale

None

## Per: HwTq5Meas_Per4

## Design Rationale

None

## Server Runables 

## HwTq5AutTrim_Oper

## Design Rationale

None

## HwTq5ClrSnsrSca_Oper

## Design Rationale

None

## HwTq5ClrTrim_Oper

## Design Rationale

None

## HwTq5ReadSnsrSca_Oper

## Design Rationale

None

## HwTq5ReadTrim_Oper

## Design Rationale

None

## HwTq5TrimPrfmdSts_Oper

## Design Rationale

None

## HwTq5WrSnsrSca_Oper

## Design Rationale

None

## HwTq5WrTrim_Oper

## Design Rationale

None

## HwTq5SnsrScaPrfmdSts_Oper

## Design Rationale

None

## Module Internal (Local) Functions

## Local Function \#1

|                      |                         |          |                    |                    |
|-------------|--------------------------|---------|-------------|------------|
| **Function Name**    | HwTqQlfr                | Type     | Min                | Max                |
| **Arguments Passed** | NtcSts_Cnt_T_enum       | SigQlfr1 | SIGQLFR_NORES (0U) | SIGQLFR_FAILD (2U) |
|                      | ParamByte_Cnt_T_u08     | uint8    | 0                  | 4                  |
|                      | \* HwTq5Qlfr_Cnt_T_enum | SigQlfr1 | SIGQLFR_NORES (0U) | SIGQLFR_FAILD (2U) |
| **Return Value**     | NA                      | NA       | NA                 | NA                 |

## Design Rationale

## Processing

Please refer to the below path in the FDD model.

ES220A_HwTq5Meas/HwTq5Meas/HwTq5MeasPer2/HwTqQlfr

# Known Limitations with Design

None.

# UNIT TEST CONSIDERATION

Rte_Pim_HwTq5PrevRollgCntr is used as a rolling counter. Hence roll over
is intentional..

####### Abbreviations and Acronyms

| **Abbreviation or Acronym** | **Description** |
|-----------------------------|-----------------|
|                             |                 |
|                             |                 |

####### Glossary

**Note**: Terms and definitions from the source “Nexteer Automotive”
take precedence over all other definitions of the same term. Terms and
definitions from the source “Nexteer Automotive” are formulated from
multiple sources, including the following:

-   ISO 9000

-   ISO/IEC 12207

-   ISO/IEC 15504

-   Automotive SPICE® Process Reference Model (PRM)

-   Automotive SPICE® Process Assessment Model (PAM)

-   ISO/IEC 15288

-   ISO 26262

-   IEEE Standards

-   SWEBOK

-   PMBOK

-   Existing Nexteer Automotive documentation

| **Term** | **Definition**         | **Source** |
|----------|------------------------|------------|
| MDD      | Module Design Document |            |
| DFD      | Data Flow Diagram      |            |

####### References

| **Ref. \#** | **Title**                                                                                                                                                             | **Version**                    |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                    | v1.3.0 R4.0 Rev 2              |
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.00                   |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 1.0                            |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.1                            |
| 5           | ES221A_HwTq5Meas_Design                                                                                                                                               | See Synergy subproject version |

{% endraw %}