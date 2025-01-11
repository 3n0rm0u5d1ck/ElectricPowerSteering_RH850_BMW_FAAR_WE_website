---
layout: default
title: MotAg0Meas_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**Motor Angle 0 Measurement**

**May** **04, 2018**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                                           |                  |             |             |
|------------------------|---------------------|--------------|--------------|
| **Description**                           | **Author**       | **Version** | **Date**    |
| Initial Version                           | Avinash James    | 1.0         | 06-Jun-2016 |
| Removed local function CalcTurnCntr       | Avinash James    | 2.0         | 13-Jun-2016 |
| Updated as per Design version 2.0.0       | Krzysztof Byrski | 3.0         | 19-Oct-2017 |
| Updated as per Design version 5.0.0       | Krzysztof Byrski | 4.0         | 25-Apr-2018 |
| Updated the diagram for IO port additions | Avinash James    | 5.0         | 27-Apr-2018 |
| Added updates for sensor offset learning  | Avinash James    | 6.0         | 04-May-2018 |

**  
**

<u>Table of Contents</u>

[1 Introduction [5](#introduction)](#introduction)

[1.1 Purpose [5](#purpose)](#purpose)

[1.2 Scope [5](#scope)](#scope)

[2 MotAg0MeasHigh-Level Description
[6](#motag0meashigh-level-description)](#motag0meashigh-level-description)

[3 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of MotAg0Meas
[7](#graphical-representation-of-motag0meas)](#graphical-representation-of-motag0meas)

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

[5.1.1 Init: MotAg0MeasInit1
[9](#init-motag0measinit1)](#init-motag0measinit1)

[5.1.1.1 Design Rationale [9](#design-rationale)](#design-rationale)

[5.1.1.2 Module Outputs [9](#module-outputs)](#module-outputs)

[5.1.1.3 Module Internal [9](#module-internal)](#module-internal)

[5.1.2 Per: MotAg0MeasPer1
[9](#per-motag0measper1)](#per-motag0measper1)

[5.1.2.1 Design Rationale [9](#design-rationale-1)](#design-rationale-1)

[5.1.2.2 Store Module Inputs to Local copies
[9](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[5.1.2.3 (Processing of function)………
[9](#processing-of-function)](#processing-of-function)

[5.1.2.4 Store Local copy of outputs into Module Outputs
[9](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[5.1.3 Per: MotAg0MeasPer2
[9](#per-motag0measper2)](#per-motag0measper2)

[5.1.3.1 Design Rationale [9](#design-rationale-2)](#design-rationale-2)

[5.1.3.2 Store Module Inputs to Local copies
[9](#store-module-inputs-to-local-copies-1)](#store-module-inputs-to-local-copies-1)

[5.1.3.3 (Processing of function)………
[10](#processing-of-function-1)](#processing-of-function-1)

[5.1.3.4 Store Local copy of outputs into Module Outputs
[10](#store-local-copy-of-outputs-into-module-outputs-1)](#store-local-copy-of-outputs-into-module-outputs-1)

[5.1.4 Per: MotAg0MeasPer3
[10](#per-motag0measper3)](#per-motag0measper3)

[5.1.4.1 Design Rationale
[10](#design-rationale-3)](#design-rationale-3)

[5.1.4.2 Store Module Inputs to Local copies
[10](#store-module-inputs-to-local-copies-2)](#store-module-inputs-to-local-copies-2)

[5.1.4.3 (Processing of function)………
[10](#processing-of-function-2)](#processing-of-function-2)

[5.1.4.4 Store Local copy of outputs into Module Outputs
[10](#store-local-copy-of-outputs-into-module-outputs-2)](#store-local-copy-of-outputs-into-module-outputs-2)

[5.2 Server Runables: MotAg0CoeffTblRead
[10](#server-runables-motag0coefftblread)](#server-runables-motag0coefftblread)

[5.2.1.1 Design Rationale
[10](#design-rationale-4)](#design-rationale-4)

[5.2.1.2 Store Module Inputs to Local copies
[10](#store-module-inputs-to-local-copies-3)](#store-module-inputs-to-local-copies-3)

[5.2.1.3 (Processing of function)………
[10](#processing-of-function-3)](#processing-of-function-3)

[5.2.1.4 Store Local copy of outputs into Module Outputs
[10](#store-local-copy-of-outputs-into-module-outputs-3)](#store-local-copy-of-outputs-into-module-outputs-3)

[5.3 Server Runables: MotAg0CoeffTblWr
[10](#server-runables-motag0coefftblwr)](#server-runables-motag0coefftblwr)

[5.3.1.1 Design Rationale
[10](#design-rationale-5)](#design-rationale-5)

[5.3.1.2 Store Module Inputs to Local copies
[10](#store-module-inputs-to-local-copies-4)](#store-module-inputs-to-local-copies-4)

[5.3.1.3 (Processing of function)………
[10](#processing-of-function-4)](#processing-of-function-4)

[5.3.1.4 Store Local copy of outputs into Module Outputs
[11](#store-local-copy-of-outputs-into-module-outputs-4)](#store-local-copy-of-outputs-into-module-outputs-4)

[5.4 Interrupt Functions
[11](#interrupt-functions)](#interrupt-functions)

[5.5 Module Internal (Local) Functions
[12](#module-internal-local-functions)](#module-internal-local-functions)

[5.5.1 ProcessErrorRegAndDieRevCtr
[12](#processerrorreganddierevctr)](#processerrorreganddierevctr)

[5.5.2 SPI_AnglePolarityAdjust [12](#section)](#section)

[5.5.3 SPIvsENCA [12](#spivsenca)](#spivsenca)

[5.5.4 CalcCorrnTbl [13](#calccorrntbl)](#calccorrntbl)

[5.5.5 MotAgFaultProcessing
[13](#motagfaultprocessing)](#motagfaultprocessing)

[5.5.6 CalcNtcPrm [14](#calcntcprm)](#calcntcprm)

[5.5.7 SetMotAg0FltNtc [14](#setmotag0fltntc)](#setmotag0fltntc)

[5.5.8 OffsetCalculation [15](#section-3)](#section-3)

[5.5.9 CalculateMotAgTurnCntr
[15](#calculatemotagturncntr)](#calculatemotagturncntr)

[5.5.10 SPI_AngleRawProcess
[16](#spi_anglerawprocess)](#spi_anglerawprocess)

[5.5.11 CompensateMechMtrPos
[16](#compensatemechmtrpos)](#compensatemechmtrpos)

[5.6 GLOBAL Function/Macro Definitions
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

This document defines the module level design for the Sensor Offset and
Correction Component. Major part of design has been captured in the FDD
and any design rationale that has not been identified in the FDD and has
been used to implement the component has been documented in the MDD

## Scope

The following definitions are used throughout this document:

-   **<u>Shall</u>**: indicates a mandatory requirement without
    exception in compliance.

-   **<u>Should</u>**: indicates a mandatory requirement; exceptions
    allowed only with documented justification.

-   **<u>May</u>**: indicates an optional action.

# MotAg0MeasHigh-Level Description

The CDD_MotAg0Meas component is the complex driver for the motor angle 1
measurement subsystem. This function initializes the registers for CSIH3
SPI channel for communicating with the motor angle 1 measurement sensor
board. The SPI transmission is triggered periodically by DMA component.
This function receives the RAW sensor data at 62.5uS rate. The component
contains two source files, both described in this MDD: CDD_MotAg0Meas.c
contains the RTE runnables and services; CDD_MotAg0Meas_MotCtrl.c
contains the motor control runnable.

# Design details of software module

See FDD.

## Graphical representation of MotAg0Meas

## Data Flow Diagram

See FDD.

### Component level DFD

See FDD.

### Function level DFD

See FDD.

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name                         | Resolution   | Units | Value      |
|---------------------------------------|--------------|-------|------------|
| MOTAG0TURNCNTRLOLIM_CNT_F32           | Single point | Cnt   | -256.09375 |
| MOTAG0TURNCNTRHILIM_CNT_F32           | Single point | Cnt   | 255.96875  |
| MOTCTRLMOTAG0WARNREGLOLIM_CNT_U32     | 1            | Cnt   | 0          |
| MOTCTRLMOTAG0WARNREGHILIM_CNT_U32     | 1            | Cnt   | 67108863   |
| MOTCTRLMOTAG0ERRREGLOLIM_CNT_U32      | 1            | Cnt   | 0          |
| MOTCTRLMOTAG0ERRREGHILIM_CNT_U32      | 1            | Cnt   | 67108863   |
| MOTCTRLMOTAG0TURNCNTRREGLOLIM_CNT_U32 | 1            | Cnt   | 0          |
| MOTCTRLMOTAG0TURNCNTRREGHILIM_CNT_U32 | 1            | Cnt   | 67108863   |

**\* Also see FDD – CM620B_MotAg0Meas_DataDict.m file**

# Software Component Implementation

## Sub-Module Functions

The sub-module functions are grouped based on similar functionality that
needs to be executed in a given “State” of the system (refer States and
Modes). For a given module, the MDD will identify the type and number of
sub-modules required. The sub-module types are described below.

### Init: MotAg0MeasInit1

## Design Rationale

All register initialization that is allowed at the register level (see
Register/Field column of the
CM620B_MotAg0Meas_RegisterConfiguration.xlsm spreadsheet in the FDD) is
done at the register level to save execution time as compared to the
read/modify/writes that would be needed to initialize at the field
level. Field level initialization done only where required by the
spreadsheet.

## Module Outputs

See FDD: MotAg0MeasInit1 model block.

## Module Internal 

See FDD: MotAg0MeasInit1 model block for Per Instance Memory.

### Per: MotAg0MeasPer1

## Design Rationale

For run time efficiency in the motor control loop the **Compensate
MechMtrPos** block is implemented in a optimized way in the code by
letting a uint16 variable be overflown

## Store Module Inputs to Local copies

See FDD: MotAg0MeasPer1 model block

## (Processing of function)………

See FDD: MotAg0MeasPer1 model block.

## Store Local copy of outputs into Module Outputs

See FDD: MotAg0MeasPer1 model block.

### Per: MotAg0MeasPer2

## Design Rationale

None

## Store Module Inputs to Local copies

See FDD: MotAg0MeasPer2 model block

## (Processing of function)………

See FDD: MotAg0MeasPer2 model block.

## Store Local copy of outputs into Module Outputs

See FDD: MotAg0MeasPer2 model block.

### Per: MotAg0MeasPer3

## Design Rationale

None

## Store Module Inputs to Local copies

See FDD: MotAg0MeasPer3 model block

## (Processing of function)………

See FDD: MotAg0MeasPer3 model block.

## Store Local copy of outputs into Module Outputs

See FDD: MotAg0MeasPer3 model block.

## Server Runables: MotAg0CoeffTblRead

## Design Rationale

None

## Store Module Inputs to Local copies

None

## (Processing of function)………

*See* MotAg0CoeffTblRead *block in the FDD*

## Store Local copy of outputs into Module Outputs

None

## Server Runables: MotAg0CoeffTblWr

## Design Rationale

None

## Store Module Inputs to Local copies

None

## (Processing of function)………

*See* MotAg0CoeffTblWr *block in the FDD*

## Store Local copy of outputs into Module Outputs

*See* MotAg0MeasMotAg0CoeffTblWr*block in the FDD*

## Server Runables: MotAg0CfgLoPwrMod

## Design Rationale

None

## Store Module Inputs to Local copies

None

## (Processing of function)………

*See* MotAg0CfgLoPwrMod *block in the FDD*

## Store Local copy of outputs into Module Outputs

*See* MotAg0CfgLoPwrMod *block in the FDD*

## Interrupt Functions

None

##  Module Internal (Local) Functions

### ProcessErrorRegAndDieRevCtr

|                      |                                  |        |       |          |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | ProcessErrorRegAndDieRevCtr      | Type   | Min   | Max      |
| **Arguments Passed** | MotAgErrReg_Cnt_T_u32            | uint32 | 0     | 67108863 |
|                      | MotAgTurnCntrReg_Cnt_T_u32       | uint32 | 0     | 67108863 |
|                      | MotAgWarnReg_Cnt_T_u32           | uint32 | 0     | 67108863 |
| **Return Value**     | MotAg0Err_Cnt_T_u16              | uint16 | 0     | 65535    |
|                      | MotAg0Warn_Cnt_T_u16             | uint16 | 0     | 65535    |
|                      | TurnCntrParFltCnt_Cnt_T_u16      | uint16 | 0     | 65535    |
|                      | TurnCntr_Cnt_T_s16               | sint16 | -2048 | 2048     |
|                      | MotAgTurnCntrRollgCntr_Cnt_T_u08 | uint8  | 0     | 65535    |

#### Design Rationale

Implementation of "Process ErrorReg and DieRevCtr" Simulink block

### 

|     |     |     |     |     |
|-----|-----|-----|-----|-----|
|     |     |     |     |     |
|     |     |     |     |     |
|     |     |     |     |     |
|     |     |     |     |     |

#### 

### SPIvsENCA

|                      |                              |       |     |       |
|----------------------|------------------------------|-------|-----|-------|
| **Function Name**    | SPIvsENCA                    | Type  | Min | Max   |
| **Arguments Passed** | MotAgSpiMecl_MotRev_T_u0p16  | u0p16 | 0   | 65535 |
|                      | MotAgEncaMecl_MotRev_T_u0p16 | u0p16 | 0   | 65535 |
| **Return Value**     | MotAgSyncErr_Cnt_T_u08       | uint8 | 0   | 1     |

#### Design Rationale

Implementation of "SPI vs ENCA" Simulink block

### CalcCorrnTbl

|                      |              |      |     |     |
|----------------------|--------------|------|-----|-----|
| **Function Name**    | CalcCorrnTbl | Type | Min | Max |
| **Arguments Passed** | None         | N/A  | N/A | N/A |
| **Return Value**     | N/A          | N/A  | N/A | N/A |

#### Design Rationale

See “Calculate Correction Table” block in the Simulink model of the
design

### MotAgFaultProcessing

|                      |                              |          |       |       |
|----------------------|------------------------------|----------|-------|-------|
| **Function Name**    | MotAgFaultProcessing         | Type     | Min   | Max   |
| **Arguments Passed** | MotAgErr_Cnt_T_u16           | uint16   | 0     | 65535 |
|                      | MotAgWarn_Cnt_T_u16          | uint16   | 0     | 65535 |
|                      | TurnCntrParFltCnt_Cnt_T_u16  | uint16   | 0     | 65535 |
|                      | MotAgVltgFltCnt_Cnt_T_u16    | uint16   | 0     | 65535 |
|                      | MotAgParFltCnt_Cnt_T_u16     | uint16   | 0     | 65535 |
|                      | MotAgSyncErr_Cnt_T_u16       | uint8    | 0     | 1     |
|                      | MotAg3Mecl_MotRev_T_u0p16    | u0p16    | 0     | 65535 |
|                      | MotAgSpiMecl_MotRev_T_u0p16  | u0p16    | 0     | 65535 |
|                      | TurnCntr_Cnt_T_s16           | sint16   | -2048 | 2048  |
| **Return Value**     | MotAgQlfr_Cnt_T_enum         | SigQlfr1 | 0     | 2     |
|                      | MotAgTurnCntrQlfr_Cnt_T_enum | SigQlfr1 | 0     | 2     |
|                      | MotAgQepFaild_Cnt_T_logl     | boolean  | FALSE | TRUE  |

#### Design Rationale

Implementation of "MotAg Fault Processing" Simulink block

###  CalcNtcPrm

|                      |                              |        |     |       |
|----------------------|------------------------------|--------|-----|-------|
| **Function Name**    | CalcNtcPrm                   | Type   | Min | Max   |
| **Arguments Passed** | MotAgErr_Cnt_T_u16           | uint16 | 0   | 65535 |
|                      | MotAgWarn_Cnt_T_u16          | uint16 | 0   | 65535 |
|                      | TurnCntrParFltCnt_Cnt_T_u16  | uint16 | 0   | 65535 |
|                      | MotAgVltgFltCnt_Cnt_T_u16    | uint16 | 0   | 65535 |
|                      | MotAgParFltCnt_Cnt_T_u16     | uint16 | 0   | 65535 |
| **Return Value**     | MotAgNtcParm_Cnt_T_u08       | uint8  | 0   | 127   |
|                      | TurnCtrNtcParm_Cnt_T_u08     | uint8  | 0   | 255   |
|                      | TurnCtrVltgNtcParm_Cnt_T_u08 | uint8  | 0   | 1     |

#### Design Rationale

See “Determine NTC Parameters” block in the Simulink model of the design

###  [section-2]

### SetMotAg0FltNtc

|                      |                                |        |       |       |
|----------------------|--------------------------------|--------|-------|-------|
| **Function Name**    | SetMotAg0FltNtc                | Type   | Min   | Max   |
| **Arguments Passed** | MotAgNtcParm_Cnt_T_u08         | uint8  | 0     | 127   |
|                      | TurnCntrNtcParm_Cnt_T_u08      | uint8  | 0     | 255   |
|                      | TurnCntrVltgNtcParm_Cnt_T_u08  | uint8  | 0     | 1     |
|                      | MotAgQepMecl_MotRev_T_u0p16    | u0p16  | 0     | 65535 |
|                      | MotAgSPIMecl\_\_MotRev_T_u0p16 | u0p16  | 0     | 65535 |
|                      | TurnCntr_Cnt_T_s16             | sint16 | -2048 | 2048  |
| **Return Value**     | N/A                            | N/A    | N/A   | N/A   |

#### Design Rationale

See “MotAg0PtrclFlt Processing, MotAg0TurnCntrFlt Processing &
MotAg0TurnCntrVltgFlt Processing” block in the Simulink model of the
design

###   

<table>
<colgroup>
<col style="width: 18%" />
<col style="width: 41%" />
<col style="width: 13%" />
<col style="width: 12%" />
<col style="width: 13%" />
</colgroup>
<tbody>
<tr class="odd">
<td><h3 id="section-4"></h3></td>
<td><h3 id="section-5"></h3></td>
<td><h3 id="section-6"></h3></td>
<td><h3 id="section-7"></h3></td>
<td><h3 id="section-8"></h3></td>
</tr>
<tr class="even">
<td><h3 id="section-9"></h3></td>
<td><h3 id="section-10"></h3></td>
<td><h3 id="section-11"></h3></td>
<td><h3 id="section-12"></h3></td>
<td><h3 id="section-13"></h3></td>
</tr>
<tr class="odd">
<td><h3 id="section-14"></h3></td>
<td><h3 id="section-15"></h3></td>
<td><h3 id="section-16"></h3></td>
<td><h3 id="section-17"></h3></td>
<td><h3 id="section-18"></h3></td>
</tr>
<tr class="even">
<td><h3 id="section-19"></h3></td>
<td><h3 id="section-20"></h3></td>
<td><h3 id="section-21"></h3></td>
<td><h3 id="section-22"></h3></td>
<td><h3 id="section-23"></h3></td>
</tr>
</tbody>
</table>

###  [section-24]

###  [section-25]

###  [section-26]

### CalculateMotAgTurnCntr

|                      |                             |         |            |           |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | CalculateMotAgTurnCntr      | Type    | Min        | Max       |
| **Arguments Passed** | MotAgSpiMecl_MotRev_T_u0p16 | u0p16   | 0          | 65535     |
|                      | TurnCntr_Cnt_T_s16          | sint16  | -2048      | 2048      |
|                      | MotAgPolarity_Cnt_T_s08     | sint8   | -1         | 1         |
| **Return Value**     | MotAgTurnCntr_Cnt_T_f32     | float32 | -256.09375 | 255.96875 |

#### Design Rationale

Implementation of "Calculate MotAgTurnCntr" Simulink block

###  SPI_AngleRawProcess

|                      |                     |        |     |          |
|----------------------|---------------------|--------|-----|----------|
| **Function Name**    | SPI_AngleRawProcess | Type   | Min | Max      |
| **Arguments Passed** | RawAngReg_Cnt_T_u32 | uint32 | 0   | 67108863 |
| **Return Value**     | N/A                 | N/A    | N/A | N/A      |

#### Design Rationale

Implementation of "SPI_AngleRawProcess" Simulink block

### CompensateMechMtrPos

|                      |                          |       |     |       |
|----------------------|--------------------------|-------|-----|-------|
| **Function Name**    | CompensateMechMtrPos     | Type  | Min | Max   |
| **Arguments Passed** | MotAgRawMecl_Cnt_T_u0p16 | u0p16 | 0   | 65535 |
| **Return Value**     | MotAgMecl_MotRev_T_u0p16 | u0p16 | 0   | 65535 |

#### Design Rationale

Implementation of "Compensate MechMtrPos" Simulink block

##  GLOBAL Function/Macro Definitions

-   MotAg0MeasPer1

-   MotAg0CfgLoPwrMod

# Known Limitations with Design

None

# UNIT TEST CONSIDERATION

Following variables are used as rolling counters, so the overflow of
these variables is intentional.

Rte_Pim_MotAg0VltgFltCntPrev

Rte_Pim_MotAg0ParFltCntPrev

Rte_Pim_MotAg0MeclRollgCntrPrev

Rte_Pim_MotAg0TurnCntrParFltCntPrev

There is an unreachable code in the SinCos_f32() function, because the
input of this function is always positive. This is ok as the
SinCos_f32() is a library function.

For the config param MOTAG0MEAS_DIQEPIF_CNT_LOGL, please use the file
CDD_MotAg0Meas_Cfg.h in the include folder.

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

| **Ref. \#** | **Title**                                                                                                                                                                                                                                    | **Version**                     |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[<u>AUTOSAR_SWS_MemoryMapping.pdf</u>](https://www.autosar.org/fileadmin/files/standards/classic/4-0/software-architecture/implementation-integration/standard/AUTOSAR_SWS_MemoryMapping.pdf)) | v1.4.0 R4.0 Rev 3               |
| 2           | MDD Guideline EA4                                                                                                                                                                                                                            | 01.00.01                        |
| 3           | EA4 Software Naming Conventions                                                                                                                                                                                                              | 01.01.00                        |
| 4           | Software Design and Coding Standards                                                                                                                                                                                                         | 2.1                             |
| 5           | CM620B_MotAg0Meas_Design                                                                                                                                                                                                                     | See Synergy Sub Project Version |

{% endraw %}