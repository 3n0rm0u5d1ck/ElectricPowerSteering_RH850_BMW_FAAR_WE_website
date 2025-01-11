---
layout: default
title: CtrldVelRtn_MDD
nav_order: 3
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**CtrldVelRtn**

**OCT 17,2017**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**TATA**

**TRIVANDRUM, INDIA**

**  
<u>Change History</u>**

|                 |            |             |             |
|-----------------|------------|-------------|-------------|
| **Description** | **Author** | **Version** | **Date**    |
| Initial Version | TATA       | 1.0         | 17-Oct-2017 |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [5](#introduction)](#introduction)

[1.1 Purpose [5](#purpose)](#purpose)

[2 CtrldVelRtn & High-Level Description
[6](#ctrldvelrtn-high-level-description)](#ctrldvelrtn-high-level-description)

[3 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of CtrldVelRtn
[7](#graphical-representation-of-ctrldvelrtn)](#graphical-representation-of-ctrldvelrtn)

[3.2 Data Flow Diagram [8](#data-flow-diagram)](#data-flow-diagram)

[3.2.1 Component level DFD
[8](#component-level-dfd)](#component-level-dfd)

[3.2.2 Function level DFD [8](#function-level-dfd)](#function-level-dfd)

[4 Constant Data Dictionary
[9](#constant-data-dictionary)](#constant-data-dictionary)

[4.1 Program (fixed) Constants
[9](#program-fixed-constants)](#program-fixed-constants)

[4.1.1 Embedded Constants [9](#embedded-constants)](#embedded-constants)

[5 Software Component Implementation
[10](#software-component-implementation)](#software-component-implementation)

[5.1 Sub-Module Functions
[10](#sub-module-functions)](#sub-module-functions)

[5.1.1 Init: CtrldVelRtnInit1
[10](#init-ctrldvelrtninit1)](#init-ctrldvelrtninit1)

[5.1.1.1 Design Rationale [10](#design-rationale)](#design-rationale)

[5.1.1.2 Module Outputs [10](#module-outputs)](#module-outputs)

[5.1.2Per: CtrldVelRtnPer1
[10](#per-ctrldvelrtnper1)](#per-ctrldvelrtnper1)

[5.1.1.3 Design Rationale
[10](#design-rationale-1)](#design-rationale-1)

[5.1.1.4 Store Module Inputs to Local copies
[10](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[5.1.1.5 (Processing of function)………
[10](#processing-of-function)](#processing-of-function)

[5.1.1.6 Store Local copy of outputs into Module Outputs
[10](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[5.2 Server Runables [10](#server-runables)](#server-runables)

[5.3 Interrupt Functions
[10](#interrupt-functions)](#interrupt-functions)

[5.4 Module Internal (Local) Functions
[11](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 Local Function \#1 [11](#local-function-1)](#local-function-1)

[5.4.1.1 Design Rationale
[11](#design-rationale-2)](#design-rationale-2)

[5.4.1.2 Processing [11](#processing)](#processing)

[5.4.2 Local Function \#2 [11](#local-function-2)](#local-function-2)

[5.4.2.1 Design Rationale
[11](#design-rationale-3)](#design-rationale-3)

[5.4.2.2 Processing [11](#processing-1)](#processing-1)

[5.5 GLOBAL Function/Macro Definitions
[11](#global-functionmacro-definitions)](#global-functionmacro-definitions)

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

MDD for Controlled Velocity Return.

# CtrldVelRtn & High-Level Description

Please refer FDD.

# Design details of software module

## Graphical representation of CtrldVelRtn

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/SF065A_CtrldVelRtn_Impl/doc/mediax/media/image1.png"
style="width:2.38542in;height:6.01042in" />

## Data Flow Diagram

### Component level DFD

Please refer FDD.

### Function level DFD

Please refer FDD.

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name                        | Resolution | Units | Value |
|--------------------------------------|------------|-------|-------|
| Please refer Data Dictionary .m file | NA         | NA    | NA    |
| IDX2_CNT_U08                         | Uint8      | CNT   | 2U    |
| IDX3_CNT_U08                         | Uint8      | CNT   | 3U    |
| IDX4_CNT_U08                         | Uint8      | CNT   | 4U    |
| IDX5_CNT_U08                         | Uint8      | CNT   | 5U    |

# Software Component Implementation

## Sub-Module Functions

### 5.1.1 Init: CtrldVelRtnInit1 [init-ctrldvelrtninit1]

## Design Rationale

None

## Module Outputs

None

### 5.1.2Per: CtrldVelRtnPer1 [per-ctrldvelrtnper1]

## Design Rationale

None

## Store Module Inputs to Local copies

None

##  (Processing of function)………

Please refer FDD

## Store Local copy of outputs into Module Outputs

Please refer FDD

## Server Runables 

None

## Interrupt Functions

None

## Module Internal (Local) Functions

## Local Function \#1

|                      |                                 |         |          |         |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | DrvrTqSeln                      | Type    | Min      | Max     |
| **Arguments Passed** | MotTqCmdPwrLimd_MotNwtMtr_T_f32 | float32 | -8.8F    | 8.8F    |
|                      | HwTq_HwNwtMtr_T_f32             | float32 | -10.0F   | 10.0F   |
|                      | HwAgCmp_HwDeg_T_f32             | float32 | -1440.0F | 1440.0F |
|                      | HwVel_HwRadPerSec_T_f32         | float32 | -42.0F   | 42.0F   |
|                      | AssiMechPolarity_Uls_T_s08      | sint8   | -1U      | 1U      |
| **Return Value**     | DrvrTq_HwNwtMtr_T_f32           | float32 | -10.0F   | 10.0F   |

## Design Rationale

None.

## Processing

Refer to the “DriverTorque Selector” block of the Simulink model of the
design.

## Local Function \#2

|                      |                          |         |          |         |
|----------------------|--------------------------|---------|----------|---------|
| **Function Name**    | Dampg                    | Type    | Min      | Max     |
| **Arguments Passed** | HwVel_HwDegPerSec_T_f32  | float32 | -2406.0F | 2406.0F |
|                      | CtrlSca_Uls_T_f32        | float32 | 0.0F     | 1.0F    |
|                      | VehSpd_Kph_T_u9p7        | Uint16  | 0U       | 65535U  |
| **Return Value**     | DampgTerm_HwNwtMtr_T_f32 | float32 | -100.0F  | 100.0F  |

## Design Rationale

None.

## Processing

Refer to the “Damping” block of the Simulink model of the design.

## GLOBAL Function/Macro Definitions

None.

# Known Limitations with Design

None.

# UNIT TEST CONSIDERATION

None.

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

| **Ref. \#** | **Title**                                                                                                                                                             | **Version**                     |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                    | v1.3.0 R4.0 Rev 2               |
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.00                    |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 1.0                             |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.1                             |
| 5           | FDD : SF065A_CtrldVelRtn_Design                                                                                                                                       | See Synergy Sub-project version |

{% endraw %}