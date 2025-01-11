---
layout: default
title: PwrLimr_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**PwrLimr**

**20-APR-2018**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Shawn Penning,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                 |               |             |             |
|-----------------|---------------|-------------|-------------|
| **Description** | **Author**    | **Version** | **Date**    |
| Initial Version | Shawn Penning | 1.0         | 20-APR-2018 |

**<u>  
</u>**

<u>Table of Contents</u>

[1 PwrLimr High-Level Description
[5](#pwrlimr-high-level-description)](#pwrlimr-high-level-description)

[2 Design details of software module
[6](#design-details-of-software-module)](#design-details-of-software-module)

[2.1 Graphical representation of PwrLimr
[6](#graphical-representation-of-pwrlimr)](#graphical-representation-of-pwrlimr)

[2.2 Data Flow Diagram [6](#data-flow-diagram)](#data-flow-diagram)

[2.2.1 Component level DFD
[6](#component-level-dfd)](#component-level-dfd)

[2.2.2 Function level DFD [6](#function-level-dfd)](#function-level-dfd)

[3 Constant Data Dictionary
[7](#constant-data-dictionary)](#constant-data-dictionary)

[3.1 Program (fixed) Constants
[7](#program-fixed-constants)](#program-fixed-constants)

[3.1.1 Embedded Constants [7](#embedded-constants)](#embedded-constants)

[4 Software Component Implementation
[8](#software-component-implementation)](#software-component-implementation)

[4.1 Sub-Module Functions
[8](#sub-module-functions)](#sub-module-functions)

[4.1.1 Init: PwrLimrInit1 [8](#init-pwrlimrinit1)](#init-pwrlimrinit1)

[4.1.1.1 Design Rationale [8](#design-rationale)](#design-rationale)

[4.1.1.2 Module Outputs [8](#module-outputs)](#module-outputs)

[4.1.2 Per: PwrLimrPer1 [8](#per-pwrlimrper1)](#per-pwrlimrper1)

[4.1.2.1 Design Rationale [8](#design-rationale-1)](#design-rationale-1)

[4.1.2.2 Store Module Inputs to Local copies
[8](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[4.1.2.3 (Processing of function)………
[8](#processing-of-function)](#processing-of-function)

[4.1.2.4 Store Local copy of outputs into Module Outputs
[8](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[4.1.3 Per: PwrLimrPer2 [8](#per-pwrlimrper2)](#per-pwrlimrper2)

[4.1.3.1 Design Rationale [8](#design-rationale-2)](#design-rationale-2)

[4.1.3.2 Store Module Inputs to Local copies
[8](#store-module-inputs-to-local-copies-1)](#store-module-inputs-to-local-copies-1)

[4.1.3.3 (Processing of function)………
[8](#processing-of-function-1)](#processing-of-function-1)

[4.1.3.4 Store Local copy of outputs into Module Outputs
[8](#store-local-copy-of-outputs-into-module-outputs-1)](#store-local-copy-of-outputs-into-module-outputs-1)

[4.2 Server Runnables [9](#server-runnables)](#server-runnables)

[4.3 Interrupt Functions
[9](#interrupt-functions)](#interrupt-functions)

[4.4 Module Internal (Local) Functions
[9](#module-internal-local-functions)](#module-internal-local-functions)

[4.4.1 AssiLimCdn [9](#assilimcdn)](#assilimcdn)

[5 Known Limitations with Design
[10](#known-limitations-with-design)](#known-limitations-with-design)

[6 UNIT TEST CONSIDERATION
[11](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[12](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [13](#glossary)](#glossary)

[Appendix C References [14](#references)](#references)

# PwrLimr High-Level Description

*Refer FDD*

# Design details of software module

## Graphical representation of PwrLimr

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/SF019D_PwrLimr_Impl/doc/mediax/media/image1.png"
style="width:5.10417in;height:5.6875in" />

## Data Flow Diagram

### Component level DFD

### Function level DFD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name    | Resolution | Units | Value |
|------------------|------------|-------|-------|
| BIT1MASK_ULS_U08 | 1          | Uls   | 2U    |
| Refer DataDict.m |            |       |       |

# Software Component Implementation

## Sub-Module Functions

## Init: PwrLimrInit1

## Design Rationale

*Refer FDD*

## Module Outputs

*Refer FDD*

###  [section]

## Per: PwrLimrPer1

## Design Rationale

*Refer FDD*

## Store Module Inputs to Local copies

*Refer FDD*

## (Processing of function)………

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*Refer FDD*

## Per: PwrLimrPer2

## Design Rationale

*Refer FDD*

## Store Module Inputs to Local copies

*Refer FDD*

## (Processing of function)………

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*Refer FDD*

## Server Runnables 

None

## Interrupt Functions

None

## Module Internal (Local) Functions

### AssiLimCdn

|                      |                     |         |      |       |
|----------------------|---------------------|---------|------|-------|
| **Function Name**    | AssiLimCdn          | Type    | Min  | Max   |
| **Arguments Passed** | FildTqLim_Uls_T_f32 | float32 | 0.0F | 1.0F  |
|                      | BrdgVltg_Volt_T_f32 | float32 | 6.0F | 26.5F |
| **Return Value**     | None                | N/A     | N/A  | N/A   |

#### Design Rationale

See “Asst_Lmt_Condition_Determination” block in the Simulink model of
the design.

# Known Limitations with Design

None

# UNIT TEST CONSIDERATION

None

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

| **Ref. \#** | **Title**                                                                                                                                                               | **Version**                    |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:AUTOSAR_SWS_MemoryMapping.pdf)                                                                                            | v1.3.0 R4.0 Rev 2              |
| 2           | MDD Guideline                                                                                                                                                           | EA4 01.00.00                   |
| 3           | EA4 [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc) | 01.01.00                       |
| 4           | Software Design and Coding Standards.doc                                                                                                                                | 2.1                            |
| 5           | FDD – SF019D Power Limiter                                                                                                                                              | See Synergy subproject version |

{% endraw %}