---
layout: default
title: HeaderGen
nav_order: 6
parent: Component Implementation
---
{% raw %}
Rev. 1.2

April 20th, 2016

Introduction

This document describes installation and usage of the C code header file
generation script (HeaderGen) created by Renesas. The HeaderGen script
is a Python based script that utilizes one external Python module for
parsing Excel files. The purpose of the tool is to enable more
configurable and consistent header file generation for our customers, as
well as to provide some useful formatting options within the header
files themselves.

Contents

[1. Installation [1](#installation)](#installation)

[2. Usage [2](#usage)](#usage)

[2.1 Configuration File [2](#configuration-file)](#configuration-file)

[2.2 Execution [3](#execution)](#execution)

[2.3 Output [3](#output)](#output)

[3. Revision Record [4](#revision-record)](#revision-record)

[4. Testing [5](#testing)](#testing)

# Installation

The following tools are needed for execution of the Script

<table>
<colgroup>
<col style="width: 17%" />
<col style="width: 23%" />
<col style="width: 58%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Tool</strong></th>
<th><strong>Version</strong></th>
<th><strong>Install instructions</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Python</td>
<td>v2.7.9</td>
<td><p>Visit the Python Install site and download the latest v2.x.x
Windows version:</p>
<p>https://www.python.org/downloads/</p></td>
</tr>
<tr class="even">
<td>openpyxl</td>
<td>v2.3.0</td>
<td><p>(1) Download easy_install from Windows from this link: <a
href="https://bootstrap.pypa.io/ez_setup.py">https://bootstrap.pypa.io/ez_setup.py</a></p>
<p>(2) execute the file ez_setup.py:</p>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th>&gt;python ez_setup.py</th>
</tr>
</thead>
<tbody>
</tbody>
</table>
<p>(3) Navigate to C:\PythonXX\Script and execute</p>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th>&gt; easy_install openpyxl</th>
</tr>
</thead>
<tbody>
</tbody>
</table>
<p><u>.</u></p></td>
</tr>
<tr class="odd">
<td>Excel</td>
<td>2013</td>
<td>Script requires use of the .xlsx Excel file format</td>
</tr>
</tbody>
</table>

Table 1: Required SW Packages

# Usage

## Configuration File

The script takes as an input a text configuration file. Required fields
in the file are:

<table>
<colgroup>
<col style="width: 22%" />
<col style="width: 35%" />
<col style="width: 42%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Field</strong></th>
<th><strong>Description</strong></th>
<th><strong>Example</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Input_file_name</td>
<td>Excel input file name and full or relative path</td>
<td>./dr7f701310_matrix_smaller.xlsx</td>
</tr>
<tr class="even">
<td>Tab_name</td>
<td>Excel tab name with relevant data – typically “APB area2”</td>
<td>APB area2</td>
</tr>
<tr class="odd">
<td>Output_file_location</td>
<td><p>Location where the resulting header files will be written with
full or relative path.</p>
<p><strong>NOTE: this is currently unsupported</strong></p></td>
<td>./</td>
</tr>
<tr class="even">
<td>Base_type_byte</td>
<td>Base type for byte variables</td>
<td>uint8</td>
</tr>
<tr class="odd">
<td>Base_type_short</td>
<td>Base type for short (two byte) variables</td>
<td>uint16</td>
</tr>
<tr class="even">
<td>Base_type_long</td>
<td>Base type for long (four byte) type variables</td>
<td>uint32</td>
</tr>
<tr class="odd">
<td>Base_union_name_byte</td>
<td>Name for byte variable access within union of register access
types</td>
<td>UINT8</td>
</tr>
<tr class="even">
<td>Base_union_name_short</td>
<td>Name for short variable access within union of register access
types</td>
<td>UINT16</td>
</tr>
<tr class="odd">
<td>Base_union_name_long</td>
<td>Name for long variable access within union of register access
types</td>
<td>UINT32</td>
</tr>
<tr class="even">
<td>Base_union_name_bits</td>
<td>Name for bit variable access within union of register access types.
This will provide access to the bitfield structure.</td>
<td>BITS</td>
</tr>
<tr class="odd">
<td>[prefix] (sample text)</td>
<td>Anything following a line starting with [prefix] will be printed
exactly at the start of the header file, after the inclusion guard
#ifdef</td>
<td></td>
</tr>
<tr class="even">
<td>[groups] (sample group)</td>
<td><p>By default, all register access structures, address binding
pragmas, and access macros will be placed into the default output file.
Adding a group to the configuration file will place any register whose
name starts with the text following [groups] into a separate file.</p>
<p>More than one piece of text can follow a group name, as shown in the
example.</p></td>
<td><p>[groups] ADC_FILE = ADCD0, ADCD1</p>
<p>This will place all registers starting with either “ADC0” or “ADCD1”
into an output file called dr7f701310_ADC_FILE.h, and cause them to skip
the default header file.</p>
<p>[groups] DEFAULT =</p>
<p>This is the default group for all register information. It must be
present in the configuration file. This will place all unmatched
registers into an output file called dr7f701310_DEFAULT.h.</p></td>
</tr>
<tr class="odd">
<td>[suffix] (sample text)</td>
<td>Anything following a line starting with [suffix] will be printed
exactly at the end of the header file, before the inclusion guard
#endif</td>
<td></td>
</tr>
<tr class="even">
<td>[skip] (address)</td>
<td>Only hexadecimal addresses are allowed to follow the [skip] tag. Any
register whose address overlaps with this address will be placed into a
group labeled “skip” and generate into a _SKIP.h file</td>
<td>[skip] DEADBEEF</td>
</tr>
<tr class="odd">
<td>use_module_names = &lt;True/False&gt;</td>
<td>Setting this argument to true will ignore all [groups] arguments and
use the module column from the Excel file as register grouping
names.</td>
<td>use_module_names = True</td>
</tr>
<tr class="even">
<td>gen_address_macros = &lt;True/False&gt;</td>
<td>Setting this argument to true will generate macros for each register
mapping their address to the register name followed by “_ADDR”</td>
<td>gen_address_macros = True</td>
</tr>
</tbody>
</table>

Table 2: configuration file entries

## Execution

The script can be executed by issuing this command from the command
line:

| \> python headerGen.py config.txt |
|-----------------------------------|

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/AR202A_MicroCtrlrSuprt_Impl/tools/P1XC/HeaderGenScript/mediax/media/image1.jpeg"
style="width:0.46667in;height:0.38889in" />

**Note:** this assumes (1) the python executable has been added to your
system path, and (2) the headerGen,py script and config file are
resident in your current directory.

The script will print several informative messages to the command line
as it runs. Because the Excel file for a typical micro is very large
(\>50,000 lines), the script can take up to 10 minutes to execute. It
will print percentage complete status messages during long running
sections.

You will see these messages when the command line script has completed:

<img
src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/AR202A_MicroCtrlrSuprt_Impl/tools/P1XC/HeaderGenScript/mediax/media/image2.png"
style="width:6.69375in;height:2.43264in" />

## Output

![](ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/AR202A_MicroCtrlrSuprt_Impl/tools/P1XC/HeaderGenScript/mediax/media/image3.emf)

Figure 1: header file contents and usage

# Revision Record

|      |           |             |                                                                                                                          |
|---------|-------------|----------|-----------------------------------------|
| Rev. | Date      | Description |                                                                                                                          |
|      |           | Page        | Summary                                                                                                                  |
| 1.0  | 2/8/2016  | All         | Initial Draft                                                                                                            |
| 1.1  | 2/25/2016 | Multiple    | Adding support for multiple groups, marking output file directory config option as unsupported.                          |
| 1.2  | 4/20/2016 | Multiple    | Adding support for register address macro generation as well as register grouping based on module name column from Excel |

# Testing

Due to the size of the input Excel file, it is not feasible for Renesas
or a customer (user) of the script to test each of the registers
generated. Therefore, we have identified a sub-set of registers that
represent interesting register layout permutations for testing. As long
as these registers have generated fine, we can assume that all other
register, being of identical pattern to these registers, are fine as
well.

The registers in the test suite are:

| **Number**                                                                                                                                                       | **Register size** | **Base access type**  | **Bit access type**                          | **P1M example**         |
|-----------|-------------|---------------|---------------|--------------------|
| 1                                                                                                                                                                | 8-bit             | 8-bit                 | 8-bit                                        | 15.3.10 – SCI30BRR      |
| <img                                                                                                                                                             
 src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/AR202A_MicroCtrlrSuprt_Impl/tools/P1XC/HeaderGenScript/mediax/media/image4.png"                         
 style="width:6.49139in;height:1.67487in" />                                                                                                                       |                   |                       |                                              |                         |
| **NOTE:** SCI30BRR and SCI30MDDR are allocated to the same address, so the script will parse this incorrectly.                                                   |                   |                       |                                              |                         |
|                                                                                                                                                                  |                   |                       |                                              |                         |
| 2                                                                                                                                                                | 8-bit             | 8-bit                 | \< 8-bit, single                             | 10.4.2 – CVMF           |
| <img                                                                                                                                                             
 src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/AR202A_MicroCtrlrSuprt_Impl/tools/P1XC/HeaderGenScript/mediax/media/image5.png"                         
 style="width:6.50906in;height:1.01698in" />                                                                                                                       |                   |                       |                                              |                         |
|                                                                                                                                                                  |                   |                       |                                              |                         |
| 3                                                                                                                                                                | 8-bit             | 8-bit                 | \< 8-bit, multiple                           | 16.3.2.1 – RLN30LWBR    |
| <img                                                                                                                                                             
 src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/AR202A_MicroCtrlrSuprt_Impl/tools/P1XC/HeaderGenScript/mediax/media/image6.png"                         
 style="width:6.4928in;height:1.6072in" />                                                                                                                         |                   |                       |                                              |                         |
|                                                                                                                                                                  |                   |                       |                                              |                         |
| 3a                                                                                                                                                               | 8-bit             | 8-bit, 1-bit          | \< 8-bit, single                             | 14.3.2 – CSIH0CTL0      |
| <img                                                                                                                                                             
 src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/AR202A_MicroCtrlrSuprt_Impl/tools/P1XC/HeaderGenScript/mediax/media/image7.png"                         
 style="width:6.50852in;height:1.63878in" />                                                                                                                       |                   |                       |                                              |                         |
|                                                                                                                                                                  |                   |                       |                                              |                         |
| 4                                                                                                                                                                | 16-bit            | 16-bit                | 16-bit                                       | 13.3.10 – CSIG0TX0H     |
| <img                                                                                                                                                             
 src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/AR202A_MicroCtrlrSuprt_Impl/tools/P1XC/HeaderGenScript/mediax/media/image8.png"                         
 style="width:6.4793in;height:1.71209in" />                                                                                                                        |                   |                       |                                              |                         |
|                                                                                                                                                                  |                   |                       |                                              |                         |
| 5                                                                                                                                                                | 16-bit            | 16-bit                | 8-bit                                        | 16.3.3.18 – RLN30LUTDR  |
| <img                                                                                                                                                             
 src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/AR202A_MicroCtrlrSuprt_Impl/tools/P1XC/HeaderGenScript/mediax/media/image9.png"                         
 style="width:6.49482in;height:2.06387in" />                                                                                                                       |                   |                       |                                              |                         |
|                                                                                                                                                                  |                   |                       |                                              |                         |
| 6                                                                                                                                                                | 16-bit            | 16-bit                | \< 8-bit, single                             | 13.3.6 – CSIG0STCR0     |
| <img                                                                                                                                                             
 src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/AR202A_MicroCtrlrSuprt_Impl/tools/P1XC/HeaderGenScript/mediax/media/image10.png"                        
 style="width:6.50897in;height:1.85093in" />                                                                                                                       |                   |                       |                                              |                         |
|                                                                                                                                                                  |                   |                       |                                              |                         |
| 7                                                                                                                                                                | 16-bit            | 16-bit                | \< 8-bit, multiple, cross byte boundaries    | 13.3.4 – CSIG0CTL2      |
| <img                                                                                                                                                             
 src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/AR202A_MicroCtrlrSuprt_Impl/tools/P1XC/HeaderGenScript/mediax/media/image11.png"                        
 style="width:6.46468in;height:1.70286in" />                                                                                                                       |                   |                       |                                              |                         |
|                                                                                                                                                                  |                   |                       |                                              |                         |
| 8                                                                                                                                                                | 16-bit            | 16-bit, 8-bit         | 16-bit                                       |                         |
|                                                                                                                                                                  |                   |                       |                                              |                         |
| 9                                                                                                                                                                | 16-bit            | 16-bit, 8-bit         | 8-bit                                        |                         |
|                                                                                                                                                                  |                   |                       |                                              |                         |
| 10                                                                                                                                                               | 16-bit            | 16-bit, 8-bit         | \< 8-bit, single                             |                         |
|                                                                                                                                                                  |                   |                       |                                              |                         |
| 11                                                                                                                                                               | 16-bit            | 16-bit, 8-bit         | \< 8-bit, multiple                           |                         |
|                                                                                                                                                                  |                   |                       |                                              |                         |
| 12                                                                                                                                                               | 32-bit            | 32-bit                | 32-bit                                       | 19.3.2 – RSENTT0TSC     |
| <img                                                                                                                                                             
 src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/AR202A_MicroCtrlrSuprt_Impl/tools/P1XC/HeaderGenScript/mediax/media/image12.png"                        
 style="width:6.4658in;height:2.56244in" />                                                                                                                        |                   |                       |                                              |                         |
|                                                                                                                                                                  |                   |                       |                                              |                         |
| 13                                                                                                                                                               | 32-bit            | 32-bit                | 16-bit                                       | 13.3.9 – CSIG0TX0W      |
| <img                                                                                                                                                             
 src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/AR202A_MicroCtrlrSuprt_Impl/tools/P1XC/HeaderGenScript/mediax/media/image13.png"                        
 style="width:6.53929in;height:2.62617in" />                                                                                                                       |                   |                       |                                              |                         |
|                                                                                                                                                                  |                   |                       |                                              |                         |
| 14                                                                                                                                                               | 32-bit            | 32-bit                | 8-bit                                        | 14.3.5 – CSIH0STR0      |
| <img                                                                                                                                                             
 src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/AR202A_MicroCtrlrSuprt_Impl/tools/P1XC/HeaderGenScript/mediax/media/image14.png"                        
 style="width:6.49801in;height:2.54285in" />                                                                                                                       |                   |                       |                                              |                         |
|                                                                                                                                                                  |                   |                       |                                              |                         |
| 15                                                                                                                                                               | 32-bit            | 32-bit                | \< 8-bit, single                             | 7.9.2.1 – DMACTL        |
| <img                                                                                                                                                             
 src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/AR202A_MicroCtrlrSuprt_Impl/tools/P1XC/HeaderGenScript/mediax/media/image15.png"                        
 style="width:6.555in;height:2.67056in" />                                                                                                                         |                   |                       |                                              |                         |
|                                                                                                                                                                  |                   |                       |                                              |                         |
| 15b                                                                                                                                                              | 32-bit            | 32-bit                | \< 8-bit, single, all 32-bits                | 7.9.2.13 – DTSPR0       |
| <img                                                                                                                                                             
 src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/AR202A_MicroCtrlrSuprt_Impl/tools/P1XC/HeaderGenScript/mediax/media/image16.png"                        
 style="width:6.49067in;height:2.5999in" />                                                                                                                        |                   |                       |                                              |                         |
| **Note:** Excel and .pdf UM don’t match exactly, Excel shows these as 2-bit entries, while UM shows them as single bit entries that are clearly paired via name. |                   |                       |                                              |                         |
|                                                                                                                                                                  |                   |                       |                                              |                         |
| 16                                                                                                                                                               | 32-bit            | 32-bit                | \< 8-bit, multiple                           | 7.9.2.9 – DM0CMV        |
| <img                                                                                                                                                             
 src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/AR202A_MicroCtrlrSuprt_Impl/tools/P1XC/HeaderGenScript/mediax/media/image17.png"                        
 style="width:6.55369in;height:2.64758in" />                                                                                                                       |                   |                       |                                              |                         |
|                                                                                                                                                                  |                   |                       |                                              |                         |
| 16b                                                                                                                                                              | 32-bit            | 32-bit                | \< 8-bit, multiple, crossing byte boundaries | 11.3.5 – TSNREFD        |
| <img                                                                                                                                                             
 src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/AR202A_MicroCtrlrSuprt_Impl/tools/P1XC/HeaderGenScript/mediax/media/image18.png"                        
 style="width:6.5236in;height:2.66115in" />                                                                                                                        |                   |                       |                                              |                         |
|                                                                                                                                                                  |                   |                       |                                              |                         |
| 17                                                                                                                                                               | 32-bit            | 32-bit, 16-bit        | 32-bit                                       |                         |
|                                                                                                                                                                  |                   |                       |                                              |                         |
| 18                                                                                                                                                               | 32-bit            | 32-bit, 16-bit        | 16-bit                                       |                         |
|                                                                                                                                                                  |                   |                       |                                              |                         |
| 19                                                                                                                                                               | 32-bit            | 32-bit, 16-bit        | 8-bit                                        |                         |
|                                                                                                                                                                  |                   |                       |                                              |                         |
| 20                                                                                                                                                               | 32-bit            | 32-bit, 16-bit        | \< 8-bit, single                             |                         |
|                                                                                                                                                                  |                   |                       |                                              |                         |
| 21                                                                                                                                                               | 32-bit            | 32-bit, 16-bit        | \< 8-bit, multiple                           |                         |
|                                                                                                                                                                  |                   |                       |                                              |                         |
| 22                                                                                                                                                               | 32-bit            | 32-bit, 16-bit, 8-bit | 32-bit                                       | 18.2.7.12 – FLXA0FRNMV1 |
| <img                                                                                                                                                             
 src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/AR202A_MicroCtrlrSuprt_Impl/tools/P1XC/HeaderGenScript/mediax/media/image19.png"                        
 style="width:6.54952in;height:2.74646in" />                                                                                                                       |                   |                       |                                              |                         |
|                                                                                                                                                                  |                   |                       |                                              |                         |
| 23                                                                                                                                                               | 32-bit            | 32-bit, 16-bit, 8-bit | 16-bit                                       | 18.2.6.2 – FLXA0FRSUCC2 |
| <img                                                                                                                                                             
 src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/AR202A_MicroCtrlrSuprt_Impl/tools/P1XC/HeaderGenScript/mediax/media/image20.png"                        
 style="width:6.53592in;height:2.60718in" />                                                                                                                       |                   |                       |                                              |                         |
|                                                                                                                                                                  |                   |                       |                                              |                         |
| 24                                                                                                                                                               | 32-bit            | 32-bit, 16-bit, 8-bit | 8-bit                                        | 18.2.3.1 – FLXA0FRLCK   |
| <img                                                                                                                                                             
 src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/AR202A_MicroCtrlrSuprt_Impl/tools/P1XC/HeaderGenScript/mediax/media/image21.png"                        
 style="width:6.51103in;height:2.61819in" />                                                                                                                       |                   |                       |                                              |                         |
|                                                                                                                                                                  |                   |                       |                                              |                         |
| 25                                                                                                                                                               | 32-bit            | 32-bit, 16-bit, 8-bit | \< 8-bit, single                             | 18.2.2.1 – FLXA0FROC    |
| <img                                                                                                                                                             
 src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/AR202A_MicroCtrlrSuprt_Impl/tools/P1XC/HeaderGenScript/mediax/media/image22.png"                        
 style="width:6.52368in;height:2.66456in" />                                                                                                                       |                   |                       |                                              |                         |
|                                                                                                                                                                  |                   |                       |                                              |                         |
| 26                                                                                                                                                               | 32-bit            | 32-bit, 16-bit, 8-bit | \< 8-bit, multiple, crossing byte boundaries | 18.2.5.1 – FLXA0FRT0C   |
| <img                                                                                                                                                             
 src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/AR202A_MicroCtrlrSuprt_Impl/tools/P1XC/HeaderGenScript/mediax/media/image23.png"                        
 style="width:6.53782in;height:2.73681in" />                                                                                                                       |                   |                       |                                              |                         |
|                                                                                                                                                                  |                   |                       |                                              |                         |
| 27                                                                                                                                                               | Multiple          | 32-bit, 16-bit, 8-bit |                                              | 17.3.3 – RSCAN0C0CTR    |
| <img                                                                                                                                                             
 src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/AR202A_MicroCtrlrSuprt_Impl/tools/P1XC/HeaderGenScript/mediax/media/image24.png"                        
 style="width:6.5147in;height:3.87408in" />                                                                                                                        |                   |                       |                                              |                         |
| 28                                                                                                                                                               | Multiple          | 16-bit, 8-bit         |                                              | 16.3.3.2 – RLN30LBRP01  |
| <img                                                                                                                                                             
 src="ElectricPowerSteering_RH850_BMW_FAAR_WE_website/docs/AR202A_MicroCtrlrSuprt_Impl/tools/P1XC/HeaderGenScript/mediax/media/image25.png"                        
 style="width:6.55334in;height:2.04167in" />                                                                                                                       |                   |                       |                                              |                         |
| **Note:** The Excel file shows this split into two 8-bit named entries: LBRP0 and LBRP1, while the UM shows a single entry.                                      |                   |                       |                                              |                         |

{% endraw %}