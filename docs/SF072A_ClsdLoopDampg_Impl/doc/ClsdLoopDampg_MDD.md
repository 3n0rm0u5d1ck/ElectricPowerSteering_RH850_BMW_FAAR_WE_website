---
layout: default
title: ClsdLoopDampg_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**ClsdLoopDampg**

**April 05, 2018**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**TATA ELXSI,**

**INDIA**

**  
<u>Change History</u>**

<table>
<colgroup>
<col style="width: 10%" />
<col style="width: 37%" />
<col style="width: 20%" />
<col style="width: 11%" />
<col style="width: 19%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Sl. No.</strong></td>
<td><strong>Description</strong></td>
<td><strong>Author</strong></td>
<td><strong>Version</strong></td>
<td><strong>Date</strong></td>
</tr>
<tr class="even">
<td>1</td>
<td>Initial version</td>
<td>Krzysztof Byrski</td>
<td>1</td>
<td>27-Feb-2018</td>
</tr>
<tr class="odd">
<td>2</td>
<td><p>Updated to add the additional _Init function generated for
autocode in Section 5.</p>
<p>Updated to add additional local constants required for autocode in
Section 4.1.1.1</p></td>
<td>Vipin David</td>
<td>2</td>
<td>05-Apr-2018</td>
</tr>
</tbody>
</table>

**  
**

<u>Table of Contents</u>1 Introduction 4

1.1 Purpose 4

1.2 Scope 4

2 ClsdLoopDampg & High-Level Description 5

3 Design details of software module 6

3.1 Graphical representation of ClsdLoopDampg 6

3.2 Data Flow Diagram 6

3.2.1 Component level DFD 6

3.2.2 Function level DFD 6

4 Constant Data Dictionary 7

4.1 Program (fixed) Constants 7

4.1.1 Embedded Constants 7

5 Software Component Implementation 8

5.1 Sub-Module Functions 8

5.1.1 Init: ClsdLoopDampgInit1 8

5.1.2 Init: ClsdLoopDampg_Init 8

5.1.3 Per: ClsdLoopDampgPer1 8

5.2 Server Runables 8

5.3 Interrupt Functions 8

5.4 Module Internal (Local) Functions 9

5.5 GLOBAL Function/Macro Definitions 9

6 Known Limitations with Design 10

7 UNIT TEST CONSIDERATION 11

Appendix A Abbreviations and Acronyms 12

Appendix B Glossary 13

Appendix C References 14

# Introduction

## Purpose

Module Design Document for SF072A_ClsdLoopDampg_Impl.

## Scope

The following definitions are used throughout this document:

-   **<u>Shall</u>**: indicates a mandatory requirement without
    exception in compliance.

-   **<u>Should</u>**: indicates a mandatory requirement; exceptions
    allowed only with documented justification.

-   **<u>May</u>**: indicates an optional action.

# ClsdLoopDampg & High-Level Description

This function produces a handwheel reference torque for the closed loop
system. This function calculates damping torque based on motor velocity
and scaled by factors such a rack force estimation. Closed Loop Damping
shall be calibrated based on vehicle speed, and motor velocity. End of
Travel shall affect the output signal command based on the EoT State,
EoT Delta Angle and EoT Assist Scale.

# Design details of software module

## Graphical representation of ClsdLoopDampg

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/SF072A_ClsdLoopDampg_Impl/doc/mediax/media/image1.png"
style="width:2.36224in;height:4.34367in" />

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
|               |            |       |       |
|               |            |       |       |
|               |            |       |       |
|               |            |       |       |
|               |            |       |       |
|               |            |       |       |
|               |            |       |       |
|               |            |       |       |
|               |            |       |       |
|               |            |       |       |

Refer SF072A_ClsdLoopDampg_DataDict.m for details.

# Software Component Implementation

## Sub-Module Functions

The sub-module functions are grouped based on similar functionality that
needs to be executed in a given “State” of the system (refer States and
Modes). For a given module, the MDD will identify the type and number of
sub-modules required. The sub-module types are described below.

### Init: ClsdLoopDampgInit1

#### Design Rationale

Refer FDD

#### Module Outputs

Refer FDD

### Init: ClsdLoopDampg_Init

#### Design Rationale

This init function is generated by embedded coder and is not present in
the Simulink model.

This function is always empty and is not called.

#### Module Outputs

There are no outputs for this function.

###  [section]

### Per: ClsdLoopDampgPer1

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
| 3           | EA4 Software Naming Conventions                                                                                                                                                                                                       | 1.0.3 draft                     |
| 4           | Software Design and Coding Standards                                                                                                                                                                                                  | 3.0 draft                       |
| 5           | SF072A_ClsdLoopDampg_Design                                                                                                                                                                                                           | See Synergy Sub Project Version |

{% endraw %}