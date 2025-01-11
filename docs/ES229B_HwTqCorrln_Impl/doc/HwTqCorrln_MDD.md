---
layout: default
title: HwTqCorrln_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**HwTqCorrln**

**01-June-2016**

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
| 1           | Initial Version | Basavaraja Ganeshappa | 1.0         | 1^st^ June 2016 |

**  
**

**<u>Table of Contents</u>**

[1 HwTqCorrln High-Level Description
[4](#hwtqcorrln-high-level-description)](#hwtqcorrln-high-level-description)

[2 Design details of software module
[5](#design-details-of-software-module)](#design-details-of-software-module)

[2.1 Graphical representation of ‘HwTqCorrln’
[5](#graphical-representation-of-hwtqcorrln)](#graphical-representation-of-hwtqcorrln)

[2.2 Data Flow Diagram [5](#data-flow-diagram)](#data-flow-diagram)

[2.2.1 Component level DFD
[5](#component-level-dfd)](#component-level-dfd)

[2.2.2 Function level DFD [5](#function-level-dfd)](#function-level-dfd)

[3 Constant Data Dictionary
[7](#constant-data-dictionary)](#constant-data-dictionary)

[3.1 Program (fixed) Constants
[7](#program-fixed-constants)](#program-fixed-constants)

[3.1.1 Embedded Constants [7](#embedded-constants)](#embedded-constants)

[4 Software Component Implementation
[8](#software-component-implementation)](#software-component-implementation)

[4.1 Sub-Module Functions
[8](#sub-module-functions)](#sub-module-functions)

[4.1.1 Init: HwTqCorrlnInit1
[8](#init-hwtqcorrlninit1)](#init-hwtqcorrlninit1)

[4.1.1.1 Design Rationale [8](#design-rationale)](#design-rationale)

[4.1.1.2 Module Outputs [8](#module-outputs)](#module-outputs)

[4.1.2 Per: HwTqCorrlnPer1
[8](#per-hwtqcorrlnper1)](#per-hwtqcorrlnper1)

[4.1.2.1 Design Rationale [8](#design-rationale-1)](#design-rationale-1)

[4.1.2.2 Store Module Inputs to Local copies
[8](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[4.1.2.3 (Processing of function)………
[8](#processing-of-function)](#processing-of-function)

[4.1.2.4 Store Local copy of outputs into Module Outputs
[8](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[4.2 Server Runnables [8](#server-runnables)](#server-runnables)

[4.3 Interrupt Functions
[8](#interrupt-functions)](#interrupt-functions)

[4.4 Module Internal (Local) Functions
[8](#module-internal-local-functions)](#module-internal-local-functions)

[4.4.1 Local Function \#1 [8](#local-function-1)](#local-function-1)

[4.4.1.1 Design Rationale [9](#design-rationale-4)](#design-rationale-4)

[4.4.1.2 Processing [9](#processing)](#processing)

[4.5 GLOBAL Function/Macro Definitions
[9](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[5 Known Limitations with Design
[10](#known-limitations-with-design)](#known-limitations-with-design)

[6 UNIT TEST CONSIDERATION
[11](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[12](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [13](#glossary)](#glossary)

[Appendix C References [14](#references)](#references)

# HwTqCorrln High-Level Description

*Refer FDD*

# Design details of software module

## Graphical representation of ‘HwTqCorrln’

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/ES229B_HwTqCorrln_Impl/doc/mediax/media/image1.png"
style="width:5.78125in;height:5.88542in" />

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

### Init: HwTqCorrlnInit1

## Design Rationale

*Refer FDD*

## Module Outputs

*Refer FDD*

## Per: HwTqCorrlnPer1

## Design Rationale

*None*

## Store Module Inputs to Local copies

*None*

## (Processing of function)………

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*Refer FDD*

## Per: HwTqCorrlnPer2

## Design Rationale

*None*

## Store Module Inputs to Local copies

*None*

## (Processing of function)………

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*Refer FDD*

## Per: HwTqCorrlnPer3

## Design Rationale

*None*

## Store Module Inputs to Local copies

*None*

## (Processing of function)………

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*Refer FDD*

## Server Runnables 

None

## Interrupt Functions

*None*

## Module Internal (Local) Functions

## Local Function \#1

|                      |                         |         |       |      |
|----------------------|-------------------------|---------|-------|------|
| **Function Name**    | CorrlnSigAvlChk         | Type    | Min   | Max  |
| **Arguments Passed** | SigRollgCnt_Cnt_T_u08   | Uint8   | 0     | 255  |
|                      | MaxStallCnt_Cnt_T_u08   | Const   | 10    |      |
|                      | \*LstRollgCnt_Cnt_T_u08 | Uint8   | 0     | 255  |
|                      | \*StallCnt_Cnt_T_u08    | Uint8   | 0     | 255  |
| **Return Value**     | SigAAvail_Cnt_T_lgc     | boolean | FALSE | TRUE |

## Design Rationale

Refer FDD

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

| **Ref. \#** | **Title**                                                                                                                                                             | **Version**                    |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                    | Process 04.02.01               |
| 2           | MDD Guideline                                                                                                                                                         | Process 04.02.01               |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | Process 04.02.01               |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | Process 04.02.01               |
| 5           | ES229B_HwTqCorrln_Design                                                                                                                                              | See synergy subproject version |

{% endraw %}