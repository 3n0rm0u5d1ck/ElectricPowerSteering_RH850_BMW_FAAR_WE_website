---
layout: default
title: DiagcMgr_IntegrationManual
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**Diagnostic Manager**

**VERSION:** **7.0**

**DATE:** **26-APR-2017**

**Prepared By:**

**Shruthi Raghavan,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

<table>
<colgroup>
<col style="width: 8%" />
<col style="width: 49%" />
<col style="width: 17%" />
<col style="width: 9%" />
<col style="width: 14%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Sl. No.</strong></td>
<td><strong>Description</strong></td>
<td><strong>Author</strong></td>
<td><strong>Version</strong></td>
<td><strong>Date</strong></td>
</tr>
<tr class="even">
<td>1</td>
<td>Initial version</td>
<td>Spandana Balani</td>
<td>1.0</td>
<td>23-Apr-2015</td>
</tr>
<tr class="odd">
<td>2</td>
<td>Updated to FDD version 2</td>
<td>Spandana Balani</td>
<td>2.0</td>
<td>11-Mar-2016</td>
</tr>
<tr class="even">
<td>3</td>
<td>Updated to FDD version 3</td>
<td>Spandana Balani</td>
<td>3.0</td>
<td>22-APR-2016</td>
</tr>
<tr class="odd">
<td>4</td>
<td>Updated to FDD version 4</td>
<td>Spandana Balani</td>
<td>4.0</td>
<td>22-Jun-2016</td>
</tr>
<tr class="even">
<td>5</td>
<td>Added new parameter in configurator</td>
<td>Spandana Balani</td>
<td>5.0</td>
<td>30-Nov-2016</td>
</tr>
<tr class="odd">
<td>6</td>
<td>Remove Nvm block id for SnpshtDataAry</td>
<td>Spandana Balani</td>
<td>6.0</td>
<td>07-Dec-2016</td>
</tr>
<tr class="even">
<td>7</td>
<td><p>Add Nvm block id for new LtchCntrAry NVM</p>
<p>Added runnable scheduling for added runnables</p></td>
<td>Shruthi Raghavan</td>
<td>7.0</td>
<td>26-APR-2017</td>
</tr>
</tbody>
</table>

Table of Contents

[1 Abbrevations And Acronyms 4](#abbrevations-and-acronyms)

[2 References 5](#references)

[3 Dependencies 6](#dependencies)

[3.1 SWCs 6](#swcs)

[3.2 Global Functions(Non RTE) to be provided to Integration Project
6](#global-functionsnon-rte-to-be-provided-to-integration-project)

[4 Configuration REQUIREMeNTS 7](#configuration-requirements)

[4.1 Build Time Config. 7](#build-time-config.)

[4.2 Configuration Files to be provided by Integration Project
7](#configuration-files-to-be-provided-by-integration-project)

[4.3 Da Vinci Parameter Configuration Changes
7](#da-vinci-parameter-configuration-changes)

[4.4 DaVinci Interrupt Configuration Changes
8](#davinci-interrupt-configuration-changes)

[4.5 Manual Configuration Changes 8](#manual-configuration-changes)

[5 Integration DATAFLOW REQUIREMENTS
9](#integration-dataflow-requirements)

[5.1 Required Global Data Inputs 9](#required-global-data-inputs)

[5.2 Required Global Data Outputs 9](#required-global-data-outputs)

[5.3 Specific Include Path present 9](#specific-include-path-present)

[6 Runnable Scheduling 10](#runnable-scheduling)

[7 Memory Map REQUIREMENTS 11](#memory-map-requirements)

[7.1 Mapping 11](#mapping)

[7.2 Usage 11](#usage)

[7.3 NvM Blocks 11](#nvm-blocks)

[8 Compiler Settings 12](#compiler-settings)

[8.1 Preprocessor MACRO 12](#preprocessor-macro)

[8.2 Optimization Settings 12](#optimization-settings)

[9 Appendix 13](#appendix)

# Abbrevations And Acronyms

|                  |                           |
|------------------|---------------------------|
| **Abbreviation** | **Description**           |
| DFD              | Design functional diagram |
| MDD              | Module design Document    |
|                  |                           |
|                  |                           |
|                  |                           |

# References

This section lists the title & version of all the documents that are
referred for development of this document

|             |                                      |                                                                                                                                                                                                                              |
|--------|-----------------------------|------------------------------------|
| **Sr. No.** | **Title**                            | **Version**                                                                                                                                                                                                                  |
| 1           | MDD Guidelines                       | See process v04.04.02 document from eRoom [here](http://eroom.nexteer.com/eRoomReq/Files/Nexteer-ProductLineSystems/ProcessDocumentsSystemsElectronicSystems/0_35a47/MDD%20Guideline%20EA4%2001.00.01.docx)                  |
| 2           | EA4 Software Naming Conventions      | See process v04.04.02 document from eRoom [here](http://eroom.nexteer.com/eRoomReq/Files/Nexteer-ProductLineSystems/ProcessDocumentsSystemsElectronicSystems/0_35e15/EA4%20Software%20Naming%20Conventions%2001.01.00.docx)  |
| 3           | Software Design And Coding standards | See process v04.04.02 document from eRoom [here](http://eroom.nexteer.com/eRoomReq/Files/Nexteer-ProductLineSystems/ProcessDocumentsSystemsElectronicSystems/0_35a2f/Software%20Design%20and%20Coding%20Standards%202.1.doc) |
| 4           | FDD – ES101A Diagnostic Manager      | See Synergy Design Subproject Version                                                                                                                                                                                        |
|             |                                      |                                                                                                                                                                                                                              |

# Dependencies

## SWCs

|            |                      |
|------------|----------------------|
| **Module** | **Required Feature** |
| **None**   | N/A                  |

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
referred. Developer should track the references.

## Global Functions(Non RTE) to be provided to Integration Project

DiagcMgrPwrDwn() –Non RTE Server Runnable, called from BswM.

It calls "SetRamBlockSts" Non-RTE version (NvMProxy_SetRamBlockStatus).

RestoreNtcFltAryDft() , RestoreSnpshtAryDft(),
RestoreDiagcMgrLtchCntrAryDft () – Non RTE Server Runnables (callback
functions), called from Nvm Manager if the Nvm Data is corrupted.

# Configuration REQUIREMeNTS

Only proxies components that have active NTCs should be brought into
developer worksace. Stub needs to be integrated for connection to the
core's client ports for all the un-implemented applications. Proper .gpj
fles needs to be selected for inclusion in the project’s .gpj file.

The Integrator must configure one and only one
“/Nexteer/EcucDefs_DiagcMgr/DiagcMgr/DTCEnaCndn” for configured DTC in
the DEM

## Build Time Config.

|             |           |     |
|-------------|-----------|-----|
| **Modules** | **Notes** |     |
| **None**    |           |     |

## Configuration Files to be provided by Integration Project

DiagcMgr_Cfg.h

DiagcMgr_Cfg.c

Note: Include “DiagcMgr_Cfg.h” in the “Rte_UserTypes.h” header file

## Da Vinci Parameter Configuration Changes

<table>
<colgroup>
<col style="width: 40%" />
<col style="width: 44%" />
<col style="width: 14%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Parameter</strong></td>
<td><strong>Notes</strong></td>
<td><strong>SWC</strong></td>
</tr>
<tr class="even">
<td><strong>/Nexteer/EcucDefs_DiagcMgr/DiagcMgr</strong></td>
<td>Configuration of the DiagcMgr module</td>
<td>DiagcMgr</td>
</tr>
<tr class="odd">
<td><strong>/Nexteer/EcucDefs_DiagcMgr/DiagcMgr/NTCNR</strong></td>
<td>Container with NTC number properties</td>
<td>DiagcMgr</td>
</tr>
<tr class="even">
<td><strong>/Nexteer/EcucDefs_DiagcMgr/DiagcMgr/NTCNR/NTCOsApplicationRef</strong></td>
<td>NTC Os Application. This defines the application corresponding to a
particular NTC</td>
<td>DiagcMgr</td>
</tr>
<tr class="odd">
<td><strong>/Nexteer/EcucDefs_DiagcMgr/DiagcMgr/NTCNR/Debounce</strong></td>
<td>Set to true if NTC is type debounce</td>
<td>DiagcMgr</td>
</tr>
<tr class="even">
<td><strong>/Nexteer/EcucDefs_DiagcMgr/DiagcMgr/NTCNR/LtchgEna</strong></td>
<td>Set to true if NTC is latched. Currently only a maximum of 20
Latching NTCs are supported in a project.</td>
<td>DiagcMgr</td>
</tr>
<tr class="odd">
<td><strong>/Nexteer/EcucDefs_DiagcMgr/DiagcMgr/NTCNR/LtchCntrThd</strong></td>
<td>Set a value between 1-255 if NTC is latching. Else, the value is
ignored &amp; written as 0XFF in the generated file by default when
needed.</td>
<td>DiagcMgr</td>
</tr>
<tr class="even">
<td><strong>/Nexteer/EcucDefs_DiagcMgr/DiagcMgr/NTCNR/MfgNtcInhibInNonOper</strong></td>
<td>Boolean Value of &lt;Mfg NTC Inhibit Non-Operate States&gt; column
for corresponding NTC in the NTC Master List of the project.</td>
<td>DiagcMgr</td>
</tr>
<tr class="odd">
<td><strong>/Nexteer/EcucDefs_DiagcMgr/DiagcMgr/NTCNR/MfgNtcInhibInOper</strong></td>
<td>Boolean Value of &lt;Mfg NTC Inhibit Operate State&gt; column for
corresponding NTC in the NTC Master List of the project.</td>
<td>DiagcMgr</td>
</tr>
<tr class="even">
<td><strong>/Nexteer/EcucDefs_DiagcMgr/DiagcMgr/NTCNR/NtcPwrCycLtch</strong></td>
<td>Boolean Value of &lt;NTC Power Cycle Latch&gt; column for
corresponding NTC in the NTC Master List of the project.</td>
<td>DiagcMgr</td>
</tr>
<tr class="odd">
<td><strong>/Nexteer/EcucDefs_DiagcMgr/DiagcMgr/DTCEnaCndn</strong></td>
<td>Container with DTC ENABLE Criteria</td>
<td>DiagcMgr</td>
</tr>
<tr class="even">
<td><strong>/Nexteer/EcucDefs_DiagcMgr/DiagcMgr/DTCEnaCndn/DTC</strong></td>
<td>This defines the DEM DTC Class.</td>
<td>DiagcMgr</td>
</tr>
<tr class="odd">
<td><strong>/Nexteer/EcucDefs_DiagcMgr/DiagcMgr/DTCEnaCndn/Bit_X<sup>1</sup></strong></td>
<td>Set to true if Enable Condition for Bit X<sup>1</sup> is applicable
to configured DTC</td>
<td>DiagcMgr</td>
</tr>
<tr class="even">
<td><strong>/Nexteer/EcucDefs_DiagcMgr/DiagcMgr/DTCEnaCndn/DiagcMgrDTCIdx</strong></td>
<td>Value represents index value DiagcMgr uses internally for NTC
mapping to DTCs to the Event ID that the Dem identifies for a particular
DTC</td>
<td>DiagcMgr</td>
</tr>
<tr class="odd">
<td><strong>/Nexteer/EcucDefs_DiagcMgr/DiagcMgr/DiagcMgrGeneral</strong></td>
<td>Container with General DiagcMgr configuration</td>
<td>DiagcMgr</td>
</tr>
<tr class="even">
<td><strong>/Nexteer/EcucDefs_DiagcMgr/DiagcMgr/DiagcMgrGeneral/DIAGCMGR_DEMCHK</strong></td>
<td><p>Set to true to enable DET consistency check between DEM and
DiagcMgr DTC configuration.</p>
<p>This check assumes the Dem will generate the constant table named”
Dem_C_DtcTable” that will be sized to the configured DTCs + 1. If this
assumption is not true, turn this parameter OFF.</p></td>
<td>DiagcMgr</td>
</tr>
<tr class="odd">
<td><strong>/Nexteer/EcucDefs_DiagcMgr/DiagcMgr/DiagcMgrGeneral/DEMTOTNROFDTC</strong></td>
<td>This needs to be configured to an expression that would result in
the total number DTCs that are configured in the system based on
generated Dem code</td>
<td>DiagcMgr</td>
</tr>
</tbody>
</table>

**^1^** Note: X = \_0 to 15

## DaVinci Interrupt Configuration Changes

|              |            |                         |           |
|--------------|------------|-------------------------|-----------|
| **ISR Name** | **VIM \#** | **Priority Dependency** | **Notes** |
| **N/A**      |            |                         |           |

## Manual Configuration Changes

|              |           |         |
|--------------|-----------|---------|
| **Constant** | **Notes** | **SWC** |
| **N/A**      |           |         |

# Integration DATAFLOW REQUIREMENTS

## Required Global Data Inputs

Refer DataDict.m file

## Required Global Data Outputs

Refer DataDict.m file

## Specific Include Path present

Yes

# Runnable Scheduling 

This section specifies the required runnable scheduling.

|                            |                                                                                                                                                                |             |
|------------------|----------------------------------------------|--------|
| **Init**                   | **Scheduling Requirements**                                                                                                                                    | **Trigger** |
| **DiagcMgProxyApplXInit1** | Init function needs to run before any other init function that is trying to set an NTC and it therefore should be called early on in the initialization tasks. | Rte_Init    |
| **DiagcMgrInit1**          | To be scheduled after CM102A init & after DiagcMgrProxyApplXInit1^1^                                                                                           | RTE Init    |

|                                       |                               |                         |
|-------------------------|------------------------------|------------------|
| **Runnable**                          | **Scheduling Requirements**   | **Trigger**             |
| **DiagcMgrPer1**                      | None                          | RTE 2ms Task            |
| **DiagcMgrPer2**                      | None                          | RTE 100ms Task          |
| **ClrAllDiagc_Oper**                  | Server Runnable               | Client Call             |
| **ClrLtchCntrData_Oper**              | Server Runnable               | Client Call             |
| **ClrSnpshtData_Oper**                | Server Runnable               | Client Call             |
| **CnvSnpshtData\_\<Type\>^3,5^**      | Server Runnable               | Client Call             |
| **DiagcMgrIninCore_Oper**             | Server Runnable               | Internal to DiagcMgr^2^ |
| **GetNtcActvCore_Oper**               | Server Runnable               | Internal to DiagcMgr^2^ |
| **GetNtcQlfrStsCore_Oper**            | Server Runnable               | Internal to DiagcMgr^2^ |
| **GetNtcStsCore_Oper**                | Server Runnable               | Internal to DiagcMgr^2^ |
| **ReadNtcFltAryCore_Oper^3^**         | Server Runnable               | Client Call             |
| **ReadNtcInfoAndDebCntr_Oper^3^**     | Server Runnable               | Client Call             |
| **ReadSnpshtData_Oper**               | Server Runnable               | Client Call             |
| **SetNtcStsCore_Oper**                | Server Runnable               | Internal to DiagcMgr^2^ |
| **DiagcMgrPwrDwn**                    | Non RTE Server Runnable       | Client Call             |
| **RestoreNtcFltAryDft**               | Non RTE Server Runnable       | Client Call             |
| **RestoreDiagcMgrLtchCntrAryDft**     | Non RTE Server Runnable       | Client Call             |
| **ReadLtchCntrData**                  | Server Runnable               | Client Call             |
| **RestoreSnpshtAryDft**               | Non RTE Server Runnable       | Client Call             |
| **DiagcMgrProxyApplXInit1^1^**        | Schedule before DiagcMgrInit1 | RTE Init                |
| **DiagcMgrProxyApplXPer1^1^**         | None                          | RTE 10ms Task           |
| **GetDiagcDataApplX_Oper^1^**         | Server Runnable               | Internal to DiagcMgr^2^ |
| **GetNtcActvX_Oper^1,3^**             | Server Runnable               | Client Call             |
| **GetNtcDebCntrAppl0_Oper^1^**        | Server Runnable               | Client Call             |
| **GetNtcInfoApplX_Oper^1^**           | Server Runnable               | Internal to DiagcMgr^2^ |
| **GetNtcQlfrStsX_Oper^1,3^**          | Server Runnable               | Client Call             |
| **GetNtcStsX_Oper^1,3^**              | Server Runnable               | Client Call             |
| **SetNtcStsX_Oper^1,3^**              | Server Runnable               | Client Call             |
| **SetNtcStsAndSnpshtDataX_Oper^1,3^** | Server Runnable               | Client Call             |
| **UpdDtcEnaCdn^4^**                   | Non RTE Server Runnable       | Client Call             |

^1^X in the Runnable name represent the application number. There 11
applications (0 to 10) and each application has a ProxyDiagcMgr
component. One set of these server runnables exist in each proxy
component.

^2^Runnables with trigger ‘Internal to DiagcMgr’ are local to DiagcMgr
main component and 11 proxy components, other components will not have
access to these functions. Whenever a component inside an application
calls one of the server runnables, the ProxyDiagcMgr of that application
will make a client call to the DiagcMgr main component.

^3^These Server Runnables must be defined with “can be invoked
concurrently” enabled in Developer.

^4^This function is assumed to be called by bswm providing periodic
updates of DTC enable condition.

DTC enable conditions should be defined by the fault code requirement.

^5^The \<Type\> in this function can be f32,logl,s08,s16,s32,u08 or u16

# Memory Map REQUIREMENTS

## Mapping

|                                                   |                 |           |
|------------------------------------|------------------|------------------|
| **Memory Section**                                | **Contents**    | **Notes** |
| **GlobalShared_START_SEC_VAR_NOINIT_UNSPECIFIED** | SnpshtDataAry_M |           |
|                                                   |                 |           |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

|                            |         |         |
|----------------------------|---------|---------|
| **Feature**                | **RAM** | **ROM** |
| **\<Memmap usuage info\>** |         |         |

Table 1: ARM Cortex R4 Memory Usage

## NvM Blocks

\*See DataDict.m

1\. This component assumes that the integrator will keep the default NvM
block name and the Block ID name will be
"NvMConf_NvMBlockDescriptor_Rte_NvmBlock_DiagcMgr_DiagcMgrNtcFltAry” and
“NvMConf_NvMBlockDescriptor_Rte_NvmBlock_DiagcMgr_DiagcMgrLtchCntrAry”
2. The shadow RAM for SnpshtDataAry NVM lives in the global variable
SnpshtDataAry_M. This should be mapped appropriately.

# Compiler Settings

##  Preprocessor MACRO

None

## Optimization Settings

None

# Appendix

1.  There is the following compiler warning shows up in the compilation
    of DiagcMgr.c.  
    <img
    src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/ES101A_DiagcMgr_Impl/doc/mediax/media/image1.png"
    style="width:5.46736in;height:0.64722in" />  
    **<u>Justification:</u>** The intention of CnvSnpshtData_f32_Oper
    server runnable is to retain the bits of the single precision float
    input argument as is in the uint32 output. Typecasting the float32
    input to uint32 will not preserve the bits as intended hence this
    type of casting is required.

> **<u>Note:</u>** We are deviating from MISRA Rule 11.4 (refer static
> analysis guideline D 11.4.5)

1.  The components that need to be integrated/ brought into the
    developer project are:

    1.  DiagcMgr

    2.  DiagcMgrStub

    3.  DiagcMgrProxyApplX for each application(#X) that exists in the
        project.

> **<u>Note:</u>** In DiagcMgr davinci component interface, only the
> client ports of applications that are present in the project will have
> server ports to connect to. All the client ports that do not have the
> corresponding application in the project need to be connected to the
> corresponding server port in DiagcMgr_Stub component.

{% endraw %}