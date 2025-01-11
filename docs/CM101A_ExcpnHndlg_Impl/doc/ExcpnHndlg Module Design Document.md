---
layout: default
title: ExcpnHndlg Module Design Document
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**ExcpnHndlg**

**04-Apr-2018**

**Prepared By:**

**Shruthi Raghavan,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                                                                                                                              |                    |             |              |
|----------------------------------------|--------------|--------|-----------|
| **Description**                                                                                                              | **Author**         | **Version** | **Date**     |
| Initial Version                                                                                                              | Avinash James      | 1.0         | 05-Apr-2016  |
| Updated the \#define for ECC single bit code flash fault                                                                     | Avinash James      | 2.0         | 18-Apr-2016  |
| Updated for v3.2.0 of the FDD                                                                                                | Selva Sengottaiyan | 3.0         | 24-June-2016 |
| Updated for v4.0.0 of the FDD                                                                                                | Avinash James      | 4.0         | 17-Aug-2016  |
| Updated to remove constants that were used for parameter byte for CVM startup tests because this test is removed from CM101A | Shruthi Raghavan   | 5.0         | 18-May-2017  |
| Added constants for the handling of code flash register write MCAL failure.                                                  | Shruthi Raghavan   | 6.0         | 25-May-2017  |
| Removed the ProcEcmRst Function                                                                                              | Avinash James      | 7.0         | 25-Jul-2017  |
| Added local constants                                                                                                        | Avinash James      | 8.0         | 21-Sep-2017  |
| Added handler for DTS single bit ECC error                                                                                   | Avinash James      | 9.0         | 04-Apr-2018  |

**  
**

<u>Table of Contents</u>[1 Introduction
[7](#introduction)](#introduction)

[1.1 Purpose [7](#purpose)](#purpose)

[2 ExcpnHndlg & High-Level Description
[8](#excpnhndlg-high-level-description)](#excpnhndlg-high-level-description)

[3 Design details of software module
[9](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of ExcpnHndlg
[9](#graphical-representation-of-excpnhndlg)](#graphical-representation-of-excpnhndlg)

[3.2 Data Flow Diagram [9](#data-flow-diagram)](#data-flow-diagram)

[3.2.1 Component level DFD
[9](#component-level-dfd)](#component-level-dfd)

[3.2.2 Function level DFD [9](#function-level-dfd)](#function-level-dfd)

[4 Constant Data Dictionary
[10](#constant-data-dictionary)](#constant-data-dictionary)

[4.1 Program (fixed) Constants
[10](#program-fixed-constants)](#program-fixed-constants)

[4.1.1 Embedded Constants
[10](#embedded-constants)](#embedded-constants)

[5 Software Component Implementation
[14](#software-component-implementation)](#software-component-implementation)

[5.1 Sub-Module Functions
[14](#sub-module-functions)](#sub-module-functions)

[5.1.1 Init: ExcpnHndlgInit1
[14](#init-excpnhndlginit1)](#init-excpnhndlginit1)

[5.1.1.1 Design Rationale [14](#design-rationale)](#design-rationale)

[5.1.1.2 Module Outputs [14](#module-outputs)](#module-outputs)

[5.1.2 Init: ExcpnHndlgInit2
[14](#init-excpnhndlginit2)](#init-excpnhndlginit2)

[5.1.2.1 Design Rationale
[14](#design-rationale-1)](#design-rationale-1)

[5.1.2.2 Module Outputs [14](#module-outputs-1)](#module-outputs-1)

[5.1.3 Per: ExcpnHndlgPer1
[14](#per-excpnhndlgper1)](#per-excpnhndlgper1)

[5.1.3.1 Design Rationale
[14](#design-rationale-2)](#design-rationale-2)

[5.1.3.2 Store Module Inputs to Local copies
[14](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[5.1.3.3 (Processing of function)………
[14](#processing-of-function)](#processing-of-function)

[5.1.3.4 Store Local copy of outputs into Module Outputs
[14](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[5.2 Server Runables [14](#server-runables)](#server-runables)

[5.2.1 ChkForStrtUpTest [14](#chkforstrtuptest)](#chkforstrtuptest)

[5.2.1.1 Design Rationale
[14](#design-rationale-3)](#design-rationale-3)

[5.2.1.2 (Processing of function)………
[14](#processing-of-function-1)](#processing-of-function-1)

[5.2.2 FeNmiClkMonr0RtLowrLimFlt
[15](#fenmiclkmonr0rtlowrlimflt)](#fenmiclkmonr0rtlowrlimflt)

[5.2.2.1 Design Rationale
[15](#design-rationale-4)](#design-rationale-4)

[5.2.2.2 (Processing of function)………
[15](#processing-of-function-2)](#processing-of-function-2)

[5.2.3 FeNmiClkMonr0RtUpprLimFlt
[15](#fenmiclkmonr0rtupprlimflt)](#fenmiclkmonr0rtupprlimflt)

[5.2.3.1 Design Rationale
[15](#design-rationale-5)](#design-rationale-5)

[5.2.3.2 (Processing of function)………
[15](#processing-of-function-3)](#processing-of-function-3)

[5.2.4 FeNmiClkMonr1RtLowrLimFlt
[15](#fenmiclkmonr1rtlowrlimflt)](#fenmiclkmonr1rtlowrlimflt)

[5.2.4.1 Design Rationale
[15](#design-rationale-6)](#design-rationale-6)

[5.2.4.2 (Processing of function)………
[15](#processing-of-function-4)](#processing-of-function-4)

[5.2.5 FeNmiClkMonr1RtUpprLimFlt
[15](#fenmiclkmonr1rtupprlimflt)](#fenmiclkmonr1rtupprlimflt)

[5.2.5.1 Design Rationale
[15](#design-rationale-7)](#design-rationale-7)

[5.2.5.2 (Processing of function)………
[15](#processing-of-function-5)](#processing-of-function-5)

[5.2.6 FeNmiClkMonr2RtLowrLimFlt
[15](#fenmiclkmonr2rtlowrlimflt)](#fenmiclkmonr2rtlowrlimflt)

[5.2.6.1 Design Rationale
[15](#design-rationale-8)](#design-rationale-8)

[5.2.6.2 (Processing of function)………
[15](#processing-of-function-6)](#processing-of-function-6)

[5.2.7 FeNmiClkMonr2RtUpprLimFlt
[15](#fenmiclkmonr2rtupprlimflt)](#fenmiclkmonr2rtupprlimflt)

[5.2.7.1 Design Rationale
[15](#design-rationale-9)](#design-rationale-9)

[5.2.7.2 (Processing of function)………
[16](#processing-of-function-7)](#processing-of-function-7)

[5.2.8 FeNmiClkMonr3RtLowrLimFlt
[16](#fenmiclkmonr3rtlowrlimflt)](#fenmiclkmonr3rtlowrlimflt)

[5.2.8.1 Design Rationale
[16](#design-rationale-10)](#design-rationale-10)

[5.2.8.2 (Processing of function)………
[16](#processing-of-function-8)](#processing-of-function-8)

[5.2.9 FeNmiClkMonr3RtUpprLimFlt
[16](#fenmiclkmonr3rtupprlimflt)](#fenmiclkmonr3rtupprlimflt)

[5.2.9.1 Design Rationale
[16](#design-rationale-11)](#design-rationale-11)

[5.2.9.2 (Processing of function)………
[16](#processing-of-function-9)](#processing-of-function-9)

[5.2.10 FeNmiDmaTrf [16](#fenmidmatrf)](#fenmidmatrf)

[5.2.10.1 Design Rationale
[16](#design-rationale-12)](#design-rationale-12)

[5.2.10.2 (Processing of function)………
[16](#processing-of-function-10)](#processing-of-function-10)

[5.2.11 FeNmiDmaRegAcsProtnErr
[16](#fenmidmaregacsprotnerr)](#fenmidmaregacsprotnerr)

[5.2.11.1 Design Rationale
[16](#design-rationale-13)](#design-rationale-13)

[5.2.11.2 (Processing of function)………
[16](#processing-of-function-11)](#processing-of-function-11)

[5.2.12 FeNmiEcmMstChkrCmp
[16](#fenmiecmmstchkrcmp)](#fenmiecmmstchkrcmp)

[5.2.12.1 Design Rationale
[16](#design-rationale-14)](#design-rationale-14)

[5.2.12.2 (Processing of function)………
[16](#processing-of-function-12)](#processing-of-function-12)

[5.2.13 FeNmiOperModErrFlsProgmModStrtd
[17](#fenmiopermoderrflsprogmmodstrtd)](#fenmiopermoderrflsprogmmodstrtd)

[5.2.13.1 Design Rationale
[17](#design-rationale-15)](#design-rationale-15)

[5.2.13.2 (Processing of function)………
[17](#processing-of-function-13)](#processing-of-function-13)

[5.2.14 FeNmiOperModErrSngChipInactv
[17](#fenmiopermoderrsngchipinactv)](#fenmiopermoderrsngchipinactv)

[5.2.14.1 Design Rationale
[17](#design-rationale-16)](#design-rationale-16)

[5.2.14.2 (Processing of function)………
[17](#processing-of-function-14)](#processing-of-function-14)

[5.2.15 FeNmiOperModErrTestModStrtd
[17](#fenmiopermoderrtestmodstrtd)](#fenmiopermoderrtestmodstrtd)

[5.2.15.1 Design Rationale
[17](#design-rationale-17)](#design-rationale-17)

[5.2.15.2 (Processing of function)………
[17](#processing-of-function-15)](#processing-of-function-15)

[5.2.16 FeNmiPeg [17](#fenmipeg)](#fenmipeg)

[5.2.16.1 Design Rationale
[17](#design-rationale-18)](#design-rationale-18)

[5.2.16.2 (Processing of function)………
[17](#processing-of-function-16)](#processing-of-function-16)

[5.2.17 FeNmiWdg [17](#fenmiwdg)](#fenmiwdg)

[5.2.17.1 Design Rationale
[17](#design-rationale-19)](#design-rationale-19)

[5.2.17.2 (Processing of function)………
[17](#processing-of-function-17)](#processing-of-function-17)

[5.2.18 GetMcuDiagcIdnData
[18](#getmcudiagcidndata)](#getmcudiagcidndata)

[5.2.18.1 Design Rationale
[18](#design-rationale-21)](#design-rationale-21)

[5.2.18.2 (Processing of function)………
[18](#processing-of-function-19)](#processing-of-function-19)

[5.2.19 ProcMpuExcpnErr [18](#procmpuexcpnerr)](#procmpuexcpnerr)

[5.2.19.1 Design Rationale
[18](#design-rationale-22)](#design-rationale-22)

[5.2.19.2 (Processing of function)………
[18](#processing-of-function-20)](#processing-of-function-20)

[5.2.20 ProcNonCritOsErr [18](#procnoncritoserr)](#procnoncritoserr)

[5.2.20.1 Design Rationale
[18](#design-rationale-23)](#design-rationale-23)

[5.2.20.2 (Processing of function)………
[18](#processing-of-function-21)](#processing-of-function-21)

[5.2.21 ProcPrmntOsErr [18](#procprmntoserr)](#procprmntoserr)

[5.2.21.1 Design Rationale
[18](#design-rationale-24)](#design-rationale-24)

[5.2.21.2 (Processing of function)………
[18](#processing-of-function-22)](#processing-of-function-22)

[5.2.22 ProcPrvlgdInstrExcpnErr
[18](#procprvlgdinstrexcpnerr)](#procprvlgdinstrexcpnerr)

[5.2.22.1 Design Rationale
[18](#design-rationale-25)](#design-rationale-25)

[5.2.22.2 (Processing of function)………
[18](#processing-of-function-23)](#processing-of-function-23)

[5.2.23 ProcUkwnExcpnErr [19](#procukwnexcpnerr)](#procukwnexcpnerr)

[5.2.23.1 Design Rationale
[19](#design-rationale-26)](#design-rationale-26)

[5.2.23.2 (Processing of function)………
[19](#processing-of-function-24)](#processing-of-function-24)

[5.2.24 SetMcuDiagcIdnData
[19](#setmcudiagcidndata)](#setmcudiagcidndata)

[5.2.24.1 Design Rationale
[19](#design-rationale-27)](#design-rationale-27)

[5.2.24.2 (Processing of function)………
[19](#processing-of-function-25)](#processing-of-function-25)

[5.3 Interrupt Functions
[19](#interrupt-functions)](#interrupt-functions)

[5.3.1 AlgnErrIrq [19](#algnerrirq)](#algnerrirq)

[5.3.1.1 Design Rationale
[19](#design-rationale-28)](#design-rationale-28)

[5.3.1.2 (Processing of the ISR function)…..
[19](#processing-of-the-isr-function..)](#processing-of-the-isr-function..)

[5.3.2 FpuErrIrq [19](#fpuerrirq)](#fpuerrirq)

[5.3.2.1 Design Rationale
[19](#design-rationale-29)](#design-rationale-29)

[5.3.2.2 (Processing of the ISR function)…..
[19](#processing-of-the-isr-function..-1)](#processing-of-the-isr-function..-1)

[5.3.3 SysErrIrq [19](#syserrirq)](#syserrirq)

[5.3.3.1 Design Rationale
[19](#design-rationale-30)](#design-rationale-30)

[5.3.3.2 (Processing of the ISR function)…..
[19](#processing-of-the-isr-function..-2)](#processing-of-the-isr-function..-2)

[5.3.4 ResdOperIrq [20](#resdoperirq)](#resdoperirq)

[5.3.4.1 Design Rationale
[20](#design-rationale-31)](#design-rationale-31)

[5.3.4.2 (Processing of the ISR function)…..
[20](#processing-of-the-isr-function..-3)](#processing-of-the-isr-function..-3)

[5.4 Module Internal (Local) Functions
[20](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 ProcStrtUpOrSwRst [20](#procstrtuporswrst)](#procstrtuporswrst)

[5.4.1.1 Design Rationale
[20](#design-rationale-32)](#design-rationale-32)

[5.4.1.2 Processing [20](#processing)](#processing)

[5.4.2 ProcPinRst [20](#procpinrst)](#procpinrst)

[5.4.2.1 Design Rationale
[20](#design-rationale-33)](#design-rationale-33)

[5.4.2.2 Processing [20](#processing-1)](#processing-1)

[5.4.3 McuDiagcRstChk [20](#mcudiagcrstchk)](#mcudiagcrstchk)

[5.4.3.1 Design Rationale
[21](#design-rationale-34)](#design-rationale-34)

[5.4.3.2 Processing [21](#processing-2)](#processing-2)

[5.5 GLOBAL Function/Macro Definitions
[21](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[5.5.1 GLOBAL Function \#1 [21](#global-function-1)](#global-function-1)

[5.5.1.1 Design Rationale
[21](#design-rationale-35)](#design-rationale-35)

[5.5.1.2 processing [21](#processing-3)](#processing-3)

[6 Known Limitations with Design
[22](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[23](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[24](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [25](#glossary)](#glossary)

[Appendix C References [26](#references)](#references)

# Introduction

## Purpose

This document details the design in the FDD and also lists out any
deviations which were made from the design for the implementation due to
any constraints in development. ExcpnHndlg MDD describes the exception
handling / reset cause determination for microcontroller diagnostics

# ExcpnHndlg & High-Level Description

Refer FDD

# Design details of software module

## Graphical representation of ExcpnHndlg

## Data Flow Diagram

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/CM101A_ExcpnHndlg_Impl/doc/mediax/media/image1.png"
style="width:2.87986in;height:1.71319in" />

### Component level DFD

**N/A**

### Function level DFD

**N/A**

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name                      | Resolution | Units  | Value                   |
|---------------------------|-------------|----------|-----------------------|
| FPCFGININVAL_CNT_T_U32             | 1          | Counts | 0x0000001CU             |
| FPCFGREGID_CNT_S32                 | 1          | Counts | 10                      |
| FPCFGSELNID_CNT_S32                | 1          | Counts | 0                       |
| FPUINVLDOPERSTSBIT_CNT_U32         | 1          | Counts | ((uint32)(0x00004000U)) |
| FPUDIVBYZEROSTSBIT_CNT_U32         | 1          | Counts | ((uint32)(0x00002000U)) |
| FPUOVFSTSBIT_CNT_U32               | 1          | Counts | ((uint32)(0x00001000U)) |
| MEMERRINFOREADWRBIT_CNT_U32        | 1          | Counts | ((uint32)(0x00000001U)) |
| CF1STERSTRADRPARMASK_CNT_U32       | 1          | Counts | ((uint32)(0x00000004U)) |
| CF1STERSTRDBLBITMASK_CNT_U32       | 1          | Counts | ((uint32)(0x00000002U)) |
| CF1STERSTRSNGBITMASK_CNT_U32       | 1          | Counts | ((uint32)(0x00000001U)) |
| PRPHLBUSDATAPARMASK_CNT_U32        | 1          | Counts | ((uint32)(0x10000000U)) |
| DTSDBLBITMASK_CNT_U32              | 1          | Counts | ((uint32)(0x80000000U)) |
| CODFLSSNGBITHARDFLT_CNT_U08        | 1          | Counts | 1U                      |
| CODFLSECCDBLBIT_CNT_U08            | 1          | Counts | 2U                      |
| CODFLSADRPAR_CNT_U08               | 1          | Counts | 4U                      |
| CODFLASHEXECENAREGFAILR_CNT_U08    | 1          | Counts | 8U                      |
| MEMBISTSTRTUPTESTFAILR_CNT_U08     | 1          | Counts | 1U                      |
| LCLRAMECCSNGBITHARDFLT_CNT_U08     | 1          | Counts | 1U                      |
| LCLRAMECCDBLBIT_CNT_U08            | 1          | Counts | 2U                      |
| INVLDRAMAREA_CNT_U08               | 1          | Counts | 4U                      |
| DTSDBLBIT_CNT_U08                  | 1          | Counts | 2U                      |
| DTSSNGBITFLT_CNT_U08               | 1          | Counts | 4U                      |
| SPI0PRPHLRAMDBLBIT_CNT_U08         | 1          | Counts | 2U                      |
| SPI1PRPHLRAMDBLBIT_CNT_U08         | 1          | Counts | 2U                      |
| SPI2PRPHLRAMDBLBIT_CNT_U08         | 1          | Counts | 2U                      |
| SPI3PRPHLRAMDBLBIT_CNT_U08         | 1          | Counts | 2U                      |
| BISTCODECCFAILR_CNT_U08            | 1          | Counts | 1U                      |
| LOGLBISTSTRTUPTESTFAILR_CNT_U08    | 1          | Counts | 4U                      |
| BISTNOTCMPL_CNT_U08                | 1          | Counts | 16U                     |
| CPULOCKSTEPSTRTUPTESTFAILR_CNT_U08 | 1          | Counts | 32U                     |
| DMALOCKSTEPSTRTUPTESTFAILR_CNT_U08 | 1          | Counts | 64U                     |
| FACIRSTTRFERR_CNT_U08              | 1          | Counts | 128U                    |
| LOCKSTEPCOMP_CNT_U08               | 1          | Counts | 1U                      |
| SYSVCIE_CNT_U08                    | 1          | Counts | 2U                      |
| RESDOPER_CNT_U08                   | 1          | Counts | 4U                      |
| ALGNREAD_CNT_U08                   | 1          | Counts | 8U                      |
| ALGNWR_CNT_U08                     | 1          | Counts | 16U                     |
| INSTRFETCH_CNT_U08                 | 1          | Counts | 32U                     |
| INTCNCTRESDAREA_CNT_U08            | 1          | Counts | 64U                     |
| INVLDMEMACS_CNT_U08                | 1          | Counts | 128U                    |
| CLKMONR0RTLOWRLIMFLT_CNT_U08       | 1          | Counts | 4U                      |
| CLKMONR0RTUPPRLIMFLT_CNT_U08       | 1          | Counts | 8U                      |
| CLKMONR2RTLOWRLIMFLT_CNT_U08       | 1          | Counts | 64U                     |
| CLKMONR2RTUPPRLIMFLT_CNT_U08       | 1          | Counts | 128U                    |
| OPERMODERRFLSPROGMMODSTRTD_CNT_U08 | 1          | Counts | 1U                      |
| OPERMODERRTESTMODSTRTD_CNT_U08     | 1          | Counts | 2U                      |
| OPERMODERRSNGCHIPINACTV_CNT_U08    | 1          | Counts | 4U                      |
| CLKMONR1RTLOWRLIMFLT_CNT_U08       | 1          | Counts | 4U                      |
| CLKMONR1RTUPPRLIMFLT_CNT_U08       | 1          | Counts | 8U                      |
| CLKMONR3RTLOWRLIMFLT_CNT_U08       | 1          | Counts | 64U                     |
| CLKMONR3RTUPPRLIMFLT_CNT_U08       | 1          | Counts | 128U                    |
| DATAANDINSTRPROTNERR_CNT_U08       | 1          | Counts | 1U                      |
| ECMSTSFLT_CNT_U08                  | 1          | Counts | 1U                      |
| EIINTRPTSTRTUPFLT_CNT_U08          | 1          | Counts | 2U                      |
| ECMMSTSTRTUPTESTFAILR_CNT_U08      | 1          | Counts | 4U                      |
| ECMCHKRSTRTUPTESTFAILR_CNT_U08     | 1          | Counts | 8U                      |
| ECMPSDOERRINJFLT_CNT_U08           | 1          | Counts | 16U                     |
| ECMRTMSTCHKRCOMPFLT_CNT_U08        | 1          | Counts | 128U                    |
| FPUINVLDOPEREXCPN_CNT_U08          | 1          | Counts | 2U                      |
| FPUDIVBYZEROEXCPN_CNT_U08          | 1          | Counts | 4U                      |
| FPUOVFEXCPN_CNT_U08                | 1          | Counts | 8U                      |
| FPUUKWNEXCPN_CNT_U08               | 1          | Counts | 16U                     |
| UKWNRST_CNT_U08                    | 1          | Counts | 1U                      |
| UKWNECMRST_CNT_U08                 | 1          | Counts | 2U                      |
| BACKUPRAMTSTFAILRINBTLDR_CNT_U08   | 1          | Counts | 8U                      |
| UKWNSWRST_CNT_U08                  | 1          | Counts | 16U                     |
| BACKUPRAMTSTFAILR_CNT_U08          | 1          | Counts | 32U                     |
| FLSBTLDRPREOSSRTUPEXCPN_CNT_U08    | 1          | Counts | 64U                     |
| STRTUPRSTINFOFAILD_CNT_U08         | 1          | Counts | 128U                    |
| PROGFLOW_CNT_U08                   | 1          | Counts | 1U                      |
| DEADLINEMONR_CNT_U08               | 1          | Counts | 2U                      |
| ALVMONR_CNT_U08                    | 1          | Counts | 4U                      |
| WDGTOUT_CNT_U08                    | 1          | Counts | 1U                      |
| PEGRTFLT_CNT_U08                   | 1          | Counts | 2U                      |
| IPGRTFLT_CNT_U08                   | 1          | Counts | 8U                      |
| PBGSTRTUPTSTAILR_CNT_U08           | 1          | Counts | 16U                     |
| PBGRTFLT_CNT_U08                   | 1          | Counts | 32U                     |
| DBGRST_CNT_U08                     | 1          | Counts | 1U                      |
| OSCRITFLT_CNT_U08                  | 1          | Counts | 1U                      |
| UKWNEXCPN_CNT_U08                  | 1          | Counts | 2U                      |
| OSNONCRITFLT_CNT_U08               | 1          | Counts | 1U                      |
| DMATRFERR_CNT_U08                  | 1          | Counts | 1U                      |
| DMAREGACSPROTCNERR_CNT_U08         | 1          | Counts | 2U                      |
| PRPHLBUSDATAPARSTRTUPFLT_CNT_U08   | 1          | Counts | 64U                     |
| PRPHLBUSDATAPARPRTFLT_CNT_U08      | 1          | Counts | 128U                    |
| INTCVMOVERVLTGMONR_CNT_U08         | 1          | Counts | 1U                      |
| INTCVMUNDERVLTGMONR_CNT_U08        | 1          | Counts | 2U                      |
| INTMONRLOVCCFLT_CNT_U08            | 1          | Counts | 16U                     |
| EXTVLTGMONRFLT_CNT_U08             | 1          | Counts | 128U                    |
| UPPR16BITMASK_CNT_U32              | 1          | Counts | ((uint32)(0xFFFF0000U)) |
| LOWR16BITMASK_CNT_U32              | 1          | Counts | ((uint32)(0x0000FFFFU)) |
| INTCNCTRESDAREA1UPPRADR_CNT_U08    | 1          | Counts | (0XFFFF4FFFU)           |
| INTCNCTRESDAREA1LOWRADR_CNT_U08    | 1          | Counts | (0xFFFF0000U)           |
| INTCNCTRESDAREA2UPPRADR_CNT_U08    | 1          | Counts | (0XFFFEBFFFU)           |
| INTCNCTRESDAREA2LOWRADR_CNT_U08    | 1          | Counts | (0xFFFE0000U)           |
| INTCNCTRESDAREA3UPPRADR_CNT_U08    | 1          | Counts | (0XFE9FFFFFU)           |
| INTCNCTRESDAREA3LOWRADR_CNT_U08    | 1          | Counts | (0XFB000000U)           |
| INTCNCTRESDAREA4UPPRADR_CNT_U08    | 1          | Counts | (0XF8FFFFFFU)           |
| INTCNCTRESDAREA4LOWRADR_CNT_U08    | 1          | Counts | (0XF3000000U)           |
| INVLDMEMACSUPPRADR_CNT_U08         | 1          | Counts | (0XFFFF7EFFU)           |
| INVLDMEMACSLOWRADR_CNT_U08         | 1          | Counts | (0xFFFF7900U)           |
| FEPCREGID_CNT_S32                  | 1          | Counts | 2                       |
| FEPCSELNID_CNT_S32                 | 1          | Counts | 0                       |
| MEAREGID_CNT_S32                   | 1          | Counts | 6                       |
| MEASELNID_CNT_S32                  | 1          | Counts | 2                       |
| NROFBRAMDATREGS_CNT_U08            | 1          | Counts | ((uint8)4U)             |
| SIZEOFBRAMDATREGS_CNT_U08          | 1          | Counts | ((uint8)4U)             |

# Software Component Implementation

## Sub-Module Functions

## Init: ExcpnHndlgInit1

## Design Rationale

*Non-RTE function because it needs to be called before the OS is
started - so that floating point exceptions can be enabled before
anything uses floating point*

## Module Outputs

*None*

## Init: ExcpnHndlgInit2

## Design Rationale

*RTE function to initialize all the NTCs to pass*

## Module Outputs

*None*

## Per: ExcpnHndlgPer1

## Design Rationale

*RTE Periodic function called every 2 ms to check for OS errors*

## Store Module Inputs to Local copies

*Refer MDD*

##  (Processing of function)………

*Triggered on Timing Event every 2ms*

## Store Local copy of outputs into Module Outputs

*None*

## Server Runables 

## ChkForStrtUpTest

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## FeNmiClkMonr0RtLowrLimFlt

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## FeNmiClkMonr0RtUpprLimFlt

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## FeNmiClkMonr1RtLowrLimFlt

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## FeNmiClkMonr1RtUpprLimFlt

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## FeNmiClkMonr2RtLowrLimFlt

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## FeNmiClkMonr2RtUpprLimFlt

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## FeNmiClkMonr3RtLowrLimFlt

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## FeNmiClkMonr3RtUpprLimFlt

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## FeNmiDmaTrf

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## FeNmiDmaRegAcsProtnErr

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## FeNmiEcmMstChkrCmp

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## FeNmiOperModErrFlsProgmModStrtd

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## FeNmiOperModErrSngChipInactv

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## FeNmiOperModErrTestModStrtd

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## FeNmiPeg

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## FeNmiWdg

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## FeNmiDtsEccSngBitErr

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## GetMcuDiagcIdnData

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## ProcMpuExcpnErr

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## ProcNonCritOsErr

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## ProcPrmntOsErr

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## ProcPrvlgdInstrExcpnErr

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## ProcUkwnExcpnErr

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## SetMcuDiagcIdnData

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## Interrupt Functions

## AlgnErrIrq 

## Design Rationale

*Refer FDD*

## (Processing of the ISR function)…..

*Refer FDD*

## FpuErrIrq 

## Design Rationale

*Refer FDD*

## (Processing of the ISR function)…..

*Refer FDD*

## SysErrIrq

## Design Rationale

*Refer FDD*

## (Processing of the ISR function)…..

*Refer FDD*

## ResdOperIrq

## Design Rationale

*Refer FDD*

## (Processing of the ISR function)…..

*Refer FDD*

## Module Internal (Local) Functions

## ProcStrtUpOrSwRst 

|                      |                   |      |     |     |
|----------------------|-------------------|------|-----|-----|
| **Function Name**    | ProcStrtUpOrSwRst | Type | Min | Max |
| **Arguments Passed** | None              |      |     |     |
|                      |                   |      |     |     |
| **Return Value**     | NA                |      |     |     |

## Design Rationale

*Refer FDD*

## Processing

## ProcPinRst 

|                      |            |      |     |     |
|----------------------|------------|------|-----|-----|
| **Function Name**    | ProcPinRst | Type | Min | Max |
| **Arguments Passed** | None       |      |     |     |
|                      |            |      |     |     |
| **Return Value**     | NA         |      |     |     |

## Design Rationale

*Refer FDD*

## Processing

## McuDiagcRstChk 

|                      |                          |           |             |             |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | McuDiagcRstChk           | Type      | Min         | Max         |
| **Arguments Passed** | RstInfo_Cnt_T_enum       | McuDiagc1 | Refer FDD\* | Refer FDD\* |
|                      |                          |           |             |             |
| **Return Value**     | McuDiagcRstChk_Cnt_T_lgc | Boolean   | FALSE       | TRUE        |

## Design Rationale

*Checks if the reset cause is power on/Flash Progamming /Hard Reset
/Soft Reset.*

## Processing

Refer the FDD

## GLOBAL Function/Macro Definitions

\<If these are numerous and defined in a separate source file then
reference the source file only.\>

## GLOBAL Function \#1

|                      |                                                    |                               |                               |                               |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | (Exact name used)                                  | Type                          | Min                           | Max                           |
| **Arguments Passed** | (if none, write None)                              | \<Refer MDD guidelines\[1\]\> | \<Refer MDD guidelines\[1\]\> | \<Refer MDD guidelines\[1\]\> |
|                      | (Insert more rows for additional passed arguments) |                               |                               |                               |
| **Return Value**     | (if no value returned, write N/A)                  |                               |                               |                               |

## Design Rationale

## processing

(Place flowchart/design for local function)

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
|-------|--------------------------------------------|----------------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                    | v1.3.0 R4.0 Rev 2              |
| 2           | MDD Guideline                                                                                                                                                         | 1.02                           |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 1.02                           |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.01                           |
| 5           | FDD (CM101A_ExcpnHndlg_Design)                                                                                                                                        | See Synergy Subproject version |

{% endraw %}