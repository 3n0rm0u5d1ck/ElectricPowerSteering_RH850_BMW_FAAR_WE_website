---
layout: default
title: CoreVltgMonr_MDD
nav_order: 3
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**CoreVtlgMonr**

**Aug 2, 2017**

**Version : 2.0**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                                                            |                  |             |             |
|--------------------------------------|--------------|----------|-----------|
| **Description**                                            | **Author**       | **Version** | **Date**    |
| Initial Version of Module Design Document for CoreVltgMonr | Shruthi Raghavan | 1.0         | 19-May-2017 |
| Made CVM start up test as an Init function                 | Avinash James    | 2.0         | 02-Aug-2017 |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [4](#introduction)](#introduction)

[1.1 Purpose [4](#purpose)](#purpose)

[2 CoreVtlgMonr & High-Level Description
[5](#corevtlgmonr-high-level-description)](#corevtlgmonr-high-level-description)

[3 Design details of software module
[6](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of CoreVtlgMonr
[6](#graphical-representation-of-corevtlgmonr)](#graphical-representation-of-corevtlgmonr)

[3.2 Data Flow Diagram [6](#data-flow-diagram)](#data-flow-diagram)

[3.2.1 Component level DFD
[6](#component-level-dfd)](#component-level-dfd)

[3.2.2 Function level DFD [6](#function-level-dfd)](#function-level-dfd)

[4 Constant Data Dictionary
[7](#constant-data-dictionary)](#constant-data-dictionary)

[4.1 Program (fixed) Constants
[7](#program-fixed-constants)](#program-fixed-constants)

[4.1.1 Embedded Constants [7](#embedded-constants)](#embedded-constants)

[5 Software Component Implementation
[8](#software-component-implementation)](#software-component-implementation)

[5.1 Sub-Module Functions
[8](#sub-module-functions)](#sub-module-functions)

[5.1.1 Init: CoreVtlgMonrInit1
[8](#init-corevtlgmonrinit1)](#init-corevtlgmonrinit1)

[5.1.1.1 Design Rationale [8](#design-rationale)](#design-rationale)

[5.1.2 Per: \<Component Name\>\_Per\<n\>
[8](#per-component-name_pern)](#per-component-name_pern)

[5.1.2.1 Design Rationale [8](#design-rationale-2)](#design-rationale-2)

[5.2 Server Runables [8](#server-runables)](#server-runables)

[5.2.1 PrphlVltgMonrStrtUpTestFlt [8](#section)](#section)

[5.2.1.1 Design Rationale [8](#section-1)](#section-1)

[5.3 Interrupt Functions
[8](#interrupt-functions)](#interrupt-functions)

[5.4 Module Internal (Local) Functions
[8](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 Local Function \#1 [8](#local-function-1)](#local-function-1)

[5.4.1.1 Design Rationale [8](#design-rationale-3)](#design-rationale-3)

[5.5 GLOBAL Function/Macro Definitions
[8](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[5.5.1 GLOBAL Function \#1 [9](#global-function-1)](#global-function-1)

[5.5.1.1 Design Rationale [9](#design-rationale-4)](#design-rationale-4)

[6 Known Limitations with Design
[10](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[11](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[12](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [13](#glossary)](#glossary)

[Appendix C References [14](#references)](#references)

# Introduction

## Purpose

> Module design document for Core voltage Monitor.

# CoreVtlgMonr & High-Level Description

CoreVltgMonr component is a MCAL supporting function for startup test
for CVM

# Design details of software module

## Graphical representation of CoreVtlgMonr

> <img
> src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/CM112A_CoreVltgMonr_Impl/doc/mediax/media/image2.png"
> style="width:3.425in;height:1.525in" />

## Data Flow Diagram

> Refer FDD Simulink Model.

### Component level DFD

> Refer FDD Simulink Model.

### Function level DFD

> Refer FDD Simulink Model.

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name     | Resolution | Units | Value |
|-------------------|------------|-------|-------|
|                   |            |       |       |
| NODEBSTEP_CNT_U16 | 1          | Cnt   | 0U    |
| Refer .m file     |            |       |       |

# Software Component Implementation

## Sub-Module Functions

## Init: CoreVtlgMonrInit1

## Design Rationale

## Init: CoreVtlgMonrInit2

## Design Rationale

## Per: \<Component Name\>\_Per\<n\>

## Design Rationale

> This SWC does not have any periodic

## Server Runables 

## 

|     |     |     |     |     |
|-----|-----|-----|-----|-----|
|     |     |     |     |     |
|     |     |     |     |     |
|     |     |     |     |     |

## 

## Interrupt Functions

None.

## Module Internal (Local) Functions

## Local Function \#1

|                      |       |      |     |     |
|----------------------|-------|------|-----|-----|
| **Function Name**    | None. | Type | Min | Max |
| **Arguments Passed** | NA    | \-   | \-  | \-  |
| **Return Value**     | NA    | \-   | \-  | \-  |

## Design Rationale

> NA

## GLOBAL Function/Macro Definitions

None

## GLOBAL Function \#1

|                      |       |      |     |     |
|----------------------|-------|------|-----|-----|
| **Function Name**    | None. | Type | Min | Max |
| **Arguments Passed** | NA    | \-   | \-  | \-  |
| **Return Value**     | NA    | \-   | \-  | \-  |

## Design Rationale

None

# Known Limitations with Design

None

# UNIT TEST CONSIDERATION

> None

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

| **Ref. \#** | **Title**                                                                                                                                                             | **Version**                           |
|------|---------------------------------------|---------------------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                    | v1.3.0 R4.0 Rev 2                     |
| 2           | MDD Guideline                                                                                                                                                         | Software Engineering Process 04.04.02 |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | Software Engineering Process 04.04.02 |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | Software Engineering Process 04.04.02 |

{% endraw %}