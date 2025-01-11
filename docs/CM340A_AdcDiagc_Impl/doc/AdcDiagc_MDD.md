---
layout: default
title: AdcDiagc_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**AdcDiagc**

**Mar 13, 2017**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                                    |               |             |             |
|---------------------------|-------------------|--------------|-------------|
| **Description**                    | **Author**    | **Version** | **Date**    |
| Initial Version                    | Rijvi Ahmed   | 1.0         | 02-Feb-2016 |
| Updated per design rev. 1.1.0      | Rijvi Ahmed   | 2.0         | 23-Mar-2016 |
| Updated per design rev. 1.4.0      | Avinash James | 3.0         | 21-Jun-2016 |
| Updated per design rev. 1.6.0      | Avinash James | 4.0         | 15-Jul-2016 |
| Updated per design rev. 1.7.0      | Avinash James | 5.0         | 25-Aug-2016 |
| Updated to include error injection | Avinash James | 6.0         | 13-Mar-2017 |

**  
**

<u>Table of Contents</u>

1 Introduction 5

1.1 Purpose 5

1.2 Scope 5

2 AdcDiagc & High-Level Description 6

3 Design details of software module 7

3.1 Graphical representation of AdcDiagc 7

3.2 Data Flow Diagram 7

3.2.1 Component level DFD 7

3.2.2 Function level DFD 7

4 Constant Data Dictionary 8

4.1 Program (fixed) Constants 8

4.1.1 Embedded Constants 8

5 Software Component Implementation 9

5.1 Sub-Module Functions 9

5.1.1 Init: AdcDiagcInit1 9

5.1.1.1 Design Rationale 9

5.1.1.2 Module Outputs 9

5.1.2 Per: AdcDiagcPer1 9

5.1.2.1 Design Rationale 9

5.1.2.2 Store Module Inputs to Local copies 9

5.1.2.3 (Processing of function)……… 9

5.1.2.4 Store Local copy of outputs into Module Outputs 9

5.2 Server Runables 9

5.3 Interrupt Functions 9

5.4 Module Internal (Local) Functions 9

5.4.1 Local Function \#1 9

5.4.1.1 Design Rationale 10

5.4.1.2 Processing 10

5.4.2 Local Function \#2 10

5.4.2.1 Design Rationale 10

5.4.2.2 Processing 10

5.4.3 Local Function \#3 10

5.4.3.1 Design Rationale 11

5.4.3.2 Processing 11

5.4.4 Local Function \#4 11

5.4.4.1 Design Rationale 11

5.4.4.2 Processing 11

5.4.5 Local Function \#5 11

5.4.5.1 Design Rationale 11

5.4.5.2 Processing 11

5.4.6 Local Function \#6 11

5.4.6.1 Design Rationale 12

5.4.6.2 Processing 12

5.4.7 Local Function \#7 12

5.4.7.1 Design Rationale 12

5.4.7.2 Processing 12

5.4.8 Local Function \#8 12

5.4.8.1 Design Rationale 12

5.4.8.2 Processing 12

5.4.9 Local Function \#9 12

5.4.9.1 Design Rationale 12

5.4.9.2 Processing 12

5.5 GLOBAL Function/Macro Definitions 13

6 Known Limitations with Design 14

7 UNIT TEST CONSIDERATION 15

Appendix A Abbreviations and Acronyms 16

Appendix B Glossary 17

Appendix C References 18

# Introduction

## Purpose

MDD for AdcDiagc

## Scope

# AdcDiagc & High-Level Description

*Refer to FDD.*

# Design details of software module

## Graphical representation of AdcDiagc

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/CM340A_AdcDiagc_Impl/doc/mediax/media/image2.png"
style="width:6.24375in;height:5.25in" />

## Data Flow Diagram

None.

### Component level DFD

Refer FDD.

### Function level DFD

Refer FDD.

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name         | Resolution | Units | Value |
|-----------------------|------------|-------|-------|
| MAXADCDIAGCST_CNT_U08 | 1          | CNT   | 7U    |
| Refer to the FDD      |            |       |       |
| MASKFLTCNTR_CNT_U08   | 1          | CNT   | 127U  |

# Software Component Implementation

## Sub-Module Functions

The sub-module functions are grouped based on similar functionality that
needs to be executed in a given “State” of the system (refer States and
Modes). For a given module, the MDD will identify the type and number of
sub-modules required. The sub-module types are described below.

### Init: 

## Design Rationale

*None*

## Module Outputs

*None*

###  [section]

### Per: 

## Design Rationale

*Refer FDD.*

## Store Module Inputs to Local copies

*Refer FDD*

## (Processing of function)………

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*Refer FDD.*

## Server Runables 

## Interrupt Functions

*None*

## Module Internal (Local) Functions

## Local Function \#1

|                      |                         |         |     |     |
|----------------------|-------------------------|---------|-----|-----|
| **Function Name**    | St2Proc                 | Type    | Min | Max |
| **Arguments Passed** | AdcSelfDiag0_Volt_T_f32 | float32 | 0.0 | 5.0 |
|                      | AdcSelfDiag2_Volt_T_f32 | float32 | 0.0 | 5.0 |
|                      | AdcSelfDiag4_Volt_T_f32 | float32 | 0.0 | 5.0 |
|                      | AdcDiagcSt_Uls_T_u08    | Uint8   | 0   | 3   |
|                      | \*RollgCntr_Cnt_T_u08   | \*uint8 | 0   | 255 |
| **Return Value**     | AdcNtcStInfo_Uls_T_u08  | Uint8   | 0   | 255 |

## Design Rationale

## Processing

See “State 2” block in the Simulink model of the design.

## Local Function \#2

|                      |                         |         |     |     |
|----------------------|-------------------------|---------|-----|-----|
| **Function Name**    | St4Proc                 | Type    | Min | Max |
| **Arguments Passed** | AdcSelfDiag0_Volt_T_f32 | float32 | 0.0 | 5.0 |
|                      | AdcSelfDiag2_Volt_T_f32 | float32 | 0.0 | 5.0 |
|                      | AdcSelfDiag4_Volt_T_f32 | float32 | 0.0 | 5.0 |
|                      | AdcDiagcSt_Uls_T_u08    | Uint8   | 0   | 3   |
|                      | \*RollgCntr_Cnt_T_u08   | \*uint8 | 0   | 255 |
| **Return Value**     | AdcNtcStInfo_Uls_T_u08  | Uint8   | 0   | 255 |

## Design Rationale

## Processing

See “State 4” block in the Simulink model of the design.

## Local Function \#3

|                      |                         |         |     |     |
|----------------------|-------------------------|---------|-----|-----|
| **Function Name**    | St6Proc                 | Type    | Min | Max |
| **Arguments Passed** | AdcSelfDiag0_Volt_T_f32 | float32 | 0.0 | 5.0 |
|                      | AdcSelfDiag2_Volt_T_f32 | float32 | 0.0 | 5.0 |
|                      | AdcSelfDiag4_Volt_T_f32 | float32 | 0.0 | 5.0 |
|                      | AdcDiagcSt_Uls_T_u08    | Uint8   | 0   | 3   |
|                      | \*RollgCntr_Cnt_T_u08   | \*uint8 | 0   | 255 |
| **Return Value**     | AdcNtcStInfo_Uls_T_u08  | Uint8   | 0   | 255 |

## Design Rationale

## Processing

See “State 6” block in the Simulink model of the design.

## Local Function \#4

|                      |                         |         |     |      |
|----------------------|-------------------------|---------|-----|------|
| **Function Name**    | St0Proc                 | Type    | Min | Max  |
| **Arguments Passed** | AdcSelfDiag0_Volt_T_f32 | float32 | 0.0 | 5.0  |
|                      | AdcSelfDiag2_Volt_T_f32 | float32 | 0.0 | 5.0  |
|                      | AdcSelfDiag4_Volt_T_f32 | float32 | 0.0 | 5.0  |
|                      | \*RollgCntr_Cnt_T_u08   | \*uint8 | 00  | 3255 |
|                      |                         | \*uint8 | 0   | 255  |
| **Return Value**     | AdcNtcStInfo_Uls_T_u08  | Uint8   | 0   | 255  |

## Design Rationale

## Processing

See “State 0” block in the Simulink model of the design.

## Local Function \#5

|                      |                      |       |     |     |
|----------------------|----------------------|-------|-----|-----|
| **Function Name**    | Adc0StBasdProc       | Type  | Min | Max |
| **Arguments Passed** | Adc0ParFlt_Cnt_T_u08 | uint8 | 0   | 255 |
| **Return Value**     | None                 | N/A   | N/A | N/A |

## Design Rationale

## Processing

See “Adc0 State Based Processing” block in the Simulink model of the
design.

## Local Function \#6

|                      |                      |       |     |     |
|----------------------|----------------------|-------|-----|-----|
| **Function Name**    | Adc1StBasdProc       | Type  | Min | Max |
| **Arguments Passed** | Adc1ParFlt_Cnt_T_u08 | uint8 | 0   | 255 |
| **Return Value**     | None                 | N/A   | N/A | N/A |

## Design Rationale

## Processing

See “Adc1 State Based Processing” block in the Simulink model of the
design.

## Local Function \#7

|                      |                 |      |     |     |
|----------------------|-----------------|------|-----|-----|
| **Function Name**    | AdcDiagcPtrProc | Type | Min | Max |
| **Arguments Passed** | None            | N/A  | N/A | N/A |
| **Return Value**     | None            | N/A  | N/A | N/A |

## Design Rationale

## Processing

See “Adc Daigc Pointer” block in the Simulink model of the design.

## Local Function \#8

|                      |                                   |         |     |     |
|----------------------|-----------------------------------|---------|-----|-----|
| **Function Name**    | ScanGroupAccrcyChk                | Type    | Min | Max |
| **Arguments Passed** | AdcScanGroupInpRefVltg_Volt_T_f32 | float32 | 0.0 | 5.0 |
|                      | AdcScanGroupRefVltg_Volt_T_f32    | float32 | 0.0 | 5.0 |
|                      | AdcScanGroupInpRefPrm_Cnt_T_u08   | Uint8   | 0   | 255 |
| **Return Value**     | ScanGroupAccrcyChkRefPrm_Cnt_u08  | Uint8   | 0   | 255 |

## Design Rationale

## Processing

See “Scan Group Accuracy Check” block in the Simulink model of the
design.

## Local Function \#9

|                      |                        |       |     |     |
|----------------------|------------------------|-------|-----|-----|
| **Function Name**    | SetAdcParFlt           | Type  | Min | Max |
| **Arguments Passed** | \*Adc0ParFlt_Cnt_T_u08 | Uint8 | 0   | 255 |
|                      | \*Adc1ParFlt_Cnt_T_u08 | Uint8 | 0   | 255 |
|                      |                        |       |     |     |
| **Return Value**     |                        |       |     |     |

## Design Rationale

## Processing

See “Adc Parity Fault” block in the Simulink model of the design.

## GLOBAL Function/Macro Definitions

Note: The server runnable of this component are non-rte. So they are
actually global functions which should belong to this section. But as
they are already described under Server Runnable section so it’s omitted
here.

# Known Limitations with Design

None.

# UNIT TEST CONSIDERATION

The overflow for the following PIMs are intentional as they are used as
rolling counter.

Rte_Pim_Adc0FltCntSt0

Rte_Pim_Adc0FltCntSt2

Rte_Pim_Adc0FltCntSt4

Rte_Pim_Adc0FltCntSt6

Rte_Pim_Adc1FltCntSt0

Rte_Pim_Adc1FltCntSt2

Rte_Pim_Adc1FltCntSt4

Rte_Pim_Adc1FltCntSt6

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

| **Ref. \#** | **Title**                                                                                                                                                             | **Version**                     |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                    | v1.3.0 R4.0 Rev 2               |
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.01                    |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 1.0                             |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.1                             |
| 5           | FDD - CM340A_AdcDiagc_Design                                                                                                                                          | See Synergy sub project version |

{% endraw %}