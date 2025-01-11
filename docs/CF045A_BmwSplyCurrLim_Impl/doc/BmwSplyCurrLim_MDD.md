---
layout: default
title: BmwSplyCurrLim_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**BmwSplyCurrLim**

**May 24, 2018**

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
| Initial version | Marek Brykczyński | 1           | 24-May-2018 |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [4](#introduction)](#introduction)

[1.1 Purpose [4](#purpose)](#purpose)

[1.2 Scope [4](#scope)](#scope)

[2 BmwSplyCurrLim & High-Level Description
[5](#bmwsplycurrlim-high-level-description)](#bmwsplycurrlim-high-level-description)

[3 Design details of software module
[6](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of BmwSplyCurrLim
[6](#graphical-representation-of-bmwsplycurrlim)](#graphical-representation-of-bmwsplycurrlim)

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

[5.1.1 Init: BmwSplyCurrLimInit1 [8](#init-init1)](#init-init1)

[5.1.2 Per: BmwSplyCurrLimPer1 [8](#per-per1)](#per-per1)

[5.2 Server Runables [8](#server-runables)](#server-runables)

[5.3 Interrupt Functions
[8](#interrupt-functions)](#interrupt-functions)

[5.4 Module Internal (Local) Functions
[9](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 VltgDptCurrLim [9](#vltgdptcurrlim)](#vltgdptcurrlim)

[5.5 GLOBAL Function/Macro Definitions
[9](#global-functionmacro-definitions)](#global-functionmacro-definitions)

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

Module Design Document for CF045A_BmwSplyCurrLim_Impl.

## Scope

The following definitions are used throughout this document:

-   **<u>Shall</u>**: indicates a mandatory requirement without
    exception in compliance.

-   **<u>Should</u>**: indicates a mandatory requirement; exceptions
    allowed only with documented justification.

-   **<u>May</u>**: indicates an optional action.

# BmwSplyCurrLim & High-Level Description

The BMW Supply Current Limit function specifies the supply current limit
based on operating conditions of the vehicle. The supply current limit
is a function of vehicle speed, supply voltage measurement, customer
serial communication messages and motor start stop (MSA). The function
arbitrates between limits specified for each interface to meet the
requirements provided by the customer.

# Design details of software module

## Graphical representation of BmwSplyCurrLim

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/CF045A_BmwSplyCurrLim_Impl/doc/mediax/media/image1.png"
style="width:6.5in;height:5.74444in" />

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

### Init: Init1

#### Design Rationale

Refer FDD

#### Module Outputs

Refer FDD

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

### VltgDptCurrLim

|                      |                                                    |         |       |       |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | VltgDptCurrLim                                     | Type    | Min   | Max   |
| **Arguments Passed** | RemCtrlPrkgEna_Cnt_T_logl                          | boolean | FALSE | TRUE  |
|                      | BrdgVltg_Volt_T_u6p10                              | uint16  | 6144  | 27136 |
| **Return Value**     | A result of a conversion of fixed-point to float32 | float32 | 0     | 120   |

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
| 5           | CF045A_BmwSplyCurrLim_Design                                                                                                                                                                                                          | See Synergy Sub Project Version |

{% endraw %}