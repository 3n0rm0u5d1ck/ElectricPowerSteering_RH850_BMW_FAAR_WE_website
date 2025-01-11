---
layout: default
title: MotRefMdl_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**MotRefMdl**

**VERSION:** **6.0**

**DATE: 15-Nov-2017**

**Prepared By:**

**Krishna Anne,**

**Software Component Group**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                                         |            |             |             |
|------|-----------------------------------|------------|----------|------------|
| **Sl. No.** | **Description**                         | **Author** | **Version** | **Date**    |
| 1           | Initial Version                         | Selva      | 1.0         | 12-JUN-2015 |
| 2           | Updated per design rev. 1.2.0           | Rijvi      | 2.0         | 13-Mar-2016 |
| 3           | Updated as per v1.3.0 of FDD            | Krishna    | 3.0         | 29-Apr-16   |
| 4\.         | Updated as per v2.3.0 of FDD            | Krishna    | 4.0         | 15-Nov-2016 |
| 5\.         | Updated as per v4.0.0 of FDD            | TATA       | 5.0         | 25-Sep-2017 |
| 6\.         | Fixed Design vs Implementation Mismatch | Krishna    | 6.0         | 15-Nov-2017 |

Table of Contents

[1 Abbrevations And Acronyms 5](#abbrevations-and-acronyms)

[2 References 6](#references)

[3 MotRefMdl & High-Level Description
7](#motrefmdl-high-level-description)

[4 Design details of software module
8](#design-details-of-software-module)

[4.1 Graphical representation of MotRefMdl
8](#graphical-representation-of-motrefmdl)

[4.2 Data Flow Diagram 8](#data-flow-diagram)

[4.2.1 Module level DFD 8](#module-level-dfd)

[4.2.2 Sub-Module level DFD 8](#sub-module-level-dfd)

[4.3 COMPONENT FLOW DIAGRAM 8](#component-flow-diagram)

[5 Variable Data Dictionary 9](#variable-data-dictionary)

[5.1 User defined typedef definition/declaration
9](#user-defined-typedef-definitiondeclaration)

[5.2 Variable definition for enumerated types
9](#variable-definition-for-enumerated-types)

[6 Constant Data Dictionary 10](#constant-data-dictionary)

[6.1 Program(fixed) Constants 10](#programfixed-constants)

[6.1.1 Embedded Constants 10](#embedded-constants)

[6.1.1.1 Local 10](#local)

[6.1.1.2 Global 10](#global)

[6.1.2 Module specific Lookup Tables Constants
10](#module-specific-lookup-tables-constants)

[7 Software Module Implementation 11](#software-module-implementation)

[7.1 Sub-Module Functions 11](#sub-module-functions)

[7.2 Initialization Functions 11](#initialization-functions)

[7.2.1 Per: MotRefMdlINIT1 11](#per-motrefmdlinit1)

[7.2.1.1 Design Rationale 11](#design-rationale)

[7.2.1.2 Store Module Inputs to Local copies
11](#store-module-inputs-to-local-copies)

[7.2.1.3 (Processing of function)……… 11](#processing-of-function)

[7.2.1.4 Store Local copy of outputs into Module Outputs
11](#store-local-copy-of-outputs-into-module-outputs)

[7.3 PERIODIC FUNCTIONS 11](#periodic-functions)

[7.3.1 Per: MotRefMdlper1 11](#per-motrefmdlper1)

[7.3.1.1 Design Rationale 11](#design-rationale-1)

[7.3.1.2 Store Module Inputs to Local copies
11](#store-module-inputs-to-local-copies-1)

[7.3.1.3 (Processing of function)……… 11](#processing-of-function-1)

[7.3.1.4 Store Local copy of outputs into Module Outputs
11](#store-local-copy-of-outputs-into-module-outputs-1)

[7.4 Non PERIODIC FUNCTIONS 11](#non-periodic-functions)

[7.5 Interrupt Functions 11](#__RefHeading___Toc494125579)

[7.6 Serial Communication Functions 12](#serial-communication-functions)

[7.7 Local Function/Macro Definitions
12](#local-functionmacro-definitions)

[7.7.1 Local Function \#1 CalcCurrMagSqRef
12](#local-function-1-calccurrmagsqref)

[7.7.1.1 Description 12](#description)

[7.7.2 Local Function \#2 CalcIq 12](#local-function-2-calciq)

[7.7.2.1 Description 12](#description-1)

[7.7.3 Local Function \#3 CurrtoVoltTest
12](#local-function-3-currtovolttest)

[7.7.3.1 Description 12](#description-2)

[7.7.4 Local Function \#4 CalcMinMotCurr
12](#local-function-4-calcminmotcurr)

[7.7.4.1 Description 13](#description-3)

[7.7.5 Local Function \#5 CalcTq 13](#local-function-5-calctq)

[7.7.5.1 Description 13](#description-4)

[7.7.6 Local Function \#6 CalcMaxTqPt 13](#local-function-6-calcmaxtqpt)

[7.7.6.1 Description 13](#description-5)

[7.7.7 Local Function \#7 PrbcIntrpn 13](#local-function-7-prbcintrpn)

[7.7.7.1 Description 13](#description-6)

[7.7.8 Local Function \#7 PrbcIntrpn 13](#local-function-8-decoder)

[7.7.8.1 Description 14](#description-7)

[7.8 GLObAL Function/Macro Definitions
14](#global-functionmacro-definitions)

[7.9 TRANSIENT FUNCTIONS 14](#transient-functions)

[8 Unit Test Considerations 15](#unit-test-considerations)

[9 Known Limitations With Design 16](#known-limitations-with-design)

[10 Appendix 17](#appendix)

# Abbrevations And Acronyms

|              |                           |
|--------------|---------------------------|
| Abbreviation | Description               |
| DFD          | Design functional diagram |
| MDD          | Module design Document    |

# References

This section lists the title & version of all the documents that are
referred for development of this document

|         |                                 |                                |
|---------|---------------------------------|--------------------------------|
| Sr. No. | Title                           | Version                        |
| \<1\>   | \<MDD Guidelines\>              | Process 04.02.01               |
| \<2\>   | \<Software Naming Conventions\> | Process 04.02.01               |
| \<3\>   | \<Coding standards\>            | Process 04.02.01               |
| \<4\>   | FDD - SF103A_MotRefMdl_Design   | See Synergy Subproject version |
|         | \<Add if more available\>       |                                |

# MotRefMdl & High-Level Description

# Design details of software module

## Graphical representation of MotRefMdl

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/SF103A_MotRefMdl_Impl/doc/mediax/media/image1.png"
style="width:3.14583in;height:5.625in" />

## Data Flow Diagram

## Module level DFD

## Sub-Module level DFD

## COMPONENT FLOW DIAGRAM

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
<tbody>
<tr class="odd">
<td>Typedef Name</td>
<td>Element Name</td>
<td>User Defined Type</td>
<td><p>Legal Range</p>
<p>(min)</p></td>
<td><p>Legal Range</p>
<p>(max)</p></td>
</tr>
<tr class="even">
<td>MotInterCalcnsRec</td>
<td>RelncTqCoeff_Henry_f32</td>
<td>Single Precision float</td>
<td>3e-05</td>
<td>0.00041</td>
</tr>
<tr class="odd">
<td></td>
<td>MotREstimd_Ohm_f32</td>
<td>Single Precision float</td>
<td>0.005</td>
<td>0.12565</td>
</tr>
<tr class="even">
<td></td>
<td>ReacncDaxOverR_Uls_f32</td>
<td>Single Precision float</td>
<td>-14.4436</td>
<td>+14.4436</td>
</tr>
<tr class="odd">
<td></td>
<td>ReacncQaxOverR_Uls_f32</td>
<td>Single Precision float</td>
<td>-14.4436</td>
<td>+14.4436</td>
</tr>
<tr class="even">
<td></td>
<td>EgOverR_Ampr_f32</td>
<td>Single Precision float</td>
<td>-200</td>
<td>200</td>
</tr>
<tr class="odd">
<td></td>
<td>VltgOverR_Ampr_f32</td>
<td>Single Precision float</td>
<td>-200</td>
<td>200</td>
</tr>
<tr class="even">
<td></td>
<td>VovrRAllSqd_AmprSqd_f32</td>
<td>Single Precision float</td>
<td>0</td>
<td>40000</td>
</tr>
<tr class="odd">
<td></td>
<td>EgOverROverZ_Ampr_f32</td>
<td>Single Precision float</td>
<td>-200</td>
<td>200</td>
</tr>
<tr class="even">
<td></td>
<td>VovrRovrZ_Ampr_f32</td>
<td>Single Precision float</td>
<td>-200</td>
<td>200</td>
</tr>
<tr class="odd">
<td></td>
<td>MotKeEstimd_VoltPerMotRadPerSec_f32</td>
<td>Single Precision float</td>
<td>.025</td>
<td>.075</td>
</tr>
</tbody>
</table>

## Variable definition for enumerated types

|           |                                          |                       |
|--------------------------------|-----------------------------|------------|
| Enum Name | Element Name                             | Value                 |
| N/A       | \<(Variable name qualified Refer\[2\])\> | \<Define the value \> |

# Constant Data Dictionary

## Program(fixed) Constants

## Embedded Constants

## Local

|                              |                        |       |        |
|------------------------------|------------------------|-------|--------|
| Constant Name                | Resolution             | Units | Value  |
| MOTVLTGDAXEFLOLIM_VOLT_F32   | Single precision float | Volt  | -26.5F |
| MOTVLTGDAXEFHILIM_VOLT_F32   | Single precision float | Volt  | 26.5F  |
| MOTVLTGQAXEFLOLIM_VOLT_F32   | Single precision float | Volt  | -26.5F |
| MOTVLTGQAXEFHILIM_VOLT_F32   | Single precision float | Volt  | 26.5F  |
| BITMASK1_CNT_U08             | 1                      | Cnt   | 1U     |
| BITMASK2_CNT_U08             | 1                      | Cnt   | 2U     |
| BITMASK4_CNT_U08             | 1                      | Cnt   | 4U     |
| Refer constants from .m file |                        |       |        |

## Global

|                              |
|------------------------------|
| Constant Name                |
| Refer constants from .m file |
|                              |
|                              |

## Module specific Lookup Tables Constants

|               |            |       |                  |
|---------------|------------|-------|------------------|
| Constant Name | Resolution | Value | Software Segment |
| Refer .m file |            |       |                  |

# Software Module Implementation

## Sub-Module Functions

*NONE*

## Initialization Functions

## Per: MotRefMdlINIT1

## Design Rationale

*Refer to FDD*

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD*

##  Store Local copy of outputs into Module Outputs

*Refer to FDD*

## PERIODIC FUNCTIONS 

## Per: MotRefMdlper1

## Design Rationale

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD*

##  Store Local copy of outputs into Module Outputs

*Refer to FDD*

## Non PERIODIC FUNCTIONS 

*None*

## Interrupt Functions

*None*

## Serial Communication Functions

*None*

## Local Function/Macro Definitions

## Local Function \#1 CalcCurrMagSqRef

|                      |                           |         |      |       |
|----------------------|---------------------------|---------|------|-------|
| **Function Name**    | CalcCurrMagSqRef          | Type    | Min  | Max   |
| **Arguments Passed** | CurrDaxRef_Ampr_T_f32     | float32 | -200 | 200   |
|                      | CurrQaxRef_Ampr_T_f32     | float32 | -200 | 200   |
| **Return Value**     | CurrMagSqRef_AmprSq_T_f32 | float32 | 0    | 40000 |

## Description

Refer FDD (F_CalcIqCommand)

## Local Function \#2 CalcIq

|                      |                            |         |                                   |                                   |
|--------------|------------------------------|---------|-----------|-----------|
| **Function Name**    | CalcIq                     | Type    | Min                               | Max                               |
| **Arguments Passed** | Tqcmd_MotNwtMtr_T_f32      | float32 | -8.8                              | 8.8                               |
|                      | CurrDaxRef_Ampr_T_f32      | float32 | -200                              | 200                               |
|                      | MotRefMdlInterCalcns_T_str | struct  | Refer Struct Definition in Sec5.1 | Refer Struct Definition in Sec5.1 |
| **Return Value**     | CurrQaxRefTmp_Ampr_T_f32   | float32 | -200                              | 200                               |

## Description

Refer FDD (F_CalcIqCommand)

## Local Function \#3 CurrtoVoltTest

|                      |                            |         |                                   |                                   |
|--------------|------------------------------|---------|-----------|-----------|
| **Function Name**    | CalcIq                     | Type    | Min                               | Max                               |
| **Arguments Passed** | CurrQaxRef_Ampr_T_f32      | float32 | -8.8                              | 8.8                               |
|                      | CurrDaxRef_Ampr_T_f32      | float32 | -200                              | 200                               |
|                      | MotRefMdlInterCalcns_T_str | struct  | Refer Struct Definition in Sec5.1 | Refer Struct Definition in Sec5.1 |
| **Return Value**     | VdR_Ampr_T_f32             | float32 | -200                              | 200                               |
|                      | VqR_Ampr_T_f32             | float32 | -200                              | 200                               |
|                      | CurrQaxRefTmp_Ampr_T_f32   | float32 | -200                              | 200                               |

## Description

Refer FDD ( F_ItoV)

## Local Function \#4 CalcMinMotCurr

|                      |                            |         |                                   |                                   |
|--------------|------------------------------|---------|------------|---------|
| **Function Name**    | CalcMinMotCurr             | Type    | Min                               | Max                               |
| **Arguments Passed** | MotTqCmd_MotNwtMtr_T_f32   | float32 | -8.8                              | 8.8                               |
|                      | MotRefMdlInterCalcns_T_str | struct  | Refer Struct Definition in Sec5.1 | Refer Struct Definition in Sec5.1 |
| **Return Value**     | CurrQaxMin_Ampr_T_f32      | float32 | -200                              | 200                               |
|                      | CurrDaxMin_Ampr_T_f32      | float32 | -200                              | 200                               |
|                      | ImSqrMin_AmprSq_T_f32      | float32 | 0                                 | 40000                             |

## Description

Refer FDD (Locate Reference)

## Local Function \#5 CalcTq

|                      |                            |         |                                   |                                   |
|--------------|------------------------------|---------|-----------|-----------|
| **Function Name**    | CalcTq                     | Type    | Min                               | Max                               |
| **Arguments Passed** | CosDelta_Cnt_T_f32         | float32 | -1                                | 1                                 |
|                      | SinDelta_Cnt_T_f32         | float32 | -1                                | 1                                 |
|                      | MotRefMdlInterCalcns_T_str | struct  | Refer Struct Definition in Sec5.1 | Refer Struct Definition in Sec5.1 |
| **Return Value**     | TqCalc_MotNwtMtr_T_f32     | float32 | -8.8                              | 8.8                               |
|                      | CurrDaxMax_Ampr_T_f32      | float32 | -200                              | 200                               |

## Description

Refer FDD (CalculateTorque)

## Local Function \#6 CalcMaxTqPt

|                      |                              |         |                                   |                                   |
|--------------|------------------------------|---------|-----------|-----------|
| **Function Name**    | CalcMaxTqPt                  | Type    | Min                               | Max                               |
| **Arguments Passed** | MotTqCmd_MotNwtMtr_T_f32     | float32 | -8.8                              | 8.8                               |
|                      | MotRefMdlInterCalcns_T_str   | struct  | Refer Struct Definition in Sec5.1 | Refer Struct Definition in Sec5.1 |
| **Return Value**     | MotTqCmdLimd_MotNwtMtr_T_f32 | float32 | -8.8                              | 8.8                               |
|                      | CurrDaxMax_Ampr_T_f32        | float32 | -200                              | 200                               |

## Description

Refer FDD (LocateTorqueExtremes)

## Local Function \#7 PrbcIntrpn

|                      |                      |         |            |            |
|--------------|------------------------------|---------|-----------|-----------|
| **Function Name**    | PrbcIntrpn           | Type    | Min        | Max        |
| **Arguments Passed** | IntrpnPts_T_f32      | float32 | Full range | Full range |
| **Return Value**     | ParaIntpol_Uls_T_f32 | float32 | Full range | Full range |
|                      |                      |         |            |            |

## Description

Refer FDD ( Parabolic Interpolations)

## Local Function \#8 Decoder

|                      |                                  |         |       |      |
|--------------|------------------------------|---------|-----------|-----------|
| **Function Name**    | Decoder                          | Type    | Min   | Max  |
| **Arguments Passed** | MotAndThermProtnLoaMod_Cnt_T_u08 | Uin8    | 0     | 255  |
| **Return Value**     | CurrMeasLoaMtgtnEna_Cnt_T_logl   | Boolean | FALSE | TRUE |
|                      | IvtrLoaMtgtnEna_Cnt_T_logl       | Boolean | FALSE | TRUE |
|                      | FetLoaMtgtnEna_Cnt_T_logl        | Boolean | FALSE | TRUE |

## Description

Refer FDD ( Decoder)

## Local Function \#9 VltgSdlCalc

|                      |                                        |          |      |       |
|--------------|------------------------------|---------|-----------|-----------|
| **Function Name**    | VltgSdlCalc                            | Type     | Min  | Max   |
| **Arguments Passed** | MotQuad_Cnt_T_enum                     | MotQuad1 | 1U   | 4U    |
|                      | AbsltMotVelFiltLp_MotRadPerSec_T_u11p5 | uint16   | 0U   | 1350U |
| **Return Value**     | VltgSdl_Volt_T_f32                     | Boolean  | 0.0F | 40.0F |

## Description

This function is split from Per1 to reduce the path count to less than
300.

## GLObAL Function/Macro Definitions

None

## TRANSIENT FUNCTIONS 

None

# Unit Test Considerations

None

# Known Limitations With Design

None

# Appendix

*None*

{% endraw %}