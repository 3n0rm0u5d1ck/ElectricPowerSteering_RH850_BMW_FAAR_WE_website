---
layout: default
title: BattVltg_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**BattVltg**

**27-Sep-2017**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Brionna Spencer,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                                             |            |             |             |
|--------------------------------|-------------|------------|---------------|
| **Description**                             | **Author** | **Version** | **Date**    |
| Initial Version                             | N. Saxton  | 1.0         | 18-May-2016 |
| Removed local constants and updated graphic | B. Spencer | 2.0         | 27-Sep-2017 |

<u>Table of Contents</u>

[1 BattVltg High-Level Description
[4](#battvltg-high-level-description)](#battvltg-high-level-description)

[2 Design details of software module
[5](#design-details-of-software-module)](#design-details-of-software-module)

[2.1 Graphical representation of BattVltg
[5](#graphical-representation-of-battvltg)](#graphical-representation-of-battvltg)

[2.2 Data Flow Diagram [5](#data-flow-diagram)](#data-flow-diagram)

[2.2.1 Component level DFD
[5](#component-level-dfd)](#component-level-dfd)

[2.2.2 Function level DFD [5](#function-level-dfd)](#function-level-dfd)

[3 Constant Data Dictionary
[6](#constant-data-dictionary)](#constant-data-dictionary)

[3.1 Program (fixed) Constants
[6](#program-fixed-constants)](#program-fixed-constants)

[3.1.1 Embedded Constants [6](#embedded-constants)](#embedded-constants)

[4 Software Component Implementation
[7](#software-component-implementation)](#software-component-implementation)

[4.1 Sub-Module Functions
[7](#sub-module-functions)](#sub-module-functions)

[4.1.1 Per: BattVltgPer1 [7](#per-battvltgper1)](#per-battvltgper1)

[4.1.1.1 Design Rationale [7](#design-rationale)](#design-rationale)

[4.1.1.2 Store Module Inputs to Local copies
[7](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[4.1.1.3 (Processing of function)………
[7](#processing-of-function)](#processing-of-function)

[4.1.1.4 Store Local copy of outputs into Module Outputs
[7](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[4.2 Server Runables [7](#server-runnables)](#server-runnables)

[4.3 Interrupt Functions
[7](#interrupt-functions)](#interrupt-functions)

[4.4 Module Internal (Local) Functions
[7](#module-internal-local-functions)](#module-internal-local-functions)

[4.5 GLOBAL Function/Macro Definitions
[7](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[5 Known Limitations with Design
[8](#known-limitations-with-design)](#known-limitations-with-design)

[6 UNIT TEST CONSIDERATION
[9](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[10](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [11](#glossary)](#glossary)

[Appendix C References [12](#references)](#references)

# BattVltg High-Level Description

*Refer FDD*

# Design details of software module

## Graphical representation of BattVltg

## Data Flow Diagram

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/ES250B_BattVltg_Impl/doc/mediax/media/image2.png"
style="width:2.94192in;height:2.00017in" /> Refer FDD

### Component level DFD

Refer FDD

### Function level DFD

Refer FDD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name                     | Units | Value |
|-----------------------------------|-------|-------|
|                                   |       |       |
|                                   |       |       |
|                                   |       |       |
| Refer .m file for other constants |       |       |

# Software Component Implementation

## Sub-Module Functions

## Per: BattVltgPer1

## Design Rationale

Refer FDD

## Store Module Inputs to Local copies

##  (Processing of function)………

## Store Local copy of outputs into Module Outputs

## Server Runnables 

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

####### Abbreviations and Acronyms

| **Abbreviation or Acronym** | **Description**        |
|-----------------------------|------------------------|
| MDD                         | Module Design Document |
| DFD                         | Data Flow Diagram      |

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

|     |     |     |
|-----|-----|-----|
|     |     |     |
|     |     |     |

####### References

| **Ref. \#** | **Title**                                                                                                                                                               | **Version**                    |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping                                                                                                                                 | v1.3.0 R4.0 Rev 2              |
| 2           | MDD Guideline                                                                                                                                                           | EA4 01.00.00                   |
| 3           | EA4 [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc) | 01.00.00                       |
| 4           | Software Design and Coding Standards                                                                                                                                    | 2.1                            |
| 5           | ES250B_BattVltg_Design                                                                                                                                                  | See Synergy subproject version |

{% endraw %}