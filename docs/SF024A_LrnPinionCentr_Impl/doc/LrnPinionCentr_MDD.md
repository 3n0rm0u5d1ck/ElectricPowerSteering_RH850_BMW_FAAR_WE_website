---
layout: default
title: LrnPinionCentr_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**LrnPinionCentr**

**12-Jan-2018**

**Prepared By:**

**Brendon Binder,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**<u>Change History</u>**

|                                             |            |             |             |
|-------------------------------------------|-------------|-------|----------|
| **Description**                             | **Author** | **Version** | **Date**    |
| Initial Version                             | ML         | 1.0         | 18-Sep-2017 |
| Updated DaVinci graphic for Cal name change | BRB        | 2.0         | 12-Jan-2018 |

**  
**

<u>Table of Contents</u>

1 Introduction 5

1.1 Purpose 5

1.2 Scope 5

2 LrnPinionCentr & High-Level Description 6

3 Design details of software module 7

3.1 Graphical representation of LrnPinionCentr 7

3.2 Data Flow Diagram 7

3.2.1 Component level DFD 7

3.2.2 Function level DFD 7

4 Constant Data Dictionary 8

4.1 Program (fixed) Constants 8

4.1.1 Embedded Constants 8

5 Software Component Implementation 9

5.1 Sub-Module Functions 9

5.1.1 Init: LrnPinionCentrInit1 9

5.1.1.1 Design Rationale 9

5.1.2 Per: LrnPinionCentrPer1 9

5.1.2.1 Design Rationale 9

5.2 Server Runnable 9

5.2.1 SetInpPrm 9

5.3 Interrupt Functions 9

5.4 Module Internal (Local) Functions 9

5.4.1 Local Function \#1 9

5.4.1.1 Description 9

5.4.2 Local Function \#2 9

5.4.2.1 Description 10

5.4.3 Local Function \#3 10

5.4.3.1 Description 10

5.4.4 Local Function \#4 10

5.4.4.1 Description 10

5.4.5 Local Function \#5 10

5.4.5.1 Description 11

5.4.6 Local Function \#6 11

5.4.6.1 Description 11

5.5 GLOBAL Function/Macro Definitions 11

6 Known Limitations with Design 12

7 UNIT TEST CONSIDERATION 13

Appendix A Abbreviations and Acronyms 14

Appendix B Glossary 15

Appendix C References 16

# Introduction

## Purpose

## Scope

# LrnPinionCentr & High-Level Description

*Refer FDD.*

# Design details of software module

## Graphical representation of LrnPinionCentr 

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/SF024A_LrnPinionCentr_Impl/doc/mediax/media/image2.png"
style="width:2.6896in;height:3.24079in" />

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

| Constant Name                                      | Resolution | Units | Value |
|---------------------------------|---------------|-----------|-------------|
| Refer DataDict.m file from FDD for other constants | \-         | \-    | \-    |

# Software Component Implementation

## Sub-Module Functions

## Init: LrnPinionCentrInit1

> Refer FDD Simulink model

## Design Rationale

> Refer to Anomaly EA4#17174. Implementation deviates to fix this issue
> for build.

## Per: LrnPinionCentrPer1

> Refer FDD Simulink Model

## Design Rationale

None

## Server Runnable

###  SetInpPrm

> Refer FDD Simulink Model

## Interrupt Functions

None

## Module Internal (Local) Functions

## Local Function \#1

|                      |                              |         |         |        |
|--------------|------------------------------|---------|-----------|-----------|
| **Function Name**    | RunMinMax                    | Type    | Min     | Max    |
| **Arguments Passed** | HwAg_HwDeg_T_f32             | float32 | -1440.0 | 1440.0 |
|                      | PinionCentrLrnEna_Cnt_T_logl | boolean | FALSE   | TRUE   |
|                      | \*MaxHwPosn_HwDeg_T_f32      | float32 | -1440.0 | 1440.0 |
|                      | \*MinHwPosn_HwDeg_T_f32      | float32 | -1440.0 | 1440.0 |
| **Return Value**     | None                         |         |         |        |

## Description

Implementation of ‘Running MinMax’ function.

## Local Function \#2

|                      |                              |         |         |        |
|--------------|------------------------------|---------|-----------|-----------|
| **Function Name**    | PosAgVelStCtrl1              | Type    | Min     | Max    |
| **Arguments Passed** | HwAg_HwDeg_T_f32             | float32 | -1440.0 | 1440.0 |
|                      | MotVelCrf_MotRadPerSec_T_f32 | float32 | -1350.0 | 1350.0 |
|                      | TarMotVel_MotRadPerSec_T_f32 | float32 | 0.0     | 1600.0 |
|                      | \*PinionCentrLrnSt_Cnt_T_u08 | uint8   | 0       | 7      |
|                      | \*TqCmd_MotNwtMtr_T_f32      | float32 | -8.8    | 8.8    |
|                      | \*MotPosnCmd_MotRad_T_f32    | float32 | -1440.0 | 1440.0 |
| **Return Value**     | None                         |         |         |        |

## Description

Implementation of ‘POSANGVEL State Control 1’ function.

## Local Function \#3

|                      |                              |         |         |        |
|--------------|------------------------------|---------|-----------|-----------|
| **Function Name**    | PosMotTqStCtrl2              | Type    | Min     | Max    |
| **Arguments Passed** | \*PinionCentrLrnSt_Cnt_T_u08 | uint8   | 0       | 7      |
|                      | \*TqCmd_MotNwtMtr_T_f32      | float32 | -8.8    | 8.8    |
|                      | \*MotPosnCmd_MotRad_T_f32    | float32 | -1440.0 | 1440.0 |
| **Return Value**     | None                         |         |         |        |

## Description

Implementation of ‘POSMTRTRQ State Control 2’ function.

## Local Function \#4

|                      |                              |         |         |        |
|--------------|------------------------------|---------|-----------|-----------|
| **Function Name**    | NegAgVelStCtrl3              | Type    | Min     | Max    |
| **Arguments Passed** | HwAg_HwDeg_T_f32             | float32 | -1440.0 | 1440.0 |
|                      | MotVelCrf_MotRadPerSec_T_f32 | float32 | -1350.0 | 1350.0 |
|                      | TarMotVel_MotRadPerSec_T_f32 | float32 | 0.0     | 1600.0 |
|                      | \*PinionCentrLrnSt_Cnt_T_u08 | uint8   | 0       | 7      |
|                      | \*TqCmd_MotNwtMtr_T_f32      | float32 | -8.8    | 8.8    |
|                      | \*MotPosnCmd_MotRad_T_f32    | float32 | -1440.0 | 1440.0 |
| **Return Value**     | None                         |         |         |        |

## Description

Implementation of ‘NEGANGVEL State Control 3’ function.

## Local Function \#5

|                      |                              |         |         |        |
|--------------|------------------------------|---------|-----------|-----------|
| **Function Name**    | NegMotTqStCtrl4              | Type    | Min     | Max    |
| **Arguments Passed** | MaxHwPosn_HwDeg_T_f32        | float32 | -1440.0 | 1440.0 |
|                      | MinHwPosn_HwDeg_T_f32        | float32 | -1440.0 | 1440.0 |
|                      | \*PinionCentrLrnSt_Cnt_T_u08 | uint8   | 0       | 7      |
|                      | \*TqCmd_MotNwtMtr_T_f32      | float32 | -8.8    | 8.8    |
|                      | \*MotPosnCmd_MotRad_T_f32    | float32 | -1440.0 | 1440.0 |
| **Return Value**     | None                         |         |         |        |

## Description

Implementation of ‘NEGMTRTRQ State Control 4’ function.

## Local Function \#6

|                      |                              |         |         |        |
|--------------|------------------------------|---------|-----------|-----------|
| **Function Name**    | MoveToStCtrl5                | Type    | Min     | Max    |
| **Arguments Passed** | HwAg_HwDeg_T_f32             | float32 | -1440.0 | 1440.0 |
|                      | TarHwAg_HwDeg_T_f32          | float32 | -1440.0 | 1440.0 |
|                      | MotVelCrf_MotRadPerSec_T_f32 | float32 | -1350.0 | 1350.0 |
|                      | TarMotVel_MotRadPerSec_T_f32 | float32 | 0.0     | 1600.0 |
|                      | \*PinionCentrLrnSt_Cnt_T_u08 | uint8   | 0       | 7      |
|                      | \*TqCmd_MotNwtMtr_T_f32      | float32 | -8.8    | 8.8    |
|                      | \*MotPosnCmd_MotRad_T_f32    | float32 | -1440.0 | 1440.0 |
| **Return Value**     | None                         |         |         |        |

## Description

Implementation of ‘MOVETO State Control 5’ function.

## GLOBAL Function/Macro Definitions

None

# Known Limitations with Design

None

# UNIT TEST CONSIDERATION

> None

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

| **Ref. \#** | **Title**                                                                                                                                                           | **Version**                    |
|-------|--------------------------------------------------|----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:AUTOSAR_SWS_MemoryMapping.pdf)                                                                                        | v1.4.0 R4.0 Rev 3              |
| 2           | MDD Guideline                                                                                                                                                       | EA4 01.00.01                   |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc) | 1.0                            |
| 4           | Software Design and Coding Standards.doc                                                                                                                            | 2.01                           |
| 5           | FDD – SF024A_LrnPinionCentr_Design                                                                                                                                  | See Synergy Subproject verison |

{% endraw %}