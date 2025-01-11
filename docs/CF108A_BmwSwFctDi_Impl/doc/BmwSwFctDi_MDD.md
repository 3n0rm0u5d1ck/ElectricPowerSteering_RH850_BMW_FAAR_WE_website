---
layout: default
title: BmwSwFctDi_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**BmwSwFctDi**

**July 28, 2018**

**Prepared By:**

**Akilan Rathakrishnan,**

**Nexteer Automotive,**

**Saginaw, USA  
<u>Change History</u>**

|                                                          |                       |             |             |
|-------------------------------------|-------------|---------|-------------|
| **Description**                                          | **Author**            | **Version** | **Date**    |
| Initial version                                          | Akilan Rathakrishnan  | 1.0         | 28-Jul-2018 |
| Updated Design rationale for periodic and init runnables | Akilan Rathakrishanan | 2.0         | 30-Jul-2018 |

**  
**

<u>Table of Contents</u>

[1 Introduction [5](#introduction)](#introduction)

[1.1 Purpose [5](#purpose)](#purpose)

[1.2 Scope [5](#scope)](#scope)

[2 BmwSwFctDi High-Level Description
[6](#bmwswfctdi-high-level-description)](#bmwswfctdi-high-level-description)

[3 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of BmwVehSpd
[8](#graphical-representation-of-bmwvehspd)](#graphical-representation-of-bmwvehspd)

[3.2 Data Flow Diagram [9](#data-flow-diagram)](#data-flow-diagram)

[3.2.1 Component level DFD
[9](#component-level-dfd)](#component-level-dfd)

[3.2.2 Function level DFD [9](#function-level-dfd)](#function-level-dfd)

[4 Constant Data Dictionary
[10](#constant-data-dictionary)](#constant-data-dictionary)

[4.1 Program (fixed) Constants
[10](#program-fixed-constants)](#program-fixed-constants)

[4.1.1 Embedded Constants
[10](#embedded-constants)](#embedded-constants)

[5 Software Component Implementation
[11](#software-component-implementation)](#software-component-implementation)

[5.1 Sub-Module Functions
[11](#sub-module-functions)](#sub-module-functions)

[5.1.1 BmwSwFctDiInit1 [11](#bmwswfctdiinit1)](#bmwswfctdiinit1)

[5.1.1.1 Design Rationale [11](#design-rationale)](#design-rationale)

[5.1.1.2 Module Outputs [11](#_Toc421011516)](#_Toc421011516)

[5.1.2 BmwSwFctDiPer1 [11](#bmwswfctdiper1)](#bmwswfctdiper1)

[5.1.2.1 Design Rationale
[11](#design-rationale-1)](#design-rationale-1)

[5.1.2.2 Module Outputs [11](#module-outputs-1)](#module-outputs-1)

[5.2 Server Runnables [11](#server-runnables)](#server-runnables)

[5.3 Interrupt Functions
[11](#interrupt-functions)](#interrupt-functions)

[5.3.1 Interrupt Function Name
[11](#interrupt-function-name)](#interrupt-function-name)

[5.4 Module Internal (Local) Functions
[11](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 UpdCodingBits [11](#updcodingbits)](#updcodingbits)

[5.4.2 ReadCodingData [11](#readcodingdata)](#readcodingdata)

[5.4.3 PullCmpCmdDiBmwOvrd
[12](#pullcmpcmddibmwovrd)](#pullcmpcmddibmwovrd)

[5.4.4 InertiaCmpVelCmdDiBmwOvrd
[12](#inertiacmpvelcmddibmwovrd)](#inertiacmpvelcmddibmwovrd)

[5.4.5 ClsdLoopHysEna [12](#clsdloophysena)](#clsdloophysena)

[5.4.6 CtrldVelRtnEna [12](#ctrldvelrtnena)](#ctrldvelrtnena)

[5.4.7 OvrdCmdEna [12](#ovrdcmdena)](#ovrdcmdena)

[5.5 GLOBAL Function/Macro Definitions
[12](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[6 Known Limitations with Design
[13](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[14](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[15](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [16](#glossary)](#glossary)

[Appendix C Please references
[17](#please-references)](#please-references)

# Introduction

## Purpose

Module Design Document for CF0108A_BmwSwFctDi_Impl

## Scope

The following definitions are used throughout this document:

-   **<u>Shall</u>**: indicates a mandatory requirement without
    exception in compliance.

-   **<u>Should</u>**: indicates a mandatory requirement; exceptions
    allowed only with documented justification.

-   **<u>May</u>**: indicates an optional action.

# BmwSwFctDi High-Level Description

This is BMW specific and will allow features to be disabled per customer
requirements without altering multiple SF''s. It will also take a client
call from the BAC module coding and output Boolean logic to allow BMW to
disable the required features. This client call will be changing over
time from BMW and this function allows change to happen in one component
instead of adjusting all the CF components that need and output from
this.

# Design details of software module

Please refer FDD

## Graphical representation of BmwVehSpd

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/CF108A_BmwSwFctDi_Impl/doc/mediax/media/image1.png"
style="width:5.41667in;height:8.85417in" />

## Data Flow Diagram

Please refer FDD

### Component level DFD

Please refer FDD

### Function level DFD

Please refer FDD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name                      | Resolution | Units | Value |
|------------------------------------|------------|-------|-------|
| Please refer .m file for constants |            |       |       |

# Software Component Implementation

## Sub-Module Functions

### BmwSwFctDiInit1

## Design Rationale

<span id="_Toc421011516" class="anchor"></span>Implementation of the
init runnable differs from design due to the way this component need to
interact with BMW BAC Coding component.

## Module Outputs

None

## BmwSwFctDiPer1

## Design Rationale

Implementation of the periodic differs from design due to the way this
component need to interact with BMW BAC Coding component.

## Module Outputs

None

## Server Runnables 

None

## Interrupt Functions

None

## Interrupt Function Name

None

## Module Internal (Local) Functions

### UpdCodingBits

|                      |                          |       |     |     |
|----------------------|--------------------------|-------|-----|-----|
| **Function Name**    | UpdCodingBits            | Type  | Min | Max |
| **Arguments Passed** | CodingDataMode_Cnt_T_u08 | Uint8 | 0   | 5   |
| **Return Value**     | None                     | \-    | \-  | \-  |

### ReadCodingData

|                      |                          |       |     |     |
|----------------------|--------------------------|-------|-----|-----|
| **Function Name**    | ReadCodingData           | Type  | Min | Max |
| **Arguments Passed** | CodingDataMode_Cnt_T_u08 | uint8 | 0   | 5   |
| **Return Value**     | None                     | \-    | \-  | \-  |

### PullCmpCmdDiBmwOvrd

|                      |                                |         |       |      |
|----------------------|--------------------------------|---------|-------|------|
| **Function Name**    | VehSpdRateLim                  | Type    | Min   | Max  |
| **Arguments Passed** | PullCmpCmdDi_Cnt_T_logl        | Boolean | FALSE | TRUE |
| **Return Value**     | PullCmpCmdDiBmwOvrd_Cnt_T_logl | Boolean | FALSE | TRUE |

### InertiaCmpVelCmdDiBmwOvrd

|                      |                                      |         |       |      |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | InertiaCmpVelCmdDiBmwOvrd            | Type    | Min   | Max  |
| **Arguments Passed** | InertiaCmpVelCmdDi_Cnt_T_logl        | boolean | FALSE | TRUE |
| **Return Value**     | InertiaCmpVelCmdDiBmwOvrd_Cnt_T_logl | boolean | FALSE | TRUE |

### ClsdLoopHysEna

|                      |                                  |         |     |     |
|----------------------|----------------------------------|---------|-----|-----|
| **Function Name**    | ClsdLoopHysEna                   | Type    | Min | Max |
| **Arguments Passed** | HwTqCmdHys_HwNwtMtr_T_f32        | Float32 | -10 | 10  |
| **Return Value**     | HwTqCmdHysBmwOvrd_HwNwtMtr_T_f32 | Float32 | -10 | 10  |

###  [section]

### CtrldVelRtnEna

|                      |                                       |         |      |     |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | CtrldVelRtnEna                        | Type    | Min  | Max |
| **Arguments Passed** | CtrldVelRtnCmd_MotNwtMtr_T_f32        | Float32 | -8.8 | 8.8 |
| **Return Value**     | CtrldVelRtnCmdBmwOvrd_MotNwtMtr_T_f32 | Float32 | -8.8 | 8.8 |

### OvrdCmdEna

|                      |                           |         |       |      |
|----------------------|---------------------------|---------|-------|------|
| **Function Name**    | ProcessFourthAndGateState | Type    | Min   | Max  |
| **Arguments Passed** | OvrdCal_Cnt_T_u08         | Uint8   | 0     | 255  |
|                      | CodingBit_Cnt_T_u08       | Uint8   | 0     | 255  |
| **Return Value**     | OvrlCmdEna_Cnt_T_logl     | boolean | FALSE | TRUE |

## GLOBAL Function/Macro Definitions

None

# Known Limitations with Design

None.

# UNIT TEST CONSIDERATION

1.  Client calls to BMW BAC Coding component are not listed in the
    design since this will require modeling 3^rd^ party software.

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

-   Automotive SPICE® Process Please reference Model (PRM)

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

####### Please references

| **Ref. \#** | **Title**                                                                                                                                                             | **Version**                    |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                    | v1.3.0 R4.0 Rev 2              |
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.00                   |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 1.0                            |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.1                            |
| 5           | FDD: CF108A_BmwSwFctDi_Design                                                                                                                                         | See Synergy subproject version |

{% endraw %}