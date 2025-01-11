---
layout: default
title: BattRtnCurr_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**BattRtnCurr**

**October 11, 2017**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                                     |                  |             |                 |
|---------------------------|------------------|--------------|--------------|
| **Description**                     | **Author**       | **Version** | **Date**        |
| Initial Version                     | Krzysztof Byrski | 1           | 21-July-2017    |
| Updated as per Design version 1.1.0 | Krzysztof Byrski | 2           | 11-October-2017 |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [4](#introduction)](#introduction)

[1.1 Purpose [4](#purpose)](#purpose)

[1.2 Scope [4](#scope)](#scope)

[2 BattRtnCurr & High-Level Description
[5](#battrtncurr-high-level-description)](#battrtncurr-high-level-description)

[3 Design details of software module
[6](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of BattRtnCurr
[6](#graphical-representation-of-battrtncurr)](#graphical-representation-of-battrtncurr)

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

[5.1.1 Init: BattRtnCurrInit1 [8](#init-init1)](#init-init1)

[5.1.2 Per: BattRtnCurrPer1 [8](#per-per1)](#per-per1)

[5.1.3 Per: BattRtnCurrPer2
[8](#per-battrtncurrper2)](#per-battrtncurrper2)

[5.2 Server Runables [9](#server-runables)](#server-runables)

[5.3 Interrupt Functions
[9](#interrupt-functions)](#interrupt-functions)

[5.4 Module Internal (Local) Functions
[9](#module-internal-local-functions)](#module-internal-local-functions)

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

Module Design Document for ES251A_BattRtnCurr

## Scope

The following definitions are used throughout this document:

-   **<u>Shall</u>**: indicates a mandatory requirement without
    exception in compliance.

-   **<u>Should</u>**: indicates a mandatory requirement; exceptions
    allowed only with documented justification.

-   **<u>May</u>**: indicates an optional action.

# BattRtnCurr & High-Level Description

Refer FDD.

# Design details of software module

This function handles measurement of battery return current. It receives
ADC samples representing current in volts and converts them to ampere
units.

Additionally, it performs basic output signal limitation. Module design
allows execution from motor control loop or 2ms periodic. Therefore two
sets of input and outputs signals are available where ones prefixed with
"MotCtrl" shall be used inside motor control loop.

## Graphical representation of BattRtnCurr

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/ES251A_BattRtnCurr_Impl/doc/mediax/media/image2.png"
style="width:3.31472in;height:2.71759in" />

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

| Constant Name                   | Resolution | Units | Value |
|---------------------------------|------------|-------|-------|
| BATTRTNCURRPASSD_CNT_U08        | 1          | Cnt   | 0     |
| BATTRTNCURROVERMAX_CNT_U08      | 1          | Cnt   | 1     |
| BATTRTNCURRUNDERMIN_CNT_U08     | 1          | Cnt   | 2     |
| BATTRTNCURRFAILDADC_CNT_U08     | 1          | Cnt   | 4     |
| BATTRTNCURRESTIMDIFFFLT_CNT_U08 | 1          | Cnt   | 8     |

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

### Per: BattRtnCurrPer2

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

None

## GLOBAL Function/Macro Definitions

None

# Known Limitations with Design

None

# UNIT TEST CONSIDERATION

None

# Abbreviations and Acronyms

| **Abbreviation or Acronym** | **Description** |
|-----------------------------|-----------------|
| \-                          | \-              |

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

| **Ref. \#** | **Title**                                                                                                                                                             | **Version**                     |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                    | v1.3.0 R4.0 Rev 2               |
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.01                    |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 01.01.00                        |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.1                             |
| 5           | ES251A_BattRtnCurr_Design                                                                                                                                             | See Synergy Sub Project Version |

{% endraw %}