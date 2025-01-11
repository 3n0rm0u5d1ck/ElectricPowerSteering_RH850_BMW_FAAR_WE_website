---
layout: default
title: BmwStReqMgr_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**BmwStReqMgr**

**May 22, 2018**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                                        |                  |             |             |
|--------------------------------|------------------|-----------|------------|
| **Description**                        | **Author**       | **Version** | **Date**    |
| Initial Version                        | Krzysztof Byrski | 1           | 24-Oct-2017 |
| Update to FDD 2.0.0                    | Mateusz Bartocha | 2           | 14-Nov-17   |
| Updated Diagram                        | Matthew Leser    | 3           | 10-Jan-18   |
| Updated TargetECUState function inputs | Matthew Leser    | 4           | 23-Feb-18   |
| Updated local functions                | Krzysztof Byrski | 5           | 22-Mar-2018 |
| Update to FDD 4.0.0                    | Krzysztof Byrski | 6           | 22-May-2018 |

**  
**

<u>Table of Contents</u>[1 Introduction
[4](#introduction)](#introduction)

[1.1 Purpose [4](#purpose)](#purpose)

[1.2 Scope [4](#scope)](#scope)

[2 BmwStReqMgr & High-Level Description
[5](#bmwstreqmgr-high-level-description)](#bmwstreqmgr-high-level-description)

[3 Design details of software module
[6](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of BmwStReqMgr
[6](#graphical-representation-of-bmwstreqmgr)](#graphical-representation-of-bmwstreqmgr)

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

[5.1.1 Init: BmwStReqMgrInit1 [8](#init-init1)](#init-init1)

[5.1.2 Per: BmwStReqMgrPer1 [8](#per-per1)](#per-per1)

[5.2 Server Runables [8](#server-runables)](#server-runables)

[5.3 Interrupt Functions
[8](#interrupt-functions)](#interrupt-functions)

[5.4 Module Internal (Local) Functions
[9](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 Local Function Override
[9](#local-function-override)](#local-function-override)

[5.4.2 Local Function CalcOfStsSteerAssiAndEpsFctSts
[9](#local-function-calcofstssteerassiandepsfctsts)](#local-function-calcofstssteerassiandepsfctsts)

[5.4.3 Local Function StsDrvrActvyTmr
[10](#local-function-stsdrvractvytmr)](#local-function-stsdrvractvytmr)

[5.4.4 Local Function AssiOnToOffFlg
[10](#local-function-assiontooffflg)](#local-function-assiontooffflg)

[5.4.5 Local Function AllwToOff
[11](#local-function-allwtooff)](#local-function-allwtooff)

[5.4.6 Local Function TargetECUState
[11](#local-function-targetecustate)](#local-function-targetecustate)

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

Module Design Document for CF069A_BmwStReqMgr_Impl

## Scope

The following definitions are used throughout this document:

-   **<u>Shall</u>**: indicates a mandatory requirement without
    exception in compliance.

-   **<u>Should</u>**: indicates a mandatory requirement; exceptions
    allowed only with documented justification.

-   **<u>May</u>**: indicates an optional action.

# BmwStReqMgr & High-Level Description

This function will be responsible for requesting transitions between the
states and modes of the steering system based on vehicle signals.

# Design details of software module

## Graphical representation of BmwStReqMgr

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/CF069A_BmwStReqMgr_Impl/doc/mediax/media/image2.png"
style="width:4.1875in;height:5.98088in" />

## Data Flow Diagram

Refer FDD

### Component level DFD

None

### Function level DFD

None

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name | Resolution | Units | Value |
|---------------|------------|-------|-------|
| \-            |            |       |       |
|               |            |       |       |
|               |            |       |       |
|               |            |       |       |
|               |            |       |       |
|               |            |       |       |

\*Refer FDD for local constants

# Software Component Implementation

## Sub-Module Functions

The sub-module functions are grouped based on similar functionality that
needs to be executed in a given “State” of the system (refer States and
Modes). For a given module, the MDD will identify the type and number of
sub-modules required. The sub-module types are described below.

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

## Server Runables 

None

## Interrupt Functions

None

## Module Internal (Local) Functions

### Local Function Override

|                      |                         |         |       |      |
|----------------------|-------------------------|---------|-------|------|
| **Function Name**    | Override                | Type    | Min   | Max  |
| **Arguments Passed** | BmwVehCdnVld_Cnt_T_logl | boolean | FALSE | TRUE |
|                      | BmwVehCdn_Cnt_T_enum    | enum    | 1     | 15   |
| **Return Value**     | BmwVehCdnVld_Cnt_T_logl | boolean | FALSE | TRUE |
|                      | BmwVehCdn_Cnt_T_enum    | enum    | 1     | 15   |

#### Design Rationale

Refer FDD

#### Processing

Implementation of Simulink block Override

### Local Function CalcOfStsSteerAssiAndEpsFctSts

|                      |                                          |         |       |      |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | CalcOfStsSteerAssiAndEpsFctSts           | Type    | Min   | Max  |
| **Arguments Passed** | SysSt_Cnt_T_enum                         | enum    | 0     | 3    |
|                      | ThermRednFac_Uls_T_f32                   | float32 | 0     | 1    |
|                      | RcvrlFltPrsnt_Cnt_T_logl                 | boolean | FALSE | TRUE |
|                      | DiagcStsNonRcvrlReqDiFltPrsnt_Cnt_T_logl | boolean | FALSE | TRUE |
|                      | PwrLimrRednFac_Uls_T_f32                 | float32 | 0     | 1    |
| **Return Value**     | StsSteerAssi_Cnt_T_enum                  | enum    | 0     | 1    |
|                      | BmwEpsFctSts_Cnt_T_enum                  | enum    | 96    | 224  |

#### Design Rationale

Refer FDD

#### Processing

Implementation of Simulink block
DeterminationOfStatusSteeringAssistAndEpsFctSts

### Local Function StsDrvrActvyTmr

|                      |                         |         |     |     |
|----------------------|-------------------------|---------|-----|-----|
| **Function Name**    | StsDrvrActvyTmr         | Type    | Min | Max |
| **Arguments Passed** | HwTq_HwNwtMtr_T_f32     | float32 | -10 | 10  |
| **Return Value**     | StsDrvrActvy_Cnt_T_enum | enum    | 0   | 1   |

#### Design Rationale

Refer FDD

#### Processing

Implementation of Simulink block StsDrvrActvyTmr

### Local Function AssiOnToOffFlg

|                      |                                          |         |       |      |
|-------------|------------------------------------|--------|--------|--------|
| **Function Name**    | AssiOnToOffFlg                           | Type    | Min   | Max  |
| **Arguments Passed** | DiagcStsNonRcvrlReqDiFltPrsnt_Cnt_T_logl | boolean | FALSE | TRUE |
|                      | BmwVehCdnVld_Cnt_T_logl                  | boolean | FALSE | TRUE |
|                      | BmwVehSpdSts_Cnt_T_enum                  | enum    | 1     | 15   |
|                      | VehSpd_Kph_T_f32                         | float32 | 0     | 350  |
|                      | BmwVehCdn_Cnt_T_enum                     | enum    | 1     | 15   |
|                      | StsDrvrActvy_Cnt_T_enum                  | enum    | 0     | 1    |
| **Return Value**     | AssiOnToOffFlg_Cnt_T_logl                | boolean | FALSE | TRUE |

#### Design Rationale

Refer FDD

#### Processing

Implementation of Simulink block AssiOnToOffFlg

### Local Function AllwToOff

|                      |                      |         |       |      |
|----------------------|----------------------|---------|-------|------|
| **Function Name**    | AllwToOff            | Type    | Min   | Max  |
| **Arguments Passed** | BmwVehCdn_Cnt_T_enum | enum    | 1     | 15   |
|                      | IgnLine_Cnt_T_logl   | boolean | FALSE | TRUE |
| **Return Value**     | AllwToOff_Cnt_T_logl | boolean | FALSE | TRUE |

#### Design Rationale

Refer FDD

#### Processing

Implementation of Simulink block AllwToOff

### Local Function TargetECUState

|                      |                                          |         |       |      |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | TargetECUState                           | Type    | Min   | Max  |
| **Arguments Passed** | DiagcStsNonRcvrlReqDiFltPrsnt_Cnt_T_logl | enum    | FALSE | TRUE |
|                      | BmwVehCdn_Cnt_T_enum                     | enum    | 1     | 15   |
|                      | AssiOnToOffFlg_Cnt_T_logl                | boolean | FALSE | TRUE |
|                      | AllwTranToDi_Cnt_T_logl                  | boolean | FALSE | TRUE |
|                      | IgnLine_Cnt_T_logl                       | boolean | FALSE | TRUE |
|                      | AllwToOff_Cnt_T_logl                     | boolean | FALSE | TRUE |
| **Return Value**     | TarEcuSt_Cnt_T_enum                      | enum    | 0     | 3    |
|                      | PwrSplyEnaReq_Cnt_T_logl                 | boolean | FALSE | TRUE |
|                      | SysStReqEna_Cnt_T_logl                   | boolean | FALSE | TRUE |
|                      | SysOperMotTqCmdSca_Uls_T_f32             | float   | 0     | 1    |

#### Design Rationale

Refer FDD

#### Processing

Implementation of Simulink block TargetECUState

## GLOBAL Function/Macro Definitions

None

# Known Limitations with Design

None

# UNIT TEST CONSIDERATION

None

# Abbreviations and Acronyms

| **Abbreviation or Acronym** | **Description**                              |
|------------------------|------------------------------------------------|
| FDD                         | Functional Design Document. (See references) |

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

| **Ref. \#** | **Title**                                                                                                                                                                                                                             | **Version**                     |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](https://www.autosar.org/fileadmin/files/standards/classic/4-0/software-architecture/implementation-integration/standard/AUTOSAR_SWS_MemoryMapping.pdf)) | v1.4.0 R4.0 Rev 3               |
| 2           | MDD Guideline EA4                                                                                                                                                                                                                     | 1.02                            |
| 3           | EA4 Software Naming Conventions                                                                                                                                                                                                       | 1.01                            |
| 4           | Software Design and Coding Standards                                                                                                                                                                                                  | 2.01                            |
| 5           | CF069A_BmwStReqMgr_Design                                                                                                                                                                                                             | See Synergy Sub Project Version |

{% endraw %}