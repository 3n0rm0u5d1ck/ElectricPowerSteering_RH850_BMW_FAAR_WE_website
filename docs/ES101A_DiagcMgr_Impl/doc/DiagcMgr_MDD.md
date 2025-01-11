---
layout: default
title: DiagcMgr_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**Diagnostic Manager**

**VERSION:** **11.0**

**DATE:** **14-DEC-2017**

**Prepared By:**

**Shruthi Raghavan**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|                                                                                                                                                                                                           |            |             |             |
|---------------------------------------------|--------|--------|------------|
| **Description**                                                                                                                                                                                           | **Author** | **Version** | **Date**    |
| Initial Version                                                                                                                                                                                           | SB         | 1.0         | 23-Apr-2015 |
| Added to Design Limitations section                                                                                                                                                                       | KMC        | 2.0         | 03-Jun-2015 |
| ES101A_DiagcMgr_Design version 2 implementation                                                                                                                                                           | SB         | 3.0         | 11-Mar-2016 |
| ES101A_DiagcMgr_Design version 3 implementation                                                                                                                                                           | SB         | 4.0         | 19-Apr-2016 |
| ES101A_DiagcMgr_Design version 4 implementation                                                                                                                                                           | SB         | 5.0         | 22-Jun-2016 |
| Added DETs to “SetNtcStsCore_Oper” server runnables                                                                                                                                                       | SB         | 6.0         | 26-Sep-2016 |
| Updated to fix anomalies EA4#8118 and EA4#8115                                                                                                                                                            | SB         | 7.0         | 02-Dec-2016 |
| Updated the graphical representation. Added server runnables CnvSnpshtData\_\*, noted design limitations and design rationales and added local functions                                                  | SR         | 8.0         | 21-Apr-2017 |
| Updated Unit Test considerations as per EA4#9649                                                                                                                                                          | SR         | 9.0         | 29-Jun-2017 |
| Updated Unit Test considerations for new process to handle configuration parameters for PIL testing. Also updated design limitations per latest design baseline.                                          | SR         | 10.0        | 26-Sep-2017 |
| Removed Static analysis explanation from DiagcMgr PwrDwn function’s rationale because it is no longer applicable. Also removed design limitation that was corrected in the current design version (5.3.0) | SR         | 11.0        | 14-Dec-2017 |

Table of Contents

[1 Abbrevations And Acronyms 6](#abbrevations-and-acronyms)

[2 References 7](#references)

[3 DiagcMgr & High-Level Description
8](#diagcmgr-high-level-description)

[4 Design details of software module
9](#design-details-of-software-module)

[Graphical representation of Diagcmgr
9](#graphical-representation-of-diagcmgr)

[4.1 9](#graphical-representation-of-diagcmgr)

[4.2 Data Flow Diagram 9](#data-flow-diagram)

[4.2.1 Module level DFD 9](#module-level-dfd)

[4.2.2 Sub-Module level DFD 9](#sub-module-level-dfd)

[4.3 COMPONENT FLOW DIAGRAM 9](#component-flow-diagram)

[5 Variable Data Dictionary 10](#variable-data-dictionary)

[5.1 User defined typedef definition/declaration
10](#user-defined-typedef-definitiondeclaration)

[5.2 Variable definition for enumerated types
10](#variable-definition-for-enumerated-types)

[5.3 Global Variable definition 10](#global-variable-definition)

[6 Constant Data Dictionary 11](#constant-data-dictionary)

[6.1 Program(fixed) Constants 11](#programfixed-constants)

[6.1.1 Embedded Constants 11](#embedded-constants)

[6.1.1.1 Local 11](#local)

[6.1.1.2 Global 11](#global)

[Module specific Lookup Tables Constants
11](#module-specific-lookup-tables-constants)

[6.1.2 11](#module-specific-lookup-tables-constants)

[7 Software Module Implementation 12](#software-module-implementation)

[7.1 Sub-Module Functions 12](#sub-module-functions)

[7.1.1 Initialization Functions 12](#initialization-functions)

[7.1.2 PERIODIC FUNCTIONS 12](#periodic-functions)

[7.1.2.1 Per: diagcmgrPer1 12](#per-diagcmgrper1)

[7.1.2.1.1 Design Rationale 12](#design-rationale)

[7.1.2.2 Per: diagcmgrPer2 12](#per-diagcmgrper2)

[7.1.2.2.1 Design Rationale 12](#design-rationale-1)

[7.1.3 Interrupt Functions 12](#interrupt-functions)

[Server Runnable Functions 13](#server-runnable-functions)

[7.1.4 13](#server-runnable-functions)

[7.1.4.1 ClrAllDiagc_Oper 13](#clralldiagc_oper)

[7.1.4.2 ClrSnpshtData_Oper 13](#clrsnpshtdata_oper)

[7.1.4.2.1 Design Rationale 13](#design-rationale-2)

[7.1.4.3 DiagcMgrIninCore_Oper 13](#diagcmgrinincore_oper)

[7.1.4.4 DiagcMgrPwrDwN 14](#diagcmgrpwrdwn)

[7.1.4.4.1 Design Rationale 14](#design-rationale-3)

[7.1.4.5 UpdDtcEnaCdn 14](#upddtcenacdn)

[7.1.4.5.1 Design Rationale 15](#design-rationale-4)

[7.1.4.6 GetNtcActvCORE_Oper 15](#getntcactvcore_oper)

[7.1.4.7 GetNtcQlfrStsCORE_Oper 15](#getntcqlfrstscore_oper)

[7.1.4.8 GetNtcStsCORE_Oper 15](#getntcstscore_oper)

[7.1.4.9 ReadNtcFltAry_Oper 15](#readntcfltary_oper)

[7.1.4.9.1 Design Rationale 15](#design-rationale-5)

[7.1.4.10 ReadNtcInfoAndDebCntr_Oper 15](#readntcinfoanddebcntr_oper)

[7.1.4.10.1 Design Rationale 15](#design-rationale-6)

[7.1.4.11 ReadSnpshtData_Oper 15](#readsnpshtdata_oper)

[7.1.4.12 CnvSnpshtData_f32_Oper 15](#cnvsnpshtdata_f32_oper)

[7.1.4.13 CnvSnpshtData_logl_Oper 15](#cnvsnpshtdata_logl_oper)

[7.1.4.14 CnvSnpshtData_s08_Oper 15](#cnvsnpshtdata_s08_oper)

[7.1.4.15 CnvSnpshtData_s16_Oper 15](#cnvsnpshtdata_s16_oper)

[7.1.4.16 CnvSnpshtData_s32_Oper 15](#cnvsnpshtdata_s32_oper)

[7.1.4.17 CnvSnpshtData_u08_Oper 16](#cnvsnpshtdata_u08_oper)

[7.1.4.18 CnvSnpshtData_u16_Oper 16](#cnvsnpshtdata_u16_oper)

[7.1.4.19 SetNtcStsCore_Oper 16](#setntcstscore_oper)

[7.1.4.19.1 Design Rationale 16](#design-rationale-7)

[7.1.4.20 ClrLtchCntrData_Oper 16](#clrltchcntrdata_oper)

[7.1.4.21 ReadLtchCntrData_Oper 16](#readltchcntrdata_oper)

[7.1.4.22 RestoreDiagcMgrLtchCntrAryDft
17](#restorediagcmgrltchcntrarydft)

[7.1.4.23 RestoreNtcFltAryDft 17](#restorentcfltarydft)

[7.1.4.24 RestoreSnpshtAryDft 17](#restoresnpshtarydft)

[7.1.5 Local Function/Macro Definitions
17](#local-functionmacro-definitions)

[7.1.5.1 Local Function \#1 17](#local-function-1)

[7.1.5.1.1 Description 17](#description)

[7.1.5.2 Local Function \#2 17](#local-function-2)

[7.1.5.3 Description 17](#description-1)

[7.1.5.3.1 Design Rationale 18](#design-rationale-8)

[7.1.5.4 Local Function \#3 18](#local-function-3)

[7.1.5.4.1 Design Rationale 18](#design-rationale-9)

[7.1.5.5 Local Function \#4 18](#local-function-4)

[7.1.5.5.1 Design Rationale 18](#design-rationale-10)

[7.1.5.6 Local Function \#5 18](#local-function-5)

[7.1.5.6.1 Design Rationale 18](#design-rationale-11)

[7.1.5.7 Local Function \#6 18](#local-function-6)

[7.1.5.7.1 Design Rationale 19](#design-rationale-12)

[7.1.5.8 Local Function \#7 19](#local-function-7)

[7.1.5.8.1 Design Rationale 19](#design-rationale-13)

[7.1.5.9 Local Function \#8 19](#local-function-8)

[7.1.5.9.1 Design Rationale 19](#design-rationale-14)

[7.1.6 GLObAL Function/Macro Definitions
19](#global-functionmacro-definitions)

[7.1.6.1 GLObAL Function \#1 19](#global-function-1)

[7.1.6.1.1 Description 20](#description-2)

[GLObAL Function \#2 20](#global-function-2)

[7.1.6.2 20](#global-function-2)

[7.1.6.2.1 Description 20](#description-3)

[GLObAL Function \#3 20](#global-function-3)

[7.1.6.3 20](#global-function-3)

[7.1.6.3.1 Description 20](#description-4)

[GLObAL Function \#4 20](#global-function-4)

[7.1.6.4 20](#global-function-4)

[7.1.6.4.1 Description 20](#description-5)

[GLObAL Function \#5 20](#global-function-5)

[7.1.6.5 20](#global-function-5)

[7.1.6.5.1 Description 20](#description-6)

[7.1.6.6 GLObAL Function \#6 20](#global-function-6)

[7.1.6.6.1 Description 20](#description-7)

[7.1.7 TRANSIENT FUNCTIONS 21](#transient-functions)

[8 Known Limitations With Design 22](#known-limitations-with-design)

[9 UNIT TEST CONSIDERATION 23](#__RefHeading___Toc481665925)

[10 Appendix 24](#appendix)

# Abbrevations And Acronyms

|              |                                         |
|--------------|-----------------------------------------|
| Abbreviation | Description                             |
| DFD          | Design functional diagram               |
| MDD          | Module design Document                  |
|              | \<ADD more to the table if applicable\> |
|              |                                         |

# References

This section lists the title & version of all the documents that are
referred for development of this document

|     |                                                                                                                                                                                                  |                                |
|------|-------------------------------|-----------------------------------|
| \#  | Title                                                                                                                                                                                            | Version                        |
| 1   | [MDD Guideline EA4](https://nexteerautomotive.sharepoint.com/engineering/ASPICE/_layouts/15/DocIdRedir.aspx?ID=4FSMJ3P65F55-550837352-128)                                                       | 1.02                           |
| 2   | [EA4 Software Naming Conventions](https://nexteerautomotive.sharepoint.com/engineering/ASPICE/_layouts/15/DocIdRedir.aspx?ID=4FSMJ3P65F55-550837352-179&e=a659b1a20e4143bf821960648887541f)      | 1.02                           |
| 3   | [Software Design and Coding standards](https://nexteerautomotive.sharepoint.com/engineering/ASPICE/_layouts/15/DocIdRedir.aspx?ID=4FSMJ3P65F55-550837352-172&e=bb4a4726c39843678b6aaab41fffc02a) | 2.01                           |
| 4   | ES101A_DiagcMgr_Design                                                                                                                                                                           | See Synergy Subproject version |

# DiagcMgr & High-Level Description

> This function is responsible for handling all the NTCs that are used
> by different FDDs. The Diagnostic Manager sets the Ntc called by any
> component and requests the system to either ramp down to Disable or
> take no action. It also handles latched Ntcs & owns the associated
> NTCNR_0x0A Ntc.

# Design details of software module

## Graphical representation of Diagcmgr

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/ES101A_DiagcMgr_Impl/doc/mediax/media/image1.png"
style="width:3.325in;height:6.03125in" />

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
<col style="width: 24%" />
<col style="width: 18%" />
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
<td>NtcMapRec1</td>
<td>ApplIdx</td>
<td>Uint8</td>
<td>0</td>
<td>10</td>
</tr>
<tr class="odd">
<td></td>
<td>NtcInfoIdx</td>
<td>uint8</td>
<td>0</td>
<td>255</td>
</tr>
<tr class="even">
<td></td>
<td>DebCntrIdx</td>
<td>Uint8</td>
<td>0</td>
<td>255</td>
</tr>
<tr class="odd">
<td>NtcInfoRec4</td>
<td>NtcStInfo</td>
<td>Uint8</td>
<td>0</td>
<td>255</td>
</tr>
<tr class="even">
<td></td>
<td>Sts</td>
<td>Uint8</td>
<td>0</td>
<td>255</td>
</tr>
<tr class="odd">
<td></td>
<td>AgiCntr</td>
<td>Uint8</td>
<td>0</td>
<td>255</td>
</tr>
<tr class="even">
<td>Ary1D_NtcInfoRec4</td>
<td></td>
<td>NtcInfoRec4[]<sup>1</sup></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>Ary1D_NtcInfoRec4_DiagcMgrProxyApplX<sup>3</sup></td>
<td></td>
<td>NtcInfoRec4[]<sup>1</sup></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>Ary1D_s16_DiagcMgrProxyApplX<sup>3</sup></td>
<td></td>
<td>Sint16[]<sup>2</sup></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

1 – Array of NtcInfoRec4

2 – Array of sint16

3 – One for each Application configured with NTCs  
For example – Application 6 and 10 have NTCs then -
Ary1D_NtcInfoRec4_DiagcMgrProxyAppl6,
Ary1D_NtcInfoRec4_DiagcMgrProxyAppl10, Ary1D_s16_DiagcMgrProxyAppl6,
Ary1D_s16_DiagcMgrProxyAppl10 would exist with configured sizes.

## Variable definition for enumerated types

|                     |              |       |
|---------------------|--------------|-------|
| Enum Name           | Element Name | Value |
| See DataDict.m file |              |       |

## Global Variable definition

|                         |                |     |     |
|-------------------------|----------------|-----|-----|
| Name                    | Type           |     |     |
| SnpshtDataAry_M\[8\]^1^ | SnpshtDataRec2 |     |     |

|                |                 |        |             |               |
|----------------|-----------------|--------|-------------|---------------|
| Name           | Element Name    | Type   | Min         | Max           |
| SnpshtDataRec2 | SpclSnpshtData0 | uint32 | 0           | 4294967295    |
|                | SpclSnpshtData1 | uint32 | 0           | 4294967295    |
|                | SpclSnpshtData2 | uint32 | 0           | 4294967295    |
|                | MicroDiagcData  | uint32 | 0           | 4294967295    |
|                | IgnCntr         | uint32 | 0           | 4294967295    |
|                | HwTq            | sint16 | -10         | 10            |
|                | MotTqCmdMrfScad | sint16 | -8.8        | 8.8           |
|                | BrdgVltg        | uint16 | 6           | 26.5          |
|                | EcuTFild        | sint16 | -50         | 150           |
|                | NtcNr           | NtcNr1 | NTCNR_0X001 | NTCNR_0X1FF   |
|                | NtcStInfo       | uint8  | 0           | 255           |
|                | SysSt           | SysSt1 | SYSST_DI    | SYSST_WRMININ |

Notes:

1- This variable is mapped to MemMap –
“GlobalShared_START_SEC_VAR_NOINIT_UNSPECIFIED”

# Constant Data Dictionary

## Program(fixed) Constants

## Embedded Constants

## Local

|                           |            |        |                 |
|---------------------------|------------|--------|-----------------|
| Constant Name             | Resolution | Units  | Value           |
| See DataDict.m file       | N/A        | N/A    | N/A             |
| IMDTSHTDWNFLT_CNT_U16     | 1          | Counts | 5U              |
| CTRLDSHTDWNFLT_CNT_U16    | 1          | Counts | 6U              |
| INFOONLYFLT_CNT_U16       | 1          | Counts | 7U              |
| TOTNROFDTC_CNT_U08^4^     | 1          | Counts | Configured      |
| PimSnpshtDataAry_rec      | N/A        | N/A    | SnpshtDataAry_M |
| D_MAXNUMBEROFNTCS_CNT_U16 | 1          | CNT    | 512U            |

4 - Number of DTCs for that program.

## Global

|                     |       |
|---------------------|-------|
| Constant Name       | Value |
| See DataDict.m file | N/A   |

## *Module specific Lookup Tables Constants*

|                                          |                        |                               |                         |
|-------------------------|--------------|-----------------|-----------------|
| Constant Name                            | Resolution             | Value                         | Software Segment        |
| DIAGCMGRNTCMAP_CNT_REC \[512\]           | NtcMapRec1             | Configured                    | DiagcMgr_START_SEC_CODE |
| NTCNRARYAPPLX_CNT_U16 \[Configured\]^5^  | 1                      | Configured                    | DiagcMgr_START_SEC_CODE |
| DTCENAMASK \[Configured\]^6^             | 1                      | Configured                    | DiagcMgr_START_SEC_CODE |
| DEMDTCEVEIDMAP \[Configured\]^6^         | 1                      | Configured                    | DiagcMgr_START_SEC_CODE |
| FLTRESPRAMPTBL_ULS_F32 \[5\]             | Single Precision Float | {0.1F,0.125F,0.2F,1.0F,10.0F} | DiagcMgr_START_SEC_CODE |
| DIAGCMGRNTCPPTYARY_CNT_U08\[512\]        | 1                      | Configured                    | DiagcMgr_START_SEC_CODE |
| DIAGCMGRLISTOFLTCHGNTC_CNT_ENUM\[20^7^\] | 1                      | Configured                    | DiagcMgr_START_SEC_CODE |
| DIAGCMGRNTCLTCHCNTRTHD_CNT_U08\[20^7^\]  | 1                      | Configured                    | DiagcMgr_START_SEC_CODE |

5 - One for each Application configured with NTCs.

6 - Variable Length (TOTNROFDTC_CNT_U08 + 1) for each build/program
depending on the Number of DTCs

for that program.

7 – The length of this array depends on MaximumNumberOfLatching Ntcs the
software is designed to handle – currently it is 20.

# Software Module Implementation

## Sub-Module Functions

None

## Initialization Functions

*None*

## PERIODIC FUNCTIONS 

## Per: diagcmgrPer1

This function exists in “DiagcMgr.c” file. Refer Simulink model for
details

## Design Rationale

“Rte_Call_GetDiagcDataApplX_Oper” for each application(X) is called
based on conditional compile using constants generated in DiagcMgr_Cfg.h

## Per: diagcmgrPer2

This function exists in “DiagcMgr.c” file. Refer Simulink model for
details

## Design Rationale

“Rte_Call_GetDiagcDataApplX_Oper” for each application(X) is called
based on conditional compile using constants generated in DiagcMgr_Cfg.h

## Interrupt Functions

*None*

## Server Runnable Functions

## ClrAllDiagc_Oper

See DataDict.m file and model. This function exists in “DiagcMgr.c”
file.

## ClrSnpshtData_Oper

See DataDict.m file and model. This function exists in “DiagcMgr.c”
file.

## Design Rationale

“NvMConf_NvMBlockDescriptor_Rte_NvmBlock_DiagcMgr_SnpshtDataAry” is used
instead of BlockID Number in “NvMProxy_SetRamBlockStatus” call so that
the Integrator doesn’t have to configure the DiagcMgr to know about the
Nvm block Ids.

## DiagcMgrIninCore_Oper

See DataDict.m file and modelThis function exists in “DiagcMgr.c” file.

![](ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/ES101A_DiagcMgr_Impl/doc/mediax/media/image2.wmf)

## DiagcMgrPwrDwN

See DataDict.m file and model

This function exists in “DiagcMgrNonRte.c” file.

## Design Rationale

“GetNtcInfoApplX_Oper” for each application(X) is called based on
conditional compile using constants generated in DiagcMgr_Cfg.h.

“NvMConf_NvMBlockDescriptor_Rte_NvmBlock_DiagcMgr_DiagcMgrNtcFltAry” is
used instead of BlockID Number in “NvMProxy_SetRamBlockStatus” call so
that the Integrator doesn’t have to configure the DiagcMgr to know about
the Nvm block Ids.

## UpdDtcEnaCdn

See DataDict.m file and model. This function exists in
“DiagcMgrNonRte.c” file.

![](ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/ES101A_DiagcMgr_Impl/doc/mediax/media/image3.wmf)

## Design Rationale

“GetNtcInfoApplX_Oper” for each application(X) is called based on
conditional compile using constants generated in DiagcMgr_Cfg.h.

## GetNtcActvCORE_Oper

See DataDict.m file and model. This function exists in “DiagcMgr.c”
file.

## GetNtcQlfrStsCORE_Oper

See DataDict.m file and model. This function exists in “DiagcMgr.c”
file.

## GetNtcStsCORE_Oper

See DataDict.m file and model

This function exists in “DiagcMgr.c” file.

## ReadNtcFltAry_Oper

See DataDict.m file and model. This function exists in “DiagcMgr.c”
file.

## Design Rationale

“GetNtcInfoApplX_Oper” for each application(X) is called based on
conditional compile using constants generated in DiagcMgr_Cfg.h  
QAC flags MISRA Rule 9.1 for HistNtcFltAry_T_rec being used to write to
PIM before initialization but it isn’t actually an issue because the
logic only uses the elements of the array that have been written to.

## ReadNtcInfoAndDebCntr_Oper

See DataDict.m file and model. This function exists in “DiagcMgr.c”
file.

## Design Rationale

“GetNtcDebCntrApplX” and “GetNtcInfoApplX_Oper” for each application(X)
is called based on conditional compile using constants generated in
DiagcMgr_Cfg.h

## ReadSnpshtData_Oper

See DataDict.m file and model. This function exists in “DiagcMgr.c”
file.

## CnvSnpshtData_f32_Oper

See DataDict.m file and model. This function exists in “DiagcMgr.c”
file.

## CnvSnpshtData_logl_Oper

See DataDict.m file and model. This function exists in “DiagcMgr.c”
file.

## CnvSnpshtData_s08_Oper

See DataDict.m file and model. This function exists in “DiagcMgr.c”
file.

## CnvSnpshtData_s16_Oper

See DataDict.m file and model. This function exists in “DiagcMgr.c”
file.

## CnvSnpshtData_s32_Oper

See DataDict.m file and model. This function exists in “DiagcMgr.c”
file.

## CnvSnpshtData_u08_Oper

See DataDict.m file and model. This function exists in “DiagcMgr.c”
file.

## CnvSnpshtData_u16_Oper

See DataDict.m file and model. This function exists in “DiagcMgr.c”
file.

## SetNtcStsCore_Oper

See DataDict.m file and model. This function exists in “DiagcMgr.c”
file.

![](ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/ES101A_DiagcMgr_Impl/doc/mediax/media/image4.wmf)

##  Design Rationale

The array DTCENAMASK is indexed by DtctempIdx_Cnt_T_u08 which
corresponds to the lower 8-bits of the FltRespTbl. So the index can
range from \[0,255\].

However the calibration PrmDiagcMgrFltResp_u16 is checked (using DET) at
init functions of each ApplProxy such that the value of the lower 8-bits
of each of its elements are in the range of \[0,sizeof(DTCENAMASK)\]. So
there will never be an out-of-bounds array access scenario on the
DTCENAMASK array.

Note: Lower 8-bits corresponds to FLTRESPDTCIDX_CNT_U16 mask being 0xFF.

## ClrLtchCntrData_Oper

See DataDict.m file and model. This function exists in “DiagcMgr.c”
file.

## ReadLtchCntrData_Oper

See DataDict.m file and model. This function exists in “DiagcMgr.c”
file.

## RestoreDiagcMgrLtchCntrAryDft

See DataDict.m file and model. This function exists in “DiagcMgr.c”
file.

## RestoreNtcFltAryDft

See DataDict.m file and model. This function exists in
“DiagcMgrNonRte.c” file.

## RestoreSnpshtAryDft

See DataDict.m file and model. This function exists in
“DiagcMgrNonRte.c” file.

## Local Function/Macro Definitions

## Local Function \#1

|                      |                                       |               |     |     |
|-------------|---------------------------|------------------|--------|--------|
| **Function Name**    | ProcRampResp                          | Type          | Min | Max |
| **Arguments Passed** | NtcNr_Cnt_T_u16                       | uint16        | 0   | 511 |
|                      | DiagcData_T_rec                       | DiagcDataRec2 |     |     |
|                      | DiagcData_T_rec .DiagcSts             |               | 0   | 255 |
|                      | DiagcData_T_rec .ActvRampRate         |               | 0.1 | 500 |
|                      | DiagcData_T_rec ActvMotTqCmdSca       |               | 0   | 1   |
|                      | ProxySetNtcData_T_rec                 | DiagcDataRec2 |     |     |
|                      | ProxySetNtcData_T_rec .DiagcSts       |               | 0   | 255 |
|                      | ProxySetNtcData_T_rec .ActvRampRate   |               | 0.1 | 500 |
|                      | ProxySetNtcData_T_rec ActvMotTqCmdSca |               | 0   | 1   |
| **Return Value**     | N/A                                   |               |     |     |

## Description

Refer ‘ProcessRampResponse and DiagcSts’ block in Simulink model for
DiagcMgr

This function exists in “DiagcMgr.c” file.

## Local Function \#2

|                      |                             |        |             |               |
|-------------|-----------------------------|----------|----------|-----------|
| **Function Name**    | UpdSnpshtData               | Type   | Min         | Max           |
| **Arguments Passed** | SpclSnpshtData0_Cnt_T_u32   | uint32 | 0           | 4294967295    |
|                      | SpclSnpshtData1_Cnt_T_u32   | uint32 | 0           | 4294967295    |
|                      | SpclSnpshtData2_Cnt_T_u32   | uint32 | 0           | 4294967295    |
|                      | McuDiagcSpplData_Cnt_T_u32  | uint32 | 0           | 4294967295    |
|                      | IgnCntr_Cnt_T_u32           | uint32 | 0           | 4294967295    |
|                      | HwTq_Cnt_T_s5p10            | sint16 | -10         | 10            |
|                      | MotTqCmdMrfScad_Cnt_T_s5p10 | sint16 | -8.8        | 8.8           |
|                      | BrdgVltg_Cnt_T_u6p10        | uint16 | 6           | 26.5          |
|                      | EcuTFild_Cnt_T_s8p7         | sint16 | -50         | 150           |
|                      | NtcNr_Cnt_T_u16             | NtcNr1 | NTCNR_0X001 | NTCNR_0X1FF   |
|                      | NtcStInfo_Cnt_T_u08         | uint8  | 0           | 255           |
|                      | SysSt_Cnt_T_enum            | SysSt1 | SYSST_DI    | SYSST_WRMININ |
| **Return Value**     | N/A                         |        |             |               |

## Description

Refer ‘UpdSnpshtData’ block in Simulink model for DiagcMgr. This
function exists in “DiagcMgr.c” file

## Design Rationale

“NvMConf_NvMBlockDescriptor_Rte_NvmBlock_DiagcMgr_SnpshtDataAry” is used
instead of BlockID Number in “NvMProxy_SetRamBlockStatus” call so that
the Integrator doesn’t have to configure the DiagcMgr to know about the
Nvm block Ids.

## Local Function \#3

|                      |                        |             |            |            |
|-------------|-----------------------------|----------|----------|-----------|
| **Function Name**    | GetNtcInfoApplX        | Type        | Min        | Max        |
| **Arguments Passed** | ApplIdx_Cnt_T_u08      | uint8       | 0          | 255        |
|                      | NtcInfoIdx_Cnt_T_u08   | uint8       | 0          | 255        |
|                      | \*NtcInfoPtr_Cnt_T_rec | NtcInfoRec4 | See DT def | See DT def |
| **Return Value**     | ApplIDValid_Cnt_T_logl | boolean     | FALSE      | TRUE       |

## Design Rationale

The function is a switch case that calls the GetNtcInfo of correct
application to modify the value of NtcInfo at the address passed as an
argument. It should be used in Non-RTE context only.

## Local Function \#4

|                      |                        |             |            |            |
|-------------|-----------------------------|----------|----------|-----------|
| **Function Name**    | GetNtcInfoApplXRte     | Type        | Min        | Max        |
| **Arguments Passed** | ApplIdx_Cnt_T_u08      | uint8       | 0          | 255        |
|                      | NtcInfoIdx_Cnt_T_u08   | uint8       | 0          | 255        |
|                      | \*NtcInfoPtr_Cnt_T_rec | NtcInfoRec4 | See DT def | See DT def |
| **Return Value**     | ApplIDValid_Cnt_T_logl | boolean     | FALSE      | TRUE       |

## Design Rationale

The function is a switch case that calls the GetNtcInfo of correct
application to modify the value of NtcInfo at the address passed as an
argument. It should be used in RTE context only.

## Local Function \#5

|                      |                            |        |     |                       |
|-------------|---------------------------|---------|---------|---------------|
| **Function Name**    | UpdDtcSts                  | Type   | Min | Max                   |
| **Arguments Passed** | NtcMapIdx_Cnt_T_u16        | Uint16 | 0   | 511                   |
|                      | NtcInfoRecSts_Cnt_T_u08    | uint8  | 0   | 255                   |
|                      | DtctempIdx_Cnt_T_u08       | Uint8  | 0   | TOTNROFDTC_CNT_U08^?^ |
|                      | \* DtcIdxCurrSts_Cnt_T_u08 | Uint   | 0   | 255                   |
| **Return Value**     | None                       | N/A    | N/A | N/A                   |

^?^ – This is a configurable constant.

## Design Rationale

Implement "Update DTC Status" subblock from Per2 in the FDD. Note that
it is called inside a while loop. Created for complexity metrics
compliance with design and coding standards.

## Local Function \#6

|                      |                            |             |            |            |
|-------------|-----------------------------|----------|----------|-----------|
| **Function Name**    | ProcNtcStsPassd            | Type        | Min        | Max        |
| **Arguments Passed** | NtcNr_Cnt_T_enum           | NtcNr1      | 1          | 511        |
|                      | \*NtcInfo_Cnt_T_rec        | NtcInfoRec4 | See DT def | See DT def |
|                      | \*NtcInfoDebCntr_Cnt_T_s16 | Sint16      | -32768     | 32767      |
| **Return Value**     | None                       | N/A         | N/A        | N/A        |

## Design Rationale

Implements 'NTCSTS_PASSD' inside SetNtcStsCore block of the DiagcMgr
simulink model in the FDD. Created to reduce the cyclomatic complexity
of SetNtcStsCore_Oper() server runnable.

## Local Function \#7

|                      |                            |             |            |            |
|-------------|-----------------------------|----------|----------|-----------|
| **Function Name**    | ProcNtcStsPrePassd         | Type        | Min        | Max        |
| **Arguments Passed** | NtcNr_Cnt_T_enum           | NtcNr1      | 1          | 511        |
|                      | DebStep_Cnt_T_u16          | Uint16      | 0          | 65535      |
|                      | \*NtcInfo_Cnt_T_rec        | NtcInfoRec4 | See DT def | See DT def |
|                      | \*NtcInfoDebCntr_Cnt_T_s16 | Sint16      | -32768     | 32767      |
| **Return Value**     | None                       | N/A         | N/A        | N/A        |

## Design Rationale

Implements 'NTCSTS_PREPASSD' inside SetNtcStsCore block of the DiagcMgr
simulink model in the FDD. Created to reduce the cyclomatic complexity
of SetNtcStsCore_Oper() server runnable.

## Local Function \#8

|                      |                             |                |     |     |
|-------------|-----------------------------|-----------|----------|-----------|
| **Function Name**    | ChkAgiCntr                  | Type           | Min | Max |
| **Arguments Passed** | AgiCntr_Cnt_T_u08           | uint8          | 0   | 255 |
|                      | Sts_Cnt_T_u08               | uint8          | 0   | 255 |
|                      | NtcMapIdx_Cnt_T_u16         | uint16         | 0   | 511 |
|                      | \*NtcFltAryIdx_Cnt_T_u16    | uint16         | 0   | 20  |
|                      | \*HistFltAryIdx_Cnt_T_u16   | uint16         | 0   | 20  |
|                      | HistNtcFltAry_T_rec         | NtcFltInfoRec2 | \-  | \-  |
|                      | HistNtcFltAry_T_rec.NtcNr   | NtcNrWithResd1 | 0   | 511 |
|                      | HistNtcFltAry_T_rec.AgiCntr | uint8          | 0   | 255 |
|                      | HistNtcFltAry_T_rec.Sts     | uint8          | 0   | 255 |
| **Return Value**     | None                        | N/A            | N/A | N/A |

## Design Rationale

Implements the 'Check Aging Counter' in DiagcMgrPwr block of DiagcMgr
simulink model in FDD. Created to reduce the static path count of
DiagMgrPwrDwn() server runnable.

## GLObAL Function/Macro Definitions

All the global functions described below are declared in
DiagcMgr_private.h and are intended to be used only by DiagcMgr and the
DiagcMgrProxyApplX components. These functions exist in
“DiagcMgr_private.c” file.

## GLObAL Function \#1

|                      |                                      |               |     |     |
|--------------|------------------------------|------------------|-----|------|
| **Function Name**    | ProcProxyRampRespAndDiagcSts         | Type          | Min | Max |
| **Arguments Passed** | NtcNr_Cnt_T_u16                      | uint16        | 0   | 511 |
|                      | ProxyDiagcData_T_rec                 | DiagcDataRec2 |     |     |
|                      | ProxyDiagcData_T_rec .DiagcSts       |               | 0   | 255 |
|                      | ProxyDiagcData_T_rec .ActvRampRate   |               | 0.1 | 500 |
|                      | ProxyDiagcData_T_rec ActvMotTqCmdSca |               | 0   | 1   |
| **Return Value**     | N/A                                  |               |     |     |

## Description

Refer ‘ProcessRampResponse and DiagcSts’ block in Simulink path ”
ES101A_DiagcMgrProxyX/DiagcMgrProxyApplX/DiagcMgrProxyApplXPer1/Update
the DiagcSts/For Number of NTCs/Update DiagcSts and Ramp Response/Update
Latest Values/ProcessRampResponse”

## GLObAL Function \#2

|                      |                     |        |     |     |
|----------------------|---------------------|--------|-----|-----|
| **Function Name**    | DiagcMgrSetBits_u16 | Type   | Min | Max |
| **Arguments Passed** | Data                | uint16 | 0   | 511 |
|                      | BitMask             | Uint16 | 0   | 511 |
| **Return Value**     | Data                | Uint16 | 0   | 511 |

## Description

This function will set bits based on the passed BitMask for a uint16
datatype.

## GLObAL Function \#3

|                      |                     |       |     |     |
|----------------------|---------------------|-------|-----|-----|
| **Function Name**    | DiagcMgrSetBits_u08 | Type  | Min | Max |
| **Arguments Passed** | Data                | Uint8 | 0   | 255 |
|                      | BitMask             | Uint8 | 0   | 255 |
| **Return Value**     | Data                | Uint8 | 0   | 255 |

## Description

This function will set bits based on the passed BitMask for a uint8
datatype

## GLObAL Function \#4

|                      |                     |       |     |     |
|----------------------|---------------------|-------|-----|-----|
| **Function Name**    | DiagcMgrClrBits_u08 | Type  | Min | Max |
| **Arguments Passed** | Data                | Uint8 | 0   | 255 |
|                      | BitMask             | Uint8 | 0   | 255 |
| **Return Value**     | Data                | Uint8 | 0   | 255 |

## Description

This function will clear bits based on the passed BitMask for a uint8
datatype

## GLObAL Function \#5

|                      |                     |       |     |     |
|----------------------|---------------------|-------|-----|-----|
| **Function Name**    | DiagcMgrReadBit_u08 | Type  | Min | Max |
| **Arguments Passed** | Data                | Uint8 | 0   | 255 |
|                      | BitMask             | Uint8 | 0   | 255 |
| **Return Value**     | Data                | Uint8 | 0   | 255 |

## Description

This function will return TRUE if any bits are set based on the passed
BitMask for a uint8 datatype

## GLObAL Function \#6

|                      |                     |        |     |     |
|----------------------|---------------------|--------|-----|-----|
| **Function Name**    | DiagcMgrReadBit_u16 | Type   | Min | Max |
| **Arguments Passed** | Data                | uint16 | 0   | 511 |
|                      | BitMask             | Uint16 | 0   | 511 |
| **Return Value**     | Data                | Uint16 | 0   | 511 |

## Description

This function will return TRUE if any bits are set based on the passed
BitMask for a uint16 datatype

## TRANSIENT FUNCTIONS 

*None*

# Known Limitations With Design

1.  Per the FDD author, safety critical data is protected in an
    exclusive area but there is a possibility of corruption of non
    critical data.

2.  Refer to Design Rationale section on the top level of DiagcMgr
    Simulink model.

3.  GetErrorStatus() for NVM block isnt used in the FDD because

    1.  Default block is used that resets appln crc to zero, so the
        latch counter array will get reset as it will enter the
        condition swapplcrc!=nvmapplcrc

    2.  Above point assumed that a valid swapplncrc will never be zero

    3.  It is known and noted that if there is an nvm read problem while
        ntcs are set we clear the ntcs as well

4.  This design does not support having multiple Flash application CRC
    regions being allowed to set latching ntcs \[Note: As of today, no
    programs have more than 1 Flash application crc region\]

5.  DiagcMgr_Cfg.c and DiagcMgr_Cfg.h files define the NTC arrays as
    uint16 (base type of NtcNrwithResd1) arrays instead of the
    NtcNrResd1 type arrays because they do not have visibility to Rte
    types. \[Not actually a design limitation : noted here for future
    reference\]

6.  In v3.0.0 of the implementation it was found that the
    DiagcMgr_Cfg_Private.h file was being included in the integration
    project’s Rte_UserTypes.h file because of the need for visibility to
    the Ary Types that are defined as typedefs in there. At that point
    it was decided that it was better to rename it as DiagcMgr_Cfg.h
    file instead. \[Not actually a design limitation : noted here for
    future reference\]

7.  

```{=html}
<!-- -->
```
1.  <span id="__RefHeading___Toc481665925" class="anchor"></span>UNIT
    TEST CONSIDERATION

```{=html}
<!-- -->
```
1.  

2.  

3.  For SetNtcStsCore_Oper: The input value of the lower 8 bits of each
    element of PrmDiagcMgrFltResp_u16 calibration while unit testing
    this runnable should be such that its maximum is
    \[sizeof(DTCENAMASK)-1\] and minimum is 0.

# Appendix

*None*

{% endraw %}