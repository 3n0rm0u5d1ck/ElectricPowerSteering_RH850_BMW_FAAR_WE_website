---
layout: default
title: MotAg1Meas_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**Motor Angle 1 Measurement**

**May 04, 2018**

**Prepared By:**

**Avinash James**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**  
<u>Change History</u>**

|                                                                                                                                                     |                  |             |             |
|------------------------|---------------------|--------------|--------------|
| **Description**                                                                                                                                     | **Author**       | **Version** | **Date**    |
| Initial Version                                                                                                                                     | Avinash James    | 1.0         | 07-Jun-2016 |
| Removed local function CalcTurnCntr                                                                                                                 | Avinash James    | 2.0         | 13-Jun-2016 |
| Added local function ProcTurnCntrReg. Added constants required for bitshifting and signal limiting. Added limiting block for output MotAg1TurnCntr. | Brendon Binder   | 3.0         | 25-Aug-2017 |
| Update to FDD 4.1.0 added MotAg1WarnReg function                                                                                                    | Mateusz Bartocha | 4.0         | 23-Oct-17   |
| Fix – Missed MotAg1TurnCntrRollgCntr output                                                                                                         | Mateusz Bartocha | 5           | 21-Nov-17   |
| Updated Diagram & Unit Test Considerations                                                                                                          | Matthew Leser    | 6.0         | 14-Dec-2017 |
| Updated as per Design version 5.0.0                                                                                                                 | Krzysztof Byrski | 7.0         | 25-Apr-2018 |
| Added ports for IO access                                                                                                                           | Avinash James    | 8.0         | 27-Apr-2018 |
| Added updates for sensor offset learning                                                                                                            | Avinash James    | 9.0         | 04-May-2018 |

**  
**

<u>Table of Contents</u>

[1 Introduction [5](#introduction)](#introduction)

[1.1 Purpose [5](#purpose)](#purpose)

[1.2 Scope [5](#scope)](#scope)

[2 MotAg1Meas High-Level Description
[6](#motag1meashigh-level-description)](#motag1meashigh-level-description)

[3 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of MotAg1Meas
[7](#graphical-representation-of-motag1meas)](#graphical-representation-of-motag1meas)

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

[5.1.1 Init: MotAg1MeasInit1
[9](#init-motag1measinit1)](#init-motag1measinit1)

[5.1.1.1 Design Rationale [9](#design-rationale)](#design-rationale)

[5.1.1.2 Module Outputs [9](#module-outputs)](#module-outputs)

[5.1.1.3 Module Internal [9](#module-internal)](#module-internal)

[5.1.2 Per: MotAg1MeasPer1
[9](#per-motag1measper1)](#per-motag1measper1)

[5.1.2.1 Design Rationale [9](#design-rationale-1)](#design-rationale-1)

[5.1.2.2 Store Module Inputs to Local copies
[9](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[5.1.2.3 (Processing of function)………
[9](#processing-of-function)](#processing-of-function)

[5.1.2.4 Store Local copy of outputs into Module Outputs
[9](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[5.1.3 Per: MotAg1MeasPer2
[9](#per-motag1measper2)](#per-motag1measper2)

[5.1.3.1 Design Rationale [9](#design-rationale-2)](#design-rationale-2)

[5.1.3.2 Store Module Inputs to Local copies
[10](#store-module-inputs-to-local-copies-1)](#store-module-inputs-to-local-copies-1)

[5.1.3.3 (Processing of function)………
[10](#processing-of-function-1)](#processing-of-function-1)

[5.1.3.4 Store Local copy of outputs into Module Outputs
[10](#store-local-copy-of-outputs-into-module-outputs-1)](#store-local-copy-of-outputs-into-module-outputs-1)

[5.2 Server Runnables: MotAg1CoeffTblRead
[10](#server-runnables-motag1coefftblread)](#server-runnables-motag1coefftblread)

[5.2.1.1 Design Rationale
[10](#design-rationale-3)](#design-rationale-3)

[5.2.1.2 Store Module Inputs to Local copies
[10](#store-module-inputs-to-local-copies-2)](#store-module-inputs-to-local-copies-2)

[5.2.1.3 (Processing of function)………
[10](#processing-of-function-2)](#processing-of-function-2)

[5.2.1.4 Store Local copy of outputs into Module Outputs
[10](#store-local-copy-of-outputs-into-module-outputs-2)](#store-local-copy-of-outputs-into-module-outputs-2)

[5.3 Server Runnables: MotAg1CoeffTblWr
[10](#server-runnables-motag1coefftblwr)](#server-runnables-motag1coefftblwr)

[5.3.1.1 Design Rationale
[10](#design-rationale-4)](#design-rationale-4)

[5.3.1.2 Store Module Inputs to Local copies
[10](#store-module-inputs-to-local-copies-3)](#store-module-inputs-to-local-copies-3)

[5.3.1.3 (Processing of function)………
[10](#processing-of-function-3)](#processing-of-function-3)

[5.3.1.4 Store Local copy of outputs into Module Outputs
[10](#store-local-copy-of-outputs-into-module-outputs-3)](#store-local-copy-of-outputs-into-module-outputs-3)

[5.4 Server Runnables: MotAg1CfgLoPwrMod
[10](#server-runnables-motag1cfglopwrmod)](#server-runnables-motag1cfglopwrmod)

[5.4.1.1 Design Rationale
[10](#design-rationale-5)](#design-rationale-5)

[5.4.1.2 Store Module Inputs to Local copies
[10](#store-module-inputs-to-local-copies-4)](#store-module-inputs-to-local-copies-4)

[5.4.1.3 (Processing of function)………
[11](#processing-of-function-4)](#processing-of-function-4)

[5.4.1.4 Store Local copy of outputs into Module Outputs
[11](#store-local-copy-of-outputs-into-module-outputs-4)](#store-local-copy-of-outputs-into-module-outputs-4)

[5.5 Interrupt Functions
[11](#interrupt-functions)](#interrupt-functions)

[5.6 Module Internal (Local) Functions
[11](#module-internal-local-functions)](#module-internal-local-functions)

[5.6.1 ProcessErrorRegAndDieRevCtr
[11](#processerrorreganddierevctr)](#processerrorreganddierevctr)

[5.6.2 SPI_AnglePolarityAdjust [11](#section)](#section)

[5.6.3 SPIvsENCA [12](#spivsenca)](#spivsenca)

[5.6.4 CalcCorrnTbl [12](#calccorrntbl)](#calccorrntbl)

[5.6.5 MotAgFaultProcessing
[12](#motagfaultprocessing)](#motagfaultprocessing)

[5.6.6 CalcNtcPrm [13](#calcntcprm)](#calcntcprm)

[5.6.7 SetMotAg1FltNtc [13](#setmotag1fltntc)](#setmotag1fltntc)

[5.6.8 OffsetCalculation [14](#section-3)](#section-3)

[5.6.9 CalculateMotAgTurnCntr
[14](#calculatemotagturncntr)](#calculatemotagturncntr)

[5.6.10 SPI_AngleRawProcess
[15](#spi_anglerawprocess)](#spi_anglerawprocess)

[5.6.11 CompensateMechMtrPos
[15](#compensatemechmtrpos)](#compensatemechmtrpos)

[5.7 GLOBAL Function/Macro Definitions
[16](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[6 Known Limitations with Design
[17](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[18](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[19](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [20](#glossary)](#glossary)

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

# MotAg1MeasHigh-Level Description

The CDD_MotAg1Meas component is the complex driver for the motor angle 1
measurement subsystem. This function initializes the registers for CSIH3
SPI channel for communicating with the motor angle 1 measurement sensor
board. The SPI transmission is triggered periodically by DMA component.
This function receives the RAW sensor data at 62.5uS rate. The component
contains two source files, both described in this MDD: CDD_MotAg1Meas.c
contains the RTE runnables and services; CDD_MotAg1Meas_MotCtrl.c
contains the motor control runnable.

.

# Design details of software module

See FDD.

## Graphical representation of MotAg1Meas

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
| MOTAG1TURNCNTRLOLIM_CNT_F32           | Single point | Cnt   | -256.09375 |
| MOTAG1TURNCNTRHILIM_CNT_F32           | Single point | Cnt   | 255.96875  |
| MOTCTRLMOTAG1WARNREGLOLIM_CNT_U32     | 1            | Cnt   | 0          |
| MOTCTRLMOTAG1WARNREGHILIM_CNT_U32     | 1            | Cnt   | 67108863   |
| MOTCTRLMOTAG1ERRREGLOLIM_CNT_U32      | 1            | Cnt   | 0          |
| MOTCTRLMOTAG1ERRREGHILIM_CNT_U32      | 1            | Cnt   | 67108863   |
| MOTCTRLMOTAG1TURNCNTRREGLOLIM_CNT_U32 | 1            | Cnt   | 0          |
| MOTCTRLMOTAG1TURNCNTRREGHILIM_CNT_U32 | 1            | Cnt   | 67108863   |

**\* Also see see FDD – CM640B_MotAg1Meas_DataDict.m file**

# Software Component Implementation

## Sub-Module Functions

The sub-module functions are grouped based on similar functionality that
needs to be executed in a given “State” of the system (refer States and
Modes). For a given module, the MDD will identify the type and number of
sub-modules required. The sub-module types are described below.

### Init: MotAg1MeasInit1

## Design Rationale

All register initialization that is allowed at the register level (see
Register/Field column of the
CM640A_MotAg1Meas_RegisterConfiguration.xlsm spreadsheet in the FDD) is
done at the register level to save execution time as compared to the
read/modify/writes that would be needed to initialize at the field
level. Field level initialization done only where required by the
spreadsheet.

## Module Outputs

See FDD: MotAg1MeasInit1 model block.

## Module Internal 

See FDD: MotAg1MeasInit1 model block for Per Instance Memory.

### Per: MotAg1MeasPer1

## Design Rationale

For run time efficiency in the motor control loop the **Compensate
MechMtrPos** block is implemented in a optimized way in the code by
letting a uint16 variable be overflown

## Store Module Inputs to Local copies

See FDD: MotAg1MeasPer1 model block

## (Processing of function)………

See FDD: MotAg1MeasPer1 model block.

## Store Local copy of outputs into Module Outputs

See FDD: MotAg1MeasPer1 model block.

### Per: MotAg1MeasPer2

## Design Rationale

Details of the implementation of block “Process MotAg1RawErr” differ
from the model in order to meet design and coding standards.

## Store Module Inputs to Local copies

See FDD: MotAg1MeasPer2 model block

## (Processing of function)………

See FDD: MotAg1MeasPer2 model block.

## Store Local copy of outputs into Module Outputs

See FDD: MotAg1MeasPer2 model block.

## Server Runnables: MotAg1CoeffTblRead

## Design Rationale

None

## Store Module Inputs to Local copies

None

## (Processing of function)………

*See* MotAg1CoeffTblRead *block in the FDD*

## Store Local copy of outputs into Module Outputs

None

## Server Runnables: MotAg1CoeffTblWr

## Design Rationale

None

## Store Module Inputs to Local copies

None

## (Processing of function)………

*See* MotAg1CoeffTblWr *block in the FDD*

## Store Local copy of outputs into Module Outputs

*See* MotAg1MeasMotAg1CoeffTblWr*block in the FDD*

## Server Runnables: MotAg1CfgLoPwrMod

## Design Rationale

None

## Store Module Inputs to Local copies

None

## (Processing of function)………

*See* *MotAg1CfgLoPwrMod* *block in the FDD*

## Store Local copy of outputs into Module Outputs

*See MotAg1CfgLoPwrMo*d *block in the FDD*

## Interrupt Functions

None

## Module Internal (Local) Functions

### ProcessErrorRegAndDieRevCtr

|                      |                                  |        |       |          |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | ProcessErrorRegAndDieRevCtr      | Type   | Min   | Max      |
| **Arguments Passed** | MotAgErrReg_Cnt_T_u32            | uint32 | 0     | 67108863 |
|                      | MotAgTurnCntrReg_Cnt_T_u32       | uint32 | 0     | 67108863 |
|                      | MotAgWarnReg_Cnt_T_u32           | uint32 | 0     | 67108863 |
| **Return Value**     | MotAg1Err_Cnt_T_u16              | uint16 | 0     | 65535    |
|                      | MotAg1Warn_Cnt_T_u16             | uint16 | 0     | 65535    |
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
|                      | MotAg4Mecl_MotRev_T_u0p16    | u0p16    | 0     | 65535 |
|                      | MotAgSpiMecl_MotRev_T_u0p16  | u0p16    | 0     | 65535 |
|                      | TurnCntr_Cnt_T_s16           | sint16   | -2048 | 2048  |
| **Return Value**     | MotAgQlfr_Cnt_T_enum         | SigQlfr1 | 0     | 2     |
|                      | MotAgTurnCntrQlfr_Cnt_T_enum | SigQlfr1 | 0     | 2     |
|                      | MotAgQepFaild_Cnt_T_logl     | boolean  | FALSE | TRUE  |

#### Design Rationale

Implementation of "MotAg Fault Processing" Simulink block

### CalcNtcPrm

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

### SetMotAg1FltNtc

|                      |                                |        |       |       |
|----------------------|--------------------------------|--------|-------|-------|
| **Function Name**    | SetMotAg1FltNtc                | Type   | Min   | Max   |
| **Arguments Passed** | MotAgNtcParm_Cnt_T_u08         | uint8  | 0     | 127   |
|                      | TurnCntrNtcParm_Cnt_T_u08      | uint8  | 0     | 255   |
|                      | TurnCntrVltgNtcParm_Cnt_T_u08  | uint8  | 0     | 1     |
|                      | MotAgQepMecl_MotRev_T_u0p16    | u0p16  | 0     | 65535 |
|                      | MotAgSPIMecl\_\_MotRev_T_u0p16 | u0p16  | 0     | 65535 |
|                      | TurnCntr_Cnt_T_s16             | sint16 | -2048 | 2048  |
| **Return Value**     | N/A                            | N/A    | N/A   | N/A   |

#### Design Rationale

See “MotAg1PtrclFlt Processing, MotAg1TurnCntrFlt Processing &
MotAg1TurnCntrVltgFlt Processing” block in the Simulink model of the
design

###   

<table>
<colgroup>
<col style="width: 18%" />
<col style="width: 42%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
</colgroup>
<tbody>
<tr class="odd">
<td><h3 id="section-4" class="unnumbered"></h3></td>
<td><h3 id="section-5" class="unnumbered"></h3></td>
<td><h3 id="section-6" class="unnumbered"></h3></td>
<td><h3 id="section-7" class="unnumbered"></h3></td>
<td><h3 id="section-8" class="unnumbered"></h3></td>
</tr>
<tr class="even">
<td><h3 id="section-9" class="unnumbered"></h3></td>
<td><h3 id="section-10" class="unnumbered"></h3></td>
<td><h3 id="section-11" class="unnumbered"></h3></td>
<td><h3 id="section-12" class="unnumbered"></h3></td>
<td><h3 id="section-13" class="unnumbered"></h3></td>
</tr>
<tr class="odd">
<td><h3 id="section-14" class="unnumbered"></h3></td>
<td><h3 id="section-15" class="unnumbered"></h3></td>
<td><h3 id="section-16" class="unnumbered"></h3></td>
<td><h3 id="section-17" class="unnumbered"></h3></td>
<td><h3 id="section-18" class="unnumbered"></h3></td>
</tr>
<tr class="even">
<td><h3 id="section-19" class="unnumbered"></h3></td>
<td><h3 id="section-20" class="unnumbered"></h3></td>
<td><h3 id="section-21" class="unnumbered"></h3></td>
<td><h3 id="section-22" class="unnumbered"></h3></td>
<td><h3 id="section-23" class="unnumbered"></h3></td>
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

None

# Known Limitations with Design

Analysis was done to ensure the datatype sm5p12 is sufficient to hold
worst case values for the MotAg1CorrlnTbl.  This analysis will be added
to the FDD.  See CR EA4#14937.  In addition, the correlation table
values are verified in manufacturing after writing the coefficient table
to NVM.

# UNIT TEST CONSIDERATION

Following variables are used as rolling counters, so the overflow of
these variables is intentional.

Rte_Pim_MotAg1VltgFltCntPrev

Rte_Pim_MotAg1ParFltCntPrev

Rte_Pim_MotAg1MeclRollgCntrPrev

Rte_Pim_MotAg1TurnCntrParFltCntPrev

There is code in the SinCos_f32() function which will not be covered in
this component, because the input to this function is always positive.
This is ok as the SinCos_f32() is a library function.

For the config param MOTAG1MEAS_DIQEPIF_CNT_LOGL please use the file
CDD_MotAg1Meas_Cfg.h in the include folder.

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

References

| **Ref. \#** | **Title**                                                                    | **Version**                    |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:AUTOSAR_SWS_MemoryMapping.pdf) | v1.3.0 R4.0 Rev 2              |
| 2           | MDD Guideline                                                                | EA4 01.00.00                   |
| 3           | EA4 Software Naming Conventions                                              | 01.01.00                       |
| 4           | Software Design and Coding Standards.doc                                     | 2.1                            |
| 5           | FDD – CM640B Motor Angle 1 Measure                                           | See Synergy subproject version |

{% endraw %}