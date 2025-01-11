---
layout: default
title: PhaDiscnct_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**PhaDiscnct**

**February 16, 2018**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                                     |                  |             |             |
|---------------------------|------------------|--------------|--------------|
| **Description**                     | **Author**       | **Version** | **Date**    |
| Initial Version                     | Krzysztof Byrski | 1           | 24-Aug-2017 |
| Updated as per Design version 1.2.0 | Krzysztof Byrski | 2           | 03-Oct-2017 |
| Updated as per Design version 1.3.0 | Krzysztof Byrski | 3           | 16-Feb-2018 |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [4](#introduction)](#introduction)

[1.1 Purpose [4](#purpose)](#purpose)

[1.2 Scope [4](#scope)](#scope)

[2 PhaDiscnct & High-Level Description
[5](#phadiscnct-high-level-description)](#phadiscnct-high-level-description)

[3 Design details of software module
[6](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of PhaDiscnct
[6](#graphical-representation-of-phadiscnct)](#graphical-representation-of-phadiscnct)

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

[5.1.1 Init: PhaDiscnctInit1 [8](#init-init1)](#init-init1)

[5.1.2 Per: PhaDiscnctPer1 [8](#per-per1)](#per-per1)

[5.1.3 Per: PhaDiscnctPer2
[8](#per-phadiscnctper2)](#per-phadiscnctper2)

[5.2 Server Runables [8](#server-runables)](#server-runables)

[5.3 Interrupt Functions
[9](#interrupt-functions)](#interrupt-functions)

[5.4 Module Internal (Local) Functions
[9](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 Local Function PerformDiag
[9](#local-function-performdiag)](#local-function-performdiag)

[5.4.2 Local Function ClosingStateBody
[9](#local-function-closingstatebody)](#local-function-closingstatebody)

[5.4.3 Local Function ClosedStateBody
[10](#local-function-closedstatebody)](#local-function-closedstatebody)

[5.4.4 Local Function OpeningStateBody
[10](#local-function-openingstatebody)](#local-function-openingstatebody)

[5.4.5 Local Function OpenedStateBody
[10](#local-function-openedstatebody)](#local-function-openedstatebody)

[5.4.6 Local Function SetHwPhaDiscnctIO
[11](#local-function-sethwphadiscnctio)](#local-function-sethwphadiscnctio)

[5.5 GLOBAL Function/Macro Definitions
[12](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[6 Known Limitations with Design
[13](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[14](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[15](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [16](#glossary)](#glossary)

[Appendix C References [17](#references)](#references)

# Introduction

## Purpose

MDD for ES330A_PhaDiscnct_Impl

## Scope

The following definitions are used throughout this document:

-   **<u>Shall</u>**: indicates a mandatory requirement without
    exception in compliance.

-   **<u>Should</u>**: indicates a mandatory requirement; exceptions
    allowed only with documented justification.

-   **<u>May</u>**: indicates an optional action.

# PhaDiscnct & High-Level Description

Phase Disconnect provides mechanism of disconnecting Motor Phases from
system in order to prevent generation of unintended negative or positive
motor torque. Phase Disconnect is controlled by System State and Motor
Control Gate Driver FET fault signals. Phase Disconnect functionality
provides support for loss of assist mitigation.

# Design details of software module

## Graphical representation of PhaDiscnct

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/ES330A_PhaDiscnct_Impl/doc/mediax/media/image1.png"
style="width:5.41667in;height:5.88542in" />

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

| Constant Name                    | Resolution | Units | Value |
|----------------------------------|------------|-------|-------|
| DIAGFLTPRMFAILTODIAGFLG_CNT_U08  | 1          | Cnt   | 8     |
| DIAGMOTCURRCORRDABITPOSN_CNT_U08 | 1          | Cnt   | 1     |
| DIAGMOTCURRCORRDBBITPOSN_CNT_U08 | 1          | Cnt   | 2     |
| DIAGMOTCURRCORRDCBITPOSN_CNT_U08 | 1          | Cnt   | 4     |
| DIAGSTCMPL_CNT_U08               | 1          | Cnt   | 2     |
| DIAGSTINI_CNT_U08                | 1          | Cnt   | 0     |
| DIAGSTPROC_CNT_U08               | 1          | Cnt   | 1     |
| DIAGSTSFAILTODIAG_CNT_U08        | 1          | Cnt   | 2     |
| DIAGSTSFAILTOOPEN_CNT_U08        | 1          | Cnt   | 1     |
| DIAGSTSPASS_CNT_U08              | 1          | Cnt   | 0     |
| DIAGTSTITRNPHAA_CNT_U08          | 1          | Cnt   | 2     |
| DIAGTSTITRNPHAB_CNT_U08          | 1          | Cnt   | 1     |
| DIAGTSTITRNPHAC_CNT_U08          | 1          | Cnt   | 0     |
| DISCNCTCURRCOMPIDX_CNT_U08       | 1          | Cnt   | 0     |
| OPERSTCLSPROGSN_CNT_U08          | 1          | Cnt   | 0     |
| OPERSTCLS_CNT_U08                | 1          | Cnt   | 1     |
| OPERSTOPENPROGSN_CNT_U08         | 1          | Cnt   | 2     |
| OPERSTOPEN_CNT_U08               | 1          | Cnt   | 3     |
| PHADISCNCTCMDALLOFF_CNT_U08      | 1          | Cnt   | 0     |
| PHADISCNCTCMDALLON_CNT_U08       | 1          | Cnt   | 7     |
| PHADISCNCTCMDAON_CNT_U08         | 1          | Cnt   | 1     |
| PHADISCNCTCMDBON_CNT_U08         | 1          | Cnt   | 2     |
| PHADISCNCTCMDCON_CNT_U08         | 1          | Cnt   | 4     |

# Software Component Implementation

## Sub-Module Functions

### Init: Init1

#### Design Rationale

Refer FDD

#### Module Outputs

Refer FDD

###  [section]

### Per: Per1

#### Design Rationale

Refer FDD

#### Store Module Inputs to Local copies

Refer FDD

#### (Processing of function)………

Refer FDD

#### Store Local copy of outputs into Module Outputs

Refer FDD

### Per: PhaDiscnctPer2

#### Design Rationale

Refer FDD

#### Store Module Inputs to Local copies

Refer FDD

#### (Processing of function)………

Refer FDD

#### Store Local copy of outputs into Module Outputs

Refer FDD

## Server Runables 

None

## Interrupt Functions

None

## Module Internal (Local) Functions

### Local Function PerformDiag

|                      |                                   |         |        |       |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | PerformDiag                       | Type    | Min    | Max   |
| **Arguments Passed** | MotCurrCorrdA_Ampr_T_f32          | float32 | -200.0 | 200.0 |
|                      | MotCurrCorrdB_Ampr_T_f32          | float32 | -200.0 | 200.0 |
|                      | MotCurrCorrdC_Ampr_T_f32          | float32 | -200.0 | 200.0 |
| **Return Value**     | PhaDiscnctDiagcPwmVect_Cnt_T_enum | enum    | 1      | 4     |

#### Design Rationale

Refer FDD

#### Processing

Refer FDD

### Local Function ClosingStateBody

|                      |                                 |         |       |      |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | ClosingStateBody                | Type    | Min   | Max  |
| **Arguments Passed** | StrtUpSt_Cnt_T_u08              | uint8   | 0     | 160  |
|                      | SysSt_Cnt_T_enum                | enum    | 0     | 3    |
| **Return Value**     | PhaDiscnctInactvTemp_Cnt_T_logl | boolean | FALSE | TRUE |

#### Design Rationale

Refer FDD

#### Processing

Refer FDD

###  Local Function ClosedStateBody

|                      |                             |       |     |     |
|----------------------|-----------------------------|-------|-----|-----|
| **Function Name**    | ClosedStateBody             | Type  | Min | Max |
| **Arguments Passed** | IvtrFetFltPha_Cnt_T_enum    | enum  | 0   | 4   |
|                      | IvtrFetFltTyp_Cnt_T_enum    | enum  | 0   | 4   |
|                      | SysSt_Cnt_T_enum            | enum  | 0   | 3   |
| **Return Value**     | PhaDiscnctCmdTemp_Cnt_T_u08 | Uint8 | 0   | 7   |

#### Design Rationale

Refer FDD

#### Processing

Refer FDD

### Local Function OpeningStateBody

|                      |                             |       |     |     |
|----------------------|-----------------------------|-------|-----|-----|
| **Function Name**    | OpeningStateBody            | Type  | Min | Max |
| **Arguments Passed** | IvtrFetFltTyp_Cnt_T_enum    | enum  | 0   | 4   |
|                      | SysSt_Cnt_T_enum            | enum  | 0   | 3   |
| **Return Value**     | PhaDiscnctCmdTemp_Cnt_T_u08 | uint8 | 0   | 7   |

#### Design Rationale

Refer FDD

#### Processing

Refer FDD

### Local Function OpenedStateBody

|                      |                                 |         |       |      |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | OpenedStateBody                 | Type    | Min   | Max  |
| **Arguments Passed** | IvtrFetFltPha_Cnt_T_enum        | enum    | 0     | 4    |
|                      | IvtrFetFltTyp_Cnt_T_enum        | enum    | 0     | 4    |
|                      | SysSt_Cnt_T_enum                | enum    | 0     | 3    |
| **Return Value**     | PhaDiscnctInactvTemp_Cnt_T_logl | boolean | FALSE | TRUE |
|                      | PhaDiscnctCmdTemp_Cnt_T_u08     | uint8   | 0     | 7    |

#### Design Rationale

Refer FDD

#### Processing

Refer FDD

### Local Function SetHwPhaDiscnctIO

|                      |                     |       |     |     |
|----------------------|---------------------|-------|-----|-----|
| **Function Name**    | SetHwPhaDiscnctIO   | Type  | Min | Max |
| **Arguments Passed** | PhaDiscnt_Cnt_T_u08 | uint8 | 0   | 7   |
| **Return Value**     | N/A                 |       |     |     |

#### Design Rationale

Refer FDD

#### Processing

Refer FDD

##  GLOBAL Function/Macro Definitions

None

# Known Limitations with Design

None

# UNIT TEST CONSIDERATION

None

# Abbreviations and Acronyms

| **Abbreviation or Acronym** | **Description** |
|-----------------------------|-----------------|
|                             |                 |

# Glossary

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

# References

| **Ref. \#** | **Title**                                                                                                                                          | **Version**                     |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf)) | v1.4.0 R4.0 Rev 3               |
| 2           | MDD Guideline EA4                                                                                                                                  | 1.02                            |
| 3           | EA4 Software Naming Conventions                                                                                                                    | 1.01                            |
| 4           | Software Design and Coding Standards                                                                                                               | 2.01                            |
| 5           | ES330A_PhaDiscnct_Design                                                                                                                           | See Synergy Sub Project Version |

{% endraw %}