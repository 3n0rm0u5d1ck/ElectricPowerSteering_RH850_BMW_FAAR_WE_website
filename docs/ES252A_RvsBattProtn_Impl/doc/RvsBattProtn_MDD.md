---
layout: default
title: RvsBattProtn_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**RvsBattProtn**

**October 16, 2017**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                 |                  |             |             |
|-----------------|------------------|-------------|-------------|
| **Description** | **Author**       | **Version** | **Date**    |
| Initial Version | Krzysztof Byrski | 1           | 16-Oct-2017 |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [4](#introduction)](#introduction)

[1.1 Purpose [4](#purpose)](#purpose)

[1.2 Scope [4](#scope)](#scope)

[2 RvsBattProtn & High-Level Description
[5](#rvsbattprotn-high-level-description)](#rvsbattprotn-high-level-description)

[3 Design details of software module
[6](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of RvsBattProtn
[6](#graphical-representation-of-rvsbattprotn)](#graphical-representation-of-rvsbattprotn)

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

[5.1.1 Init: RvsBattProtn_Init\<n\>
[8](#init-rvsbattprotninit1)](#init-rvsbattprotninit1)

[5.1.2 Per: RvsBattProtn_Per\<n\>
[8](#per-rvsbattprotnper1)](#per-rvsbattprotnper1)

[5.2 Server Runables [8](#server-runables)](#server-runables)

[5.2.1 \<Server Runable Name\> [8](#_Toc495923082)](#_Toc495923082)

[5.3 Interrupt Functions
[9](#interrupt-functions)](#interrupt-functions)

[5.3.1 Interrupt Function Name [9](#_Toc495923084)](#_Toc495923084)

[5.4 Module Internal (Local) Functions
[9](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 Local Function \#1 [9](#_Toc495923086)](#_Toc495923086)

[5.5 GLOBAL Function/Macro Definitions
[9](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[5.5.1 GLOBAL Function \#1 [9](#_Toc495923088)](#_Toc495923088)

[6 Known Limitations with Design
[11](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[12](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[13](#_Toc495923091)](#_Toc495923091)

[Appendix B Glossary [14](#glossary)](#glossary)

[Appendix C References [15](#references)](#references)

# Introduction

## Purpose

Module Design Document for ES252A_RvsBattProtn_Impl

## Scope

The following definitions are used throughout this document:

-   **<u>Shall</u>**: indicates a mandatory requirement without
    exception in compliance.

-   **<u>Should</u>**: indicates a mandatory requirement; exceptions
    allowed only with documented justification.

-   **<u>May</u>**: indicates an optional action.

# RvsBattProtn & High-Level Description

Refer FDD.

# Design details of software module

This module provides diagnostics of Reverse Battery Protection Module.
Main task is to detect opened Reverse Protection MOSFET channel.

## Graphical representation of RvsBattProtn

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/ES252A_RvsBattProtn_Impl/doc/mediax/media/image1.png"
style="width:4.67708in;height:3.375in" />

## Data Flow Diagram

Refer FDD

### Component level DFD

None

### Function level DFD

None

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name                       | Resolution | Units | Value |
|-------------------------------------|------------|-------|-------|
| RVSBATTPROTN_FLTTYPADCFAILD_CNT_U08 | 1          | Cnt   | 4     |
| RVSBATTPROTN_FLTTYPOOR_CNT_U08      | 1          | Cnt   | 2     |
| RVSBATTPROTN_FLTTYPRVSFLT_CNT_U08   | 1          | Cnt   | 1     |

# Software Component Implementation

## Sub-Module Functions

The sub-module functions are grouped based on similar functionality that
needs to be executed in a given “State” of the system (refer States and
Modes). For a given module, the MDD will identify the type and number of
sub-modules required. The sub-module types are described below.

### Init: RvsBattProtnInit1

#### Design Rationale

Refer FDD

#### Module Outputs

Refer FDD

### Per: RvsBattProtnPer1

#### Design Rationale

Refer FDD

#### Store Module Inputs to Local copies

Refer FDD

####  (Processing of function)………

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

<span id="_Toc495923091" class="anchor"></span>This component uses
config params for some configurable constants. However for testing these
in PIL/SIL, please use the following strategy:

1.  Rename the *RvsBattProtn_Cfg_PIL.h* file in *tools/local/include*
    folder to *RvsBattProtn_Cfg.h*

2.  Replace the *RvsBattProtn_Cfg.h* file in tools/local/generate folder
    with the above file.

Now, Tessy must be able to modify the values of these config params. We
should then test them with the range that is given in their definition
in the DataDict.m file.

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
| 2           | MDD Guideline EA4                                                                                                                                                                                                                     | 01.00.01                        |
| 3           | EA4 Software Naming Conventions                                                                                                                                                                                                       | 01.01.00                        |
| 4           | Software Design and Coding Standards                                                                                                                                                                                                  | 2.1                             |
| 5           | ES252A_RvsBattProtn_Design                                                                                                                                                                                                            | See Synergy Sub Project Version |

{% endraw %}