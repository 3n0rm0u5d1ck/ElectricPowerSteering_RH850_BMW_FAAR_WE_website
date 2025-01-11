---
layout: default
title: MotVel_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**‘MotVel’**

**VERSION: 2.0**

**DATE:** **25-Jul-2017**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Shawn Penning**

**Saginaw, MI**

**  
Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                               |               |             |               |
|-----|-------------------------------|----------------|----------|-----------|
| **Sl. No.** | **Description**               | **Author**    | **Version** | **Date**      |
| 1           | Initial Version               | Rijvi Ahmed   | 1.0         | 12-April-2016 |
| 2           | Updated per design rev. 2.0.0 | TATA          | 2.0         | 18-Nov-2016   |
| 3           | Updated per design rev. 2.1.0 | Shawn Penning | 3.0         | 25-Jul-2017   |

**<u>  
Table of Contents</u>**

[1 Abbrevations And Acronyms
[5](#abbrevations-and-acronyms)](#abbrevations-and-acronyms)

[2 References [6](#references)](#references)

[3 MotVel & High-Level Description
[7](#motvel-high-level-description)](#motvel-high-level-description)

[4 Design details of software module
[8](#design-details-of-software-module)](#design-details-of-software-module)

[4.1 Graphical representation OF MotVel
[8](#graphical-representation-of-motvel)](#graphical-representation-of-motvel)

[4.2 Data Flow Diagram [8](#data-flow-diagram)](#data-flow-diagram)

[4.2.1 Module level DFD [8](#module-level-dfd)](#module-level-dfd)

[4.2.2 Sub-Module level DFD
[8](#sub-module-level-dfd)](#sub-module-level-dfd)

[4.3 COMPONENT FLOW DIAGRAM
[8](#component-flow-diagram)](#component-flow-diagram)

[5 Variable Data Dictionary
[9](#variable-data-dictionary)](#variable-data-dictionary)

[5.1 User defined typedef definition/declaration
[9](#user-defined-typedef-definitiondeclaration)](#user-defined-typedef-definitiondeclaration)

[5.2 Variable definition for enumerated types
[9](#variable-definition-for-enumerated-types)](#variable-definition-for-enumerated-types)

[6 Constant Data Dictionary
[10](#constant-data-dictionary)](#constant-data-dictionary)

[6.1 Program(fixed) Constants
[10](#programfixed-constants)](#programfixed-constants)

[6.1.1 Embedded Constants
[10](#embedded-constants)](#embedded-constants)

[6.1.1.1 Local [10](#local)](#local)

[6.1.2 Module specific Lookup Tables Constants
[10](#module-specific-lookup-tables-constants)](#module-specific-lookup-tables-constants)

[7 Software Module Implementation
[11](#software-module-implementation)](#software-module-implementation)

[7.1 Sub-Module Functions
[11](#sub-module-functions)](#sub-module-functions)

[7.1.1 Initialization Functions
[11](#initialization-functions)](#initialization-functions)

[7.1.2 PERIODIC FUNCTIONS
[11](#periodic-functions)](#periodic-functions)

[7.1.2.1 INIT: MotVelPER1 [11](#init-motvelper1)](#init-motvelper1)

[7.1.2.1.1 Design Rationale [11](#_Toc467233508)](#_Toc467233508)

[7.1.2.2 Design Rationale [11](#design-rationale)](#design-rationale)

[7.1.2.3 Store Module Inputs to Local copies
[11](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[7.1.2.4 (Processing of function)………
[11](#processing-of-function)](#processing-of-function)

[7.1.2.5 Store Local copy of outputs into Module Outputs
[11](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[7.1.3 PERIODIC FUNCTIONS
[11](#periodic-functions-1)](#periodic-functions-1)

[7.1.3.1 INIT: MotVelPER2 [11](#init-motvelper2)](#init-motvelper2)

[7.1.3.1.1 Design Rationale [11](#_Toc467233515)](#_Toc467233515)

[7.1.3.2 Design Rationale
[11](#design-rationale-1)](#design-rationale-1)

[7.1.3.3 Store Module Inputs to Local copies
[11](#store-module-inputs-to-local-copies-1)](#store-module-inputs-to-local-copies-1)

[7.1.3.4 (Processing of function)………
[11](#processing-of-function-1)](#processing-of-function-1)

[7.1.3.5 Store Local copy of outputs into Module Outputs
[11](#store-local-copy-of-outputs-into-module-outputs-1)](#store-local-copy-of-outputs-into-module-outputs-1)

[7.1.4 Interrupt Functions
[12](#interrupt-functions)](#interrupt-functions)

[Server runnables [12](#server-runnables)](#server-runnables)

[7.1.4.1.1 Store Local copy of outputs into Module Outputs
[12](#store-local-copy-of-outputs-into-module-outputs-2)](#store-local-copy-of-outputs-into-module-outputs-2)

[7.1.4.2 Local Function/Macro Definitions
[12](#local-functionmacro-definitions)](#local-functionmacro-definitions)

[7.1.5 GLObAL Function/Macro Definitions
[12](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[7.1.6 Tranisition FUNCTIONS
[12](#tranisition-functions)](#tranisition-functions)

[8 Known Limitations With Design
[13](#known-limitations-with-design)](#known-limitations-with-design)

[9 UNIT TEST CONSIDERATION
[14](#unit-test-consideration)](#unit-test-consideration)

[10 Appendix [15](#appendix)](#appendix)

# Abbrevations And Acronyms

| Abbreviation | Description                |
|--------------|----------------------------|
| DFD          | Design functional diagram  |
| MDD          | Module design Document     |
| FDD          | Functional Design Document |

# References

This section lists the title & version of all the documents that are
referred for development of this document

| Sr. No. | Title                                | Version                         |
|----------|----------------------------------------------|-----------------|
| 1       | MDD Guidelines                       | Process 04.02.01                |
| 2       | Software Naming Conventions          | Process 04.02.01                |
| 3       | Software Design and Coding standards | Process 04.02.01                |
| 4       | FDD : SF40A_MotVel_Design            | See Synergy sub project version |

# MotVel & High-Level Description

Please refer FDD.

# Design details of software module

## Graphical representation OF MotVel

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/SF040A_MotVel_Impl/doc/mediax/media/image1.png"
style="width:2.9375in;height:3.14583in" />

## Data Flow Diagram

*Refer FDD*

## Module level DFD

*Refer FDD*

## Sub-Module level DFD

*Refer FDD*

## COMPONENT FLOW DIAGRAM

*Refer FDD*

# Variable Data Dictionary

## User defined typedef definition/declaration 

<table>
<colgroup>
<col style="width: 34%" />
<col style="width: 31%" />
<col style="width: 11%" />
<col style="width: 11%" />
<col style="width: 11%" />
</colgroup>
<thead>
<tr class="header">
<th>Typedef Name</th>
<th>Element Name</th>
<th>User Defined Type</th>
<th><p>Legal Range</p>
<p>(min)</p></th>
<th><p>Legal Range</p>
<p>(max)</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>None</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
</tr>
</tbody>
</table>

## Variable definition for enumerated types

| Enum Name | Element Name | Value |
|-----------|--------------|-------|
| None      | N/A          | N/A   |

# Constant Data Dictionary

## Program(fixed) Constants

## Embedded Constants

## Local 

| Constant Name     | Resolution | Units | Value |
|-------------------|------------|-------|-------|
| Refer the m files |            |       |       |

**6.1.1.2 Global**

| Constant Name |
|---------------|
| N/A           |

## Module specific Lookup Tables Constants

| Constant Name | Resolution | Value | Software Segment |
|---------------|------------|-------|------------------|
| None          | N/A        | N/A   | N/A              |

# Software Module Implementation

## Sub-Module Functions 

## Initialization Functions

*None*

## PERIODIC FUNCTIONS 

## INIT: MotVelPER1

## Design Rationale

*None*

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD*

## Store Local copy of outputs into Module Outputs

*Refer to FDD*

##  [section]

## PERIODIC FUNCTIONS 

## INIT: MotVelPER2

## Design Rationale

*None*

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD*

## Store Local copy of outputs into Module Outputs

*Refer to FDD*

## Interrupt Functions

*None*

## Server runnables [server-runnables]

*None*

## Store Local copy of outputs into Module Outputs

*None*

## Local Function/Macro Definitions

*None*

## GLObAL Function/Macro Definitions

None

## Tranisition FUNCTIONS 

None

# Known Limitations With Design

1.  

2.  

3.  Per-Instance Memory variables in Design 2.1, MotAgBufIdxPrev and
    MotAgBufIdxPrim, are set with range of 0 to 255, but are index
    variables for an array of only 8 elements. Design to be corrected in
    the next version as follows: the Max Value for both PIM’s to be 7
    instead of 255 (range 0..7 instead of 0..255).

# UNIT TEST CONSIDERATION

> Per-Instance Memory variables in Design 2.1, MotAgBufIdxPrev and
> MotAgBufIdxPrim, are set with range of 0 to 255, but are index
> variables for an array of only 8 elements. Design to be corrected in
> the next version as follows: the Max Value for both PIM’s to be 7
> instead of 255 (range 0..7 instead of 0..255).

# Appendix

*None*

{% endraw %}