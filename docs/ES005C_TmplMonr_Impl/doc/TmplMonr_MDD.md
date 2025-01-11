---
layout: default
title: TmplMonr_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**Temporal Monitor Function**

**Mar 24, 2017**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**<u>Saginaw, MI, USAChange</u>** History

|                                           |              |             |             |
|-------------------------------------|----------------|---------|-----------|
| **Description**                           | **Author**   | **Version** | **Date**    |
| Initial Version                           | Krishna Anne | 1.0         | 24-Mar-2017 |
| Removed limitations from previous version | Krishna Anne | 2.0         | 27-Mar-2017 |

<u>Table of Contents</u>

[1 Introduction 6](#introduction)

[1.1 Purpose 6](#purpose)

[2 TmplMonr & High-Level Description
7](#tmplmonr-high-level-description)

[3 Design details of software module
8](#design-details-of-software-module)

[3.1 Graphical representation of TmplMonr
8](#graphical-representation-of-tmplmonr)

[3.2 Data Flow Diagram 8](#data-flow-diagram)

[3.2.1 Component level DFD 8](#component-level-dfd)

[3.2.2 Function level DFD 8](#function-level-dfd)

[4 Constant Data Dictionary 9](#constant-data-dictionary)

[4.1 Program (fixed) Constants 9](#program-fixed-constants)

[4.1.1 Embedded Constants 9](#embedded-constants)

[5 Software Component Implementation
10](#software-component-implementation)

[5.1 Sub-Module Functions 10](#sub-module-functions)

[5.1.1 Init: TmplMonrInit1 10](#init-tmplmonrinit1)

[5.1.1.1 Design Rationale 10](#design-rationale)

[5.1.1.2 Module Outputs 10](#module-outputs)

[5.1.2 Per: TmplMonrPer1 10](#per-tmplmonrper1)

[5.1.2.1 Design Rationale 10](#design-rationale-1)

[5.1.2.2 Store Module Inputs to Local copies
10](#store-module-inputs-to-local-copies)

[5.1.2.3 (Processing of function)……… 10](#processing-of-function)

[5.1.2.4 Store Local copy of outputs into Module Outputs
10](#store-local-copy-of-outputs-into-module-outputs)

[5.1.3 Per: TmplMonrPer2 10](#per-tmplmonrper2)

[5.1.3.1 Design Rationale 10](#design-rationale-2)

[5.1.3.2 Store Module Inputs to Local copies
10](#store-module-inputs-to-local-copies-1)

[5.1.3.3 (Processing of function)……… 10](#processing-of-function-1)

[5.1.3.4 Store Local copy of outputs into Module Outputs
11](#store-local-copy-of-outputs-into-module-outputs-1)

[5.1.4 Per: TmplMonrPer3 11](#per-tmplmonrper3)

[5.1.4.1 Design Rationale 11](#design-rationale-3)

[5.1.4.2 Store Module Inputs to Local copies
11](#store-module-inputs-to-local-copies-2)

[5.1.4.3 (Processing of function)……… 11](#processing-of-function-2)

[5.1.4.4 Store Local copy of outputs into Module Outputs
11](#store-local-copy-of-outputs-into-module-outputs-2)

[5.2 Server Runables 11](#server-runables)

[5.3 Interrupt Functions 11](#interrupt-functions)

[5.4 Module Internal (Local) Functions
11](#module-internal-local-functions)

[5.4.1 Local Function \#1 11](#local-function-1)

[5.4.1.1 Design Rationale 11](#design-rationale-4)

[5.4.1.2 Processing 11](#processing)

[5.4.2 Local Function \#2 12](#local-function-2)

[5.4.2.1 Design Rationale 12](#design-rationale-5)

[5.4.2.2 Processing 12](#processing-1)

[5.4.3 Local Function \#3 12](#local-function-3)

[5.4.3.1 Design Rationale 12](#design-rationale-6)

[5.4.3.2 Processing 12](#processing-2)

[5.4.4 Local Function \#4 12](#local-function-4)

[5.4.4.1 Design Rationale 12](#design-rationale-7)

[5.4.4.2 Processing 12](#processing-3)

[5.4.5 Local Function \#5 12](#local-function-5)

[5.4.5.1 Design Rationale 13](#design-rationale-8)

[5.4.5.2 Processing 13](#processing-4)

[5.4.6 Local Function \#6 13](#local-function-6)

[5.4.6.1 Design Rationale 13](#design-rationale-9)

[5.4.6.2 Processing 13](#processing-5)

[5.4.7 Local Function \#7 13](#local-function-7)

[5.4.7.1 Design Rationale 13](#design-rationale-10)

[5.4.7.2 Processing 13](#processing-6)

[5.4.8 Local Function \#8 13](#local-function-8)

[5.4.8.1 Design Rationale 14](#design-rationale-11)

[5.4.8.2 Processing 14](#processing-7)

[5.4.9 Local Function \#9 14](#local-function-9)

[5.4.9.1 Design Rationale 14](#design-rationale-12)

[5.4.9.2 Processing 14](#processing-8)

[5.4.10 Local Function \#10 14](#local-function-10)

[5.4.10.1 Design Rationale 14](#design-rationale-13)

[5.4.10.2 Processing 14](#processing-9)

[5.5 GLOBAL Function/Macro Definitions
15](#global-functionmacro-definitions)

[6 Known Limitations with Design 16](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION 17](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms 18](#abbreviations-and-acronyms)

[Appendix B Glossary 19](#glossary)

[Appendix C References 20](#references)

# Introduction

## Purpose

Module design document for Temporal Monitor Function.

# TmplMonr & High-Level Description

*Refer to FDD*

# Design details of software module

## Graphical representation of TmplMonr

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/ES005C_TmplMonr_Impl/doc/mediax/media/image1.png"
style="width:4.90694in;height:3.20764in" />

## Data Flow Diagram

### Component level DFD

N/A

### Function level DFD

N/A

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

|                                            |            |       |       |
|--------------------------------------------|------------|-------|-------|
| Constant Name                              | Resolution | Units | Value |
| Refer to the Data Dictionary of the design |            |       |       |

# Software Component Implementation

## Sub-Module Functions

The sub-module functions are grouped based on similar functionality that
needs to be executed in a given “State” of the system (refer States and
Modes). For a given module, the MDD will identify the type and number of
sub-modules required. The sub-module types are described below.

## Init: TmplMonrInit1

## Design Rationale

*None*

## Module Outputs

*Refer to FDD*

###  [section]

## Per: TmplMonrPer1

## Design Rationale

*None*

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD*

## Store Local copy of outputs into Module Outputs

*Refer to FDD*

## Per: TmplMonrPer2

## Design Rationale

*None*

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD*

## Store Local copy of outputs into Module Outputs

*Refer to FDD*

## Per: TmplMonrPer3

## Design Rationale

*None*

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD*

## Store Local copy of outputs into Module Outputs

*Refer to FDD*

## Server Runables 

None

## Interrupt Functions

*None*

## Module Internal (Local) Functions

## Local Function \#1

|                      |             |      |     |     |
|----------------------|-------------|------|-----|-----|
| **Function Name**    | TMFInitTest | Type | Min | Max |
| **Arguments Passed** | None        |      |     |     |
| **Return Value**     | N/A         |      |     |     |

## Design Rationale

None

## Processing

(Place flowchart/design for local function)

Refer to the “TMF Init Test” block of the Simulink model of the design.

## Local Function \#2

|                      |                  |      |     |     |
|----------------------|------------------|------|-----|-----|
| **Function Name**    | TMFInitTestCase0 | Type | Min | Max |
| **Arguments Passed** | None             |      |     |     |
| **Return Value**     | N/A              |      |     |     |

## Design Rationale

None

## Processing

(Place flowchart/design for local function)

Refer to the “TMF Init Test” block case 0 of the Simulink model of the
design.

## Local Function \#3

|                      |                                 |      |     |     |
|----------------------|---------------------------------|------|-----|-----|
| **Function Name**    | TMFInitTestCase10To11Case15To17 | Type | Min | Max |
| **Arguments Passed** | None                            |      |     |     |
| **Return Value**     | N/A                             |      |     |     |

## Design Rationale

None

## Processing

(Place flowchart/design for local function)

Refer to the “TMF Init Test” block case 10, case 11, case 15, case 16
and case 17 of the Simulink model of the design.

## Local Function \#4

|                      |                   |      |     |     |
|----------------------|-------------------|------|-----|-----|
| **Function Name**    | TMFInitTestCase13 | Type | Min | Max |
| **Arguments Passed** | None              |      |     |     |
| **Return Value**     | N/A               |      |     |     |

## Design Rationale

None

## Processing

(Place flowchart/design for local function)

Refer to the “TMF Init Test” block case 13 of the Simulink model of the
design.

## Local Function \#5

|                      |                   |      |     |     |
|----------------------|-------------------|------|-----|-----|
| **Function Name**    | TMFInitTestCase18 | Type | Min | Max |
| **Arguments Passed** | None              |      |     |     |
| **Return Value**     | N/A               |      |     |     |

## Design Rationale

None

## Processing

(Place flowchart/design for local function)

Refer to the “TMF Init Test” block case 18 of the Simulink model of the
design.

## Local Function \#6

|                      |                   |      |     |     |
|----------------------|-------------------|------|-----|-----|
| **Function Name**    | TMFInitTestCase19 | Type | Min | Max |
| **Arguments Passed** | None              |      |     |     |
| **Return Value**     | N/A               |      |     |     |

## Design Rationale

None

## Processing

(Place flowchart/design for local function)

Refer to the “TMF Init Test” block case 19 of the Simulink model of the
design.

## Local Function \#7

|                      |                   |      |     |     |
|----------------------|-------------------|------|-----|-----|
| **Function Name**    | TMFInitTestCase20 | Type | Min | Max |
| **Arguments Passed** | None              |      |     |     |
| **Return Value**     | N/A               |      |     |     |

## Design Rationale

None

## Processing

(Place flowchart/design for local function)

Refer to the “TMF Init Test” block case 20 of the Simulink model of the
design.

## Local Function \#8

|                      |                   |      |     |     |
|----------------------|-------------------|------|-----|-----|
| **Function Name**    | TMFInitTestCase21 | Type | Min | Max |
| **Arguments Passed** | None              |      |     |     |
| **Return Value**     | N/A               |      |     |     |

## Design Rationale

None

## Processing

(Place flowchart/design for local function)

Refer to the “TMF Init Test” block case 21 of the Simulink model of the
design.

## Local Function \#9

|                      |                   |      |     |     |
|----------------------|-------------------|------|-----|-----|
| **Function Name**    | TMFInitTestCase53 | Type | Min | Max |
| **Arguments Passed** | None              |      |     |     |
| **Return Value**     | N/A               |      |     |     |

## Design Rationale

None

## Processing

(Place flowchart/design for local function)

Refer to the “TMF Init Test” block case 53 of the Simulink model of the
design.

## Local Function \#10

|                      |                    |                  |     |        |
|----------------------|--------------------|------------------|-----|--------|
| **Function Name**    | SpiAsyncTx         | Type             | Min | Max    |
| **Arguments Passed** | Channel_Cnt_T_u16  | Spi_ChannelType  | 0U  | 65535U |
|                      | TxData_Cnt_T_u16   | Spi_DataType     | 0U  | 65535U |
|                      | Sequence_Cnt_T_u08 | Spi_SequenceType | 0U  | 255U   |
| **Return Value**     | N/A                |                  |     |        |

## Design Rationale

None

## Processing

(Place flowchart/design for local function)

This function is defined in order to call Spi_WriteIB and
Call_Spi_AsyncTransmit together in a sequence.

## GLOBAL Function/Macro Definitions

None

# Known Limitations with Design

None.

# UNIT TEST CONSIDERATION

Rte_Pim_TrsmErrCntr is a free running counter hence Overflow or rollover
is intentional.

####### Abbreviations and Acronyms

| **Abbreviation or Acronym** | **Description**           |
|-----------------------------|---------------------------|
| DFD                         | Design functional diagram |
| MDD                         | Module design Document    |

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
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 2.0                            |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.1                            |
| 5           | FDD – ES005C TmplMonr                                                                                                                                                 | See Synergy subproject version |

{% endraw %}