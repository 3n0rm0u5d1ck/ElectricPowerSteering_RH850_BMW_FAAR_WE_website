---
layout: default
title: BmwVehSpd_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**BmwVehSpd**

**June 22, 2018**

**Prepared By:**

**Marek Brykczyński,**

**Nexteer Automotive,**

**Tychy, Poland  
<u>Change History</u>**

|                                   |                   |             |             |
|-------------------------------------|-------------|---------|-------------|
| **Description**                   | **Author**        | **Version** | **Date**    |
| Initial version                   | Matthew Leser     | 1.0         | 27-Feb-2018 |
| Updated according to design 3.0.0 | Marek Brykczyński | 2.0         | 25-Jun-2018 |

**  
**

<u>Table of Contents</u>

1 Introduction 5

1.1 Purpose 5

1.2 Scope 5

2 BmwVehSpd High-Level Description 6

3 Design details of software module 7

3.1 Graphical representation of BmwVehSpd 7

3.2 Data Flow Diagram 7

3.2.1 Component level DFD 7

3.2.2 Function level DFD 7

4 Constant Data Dictionary 8

4.1 Program (fixed) Constants 8

4.1.1 Embedded Constants 8

5 Software Component Implementation 9

5.1 Sub-Module Functions 9

5.1.1 BmwVehSpdInit1 9

5.1.1.1 Design Rationale 9

5.1.1.2 Module Outputs 9

5.1.2 BmwVehSpdPer1 9

5.1.2.1 Design Rationale 9

5.1.2.2 Module Outputs 9

5.2 Server Runnables 9

5.3 Interrupt Functions 9

5.3.1 Interrupt Function Name 9

5.4 Module Internal (Local) Functions 9

5.4.1 Cntr 9

5.4.2 VehSpdVldCalcn 10

5.4.3 VehSpdRateLim 10

5.4.4 ProcessSecondAndGateState 10

5.4.5 ProcessThirdAndGateState 10

5.4.6 ProcessSixthAndGateState 10

5.4.7 ProcessFourthAndGateState 11

5.4.8 ProcessThridConditionOfOrGate 11

5.5 GLOBAL Function/Macro Definitions 11

6 Known Limitations with Design 12

7 UNIT TEST CONSIDERATION 13

Appendix A Abbreviations and Acronyms 14

Appendix B Glossary 15

Appendix C Please references 16

# Introduction

## Purpose

Module Design Document for CF080A_BmwVehSpd_Impl

## Scope

The following definitions are used throughout this document:

-   **<u>Shall</u>**: indicates a mandatory requirement without
    exception in compliance.

-   **<u>Should</u>**: indicates a mandatory requirement; exceptions
    allowed only with documented justification.

-   **<u>May</u>**: indicates an optional action.

# BmwVehSpd High-Level Description

The BmwVehSpd software component is responsible for determining the
Vehicle Speed.

# Design details of software module

Please refer FDD

## Graphical representation of BmwVehSpd

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/CF080A_BmwVehSpd_Impl/doc/mediax/media/image2.png"
style="width:6.5in;height:4.37153in" />

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

## BmwVehSpdInit1

## Design Rationale

Please refer FDD

## Module Outputs

None

## BmwVehSpdPer1

## Design Rationale

Please refer FDD.

## Module Outputs

None

## Server Runnables 

None

## Interrupt Functions

None

## Interrupt Function Name

None

## Module Internal (Local) Functions

### Cntr

|                      |                             |                          |       |      |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | Cntr                        | Type                     | Min   | Max  |
| **Arguments Passed** | CntrTrigInp_Cnt_T_logl      | boolean                  | FALSE | TRUE |
|                      | SigValVld_Cnt_T_logl        | const pointer to boolean | FALSE | TRUE |
|                      | CdnDurnSigValVld_Cnt_T_logl | const pointer to boolean | FALSE | TRUE |
| **Return Value**     | None                        | \-                       | \-    | \-   |

### VehSpdVldCalcn

|                      |                              |         |       |      |
|----------------------|------------------------------|---------|-------|------|
| **Function Name**    | VehSpdVldCalcn               | Type    | Min   | Max  |
| **Arguments Passed** | BmwSecurVehSpdSts_Cnt_T_enum | uint8   | 1     | 15   |
| **Return Value**     | VehSpdVld_Cnt_T_logl         | boolean | FALSE | TRUE |

### VehSpdRateLim

|                      |                              |         |     |     |
|----------------------|------------------------------|---------|-----|-----|
| **Function Name**    | VehSpdRateLim                | Type    | Min | Max |
| **Arguments Passed** | BmwSecurVehSpdSts_Cnt_T_enum | uint8   | 1   | 15  |
|                      | IntEpsVehSpd_Kph_T_f32       | float32 | 0   | 350 |
| **Return Value**     | \*Rte_Pim_VehSpdLimPrev()    | float32 | 0   | 511 |

### ProcessSecondAndGateState

|                      |                                |         |       |      |
|----------------------|--------------------------------|---------|-------|------|
| **Function Name**    | ProcessSecondAndGateState      | Type    | Min   | Max  |
| **Arguments Passed** | BmwCogVehSpdVld_Cnt_T_logl     | boolean | FALSE | TRUE |
|                      | BmwCogVehSpdQlfrVld_Cnt_T_logl | boolean | FALSE | TRUE |
|                      | BmwCogVehSpdQlfr_Cnt_T_enum    | uint8   | 1     | 15   |
| **Return Value**     | SecondAndGateEval_Cnt_T_logl   | boolean | FALSE | TRUE |

### ProcessThirdAndGateState

|                      |                                |         |       |      |
|----------------------|--------------------------------|---------|-------|------|
| **Function Name**    | ProcessThirdAndGateState       | Type    | Min   | Max  |
| **Arguments Passed** | BmwCogVehSpdVld_Cnt_T_logl     | boolean | FALSE | TRUE |
|                      | BmwCogVehSpdQlfrVld_Cnt_T_logl | boolean | FALSE | TRUE |
|                      | BmwCogVehSpdQlfr_Cnt_T_enum    | uint8   | 1     | 15   |
| **Return Value**     | ThirdAndGateEval_Cnt_T_logl    | boolean | FALSE | TRUE |

###  [section]

### ProcessSixthAndGateState

|                      |                             |         |       |      |
|----------------------|-----------------------------|---------|-------|------|
| **Function Name**    | ProcessSixthAndGateState    | Type    | Min   | Max  |
| **Arguments Passed** | BmwPinionAgQlfr_Cnt_T_enum  | boolean | FALSE | TRUE |
| **Return Value**     | SixthAndGateEval_Cnt_T_logl | boolean | FALSE | TRUE |

### ProcessFourthAndGateState

|                      |                             |         |       |      |
|----------------------|-----------------------------|---------|-------|------|
| **Function Name**    | ProcessFourthAndGateState   | Type    | Min   | Max  |
| **Arguments Passed** | ThirdAndGateEval_Cnt_T_logl | boolean | FALSE | TRUE |
|                      | SixthAndGateEval_Cnt_T_logl | boolean | FALSE | TRUE |
| **Return Value**     | function’s return value     | boolean | FALSE | TRUE |

### ProcessThridConditionOfOrGate

|                      |                                |         |       |      |
|----------------------|--------------------------------|---------|-------|------|
| **Function Name**    | ProcessThridConditionOfOrGate  | Type    | Min   | Max  |
| **Arguments Passed** | BmwCogVehSpdQlfrVld_Cnt_T_logl | boolean | FALSE | TRUE |
|                      | CdnDurnSigValVld_Cnt_T_logl    | boolean | FALSE | TRUE |
|                      | BmwCogVehSpdQlfr_Cnt_T_enum    | uint8   | 1     | 15   |
| **Return Value**     | LogicResult_Cnt_T_logl         | boolean | FALSE | TRUE |

## GLOBAL Function/Macro Definitions

None

# Known Limitations with Design

None.

# UNIT TEST CONSIDERATION

None

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
| 5           | FDD: CF080A_BmwVehSpd_Design                                                                                                                                          | See Synergy subproject version |

{% endraw %}