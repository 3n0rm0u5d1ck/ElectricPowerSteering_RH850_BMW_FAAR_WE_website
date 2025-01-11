---
layout: default
title: BmwHwAgArbnAndEotPosn_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**BmwHwAgArbnAndEotPosn**

**12-Jul-2018**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                                                                       |                   |             |             |
|--------------------------------|------------------|-----------|------------|
| **Description**                                                       | **Author**        | **Version** | **Date**    |
| Initial Version                                                       | Krzysztof Byrski  | 1           | 25-Oct-2017 |
| Updated Local Functions arguments                                     | Krzysztof Byrski  | 2           | 08-Nov-2017 |
| Updated Diagram and Function Inputs                                   | Matthew Leser     | 3           | 16-Jan-2018 |
| Updated to Design version 3.0.0                                       | Krzysztof Byrski  | 4           | 15-Mar-2018 |
| Updated to Design version 5.1.0                                       | Marek Brykczyński | 5           | 29-Jun-2018 |
| Updated graphic to include 2 new inputs, modified and added functions | Shawn Penning     | 6           | 12-Jul-2018 |

**  
**

<u>Table of Contents</u>

T

1 Introduction 5

1.1 Purpose 5

1.2 Scope 5

2 BmwHwAgArbnAndEotPosn & High-Level Description 6

3 Design details of software module 7

3.1 Graphical representation of BmwHwAgArbnAndEotPosn 7

3.2 Data Flow Diagram 8

3.2.1 Component level DFD 8

3.2.2 Function level DFD 8

4 Constant Data Dictionary 9

4.1 Program (fixed) Constants 9

4.1.1 Embedded Constants 9

5 Software Component Implementation 10

5.1 Sub-Module Functions 10

5.1.1 Init: BmwHwAgArbnAndEotPosnInit1 10

5.1.2 Per: BmwHwAgArbnAndEotPosnPer1 10

5.2 Server Runables 11

5.2.1 ClrBmwRackCentrToVehCentrOffs_Oper 11

5.2.2 ClrVehCentrPosn_Oper 11

5.2.3 SetVehCentrPosn_Oper 11

5.3 Interrupt Functions 11

5.4 Module Internal (Local) Functions 12

5.4.1 HwAgSnsrNotTrimNTC 12

5.4.2 HwPosnFltDetn 12

5.4.3 PinionAgFltTmr 12

5.4.4 OffsCorrnTmr 13

5.4.5 InitTmr 13

5.4.6 CalcBmwMotAgOffsSelnSt 13

5.4.7 CalcBmwMotAgOffsSelnStOffsCmpd 14

5.4.8 CalcBmwMotAgOffsSelnStSubVal 14

5.4.9 CalcBmwMotAgOffsSelnStTmpCmpd 14

5.4.10 CalcBmwMotAgOffsSelnStOffsCorrn 15

5.4.11 CalcBmwMotAgOffsSelnStSigInvld 15

5.4.12 CalcBmwMotAgOffsSelnStIni 15

5.4.13 BmwMotAgOffsSelnStTranCase 16

5.4.14 ChkNrcvrlFlt 16

5.4.15 TurnCntrCorrlnStsTmr 16

5.4.16 ChkTurnCntrCorrlnStsCdn 16

5.4.17 ProcessBmwQuadRotorOffs1 16

5.4.18 ProcessBmwQuadRotorOffs2 17

5.4.20 ProcessBmwQuadOffsSts 17

5.4.21 ActvtLpFil 17

5.4.22 CalcBmwPinionAgOffs 17

5.4.23 BmwMotAgSelnStOffsCmpd 18

5.4.24 BmwMotAgSelnStSigInvld 19

5.4.25 PinionAgCalc 19

5.4.26 ClrNotCmplPinionAgFlg 19

5.4.27 CalcEot 20

5.4.28 SetBmwRackCentrToVehCentrOffs 20

5.4.29 HndlgNTC 21

5.5 GLOBAL Function/Macro Definitions 22

6 Known Limitations with Design 23

7 UNIT TEST CONSIDERATION 24

Appendix A Abbreviations and Acronyms 25

Appendix B Glossary 26

Appendix C References 27

# Introduction

## Purpose

Module Design Document for CF071A_BmwHwAgArbnAndEotPosn_Impl.

## Scope

The following definitions are used throughout this document:

-   **<u>Shall</u>**: indicates a mandatory requirement without
    exception in compliance.

-   **<u>Should</u>**: indicates a mandatory requirement; exceptions
    allowed only with documented justification.

-   **<u>May</u>**: indicates an optional action.

# BmwHwAgArbnAndEotPosn & High-Level Description

This function will be responsible for determining the hand wheel
position using the motor position to provide an estimate of the hand
wheel position.

# Design details of software module

## Graphical representation of BmwHwAgArbnAndEotPosn

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/CF071A_BmwHwAgArbnAndEotPosn_Impl/doc/mediax/media/image1.png"
style="width:4.61741in;height:8.38768in" />

## Data Flow Diagram

Refer FDD

### Component level DFD

N/A

### Function level DFD

N/A

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

None

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

### ClrBmwRackCentrToVehCentrOffs_Oper

#### Design Rationale

Refer FDD

####  (Processing of function)………

Refer FDD

### ClrVehCentrPosn_Oper

#### Design Rationale

Refer FDD

####  (Processing of function)………

Refer FDD

### SetVehCentrPosn_Oper

#### Design Rationale

Refer FDD

####  (Processing of function)………

Refer FDD

## Interrupt Functions

None

## Module Internal (Local) Functions

### HwAgSnsrNotTrimNTC

|                      |                               |         |       |      |
|----------------------|-------------------------------|---------|-------|------|
| **Function Name**    | HwAgSnsrNotTrimNTC            | Type    | Min   | Max  |
| **Arguments Passed** | None                          |         |       |      |
| **Return Value**     | HwAgSnsrNotTrimFlt_Cnt_T_logl | boolean | FALSE | TRUE |

#### Design Rationale

Refer FDD

#### Processing

Refer FDD

### HwPosnFltDetn

|                      |                               |         |       |      |
|----------------------|-------------------------------|---------|-------|------|
| **Function Name**    | HwPosnFltDetn                 | Type    | Min   | Max  |
| **Arguments Passed** | MotAgVld_Cnt_T_logl           | boolean | FALSE | TRUE |
|                      | HwAgSnsrNotTrimFlt_Cnt_T_logl | boolean | FALSE | TRUE |
| **Return Value**     | PinionAgFltTmrElpd_Cnt_T_logl | boolean | FALSE | TRUE |

#### Design Rationale

Refer FDD

#### Processing

Refer FDD

### PinionAgFltTmr

|                      |                               |         |       |      |
|----------------------|-------------------------------|---------|-------|------|
| **Function Name**    | PinionAgFltTmr                | Type    | Min   | Max  |
| **Arguments Passed** | HwAgSnsrNotTrimFlt_Cnt_T_logl | boolean | FALSE | TRUE |
| **Return Value**     | PinionAgFltTmrElpd_Cnt_T_logl | boolean | FALSE | TRUE |

#### Design Rationale

Refer FDD

#### Processing

Refer FDD

### OffsCorrnTmr

|                      |                             |         |       |      |
|----------------------|-----------------------------|---------|-------|------|
| **Function Name**    | OffsCorrnTmr                | Type    | Min   | Max  |
| **Arguments Passed** | None                        |         |       |      |
| **Return Value**     | OffsCorrnTmrElpd_Cnt_T_logl | boolean | FALSE | TRUE |

#### Design Rationale

Refer FDD

#### Processing

Refer FDD

### InitTmr

|                      |                             |         |       |      |
|----------------------|-----------------------------|---------|-------|------|
| **Function Name**    | InitTmr                     | Type    | Min   | Max  |
| **Arguments Passed** | None                        |         |       |      |
| **Return Value**     | AllwExitFromInit_Cnt_T_logl | boolean | FALSE | TRUE |

#### Design Rationale

Refer FDD

#### Processing

Refer FDD

### CalcBmwMotAgOffsSelnSt

|                      |                               |         |       |      |
|----------------------|-------------------------------|---------|-------|------|
| **Function Name**    | CalcBmwMotAgOffsSelnSt        | Type    | Min   | Max  |
| **Arguments Passed** | TurnCntrVld_Cnt_T_logl        | boolean | FALSE | TRUE |
|                      | BmwQuadOffsSts_Cnt_T_enum     | enum    | 0     | 15   |
|                      | PinionAgFltTmrElpd_Cnt_T_logl | boolean | FALSE | TRUE |
|                      | OffsCorrnTmrElpd_Cnt_T_logl   | boolean | FALSE | TRUE |
|                      | HwAgNotVldFltPrsnt_Cnt_T_logl | boolean | FALSE | TRUE |
|                      | AllwExitFromInit_Cnt_T_logl   | boolean | FALSE | TRUE |
|                      | AllwTran_Cnt_T_logl           | boolean | FALSE | TRUE |
| **Return Value**     | None                          |         |       |      |

#### Design Rationale

Refer FDD

#### Processing

Refer FDD

### CalcBmwMotAgOffsSelnStOffsCmpd

|                      |                                |         |       |      |
|----------------------|--------------------------------|---------|-------|------|
| **Function Name**    | CalcBmwMotAgOffsSelnStOffsCmpd | Type    | Min   | Max  |
| **Arguments Passed** | TurnCntrVld_Cnt_T_logl         | boolean | FALSE | TRUE |
|                      | BmwQuadOffsSts_Cnt_T_enum      | enum    | 0     | 15   |
|                      | HwAgNotVldFltPrsnt_Cnt_T_logl  | boolean | FALSE | TRUE |
|                      | AllwTran_Cnt_T_logl            | boolean | FALSE | TRUE |
| **Return Value**     | None                           |         |       |      |

#### Design Rationale

Refer FDD

#### Processing

Refer FDD

### CalcBmwMotAgOffsSelnStSubVal

|                      |                               |         |       |      |
|----------------------|-------------------------------|---------|-------|------|
| **Function Name**    | CalcBmwMotAgOffsSelnStSubVal  | Type    | Min   | Max  |
| **Arguments Passed** | BmwQuadOffsSts_Cnt_T_enum     | enum    | 0     | 15   |
|                      | HwAgNotVldFltPrsnt_Cnt_T_logl | boolean | FALSE | TRUE |
|                      | AllwTran_Cnt_T_logl           | boolean | FALSE | TRUE |
| **Return Value**     | None                          |         |       |      |

#### Design Rationale

Refer FDD

#### Processing

Refer FDD

### CalcBmwMotAgOffsSelnStTmpCmpd

|                      |                               |         |       |      |
|----------------------|-------------------------------|---------|-------|------|
| **Function Name**    | CalcBmwMotAgOffsSelnStTmpCmpd | Type    | Min   | Max  |
| **Arguments Passed** | BmwQuadOffsSts_Cnt_T_enum     | enum    | 0     | 15   |
|                      | HwAgNotVldFltPrsnt_Cnt_T_logl | boolean | FALSE | TRUE |
|                      | AllwTran_Cnt_T_logl           | boolean | FALSE | TRUE |
| **Return Value**     | None                          |         |       |      |

#### Design Rationale

Refer FDD

#### Processing

Refer FDD

### CalcBmwMotAgOffsSelnStOffsCorrn

|                      |                                 |         |       |      |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | CalcBmwMotAgOffsSelnStOffsCorrn | Type    | Min   | Max  |
| **Arguments Passed** | OffsCorrnTmrElpd_Cnt_T_logl     | boolean | FALSE | TRUE |
|                      | HwAgNotVldFltPrsnt_Cnt_T_logl   | boolean | FALSE | TRUE |
|                      | AllwTran_Cnt_T_logl             | boolean | FALSE | TRUE |
| **Return Value**     | None                            |         |       |      |

#### Design Rationale

Refer FDD

#### Processing

Refer FDD

### CalcBmwMotAgOffsSelnStSigInvld

|                      |                                |         |       |      |
|----------------------|--------------------------------|---------|-------|------|
| **Function Name**    | CalcBmwMotAgOffsSelnStSigInvld | Type    | Min   | Max  |
| **Arguments Passed** | TurnCntrVld_Cnt_T_logl         | boolean | FALSE | TRUE |
|                      | PinionAgFltTmrElpd_Cnt_T_logl  | boolean | FALSE | TRUE |
|                      | HwAgNotVldFltPrsnt_Cnt_T_logl  | boolean | FALSE | TRUE |
|                      | AllwTran_Cnt_T_logl            | boolean | FALSE | TRUE |
| **Return Value**     | None                           |         |       |      |

#### Design Rationale

Refer FDD

#### Processing

Refer FDD

### CalcBmwMotAgOffsSelnStIni

|                      |                               |         |       |      |
|----------------------|-------------------------------|---------|-------|------|
| **Function Name**    | CalcBmwMotAgOffsSelnStIni     | Type    | Min   | Max  |
| **Arguments Passed** | TurnCntrVld_Cnt_T_logl        | boolean | FALSE | TRUE |
|                      | HwAgNotVldFltPrsnt_Cnt_T_logl | boolean | FALSE | TRUE |
|                      | AllwExitFromInit_Cnt_T_logl   | boolean | FALSE | TRUE |
|                      | AllwTran_Cnt_T_logl           | boolean | FALSE | TRUE |
| **Return Value**     | None                          |         |       |      |

#### Design Rationale

Refer FDD

#### Processing

Refer FDD

### BmwMotAgOffsSelnStTranCase

|                      |                                   |         |             |             |
|------------|---------------------------|---------|-------------|-------------|
| **Function Name**    | BmwMotAgOffsSelnStTranCase        | Type    | Min         | Max         |
| **Arguments Passed** | BmwQuadOffsSts_Cnt_T_enum         | enum    | 0           | 15          |
|                      | HwAgSnsrNotTrimFlt_Cnt_T_logl     | boolean | FALSE       | TRUE        |
|                      | MotAgTurnCntrDeg_MotDeg_T_f32     | float32 | -82944000   | 83008800    |
|                      | TurnCntrVld_Cnt_T_logl            | boolean | FALSE       | TRUE        |
|                      | PrevLoopBmwMotAgSelnSt_Cnt_T_enum | enum    | 2           | 15          |
|                      | BmwQuadRotorOffs_MotRev_T_s08     | sint8   | -127        | 127         |
|                      | MotAgCumvAlgnMrf_MotDeg_T_f32     | float32 | -262144     | 262143.9998 |
| **Return Value**     | PinionAgTarConf_Uls_T_f32         | float32 | 0           | 1           |
|                      | MotPosnDegArbd_MotDeg_T_f32       | float32 | \- 83206144 | 83270944\>  |

### ChkNrcvrlFlt

|                      |                     |      |     |     |
|----------------------|---------------------|------|-----|-----|
| **Function Name**    | ChkNrcvrlFlt        | Type | Min | Max |
| **Arguments Passed** | Ntc8CSts_Cnt_T_enum | enum | 1   | 2   |
|                      | Ntc8ESts_Cnt_T_enum | enum | 1   | 2   |
| **Return Value**     | \-                  | \-   | \-  | \-  |

### TurnCntrCorrlnStsTmr

|                      |                             |      |     |     |
|----------------------|-----------------------------|------|-----|-----|
| **Function Name**    | TurnCntrCorrlnStsTmr        | Type | Min | Max |
| **Arguments Passed** | TurnCntrCorrlnSts_Cnt_T_u08 | enum | 0   | 3   |
| **Return Value**     | \-                          | \-   | \-  | \-  |

### ChkTurnCntrCorrlnStsCdn

|                      |                             |      |     |     |
|----------------------|-----------------------------|------|-----|-----|
| **Function Name**    | ChkTurnCntrCorrlnStsCdn     | Type | Min | Max |
| **Arguments Passed** | TurnCntrCorrlnSts_Cnt_T_u08 | enum | 0   | 3   |
| **Return Value**     | \-                          | \-   | \-  | \-  |

### ProcessBmwQuadRotorOffs1

|                      |                               |         |       |      |
|----------------------|-------------------------------|---------|-------|------|
| **Function Name**    | ProcessBmwQuadRotorOffs       | Type    | Min   | Max  |
| **Arguments Passed** | BmwQuadOffsSts_Cnt_T_enum, ,  | Enum    | 0     | 15   |
|                      | BmwQuadRotorOffs_MotRev_T_s08 | sint8   | -127  | 127  |
|                      | ChgdValDetd_Cnt_T_logl        | boolean | FALSE | TRUE |
| **Return Value**     | \-                            | \-      | \-    | \-   |

### ProcessBmwQuadRotorOffs2

|                      |                               |         |       |      |
|----------------------|-------------------------------|---------|-------|------|
| **Function Name**    | ProcessBmwQuadRotorOffs       | Type    | Min   | Max  |
| **Arguments Passed** | BmwQuadOffsSts_Cnt_T_enum, ,  | Enum    | 0     | 15   |
|                      | BmwQuadRotorOffs_MotRev_T_s08 | sint8   | -127  | 127  |
|                      | ChgdValDetd_Cnt_T_logl        | boolean | FALSE | TRUE |
| **Return Value**     | \-                            | \-      | \-    | \-   |

###  [section]

### ProcessBmwQuadOffsSts

|                      |                           |         |       |      |
|----------------------|---------------------------|---------|-------|------|
| **Function Name**    | ProcessBmwQuadOffsSts     | Type    | Min   | Max  |
| **Arguments Passed** | BmwQuadOffsSts_Cnt_T_enum | enum    | 0     | 15   |
|                      | ChgdValDetd_Cnt_T_logl    | boolean | FALSE | TRUE |
| **Return Value**     | \-                        | \-      | \-    | \-   |

### ActvtLpFil

|                      |            |      |     |     |
|----------------------|------------|------|-----|-----|
| **Function Name**    | ActvtLpFil | Type | Min | Max |
| **Arguments Passed** | \-         | \-   | \-  | \-  |
| **Return Value**     | \-         | \-   | \-  | \-  |

### CalcBmwPinionAgOffs

|                      |                                  |         |       |      |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | CalcBmwPinionAgOffs              | Type    | Min   | Max  |
| **Arguments Passed** | BmwPinionAgOffs_HwDeg_T_f32      | float32 | -45   | 45   |
|                      | BmwPinionAgOffsSts_Cnt_T_enum    | enum    | 1     | 4    |
| **Return Value**     | -BmwPinionAgOffsOutp_HwDeg_T_f32 | float32 | -1440 | 1440 |

####  [section-1]

#### Design Rationale

Refer FDD

#### Processing

Refer FDD

### BmwMotAgSelnStOffsCmpd

|                      |                               |         |      |     |
|----------------------|-------------------------------|---------|------|-----|
| **Function Name**    | BmwMotAgSelnStOffsCmpd        | Type    | Min  | Max |
| **Arguments Passed** | BmwQuadRotorOffs_MotRev_T_s08 | sint8   | -127 | 127 |
| **Return Value**     | PinionAgTarConf_Uls_T_f32     | float32 | 0    | 1   |

#### Design Rationale

Refer FDD

#### Processing

Refer FDD

### BmwMotAgSelnStSigInvld

|                      |                                   |         |           |          |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | BmwMotAgSelnStSigInvld            | Type    | Min       | Max      |
| **Arguments Passed** | TurnCntrVld_Cnt_T_logl            | boolean | FALSE     | TRUE     |
|                      | PrevLoopBmwMotAgSelnSt_Cnt_T_enum | enum    | 2         | 15       |
|                      | HwAgSnsrNotTrimFlt_Cnt_T_logl     | boolean | FALSE     | TRUE     |
|                      | MotAgTurnCntrDeg_MotDeg_T_f32     | float32 | -82944000 | 83008800 |
| **Return Value**     | PinionAgTarConf_Uls_T_f32         | float32 | 0         | 0        |

#### Design Rationale

Refer FDD

#### Processing

Refer FDD

### PinionAgCalc

|                      |                                  |         |           |          |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | PinionAgCalc                     | Type    | Min       | Max      |
| **Arguments Passed** | OffsCpmpdMotPosn_MotDeg_T_f32    | float32 | -82989720 | 83054520 |
|                      | CmplncErrMotToPinion_HwDeg_T_f32 | float32 | -5        | 5        |
| **Return Value**     | BmwPinionAg_HwDeg_T_f32          | float32 | -1440     | 1440     |

#### Design Rationale

Refer FDD

#### Processing

Refer FDD

### ClrNotCmplPinionAgFlg

|                      |                                  |         |       |      |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | ClrNotCmplPinionAgFlg            | Type    | Min   | Max  |
| **Arguments Passed** | LongTermRackCentrCmpl_Cnt_T_logl | boolean | FALSE | TRUE |
| **Return Value**     | None                             |         |       |      |

#### Design Rationale

Refer FDD

#### Processing

Refer FDD

### CalcEot

|                      |                                  |         |       |      |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | CalcEot                          | Type    | Min   | Max  |
| **Arguments Passed** | TotRackTrvl_HwDeg_T_f32          | float32 | -2880 | 2880 |
|                      | LongTermRackCentrCmpl_Cnt_T_logl | boolean | FALSE | TRUE |
| **Return Value**     | HwAgEotCw_HwDeg_T_f32            | float32 | 360   | 900  |
|                      | HwAgEotCcw_HwDeg_T_f32           | float32 | -900  | -360 |
|                      | HwAgCwDetd_Cnt_T_logl            | boolean | FALSE | TRUE |
|                      | HwAgCcwDetd_Cnt_T_logl           | boolean | FALSE | TRUE |

#### Design Rationale

Refer FDD

#### Processing

Refer FDD

### SetBmwRackCentrToVehCentrOffs

|                      |                                  |         |       |      |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | SetBmwRackCentrToVehCentrOffs    | Type    | Min   | Max  |
| **Arguments Passed** | LongTermRackCentrCmpl_Cnt_T_logl | boolean | FALSE | TRUE |
|                      | RackCentrPinionAg_HwDeg_T_f32    | float32 | -1440 | 1440 |
| **Return Value**     | None                             |         |       |      |

#### Design Rationale

Refer FDD

#### Processing

Refer FDD

### HndlgNTC

|                      |                                |         |       |      |
|----------------------|--------------------------------|---------|-------|------|
| **Function Name**    | HndlgNTC                       | Type    | Min   | Max  |
| **Arguments Passed** | VehSpdVld_Cnt_T_logl           | boolean | FALSE | TRUE |
|                      | VehSpd_Kph_T_f32               | float32 | 0     | 350  |
|                      | BmwVehSpdSts_Cnt_T_enum        | enum    | 1     | 15   |
|                      | DiKineIntegrityTest_Cnt_T_logl | boolean | FALSE | TRUE |
| **Return Value**     | None                           |         |       |      |

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
| 2           | MDD Guideline EA4                                                                                                                                                                                                                     | 01.00.01                        |
| 3           | EA4 Software Naming Conventions                                                                                                                                                                                                       | 01.01.00                        |
| 4           | Software Design and Coding Standards                                                                                                                                                                                                  | 2.1                             |
| 5           | CF071A_BmwHwAgArbnAndEotPosn_Design                                                                                                                                                                                                   | See Synergy Sub Project Version |

{% endraw %}