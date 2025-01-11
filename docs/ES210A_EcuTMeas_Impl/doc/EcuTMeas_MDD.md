---
layout: default
title: EcuTMeas_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**EcuTMeas**

**26-Sep-2017**

**Prepared By:**

**Brendon Binder,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|           |                                                                                                                                                                                         |                  |             |             |
|------|----------------------------------------|---------|-------|----------|
| **Sl.No** | **Description**                                                                                                                                                                         | **Author**       | **Version** | **Date**    |
| 1         | Initial Version                                                                                                                                                                         | SB               | 1.0         | 23-Mar-2015 |
| 2         | ADC Hooks are added as input                                                                                                                                                            | KK               | 2.0         | 21-Mar-2016 |
| 3         | Added local constants for paramterbyte definitions                                                                                                                                      | AJM              | 3.0         | 10-Apr-2017 |
| 4         | Updated the graphical representation (all cal ports are removed), added local constants, design rationale, known limitations and unit tests considerations. Updated to the new template | Shruthi Raghavan | 4.0         | 08-Aug-2017 |
| 5         | Updated the DaVinci model (added new output).                                                                                                                                           | Brendon Binder   | 5.0         | 26-Sep-2017 |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [4](#introduction)](#introduction)

[1.1 Purpose [4](#purpose)](#purpose)

[2 EcuTMeas & High-Level Description
[5](#ecutmeas-high-level-description)](#ecutmeas-high-level-description)

[3 Design details of software module
[6](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of EcuTMeas
[6](#graphical-representation-of-ecutmeas)](#graphical-representation-of-ecutmeas)

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

[5.1.1 Init: EcuTMeasInit1
[8](#init-ecutmeasinit1)](#init-ecutmeasinit1)

[5.1.1.1 Design Rationale [8](#design-rationale)](#design-rationale)

[5.1.2 Per: EcuTMeasPer1 [8](#per-ecutmeasper1)](#per-ecutmeasper1)

[5.1.2.1 Design Rationale [8](#design-rationale-1)](#design-rationale-1)

[5.2 Server Runables [8](#server-runables)](#server-runables)

[5.3 Interrupt Functions
[8](#interrupt-functions)](#interrupt-functions)

[5.4 Module Internal (Local) Functions
[8](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 Local Function \#1 [8](#local-function-1)](#local-function-1)

[5.4.1.1 Design Rationale [8](#design-rationale-2)](#design-rationale-2)

[5.5 GLOBAL Function/Macro Definitions
[8](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[5.5.1 GLOBAL Function \#1 [8](#global-function-1)](#global-function-1)

[6 Known Limitations with Design
[9](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[10](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[11](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [12](#glossary)](#glossary)

[Appendix C References [13](#references)](#references)

# Introduction

## Purpose

> Module design document for EcuTMeas

# EcuTMeas & High-Level Description

Measures and diagnoses an analog based temperature sensor on ECU.

This particular design can tolerate a transfer function that is not
necessarily linear but can be interpolated with 8 different XY pairs.

# Design details of software module

## Graphical representation of EcuTMeas

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/ES210A_EcuTMeas_Impl/doc/mediax/media/image2.png"
style="width:3.97411in;height:2.16304in" />

## Data Flow Diagram

### Component level DFD

> Refer FDD simulink model

### Function level DFD

> Refer FDD simulink model

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name                             | Resolution             | Units   | Value  | Defined In             |
|-------------------------|---------------|--------|-------|-----------------|
| ECUTFILDMIN_DEGCGRD_F32                   | Single Precision Float | DegCgrd | -50.0F | EcuTMeas.c             |
| ECUTFILDMAX_DEGCGRD_F32                   | Single Precision Float | DegCgrd | 150.0F | EcuTMeas.c             |
| NROFSNSRXYPT_CNT_U08                      | 1                      | Cnt     | 8U\*   | EcuTMeas_Cfg_private.h |
| Refer DataDict.m file for other constants | \-                     | \-      | \-     |                        |

\*This the value might change based on EcuTx and EcuTy table size.

# Software Component Implementation

## Sub-Module Functions

## Init: EcuTMeasInit1

> Refer FDD simulink model

## Design Rationale

> ‘Filter Initialization’ block in the FDD uses ‘FilLpInit’ library
> block twice rather than just once due to a design limitation with the
> Library block (see ‘Known limitations with design’). However, code has
> no such limitation. In code, the value to be written to the state
> variable according to the logic in ‘State Variable Initialization’ is
> calculated first. Then, the ‘FilLpInit’ library function is called
> just once and that will initialize the state variable with this
> calculated value and the gain according to the set frequency & time.

## Per: EcuTMeasPer1

> Refer FDD Simulink Model

## Design Rationale

None

## Server Runables 

> None

## Interrupt Functions

None

## Module Internal (Local) Functions

## Local Function \#1

|                      |     |      |     |     |
|----------------------|-----|------|-----|-----|
| **Function Name**    | \-  | Type | Min | Max |
| **Arguments Passed** | N/A | \-   | \-  | \-  |
| **Return Value**     | N/A | \-   | \-  | \-  |

## Design Rationale

N/A

## GLOBAL Function/Macro Definitions

## GLOBAL Function \#1

|                      |     |      |     |     |
|----------------------|-----|------|-----|-----|
| **Function Name**    | \-  | Type | Min | Max |
| **Arguments Passed** | N/A | \-   | \-  | \-  |
| **Return Value**     | N/A | \-   | \-  | \-  |

# Known Limitations with Design

1.  The FilLpInit block in the model cannot accept a variable as input
    for initialization of the state variable.

# UNIT TEST CONSIDERATION

1.  This component uses config params for some configurable constants.
    However for testing these in PIL/SIL, please use the following
    strategy:

    1.  Rename the **EcuTMeas_Cfg_private_pil.h** file in
        tools/local/include folder to EcuTMeas_Cfg_private.h

    2.  Replace the EcuTMeas_Cfg_private.h file in tools/local/generate
        folder with the above file.

> Now, Tessy must be able to modify the values of these config params.
> We should then test them with the range that is given in their
> definition in the DataDict.m file

####### Abbreviations and Acronyms

| **Abbreviation or Acronym** | **Description**                              |
|------------------------|------------------------------------------------|
| FDD                         | Functional Design Document. (See references) |

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

| **Ref. \#** | **Title**                                                                                                                                                                                                                             | **Version**                         |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](https://www.autosar.org/fileadmin/files/standards/classic/4-0/software-architecture/implementation-integration/standard/AUTOSAR_SWS_MemoryMapping.pdf)) | v1.4.0 R4.0 Rev 3                   |
| 2           | MDD Guideline                                                                                                                                                                                                                         | EA4 01.00.01                        |
| 3           | EA4 [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)                                                               | 01.01.00                            |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc)                                                                 | 2.1                                 |
| 5           | ES210A_EcuTMeas_Design (FDD)                                                                                                                                                                                                          | Refer subproject verison on Synergy |

{% endraw %}