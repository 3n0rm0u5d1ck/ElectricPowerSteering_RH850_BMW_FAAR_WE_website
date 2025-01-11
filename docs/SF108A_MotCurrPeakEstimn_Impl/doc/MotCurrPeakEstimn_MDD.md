---
layout: default
title: MotCurrPeakEstimn_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**MotCurrPeakEstimn**

**Sep 25, 2017**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**TATA,**

**Trivandrum, India**

**  
<u>Change History</u>**

|                                                                 |            |             |             |
|------------------------|---------------------|--------------|--------------|
| **Description**                                                 | **Author** | **Version** | **Date**    |
| Initial Version                                                 | SB         | 1.0         | 05-Aug-2015 |
| Updated graphical representation due to changes from FDD v1.2.0 | NS         | 2.0         | 25-Apr-2016 |
| Updated to FDD v2.0.0                                           | JK         | 3.0         | 18-Nov-2016 |
| Updated to FDD v3.0.0                                           | TATA       | 4.0         | 25-Sep-2017 |

**  
**

<u>Table of Contents</u>

1 Introduction 4

1.1 Purpose 4

1.2 Scope 4

2 MotCurrPeakEstimn & High-Level Description 5

3 Design details of software module 6

3.1 Graphical representation of MotCurrPeakEstimn 6

3.2 Data Flow Diagram 6

3.2.1 Component level DFD 6

3.2.2 Function level DFD 6

4 Constant Data Dictionary 7

4.1 Program (fixed) Constants 7

4.1.1 Embedded Constants 7

5 Software Component Implementation 8

5.1 Sub-Module Functions 8

5.1.1 Init: MotCurrPeakEstimnInit1 8

5.1.2 Per: MotCurrPeakEstimnPer1 8

5.1.3 Per: MotCurrPeakEstimnPer2 8

5.2 Server Runables 8

5.3 Interrupt Functions 8

5.4 Module Internal (Local) Functions 8

5.5 GLOBAL Function/Macro Definitions 8

6 Known Limitations with Design 9

7 UNIT TEST CONSIDERATION 10

Appendix A Abbreviations and Acronyms 11

Appendix B Glossary 12

Appendix C References 13

# Introduction

## Purpose

## Scope

# MotCurrPeakEstimn & High-Level Description

*Refer FDD*

# Design details of software module

*Refer FDD*

## Graphical representation of MotCurrPeakEstimn

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/SF108A_MotCurrPeakEstimn_Impl/doc/mediax/media/image2.png"
style="width:3.3125in;height:3.58333in" />

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

| Constant Name    | Resolution | Units | Value |
|------------------|------------|-------|-------|
| Refer .m File    |            |       |       |
| BITMASK1_CNT_U08 | uint8      | CNT   | 1U    |
| BITMASK2_CNT_U08 | uint8      | CNT   | 2U    |
| BITMASK4_CNT_U08 | uint8      | CNT   | 4U    |

# Software Component Implementation

Refer FDD

## Sub-Module Functions

## Init: MotCurrPeakEstimnInit1

Refer FDD

## Per: MotCurrPeakEstimnPer1

*Refer FDD*

## Per: MotCurrPeakEstimnPer2

*Refer FDD*

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

| **Ref. \#** | **Title**                                                                                                                                                             | **Version**                    |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                    | v1.3.0 R4.0 Rev 2              |
| 2           | MDD Guideline                                                                                                                                                         | Process 04.02.00               |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | Process 04.02.00               |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | Process 04.02.00               |
| 5           | FDD – SF108A_MotCurrPeakEstimn_Design                                                                                                                                 | See Synergy SubProject version |

{% endraw %}