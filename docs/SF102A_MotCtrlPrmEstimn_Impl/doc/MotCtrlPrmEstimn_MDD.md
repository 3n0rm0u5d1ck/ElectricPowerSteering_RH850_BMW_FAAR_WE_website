---
layout: default
title: MotCtrlPrmEstimn_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**MotCtrlPrmEstimn**

**06-Dec-2017**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Brendon Binder,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|             |                                                                                 |            |             |               |
|-----|-----------------------------------|------------|---------|------------|
| **Sl. No.** | **Description**                                                                 | **Author** | **Version** | **Date**      |
| 1           | Initial Version                                                                 | Rijvi      | 1.0         | 20-JUN-2015   |
| 2           | Updated per design rev. 1.5.0                                                   | Rijvi      | 2.0         | 07-APRIL-2016 |
| 3           | Updated per design rev. 2.1.0                                                   | ML         | 3.0         | 29-NOV-2016   |
| 4           | New Input added MotAndThermProtnLoaMod and deleted IvtrLoaMtgtnEna              | TATA       | 4.0         | 25-SEP-2017   |
| 5           | Removed local function which didn’t exist, migrated document to latest template | BRB        | 5.0         | 06-DEC-2017   |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [5](#introduction)](#introduction)

[1.1 Purpose [5](#purpose)](#purpose)

[1.2 Scope [5](#scope)](#scope)

[2 MotCtrlPrmEstimn & High-Level Description
[6](#motctrlprmestimn-high-level-description)](#motctrlprmestimn-high-level-description)

[3 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of MotCtrlPrmEstimn
[7](#graphical-representation-of-motctrlprmestimn)](#graphical-representation-of-motctrlprmestimn)

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

[5.1 Sub-Module Functions
[9](#sub-module-functions)](#sub-module-functions)

[5.1.1 Init: MotCtrlPrmEstimnInit1 [9](#init-init1)](#init-init1)

[5.1.1.1 Design Rationale [9](#design-rationale)](#design-rationale)

[5.1.1.2 Module Outputs [9](#module-outputs)](#module-outputs)

[5.1.2 Per: MotCtrlPrmEstimnPer1 [9](#per-per1)](#per-per1)

[5.1.2.1 Design Rationale [9](#design-rationale-1)](#design-rationale-1)

[5.1.2.2 Store Module Inputs to Local copies
[9](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[5.1.2.3 (Processing of function)………
[9](#processing-of-function)](#processing-of-function)

[5.1.2.4 Store Local copy of outputs into Module Outputs
[9](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[5.1.1 Per: MotCtrlPrmEstimnPer2
[9](#per-motctrlprmestimnper2)](#per-motctrlprmestimnper2)

[5.1.1.1 Design Rationale [9](#design-rationale-2)](#design-rationale-2)

[5.1.1.2 Store Module Inputs to Local copies
[9](#store-module-inputs-to-local-copies-1)](#store-module-inputs-to-local-copies-1)

[5.1.1.3 (Processing of function)………
[9](#processing-of-function-1)](#processing-of-function-1)

[5.1.1.4 Store Local copy of outputs into Module Outputs
[9](#store-local-copy-of-outputs-into-module-outputs-1)](#store-local-copy-of-outputs-into-module-outputs-1)

[5.2 Server Runnables [10](#server-runnables)](#server-runnables)

[5.2.1 SetMotPrmNomEol [10](#setmotprmnomeol)](#setmotprmnomeol)

[5.2.1.1 Design Rationale
[10](#design-rationale-3)](#design-rationale-3)

[5.2.1.2 (Processing of function)………
[10](#processing-of-function-2)](#processing-of-function-2)

[5.2.2 SetMotPrmNomEol [10](#setmotprmnomeol-1)](#setmotprmnomeol-1)

[5.2.2.1 Design Rationale
[10](#design-rationale-4)](#design-rationale-4)

[5.2.2.2 (Processing of function)………
[10](#processing-of-function-3)](#processing-of-function-3)

[5.3 Interrupt Functions
[10](#interrupt-functions)](#interrupt-functions)

[5.4 Module Internal (Local) Functions
[10](#module-internal-local-functions)](#module-internal-local-functions)

[5.5 GLOBAL Function/Macro Definitions
[10](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[6 Known Limitations with Design
[11](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[12](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[13](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [14](#glossary)](#glossary)

[Appendix C References [15](#references)](#references)

# Introduction

## Purpose

## Scope

# MotCtrlPrmEstimn & High-Level Description

> Please refer FDD

# Design details of software module

## Graphical representation of MotCtrlPrmEstimn

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/SF102A_MotCtrlPrmEstimn_Impl/doc/mediax/media/image1.png"
style="width:4.24306in;height:6.04167in" />

## Data Flow Diagram

Refer FDD

### Component level DFD

Refer FDD

### Function level DFD

Refer FDD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name                | Resolution | Units | Value |
|------------------------------|------------|-------|-------|
| BITMASK2_CNT_U08             | 1          | Cnt   | 2U    |
| Refer constants from .m file |            |       |       |

# Software Component Implementation

## Sub-Module Functions

### Init: Init1

## Design Rationale

*Refer to FDD*

## Module Outputs

*Refer to FDD*

###  [section]

### Per: Per1

## Design Rationale

*Refer to FDD*

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD*

## Store Local copy of outputs into Module Outputs

*Refer to FDD*

### Per: MotCtrlPrmEstimnPer2

## Design Rationale

*Refer to FDD*

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD*

## Store Local copy of outputs into Module Outputs

*Refer to FDD*

## Server Runnables 

## SetMotPrmNomEol

## Design Rationale

*None*

##  (Processing of function)………

*See* GetMotPrmNomEol *block in FDD*

## SetMotPrmNomEol

## Design Rationale

*None*

##  (Processing of function)………

*See* SetMotPrmNomEol *block in FDD*

## Interrupt Functions

*None*

## Module Internal (Local) Functions

None

## GLOBAL Function/Macro Definitions

None

# Known Limitations with Design

CurrMeasLoaMtgtnEna and FetLoaMtgtnEna are terminated. These flags need
not be computed at all.

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

| **Ref. \#** | **Title**                                                                                                                                                                                                                | **Version**                    |
|---------|----------------------------------------|------------------------|
| 1           | [AUTOSAR Specification of Memory Mapping](http://www.autosar.org/fileadmin/files/standards/classic/4-0/software-architecture/implementation-integration/standard/AUTOSAR_SWS_MemoryMapping.pdf?_sm_au_=iVVkW148vj2N42wj) | v1.3.0 R4.0 Rev 2              |
| 2           | MDD Guideline                                                                                                                                                                                                            | EA4 01.00.00                   |
| 3           | EA4 Software Naming Conventions                                                                                                                                                                                          | 01.01.00                       |
| 4           | Software Design and Coding Standards                                                                                                                                                                                     | 2.1                            |
| 5           | FDD – SF102A Motor Control Parameter Estimation                                                                                                                                                                          | See Synergy subproject version |

{% endraw %}