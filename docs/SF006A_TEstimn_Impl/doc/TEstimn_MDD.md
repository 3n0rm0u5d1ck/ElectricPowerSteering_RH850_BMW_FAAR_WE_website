---
layout: default
title: TEstimn_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**TEstimn**

**06-Apr-2018**

**Prepared By:**

**Shawn Penning,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                                                     |                        |             |             |
|------------------------|---------------------|--------------|--------------|
| **Description**                                     | **Author**             | **Version** | **Date**    |
| Initial Version                                     | Sankardu Varadapureddi | 1           | 17-Sep-2015 |
| Updated to Design v2.2.0                            | Matthew Leser          | 2           | 26-Apr-2017 |
| Updated Graph and added new local function          | Matthew Leser          | 3           | 06-Dec-2017 |
| Added local constants and unit test considerations. | SPP                    | 4           | 06-Apr-2018 |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [4](#introduction)](#introduction)

[1.1 Purpose [4](#purpose)](#purpose)

[1.2 Scope [4](#scope)](#scope)

[2 TEstimn High-Level Description
[5](#testimn-high-level-description)](#testimn-high-level-description)

[3 Design details of software module
[6](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of TEstimn
[6](#graphical-representation-of-testimn)](#graphical-representation-of-testimn)

[3.2 Data Flow Diagram [6](#data-flow-diagram)](#data-flow-diagram)

[3.2.1 Component level DFD
[6](#component-level-dfd)](#component-level-dfd)

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

[5.1.1 Init: TEstimnInit1 [9](#init-testimninit1)](#init-testimninit1)

[5.1.1.1 Design Rationale [9](#design-rationale)](#design-rationale)

[5.1.1.2 Module Outputs [9](#module-outputs)](#module-outputs)

[5.1.2 Per: TEstimnPer1 [9](#per-testimnper1)](#per-testimnper1)

[5.1.2.1 Design Rationale [9](#design-rationale-1)](#design-rationale-1)

[5.1.2.2 Store Module Inputs to Local copies
[9](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[5.1.2.3 (Processing of function)………
[9](#processing-of-function)](#processing-of-function)

[5.1.2.4 Store Local copy of outputs into Module Outputs
[9](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[5.2 Server Runables [9](#server-runnables)](#server-runnables)

[5.3 Interrupt Functions
[9](#interrupt-functions)](#interrupt-functions)

[5.4 Module Internal (Local) Functions
[9](#module-internal-local-functions)](#module-internal-local-functions)

[5.5 GLOBAL Function/Macro Definitions
[9](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[6 Known Limitations with Design
[10](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[11](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[12](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [13](#glossary)](#glossary)

[Appendix C References [14](#references)](#references)

# Introduction

## Purpose

## Scope

# TEstimn High-Level Description

Refer to FDD

# Design details of software module

## Graphical representation of TEstimn

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/SF006A_TEstimn_Impl/doc/mediax/media/image1.png"
style="width:2.74035in;height:6.45105in" />

## Data Flow Diagram

Refer FDD

### Component level DFD

### Function level DFD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

Refer .m file

#### Local Constants

\#define TESTIMNASSIMECHTHILIM_DEGCGRD_F32 150.0F

\#define TESTIMNASSIMECHTLOLIM_DEGCGRD_F32 (-50.0F)

\#define TESTIMNFETTHILIM_DEGCGRD_F32 200.0F

\#define TESTIMNFETTLOLIM_DEGCGRD_F32 (-50.0F)

\#define TESTIMNMAGTHILIM_DEGCGRD_F32 150.0F

\#define TESTIMNMAGTLOLIM_DEGCGRD_F32 (-50.0F)

\#define TESTIMNWIDGTHILIM_DEGCGRD_F32 300.0F

\#define TESTIMNWIDGTLOLIM_DEGCGRD_F32 (-50.0F)

\#define DUALECUSTSIDX_CNT_U08 ((uint8)0U)

\#define SNGECUSTSIDX_CNT_U08 ((uint8)1U)

\#define EXPCOEFF_ULS_F32 (-1.0F)

\#define SILLFILVALMIN_ULS_F32 (-2431500.0F)

\#define SILLFILVALMAX_ULS_F32 (1001200.0F)

\#define SILPFILVALMIN_ULS_F32 (0.0F)

\#define SILPFILVALMAX_ULS_F32 (62500.0F)

\#define ASSIMECHLLFILVALMIN_ULS_F32 (-4577000.0F)

\#define ASSIMECHLLFILVALMAX_ULS_F32 (1716400.0F)

\#define ASSIMECHLPFILVALMIN_ULS_F32 (0.0F)

\#define ASSIMECHLPFILVALMAX_ULS_F32 (1764.0F)

\#define CULLFILVALMIN_ULS_F32 (-2431500.0F)

\#define CULLFILVALMAX_ULS_F32 (1001200.0F)

\#define CULPFILVALMIN_ULS_F32 (0.0F)

\#define CULPFILVALMAX_ULS_F32 (62500.0F)

\#define MAGLLFILVALMIN_ULS_F32 (-2431500.0F)

\#define MAGLLFILVALMAX_ULS_F32 (1001200.0F)

\#define MAGLPFILVALMIN_ULS_F32 (0.0F)

\#define MAGLPFILVALMAX_ULS_F32 (62500.0F)

\#define FILVALMIN_ULS_F32 (0.0F)

\#define TESTIMNFETMTGTNIDX_CNT_U08 ((uint8)2U)

\#define TESTIMNIGNTIOFFTHD_CNT_F32 (10000.0F)

# Software Component Implementation

## Sub-Module Functions

## Init: TEstimnInit1

## Design Rationale

\#define FETLOABITMASK_CNT_U08 ((uint8)4U) *Refer FDD for the
functionality.*

## Module Outputs

*Refer FDD*

## Per: TEstimnPer1

## Design Rationale

In ‘AssistMechanismLeadLagFilterRe-Initialization’ block, blocks
‘AssistMechanismInitEnable’ and ‘AssistMechanismInitDisable’ have
similar logic except for some calculations related to inputs. So the
differences are implemented in ‘if-else’ statement and common logic is
implemented after ‘if-else’ statements in the SW.

## Store Module Inputs to Local copies

*Refer FDD*

## (Processing of function)………

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*Refer FDD*

## Server Runnables 

*None*

## Interrupt Functions

*None*

## Module Internal (Local) Functions

## Local Function \#1

|                      |                               |         |       |      |
|----------------------|-------------------------------|---------|-------|------|
| **Function Name**    | FltMtgtnCalSeln               | Type    | Min   | Max  |
| **Arguments Passed** | FetLoaMtgtnEna_Cnt_T_logl     | boolean | FALSE | TRUE |
|                      | DualEcuFltMtgtnEna_Cnt_T_logl | boolean | FALSE | TRUE |
| **Return Value**     | NA                            | NA      | NA    | NA   |

## Design Rationale

Implementation of ‘Fault Mitigation Calibration Selection’ block in FDD
(To reduce cyclomatic complexity & path count in Per1).

## GLOBAL Function/Macro Definitions

None

# Known Limitations with Design

*None*

# UNIT TEST CONSIDERATION

|     |     |     |     |     |
|-----|-----|-----|-----|-----|
|     |     |     |     |     |
|     |     |     |     |     |
|     |     |     |     |     |
|     |     |     |     |     |
|     |     |     |     |     |

Calculate TEstimnSiLLFilCoeffB0 as per following equation:

TEstimnSiLLFilCoeffB0=
-1\*\[(TEstimnSiLLFilCoeffA1-1)+TEstimnSiLLFilCoeffB1\]

Calculate TEstimnCuLLFilCoeffB0 as per following equation:

TEstimnCuLLFilCoeffB0=
-1\*\[(TEstimnCuLLFilCoeffA1-1)+TEstimnCuLLFilCoeffB1\]

Calculate TEstimnMagLLFilCoeffB0 as per following equation:

TEstimnMagLLFilCoeffB0=
-1\*\[(TEstimnMagLLFilCoeffA1-1)+TEstimnMagLLFilCoeffB1\]

Calculate TEstimnAssiMechLLFilCoeffB0 as per following equation:

TEstimnAssiMechLLFilCoeffB0=
-1\*\[(TEstimnAssiMechLLFilCoeffA1-1)+TEstimnAssiMechLLFilCoeffB1\]

Anomaly 20644 Issue 1B and 1C were not addressed due to time
considerations. Anomaly 19666 issue 4 is a test issue that should be
addressed by test team but does not affect design or code.

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
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | EA4 01.00.00                    |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.1                             |
| 5           | FDD : SF006A\_ TEstimn_Design                                                                                                                                         | See Synergy sub project version |

{% endraw %}