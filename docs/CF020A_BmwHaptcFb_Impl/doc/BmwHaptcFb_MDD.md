---
layout: default
title: BmwHaptcFb_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**BmwHaptcFb**

**May 18, 2018**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                 |                  |             |             |
|-----------------|------------------|-------------|-------------|
| **Description** | **Author**       | **Version** | **Date**    |
| Initial version | Krzysztof Byrski | 1           | 18-May-2018 |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [4](#introduction)](#introduction)

[1.1 Purpose [4](#purpose)](#purpose)

[1.2 Scope [4](#scope)](#scope)

[2 BmwHaptcFb & High-Level Description
[5](#bmwhaptcfb-high-level-description)](#bmwhaptcfb-high-level-description)

[3 Design details of software module
[6](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of BmwHaptcFb
[6](#graphical-representation-of-bmwhaptcfb)](#graphical-representation-of-bmwhaptcfb)

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

[5.1.1 Init: BmwHaptcFbInit1 [8](#init-init1)](#init-init1)

[5.1.2 Per: BmwHaptcFbPer1 [8](#per-per1)](#per-per1)

[5.2 Server Runables [8](#server-runables)](#server-runables)

[5.3 Interrupt Functions
[8](#interrupt-functions)](#interrupt-functions)

[5.4 Module Internal (Local) Functions
[9](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 Local Function CalcBmwHaptcFbPatNr
[9](#local-function-calcbmwhaptcfbpatnr)](#local-function-calcbmwhaptcfbpatnr)

[5.4.2 Local Function CalcBmwHaptcFbIntenNr
[9](#local-function-calcbmwhaptcfbintennr)](#local-function-calcbmwhaptcfbintennr)

[5.4.3 Local Function CalcHwOscnEna
[10](#local-function-calchwoscnena)](#local-function-calchwoscnena)

[5.4.4 Local Function CalcAmpAndFrq
[10](#local-function-calcampandfrq)](#local-function-calcampandfrq)

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

Module Design Document for CF020A_BmwHaptcFb_Impl.

## Scope

The following definitions are used throughout this document:

-   **<u>Shall</u>**: indicates a mandatory requirement without
    exception in compliance.

-   **<u>Should</u>**: indicates a mandatory requirement; exceptions
    allowed only with documented justification.

-   **<u>May</u>**: indicates an optional action.

# BmwHaptcFb & High-Level Description

This function will alert the driver through handwheel haptic feedback if
a lane departure is detected. This function accepts pulse pattern,
amplitude, and frequency inputs from the customer and then provides an
enable/disable signal.

# Design details of software module

## Graphical representation of BmwHaptcFb

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/CF020A_BmwHaptcFb_Impl/doc/mediax/media/image1.png"
style="width:3.68683in;height:4.81545in" />

## Data Flow Diagram

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

### Local Function CalcBmwHaptcFbPatNr

|                      |                               |         |       |      |
|----------------------|-------------------------------|---------|-------|------|
| **Function Name**    | CalcBmwHaptcFbPatNr           | Type    | Min   | Max  |
| **Arguments Passed** | BmwHaptcFbPatNr_Cnt_T_enum    | enum    | 0     | 15   |
|                      | BmwHaptcFbPatNrVld_Cnt_T_logl | boolean | FALSE | TRUE |
|                      | HwOscnActv_Cnt_T_logl         | boolean | FALSE | TRUE |
| **Return Value**     | BmwHaptcFbPatNr_Cnt_T_enum    | enum    | 0     | 15   |
|                      | BmwHaptcFbPatNrLgc_Cnt_T_logl | boolean | FALSE | TRUE |

#### Design Rationale

Implementation of "CalcBmwHaptcFbPatNr" and "BmwHaptcFbPatNrLgc"
Simulink block

#### Processing

Refer FDD

### Local Function CalcBmwHaptcFbIntenNr

|                      |                                 |         |       |      |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | CalcBmwHaptcFbIntenNr           | Type    | Min   | Max  |
| **Arguments Passed** | BmwHaptcFbIntenNr_Cnt_T_enum    | enum    | 0     | 15   |
|                      | BmwHaptcFbIntenNrVld_Cnt_T_logl | boolean | FALSE | TRUE |
|                      | HwOscnActv_Cnt_T_logl           | boolean | FALSE | TRUE |
| **Return Value**     | BmwHaptcFbIntenNr_Cnt_T_enum    | enum    | 0     | 15   |
|                      | BmwHaptcFbIntenNrLgc_Cnt_T_logl | boolean | FALSE | TRUE |

#### Design Rationale

Implementation of "CalcBmwHaptcFbIntenNr" and "BmwHaptcFbIntenNrLgc"
Simulink block

#### Processing

Refer FDD

### Local Function CalcHwOscnEna

|                      |                       |         |       |      |
|----------------------|-----------------------|---------|-------|------|
| **Function Name**    | CalcHwOscnEna         | Type    | Min   | Max  |
| **Arguments Passed** | PatChgReq_Cnt_T_logl  | float32 | FALSE | TRUE |
|                      | ActvTi_MilliSec_T_f32 | float32 | 0     | 60   |
|                      | PasTi_MilliSec_T_f32  | float32 | 0     | 3    |
| **Return Value**     | HwOscnEna_Cnt_T_logl  | boolean | FALSE | TRUE |

#### Design Rationale

Implementation of "CalcHwOscnEna" Simulink block

#### Processing

Refer FDD

### Local Function CalcAmpAndFrq

|                      |                              |         |     |     |
|----------------------|------------------------------|---------|-----|-----|
| **Function Name**    | CalcAmpAndFrq                | Type    | Min | Max |
| **Arguments Passed** | VehSpd_Kph_T_f32             | float32 | 0   | 511 |
|                      | HwTq_HwNwtMtr_T_f32          | float32 | -10 | 10  |
| **Return Value**     | HwOscnMotAmp_MotNwtMtr_T_f32 | float32 | 0   | 10  |
|                      | HwOscnFrq_Hz_T_f32           | float32 | 10  | 50  |

#### Design Rationale

Implementation of "CalcAmpAndFrq" Simulink block

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
| 5           | CF020A_BmwHaptcFb_Design                                                                                                                                                                                                              | See Synergy Sub Project Version |

{% endraw %}