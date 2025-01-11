---
layout: default
title: HwTq4Meas_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**HwTq4Meas**

**Oct 30, 2017**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**TATA ELXSI,**

**TRIVANDRUM, INDIA**

**  
<u>Change History</u>**

|                                    |               |             |             |
|------------------------|---------------------|--------------|--------------|
| **Description**                    | **Author**    | **Version** | **Date**    |
| Initial Version                    | Krishna Anne  | 1.0         | 10-Jun-2016 |
| Updated to design revision 1.7.0   | Avinash James | 2.0         | 30-Nov-2016 |
| Updated as per FDD revision 1.10.0 | TATA          | 3.0         | 30-Oct-2017 |

**  
**

<u>Table of Contents</u>

1 Introduction 6

1.1 Purpose 6

2 HwTq4Meas & High-Level Description 7

3 Design details of software module 8

3.1 Graphical representation of HwTq4Meas 8

3.2 Data Flow Diagram 8

3.2.1 Component level DFD 8

3.2.2 Function level DFD 8

4 Constant Data Dictionary 9

4.1 Program (fixed) Constants 9

4.1.1 Embedded Constants 9

5 Software Component Implementation 10

5.1.1 Init: HwTq4Meas_Init1 10

5.1.1.1 Design Rationale 10

5.1.1.2 Module Outputs 10

5.1.2 Per: HwTq4Meas_Per1 10

5.1.2.1 Design Rationale 10

5.1.3 Per: HwTq4Meas_Per2 10

5.1.3.1 Design Rationale 10

5.1.4 Per: HwTq4Meas_Per3 10

5.1.4.1 Design Rationale 10

5.1.5 Per: HwTq4Meas_Per4 10

5.1.5.1 Design Rationale 10

5.2 Server Runables 10

5.2.1 HwTq4AutTrim_Oper 10

5.2.1.1 Design Rationale 10

5.2.2 HwTq4ClrSnsrSca_Oper 10

5.2.2.1 Design Rationale 10

5.2.3 HwTq4ClrTrim_Oper 11

5.2.3.1 Design Rationale 11

5.2.4 HwTq4ReadSnsrSca_Oper 11

5.2.4.1 Design Rationale 11

5.2.5 HwTq4ReadTrim_Oper 11

5.2.5.1 Design Rationale 11

5.2.6 HwTq4TrimPrfmdSts_Oper 11

5.2.6.1 Design Rationale 11

5.2.7 HwTq4WrSnsrSca_Oper 11

5.2.7.1 Design Rationale 11

5.2.8 HwTq4WrTrim_Oper 11

5.2.8.1 Design Rationale 11

5.2.9 HwTq4SnsrScaPrfmdSts_Oper 11

5.2.9.1 Design Rationale 11

5.3 Module Internal (Local) Functions 11

5.3.1 Local Function \#1 11

5.3.1.1 Design Rationale 12

5.3.1.2 Processing 12

6 Known Limitations with Design 13

7 UNIT TEST CONSIDERATION 14

Appendix A Abbreviations and Acronyms 15

Appendix B Glossary 16

Appendix C References 17

# Introduction

## Purpose

MDD for HwTq4Meas.

# HwTq4Meas & High-Level Description

# Design details of software module

Please refer to the FDD.

## Graphical representation of HwTq4Meas

## Data Flow Diagram<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/ES220A_HwTq4Meas_Impl/doc/mediax/media/image2.png"
style="width:4.20833in;height:5.26042in" />

### Component level DFD

### Function level DFD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name           | Resolution | Units | Value |
|-------------------------|------------|-------|-------|
| Please refer to the FDD |            |       |       |

# Software Component Implementation

## Init: HwTq4Meas_Init1

## Design Rationale

None

## Module Outputs

None

## Per: HwTq4Meas_Per1

## Design Rationale

Rte_Pim_HwTq4RawFastAdcIdxCntr is used in this periodic as a counter
that increments from 0 to 7 and is used to write to an output buffer
MotCtrlHwTq4RawFastAdcBuf accessed by Motor Control Manager. Whereas the
FDD describes this counter as 1 based indexing that increments from 1
till 8. Effective they are same in terms of functionality.

## Per: HwTq4Meas_Per2

## Design Rationale

None

## Per: HwTq4Meas_Per3

## Design Rationale

None

## Per: HwTq4Meas_Per4

## Design Rationale

None

## Server Runables 

## HwTq4AutTrim_Oper

## Design Rationale

None

## HwTq4ClrSnsrSca_Oper

## Design Rationale

None

## HwTq4ClrTrim_Oper

## Design Rationale

None

## HwTq4ReadSnsrSca_Oper

## Design Rationale

None

## HwTq4ReadTrim_Oper

## Design Rationale

None

## HwTq4TrimPrfmdSts_Oper

## Design Rationale

None

## HwTq4WrSnsrSca_Oper

## Design Rationale

None

## HwTq4WrTrim_Oper

## Design Rationale

None

## HwTq4SnsrScaPrfmdSts_Oper

## Design Rationale

None

## Module Internal (Local) Functions

## Local Function \#1

|                      |                         |          |                    |                    |
|-------------|--------------------------|---------|-------------|------------|
| **Function Name**    | HwTqQlfr                | Type     | Min                | Max                |
| **Arguments Passed** | NtcSts_Cnt_T_enum       | SigQlfr1 | SIGQLFR_NORES (0U) | SIGQLFR_FAILD (2U) |
|                      | ParamByte_Cnt_T_u08     | uint8    | 0                  | 4                  |
|                      | \* HwTq4Qlfr_Cnt_T_enum | SigQlfr1 | SIGQLFR_NORES (0U) | SIGQLFR_FAILD (2U) |
| **Return Value**     | NA                      | NA       | NA                 | NA                 |

## Design Rationale

## Processing

Please refer to the below path in the FDD model.

ES220A_HwTq4Meas/HwTq4Meas/HwTq4MeasPer2/HwTqQlfr

# Known Limitations with Design

None.

# UNIT TEST CONSIDERATION

Rte_Pim_HwTq4PrevRollgCntr is being used as a rolling counter. Hence the
overflow is intentional.

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

| **Ref. \#** | **Title**                                                                                                                                                             | **Version**                    |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                    | v1.3.0 R4.0 Rev 2              |
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.00                   |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 1.0                            |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.1                            |
| 5           | ES220A_HwTq4Meas_Design                                                                                                                                               | See Synergy subproject version |

{% endraw %}