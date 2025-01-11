---
layout: default
title: McuErrInj Module Design Document
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**McuErrInj**

**Jul 25, 2017**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**<u>Saginaw, MI, USAChange</u>** History

|                            |               |             |             |
|----------------------------|---------------|-------------|-------------|
| **Description**            | **Author**    | **Version** | **Date**    |
| Initial Version            | Avinash James | 1.0         | 15-Mar-2017 |
| Added the global functions | Avinash James | 2.0         | 25-Jul-2017 |

<u>Table of Contents</u>

[1 Introduction 5](#introduction)

[1.1 Purpose 5](#purpose)

[2 McuDiagc & High-Level Description
6](#mcudiagc-high-level-description)

[3 Design details of software module
7](#design-details-of-software-module)

[3.1 Graphical representation of McuDiagc
7](#graphical-representation-of-mcudiagc)

[3.2 Data Flow Diagram 7](#data-flow-diagram)

[3.2.1 Component level DFD 7](#component-level-dfd)

[3.2.2 Function level DFD 7](#function-level-dfd)

[4 Constant Data Dictionary 8](#constant-data-dictionary)

[4.1 Program (fixed) Constants 8](#program-fixed-constants)

[4.1.1 Embedded Constants 8](#embedded-constants)

[5 Software Component Implementation
9](#software-component-implementation)

[5.1 Sub-Module Functions 9](#sub-module-functions)

[5.1.1 Init: McuErrInjInit1 9](#init-mcuerrinjinit1)

[5.1.1.1 Design Rationale 9](#design-rationale)

[5.1.1.2 Module Outputs 9](#module-outputs)

[5.1.2 Per: McuErrInjPer1 9](#per-mcuerrinjper1)

[5.1.2.1 Design Rationale 9](#design-rationale-1)

[5.1.2.2 Store Module Inputs to Local copies
9](#store-module-inputs-to-local-copies)

[5.1.2.3 (Processing of function)……… 9](#processing-of-function)

[5.1.2.4 Store Local copy of outputs into Module Outputs
9](#store-local-copy-of-outputs-into-module-outputs)

[5.1.2.5 Store Local copy of outputs into Module Outputs
9](#store-local-copy-of-outputs-into-module-outputs-1)

[5.2 Server Runnable 10](#server-runnable)

[5.2.1 ClrErrInjReg_Oper 10](#clrerrinjreg_oper)

[5.2.1.1 Design Rationale 10](#design-rationale-2)

[5.2.1.2 Store Module Inputs to Local copies
10](#store-module-inputs-to-local-copies-1)

[5.2.1.3 (Processing of function)……… 10](#processing-of-function-1)

[5.2.1.4 Store Local copy of outputs into Module Outputs
10](#store-local-copy-of-outputs-into-module-outputs-2)

[5.2.1 ReadErrInjReg_Oper 10](#readerrinjreg_oper)

[5.2.1.1 Design Rationale 10](#design-rationale-3)

[5.2.1.2 Store Module Inputs to Local copies
10](#store-module-inputs-to-local-copies-2)

[5.2.1.3 (Processing of function)……… 10](#processing-of-function-2)

[5.2.1.4 Store Local copy of outputs into Module Outputs
10](#store-local-copy-of-outputs-into-module-outputs-3)

[5.2.1 UpdErrInjReg_Oper 10](#upderrinjreg_oper)

[5.2.1.1 Design Rationale 10](#design-rationale-4)

[5.2.1.2 Store Module Inputs to Local copies
10](#store-module-inputs-to-local-copies-3)

[5.2.1.3 (Processing of function)……… 10](#processing-of-function-3)

[5.2.1.4 Store Local copy of outputs into Module Outputs
10](#store-local-copy-of-outputs-into-module-outputs-4)

[5.2.1 StrtErrInjCntr 11](#strterrinjcntr)

[5.2.1.1 Design Rationale 11](#design-rationale-5)

[5.2.1.2 Store Module Inputs to Local copies
11](#store-module-inputs-to-local-copies-4)

[5.2.1.3 (Processing of function)……… 11](#processing-of-function-4)

[5.2.1.4 Store Local copy of outputs into Module Outputs
11](#store-local-copy-of-outputs-into-module-outputs-5)

[5.3 Interrupt Functions 11](#interrupt-functions)

[5.4 Module Internal (Local) Functions
11](#module-internal-local-functions)

[5.5 GLOBAL Function/Macro Definitions
11](#global-functionmacro-definitions)

[5.5.1 GLObAL Function \#1 11](#global-function-1)

[5.5.1.1 Description 11](#description)

[6 Known Limitations with Design 12](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION 13](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms 14](#abbreviations-and-acronyms)

[Appendix B Glossary 15](#glossary)

[Appendix C References 17](#references)

# Introduction

## Purpose

Module design document for Micro Controller Diagnostics Error Injection

#  McuDiagc & High-Level Description

Refer the Design.

# Design details of software module

## Graphical representation of McuDiagc

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/DF003A_McuErrInj_Impl/doc/mediax/media/image1.png"
style="width:2.94167in;height:1.49167in" />

## Data Flow Diagram

### Component level DFD

N/A

### Function level DFD

N/A

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

|                               |            |       |       |
|-------------------------------|------------|-------|-------|
| Constant Name                 | Resolution | Units | Value |
| MCUERRINJ_TESTRSTUKWN_CNT_U32 | 1          | Cnt   |       |
| SHIFTBYWORD_CNT_U08           | 1          | Cnt   | 16U   |
| SHIFTBYBYTE_CNT_U08           | 1          | Cnt   | 8U    |
| Refer .m file                 |            |       |       |

#### Global

Currently the FDD has not been updated to show define the global
constants. However the header file includes all the necessary global
constants

# Software Component Implementation

## Sub-Module Functions

The sub-module functions are grouped based on similar functionality that
needs to be executed in a given “State” of the system (refer States and
Modes). For a given module, the MDD will identify the type and number of
sub-modules required. The sub-module types are described below.

### Init: McuErrInjInit1

## Design Rationale

*Refer to FDD*

## Module Outputs

*Refer to FDD*

###  [section]

### Per: McuErrInjPer1

## Design Rationale

*None*

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD*

## Store Local copy of outputs into Module Outputs

*Refer to FDD*

## Store Local copy of outputs into Module Outputs

*Refer to FDD*

## Server Runnable 

### ClrErrInjReg_Oper

## Design Rationale

*Refer FDD*

## Store Module Inputs to Local copies

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*None*

### ReadErrInjReg_Oper

## Design Rationale

*Refer FDD. The function returns a 0 value in the case when the
MCUERRINJ is defined as STD_OFF. This is done for static compliance as
the actual functional code returns the value of BRAMDAT2 when*
*MCUERRINJ is defined as STD_ON which is encapsulated under the compiler
define and when its STD_OFF for the pointer variable to have a default
value, we return 0.*

## Store Module Inputs to Local copies

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*None*

### UpdErrInjReg_Oper

## Design Rationale

*Refer FDD*

## Store Module Inputs to Local copies

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*None*

### StrtErrInjCntr

## Design Rationale

*Refer FDD*

## Store Module Inputs to Local copies

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*None*

## Interrupt Functions

*None*

## Module Internal (Local) Functions

*None*

## GLOBAL Function/Macro Definitions

## GLObAL Function \#1

|                      |                    |      |     |     |
|----------------------|--------------------|------|-----|-----|
| **Function Name**    | McuDiagcTestTrustd | Type | Min | Max |
| **Arguments Passed** | None               |      |     |     |
| **Return Value**     | N/A                |      |     |     |

## Description

Trusted function that performs the tests which need to run in supervisor
mode of the processor as some tests needs register access at supervisor
level.

## GLObAL Functions

InjVrfyCritRegErr()

InjMcuVltgMonrErr()

InjClkMonrErr()

InjOsTmpGenericRtErr ()

InjOsPrmntGenericRtErr ()

InjWdgErr ()

InjFpuErr ()

InjMemProtnErr ()

InjModErr ()

InjMcuRtErr ()

InjProgSeqErr ()

InjPbgRtErr ()

InjRamErr()

InjEcmMstChkrRtErr()

InjUkwnStrtUpDetdErr()

InjIpgRtErr()

InjRtPegErr()

InjDataParErr()

> InjDmaErr()

InjMcuDiagcErr()

> InjAdcErr()
>
> InjSwFpuErr()

## Description

The above list is the list of global functions which are used for error
injection which gets defined in multiple FDDs based of the NTC they are
trying to set. These global functions are only enabled when the \#define
MCUDIAGCERRINJ is made STD_ON in the McuDiagcErrInj header file. So,
DF003A FDD is the owner of these global functions though they are
defined in multiple files. Return type and parameter lists are both void
for the above defined ones

# Known Limitations with Design

# UNIT TEST CONSIDERATION

####### Abbreviations and Acronyms

| **Abbreviation or Acronym** | **Description**           |
|-----------------------------|---------------------------|
| DFD                         | Design functional diagram |
| MDD                         | Module design Document    |

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

| **Ref. \#** | **Title**                                                                                                                                                             | **Version**                    |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                    | v1.3.0 R4.0 Rev 2              |
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.01                   |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 1.0                            |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.1                            |
| 5           | FDD – ES002A McuDiagc                                                                                                                                                 | See Synergy subproject version |

{% endraw %}