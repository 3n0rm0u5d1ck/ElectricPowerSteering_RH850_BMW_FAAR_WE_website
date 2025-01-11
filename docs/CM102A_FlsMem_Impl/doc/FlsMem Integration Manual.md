---
layout: default
title: FlsMem Integration Manual
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**FlsMem**

**VERSION: 8**

**DATE:** **05/17/17**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                                                                                         |                |             |            |
|-----|--------------------|--------------------|---------|--------------------|
| **Sl. No.** | **Description**                                                                         | **Author**     | **Version** | **Date**   |
| 1           | Initial version                                                                         | Lucas Wendling | 1           | 10/07/15   |
| 2           | Updated with changes for DTS configuration for Flash CRC check                          | Avinash James  | 2           | 03/18/16   |
| 3           | Removed FlsMemCodFlsSngBit handling                                                     | Avinash James  | 3           | 03/31/16   |
| 4           | Added Trusted function for DTS clean up                                                 | Avinash James  | 4           | 04/18/16   |
| 5           | Added Single bit ECC error handler and name correction for trusted funcions             | Avinash James  | 5           | 08/26/2016 |
| 6           | Added micro diagnostic support and also made the configuration to accept linker symbols | Avinash James  | 6           | 03/17/2017 |
| 7           | Added config param for application region CRC array Index                               | Avinash James  | 7           | 04/10/17   |
| 8           | Added more notes about DMA write section mapping                                        | Lucas Wendling | 8           | 05/17/17   |

Table of Contents

[1 Abbrevations And Acronyms 4](#abbrevations-and-acronyms)

[2 References 5](#references)

[3 Dependencies 6](#dependencies)

[3.1 SWCs 6](#swcs)

[3.2 Global Functions(Non RTE) to be provided to Integration Project
6](#global-functionsnon-rte-to-be-provided-to-integration-project)

[4 Configuration REQUIREMeNTS 7](#configuration-requirements)

[4.1 Build Time Config 7](#build-time-config)

[4.2 Configuration Files to be provided by Integration Project
7](#configuration-files-to-be-provided-by-integration-project)

[4.3 Da Vinci Parameter Configuration Changes
7](#da-vinci-parameter-configuration-changes)

[4.4 DaVinci Interrupt Configuration Changes
8](#__RefHeading___Toc477509000)

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

|                  |                            |
|------------------|----------------------------|
| **Abbreviation** | **Description**            |
| DFD              | Design functional diagram  |
| MDD              | Module design Document     |
| FDD              | Functional Design Document |
| CCT              | Common Checksum Tool       |
|                  |                            |

# References

This section lists the title & version of all the documents that are
referred for development of this document

|             |                             |                                |
|-------------|-----------------------------|--------------------------------|
| **Sr. No.** | **Title**                   | **Version**                    |
| 1           | FDD – CM102A FlsMem         | See Synergy subproject version |
| 2           | Software Naming Conventions | Process 04.04.02               |
| 3           | Software Coding Standards   | Process 04.04.02               |
|             |                             |                                |
|             |                             |                                |

# Dependencies

## SWCs

|                            |                                                    |
|-----------------------|-------------------------------------------------|
| **Module**                 | **Required Feature**                               |
| **AR202A MicroCtrlrSuprt** | NxtrMcuSuprtLib functions and register definitions |
| **CM800A SyncCrc**         | CRC HW Module Configuration and Allocation         |

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
referred. Developer should track the references.

## Global Functions(Non RTE) to be provided to Integration Project

DtsInin - To be defined as a trusted function as the DTS Channel master
registers need to be configured in the supervisor mode.

DtsClnUp - To be defined as a trusted function as the DTS registers are
being re-configured in the supervisor mode to avoid access protection
violation

CodFlsSngBitEcc – Single bit code flash ECC error handler call back
function provided to the MCAL driver

# Configuration REQUIREMeNTS

## Build Time Config

|                    |                                     |     |
|--------------------|-------------------------------------|-----|
| **Modules**        | **Notes**                           |     |
| **MCUDIAGCERRINJ** | STD_ON for micro diag special build |     |
|                    | STD_OFF for all other builds        |     |

## Configuration Files to be provided by Integration Project

CDD_FlsMem_Cfg.c

CDD_FlsMem_Cfg_private.h

## Da Vinci Parameter Configuration Changes

<table>
<colgroup>
<col style="width: 30%" />
<col style="width: 44%" />
<col style="width: 24%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Parameter</strong></td>
<td><strong>Notes</strong></td>
<td><strong>SWC</strong></td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>/Nexteer/FlsMem/FlashCRCRegnConfig/ StartAddress</td>
<td><p>Configured with “FlashCRCRegnConfig”</p>
<p>Each Flash region(for eg:- Boot, App, Cal1) has a start address where
the code resides on the flash</p></td>
<td>FlsMem</td>
</tr>
<tr class="even">
<td>/Nexteer/FlsMem/FlashCRCRegnConfig/Length</td>
<td><p>Configured with “FlashCRCRegnConfig”</p>
<p>Each Flash region has a length defined for the region</p></td>
<td>FlsMem</td>
</tr>
<tr class="odd">
<td>/Nexteer/FlsMem/FlashCRCRegnConfig/PredefinedCrcAddress</td>
<td><p>Configured with “FlashCRCRegnConfig”</p>
<p>Each Flash region has a PredefinedCrcAddress defined for the region
which is used by the CCT tool for storing the checksum on the flash and
serves as the reference location to retrieve the pre calculated CRC and
do a comparison with calculated CRC</p></td>
<td>FlsMem</td>
</tr>
<tr class="even">
<td>/Nexteer/FlsMem/FlashCRCRegnConfig/LengthSymbol</td>
<td><p>Configured with “FlashCRCRegnConfig”</p>
<p>Each Flash region has a length defined for the region and accepts
linker symbols</p></td>
<td>FlsMem</td>
</tr>
<tr class="odd">
<td>/Nexteer/FlsMem/FlashCRCRegnConfig/PredefinedCrcAddressSymbol</td>
<td><p>Configured with “FlashCRCRegnConfig”</p>
<p>Each Flash region has a PredefinedCrcAddress defined for the region
which is used by the CCT tool for storing the checksum on the flash and
serves as the reference location to retrieve the pre calculated CRC and
do a comparison with calculated CRC and accepts linker symbols</p></td>
<td>FlsMem</td>
</tr>
<tr class="even">
<td>/Nexteer/FlsMem/FlashCRCRegnConfig/StartingAddressSymbol</td>
<td><p>Configured with “FlashCRCRegnConfig”</p>
<p>Each Flash region(for eg:- Boot, App, Cal1) has a start address where
the code resides on the flash and accepts linker symbol</p></td>
<td>FlsMem</td>
</tr>
<tr class="odd">
<td>/Nexteer/FlsMem/FlashCRCRegnConfig/UseSymbolName</td>
<td>Configured with “FlashCRCRegnConfig” to select either the symbol
names or the actual values</td>
<td>FlsMem</td>
</tr>
<tr class="even">
<td><p>/Renesas/EcucDefs_Mcu/Mcu/McuModuleConfiguration</p>
<p>/McuEcmErrorSourcesCfg/McuEcmErrorSource36</p></td>
<td>Call back function name is “CodFlsSngBitEcc”. Refer the CM104A
Integration manual for the configuration of the error source. (Type of
the error, classification of the error eg FENMI or EI information)
.</td>
<td></td>
</tr>
<tr class="odd">
<td>/Nexteer/FlsMem/ApplCRCRegnIdx/ApplCrcRegnNr</td>
<td>The array Index for the application region CRC region
definition</td>
<td>FlsMem</td>
</tr>
</tbody>
</table>

## DaVinci Interrupt Configuration Changes

|              |            |                         |           |
|--------------|------------|-------------------------|-----------|
| **ISR Name** | **VIM \#** | **Priority Dependency** | **Notes** |
|              |            |                         |           |

## Manual Configuration Changes

|              |           |         |
|--------------|-----------|---------|
| **Constant** | **Notes** | **SWC** |
| **None**     |           |         |

# Integration DATAFLOW REQUIREMENTS

## Required Global Data Inputs

None

## Required Global Data Outputs

None

## Specific Include Path present

Yes

# Runnable Scheduling 

This section specifies the required runnable scheduling.

|                 |                                            |                                   |
|-------------------|---------------------------------------|---------------|
| **Init**        | **Scheduling Requirements**                | **Trigger**                       |
| **FlsMemInit1** | None                                       | Once At Init (RTE)                |
| **FlsMemInit2** | Non-RTE Init, Called in Startup Sequence\* | Function call in Startup Sequence |

|                |                             |             |
|----------------|-----------------------------|-------------|
| **Runnable**   | **Scheduling Requirements** | **Trigger** |
| **FlsMemPer2** | None                        | 100ms(RTE)  |

\*“FlsMemInit2” shall schedule after OS Start – Refer CM100A Start up
sequence.

PEG shall be configured before “FlsMemInit2”.

CrcHw Init shall be scheduled before “FlsMemInit2”.

**FlsMemInit1 should be called before DiagcMgrInit1**

# Memory Map REQUIREMENTS

## Mapping

<table>
<colgroup>
<col style="width: 46%" />
<col style="width: 16%" />
<col style="width: 36%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Memory Section</strong></td>
<td><strong>Contents</strong></td>
<td><strong>Notes</strong></td>
</tr>
<tr class="even">
<td><strong>CDD_FlsMem_START_SEC_CODE</strong></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><strong>CDD_FlsMemNonRte_START_SEC_VAR_INIT_128</strong></td>
<td>Data that a DMA channel writes to during CRC test</td>
<td><p>This gets mapped to a “.data_dma_128” section and/or a
“.sdata_dma_128” section (depending on compiler settings) that will need
to be explicitly added to the linker file. The intent of these sections
is to be placed in a RAM memory section that only the DMA has write
access to (processor in user mode only has read access).</p>
<p>Additionally, since these are initialized data sections, the
appropriate ROM sections will need to be added to the linker to allow
initial values to be copied from Flash to RAM during startup for these
sections.</p>
<p>e.g.:</p>
<p><em>.ROM_data_dma_128 ROM(.data_dma_128) FILL(0xFF) :{}&gt;.</em></p>
<p>and</p>
<p><em>.ROM_sdata_dma_128 ROM(.sdata_dma_128) FILL(0xFF)
:{}&gt;.</em></p></td>
</tr>
</tbody>
</table>

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

|             |         |         |
|-------------|---------|---------|
| **Feature** | **RAM** | **ROM** |
|             |         |         |

Table 1: ARM Cortex R4 Memory Usage

## NvM Blocks

\*See DataDict.m

# Compiler Settings

##  Preprocessor MACRO

None

## Optimization Settings

None

# Appendix

{% endraw %}