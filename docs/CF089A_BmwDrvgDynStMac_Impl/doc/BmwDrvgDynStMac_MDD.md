---
layout: default
title: BmwDrvgDynStMac_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**BmwDrvgDynStMac**

**April 13, 2018**

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
| Initial version | Krzysztof Byrski | 1           | 17-Apr-2018 |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [5](#introduction)](#introduction)

[1.1 Purpose [5](#purpose)](#purpose)

[1.2 Scope [5](#scope)](#scope)

[2 BmwDrvgDynStMac & High-Level Description
[6](#bmwdrvgdynstmac-high-level-description)](#bmwdrvgdynstmac-high-level-description)

[3 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of BmwDrvgDynStMac
[7](#graphical-representation-of-bmwdrvgdynstmac)](#graphical-representation-of-bmwdrvgdynstmac)

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

[5.1.1 Init: BmwDrvgDynStMacInit1
[9](#init-bmwdrvgdynstmacinit1)](#init-bmwdrvgdynstmacinit1)

[5.1.2 Per: BmwDrvgDynStMacPer1
[9](#per-bmwdrvgdynstmacper1)](#per-bmwdrvgdynstmacper1)

[5.2 Server Runables [9](#server-runables)](#server-runables)

[5.3 Interrupt Functions
[9](#interrupt-functions)](#interrupt-functions)

[5.4 Module Internal (Local) Functions
[10](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 Local Function DetermineErrorMode
[10](#local-function-determineerrormode)](#local-function-determineerrormode)

[5.4.2 Local Function Fac
[10](#local-function-fac)](#local-function-fac)

[5.4.3 Local Function AssiLvlCnd
[11](#local-function-assilvlcnd)](#local-function-assilvlcnd)

[5.4.4 Local Function CheckActivityTime
[11](#local-function-checkactivitytime)](#local-function-checkactivitytime)

[5.4.5 Local Function CheckDeactivateTime
[11](#local-function-checkdeactivatetime)](#local-function-checkdeactivatetime)

[5.4.6 Local Function ErrorIfTi
[12](#local-function-errorifti)](#local-function-errorifti)

[5.4.7 Local Function StateMachine
[12](#local-function-statemachine)](#local-function-statemachine)

[5.4.8 Local Function StateMachineInit
[13](#local-function-statemachineinit)](#local-function-statemachineinit)

[5.4.9 Local Function StateMachineIfAvl
[13](#local-function-statemachineifavl)](#local-function-statemachineifavl)

[5.4.10 Local Function StateMachineIfActv
[14](#local-function-statemachineifactv)](#local-function-statemachineifactv)

[5.4.11 Local Function StateMachineStbEpsSts
[14](#local-function-statemachinestbepssts)](#local-function-statemachinestbepssts)

[5.4.12 Local Function StateMachineEntry
[15](#local-function-statemachineentry)](#local-function-statemachineentry)

[5.5 GLOBAL Function/Macro Definitions
[16](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[6 Known Limitations with Design
[17](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[18](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[19](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [20](#glossary)](#glossary)

[Appendix C References [21](#references)](#references)

# Introduction

## Purpose

Model Deign Document for CF089A_BmwDrvgDynStMac_Impl.

## Scope

The following definitions are used throughout this document:

-   **<u>Shall</u>**: indicates a mandatory requirement without
    exception in compliance.

-   **<u>Should</u>**: indicates a mandatory requirement; exceptions
    allowed only with documented justification.

-   **<u>May</u>**: indicates an optional action.

# BmwDrvgDynStMac & High-Level Description

The component implements the functionality of Driving Dynamics State
Machine. It is based on requirements for DD State Machine in LH10716411
starting from ID_6159. It outputs signals for CF083A and CF040A.

# Design details of software module

## Graphical representation of BmwDrvgDynStMac

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/CF089A_BmwDrvgDynStMac_Impl/doc/mediax/media/image1.png"
style="width:3.374in;height:6.11881in" />

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
| \*            |            |       |       |

\*Refer FDD for local constants

# Software Component Implementation

## Sub-Module Functions

The sub-module functions are grouped based on similar functionality that
needs to be executed in a given “State” of the system (refer States and
Modes). For a given module, the MDD will identify the type and number of
sub-modules required. The sub-module types are described below.

### Init: BmwDrvgDynStMacInit1

#### Design Rationale

Refer FDD

#### Module Outputs

None

###  [section]

### Per: BmwDrvgDynStMacPer1

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

### Local Function DetermineErrorMode

|                      |                                          |         |       |      |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | DetermineErrorMode                       | Type    | Min   | Max  |
| **Arguments Passed** | SysStFltOutpReqDi_Cnt_T_logl             | boolean | 0     | 1    |
|                      | DiagcStsNonRcvrlReqDiFltPrsnt_Cnt_T_logl | boolean | 0     | 1    |
|                      | DiagcStsCtrldShtDwnFltPrsnt_Cnt_T_logl   | boolean | 0     | 1    |
|                      | StsSteerAssi_Cnt_T_enum                  | enum    | 0     | 1    |
|                      | BmwVehCdn_Cnt_T_enum                     | enum    | 1     | 15   |
| **Return Value**     | ErrMod_Cnt_T_logl                        | boolean | FALSE | TRUE |

#### Design Rationale

Implementation of "DetermineErrorMode" Simulink block

#### Processing

Refer FDD

### Local Function Fac

|                      |                        |         |       |      |
|----------------------|------------------------|---------|-------|------|
| **Function Name**    | Fac                    | Type    | Min   | Max  |
| **Arguments Passed** | EffortCmdSca_Uls_T_f32 | float32 | 1     | 2    |
|                      | DampgCmdSca_Uls_T_f32  | float32 | 0     | 1    |
|                      | RtnCmdSca_Uls_T_f32    | float32 | 0     | 1    |
| **Return Value**     | Fac_Cnt_T_logl         | boolean | FALSE | TRUE |

#### Design Rationale

Implementation of "Fac" Simulink block

#### Processing

Refer FDD

### Local Function AssiLvlCnd

|                      |                                       |         |       |      |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | AssiLvlCnd                            | Type    | Min   | Max  |
| **Arguments Passed** | MotTqCmdPwrLimd_MotNwtMtr_T_f32       | float32 | -8.8  | 8.8  |
| **Return Value**     | MotTqCmdPwrLimdActvtUppr_Cnt_T_logl   | boolean | FALSE | TRUE |
|                      | MotTqCmdPwrLimdActvtLowr_Cnt_T_logl   | boolean | FALSE | TRUE |
|                      | MotTqCmdPwrLimdDeactvtLowr_Cnt_T_logl | boolean | FALSE | TRUE |

#### Design Rationale

Implementation of "AssiLvlCnd" Simulink block

#### Processing

Refer FDD

### Local Function CheckActivityTime

|                      |                                    |         |       |      |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | CheckActivityTime                  | Type    | Min   | Max  |
| **Arguments Passed** | MotTqCmdPwrLimdCdnActvt_Cnt_T_logl | boolean | FALSE | TRUE |
| **Return Value**     | MotTqCmdPwrLimdActvt_Cnt_T_logl    | boolean | FALSE | TRUE |

#### Design Rationale

Implementation of "CheckActivity Time" Simulink block

#### Processing

Refer FDD

### Local Function CheckDeactivateTime

|                      |                                      |         |       |      |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | CheckDeactivateTime                  | Type    | Min   | Max  |
| **Arguments Passed** | MotTqCmdPwrLimdCdnDeactvt_Cnt_T_logl | boolean | FALSE | TRUE |
| **Return Value**     | MotTqCmdPwrLimdDeactvt_Cnt_T_logl    | boolean | FALSE | TRUE |

#### Design Rationale

Implementation of "CheckDeactivate Time" Simulink block

#### Processing

Refer FDD

### Local Function ErrorIfTi

|                      |                    |         |       |      |
|----------------------|--------------------|---------|-------|------|
| **Function Name**    | ErrorIfTi          | Type    | Min   | Max  |
| **Arguments Passed** | ErrIf_Cnt_T_logl   | boolean | FALSE | TRUE |
| **Return Value**     | ErrIfTi_Cnt_T_logl | boolean | FALSE | TRUE |

#### Design Rationale

Implementation of "ErrorIfTi" Simulink block

#### Processing

Refer FDD

### Local Function StateMachine

|                      |                                      |         |       |      |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | StateMachine                         | Type    | Min   | Max  |
| **Arguments Passed** | ErrMod_Cnt_T_logl                    | boolean | FALSE | TRUE |
|                      | AllwTran_Cnt_T_logl                  | boolean | FALSE | TRUE |
|                      | ErrIf_Cnt_T_logl                     | boolean | FALSE | TRUE |
|                      | BmwTarHwTqOvrlQlfr_Cnt_T_enum        | enum    | 2     | 15   |
|                      | BmwDrvgDynFacQlfr_Cnt_T_enum         | enum    | 2     | 15   |
|                      | BmwTarSteerTqDrvrActrQlfr_Cnt_T_enum | enum    | 2     | 15   |
|                      | BmwTrfcJamAssiDampgStReq_Cnt_T_enum  | enum    | 1     | 15   |
|                      | Fac_Cnt_T_logl                       | boolean | FALSE | TRUE |
|                      | MotTqCmdOvrlEquZero_Cnt_T_logl       | boolean | FALSE | TRUE |
|                      | MotTqCmdPwrLimd_MotNwtMtr_T_f32      | float32 | -8.8  | 8.8  |
| **Return Value**     | N/A                                  |         |       |      |

#### Design Rationale

Implementation of "StateMachine" Simulink state machine

#### Processing

Refer FDD

### Local Function StateMachineInit

|                      |                                      |         |       |      |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | StateMachineInit                     | Type    | Min   | Max  |
| **Arguments Passed** | ErrMod_Cnt_T_logl                    | boolean | FALSE | TRUE |
|                      | AllwTran_Cnt_T_logl                  | boolean | FALSE | TRUE |
|                      | ErrIf_Cnt_T_logl                     | boolean | FALSE | TRUE |
|                      | BmwTarHwTqOvrlQlfr_Cnt_T_enum        | enum    | 2     | 15   |
|                      | BmwDrvgDynFacQlfr_Cnt_T_enum         | enum    | 2     | 15   |
|                      | BmwTarSteerTqDrvrActrQlfr_Cnt_T_enum | enum    | 2     | 15   |
|                      | BmwTrfcJamAssiDampgStReq_Cnt_T_enum  | enum    | 1     | 15   |
|                      | MotTqCmdPwrLimdActvtUppr_Cnt_T_logl  | boolean | FALSE | TRUE |
|                      | MotTqCmdPwrLimdActvtLowr_Cnt_T_logl  | boolean | FALSE | TRUE |
| **Return Value**     | N/A                                  |         |       |      |

#### Design Rationale

Implementation of INIT State

#### Processing

Refer FDD

### Local Function StateMachineIfAvl

|                      |                                       |         |       |      |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | StateMachineIfAvl                     | Type    | Min   | Max  |
| **Arguments Passed** | ErrMod_Cnt_T_logl                     | boolean | FALSE | TRUE |
|                      | AllwTran_Cnt_T_logl                   | boolean | FALSE | TRUE |
|                      | ErrIf_Cnt_T_logl                      | boolean | FALSE | TRUE |
|                      | BmwTarHwTqOvrlQlfr_Cnt_T_enum         | enum    | 2     | 15   |
|                      | BmwDrvgDynFacQlfr_Cnt_T_enum          | enum    | 2     | 15   |
|                      | BmwTarSteerTqDrvrActrQlfr_Cnt_T_enum  | enum    | 2     | 15   |
|                      | BmwTrfcJamAssiDampgStReq_Cnt_T_enum   | enum    | 1     | 15   |
|                      | MotTqCmdPwrLimdDeactvtLowr_Cnt_T_logl | boolean | FALSE | TRUE |
| **Return Value**     | N/A                                   |         |       |      |

#### Design Rationale

Implementation of IF_AVL State

#### Processing

Refer FDD

### Local Function StateMachineIfActv

|                      |                                      |         |       |      |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | StateMachineIfActv                   | Type    | Min   | Max  |
| **Arguments Passed** | ErrMod_Cnt_T_logl                    | boolean | FALSE | TRUE |
|                      | AllwTran_Cnt_T_logl                  | boolean | FALSE | TRUE |
|                      | ErrIf_Cnt_T_logl                     | boolean | FALSE | TRUE |
|                      | BmwTarHwTqOvrlQlfr_Cnt_T_enum        | enum    | 2     | 15   |
|                      | BmwDrvgDynFacQlfr_Cnt_T_enum         | enum    | 2     | 15   |
|                      | BmwTarSteerTqDrvrActrQlfr_Cnt_T_enum | enum    | 2     | 15   |
|                      | BmwTrfcJamAssiDampgStReq_Cnt_T_enum  | enum    | 1     | 15   |
|                      | ErrIfTi_Cnt_T_logl                   | boolean | FALSE | TRUE |
| **Return Value**     | N/A                                  |         |       |      |

#### Design Rationale

Implementation of IF_ACTV State

#### Processing

Refer FDD

### Local Function StateMachineStbEpsSts

|                      |                                      |         |       |      |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | StateMachineStbEpsSts                | Type    | Min   | Max  |
| **Arguments Passed** | ErrMod_Cnt_T_logl                    | boolean | FALSE | TRUE |
|                      | AllwTran_Cnt_T_logl                  | boolean | FALSE | TRUE |
|                      | ErrIf_Cnt_T_logl                     | boolean | FALSE | TRUE |
|                      | BmwTarHwTqOvrlQlfr_Cnt_T_enum        | enum    | 2     | 15   |
|                      | BmwDrvgDynFacQlfr_Cnt_T_enum         | enum    | 2     | 15   |
|                      | BmwTarSteerTqDrvrActrQlfr_Cnt_T_enum | enum    | 2     | 15   |
|                      | BmwTrfcJamAssiDampgStReq_Cnt_T_enum  | enum    | 1     | 15   |
|                      | Fac_Cnt_T_logl                       | boolean | FALSE | TRUE |
|                      | MotTqCmdOvrlEquZero_Cnt_T_logl       | boolean | FALSE | TRUE |
|                      | MotTqCmdPwrLimdActvtUppr_Cnt_T_logl  | boolean | FALSE | TRUE |
| **Return Value**     | N/A                                  |         |       |      |

#### Design Rationale

Implementation of STB_EPS_STS State

#### Processing

Refer FDD

### Local Function StateMachineEntry

|                      |                                |         |       |      |
|----------------------|--------------------------------|---------|-------|------|
| **Function Name**    | StateSrvNotAvlStbEpsSts        | Type    | Min   | Max  |
| **Arguments Passed** | N/A                            |         |       |      |
| **Return Value**     | DrvgDynActv_Cnt_T_logl         | boolean | FALSE | TRUE |
|                      | DrvgDynIfSt_Cnt_T_enum         | enum    | 32    | 255  |
|                      | OutpTqOvrlRampInEna_Cnt_T_logl | boolean | FALSE | TRUE |

#### Design Rationale

Implementation of "StateMachine" Entry sections

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
| 5           | CF089A_BmwDrvgDynStMac_Design                                                                                                                                                                                                         | See Synergy Sub Project Version |

{% endraw %}