---
layout: default
title: ClsdLoopHys_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**ClsdLoopHys**

**July** **17, 2018**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Tychy, Poland  
<u>Change History</u>**

<table>
<colgroup>
<col style="width: 45%" />
<col style="width: 25%" />
<col style="width: 13%" />
<col style="width: 15%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Description</strong></td>
<td><strong>Author</strong></td>
<td><strong>Version</strong></td>
<td><strong>Date</strong></td>
</tr>
<tr class="even">
<td>Initial version</td>
<td>Marek Brykczyński</td>
<td>1</td>
<td>10-May-2018</td>
</tr>
<tr class="odd">
<td><p>Added: New input port and local function</p>
<p>Modified: the function Interpolate</p></td>
<td>Marek Brykczyński</td>
<td>2</td>
<td>17-July-2018</td>
</tr>
</tbody>
</table>

**  
**

**<u>Table of Contents</u>**

[1 Introduction [4](#introduction)](#introduction)

[1.1 Purpose [4](#purpose)](#purpose)

[1.2 Scope [4](#scope)](#scope)

[2 ClsdLoopHys & High-Level Description
[5](#clsdloophys-high-level-description)](#clsdloophys-high-level-description)

[3 Design details of software module
[6](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of ClsdLoopHys
[6](#graphical-representation-of-clsdloophys)](#graphical-representation-of-clsdloophys)

[3.2 Data Flow Diagram [6](#data-flow-diagram)](#data-flow-diagram)

[3.2.1 Component level DFD
[6](#component-level-dfd)](#component-level-dfd)

[3.2.2 Function level DFD [6](#function-level-dfd)](#function-level-dfd)

[4 Constant Data Dictionary
[7](#constant-data-dictionary)](#constant-data-dictionary)

[4.1 Program (fixed) Constants
[7](#program-fixed-constants)](#program-fixed-constants)

[4.1.1 Embedded Constants [7](#embedded-constants)](#embedded-constants)

[5 Software Component Implementation
[8](#software-component-implementation)](#software-component-implementation)

[5.1 Sub-Module Functions
[8](#sub-module-functions)](#sub-module-functions)

[5.1.1 Init: ClsdLoopHysInit1 [8](#init-init1)](#init-init1)

[5.1.2 Per: ClsdLoopHysPer1 [8](#per-per1)](#per-per1)

[5.2 Server Runables [8](#server-runables)](#server-runables)

[5.3 Interrupt Functions
[8](#interrupt-functions)](#interrupt-functions)

[5.4 Module Internal (Local) Functions
[9](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 Interpolate [9](#interpolate)](#interpolate)

[5.4.2 IntgtrLimCalcn [9](#_Toc513644735)](#_Toc513644735)

[5.4.3 CompCalcn1 [9](#compcalcn1)](#compcalcn1)

[5.4.4 CompCalcn1 [9](#compcalcn1-1)](#compcalcn1-1)

[5.5 GLOBAL Function/Macro Definitions
[10](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[6 Known Limitations with Design
[11](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[12](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[13](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [14](#glossary)](#glossary)

[Appendix C References [15](#references)](#references)

# Introduction

## Purpose

The Module Design Document for SF073A_ClsdLoopHys_Impl.

## Scope

The following definitions are used throughout this document:

-   **<u>Shall</u>**: indicates a mandatory requirement without
    exception in compliance.

-   **<u>Should</u>**: indicates a mandatory requirement; exceptions
    allowed only with documented justification.

-   **<u>May</u>**: indicates an optional action.

# ClsdLoopHys & High-Level Description

The Closed Loop Hysteresis function shall provide a controllable
hysteresis shaped Reference Handwheel Torque component based on a
current Rack Load.

# Design details of software module

## Graphical representation of ClsdLoopHys

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/SF073A_ClsdLoopHys_Impl/doc/mediax/media/image2.png"
style="width:5.34375in;height:5.60417in" />

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

### Init: Init1

#### Design Rationale

Refer FDD

#### Module Outputs

Refer FDD

### Per: Per1

#### Design Rationale

Refer FDD

#### Store Module Inputs to Local copies

Refer FDD

#### (Processing of function)………

Refer FDD

#### Store Local copy of outputs into Module Outputs

Refer FDD

## Server Runables 

None

## Interrupt Functions

None

## Module Internal (Local) Functions

### Interpolate

<table>
<colgroup>
<col style="width: 18%" />
<col style="width: 43%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Function Name</strong></td>
<td>Interpolate</td>
<td>Type</td>
<td>Min</td>
<td>Max</td>
</tr>
<tr class="even">
<td><strong>Arguments Passed</strong></td>
<td><p>Y_Tbl_1D:</p>
<p>- ClsdLoopHysDelta</p>
<p>- ClsdLoopHysGain</p>
<p>- ClsdLoopHysRho<strong>*</strong></p></td>
<td>Pointer to const table with uint16</td>
<td>0</td>
<td>10240 / 20480<strong>*</strong></td>
</tr>
<tr class="odd">
<td></td>
<td>VehSpd_Kph_T_u9p7</td>
<td>uint16</td>
<td>0</td>
<td>65408</td>
</tr>
<tr class="even">
<td><strong>Return Value</strong></td>
<td>A result of a conversion of fixed-point to float32</td>
<td>float32</td>
<td>0</td>
<td>10 / 20<strong>*</strong></td>
</tr>
</tbody>
</table>

### IntgtrLimCalcn

|                      |                         |                          |              |             |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | IntgtrLimCalcn          | Type                     | Min          | Max         |
| **Arguments Passed** | HwVel_HwRadPerSec_T_f32 | float32                  | -42          | 42          |
|                      | HwAg_HwRad_T_f32        | float32                  | -25.13274192 | 25.13274192 |
|                      | UpprIngtrLim_Uls_T_f32  | const pointer to float32 | -5           | 5           |
|                      | LwrIngtrLim_Uls_T_f32   | const pointer to float32 | -5           | 5           |
| **Return Value**     | \-                      | \-                       | \-           | \-          |

### CompCalcn1

|                      |                         |         |        |       |
|----------------------|-------------------------|---------|--------|-------|
| **Function Name**    | CompCalcn1              | Type    | Min    | Max   |
| **Arguments Passed** | HwVel_HwRadPerSec_T_f32 | float32 | -42    | 42    |
|                      | HysBasFac_Uls_T_f32     | float32 | -10    | 10    |
|                      | Delta_Uls_T_f32         | float32 | 0      | 10    |
| **Return Value**     | Result_T_Uls_f32        | Float32 | -42000 | 42000 |

### CompCalcn1

|                      |                         |         |       |       |
|----------------------|-------------------------|---------|-------|-------|
| **Function Name**    | CompCalcn2              | Type    | Min   | Max   |
| **Arguments Passed** | HwVel_HwRadPerSec_T_f32 | float32 | -42   | 42    |
|                      | HysBasFac_Uls_T_f32     | float32 | -10   | 10    |
|                      | Delta_Uls_T_f32         | float32 | 0     | 10    |
| **Return Value**     | Result_T_Uls_f32        | float32 | -4200 | 37800 |

### SysFricOffsLimdCalc

|                      |                                                  |         |     |       |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | SysFricOffsLimdCalc                              | Type    | Min | Max   |
| **Arguments Passed** | VehSpd_Kph_T_u9p7                                | uint16  | 0   | 65408 |
|                      | SysFricOffs_HwNwtMtr_T_f32                       | float32 | -5  | 5     |
| **Return Value**     | return value of conversion from u2p14 to float32 | float32 | 0   | 2     |

#### Design Rationale

Refer FDD

#### Processing

Refer FDD

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
| 5           | SF073A_ClsdLoopHys_Design                                                                                                                                                                                                             | See Synergy Sub Project Version |

{% endraw %}