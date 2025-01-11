---
layout: default
title: CurrMeas_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**CurrMeas**

**Mar 23, 2018**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                                                                                                        |                  |             |             |
|---------------------------|------------------|--------------|--------------|
| **Description**                                                                                        | **Author**       | **Version** | **Date**    |
| Initial Version                                                                                        | Krzysztof Byrski | 1.0         | 19-May-2017 |
| Fixed anomaly EA4#13330 by using required NVM blocks as applicable                                     | Krishna Anne     | 2.0         | 16-Oct-17   |
| Created local functions for reducing the complexity of OffsetCalibration and GainCalibration functions | Mrudula Paturi   | 3.0         | 23-Mar-18   |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [5](#introduction)](#introduction)

[1.1 Purpose [5](#purpose)](#purpose)

[1.2 Scope [5](#scope)](#scope)

[2 CurrMeas & High-Level Description
[6](#currmeas-high-level-description)](#currmeas-high-level-description)

[3 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of CurrMeas
[7](#graphical-representation-of-currmeas)](#graphical-representation-of-currmeas)

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

[5.1.1 Init: CurrMeasInit1 [9](#init-init1)](#init-init1)

[5.1.2 Per: CurrMeasPer1 [9](#per-per1)](#per-per1)

[5.1.3 Per: CurrMeasPer2 [9](#per-per2)](#per-per2)

[5.1.4 Per: CurrMeasPer3 [10](#per-per3)](#per-per3)

[5.2 Server Runables [11](#server-runables)](#server-runables)

[5.2.1 CurrMeasEolGainReq_Oper
[11](#currmeaseolgainreq_oper)](#currmeaseolgainreq_oper)

[5.2.2 CurrMeasEolGainStsReq_Oper
[11](#currmeaseolgainstsreq_oper)](#currmeaseolgainstsreq_oper)

[5.2.3 CurrMeasEolOffsReq_Oper
[11](#currmeaseoloffsreq_oper)](#currmeaseoloffsreq_oper)

[5.2.4 CurrMeasEolOffsStsReq_Oper
[11](#currmeaseoloffsstsreq_oper)](#currmeaseoloffsstsreq_oper)

[5.2.5 CurrMeasGainReadReqSngIvtr_Oper
[11](#currmeasgainreadreqsngivtr_oper)](#currmeasgainreadreqsngivtr_oper)

[5.2.6 CurrMeasGainWrReqSngIvtr_Oper
[11](#currmeasgainwrreqsngivtr_oper)](#currmeasgainwrreqsngivtr_oper)

[5.2.7 CurrMeasOffsReadReqSngIvtr_Oper
[12](#currmeasoffsreadreqsngivtr_oper)](#currmeasoffsreadreqsngivtr_oper)

[5.2.8 CurrMeasOffsWrReqSngIvtr_Oper
[12](#currmeasoffswrreqsngivtr_oper)](#currmeasoffswrreqsngivtr_oper)

[5.3 Interrupt Functions
[13](#interrupt-functions)](#interrupt-functions)

[5.4 Module Internal (Local) Functions
[13](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 OffsetCalibration [13](#offsetcalibration)](#offsetcalibration)

[5.4.2 GainCalibration [14](#gaincalibration)](#gaincalibration)

[5.4.3 RangeChkWIABC [14](#rangechkwiabc)](#rangechkwiabc)

[5.4.4 ProtocolChkENABC [15](#protocolchkenabc)](#protocolchkenabc)

[5.4.5 CalcMotCurrMotAgCorrd
[15](#calcmotcurrmotagcorrd)](#calcmotcurrmotagcorrd)

[5.4.6 CalMotCurrCorrdABC
[15](#calmotcurrcorrdabc)](#calmotcurrcorrdabc)

[5.4.7 OffsCalcABC [16](#offscalcabc)](#offscalcabc)

[5.5 GLOBAL Function/Macro Definitions
[17](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[6 Known Limitations with Design
[18](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[19](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[20](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [21](#glossary)](#glossary)

[Appendix C References [22](#references)](#references)

# Introduction

## Purpose

Module Design Document for ES200B_CurrMeas.

## Scope

The following definitions are used throughout this document:

-   **<u>Shall</u>**: indicates a mandatory requirement without
    exception in compliance.

-   **<u>Should</u>**: indicates a mandatory requirement; exceptions
    allowed only with documented justification.

-   **<u>May</u>**: indicates an optional action.

# CurrMeas & High-Level Description

Refer FDD.

# Design details of software module

## Graphical representation of CurrMeas

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/ES200B_CurrMeas_Impl/doc/mediax/media/image2.png"
style="width:5.20833in;height:7.09583in" />

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

| Constant Name                     | Resolution             | Units  | Value       |
|---------------------------------|---------------|-----------|-------------|
| CALPROCNOTSTRTD_CNT_U08           | 1                      | Cnt    | 0           |
| CALPROCSTRTD_CNT_U08              | 1                      | Cnt    | 1           |
| CALPROCPASS_CNT_U08               | 1                      | Cnt    | 2           |
| CALPROCPHAABCEOLOUTOFRNG_CNT_U08  | 1                      | Cnt    | 4           |
| CALPROCVEHSPDCNDNOTMET_CNT_U08    | 1                      | Cnt    | 16          |
| CALPROCMOTVELMRFCNDNOTMET_CNT_U08 | 1                      | Cnt    | 64          |
| VEHSPDCDNNOTMET_CNT_U08           | 1                      | Cnt    | 4           |
| MOTVELMRFCDNNOTMET_CNT_U08        | 1                      | Cnt    | 8           |
| DIAGCSTSINVTRINACTV_CNT_U08       | 1                      | Cnt    | 16          |
| FAILDATENA_CNT_U08                | 1                      | Cnt    | 2           |
| FAILDATWRMININ_CNT_U08            | 1                      | Cnt    | 3           |
| INVTRINACTV_CNT_U08               | 1                      | Cnt    | 8           |
| DIFOFFSRNGCHKMAX_VOLT_F32         | Single precision float | Volt   | 1.0         |
| DEGREES30_MOTRAD_F32              | Single precision float | MotRad | 0.5236      |
| MAXCURRCORRD_AMPR_F32             | Single precision float | Ampr   | 200.0       |
| PHAONTIBCOK_CNT_U08               | 1                      | Cnt    | 0x03        |
| PHAONTIACOK_CNT_U08               | 1                      | Cnt    | 0x05        |
| PHAONTIABOK_CNT_U08               | 1                      | Cnt    | 0x06        |
| PHAONTIABCOK_CNT_U08              | 1                      | Cnt    | 0x07        |
| PHAONTIA_CNT_U08                  | 1                      | Cnt    | 0x04        |
| PHAONTIB_CNT_U08                  | 1                      | Cnt    | 0x02        |
| PHAONTIC_CNT_U08                  | 1                      | Cnt    | 0x01        |
| NANOSECTOSEC_ULS_F32              | Single precision float | Uls    | 0.000000001 |

# Software Component Implementation

## Sub-Module Functions

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

### Per: Per2

#### Design Rationale

Refer FDD

#### Store Module Inputs to Local copies

Refer FDD

#### (Processing of function)………

Refer FDD

#### Store Local copy of outputs into Module Outputs

Refer FDD

### Per: Per3

#### Design Rationale

Refer FDD

#### Store Module Inputs to Local copies

Refer FDD

#### (Processing of function)………

Refer FDD

#### Store Local copy of outputs into Module Outputs

Refer FDD

## Server Runables 

### CurrMeasEolGainReq_Oper

#### Design Rationale

Refer FDD

#### (Processing of function)………

Refer FDD

### CurrMeasEolGainStsReq_Oper

#### Design Rationale

Refer FDD

#### (Processing of function)………

Refer FDD

### CurrMeasEolOffsReq_Oper

#### Design Rationale

Refer FDD

#### (Processing of function)………

Refer FDD

### CurrMeasEolOffsStsReq_Oper

#### Design Rationale

Refer FDD

### CurrMeasGainReadReqSngIvtr_Oper

#### Design Rationale

Refer FDD

#### (Processing of function)………

Refer FDD

### CurrMeasGainWrReqSngIvtr_Oper

#### Design Rationale

Refer FDD

#### (Processing of function)………

Refer FDD

### CurrMeasOffsReadReqSngIvtr_Oper

#### Design Rationale

Refer FDD

#### (Processing of function)………

Refer FDD

### CurrMeasOffsWrReqSngIvtr_Oper

#### Design Rationale

Refer FDD

#### (Processing of function)………

Refer FDD

## Interrupt Functions

None

## Module Internal (Local) Functions

### OffsetCalibration

|                      |                                |         |         |        |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | OffsetCalibration              | Type    | Min     | Max    |
| **Arguments Passed** | MotCurrAdcVlyA_Volt_T_f32      | float32 | 0.0     | 5.0    |
|                      | MotCurrAdcVlyB_Volt_T_f32      | float32 | 0.0     | 5.0    |
|                      | MotCurrAdcVlyC_Volt_T_f32      | float32 | 0.0     | 5.0    |
|                      | MotVelMrf_MotRadPerSec_T_f32   | float32 | -1350.0 | 1350.0 |
|                      | VehSpd_Kph_T_f32               | float32 | 0.0     | 511.0  |
|                      | VehSpdVld_Cnt_T_logl           | boolean | FALSE   | TRUE   |
|                      | BrdgVltg_Volt_T_f32            | float32 | 6.0     | 26.5   |
|                      | DiagcStsIvtr1Inactv_Cnt_T_logl | boolean | FALSE   | TRUE   |
| **Return Value**     | N/A                            | \-      | \-      | \-     |

#### Design Rationale

Refer FDD

#### Processing

Refer FDD

### GainCalibration

|                      |                                  |                  |         |        |
|--------------|-------------------------------|------------|--------|--------|
| **Function Name**    | GainCalibration                  | Type             | Min     | Max    |
| **Arguments Passed** | MotCurrEolOffsProcFlg_Cnt_T_logl | boolean          | FALSE   | TRUE   |
|                      | MotCurrAdcVlyA_Volt_T_f32        | float32          | 0.0     | 5.0    |
|                      | MotCurrAdcVlyB_Volt_T_f32        | float32          | 0.0     | 5.0    |
|                      | MotCurrAdcVlyC_Volt_T_f32        | float32          | 0.0     | 5.0    |
|                      | MotVelMrf_MotRadPerSec_T_f32     | float32          | -1350.0 | 1350.0 |
|                      | MotCurrOffsZeroAvrgA_Volt_T_f32  | float32          | 0.0     | 5.0    |
|                      | MotCurrOffsZeroAvrgB_Volt_T_f32  | float32          | 0.0     | 5.0    |
|                      | MotCurrOffsZeroAvrgC_Volt_T_f32  | float32          | 0.0     | 5.0    |
|                      | VehSpd_Kph_T_f32                 | float32          | 0.0     | 511.0  |
|                      | VehSpdVld_Cnt_T_logl             | boolean          | FALSE   | TRUE   |
|                      | DiagcStsIvtr1Inactv_Cnt_T_logl   | boolean          | FALSE   | TRUE   |
|                      | MotCurrEolCalStPrev_Cnt_T_enum   | MotCurrEolCalSt2 | 0       | 8      |
| **Return Value**     | N/A                              | \-               | \-      | \-     |

#### Design Rationale

Refer FDD

#### Processing

Refer FDD

### RangeChkWIABC

|                      |                           |         |       |      |
|----------------------|---------------------------|---------|-------|------|
| **Function Name**    | RangeChkWIABC             | Type    | Min   | Max  |
| **Arguments Passed** | MotCurrAdcVlyA_Volt_T_f32 | float32 | 0.0   | 5.0  |
|                      | MotCurrAdcVlyB_Volt_T_f32 | float32 | 0.0   | 5.0  |
|                      | MotCurrAdcVlyC_Volt_T_f32 | float32 | 0.0   | 5.0  |
| **Return Value**     | InRng_Cnt_T_logl          | boolean | FALSE | TRUE |

#### Design Rationale

Refer FDD

#### Processing

Refer FDD

### ProtocolChkENABC

|                      |                          |         |       |      |
|----------------------|--------------------------|---------|-------|------|
| **Function Name**    | ProtocolChkENABC         | Type    | Min   | Max  |
| **Arguments Passed** | N/A                      | \-      | \-    | \-   |
| **Return Value**     | ProtocolChkEn_Cnt_T_logl | boolean | FALSE | TRUE |

#### Design Rationale

Refer FDD

#### Processing

Refer FDD

### CalcMotCurrMotAgCorrd

|                      |                                     |         |         |        |
|--------------|-------------------------------|---------|----------|----------|
| **Function Name**    | CalcMotCurrMotAgCorrd               | Type    | Min     | Max    |
| **Arguments Passed** | N/A                                 | \-      | \-      | \-     |
| **Return Value**     | MotCtrlCurrMeasMotAgCorrd_Rad_T_f32 | float32 | -0.7666 | 6.2832 |

#### Design Rationale

Refer FDD

#### Processing

Refer FDD

### CalMotCurrCorrdABC

|                      |                         |         |            |           |
|--------------|-------------------------------|---------|----------|----------|
| **Function Name**    | CalMotCurrCorrdABC      | Type    | Min        | Max       |
| **Arguments Passed** | MotCurrOffsA_Volt_T_f32 | float32 | -1892868,5 | 1892873,5 |
|                      | MotCurrOffsA_Volt_T_f32 | float32 | -1892868,5 | 1892873,5 |
|                      | MotCurrOffsA_Volt_T_f32 | float32 | -1892868,5 | 1892873,5 |
| **Return Value**     | N/A                     |         |            |           |

#### Design Rationale

Refer FDD

#### Processing

Refer FDD

### OffsCalcABC

|                      |                         |         |            |           |
|--------------|-------------------------------|---------|----------|----------|
| **Function Name**    | OffsCalcABC             | Type    | Min        | Max       |
| **Arguments Passed** | N/A                     |         |            |           |
| **Return Value**     | MotCurrOffsA_Volt_T_f32 | float32 | -1892868,5 | 1892873,5 |
|                      | MotCurrOffsB_Volt_T_f32 | float32 | -1892868,5 | 1892873,5 |
|                      | MotCurrOffsC_Volt_T_f32 | float32 | -1892868,5 | 1892873,5 |

#### Design Rationale

Refer FDD

#### Processing

Refer FDD

### GainCmdAD

|                      |                                 |         |     |     |
|----------------------|---------------------------------|---------|-----|-----|
| **Function Name**    | GainCmdAD                       | Type    | Min | Max |
| **Arguments Passed** | MotCurrAdcVlyA_Volt_T_f32       | float32 | 0.0 | 5.0 |
|                      | MotCurrOffsZeroAvrgA_Volt_T_f32 | float32 | 0.0 | 5.0 |
| **Return Value**     | N/A                             |         |     |     |

#### Design Rationale

This function is created for reducing the complexity of GainCalibration
function

#### Processing

Refer the source file

### GainCmdBE

|                      |                                 |         |     |     |
|----------------------|---------------------------------|---------|-----|-----|
| **Function Name**    | GainCmdBE                       | Type    | Min | Max |
| **Arguments Passed** | MotCurrAdcVlyB_Volt_T_f32       | float32 | 0.0 | 5.0 |
|                      | MotCurrOffsZeroAvrgB_Volt_T_f32 | float32 | 0.0 | 5.0 |
| **Return Value**     | N/A                             |         |     |     |

#### Design Rationale

This function is created for reducing the complexity of GainCalibration
function

#### Processing

Refer the source file

### GainCmdCF

|                      |                                 |         |     |     |
|----------------------|---------------------------------|---------|-----|-----|
| **Function Name**    | GainCmdCF                       | Type    | Min | Max |
| **Arguments Passed** | MotCurrAdcVlyC_Volt_T_f32       | float32 | 0.0 | 5.0 |
|                      | MotCurrOffsZeroAvrgC_Volt_T_f32 | float32 | 0.0 | 5.0 |
| **Return Value**     | N/A                             |         |     |     |

#### Design Rationale

This function is created for reducing the complexity of GainCalibration
function

#### 5.4.10.2 Processing [processing-9]

Refer the source file

### CmdSafest

|                      |                                |         |       |      |
|----------------------|--------------------------------|---------|-------|------|
| **Function Name**    | CmdSafest                      | Type    | Min   | Max  |
| **Arguments Passed** | DiagcStsIvtr1Inactv_Cnt_T_logl | boolean | FALSE | TRUE |
| **Return Value**     | N/A                            |         |       |      |

#### Design Rationale

This function is created for reducing the complexity of GainCalibration
function

#### 5.4.11.2 Processing [processing-10]

Refer the source file

### OffsCmdHI

|                      |                           |         |     |      |
|----------------------|---------------------------|---------|-----|------|
| **Function Name**    | OffsCmdHI                 | Type    | Min | Max  |
| **Arguments Passed** | MotCurrAdcVlyA_Volt_T_f32 | float32 | 0.0 | 5.0  |
|                      | MotCurrAdcVlyB_Volt_T_f32 | float32 | 0.0 | 5.0  |
|                      | MotCurrAdcVlyC_Volt_T_f32 | float32 | 0.0 | 5.0  |
|                      | BrdgVltg_Volt_T_f32       | float32 | 6.0 | 26.5 |
| **Return Value**     | N/A                       |         |     |      |

#### Design Rationale

This function is created for reducing the complexity of
OffsetCalibration function

#### 5.4.12.2 Processing [processing-11]

Refer the source file

### OffsCmdLO

|                      |                           |         |     |     |
|----------------------|---------------------------|---------|-----|-----|
| **Function Name**    | OffsCmdLO                 | Type    | Min | Max |
| **Arguments Passed** | MotCurrAdcVlyA_Volt_T_f32 | float32 | 0.0 | 5.0 |
|                      | MotCurrAdcVlyB_Volt_T_f32 | float32 | 0.0 | 5.0 |
|                      | MotCurrAdcVlyC_Volt_T_f32 | float32 | 0.0 | 5.0 |
| **Return Value**     | N/A                       |         |     |     |

#### Design Rationale

This function is created for reducing the complexity of
OffsetCalibration function

#### 5.4.13.2 Processing [processing-12]

Refer the source file

### OffsCmdZERO

|                      |                           |         |     |     |
|----------------------|---------------------------|---------|-----|-----|
| **Function Name**    | OffsCmdZERO               | Type    | Min | Max |
| **Arguments Passed** | MotCurrAdcVlyA_Volt_T_f32 | float32 | 0.0 | 5.0 |
|                      | MotCurrAdcVlyB_Volt_T_f32 | float32 | 0.0 | 5.0 |
|                      | MotCurrAdcVlyC_Volt_T_f32 | float32 | 0.0 | 5.0 |
| **Return Value**     | N/A                       |         |     |     |

#### Design Rationale

This function is created for reducing the complexity of
OffsetCalibration function

#### 5.4.14.2 Processing [processing-13]

Refer the source file

### OffsCmdEND

|                      |                                |         |       |      |
|----------------------|--------------------------------|---------|-------|------|
| **Function Name**    | OffsCmdEND                     | Type    | Min   | Max  |
| **Arguments Passed** | DiagcStsIvtr1Inactv_Cnt_T_logl | boolean | FALSE | TRUE |
| **Return Value**     | N/A                            |         |       |      |

#### Design Rationale

This function is created for reducing the complexity of
OffsetCalibration function

#### 5.4.15.2 Processing [processing-14]

Refer the source file

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

| **Ref. \#** | **Title**                                                                                                                                          | **Version**                     |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf)) | v1.3.0 R4.0 Rev 2               |
| 2           | MDD Guideline                                                                                                                                      | EA4 01.00.01                    |
| 3           | Software Naming Conventions                                                                                                                        | 01.01.00                        |
| 4           | Software Design and Coding Standards                                                                                                               | 2.1                             |
| 5           | ES200B_CurrMeas_Design                                                                                                                             | See Synergy Sub Project Version |

{% endraw %}