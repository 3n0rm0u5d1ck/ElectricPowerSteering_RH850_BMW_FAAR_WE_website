---
layout: default
title: BmwTqOvrlCdngAndDrvgDynFac_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**BmwTqOvrlCdngAndDrvgDynFac**

**April 26, 2018**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Tychy, Poland  
<u>Change History</u>**

|                 |                   |             |             |
|-----------------|-------------------|-------------|-------------|
| **Description** | **Author**        | **Version** | **Date**    |
| Initial version | Marek Brykczyński | 1           | 26-Apr-2018 |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [5](#introduction)](#introduction)

[1.1 Purpose [5](#purpose)](#purpose)

[1.2 Scope [5](#scope)](#scope)

[2 BmwTqOvrlCdngAndDrvgDynFac & High-Level Description
[6](#bmwtqovrlcdnganddrvgdynfac-high-level-description)](#bmwtqovrlcdnganddrvgdynfac-high-level-description)

[3 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of BmwTqOvrlCdngAndDrvgDynFac
[7](#graphical-representation-of-bmwtqovrlcdnganddrvgdynfac)](#graphical-representation-of-bmwtqovrlcdnganddrvgdynfac)

[3.2 Data Flow Diagram [7](#data-flow-diagram)](#data-flow-diagram)

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

[5.1.1 Init: BmwTqOvrlCdngAndDrvgDynFacInit1
[10](#init-bmwtqovrlcdnganddrvgdynfacinit1)](#init-bmwtqovrlcdnganddrvgdynfacinit1)

[5.1.2 Per: BmwTqOvrlCdngAndDrvgDynFacPer1
[10](#per-bmwtqovrlcdnganddrvgdynfacper1)](#per-bmwtqovrlcdnganddrvgdynfacper1)

[5.2 Server Runables [10](#server-runables)](#server-runables)

[5.3 Interrupt Functions
[10](#interrupt-functions)](#interrupt-functions)

[5.4 Module Internal (Local) Functions
[11](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 CalcCdndTqOvrl [11](#calccdndtqovrl)](#calccdndtqovrl)

[5.4.2 CalcnDampgCmdSca [11](#calcndampgcmdsca)](#calcndampgcmdsca)

[5.4.3 CalcnEffortCmdSca [11](#calcneffortcmdsca)](#calcneffortcmdsca)

[5.4.4 CalcnLimdCdndTqOvrl
[11](#calcnlimdcdndtqovrl)](#calcnlimdcdndtqovrl)

[5.4.5 CalcnRtnCmdSca [12](#calcnrtncmdsca)](#calcnrtncmdsca)

[5.4.6 StTranDetn [12](#sttrandetn)](#sttrandetn)

[5.4.7 TqOvrlCdng [12](#tqovrlcdng)](#tqovrlcdng)

[5.5 GLOBAL Function/Macro Definitions
[12](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[6 Known Limitations with Design
[14](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[15](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[16](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [17](#glossary)](#glossary)

[Appendix C References [18](#references)](#references)

# Introduction

## Purpose

Module Design Document for CF040A_BmwTqOvrlCdngAndDrvgDynFac_Impl.

## Scope

The following definitions are used throughout this document:

-   **<u>Shall</u>**: indicates a mandatory requirement without
    exception in compliance.

-   **<u>Should</u>**: indicates a mandatory requirement; exceptions
    allowed only with documented justification.

-   **<u>May</u>**: indicates an optional action.

# BmwTqOvrlCdngAndDrvgDynFac & High-Level Description

The BMW Torque Overlay Conditioning And Driving Dynamic Factor function
handles the filtering and ramping of the BMW Output Torque Overlay
Command functionality and conditioning of the BMW Driving Dynamic
Factors for Effort/Assist, Return and Damping.

# Design details of software module

## Graphical representation of BmwTqOvrlCdngAndDrvgDynFac

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/CF040A_BmwTqOvrlCdngAndDrvgDynFac_Impl/doc/mediax/media/image1.png"
style="width:5.57292in;height:6.91667in" />

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

| Constant Name | Resolution | Units | Value |
|---------------|------------|-------|-------|
| \-            |            |       |       |

Refer FDD for local constants.

# Software Component Implementation

## Sub-Module Functions

The sub-module functions are grouped based on similar functionality that
needs to be executed in a given “State” of the system (refer States and
Modes). For a given module, the MDD will identify the type and number of
sub-modules required. The sub-module types are described below.

### Init: BmwTqOvrlCdngAndDrvgDynFacInit1

#### Design Rationale

Refer FDD

#### Module Outputs

Refer FDD

###  [section]

### Per: BmwTqOvrlCdngAndDrvgDynFacPer1

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

### CalcCdndTqOvrl

|                      |                                           |         |       |      |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | CalcCdndTqOvrl                            | Type    | Min   | Max  |
| **Arguments Passed** | FildBmwTarSteerTqDrvrActr_MotNwtMtr_T_f32 | float32 | -8.8  | 8.8  |
|                      | BmwTarSteerTqDrvrActr_MotNwtMtr_T_f32     | float32 | -8.8  | 8.8  |
|                      | BmwDrvgDynErrIfActv_Cnt_T_logl            | boolean | FALSE | TRUE |
| **Return Value**     | CdndTqOvrl_MotNwtMtr_T_f32                | float32 | -8.8  | 8.8  |

####  [section-1]

### CalcnDampgCmdSca

|                      |                            |         |       |      |
|----------------------|----------------------------|---------|-------|------|
| **Function Name**    | CalcnDampgCmdSca           | Type    | Min   | Max  |
| **Arguments Passed** | DrvgDynActv_Cnt_T_logl     | boolean | FALSE | TRUE |
|                      | ReqdDampgCmdSca_Uls_T_f32  | float32 | 0     | 1    |
|                      | DrvgDynActvTrig_Cnt_T_logl | boolean | FALSE | TRUE |
| **Return Value**     | \-                         | \-      | \-    | \-   |

### CalcnEffortCmdSca

|                      |                            |         |       |      |
|----------------------|----------------------------|---------|-------|------|
| **Function Name**    | CalcnEffortCmdSca          | Type    | Min   | Max  |
| **Arguments Passed** | DrvgDynActv_Cnt_T_logl     | boolean | FALSE | TRUE |
|                      | ReqdEffortCmdSca_Uls_T_f32 | float32 | 1     | 2    |
|                      | DrvgDynActvTrig_Cnt_T_logl | boolean | FALSE | TRUE |
| **Return Value**     | \-                         | \-      | \-    | \-   |

### CalcnLimdCdndTqOvrl

|                      |                            |         |      |       |
|----------------------|----------------------------|---------|------|-------|
| **Function Name**    | CalcnLimdCdndTqOvrl        | Type    | Min  | Max   |
| **Arguments Passed** | CdndTqOvrl_MotNwtMtr_T_f32 | float32 | -8.8 | 8.8   |
|                      | VehSpd_Kph_T_u9p7          | uint16  | 0    | 68408 |
| **Return Value**     | \-                         | \-      | \-   | \-    |

### CalcnRtnCmdSca

|                      |                            |         |       |      |
|----------------------|----------------------------|---------|-------|------|
| **Function Name**    | CalcnRtnCmdSca             | Type    | Min   | Max  |
| **Arguments Passed** | DrvgDynActv_Cnt_T_logl     | boolean | FALSE | TRUE |
|                      | ReqdRtnCmdSca_Uls_T_f32    | float32 | 0     | 1    |
|                      | DrvgDynActvTrig_Cnt_T_logl | boolean | FALSE | TRUE |
| **Return Value**     | \-                         | \-      | \-    | \-   |

### StTranDetn

|                      |                                           |         |       |      |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | StTranDetn                                | Type    | Min   | Max  |
| **Arguments Passed** | DrvgDynIfSt_Cnt_T_u08                     | uint8   | 32    | 255  |
|                      | BmwTarSteerTqDrvrActr_MotNwtMtr_T_f32     | float32 | -8.8  | 8.8  |
|                      | FildBmwTarSteerTqDrvrActr_MotNwtMtr_T_f32 | float32 | -8.8  | 8.8  |
| **Return Value**     | OutpRstTrig_Cnt_T_logl                    | boolean | FALSE | TRUE |

### TqOvrlCdng

|                      |                                       |         |       |       |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | TqOvrlCdng                            | Type    | Min   | Max   |
| **Arguments Passed** | DrvgDynIfSt_Cnt_T_u08                 | uint8   | 32    | 255   |
|                      | BmwTarSteerTqDrvrActr_MotNwtMtr_T_f32 | float32 | -8.8  | 8.8   |
|                      | VehSpd_Kph_T_u9p7                     | uint16  | 0     | 68408 |
|                      | BmwDrvgDynErrIfActv_Cnt_T_logl        | boolean | FALSE | TRUE  |
| **Return Value**     | OutpRstTrig_Cnt_T_logl                | boolean | FALSE | TRUE  |

#### Design Rationale

Refer FDD

#### Processing

Refer FDD

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
| 5           | CF011A_BmwTqOvrlCdngAndDrvgDynFac_Design                                                                                                                                                                                              | See Synergy Sub Project Version |

{% endraw %}