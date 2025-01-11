---
layout: default
title: PolarityCfg_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**‘PolarityCfg’**

**VERSION: 3.0**

**DATE:** **07-Jul-2017**

**Prepared By:**

**Shawn Penning,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**  
Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                                                    |                        |             |             |
|------|----------------------|----------------------|----------|-------------|
| **Sl. No.** | **Description**                                    | **Author**             | **Version** | **Date**    |
| 1           | Initial Version                                    | Sankardu Varadapureddi | 1.0         | 26-May-2015 |
| 3           | Corrections to Name and Graphic, Update MDD Layout | Shawn Penning          | 3.0         | 07-Jul-2017 |
|             |                                                    |                        |             |             |
|             |                                                    |                        |             |             |
|             |                                                    |                        |             |             |

**<u>  
Table of Contents</u>**

1 Polarity Configuration High-Level Description 6

2 Design details of software module 7

2.1 Graphical representation of Polarity Configuration 7

2.2 Data Flow Diagram 7

2.2.1 Module level DFD 7

2.2.2 Sub-Module level DFD 7

2.3 COMPONENT FLOW DIAGRAM 8

3 Variable Data Dictionary 9

3.1 User defined typedef definition/declaration 9

3.2 Variable definition for enumerated types 9

4 Constant Data Dictionary 10

4.1 Program(fixed) Constants 10

4.1.1 Embedded Constants 10

4.1.1.1 Local 10

4.1.1.2 Global 10

4.1.2 Module specific Lookup Tables Constants 10

5 Software Module Implementation 11

5.1 Sub-Module Functions 11

5.1.1 Initialization Functions 11

5.1.1.1 INIT: PolarityCfgInit 11

5.1.1.1.1 Design Rationale 11

5.1.1.1.2 Module Outputs 11

5.1.1.1.3 Module Internal 11

5.1.2 PERIODIC FUNCTIONS 11

5.1.3 Interrupt Functions 11

5.1.4 Server runnables 12

5.1.4.1 PolarityCfgRead 12

5.1.4.1.1 Design Rationale 12

5.1.4.1.2 Store Module Inputs to Local copies 12

5.1.4.1.3 (Processing of function)……… 12

5.1.4.1.4 Store Local copy of outputs into Module Outputs 12

5.1.4.2 PolarityCfgWr 12

5.1.4.2.1 Design Rationale 12

5.1.4.2.2 Store Module Inputs to Local copies 12

5.1.4.2.3 (Processing of function)……… 12

5.1.4.2.4 Store Local copy of outputs into Module Outputs 12

5.1.5 Local Function/Macro Definitions 12

5.1.5.1 Local Function \#1 12

5.1.5.2 Description 12

5.1.6 GLObAL Function/Macro Definitions 13

5.1.7 Transition FUNCTIONS 13

6 Known Limitations With Design 14

7 UNIT TEST CONSIDERATION 15

Appendix A Abbreviations and Acronyms 16

Appendix B Glossary 17

Appendix C References 18

#  [section]

|     |     |
|-----|-----|
|     |     |
|     |     |
|     |     |

#  [section-1]

This section lists the title & version of all the documents that are
referred for development of this document

|     |     |     |
|-----|-----|-----|
|     |     |     |
|     |     |     |
|     |     |     |
|     |     |     |
|     |     |     |

# Polarity Configuration High-Level Description

*This function will identify polarity control settings for certain
points in the design.*

# Design details of software module

## Graphical representation of Polarity Configuration

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/ES102A_PolarityCfg_Impl/doc/mediax/media/image1.png"
style="width:2.78125in;height:6.29167in" /><img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/ES102A_PolarityCfg_Impl/doc/mediax/media/image2.png"
style="width:2.39167in;height:4.925in" />

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

*\<This section documents any user types uniquely used for the
module.\>*

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
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

## Variable definition for enumerated types

| Enum Name | Element Name | Value |
|-----------|--------------|-------|
| None      |              |       |

# Constant Data Dictionary

## Program(fixed) Constants

## Embedded Constants

## Local 

| Constant Name          | Resolution    | Units | Value       |
|------------------------|---------------|-------|-------------|
| HWAG0POL_CNT_U32       | Bitfield Mask | NA    | 0x00000001U |
| HWAG1POL_CNT_U32       | Bitfield Mask | NA    | 0x00000002U |
| HWAG2POL_CNT_U32       | Bitfield Mask | NA    | 0x00000004U |
| HWAG3POL_CNT_U32       | Bitfield Mask | NA    | 0x00000008U |
| HWAG4POL_CNT_U32       | Bitfield Mask | NA    | 0x00000010U |
| HWAG5POL_CNT_U32       | Bitfield Mask | NA    | 0x00000020U |
| HWAG6POL_CNT_U32       | Bitfield Mask | NA    | 0x00000040U |
| HWAG7POL_CNT_U32       | Bitfield Mask | NA    | 0x00000080U |
| HWTQ0POL_CNT_U32       | Bitfield Mask | NA    | 0x00000100U |
| HWTQ1POL_CNT_U32       | Bitfield Mask | NA    | 0x00000200U |
| HWTQ2POL_CNT_U32       | Bitfield Mask | NA    | 0x00000400U |
| HWTQ3POL_CNT_U32       | Bitfield Mask | NA    | 0x00000800U |
| HWTQ4POL_CNT_U32       | Bitfield Mask | NA    | 0x00001000U |
| HWTQ5POL_CNT_U32       | Bitfield Mask | NA    | 0x00002000U |
| HWTQ6POL_CNT_U32       | Bitfield Mask | NA    | 0x00004000U |
| HWTQ7POL_CNT_U32       | Bitfield Mask | NA    | 0x00008000U |
| MOTAGMECL0POL_CNT_U32  | Bitfield Mask | NA    | 0x00010000U |
| MOTAGMECL1POL_CNT_U32  | Bitfield Mask | NA    | 0x00020000U |
| MOTAGMECL2POL_CNT_U32  | Bitfield Mask | NA    | 0x00040000U |
| MOTAGMECL3POL_CNT_U32  | Bitfield Mask | NA    | 0x00080000U |
| MOTAGMECL4POL_CNT_U32  | Bitfield Mask | NA    | 0x00100000U |
| MOTAGMECL5POL_CNT_U32  | Bitfield Mask | NA    | 0x00200000U |
| MOTAGMECL6POL_CNT_U32  | Bitfield Mask | NA    | 0x00400000U |
| MOTAGMECL7POL_CNT_U32  | Bitfield Mask | NA    | 0x00800000U |
| MOTELECMECLPOL_CNT_U32 | Bitfield Mask | NA    | 0x01000000U |
| ASSIMECHPOL_CNT_U32    | Bitfield Mask | NA    | 0x02000000U |

## Global

| Constant Name |
|---------------|
|               |

## Module specific Lookup Tables Constants

| Constant Name | Resolution | Value | Software Segment |
|---------------|------------|-------|------------------|
| None          |            |       |                  |

# Software Module Implementation

## Sub-Module Functions 

## Initialization Functions

*PolarityCfgInit*

## INIT: PolarityCfgInit

## Design Rationale

*Design follows implemenetation in FDD.*

## Module Outputs

*Refer ‘PolarityCfgInit’ block in FDD*

## Module Internal 

None

## PERIODIC FUNCTIONS 

None

## Interrupt Functions

*None*

##  Server runnables

##  PolarityCfgRead

## Design Rationale

*None*

## Store Module Inputs to Local copies

*None*

## (Processing of function)………

*Refer ‘PolarityCfgRead’ block in FDD*

## Store Local copy of outputs into Module Outputs

*None*

## PolarityCfgWr

## Design Rationale

*None*

## Store Module Inputs to Local copies

*None*

## (Processing of function)………

*Refer* ‘*PolarityCfgWr’ block in FDD*

## Store Local copy of outputs into Module Outputs

*None*

## Local Function/Macro Definitions

## Local Function \#1

|                      |                        |        |            |            |
|---------------|-------------------------|----------|---------------|---------|
| **Function Name**    | GetPolarity            | Type   | Min        | Max        |
| **Arguments Passed** | Polarity_Cnt_T_u32     | uint32 | 0          | 0xFFFFFFFF |
|                      | PolarityMask_Cnt_T_u32 | uint32 | 0x00000001 | 0x02000000 |
| **Return Value**     | Polarity_Cnt_T_s08     | sint08 | -1         | 1          |

## Description

-   **Design:**

if ( (Polarity_Cnt_T_u32 & PolarityMask_Cnt_T_u32) ==
PolarityMask_Cnt_T_u32 )

set ‘Polarity_Cnt_T_s08’ to ‘1’

else

set ‘Polarity_Cnt_T_s08’ to ‘-1’

-   **Note:** ‘PolarityMask_Cnt_T_u32’ is a bit field mask and takes
    values mentioned in table at sec 6.1.1.1

## GLObAL Function/Macro Definitions

None

## Transition FUNCTIONS 

None

# Known Limitations With Design

None

# UNIT TEST CONSIDERATION

None

# Appendix A Abbreviations and Acronyms [appendix-a-abbreviations-and-acronyms]

| Abbreviation | Description                |
|--------------|----------------------------|
| DFD          | Design functional diagram  |
| MDD          | Module design Document     |
| FDD          | Functional Design Document |

# Appendix B Glossary [appendix-b-glossary]

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

# Appendix C References [appendix-c-references]

| **Ref. \#** | **Title**                                | **Version**                     |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping  | v1.3.0 R4.0 Rev 2               |
| 2           | MDD Guideline                            | EA4 01.00.01                    |
| 3           | Software Naming Conventions.doc          | EA4 01.00.00                    |
| 4           | Software Design and Coding Standards.doc | 2.1                             |
| 5           | FDD : ES102A_PolarityCfg_Design          | See Synergy sub project version |

#  [section-2]

#  [section-3]

{% endraw %}