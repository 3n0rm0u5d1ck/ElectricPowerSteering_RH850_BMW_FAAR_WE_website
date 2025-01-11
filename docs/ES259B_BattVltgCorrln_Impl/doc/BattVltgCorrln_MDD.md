---
layout: default
title: BattVltgCorrln_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**BattVltgCorrln**

**27-Jun-2017**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Brionna Spencer,**

**Nexteer Automotive,**

**<u>Saginaw, MI, USAChange</u>** History

|                                                                                                                                                                                                     |            |             |             |
|---------------------------------------------|----------|-------|-----------|
| **Description**                                                                                                                                                                                     | **Author** | **Version** | **Date**    |
| Initial Version                                                                                                                                                                                     | N. Saxton  | 1.0         | 7-Jun-2016  |
| Updated the graphical representation, added design rationale for BattVltgCorrlnPer1, and updated the documentation for modified local functions (i.e. DetInstCorrln, DetIdptSig, and DetCorrlnSts). | B. Spencer | 2.0         | 27-Jun-2017 |

**<u>Table of Contents</u>**

[1 BattVltgCorrln & High-Level Description
4](#battvltgcorrln-high-level-description)

[2 Design details of software module
5](#design-details-of-software-module)

[2.1 Graphical representation of BattVltgCorrln
5](#graphical-representation-of-battvltgcorrln)

[2.2 Data Flow Diagram 6](#data-flow-diagram)

[2.2.1 Component level DFD 6](#component-level-dfd)

[2.2.2 Function level DFD 6](#function-level-dfd)

[3 Constant Data Dictionary 7](#constant-data-dictionary)

[3.1 Program (fixed) Constants 7](#program-fixed-constants)

[3.1.1 Embedded Constants 7](#embedded-constants)

[4 Software Component Implementation
8](#software-component-implementation)

[4.1.1 Sub-Module Functions 8](#sub-module-functions)

[4.1.2 Interrupt Service Routines 8](#interrupt-service-routines)

[4.1.3 Server Runnable Functions 8](#server-runnable-functions)

[4.1.4 Module Internal (Local) Functions
8](#module-internal-local-functions)

[4.1.5 Transition Functions 10](#transition-functions)

[5 Known Limitations with Design 11](#known-limitations-with-design)

[6 UNIT TEST CONSIDERATION 12](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms 13](#abbreviations-and-acronyms)

[Appendix B Glossary 14](#glossary)

[Appendix C References 15](#references)

# BattVltgCorrln & High-Level Description

Refer FDD

# Design details of software module

## Graphical representation of BattVltgCorrln

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/ES259B_BattVltgCorrln_Impl/doc/mediax/media/image2.jpeg"
style="width:4.14167in;height:5.36875in" />

## Data Flow Diagram

### Component level DFD

N/A

### Function level DFD

N/A

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

|                            |            |       |       |
|----------------------------|------------|-------|-------|
| Constant Name              | Resolution | Units | Value |
| BATTVLTGIDPTSIGMIN_CNT_U08 | None       | Cnt   | 0     |
| BATTVLTGIDPTSIGMAX_CNT_U08 | None       | Cnt   | 2     |
|                            |            |       |       |

\* Refer FDD for other constant definition

# Software Component Implementation

### Sub-Module Functions

#### Initialization sub-module {\_Init()}

##### BattVltgCorrlnInit1

###### Design Rationale

Refer to FDD

###### Store module inputs to local copies

Refer to FDD

###### (Processing of function)……

Refer to FDD

###### Store local copy of outputs into module outputs

Refer FDD

#### Periodic sub-module {\_Per()}

##### BattVltgCorrlnPer1

###### Design Rationale

Refer to FDD

Note the BattAndSwdVltg**Passed** temporary variable in the FDD was
renamed to BattVltgAndSwd1**NotFailed** because the ‘no result’ case is
also considered in the logic.

###### Store module inputs to local copies

Refer to FDD

###### (Processing of function)……

Refer to FDD

###### Store local copy of outputs into module outputs

Refer FDD

### Interrupt Service Routines

None

### Server Runnable Functions

None

### Module Internal (Local) Functions

#### Local Function \#1

|                      |                                |          |               |               |
|-------------|------------------------------|--------|-----------|-----------|
| **Function Name**    | DetInstCorrln                  | Type     | Min           | Max           |
| **Arguments Passed** | BattVltg_Volt_T_f32            | float32  | 0             | 40            |
|                      | BattVltgSwd1_Volt_T_f32        | float32  | 0             | 40            |
|                      | DiagcStsIvtr1Inactv_Cnt_T_logl | boolean  | FALSE         | TRUE          |
|                      | \*BattVltgAndSwd1Ok_Cnt_T_logl | boolean  | FALSE         | TRUE          |
|                      |                                |          |               |               |
|                      | \*UseSwdVltg_Cnt_T_logl        | boolean  | FALSE         | TRUE          |
|                      | \*UseBattVltg_Cnt_T_logl       | boolean  | FALSE         | TRUE          |
|                      | \*Ntc0x03CQlfrSts_Cnt_T_enum   | SigQlfr1 | SIGQLFR_NORES | SIGQLFR_FAILD |
|                      | \*Ntc0x044QlfrSts_Cnt_T_enum   | SigQlfr1 | SIGQLFR_NORES | SIGQLFR_FAILD |
| **Return Value**     | SwdVltgLimd_Cnt_T_logl         | boolean  | FALSE         | TRUE          |

Description

Refer “Determine Instantaneous Correlation” subsystem in FDD.

#### Local Function \#2

|                      |                                       |          |               |               |
|--------|-----------------------------------|---------|-----------|----------|
| **Function Name**    | DetIdptSig                            | Type     | Min           | Max           |
| **Arguments Passed** | Ntc0x03CQlfrSts_Cnt_T_enum            | SigQlfr1 | SIGQLFR_NORES | SIGQLFR_FAILD |
|                      | Ntc0x044QlfrSts_Cnt_T_enum            | SigQlfr1 | SIGQLFR_NORES | SIGQLFR_FAILD |
|                      | \*BattVltgAndSwd1NotFailed_Cnt_T_logl | boolean  | FALSE         | TRUE          |
|                      |                                       |          |               |               |
| **Return Value**     | BattVltgCorrlnIdptSig_Cnt_T_u08       | uint8    | 0             | 2             |

Description

This function implements the “Determine Independent Signals” subsystem
in the model.

#### Local Function \#3

|                      |                                     |         |       |      |
|-------------|------------------------------------|--------|--------|--------|
| **Function Name**    | DetCorrlnSts                        | Type    | Min   | Max  |
| **Arguments Passed** | BattVltgAndSwd1NotFailed_Cnt_T_logl | boolean | FALSE | TRUE |
|                      |                                     |         |       |      |
|                      | BattVltgAndSwd1Ok_Cnt_T_logl        | boolean | FALSE | TRUE |
|                      |                                     |         |       |      |
|                      | UseSwdVltg_Cnt_T_logl               | boolean | FALSE | TRUE |
|                      | UseBattVltg_Cnt_T_logl              | boolean | FALSE | TRUE |
|                      | \*DftBrdgVltgActv_Cnt_T_logl        | boolean | FALSE | TRUE |
| **Return Value**     | BattSwdVltgCorrlnSts_Cnt_T_u08      | uint8   | 0     | 2    |

1.  Description

This function implements the “Determine Correlation Status” subsystem in
the model.

#### Local Function \#4

|                      |                              |         |       |      |
|----------------------|------------------------------|---------|-------|------|
| **Function Name**    | BattVltgDiag                 | Type    | Min   | Max  |
| **Arguments Passed** | BattVltg_Volt_T_f32          | float32 | 0     | 40   |
|                      | InhbBattVltgDiagc_Cnt_T_logl | boolean | FALSE | TRUE |

##### Description

Implements “Battery Voltage Diagnostics” subsystem.

#### Local Function \#5

|                      |                           |         |       |      |
|----------------------|---------------------------|---------|-------|------|
| **Function Name**    | RngChk                    | Type    | Min   | Max  |
| **Arguments Passed** | BattVltg_Volt_T_f32       | float32 | 0     | 40   |
|                      | BattVltgSwdMax_Volt_T_f32 | float32 | 0     | 40   |
| **Return Value**     | TestLgc_Cnt_T_logl        | boolean | FALSE | TRUE |

##### Description

Implements “Range Check” block in the model. Created to reduce
cyclomatic complexity and static path count.

### Transition Functions

None

# Known Limitations with Design

None

# UNIT TEST CONSIDERATION

None

####### Abbreviations and Acronyms

None

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

| **Ref. \#** | **Title**                                            | **Version**                    |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping              | v1.3.0 R4.0 Rev 2              |
| 2           | MDD Guideline                                        | EA4 01.00.01                   |
| 3           | EA4 Software Naming Conventions                      | 01.01.00                       |
| 4           | Software Design and Coding Standards                 | 2.1                            |
| 5           | FDD – ES259B Battery or Switched Voltage Correlation | See Synergy subproject version |

{% endraw %}