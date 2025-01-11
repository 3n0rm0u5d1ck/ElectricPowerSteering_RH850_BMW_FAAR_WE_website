---
layout: default
title: GateDrv0Ctrl_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**Gate Drive 0 Control**

**VERSION:** **9**

**DATE:** **12-Jan-2018**

**Prepared By:**

**Shawn Penning,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

<table>
<colgroup>
<col style="width: 9%" />
<col style="width: 55%" />
<col style="width: 19%" />
<col style="width: 14%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Version</strong></td>
<td><strong>Description</strong></td>
<td><strong>Author</strong></td>
<td><strong>Date</strong></td>
</tr>
<tr class="even">
<td>1</td>
<td>Initial version</td>
<td>Rijvi Ahmed</td>
<td>07-July-2016</td>
</tr>
<tr class="odd">
<td>2</td>
<td>Updated to design revision 1.8.0</td>
<td>Avinash James</td>
<td>21-Jan-2017</td>
</tr>
<tr class="even">
<td>3</td>
<td>Updated to design revision 2.0.0</td>
<td>Shruthi Raghavan</td>
<td>17-Feb-2017</td>
</tr>
<tr class="odd">
<td>4</td>
<td>Updated to design revision 2.1.0</td>
<td>Shruthi Raghavan</td>
<td>27-Feb-2017</td>
</tr>
<tr class="even">
<td>5</td>
<td>Updated to design revision 2.3.0</td>
<td>Shruthi Raghavan</td>
<td>14-Mar-2017</td>
</tr>
<tr class="odd">
<td>6</td>
<td>Updated to design revision 2.4.0 – Fix for phase reasonableness
issues found during integration</td>
<td>Shruthi Raghavan</td>
<td>24-Mar-2017</td>
</tr>
<tr class="even">
<td>7</td>
<td><p>Removed unused inputs from OperFltMonSt function.</p>
<p>Added UT considerations per anomaly EA4#11845</p></td>
<td>Shruthi Raghavan</td>
<td>26-May-2017</td>
</tr>
<tr class="odd">
<td>8</td>
<td>Updated graphical representation for the new outputs and client
call. Added details for changed &amp; new local functions<br />
Added new enum type and local constant</td>
<td>Shruthi Raghavan</td>
<td>11-Sep-2017</td>
</tr>
<tr class="even">
<td>9</td>
<td>Updated design rationale for the state machine in Configuration
State of gate drive. Added UT considerations per test corrections
required in anomaly corrective action.</td>
<td>Shawn Penning</td>
<td>12-Jan-2018</td>
</tr>
</tbody>
</table>

Table of Contents

[1 Abbrevations And Acronyms 5](#abbrevations-and-acronyms)

[2 References 6](#references)

[3 GATEDRV0CTRL & High-Level Description
7](#gatedrv0ctrl-high-level-description)

[4 Design details of software module
8](#design-details-of-software-module)

[4.1 Graphical representation of GATEDRV0CTRL
8](#graphical-representation-of-gatedrv0ctrl)

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

[7.2.1 Per: GateDrv0CtrlInit1 11](#per-gatedrv0ctrlinit1)

[7.3 PERIODIC FUNCTIONS 11](#periodic-functions)

[7.3.1 Per: GateDrv0CtrlPer1 11](#per-gatedrv0ctrlper1)

[7.3.1.1 Design Rationale 11](#design-rationale)

[7.3.1.2 Processing of Function 11](#processing-of-function)

[7.3.2 Per: GateDrv0CtrlPer2 11](#per-gatedrv0ctrlper2)

[7.3.2.1 Design Rationale 11](#design-rationale-1)

[7.3.2.2 Processing of Function 11](#processing-of-function-1)

[7.4 Interrupt Functions 11](#interrupt-functions)

[7.5 Serial Communication Functions 11](#serial-communication-functions)

[7.6 Local Function/Macro Definitions
12](#local-functionmacro-definitions)

[7.6.1 Local Function \#1 12](#local-function-1)

[7.6.1.1 Description 12](#description)

[7.6.2 Local Function \#2 12](#local-function-2)

[7.6.2.1 Description 12](#description-1)

[7.6.3 Local Function \#3 12](#local-function-3)

[7.6.3.1 Description 12](#description-2)

[7.6.4 Local Function \#4 12](#local-function-4)

[7.6.4.1 Description 12](#description-3)

[7.6.5 Local Function \#5 12](#local-function-5)

[7.6.5.1 Description 13](#description-4)

[7.6.6 Local Function \#6 13](#local-function-6)

[7.6.6.1 Description 13](#description-5)

[7.6.7 Local Function \#7 13](#local-function-7)

[7.6.7.1 Description 13](#description-6)

[7.6.8 Local Function \#8 13](#local-function-8)

[7.6.8.1 Description 13](#description-7)

[7.6.9 Local Function \#9 13](#local-function-9)

[7.6.9.1 Description 14](#description-8)

[7.6.10 Local Function \#10 14](#local-function-10)

[7.6.10.1 Description 14](#description-9)

[7.6.11 Local Function \#11 14](#local-function-11)

[7.6.11.1 Description 14](#description-10)

[7.7 GLObAL Function/Macro Definitions
14](#global-functionmacro-definitions)

[8 Known Limitations With Design 15](#known-limitations-with-design)

[9 UNIT TEST CONSIDERATION 16](#unit-test-consideration)

# Abbrevations And Acronyms

|              |                           |
|--------------|---------------------------|
| Abbreviation | Description               |
| DFD          | Design functional diagram |
| MDD          | Module design Document    |

# References

This section lists the title & version of all the documents that are
referred for development of this document

|         |                                  |                                 |
|----------|----------------------------------------------|-----------------|
| Sr. No. | Title                            | Version                         |
| 1       | MDD Guidelines                   | 1.02                            |
| 2       | Software Naming Conventions      | 1.02                            |
| 3       | Software Coding Standards        | 1.01                            |
| 4       | FDD – ES311A_GateDrv0Ctrl_Design | See synergy sub project version |

# GATEDRV0CTRL & High-Level Description

This module configures the GateDrive0 connected with SPI channel CSIH2.
It also does the diagnostics for GateDrive0 using SPI interface.

It also performs phase reasonable diagnostics when the inverter 0 fault
input is active. Detects FET fault and indicates the type of fault and
also in the case of single fet fault it indicates the phase faulted as
well. Phase reasonableness is disabled on a phase with shorted FET

# Design details of software module

## Graphical representation of GATEDRV0CTRL

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/ES311A_GateDrv0Ctrl_Impl/doc/mediax/media/image1.png"
style="width:2.67431in;height:4.92292in" />

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
<td>GateDrvCfgSt</td>
<td>-</td>
<td>Enumeration</td>
<td>0</td>
<td>4</td>
</tr>
</tbody>
</table>

## Variable definition for enumerated types

|              |                              |       |
|--------------|------------------------------|-------|
| Enum Name    | Element Name                 | Value |
| GateDrvCfgSt | GATEDRVCFGST_RSTGATEDRVST    | 0     |
|              | GATEDRVCFGST_WAIT2MS         | 1     |
|              | GATEDRVCFGST_CFGREG          | 2     |
|              | GATEDRVCFGST_SETUPSPIREGREAD | 3     |
|              | GATEDRVCFGST_READBACKREGS    | 4     |

# Constant Data Dictionary

## Program(fixed) Constants

## Embedded Constants

## Local

|                                        |                        |         |                                                               |
|---------------------------------|---------------|-----------|-------------|
| Constant Name                          | Resolution             | Units   | Value                                                         |
| GATEDRVOFFSTCHKSIZE_CNT_U08            | 1U                     | Cnt     | ((TblSize_m(ELECGLBPRM_GATEDRVOFFSTCHKDATA_CNT_U16)/8U) - 1U) |
| BITMASK0_CNT_U08                       | 1                      | Cnt     | 0x01U                                                         |
| BITMASK2_CNT_U08                       | 1                      | Cnt     | 0x04U                                                         |
| BITMASK4_CNT_U08                       | 1                      | Cnt     | 0x10U                                                         |
| MOTDRVERRMIN_NANOSEC_F32               | Single precision float | NanoSec | 0.0F                                                          |
| MOTDRVERRMAX_NANOSEC_F32               | Single precision float | NanoSec | 40000000.0F                                                   |
| DIAG2REGBOOTSTRPSPLYFLTSTRTPOS_CNT_U08 | 1                      | Cnt     | 5U                                                            |

## Global

|                  |
|------------------|
| Constant Name    |
| Refer to the FDD |

## Module specific Lookup Tables Constants

|                     |            |       |                  |
|---------------------|------------|-------|------------------|
| Constant Name       | Resolution | Value | Software Segment |
| Refer to the design |            |       |                  |

# Software Module Implementation

## Sub-Module Functions

None

## Initialization Functions

## Per: GateDrv0CtrlInit1

## PERIODIC FUNCTIONS

## Per: GateDrv0CtrlPer1

## Design Rationale

None

## Processing of Function

See design model for details.

## Per: GateDrv0CtrlPer2

## Design Rationale

It is the intent of this design to hold the value of

MotDrvr0IninTestCmpl between iterations of GateDrv0CtrlPer2.

There was an inexplicable model issue in which MotDrvr0IninTestCmpl

was being reset to 0 when MotDrvr0IninTestCmpl was not being

written in the IF branch of model (refer model notes)

Implementation Considerations:

No need to use a PIM or a static variable as this signal is an RTE

output. Since RTE signals work like a static variable, the

implementation always holds the last value.

## Processing of Function

See design model for details.

## Interrupt Functions

None

## Serial Communication Functions

None

## Local Function/Macro Definitions

## Local Function \#1

|                      |                    |                  |     |      |
|----------------------|--------------------|------------------|-----|------|
| **Function Name**    | SpiAsyncTx         | Type             | Min | Max  |
| **Arguments Passed** | Channel_Cnt_T_u08  | Spi_ChannelType  | 0   | Full |
|                      | TxData_Cnt_T_u16   | Spi_DataType     | 0   | Full |
|                      | Sequence_Cnt_T_u08 | Spi_SequenceType | 0   | Full |
| **Return Value**     | None               |                  |     |      |

## Description

(void) Spi_WriteIB( Channel_Cnt_T_u08, &TxData_Cnt_T_u16 );

(void) Call_Spi_AsyncTransmit( Sequence_Cnt_T_u08 );

## Local Function \#2

|                      |             |      |     |     |
|----------------------|-------------|------|-----|-----|
| **Function Name**    | OffStVrfySt | Type | Min | Max |
| **Arguments Passed** | None        |      |     |     |
| **Return Value**     | None        |      |     |     |

## Description

See **GateDrv0Ctrl/GateDrv0CtrlPer2/Gate Drive Enable/Gate Drive
State/OffState Verification State**block in design model.

## Local Function \#3

|                      |                |         |       |      |
|----------------------|----------------|---------|-------|------|
| **Function Name**    | OffStVrfyData  | Type    | Min   | Max  |
| **Arguments Passed** | None           |         |       |      |
| **Return Value**     | Flt_Cnt_T_logl | Boolean | FALSE | TRUE |

## Description

See **GateDrv0Ctrl/GateDrv0CtrlPer2/Gate Drive Enable/Gate Drive
State/OffState Verification State/OffSt Verification Chk and Transition
to Config State/OffStChk Incomplete/Offstate Verification /OffState
Verification Check** block in design model.

\*It is optimized in the implementation to reduce the high static path
count.

## Local Function \#4

|                      |       |      |     |     |
|----------------------|-------|------|-----|-----|
| **Function Name**    | CfgSt | Type | Min | Max |
| **Arguments Passed** | None  |      |     |     |
| **Return Value**     | None  |      |     |     |

## Description

See **GateDrv0Ctrl/GateDrv0CtrlPer2/Gate Drive Enable/Gate Drive
State/Configuration State** block in design model.

The state machine is implemented slightly differently in code vs the
model, but they are functionally equivalent.  
The model adds 1 to the GateDrv0CfgCnt Pim to change to the next state
in Configuration,but the code assigns values from a local enumeration
(see section 5.2) instead of performing arithmetic on the Pim. The
enumerated state assigned to GateDrv0CfgCnt Pim will match with the
resulting state in the model.

## Local Function \#5

|                      |              |      |     |     |
|----------------------|--------------|------|-----|-----|
| **Function Name**    | ReadBackRegs | Type | Min | Max |
| **Arguments Passed** | None         |      |     |     |
| **Return Value**     | None         |      |     |     |

## Description

See **GateDrv0Ctrl/GateDrv0CtrlPer2/Gate Drive Enable/Gate Drive
State/Configuration State/Read back Registers** block in design model.

## Local Function \#6

|                      |                              |                        |      |             |
|--------------|-------------------|--------------|-------------|--------------|
| **Function Name**    | OperFltMonrSt                | Type                   | Min  | Max         |
| **Arguments Passed** | PhaOnTiMeasdA_NanoSec_T_u32  | Uint32                 | 0    | 4294967295  |
|                      | PhaOnTiMeasdB_NanoSec_T_u32  | Uint32                 | 0    | 4294967295  |
|                      | PhaOnTiMeasdC_NanoSec_T_u32  | Uint32                 | 0    | 4294967295  |
|                      | PhaOnTiSumAExp_NanoSec_T_u32 | Uint32                 | 0    | 4294967295  |
|                      | PhaOnTiSumBExp_NanoSec_T_u32 | Uint32                 | 0    | 4294967295  |
|                      | PhaOnTiSumCExp_NanoSec_T_u32 | Uint32                 | 0    | 4294967295  |
|                      | \*MotDrvErrA_NanoSec_T_f32   | Single precision float | 0.0F | 40000000.0F |
|                      | \*MotDrvErrB_NanoSec_T_f32   | Single precision float | 0.0F | 40000000.0F |
|                      | \*MotDrvErrC_NanoSec_T_f32   | Single precision float | 0.0F | 40000000.0F |
| **Return Value**     | None                         |                        |      |             |

## Description

See **GateDrv0Ctrl/GateDrv0CtrlPer2/Gate Drive Enable/Gate Drive
State/Operate Fault Monitor State** block in design model.

## Local Function \#7

|                      |                               |         |       |             |
|--------------|--------------------------------|---------|--------|-----------|
| **Function Name**    | GateDrvDetermineOnStSngFETFlt | Type    | Min   | Max         |
| **Arguments Passed** | \*SpclSnpshtData0_Cnt_T_u32   | Uint32  | 0U    | 4294967295U |
|                      | \*SpclSnpshtData1_Cnt_T_u32   | Uint32  | 0U    | 4294967295U |
|                      | \*SpclSnpshtData2_Cnt_T_u32   | Uint32  | 0U    | 4294967295U |
| **Return Value**     | GenGateDrvFlt_Cnt_T_logl      | Boolean | FALSE | TRUE        |

## Description

See **GateDrv0Ctrl/GateDrv0CtrlPer2/Gate Drive Enable/Gate Drive
State/Operate Fault Monitor State/Determine Faults/Status Register
indicates Fault/Determine OnState Single FET Fault** block in design
model.

## Local Function \#8

|                      |                             |         |       |             |
|--------------|--------------------------------|---------|---------|----------|
| **Function Name**    | GateDrvDetermineVltgFlt     | Type    | Min   | Max         |
| **Arguments Passed** | \*SpclSnpshtData0_Cnt_T_u32 | Uint32  | 0U    | 4294967295U |
|                      | \*SpclSnpshtData1_Cnt_T_u32 | Uint32  | 0U    | 4294967295U |
|                      | \*SpclSnpshtData2_Cnt_T_u32 | Uint32  | 0U    | 4294967295U |
| **Return Value**     | GenGateDrvFlt_Cnt_T_logl    | Boolean | FALSE | TRUE        |

## Description

See **GateDrv0Ctrl/GateDrv0CtrlPer2/Gate Drive Enable/Gate Drive
State/Operate Fault Monitor State/Determine Faults/Status Register
indicates Fault/Determine VREG/Bootstrap Voltage Fault** block in design
model.

## Local Function \#9

|                      |                             |         |       |             |
|--------------|--------------------------------|---------|---------|----------|
| **Function Name**    | GateDrvDetermineGenericFlt  | Type    | Min   | Max         |
| **Arguments Passed** | GateDrvAllSts_Cnt_T_u16     | Uint16  | 0     | 0xFFFF      |
|                      | \*SpclSnpshtData0_Cnt_T_u32 | Uint32  | 0U    | 4294967295U |
|                      | \*SpclSnpshtData1_Cnt_T_u32 | Uint32  | 0U    | 4294967295U |
|                      | \*SpclSnpshtData2_Cnt_T_u32 | Uint32  | 0U    | 4294967295U |
| **Return Value**     | GenGateDrvFlt_Cnt_T_logl    | Boolean | FALSE | TRUE        |

## Description

See **GateDrv0Ctrl/GateDrv0CtrlPer2/Gate Drive Enable/Gate Drive
State/Operate Fault Monitor State/Determine Faults/Status Register
indicates Fault/Determine Generic Gate Drive Fault** block in design
model.

## Local Function \#10

|                      |                             |                        |       |            |
|----------------|----------------------|---------------|----------|----------|
| **Function Name**    | SetNtcStInfo                | Type                   | Min   | Max        |
| **Arguments Passed** | PhaOnTiMeasd_NanoSec_T_u32  | Uint32                 | 0     | 4294967295 |
|                      | PhaOnTiSumExp_NanoSec_T_u32 | Uint32                 | 0     | 4294967295 |
|                      | AbsltErr_NanoSec_T_f32      | Single precision float | 0     | 3.4E+38    |
|                      | BitMask_Cnt_u08             | Uint8                  | 0     | 127        |
|                      | NtcStInfo_Uls_T_u08         | Uint8                  | 0     | 255        |
| **Return Value**     | Flt_Uls_T_lgc               | Boolean                | False | True       |

## Description

See **ES311A_GateDrv0Ctrl/GateDrv0Ctrl/GateDrv0CtrlPer2/GateDrv
Enable/Disable/Gate Drive Enable/Gate Drive State/Operate Fault Monitor
State/Determine Faults/No Faults/GateDrvPhaReasbnChk/MeasdPhaFltChkABC**
block in design model. This function implements **NtcStInfoPhaA**,
**NtcStInfoPhaB** and **NtcStInfoPhaC** common functionality.

## Local Function \#11

|                      |                   |       |     |     |
|----------------------|-------------------|-------|-----|-----|
| **Function Name**    | ChkResVrfyRegs    | Type  | Min | Max |
| **Arguments Passed** | PrmByte_Cnt_T_u08 | Uint8 | 128 | 138 |
| **Return Value**     | None              | \-    | \-  | \-  |

## Description

Check Results of Verify GateDrive0 Registers based on calculated
parameter byte and take appropriate action

## Local Function \#12

|                      |             |      |     |     |
|----------------------|-------------|------|-----|-----|
| **Function Name**    | WriteOutput | Type | Min | Max |
| **Arguments Passed** | None        | \-   | \-  | \-  |
| **Return Value**     | None        | \-   | \-  | \-  |

## Description

Implements the
‘**ES311A_GateDrv0Ctrl_new/GateDrv0Ctrl/GateDrv0CtrlPer2/Write Output**’
block in simulink model.

## GLObAL Function/Macro Definitions

None

# Known Limitations With Design

Note: The PIM Ivtr0InactvSts is written in Per2 and used in Per1 as well
as Per2. Data consistency is not an issue because of explicit scheduling
requirements given in the integration manual.

Note:

1.  At multiple places, the implementation does not reset the error
    counter PIM when rollover to zero happens but the model does. This
    is because in the code the rollover is automatic (and marked
    intentional ), whereas in the model it isn’t that way and requires a
    manual reset.

2.  In all the cases where (1) is applicable, the model comments say
    65535 rather than 4294967295 as the value at which reset should
    occur. Upon discussion with FDD owner, the comment is wrong and will
    be changed with the next update.

# UNIT TEST CONSIDERATION

1.  Overflow is intentional and acceptable on
    PhaOnTiSumAExp_NanoSec_T_u32, PhaOnTiSumBExp_NanoSec_T_u32 and
    PhaOnTiSumCExp_NanoSec_T_u32 in Per2 function.

2.  Rollover is intentional on Rte_Pim_GateDrv0SpiTrsmErrCntr. The code
    has comments that also mention this consideration.  
    **<u>Note:</u>** While the code and model do not exactly match on
    the implementation (because the model manually resets this error
    counter, while the code lets it auto-reset due to rollover), the
    output should be the same for the PIM because functionally they are
    same.

3.  The model is designed such that the table
    ELECGLBPRM_GATEDRVOFFSTCHKDATA_CNT_U16 is never indexed with a value
    of greater than its size in real life. However, in code we need an
    explicit check for safety. For this reason, when
    Rte_Pim_GateDrv0OffStChkIdx is given a value greater than or equal
    to the size of this table, the model and code will behave
    differently (this is expected , because it is an impossible scenario
    in the real world).  
    -\>  
    ***<u>For PIL testing, the consideration is that</u>*** the input
    values given to Rte_Pim_GateDrv0OffStChkIdx when MIL vectors are not
    available should be less than or equal to
    (GATEDRVOFFSTCHKSIZE_CNT_U08).

4.  This component has a config parameter. Use the file from
    local/include folder and NOT the one from local/generate folder for
    testing so that Tessy can vary the value of the configuration
    parameter in the range that it is given in the data dictionary.

5.  Please rectify wrong expected values of tests as part of anomaly
    corrective action. See PDF attached here (refer to both root cause
    and corrective action).

{% endraw %}