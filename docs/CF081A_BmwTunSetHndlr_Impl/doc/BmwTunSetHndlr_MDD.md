---
layout: default
title: BmwTunSetHndlr_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**BmwTunSetHndlr**

**May 17, 2018**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                          |                   |             |             |
|--------------------------|-------------------|-------------|-------------|
| **Description**          | **Author**        | **Version** | **Date**    |
| Initial version          | Krzysztof Byrski  | 1           | 27-Mar-2018 |
| Updates per design 2.0.0 | Marek Brykczyński | 2           | 10-Apr-2018 |
| Updates per design 3.0.0 | Krzysztof Byrski  | 3           | 17-May-2018 |

**  
**

**<u>Table of Contents</u>**

1 Introduction 4

1.1 Purpose 4

1.2 Scope 4

2 BmwTunSetHndlr & High-Level Description 5

3 Design details of software module 6

3.1 Graphical representation of BmwTunSetHndlr 6

3.2 Data Flow Diagram 6

3.2.1 Component level DFD 6

3.2.2 Function level DFD 6

4 Constant Data Dictionary 7

4.1 Program (fixed) Constants 7

4.1.1 Embedded Constants 7

5 Software Component Implementation 8

5.1 Sub-Module Functions 8

5.1.1 Init: BmwTunSetHndlrInit1 8

5.1.2 Per: BmwTunSetHndlrPer1 8

5.2 Server Runables 9

5.2.1 TunVrntRead_Oper 9

5.2.2 TunVrntWr_Oper 9

5.2.3 MotVrntRead_Oper 9

5.2.4 MotVrntWr_Oper 9

5.3 Interrupt Functions 10

5.4 Module Internal (Local) Functions 10

5.5 GLOBAL Function/Macro Definitions 10

6 Known Limitations with Design 11

7 UNIT TEST CONSIDERATION 12

Appendix A Abbreviations and Acronyms 13

Appendix B Glossary 14

Appendix C References 15

# Introduction

## Purpose

Module Design Document for CF081A_BmwTunSetHndlr_Impl.

## Scope

The following definitions are used throughout this document:

-   **<u>Shall</u>**: indicates a mandatory requirement without
    exception in compliance.

-   **<u>Should</u>**: indicates a mandatory requirement; exceptions
    allowed only with documented justification.

-   **<u>May</u>**: indicates an optional action.

# BmwTunSetHndlr & High-Level Description

The BMW Tuning Set Handler provides a desired Runtime Index of an
integer type. As the input, the function receives the desired Runtime
Index. If a received value is valid then the function maps it to one of
three defined values. If the proper calibration is set then the function
allows overriding the output to a calibratable value. The function
provides two server runnables in order to write to and to read from the
NVM. During the initialization, it evaluates if the NVM is valid, if the
NVM is detected invalid then it stores a predefined constant.

# Design details of software module

## Graphical representation of BmwTunSetHndlr

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/CF081A_BmwTunSetHndlr_Impl/doc/mediax/media/image2.png"
style="width:3.45114in;height:4.00154in" />

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

| Constant Name | Resolution | Units | Value |
|---------------|------------|-------|-------|
| \-            |            |       |       |

Refer FDD for local constants.

# Software Component Implementation

## Sub-Module Functions

The sub-module functions are grouped based on similar functionality that
needs to be executed in a given “State” of the system (refer States and
Modes). For a given module, the MDD will identify the type and number of
sub-modules required. The sub-module types are described below.

### Init: BmwTunSetHndlrInit1

#### Design Rationale

Refer FDD

#### Module Outputs

Refer FDD

###  [section]

### Per: BmwTunSetHndlrPer1

#### Design Rationale

Refer FDD

#### Store Module Inputs to Local copies

Refer FDD

#### (Processing of function)………

Refer FDD

#### Store Local copy of outputs into Module Outputs

Refer FDD

## Server Runables 

### TunVrntRead_Oper

#### Design Rationale

Refer FDD

####  (Processing of function)………

Refer FDD

### TunVrntWr_Oper

#### Design Rationale

Refer FDD

####  (Processing of function)………

Refer FDD

### MotVrntRead_Oper

#### Design Rationale

Refer FDD

####  (Processing of function)………

Refer FDD

### MotVrntWr_Oper

#### Design Rationale

Refer FDD

####  (Processing of function)………

Refer FDD

## Interrupt Functions

None

## Module Internal (Local) Functions

None

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
| 2           | MDD Guideline EA4                                                                                                                                                                                                                     | 1.02                            |
| 3           | EA4 Software Naming Conventions                                                                                                                                                                                                       | 1.01                            |
| 4           | Software Design and Coding Standards                                                                                                                                                                                                  | 2.01                            |
| 5           | CF081A_BmwTunSetHndlr_Design                                                                                                                                                                                                          | See Synergy Sub Project Version |

{% endraw %}