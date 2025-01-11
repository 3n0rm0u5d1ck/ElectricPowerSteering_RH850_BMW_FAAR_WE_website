---
layout: default
title: EpsStEstimn_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**EpsStEstimn**

**April 12, 2018**

**Prepared By:**

**Matthew Leser**

**Software Group,**

**Nexteer Automotive,**

**<u>Saginaw, MI, USAChange</u>** History

|                 |               |             |             |
|-----------------|---------------|-------------|-------------|
| **Description** | **Author**    | **Version** | **Date**    |
| Initial Version | Matthew Leser | 1.0         | 12-Apr-2018 |

<u>Table of Contents</u>

[1 Introduction 4](#introduction)

[1.1 Purpose 4](#purpose)

[2 EpsStEstimn & High-Level Description
5](#epsstestimn-high-level-description)

[3 Design details of software module
6](#design-details-of-software-module)

[3.1 Graphical representation of EpsStEstimn
6](#graphical-representation-of-epsstestimn)

[3.2 Data Flow Diagram 6](#data-flow-diagram)

[3.2.1 Component level DFD 6](#component-level-dfd)

[3.2.2 Function level DFD 6](#function-level-dfd)

[4 Constant Data Dictionary 7](#constant-data-dictionary)

[4.1 Program (fixed) Constants 7](#program-fixed-constants)

[4.1.1 Embedded Constants 7](#embedded-constants)

[5 Software Component Implementation
8](#software-component-implementation)

[5.1 Sub-Module Functions 8](#sub-module-functions)

[5.1.1 Init: EpsStEstimnInit1 8](#init-epsstestimninit1)

[5.1.1.1 Design Rationale 8](#design-rationale)

[5.1.1.2 Module Outputs 8](#module-outputs)

[5.1.2 Per: EpsStEstimnPer1 8](#per-epsstestimnper1)

[5.1.2.1 Design Rationale 8](#design-rationale-1)

[5.1.2.2 Store Module Inputs to Local copies
8](#store-module-inputs-to-local-copies)

[5.1.2.3 (Processing of function)……… 8](#processing-of-function)

[5.1.2.4 Store Local copy of outputs into Module Outputs
8](#store-local-copy-of-outputs-into-module-outputs)

[5.2 Server Runables 8](#server-runnables)

[5.3 Interrupt Functions 8](#interrupt-functions)

[5.4 Module Internal (Local) Functions
9](#module-internal-local-functions)

[5.5 GLOBAL Function/Macro Definitions
9](#global-functionmacro-definitions)

[6 Known Limitations with Design 10](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION 11](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms 12](#abbreviations-and-acronyms)

[Appendix B Glossary 13](#glossary)

# Introduction

## Purpose

Module design document for EpsStEstimn.

#  EpsStEstimn & High-Level Description

# Design details of software module

## Graphical representation of EpsStEstimn

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/SF066A_EpsStEstimn_Impl/doc/mediax/media/image1.png"
style="width:4.64583in;height:2.73958in" />

## Data Flow Diagram

### Component level DFD

N/A

### Function level DFD

N/A

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

|               |            |       |       |
|---------------|------------|-------|-------|
| Constant Name | Resolution | Units | Value |
| NA            | NA         | NA    | NA    |

Refer to .m file for other defined constants.

# Software Component Implementation

## Sub-Module Functions

## Init: EpsStEstimnInit1

## Design Rationale

## Module Outputs

*Refer to FDD*

###  [section]

## Per: EpsStEstimnPer1

## Design Rationale

*None*

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD*

## Store Local copy of outputs into Module Outputs

*Refer to FDD*

## Server Runnables 

## Interrupt Functions

*None*

## Module Internal (Local) Functions

*None*

## GLOBAL Function/Macro Definitions

None

# Known Limitations with Design

None.

# UNIT TEST CONSIDERATION

None.

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

References

| **Ref. \#** | **Title**                                                                                                                                                             | **Version**                    |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                    | v1.3.0 R4.0 Rev 2              |
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.00                   |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 1.0                            |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.1                            |
| 5           | FDD – SF066A_EpsStEstimn_Design                                                                                                                                       | See Synergy subproject version |

{% endraw %}