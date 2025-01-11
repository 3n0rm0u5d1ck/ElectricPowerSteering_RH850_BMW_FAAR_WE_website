---
layout: default
title: LrndRackCentr_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**LrndRackCentr**

**October 26, 2017**

**Prepared By:**

**Matthew Leser,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**<u>Change History</u>**

|                 |            |             |             |
|-----------------|------------|-------------|-------------|
| **Description** | **Author** | **Version** | **Date**    |
| Initial Version | ML         | 1.0         | 26-Oct-2017 |

**  
**

<u>Table of Contents</u>

[1 Introduction [5](#introduction)](#introduction)

[1.1 Purpose [5](#purpose)](#purpose)

[1.2 Scope [5](#scope)](#scope)

[2 LrndRackCenter & High-Level Description
[6](#lrndrackcenter-high-level-description)](#lrndrackcenter-high-level-description)

[3 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of LrndRackCentr
[7](#graphical-representation-of-lrndrackcentr)](#graphical-representation-of-lrndrackcentr)

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

[5.1.1 Init: LrndRackCentrInit1
[9](#init-lrndrackcentrinit1)](#init-lrndrackcentrinit1)

[5.1.1.1 Design Rationale [9](#design-rationale)](#design-rationale)

[5.1.2 Per: LrndRackCentrPer1
[9](#per-lrndrackcentrper1)](#per-lrndrackcentrper1)

[5.1.2.1 Design Rationale [9](#design-rationale-1)](#design-rationale-1)

[5.2 Server Runnable [9](#server-runnable)](#server-runnable)

[5.3 Interrupt Functions
[9](#interrupt-functions)](#interrupt-functions)

[5.4 Module Internal (Local) Functions
[9](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 Local Function \#1 [9](#local-function-1)](#local-function-1)

[5.4.1.1 Description [9](#description)](#description)

[5.4.2 Local Function \#2 [9](#local-function-2)](#local-function-2)

[5.4.2.1 Description [10](#description-1)](#description-1)

[5.5 GLOBAL Function/Macro Definitions
[10](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[6 Known Limitations with Design
[11](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[12](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[13](#_Toc496856019)](#_Toc496856019)

[Appendix B Glossary [14](#glossary)](#glossary)

[Appendix C References [15](#references)](#references)

# Introduction

## Purpose

## Scope

# LrndRackCenter & High-Level Description

*Refer FDD.*

# Design details of software module

## Graphical representation of LrndRackCentr 

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/SF039A_LrndRackCentr_Impl/doc/mediax/media/image1.png"
style="width:2.99327in;height:3.41732in" />

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

| Constant Name                                      | Resolution | Units | Value |
|---------------------------------|---------------|-----------|-------------|
| Refer DataDict.m file from FDD for other constants | \-         | \-    | \-    |

# Software Component Implementation

## Sub-Module Functions

## Init: LrndRackCentrInit1

> Refer FDD Simulink model

## Design Rationale

> None

## Per: LrndRackCentrPer1

> Refer FDD Simulink Model

## Design Rationale

Refer to Anomaly EA4#17201. Implementation deviates from design to fix
for build.

## Server Runnable

## Interrupt Functions

None

## Module Internal (Local) Functions

## Local Function \#1

|                      |                              |         |       |      |
|----------------------|------------------------------|---------|-------|------|
| **Function Name**    | ManLrnRackCentr              | Type    | Min   | Max  |
| **Arguments Passed** | HwAg_HwDeg_T_f32             | float32 | -1440 | 1440 |
|                      | MotVelCrf_MotRadPerSec_T_f32 | float32 | -1350 | 1350 |
|                      | MotTqCmd_MotNwtMtr_T_f32     | float32 | -8.8  | 8.8  |
| **Return Value**     | None                         |         |       |      |

## Description

Implementation of ‘MANUAL LEARN RACK CENTER’ subsystem.

## Local Function \#2

|                      |                                |         |       |      |
|----------------------|--------------------------------|---------|-------|------|
| **Function Name**    | ChkRackCentr                   | Type    | Min   | Max  |
| **Arguments Passed** | HwTrvl_HwDeg_T_f32             | float32 | 0     | 2880 |
|                      | RackCentr_HwDeg_T_f32          | float32 | -1440 | 1440 |
|                      | \*RackCentrMotAgVld_Cnt_T_logl | boolean | FALSE | TRUE |
|                      | \*RackCentrCmpl_Cnt_T_logl     | boolean | FALSE | TRUE |
| **Return Value**     | None                           |         |       |      |

## Description

Implementation of ‘Confirm Rack Center Found’ subsystem.

## GLOBAL Function/Macro Definitions

None

# Known Limitations with Design

None

# UNIT TEST CONSIDERATION

<span id="_Toc496856019" class="anchor"></span>Refer to Anomaly
EA4#17201. Implementation deviates from design to fix for build.

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

| **Ref. \#** | **Title**                                                                                                                                                                                                                             | **Version**                    |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](https://www.autosar.org/fileadmin/files/standards/classic/4-0/software-architecture/implementation-integration/standard/AUTOSAR_SWS_MemoryMapping.pdf)) | v1.4.0 R4.0 Rev 3              |
| 2           | MDD Guideline                                                                                                                                                                                                                         | EA4 01.00.01                   |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)                                                                   | 1.0                            |
| 4           | [Software Design and Coding Standards.doc](http://eroom.nexteer.com/eRoomReq/Files/Nexteer-ProductLineSystems/ProcessDocumentsSystemsElectronicSystems/0_35a2f/Software%20Design%20and%20Coding%20Standards%202.1.doc)                | 2.1                            |
| 5           | FDD – SF039A_LrndRackCentr_Design                                                                                                                                                                                                     | See Synergy Subproject verison |

{% endraw %}