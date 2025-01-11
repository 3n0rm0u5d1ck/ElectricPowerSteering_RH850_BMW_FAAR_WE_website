---
layout: default
title: RamMem_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**RamMem**

**Version: 4.0**

**Release Date: 11-Jul-2018**

**Prepared By:**

**Software Engineering,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
**

**<u>Document Change History</u>**

|             |                                                             |                    |             |
|--------|------------------------------------|-----------------|------------|
| **Version** | **Description**                                             | **Author**         | **Date**    |
| 1           | Initial Version                                             | Selva Sengottaiyan | 06-Apr-2016 |
| 2           | Created local functions for reducing cyclometric complexity | Selva Sengottaiyan | 26-Jun-2016 |
| 3           | Changed SPI ECC handling from interrupt to polling          | Avinash James      | 23-Aug-2016 |
| 4           | Updated local function arguments to match code              | Bri Spencer        | 11-Jul-2018 |

**  
**

**<u>Table of Contents</u>**

[1 RamMem & High-Level Description
[5](#rammem-high-level-description)](#rammem-high-level-description)

[2 Design details of software module
[6](#design-details-of-software-module)](#design-details-of-software-module)

[2.1 Graphical representation of RamMem
[6](#graphical-representation-of-rammem)](#graphical-representation-of-rammem)

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

[4.1.1 Init: RamMemInit1 [8](#init-rammeminit1)](#init-rammeminit1)

[4.1.1.1 Design Rationale [8](#design-rationale)](#design-rationale)

[4.1.1.2 Module Outputs [8](#module-outputs)](#module-outputs)

[4.1.2 Per: RamMemPer1 [8](#per-rammemper1)](#per-rammemper1)

[4.1.2.1 Design Rationale [8](#design-rationale-1)](#design-rationale-1)

[4.1.2.2 Store Module Inputs to Local copies
[8](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[4.1.2.3 (Processing of function) …
[8](#processing-of-function)](#processing-of-function)

[4.1.2.4 Store Local copy of outputs into Module Outputs
[8](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[4.2 Server Runnables [8](#server-runnables)](#server-runnables)

[4.2.1 RamMemLclRamSngBitEcc
[8](#rammemlclramsngbitecc)](#rammemlclramsngbitecc)

[4.2.1.1 Design Rationale [8](#design-rationale-2)](#design-rationale-2)

[4.2.1.2 (Processing of function) …
[8](#processing-of-function-1)](#processing-of-function-1)

[4.3 Interrupt Functions
[8](#interrupt-functions)](#interrupt-functions)

[4.4 Module Internal (Local) Functions
[9](#module-internal-local-functions)](#module-internal-local-functions)

[4.4.1 Local Function \#1 [9](#local-function-1)](#local-function-1)

[4.4.1.1 Design Rationale [9](#design-rationale-3)](#design-rationale-3)

[4.4.1.2 Processing [9](#processing)](#processing)

[4.4.2 Local Function \#2 [9](#local-function-2)](#local-function-2)

[4.4.2.1 Design Rationale [9](#design-rationale-4)](#design-rationale-4)

[4.4.2.2 Processing [9](#processing-1)](#processing-1)

[4.4.3 Local Function \#3 [9](#local-function-3)](#local-function-3)

[4.4.3.1 Design Rationale [9](#design-rationale-5)](#design-rationale-5)

[4.4.3.2 Processing [9](#processing-2)](#processing-2)

[4.4.4 Local Function \#4 [10](#local-function-4)](#local-function-4)

[4.4.4.1 Design Rationale
[10](#design-rationale-6)](#design-rationale-6)

[4.4.4.2 Processing [10](#processing-3)](#processing-3)

[4.4.5 Local Function \#5 [10](#local-function-5)](#local-function-5)

[4.4.5.1 Design Rationale
[10](#design-rationale-7)](#design-rationale-7)

[4.4.5.2 Processing [10](#processing-4)](#processing-4)

[4.5 GLOBAL Function/Macro Definitions
[10](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[5 Known Limitations with Design
[11](#known-limitations-with-design)](#known-limitations-with-design)

[6 UNIT TEST CONSIDERATION
[12](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[13](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [14](#glossary)](#glossary)

[Appendix C References [15](#references)](#references)

# RamMem & High-Level Description

Refer to FDD

# Design details of software module

## Graphical representation of RamMem

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/CM103A_RamMem_Impl/doc/mediax/media/image1.png"
style="width:2.375in;height:2in" />

## Data Flow Diagram

### Component level DFD

None

### Function level DFD

None

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name             | Resolution | Units | Value       |
|---------------------------|------------|-------|-------------|
| LCLRAMBASADR_CNT_U32      | 1          | Cnt   | 0xFEB80000U |
| VLDADRTESTBITMASK_CNT_U32 | 1          | Cnt   | 0xFFFE0000U |
| VLDADRTESTRES_CNT_U32     | 1          | Cnt   | 0x00060000U |
| WORDLINEADRMASK_CNT_U32   | 1          | Cnt   | 0xFFFFFF1FU |
| BNK0ERRCLRMASK_CNT_U32    | 1          | Cnt   | 0x00000001U |
| BNK1ERRCLRMASK_CNT_U32    | 1          | Cnt   | 0x00000002U |
| BNK2ERRCLRMASK_CNT_U32    | 1          | Cnt   | 0x00000004U |
| BNK3ERRCLRMASK_CNT_U32    | 1          | Cnt   | 0x00000008U |
| BNK0SNGBITERRMASK_CNT_U32 | 1          | Cnt   | 0x00000001U |
| BNK1SNGBITERRMASK_CNT_U32 | 1          | Cnt   | 0x00000100U |
| BNK2SNGBITERRMASK_CNT_U32 | 1          | Cnt   | 0x00010000U |
| BNK3SNGBITERRMASK_CNT_U32 | 1          | Cnt   | 0x01000000U |

Also see FDD DataDict.m file for constant definitions.

# Software Component Implementation

## Sub-Module Functions

## Init: RamMemInit1

##  Design Rationale

None

##  Module Outputs

Refer to FDD

## Per: RamMemPer1

##  Design Rationale

None

##  Store Module Inputs to Local copies

Refer to FDD

##  (Processing of function) …

Refer to FDD

##  Store Local copy of outputs into Module Outputs

Refer to FDD

## Server Runnables 

## RamMemLclRamSngBitEcc

## Design Rationale

None

##  (Processing of function) …

Refer to FDD

## Interrupt Functions

None

## Module Internal (Local) Functions

## Local Function \#1

|                      |           |      |     |     |
|----------------------|-----------|------|-----|-----|
| **Function Name**    | SpiEccErr | Type | Min | Max |
| **Arguments Passed** | None      |      |     |     |
| **Return Value**     | N/A       |      |     |     |

##  Design Rationale

None

##  Processing

Refer to FDD

## Local Function \#2

|                      |          |      |     |     |
|----------------------|----------|------|-----|-----|
| **Function Name**    | FrEccErr | Type | Min | Max |
| **Arguments Passed** | None     |      |     |     |
| **Return Value**     | N/A      |      |     |     |

##  Design Rationale

None

##  Processing

Refer to FDD

## Local Function \#3

|                      |           |      |     |     |
|----------------------|-----------|------|-----|-----|
| **Function Name**    | CanEccErr | Type | Min | Max |
| **Arguments Passed** | None      |      |     |     |
| **Return Value**     | N/A       |      |     |     |

##  Design Rationale

None

##  Processing

Refer to FDD

## Local Function \#4

|                      |                          |        |     |            |
|----------------------|--------------------------|--------|-----|------------|
| **Function Name**    | RamFailrModClassnChk     | Type   | Min | Max        |
| **Arguments Passed** | LclRamFailrAdr_Cnt_T_u32 | uint32 | 0   | 4294967295 |
|                      | ErrClrMask_Cnt_T_u32     | uint32 | 0   | 4294967295 |
|                      | SngBitErrMask_Cnt_T_u32  | uint32 | 0   | 4294967295 |
| **Return Value**     | N/A                      |        |     |            |

##  Design Rationale

None

##  Processing

Refer to FDD

## Local Function \#5

|                      |                          |        |     |            |
|----------------------|--------------------------|--------|-----|------------|
| **Function Name**    | RamMemLclRamFailrChk     | Type   | Min | Max        |
| **Arguments Passed** | LclRamFailrAdr_Cnt_T_u32 | uint32 | 0   | 4294967295 |
| **Return Value**     | N/A                      |        |     |            |

##  Design Rationale

None

##  Processing

Refer to FDD

## GLOBAL Function/Macro Definitions

None

# Known Limitations with Design

Local RAM single-bit PIM for address store will be overwritten for each
bank; this can be avoided by defining PIMs for each memory block. Will
be reviewed POST IVER build.

# UNIT TEST CONSIDERATION

None

####### Abbreviations and Acronyms

| **Abbreviation or Acronym** | **Description**            |
|-----------------------------|----------------------------|
| FDD                         | Functional Design Document |
| MDD                         | Module Design Document     |
| DFD                         | Data Flow Diagram          |

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

| **Ref. \#** | **Title**                                                                                                                                                           | **Version**                    |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping                                                                                                                             | v1.3.0 R4.0 Rev 2              |
| 2           | MDD Guideline                                                                                                                                                       | EA4 1.02                       |
| 3           | EA4 [Software Naming Conventions](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc) | 1.03                           |
| 4           | Software Design and Coding Standards                                                                                                                                | 2.01                           |
| 5           | FDD: CM103A_RamMem_Design                                                                                                                                           | See Synergy subproject version |

{% endraw %}