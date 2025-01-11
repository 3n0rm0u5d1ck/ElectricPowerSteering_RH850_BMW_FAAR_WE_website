---
layout: default
title: HwTqArbn_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**HwTqArbn**

**26-May-2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**SEPG,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|             |                 |                       |             |                 |
|------|----------------------|----------------------|----------|-------------|
| **SI. No.** | **Description** | **Author**            | **Version** | **Date**        |
| 1           | Initial Version | Basavaraja Ganeshappa | 1.0         | 26^th^ May 2016 |

**  
**

**<u>Table of Contents</u>**

[1 HwTrqArbn High-Level Description
[4](#hwtrqarbn-high-level-description)](#hwtrqarbn-high-level-description)

[2 Design details of software module
[5](#design-details-of-software-module)](#design-details-of-software-module)

[2.1 Graphical representation of HwTrqArbn
[5](#graphical-representation-of-hwtrqarbn)](#graphical-representation-of-hwtrqarbn)

[2.2 Data Flow Diagram [5](#data-flow-diagram)](#data-flow-diagram)

[2.2.1 Component level DFD
[5](#component-level-dfd)](#component-level-dfd)

[2.2.2 Function level DFD [5](#function-level-dfd)](#function-level-dfd)

[3 Constant Data Dictionary
[6](#constant-data-dictionary)](#constant-data-dictionary)

[3.1 Program (fixed) Constants
[6](#program-fixed-constants)](#program-fixed-constants)

[3.1.1 Embedded Constants [6](#embedded-constants)](#embedded-constants)

[4 Software Component Implementation
[7](#software-component-implementation)](#software-component-implementation)

[4.1 Sub-Module Functions
[7](#sub-module-functions)](#sub-module-functions)

[4.1.1 Init: HwTrqArbnInit1
[7](#init-hwtrqarbninit1)](#init-hwtrqarbninit1)

[4.1.1.1 Design Rationale [7](#design-rationale)](#design-rationale)

[4.1.1.2 Module Outputs [7](#module-outputs)](#module-outputs)

[4.1.2 Per: HwTrqArbnPer1 [7](#per-hwtrqarbnper1)](#per-hwtrqarbnper1)

[4.1.2.1 Design Rationale [7](#design-rationale-1)](#design-rationale-1)

[4.1.2.2 Store Module Inputs to Local copies
[7](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[4.1.2.3 (Processing of function)………
[7](#processing-of-function)](#processing-of-function)

[4.1.2.4 Store Local copy of outputs into Module Outputs
[7](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[4.2 Server Runables [7](#server-runables)](#server-runables)

[4.3 Interrupt Functions
[7](#interrupt-functions)](#interrupt-functions)

[4.4 Module Internal (Local) Functions
[7](#module-internal-local-functions)](#module-internal-local-functions)

[4.4.1 Local Function \#1 [7](#local-function-1)](#local-function-1)

[4.4.1.1 Design Rationale [8](#design-rationale-2)](#design-rationale-2)

[4.4.1.2 Processing [8](#processing)](#processing)

[4.5 GLOBAL Function/Macro Definitions
[8](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[5 Known Limitations with Design
[9](#known-limitations-with-design)](#known-limitations-with-design)

[6 UNIT TEST CONSIDERATION
[10](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[11](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [12](#glossary)](#glossary)

[Appendix C References [13](#references)](#references)

# HwTrqArbn High-Level Description

*Refer FDD*

# Design details of software module

## Graphical representation of HwTrqArbn

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/ES228B_HwTqArbn_Impl/doc/mediax/media/image1.png"
style="width:3.41667in;height:4.25in" />

## Data Flow Diagram

*Refer FDD*

### Component level DFD

*Refer FDD*

### Function level DFD

*Refer FDD*

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

Refer DD

# Software Component Implementation

*Refer FDD*

## Sub-Module Functions

*Refer FDD*

### Init: HwTrqArbnInit1

## Design Rationale

*Refer FDD*

## Module Outputs

*Refer FDD*

## Per: HwTrqArbnPer1

## Design Rationale

*None*

## Store Module Inputs to Local copies

*None*

## (Processing of function)………

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*Refer FDD*

## Server Runables 

None

## Interrupt Functions

*None*

## Module Internal (Local) Functions

## Local Function \#1

|                      |                        |         |       |      |
|----------------------|------------------------|---------|-------|------|
| **Function Name**    | FricLearning           | Type    | Min   | Max  |
| **Arguments Passed** | SigRollgCntr_Cnt_T_u08 | Uint8   | 0     | 255  |
|                      | SigQlfr_Cnt_T_enum     | enum    | 0     | 2    |
|                      | kMaxStallCnt_Cnt_T_u08 | Uint8   | 10    |      |
|                      | LstRollgCntr_Cnt_T_u08 | Uint8   | 0     | 255  |
|                      | StallCntr_Cnt_T_u08    | Uint8   | 0     | 255  |
| **Return Value**     | SigAvl_Cnt_T_logl      | boolean | FALSE | TRUE |

## Design Rationale

## Processing

Refer FDD

## GLOBAL Function/Macro Definitions

None

# Known Limitations with Design

None

# UNIT TEST CONSIDERATION

None

####### Abbreviations and Acronyms

| Abbreviation | Description                |
|--------------|----------------------------|
| DFD          | Design functional diagram  |
| MDD          | Module design Document     |
| FDD          | Functional Design Document |

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

| **Ref. \#** | **Title**                                                                                                                                                             | **Version**                      |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                    | Process 04.02.01                 |
| 2           | MDD Guideline                                                                                                                                                         | Process 04.02.01                 |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | Process 04.02.01                 |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | Process 04.02.01                 |
| 5           | ES228B_HwTqArbn_Design                                                                                                                                                | Refer synergy subproject version |

{% endraw %}