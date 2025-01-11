---
layout: default
title: TurnCntrCorrln_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**TurnCntrCorrln**

**May 18, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**TATA ELXSI,**

**Trivandrum, INDIA**

**<u>Change</u>** History

|                 |            |             |             |
|-----------------|------------|-------------|-------------|
| **Description** | **Author** | **Version** | **Date**    |
| Initial Version | TATA ELXSI | 1.0         | 18-May-2016 |

**<u>Table of Contents</u>**

[1 Introduction 5](#introduction)

[1.1 Purpose 5](#purpose)

[2 TurnCntrCorrln & High-Level Description
6](#turncntrcorrln-high-level-description)

[3 Design details of software module
7](#design-details-of-software-module)

[3.1 Graphical representation of TurnCntrCorrln
7](#graphical-representation-of-turncntrcorrln)

[3.2 Data Flow Diagram 7](#data-flow-diagram)

[3.2.1 Component level DFD 7](#component-level-dfd)

[3.2.2 Function level DFD 7](#function-level-dfd)

[4 Constant Data Dictionary 8](#constant-data-dictionary)

[4.1 Program (fixed) Constants 8](#program-fixed-constants)

[4.1.1 Embedded Constants 8](#embedded-constants)

[5 Software Component Implementation
9](#software-component-implementation)

[5.1 Sub-Module Functions 9](#sub-module-functions)

[5.1.1 Init: TurnCntrCorrlnInit1 9](#init-turncntrcorrlninit1)

[5.1.1.1 Design Rationale 9](#design-rationale)

[5.1.1.2 Module Outputs 9](#module-outputs)

[5.1.2 Per: TurnCntrCorrlnPer1 9](#per-turncntrcorrlnper1)

[5.1.2.1 Design Rationale 9](#design-rationale-1)

[5.1.2.2 Store Module Inputs to Local copies
9](#store-module-inputs-to-local-copies)

[5.1.2.3 (Processing of function)……… 9](#processing-of-function)

[5.1.2.4 Store Local copy of outputs into Module Outputs
9](#store-local-copy-of-outputs-into-module-outputs)

[5.2 Server Runables 9](#server-runables)

[5.3 Interrupt Functions 9](#interrupt-functions)

[5.4 Module Internal (Local) Functions
9](#module-internal-local-functions)

[5.4.1 Local Function \#1 9](#local-function-1)

[5.4.1.1 Design Rationale 10](#design-rationale-2)

[5.4.1.2 Processing 10](#processing)

[6 Known Limitations with Design 11](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION 12](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms 13](#abbreviations-and-acronyms)

[Appendix B Glossary 14](#glossary)

[Appendix C References 15](#references)

# Introduction

## Purpose

MDD for Turns counter correlation

# TurnCntrCorrln & High-Level Description

Please refer FDD

# Design details of software module

## Graphical representation of TurnCntrCorrln

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/ES261A_TurnCntrCorrln_Impl/doc/mediax/media/image1.png"
style="width:3.16667in;height:2.92708in" />

## Data Flow Diagram

### Component level DFD

Please refer FDD

### Function level DFD

Please refer FDD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

|                          |            |       |       |
|--------------------------|------------|-------|-------|
| Constant Name            | Resolution | Units | Value |
| Please refer the .m file |            |       |       |

# Software Component Implementation

## Sub-Module Functions

## Init: TurnCntrCorrlnInit1

## Design Rationale

None

## Module Outputs

None

## Per: TurnCntrCorrlnPer1

## Design Rationale

None

## Store Module Inputs to Local copies

None

##  (Processing of function)………

Please refer FDD

## Store Local copy of outputs into Module Outputs

Please refer FDD

## Server Runables 

None

## Interrupt Functions

None

## Module Internal (Local) Functions

## Local Function \#1

|                      |                         |          |               |               |
|--------------|------------------------------|---------|-----------|-----------|
| **Function Name**    | CorrlnSigAvlChk         | Type     | Min           | Max           |
| **Arguments Passed** | SigRollgCnt_Cnt_T_u08   | uint8    | 0             | 255           |
|                      | SigQlfr_Cnt_T_enum      | SigQlfr1 | SIGQLFR_NORES | SIGQLFR_FAILD |
|                      | \*LstRollgCnt_Cnt_T_u08 | uint8    | 0             | 255           |
|                      | \*LstStallCnt_Cnt_T_u08 | uint8    | 0             | 255           |
| **Return Value**     | SigAvl_Cnt_T_logl       | boolean  | FALSE         | TRUE          |

## Design Rationale

None

## Processing

Please refer the block CorrlnSigAvlChk0 and CorrlnSigAvlChk1 in FDD

# Known Limitations with Design

None.

# UNIT TEST CONSIDERATION

None.

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
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.00                    |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 1.0                             |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.1                             |
| 5           | ES261A_TurnCntrCorrln_Design                                                                                                                                          | See Synergy sub project version |

{% endraw %}