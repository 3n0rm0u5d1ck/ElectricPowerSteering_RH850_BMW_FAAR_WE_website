---
layout: default
title: DmaCfgAndUse_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**DmaCfgAndUse**

**Version:** **4.0**

**Release Date: 19-Feb-2018**

**Prepared For:**

**Software Engineering,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**SEPG,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
**

**<u>Document Change History</u>**

|             |                                                  |                  |             |
|--------|------------------------------------|-----------------|------------|
| **Version** | **Description**                                  | **Author**       | **Date**    |
| 1.0         | Initial Version                                  | Avinash James    | 27-May-2016 |
| 2.0         | Updated for corrected timing                     | Avinash James    | 08-Jun-2016 |
| 3.0         | Updated as per Design 3.0.0                      | Krzyszotf Byrski | 05-Dec-2017 |
| 4.0         | Updated design limitations and document template | Brionna Spencer  | 19-Feb-2018 |

**  
**

**<u>Table of Contents</u>**

[1 DmaCfgAndUse & High-Level Description
[5](#dmacfganduse-high-level-description)](#dmacfganduse-high-level-description)

[2 Design details of software module
[6](#design-details-of-software-module)](#design-details-of-software-module)

[2.1 Graphical representation of DmaCfgAndUse
[6](#graphical-representation-of-dmacfganduse)](#graphical-representation-of-dmacfganduse)

[2.2 Data Flow Diagram [6](#data-flow-diagram)](#data-flow-diagram)

[2.2.1 Component level DFD
[6](#component-level-dfd)](#component-level-dfd)

[2.2.2 Function level DFD [6](#function-level-dfd)](#function-level-dfd)

[3 Constant Data Dictionary
[7](#constant-data-dictionary)](#constant-data-dictionary)

[3.1 Program (fixed) Constants
[7](#program-fixed-constants)](#program-fixed-constants)

[3.1.1 Embedded Constants [7](#embedded-constants)](#embedded-constants)

[4 Software Component Implementation
[8](#software-component-implementation)](#software-component-implementation)

[4.1 Sub-Module Functions
[8](#sub-module-functions)](#sub-module-functions)

[4.1.1 Init: DmaCfgAndUseInit1
[8](#init-dmacfganduseinit1)](#init-dmacfganduseinit1)

[4.1.1.1 Design Rationale [8](#design-rationale)](#design-rationale)

[4.1.1.2 Module Outputs [8](#module-outputs)](#module-outputs)

[4.1.2 Per: DmaCfgAndUsePer1
[8](#per-dmacfganduseper1)](#per-dmacfganduseper1)

[4.1.2.1 Design Rationale [8](#design-rationale-1)](#design-rationale-1)

[4.1.2.2 Store Module Inputs to Local copies
[8](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[4.1.2.3 (Processing of function) …
[8](#processing-of-function)](#processing-of-function)

[4.1.2.4 Store Local copy of outputs into Module Outputs
[8](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[4.2 Server Runnables [8](#server-runnables)](#server-runnables)

[4.2.1 DmaEna2MilliSecToMotCtrlTrf
[8](#dmaena2millisectomotctrltrf)](#dmaena2millisectomotctrltrf)

[4.2.1.1 Design Rationale [8](#design-rationale-2)](#design-rationale-2)

[4.2.1.2 (Processing of function) …
[8](#processing-of-function-1)](#processing-of-function-1)

[4.2.2 DmaWaitForMotCtrlTo2MilliSecTrf
[8](#dmawaitformotctrlto2millisectrf)](#dmawaitformotctrlto2millisectrf)

[4.2.2.1 Design Rationale [8](#design-rationale-3)](#design-rationale-3)

[4.2.2.2 (Processing of function) …
[9](#processing-of-function-2)](#processing-of-function-2)

[4.2.3 MotAg0SnsrCfgDmaStrt
[9](#motag0snsrcfgdmastrt)](#motag0snsrcfgdmastrt)

[4.2.3.1 Design Rationale [9](#design-rationale-4)](#design-rationale-4)

[4.2.3.2 (Processing of function) …
[9](#processing-of-function-3)](#processing-of-function-3)

[4.3 Interrupt Functions
[9](#interrupt-functions)](#interrupt-functions)

[4.4 Module Internal (Local) Functions
[9](#module-internal-local-functions)](#module-internal-local-functions)

[4.5 GLOBAL Function/Macro Definitions
[9](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[4.5.1 GLOBAL Function \#1 [9](#global-function-1)](#global-function-1)

[4.5.1.1 Design Rationale [9](#design-rationale-5)](#design-rationale-5)

[4.5.1.2 Processing [9](#processing)](#processing)

[4.5.2 GLOBAL Function \#2 [9](#global-function-2)](#global-function-2)

[4.5.2.1 Design Rationale [9](#design-rationale-6)](#design-rationale-6)

[4.5.2.2 Processing [10](#processing-1)](#processing-1)

[4.5.3 GLOBAL Function \#3 [10](#global-function-3)](#global-function-3)

[4.5.3.1 Design Rationale
[10](#design-rationale-7)](#design-rationale-7)

[4.5.3.2 Processing [10](#processing-2)](#processing-2)

[5 Known Limitations with Design
[11](#known-limitations-with-design)](#known-limitations-with-design)

[6 UNIT TEST CONSIDERATIONS
[12](#unit-test-considerations)](#unit-test-considerations)

[Appendix A Abbreviations and Acronyms
[13](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [14](#glossary)](#glossary)

[Appendix C References [15](#references)](#references)

# DmaCfgAndUse & High-Level Description

DMA Configuration and Usage (DmaCfgAndUse) sets up the initial DMA
configuration and defines the periodic and server runnable functionality
needed for DMA transfers of SPI, ADC, and Motor Control loop/RTE
interface data.

# Design details of software module

## Graphical representation of DmaCfgAndUse

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/CM200B_DmaCfgAndUse_Impl/doc/mediax/media/image1.png"
style="width:3.95in;height:2.125in"
alt="C:\Users\nz3893\Documents\OneDrive - NEXTEER AUTOMOTIVE\1 Current Components\png_Graphic CM200B.png" />

## Data Flow Diagram

### Component level DFD

None

### Function level DFD

None

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name                     | Resolution | Units    | Value |
|-----------------------------------|------------|----------|-------|
| CPU1PEID_CNT_U32                  | 1          | Counts   | 1     |
| PRPHLTOLCLRAMSPID_CNT_U32         | 1          | Counts   | 3     |
| LCLRAMTOPRPHLSPID_CNT_U32         | 1          | Counts   | 2     |
| LCLRAMTOLCLRAMSPID_CNT_U32        | 1          | Counts   | 0     |
| USRMODENA_CNT_U32                 | 1          | Counts   | 1     |
| USRMODDI_CNT_U32                  | 1          | Counts   | 1     |
| DMACFGANDUSE_MAXWAIT_MICROSEC_U32 | 1          | MicroSec | 400   |
| INIZERO_CNT_U32                   | 1          | Counts   | 0     |

Also see FDD DataDict.m file for constant definitions.

# Software Component Implementation

## Sub-Module Functions

## Init: DmaCfgAndUseInit1

##  Design Rationale

The DMACnnCM channel master registers can be written only in supervisor
mode. After the Channel master register for a given channel has been
written, the selected Processor Element can write to that channel’s
registers in user mode. However, for simplicity, all DMA register
initialization is being done in one trusted function. Therefore, only
the Per Instance Memory initialization is done directly in the
DmaCfgAndUseInit1 function; all DMA register initialization is done in
the DmaRegInin function called by DmaCfgAndUseInit1.

##  Module Outputs

Refer to FDD

## Per: DmaCfgAndUsePer1

##  Design Rationale

None

##  Store Module Inputs to Local copies

None

##  (Processing of function) …

Refer to FDD

##  Store Local copy of outputs into Module Outputs

None

## Server Runnables

## DmaEna2MilliSecToMotCtrlTrf

## Design Rationale

None

##  (Processing of function) …

None

## DmaWaitForMotCtrlTo2MilliSecTrf

## Design Rationale

None

##  (Processing of function) …

None

## MotAg0SnsrCfgDmaStrt

## Design Rationale

None

##  (Processing of function) …

None

## Interrupt Functions

None

## Module Internal (Local) Functions

None

## GLOBAL Function/Macro Definitions

## GLOBAL Function \#1

|                      |            |      |     |     |
|----------------------|------------|------|-----|-----|
| **Function Name**    | DmaRegInin | Type | Min | Max |
| **Arguments Passed** | None       |      |     |     |
| **Return Value**     | N/A        |      |     |     |

##  Design Rationale

Trusted function that performs all register initialization from the
CM200B_DmaCfgAndUse_PeripheralCfg.xlsx spreadsheet in the FDD. The
DMACnnCM channel master registers can be written only in supervisor
mode. After the Channel master register for a given channel has been
written, the selected Processor Element can write to that channel’s
registers in user mode. However, for simplicity, all DMA register
initialization is being done in one trusted function. For timing
optimization, register level initialization is used (rather than bit
field modifications of the register fields).

##  Processing

Refer to FDD

## GLOBAL Function \#2

|                      |           |      |     |     |
|----------------------|-----------|------|-----|-----|
| **Function Name**    | InjDmaErr | Type | Min | Max |
| **Arguments Passed** | None      |      |     |     |
| **Return Value**     | N/A       |      |     |     |

##  Design Rationale

Refer to FDD

##  Processing

Refer to FDD

## GLOBAL Function \#3

|                      |                |      |     |     |
|----------------------|----------------|------|-----|-----|
| **Function Name**    | InjMcuDiagcErr | Type | Min | Max |
| **Arguments Passed** | None           |      |     |     |
| **Return Value**     | N/A            |      |     |     |

##  Design Rationale

Refer to FDD

##  Processing

Refer to FDD

# Known Limitations with Design

None

# UNIT TEST CONSIDERATIONS

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

| **Term** | **Definition**         | **Source** |
|----------|------------------------|------------|
| MDD      | Module Design Document |            |
| DFD      | Data Flow Diagram      |            |

####### References

| **Ref. \#** | **Title**                                                                                                                                                           | **Version**                    |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping                                                                                                                             | v1.3.0 R4.0 Rev 2              |
| 2           | MDD Guideline                                                                                                                                                       | EA4 01.02.00                   |
| 3           | EA4 [Software Naming Conventions](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc) | 01.02.00                       |
| 4           | Software Design and Coding Standards                                                                                                                                | 2.01                           |
| 5           | FDD: CM200B_DmaCfgAndUse_Design                                                                                                                                     | See Synergy subproject version |

{% endraw %}