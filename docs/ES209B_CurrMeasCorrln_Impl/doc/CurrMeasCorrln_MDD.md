---
layout: default
title: CurrMeasCorrln_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**Current Measurement Correlation**

**21-Feb-2018** **Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Shawn Penning,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                              |               |             |             |
|------------------------------|---------------|-------------|-------------|
| **Description**              | **Author**    | **Version** | **Date**    |
| Initial version              | Nick Saxton   | 1.0         | 26-Apr-2016 |
| Update per design rev. 1.6.0 | Shawn Penning | 2.0         | 23-May-2017 |
| Update graphic design 2.0    | Shawn Penning | 3.0         | 21-Feb-2018 |

<u>Table of Contents</u>

[1 Current Measurement Correlation & High-Level Description
[5](#current-measurement-correlation-high-level-description)](#current-measurement-correlation-high-level-description)

[2 Design details of software module
[6](#design-details-of-software-module)](#design-details-of-software-module)

[2.1 Graphical representation of Current Measurement Correlation
[6](#graphical-representation-of-current-measurement-correlation)](#graphical-representation-of-current-measurement-correlation)

[2.2 Data Flow Diagram [6](#data-flow-diagram)](#data-flow-diagram)

[2.2.1 Component level DFD
[6](#component-level-dfd)](#component-level-dfd)

[2.2.2 Function level DFD [6](#function-level-dfd)](#function-level-dfd)

[3 Constant Data Dictionary
[7](#constant-data-dictionary)](#constant-data-dictionary)

[3.1 Program (fixed) Constants
[7](#program-fixed-constants)](#program-fixed-constants)

[3.1.1 Embedded Constants [7](#embedded-constants)](#embedded-constants)

[3.1.1.1 Local [7](#local)](#local)

[4 Software Component Implementation
[8](#software-component-implementation)](#software-component-implementation)

[4.1 Sub-Module Functions
[8](#sub-module-functions)](#sub-module-functions)

[4.1.1 Initialization Functions
[8](#initialization-functions)](#initialization-functions)

[4.1.1.1 INIT [8](#init)](#init)

[4.1.1.2 Design Rationale [8](#design-rationale)](#design-rationale)

[4.1.1.3 Store Module Inputs to Local copies
[8](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[4.1.1.4 (Processing of function)………
[8](#processing-of-function)](#processing-of-function)

[4.1.1.5 Store Local copy of outputs into Module Outputs
[8](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[4.1.2 PERIODIC FUNCTIONS [8](#periodic-functions)](#periodic-functions)

[4.1.2.1 Per: CurrMeasCorrlnPer1
[8](#per-currmeascorrlnper1)](#per-currmeascorrlnper1)

[4.1.2.2 Design Rationale [8](#design-rationale-1)](#design-rationale-1)

[4.1.2.3 Store Module Inputs to Local copies
[8](#store-module-inputs-to-local-copies-1)](#store-module-inputs-to-local-copies-1)

[4.1.2.4 (Processing of function)………
[8](#processing-of-function-1)](#processing-of-function-1)

[4.1.2.5 Store Local copy of outputs into Module Outputs
[8](#store-local-copy-of-outputs-into-module-outputs-1)](#store-local-copy-of-outputs-into-module-outputs-1)

[4.2 Server Runables [8](#server-runnables)](#server-runnables)

[4.3 Interrupt Functions
[8](#interrupt-functions)](#interrupt-functions)

[4.4 Module Internal (Local) Functions
[9](#module-internal-local-functions)](#module-internal-local-functions)

[4.5 Local Function/Macro Definitions
[9](#local-functionmacro-definitions)](#local-functionmacro-definitions)

[4.5.1 Local Function \#1 SigAvlChk
[9](#local-function-1-sigavlchk)](#local-function-1-sigavlchk)

[4.5.1.1 Description [9](#description)](#description)

[4.5.2 Local Function \#2 CurrMeasCorrlnChk
[9](#local-function-2-currmeascorrlnchk)](#local-function-2-currmeascorrlnchk)

[4.5.2.1 Description [9](#description-1)](#description-1)

[4.6 GLOBAL Function/Macro Definitions
[9](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[5 Known Limitations with Design
[10](#known-limitations-with-design)](#known-limitations-with-design)

[6 UNIT TEST CONSIDERATION
[11](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[12](#continuous-improvent-cr-ea412527-written-for-output-range-correction-for-currmeascorrlnsts.abbreviations-and-acronyms)](#continuous-improvent-cr-ea412527-written-for-output-range-correction-for-currmeascorrlnsts.abbreviations-and-acronyms)

[Appendix B Glossary [13](#glossary)](#glossary)

[Appendix C References [15](#references)](#references)

# Current Measurement Correlation & High-Level Description

Refer FDD

# Design details of software module

## Graphical representation of Current Measurement Correlation

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/ES209B_CurrMeasCorrln_Impl/doc/mediax/media/image1.png"
style="width:3.55208in;height:3.97917in" />

## Data Flow Diagram

Refer FDD

### Component level DFD

Refer FDD

### Function level DFD

Refer FDD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

## Local

| Constant Name            | Units | Value  |
|--------------------------|-------|--------|
| CORRLNSTSABC_CNT_U08     | Cnt   | 0x07   |
| CURRMOTSUMLOLIM_AMPR_F32 | Ampr  | 0.0F   |
| CURRMOTSUMHILIM_AMPR_F32 | Ampr  | 600.0F |

# Software Component Implementation

## Sub-Module Functions

## Initialization Functions

## INIT

None

## Design Rationale

None

## Store Module Inputs to Local copies

None

##  (Processing of function)…

None

## Store Local copy of outputs into Module Outputs

None

## PERIODIC FUNCTIONS 

## Per: CurrMeasCorrlnPer1

## Design Rationale

*Refer FDD*

## Store Module Inputs to Local copies

*Refer FDD*

## (Processing of function)…

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*Refer FDD*

## Server Runnables 

*None*

## Interrupt Functions

*None*

## Module Internal (Local) Functions

## Local Function/Macro Definitions

## Local Function \#1 SigAvlChk

|                      |                             |          |               |               |
|-------------|------------------------------|--------|-----------|-----------|
| **Function Name**    | SigAvlChk                   | Type     | Min           | Max           |
| **Arguments Passed** | MotCurrQlfr1_Cnt_T_enum     | SigQlfr1 | SIGQLFR_NORES | SIGQLFR_FAILD |
|                      | MotCurrRollgCntr1_Cnt_T_u08 | uint8    | 0             | 255           |
| **Return Value**     | SigAvlABC_Cnt_T_logl        | boolean  | FALSE         | TRUE          |

## Description

Refer FDD.

## Local Function \#2 CurrMeasCorrlnChk

|                      |                                              |         |       |      |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | CurrMeasCorrlnChk                            | Type    | Min   | Max  |
| **Arguments Passed** | MotCurrCorrdA_Ampr_T_f32                     | float32 | -200  | 200  |
|                      | MotCurrCorrdB_Ampr_T_f32                     | float32 | -200  | 200  |
|                      | MotCurrCorrdC_Ampr_T_f32                     | float32 | -200  | 200  |
|                      | \*CurrMeasLongTermCorrlnStsVldABC_Cnt_T_logl | boolean | FALSE | TRUE |
|                      | \*CurrMotSumABC_Ampr_T_f32                   | float32 | 0     | 600  |
| **Return Value**     | CurrMeasImdtCorrlnStsVldABC_Cnt_T_logl       | boolean | FALSE | TRUE |

## Description

Refer FDD.

\* CurrMeasLongTermCorrlnStsVldABC_Cnt_T_logl and \*
CurrMotSumABC_Ampr_T_f32 are outputs of this function.

## GLOBAL Function/Macro Definitions

None

# Known Limitations with Design

In Signal Availability, SigQlfr sets up 3 possible results:

0 = No Result

1 = Pass

2 = Fail

The model converts this enumerated type to uint8 and checks if less than
2 (Fail). The code differs in that it checks explicitly for No Result
(SIGQLFR_NORES) or Pass (SIGQLFR_PASSD).

# UNIT TEST CONSIDERATION

####### Continuous improvent CR EA4#12527 written for output range correction for CurrMeasCorrlnSts.Abbreviations and Acronyms

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

| **Ref. \#** | **Title**                                                                                                                                                       | **Version**            |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping                                                                                                                         | v1.3.0 R4.0 Rev 2      |
| 2           | MDD Guideline                                                                                                                                                   | EA4 01.01.00           |
| 3           | [Software Naming Conventions](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc) | 01.01.00               |
| 4           | Software Design and Coding Standards                                                                                                                            | 2.1                    |
| 5           | FDD – ES209A Current Measurement Correlation                                                                                                                    | See synergy subversion |

{% endraw %}