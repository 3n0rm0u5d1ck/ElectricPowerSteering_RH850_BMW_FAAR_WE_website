---
layout: default
title: DiagcMgrProxy_MDD
nav_order: 4
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**Diagnostic Manager Proxy**

**VERSION:** **5.0**

**DATE:** **29-JUN-2017**

**Prepared By:**

**Shruthi Raghavan**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                                                 |            |             |             |
|-----|----------------------------------------|--------|--------|------------|
| **Sl. No.** | **Description**                                 | **Author** | **Version** | **Date**    |
| 1           | ES101A_DiagcMgr_Design version 2 implementation | SB         | 1.0         | 11-Mar-2016 |
| 2           | ES101A_DiagcMgr_Design version 4 implementation | SB         | 2.0         | 22-Jun-2016 |
| 3           | Added new DET in Init1                          | SB         | 3.0         | 02-Dec-2016 |
| 4           | Added new runnable SetNtcStsAndSnpshtData.      | SR         | 4.0         | 21-Apr-2017 |
| 5           | Added unit test considerations per EA4#9649     | SR         | 5.0         | 29-Jun-2017 |

Table of Contents

[1 Abbrevations And Acronyms 5](#abbrevations-and-acronyms)

[2 References 6](#references)

[3 DiagcMgrPROXYAPPLX & High-Level Description
7](#diagcmgrproxyapplx-high-level-description)

[4 Design details of software module
8](#design-details-of-software-module)

[4.1 Graphical representation of DiagcmgrPRoxyApplX
8](#graphical-representation-of-diagcmgrproxyapplx)

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

[7.1.1 Initialization Functions 11](#initialization-functions)

[7.1.1.1 INIT: DiagcMgrPROXYAPPLXInit1
11](#init-diagcmgrproxyapplxinit1)

[7.1.1.2 Design Rationale 11](#design-rationale)

[7.1.1.3 Store Module Inputs to Local copies
11](#__RefHeading___Toc454968199)

[7.1.1.4 (Processing of function)……… 11](#__RefHeading___Toc454968200)

[7.1.1.5 Store Local copy of outputs into Module Outputs
11](#__RefHeading___Toc454968201)

[7.1.2 PERIODIC FUNCTIONS 11](#periodic-functions)

[7.1.2.1 Per: diagcmgrPROXYAPPLXPer1 11](#per-diagcmgrproxyapplxper1)

[7.1.2.2 Design Rationale 11](#design-rationale-1)

[7.1.2.3 Store Module Inputs to Local copies
11](#__RefHeading___Toc454968205)

[7.1.2.4 (Processing of function)……… 11](#__RefHeading___Toc454968206)

[7.1.2.5 Store Local copy of outputs into Module Outputs
11](#__RefHeading___Toc454968207)

[7.1.3 Interrupt Functions 11](#interrupt-functions)

[7.1.4 Server Runnable Functions 12](#server-runnable-functions)

[7.1.4.1 GetDiagcDataApplX_Oper 12](#getdiagcdataapplx_oper)

[7.1.4.2 GetNtcActvX_Oper 12](#getntcactvx_oper)

[7.1.4.3 GetNtcDebCntrAppl0_Oper 12](#getntcdebcntrappl0_oper)

[7.1.4.4 GetNtcInfoApplX_Oper 12](#getntcinfoapplx_oper)

[7.1.4.5 GetNtcQlfrStsX_Oper 12](#getntcqlfrstsx_oper)

[7.1.4.6 GetNtcStsX_Oper 13](#getntcstsx_oper)

[7.1.4.7 SetNtcStsX_Oper 14](#setntcstsx_oper)

[7.1.5 Local Function/Macro Definitions
14](#local-functionmacro-definitions)

[7.1.5.1 Description 14](#description)

[7.1.6 TRANSIENT FUNCTIONS 14](#transient-functions)

[8 Known Limitations With Design 15](#known-limitations-with-design)

[9 UNIT TEST CONSIDERATION 16](#unit-test-consideration)

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

|         |                                 |                                                                                                                                                                                                                              |
|--------|------------------------------|-----------------------------------|
| Sr. No. | Title                           | Version                                                                                                                                                                                                                      |
| 1       | MDD Guidelines                  | See process v04.04.02 document from eRoom [here](http://eroom.nexteer.com/eRoomReq/Files/Nexteer-ProductLineSystems/ProcessDocumentsSystemsElectronicSystems/0_35a47/MDD%20Guideline%20EA4%2001.00.01.docx)                  |
| 2       | EA4 Software Naming Conventions | See process v04.04.02 document from eRoom [here](http://eroom.nexteer.com/eRoomReq/Files/Nexteer-ProductLineSystems/ProcessDocumentsSystemsElectronicSystems/0_35e15/EA4%20Software%20Naming%20Conventions%2001.01.00.docx)  |
| 3       | Coding standards                | See process v04.04.02 document from eRoom [here](http://eroom.nexteer.com/eRoomReq/Files/Nexteer-ProductLineSystems/ProcessDocumentsSystemsElectronicSystems/0_35a2f/Software%20Design%20and%20Coding%20Standards%202.1.doc) |
| 4       | ES101A_DiagcMgr_Design          | See Synergy Design Subproject Version                                                                                                                                                                                        |

# DiagcMgrPROXYAPPLX & High-Level Description

There are 11 proxy components whose design is same but the name of the
components is based on the application number. ApplX is used through out
the document in place of application number.

# Design details of software module

## Graphical representation of DiagcmgrPRoxyApplX

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/ES101A_DiagcMgr_Impl/doc/mediax/media/image1.png"
style="width:3.71181in;height:2.22917in" />

## Data Flow Diagram

## Module level DFD

*N/A*

## Sub-Module level DFD

*N/A*

## COMPONENT FLOW DIAGRAM

*N/A*

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
<td>Refer DiagcMgr_MDD</td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

## Variable definition for enumerated types

|           |              |       |
|-----------|--------------|-------|
| Enum Name | Element Name | Value |
| N/A       |              |       |

# Constant Data Dictionary

## Program(fixed) Constants

## Embedded Constants

*\< All program specific constants will be defined in detail \>*

## Local

|                     |            |       |       |
|---------------------|------------|-------|-------|
| Constant Name       | Resolution | Units | Value |
| See DataDict.m file |            |       |       |
| Refer DiagcMgr_MDD  |            |       |       |

## Global

*\<This section lists the global constants used by the module. For
details on global constants, refer to the Data Dictionary for the
application\>*

|                     |
|---------------------|
| Constant Name       |
| See DataDict.m file |
|                     |
|                     |

## Module specific Lookup Tables Constants

*\<(This is for lookup tables (arrays) with fixed values, same name as
other tables)\>*

|                    |            |       |                  |
|--------------------|------------|-------|------------------|
| Constant Name      | Resolution | Value | Software Segment |
| Refer DiagcMgr_MDD |            |       |                  |

# Software Module Implementation

## Sub-Module Functions

None

## Initialization Functions

## INIT: DiagcMgrPROXYAPPLXInit1

X in the flowchart will change based on the proxy application number.

ErrorID ‘0’ is ensuring if DTCIDX value in fault response table is set
to have value larger than the total number of DTCs in the code
configuration.

![](ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/ES101A_DiagcMgr_Impl/doc/mediax/media/image2.wmf)

## Design Rationale

## PERIODIC FUNCTIONS

## Per: diagcmgrPROXYAPPLXPer1

## Design Rationale

Design rationale for the subblock:  
***DiagcMgrProxyApplXPer1/Clear All NTCs/For Number of NTCs in
NtcInfoAryX/Clear the NTCs that are active***

This block clears the NTCs that are active and *Not Status Locked* This
Ignition Cycle.  
It also clears the NTCs that are NOT active from history even if they
are Status Locked This Igniton Cycle

In the case of an invalid aging counter, the status of the NTC must be
set to TestNotCompleteThisIgnitionCycle.

*<u>MC/DC Coverage Can be Achieved:</u>*

The above is verified to **not** be a MC/DC coverage issue  
The second condition when reached by an invalid aging counter can still
check whether the status locked and test complete conditions
individually affect it.

## Interrupt Functions

*None*

## Server Runnable Functions

## GetDiagcDataApplX_Oper

See DataDict.m file and model for detailed description.

## GetNtcActvX_Oper

See DataDict.m file and model for detailed description.

X in the flowchart will change based on the proxy application number.

ErrorID ‘0’ is ensuring if NtcNr is within the valid range.

ErrorID ‘1’ is ensuring if ApplIdx is valid.

![](ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/ES101A_DiagcMgr_Impl/doc/mediax/media/image3.wmf)

## GetNtcDebCntrAppl0_Oper

See DataDict.m file and model for detailed description.

## GetNtcInfoApplX_Oper

See DataDict.m file and model for detailed description.

## GetNtcQlfrStsX_Oper

See DataDict.m file and model for detailed description.

X in the flowchart will change based on the proxy application number.

ErrorID ‘0’ is ensuring if NtcNr is within the valid range.

ErrorID ‘1’ is ensuring if ApplIdx is valid.

![](ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/ES101A_DiagcMgr_Impl/doc/mediax/media/image4.wmf)

## GetNtcStsX_Oper

See DataDict.m file and model for detailed description.

X in the flowchart will change based on the proxy application number.

ErrorID ‘0’ is ensuring if NtcNr is within the valid range.

ErrorID ‘1’ is ensuring if ApplIdx is valid.

![](ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/ES101A_DiagcMgr_Impl/doc/mediax/media/image5.wmf)

## SetNtcStsX_Oper

See DataDict.m file and model for detailed description.

X in the flowchart will change based on the proxy application number.

ErrorID ‘0’ is ensuring if NtcNr is within the valid range.

ErrorID ‘1’ is ensuring if ApplIdx is valid.

![](ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/ES101A_DiagcMgr_Impl/doc/mediax/media/image6.wmf)

## SetNtcStsAndSnpshtDataX_Oper

See DataDict.m file and model for detailed description.

X in the flowchart will change based on the proxy application number.

ErrorID ‘0’ is ensuring if NtcNr is within the valid range.

ErrorID ‘1’ is ensuring if ApplIdx is valid.

![](ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/ES101A_DiagcMgr_Impl/doc/mediax/media/image7.wmf)

## Local Function/Macro Definitions

## Description

Proxies use functions from the private.c file, refer DiagcMgr MDD for
function descriptions.

## TRANSIENT FUNCTIONS 

*None*

# Known Limitations With Design

1.  Per the FDD author, safety critical data is protected in an
    exclusive area but there is a possibility of corruption of non
    critical data.

2.  Refer to Design Rationale section on the top level of DiagcMgrProxy
    Simulink model.

# UNIT TEST CONSIDERATION

1.  Config files in the contract folder are for a test project with
    sample configurations using Application 6 and Application 10.
    Therefore with this configuration, the following files cannot be
    tested – DiagcMgrProxyAppl0, DiagcMgrProxyAppl1, DiagcMgrProxyAppl2,
    DiagcMgrProxyAppl3, DiagcMgrProxyAppl4, DiagcMgrProxyAppl5,
    DiagcMgrProxyAppl7, DiagcMgrProxyAppl8, DiagcMgrProxyAppl9.

2.  Low Path Coverage can be justified in the notes for now, if the
    reason is due to Configurable code in the component.

Note: Continuous improvement CR EA4#9630 has been written to modify the
contract folder header files to allow better coverage in unit test.

# Appendix

*None*

{% endraw %}