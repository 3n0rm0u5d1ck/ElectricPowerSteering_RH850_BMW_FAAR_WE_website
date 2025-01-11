---
layout: default
title: CDD_NxtrTi_MDD
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**CDD_NxtrTi**

**Aug** **23, 2017**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Shawn Penning,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                             |               |             |             |
|-----------------------------|---------------|-------------|-------------|
| **Description**             | **Author**    | **Version** | **Date**    |
| Initial Version             | Shawn Penning | 1.0         | 01-May-2017 |
| Updated for error injection | Avinash James | 2.0         | 23-Aug-2017 |

**  
**

<u>Table of Contents</u>1 Introduction 5

1.1 Purpose 5

1.2 Scope 5

2 CDD_NxtrTi & High-Level Description 6

3 Design details of software module 7

3.1 Graphical representation of CDD_NxtrTi 7

3.2 Data Flow Diagram 7

Component level DFD 7

Function level DFD 7

4 Constant Data Dictionary 8

4.1 Program (fixed) Constants 8

Embedded Constants 8

5 Software Component Implementation 9

5.1 Sub-Module Functions 9

5.1.1 Init: NxtrTiInit1 9

5.1.1.1 Design Rationale 9

5.1.1.2 Store Module Inputs to Local copies 9

5.1.1.3 (Processing of function)……… 9

5.1.1.4 Module Outputs 9

5.1.2 NxtrTiInit0 9

5.1.3 Per: NxtrTiPer1 9

5.1.3.1 Design Rationale 9

5.1.3.2 Store Module Inputs to Local copies 9

5.1.3.3 (Processing of function)……… 9

5.1.3.4 Store Local copy of outputs into Module Outputs 10

5.2 Server Runnables 10

5.2.1 GetRefTmr100MicroSec32bit 10

5.2.2 GetRefTmr1MicroSec32bit 10

5.2.3 GetTiSpan100MicroSec32bit 10

5.2.4 GetTiSpan1MicroSec32bit 10

5.3 Interrupt Functions 10

5.3.1 Interrupt Function Name 10

5.3.1.1 Design Rationale 11

5.4 Module Internal (Local) Functions 11

5.4.1 Local Function \#1 11

5.4.1.1 Design Rationale 11

5.4.1.2 Processing 11

5.5 GLOBAL Function/Macro Definitions 11

5.5.1 GLOBAL Function \#1 11

5.5.1.1 Design Rationale 11

5.5.1.2 processing 11

6 Known Limitations with Design 12

7 UNIT TEST CONSIDERATION 13

Appendix A Abbreviations and Acronyms 14

Appendix B Glossary 15

Appendix C References 16

# Introduction

## Purpose

## Scope

The following definitions are used throughout this document:

-   **<u>Shall</u>**: indicates a mandatory requirement without
    exception in compliance.

-   **<u>Should</u>**: indicates a mandatory requirement; exceptions
    allowed only with documented justification.

-   **<u>May</u>**: indicates an optional action.

# CDD_NxtrTi & High-Level Description

Nexteer Time Complex Driver

Refer to FDD to be created under CR EA4#164

# Design details of software module

Refer to FDD to be created under CR EA4#164

## Graphical representation of CDD_NxtrTi

##  [section]

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/AR102A_NxtrTi_Impl/doc/mediax/media/image2.png"
style="width:2.43333in;height:1.60833in" />

## Data Flow Diagram

Refer to FDD to be created under CR EA4#164

### Component level DFD

Refer to FDD to be created under CR EA4#164

### Function level DFD

Refer to FDD to be created under CR EA4#164

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name     | Resolution | Units  | Value |
|-------------------|------------|--------|-------|
| TMRFLTTHD_CNT_U32 | 1          | Counts | 200U  |

# Software Component Implementation

Refer to FDD to be created under CR EA4#164

## Sub-Module Functions

## Init: NxtrTiInit1

## Design Rationale

*None*

## Store Module Inputs to Local copies

*None*

## (Processing of function)………

Refer to FDD to be created under CR EA4#164

## Module Outputs

*None*

## NxtrTiInit0

#### Design Rationale

*To be called by the user during initialization. If timers are not
required prior to starting the*

*\* RTE, this function does not need to be called directly by a user.*

#### (Processing of function)

*Non-RTE version of Nexteer Time Initialization function. Calling this
function will initialize and*

*\* start the hardware timers used by this module if not already done.*

### 

## Per: NxtrTiPer1

## Design Rationale

*None*

## Store Module Inputs to Local copies

*None*

## (Processing of function)………

Refer to FDD to be created under CR EA4#164

## Store Local copy of outputs into Module Outputs

Refer to FDD to be created under CR EA4#164

## Server Runnables

## GetRefTmr100MicroSec32bit

#### Design Rationale

Refer to FDD to be created under CR EA4#164

####  (Processing of function)

Refer to FDD to be created under CR EA4#164

## GetRefTmr1MicroSec32bit

#### Design Rationale

Refer to FDD to be created under CR EA4#164

####  (Processing of function)

Refer to FDD to be created under CR EA4#164

## GetTiSpan100MicroSec32bit

#### Design Rationale

Refer to FDD to be created under CR EA4#164

####  (Processing of function)

Refer to FDD to be created under CR EA4#164

## GetTiSpan1MicroSec32bit

#### Design Rationale

Refer to FDD to be created under CR EA4#164

####  (Processing of function)

Refer to FDD to be created under CR EA4#164

## Interrupt Functions

*None*

## Interrupt Function Name

*None*

## Design Rationale

*None*

## Module Internal (Local) Functions

## Local Function \#1

None

|                      |                                                    |                               |                               |                               |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | (Exact name used)                                  | Type                          | Min                           | Max                           |
| **Arguments Passed** | (if none, write None)                              | \<Refer MDD guidelines\[1\]\> | \<Refer MDD guidelines\[1\]\> | \<Refer MDD guidelines\[1\]\> |
|                      | (Insert more rows for additional passed arguments) |                               |                               |                               |
| **Return Value**     | (if no value returned, write N/A)                  |                               |                               |                               |

## Design Rationale

## Processing

## GLOBAL Function/Macro Definitions

Refer to 5.1.2

## GLOBAL Function \#1

|                      |                                                    |                               |                               |                               |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | (Exact name used)                                  | Type                          | Min                           | Max                           |
| **Arguments Passed** | (if none, write None)                              | \<Refer MDD guidelines\[1\]\> | \<Refer MDD guidelines\[1\]\> | \<Refer MDD guidelines\[1\]\> |
|                      | (Insert more rows for additional passed arguments) |                               |                               |                               |
| **Return Value**     | (if no value returned, write N/A)                  |                               |                               |                               |

## Design Rationale

## processing

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

| **Ref. \#** | **Title**                                                                                                                                                             | **Version**       |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                    | v1.3.0 R4.0 Rev 2 |
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.00      |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 2.0               |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.1               |

{% endraw %}