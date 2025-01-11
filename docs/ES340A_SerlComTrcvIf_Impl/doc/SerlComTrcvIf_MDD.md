---
layout: default
title: SerlComTrcvIf_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**SerlComTrcvIf**

**February 21, 2018**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                                         |                  |             |             |
|--------------------------------|------------------|-----------|------------|
| **Description**                         | **Author**       | **Version** | **Date**    |
| Initial version (based on Design 1.1.0) | Krzysztof Byrski | 1           | 21-Feb-2018 |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [4](#introduction)](#introduction)

[1.1 Purpose [4](#purpose)](#purpose)

[1.2 Scope [4](#scope)](#scope)

[2 SerlComTrcvIf & High-Level Description
[5](#serlcomtrcvif-high-level-description)](#serlcomtrcvif-high-level-description)

[3 Design details of software module
[6](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of SerlComTrcvIf
[6](#graphical-representation-of-serlcomtrcvif)](#graphical-representation-of-serlcomtrcvif)

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

[5.1.1 Init: SerlComTrcvIfInit1
[8](#init-serlcomtrcvifinit1)](#init-serlcomtrcvifinit1)

[5.1.2 Per: SerlComTrcvIfPer1
[8](#per-serlcomtrcvifper1)](#per-serlcomtrcvifper1)

[5.2 Server Runables [8](#server-runables)](#server-runables)

[5.3 Interrupt Functions
[8](#interrupt-functions)](#interrupt-functions)

[5.4 Module Internal (Local) Functions
[9](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 Local Function MonitorERRN
[9](#local-function-monitorerrn)](#local-function-monitorerrn)

[5.4.2 Local Function ReadAndAnalyze
[9](#local-function-readandanalyze)](#local-function-readandanalyze)

[5.4.3 Local Function AnalyzeRegister
[9](#local-function-analyzeregister)](#local-function-analyzeregister)

[5.4.4 Local Function ParityErrorCheck
[10](#local-function-parityerrorcheck)](#local-function-parityerrorcheck)

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

Module Design Document for SerlComTrcvIf.

## Scope

The following definitions are used throughout this document:

-   **<u>Shall</u>**: indicates a mandatory requirement without
    exception in compliance.

-   **<u>Should</u>**: indicates a mandatory requirement; exceptions
    allowed only with documented justification.

-   **<u>May</u>**: indicates an optional action.

# SerlComTrcvIf & High-Level Description

The Serial Communication Transceiver Interface function monitors error
status of FlexRay transceiver, reads the Status Registers via SPI and
sets appropriate NTCs.

# Design details of software module

## Graphical representation of SerlComTrcvIf

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/ES340A_SerlComTrcvIf_Impl/doc/mediax/media/image1.png"
style="width:4.13967in;height:2.27836in" />

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

| Constant Name                       | Resolution | Units | Value  |
|-------------------------------------|------------|-------|--------|
| SERLCOMTRCVIFNTCMASKBIT5_CNT_U08    | 1          | Cnt   | 32     |
| SERLCOMTRCVIFNTCMASKBIT7_CNT_U08    | 1          | Cnt   | 128    |
| SERLCOMTRCVIFRESDBITS_CNT_U16       | 1          | Cnt   | 20480  |
| SERLCOMTRCVIFSPIERRCNTRMAX_CNT_U08  | 1          | Cnt   | 1      |
| STMONRERRPIN_CNT_U08                | 1          | Cnt   | 1      |
| STREADANDDECOD_CNT_U08              | 1          | Cnt   | 2      |
| SERLCOMTRCVIFMASKBITS11TO14_CNT_U16 | 1          | Cnt   | 0x7800 |
| SERLCOMTRCVIFMASKBITS5TO10_CNT_U16  | 1          | Cnt   | 0x7E0  |

# Software Component Implementation

## Sub-Module Functions

The sub-module functions are grouped based on similar functionality that
needs to be executed in a given “State” of the system (refer States and
Modes). For a given module, the MDD will identify the type and number of
sub-modules required. The sub-module types are described below.

### Init: SerlComTrcvIfInit1

#### Design Rationale

Refer FDD

#### Module Outputs

None

###  [section]

### Per: SerlComTrcvIfPer1

#### Design Rationale

Refer FDD

#### Store Module Inputs to Local copies

None

#### (Processing of function)………

Refer FDD

#### Store Local copy of outputs into Module Outputs

Refer FDD

## Server Runables 

None

## Interrupt Functions

None

## Module Internal (Local) Functions

### Local Function MonitorERRN

|                      |             |      |     |     |
|----------------------|-------------|------|-----|-----|
| **Function Name**    | MonitorERRN | Type | Min | Max |
| **Arguments Passed** | None        |      |     |     |
| **Return Value**     | None        |      |     |     |

#### Design Rationale

Implementation of Simulink block "MonitorERRN".

#### Processing

Refer Simulink block "MonitorERRN".

### Local Function ReadAndAnalyze

|                      |                |      |     |     |
|----------------------|----------------|------|-----|-----|
| **Function Name**    | ReadAndAnalyze | Type | Min | Max |
| **Arguments Passed** | None           |      |     |     |
| **Return Value**     | None           |      |     |     |

#### Design Rationale

Implementation of Simulink block "ReadAndAnalyze".

#### Processing

Refer Simulink block "ReadAndAnalyze".

### Local Function AnalyzeRegister

|                      |                      |        |     |       |
|----------------------|----------------------|--------|-----|-------|
| **Function Name**    | AnalyzeRegister      | Type   | Min | Max   |
| **Arguments Passed** | RegIn_Cnt_T_u16      | uint16 | 0   | 65535 |
| **Return Value**     | NtcStsInfo_Cnt_T_u08 | uint8  | 0   | 128   |

#### Design Rationale

Implementation of Simulink block "AnalyzeRegister".

#### Processing

Refer Simulink block "AnalyzeRegister".

### Local Function ParityErrorCheck

|                      |                   |         |       |       |
|----------------------|-------------------|---------|-------|-------|
| **Function Name**    | ParityErrorCheck  | Type    | Min   | Max   |
| **Arguments Passed** | RegIn_Cnt_T_u16   | uint16  | 0     | 65535 |
| **Return Value**     | Parity_Cnt_T_logl | boolean | FALSE | TRUE  |

#### Design Rationale

Implementation of Simulink block "ParityErrorCheck".

#### Processing

Refer Simulink block "ParityErrorCheck".

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
| 5           | ES340A_SerlComTrcvIf_Design                                                                                                                                                                                                           | See Synergy Sub Project Version |

{% endraw %}