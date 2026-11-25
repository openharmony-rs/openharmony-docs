---
kits: ["ArkTS Kit"]
description: "Introduces the purpose and acquisition path of the ArkTS disassembler tool Disassembler, provides command-line parameter descriptions and usage examples, and helps developers disassemble abc bytecode files into readable assembly instructions for problem analysis."
keywords: [Disassembler, disassembly, DevEco Studio, ark_disasm, abc file, Ark bytecode, assembly instructions]
doctype: guide
status: active
---

# Disassembler
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @oatuwwutao-->
<!--Designer: @oatuwwutao-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=17ae88719a2d37a0c07e3b6e33ddb120ebd3dbc5 translatedAt=2026-11-06T10:51:34.871Z pushedAt=2026-11-12T13:37:41.931Z nl=1 -->

## Overview

Disassembler is a utility in the ArkTS toolchain designed to convert Ark bytecode files (*.abc) into human-readable assembly instructions. It is particularly useful when you want to analyze or debug issues related to Ark bytecode files.

Disassembler is released with the DevEco Studio SDK. For instance, on Windows, the tool can be found at: DevEco Studio/sdk/default/openharmony/toolchains/ark_disasm.exe.

## Command-Line Instructions

To use Disassembler, run the following command:

```text
ark_disasm.exe [options] input_file output_file
```

Parameters

| Parameter| Optional| Description|
| -------- | -------- | -------- |
| [options] | Yes| Command options. For details, see **Description of options** below.|
| input_file | No| Path of the Ark bytecode file to be disassembled.|
| output_file | No| Path where the disassembled file will be saved.|

Description of **options**

| Option| Mandatory| Argument Carried| Description|
| -------- | -------- | -------- | -------- |
| --debug | No | No | Enables the function of outputting debugging information. By default, debugging information is output to the screen.|
| --debug-file | No| Yes| Specifies the output file of debugging information if **--debug** is enabled.|
| --help | No| No| Displays help information.|
| --skip-string-literals | No| No| Skips disassembly of string literals.|
| --quiet | No| No| Enables all options prefixed with **--skip-**.|
| --verbose | No| No| Enables the output of additional information (byte position, ARK bytecode format, and operation code).|
| --version | No| No| Displays the version of the Ark bytecode file and the minimum supported version.|

## Usage Example

Assume that the Ark bytecode file **test.abc** exists, with the following source code:

<!-- @[disassembler_source](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkBytecode/FundamentalsAndNamingConventions/entry/src/main/ets/pages/Disassembler.ts) -->

``` TypeScript
// Disassembler.ts
let i = 99;

function show() {
  return i;
}

show();
```


Run the following command to generate a disassembled file named **test.txt**, which contains information such as the operation code and format:

```text
ark_disasm.exe test.abc test.txt
```

Run the following command to view the content of the disassembled file:


```text
cat test.txt
```

The file content is as follows:

```text
# source binary: test.abc                                                    // Disassembled Ark bytecode file.

.language ECMAScript

# ====================
# LITERALS                                                                   // Literal data.

0 0x203 { 0 [
    MODULE_REQUEST_ARRAY: {
    };
]}

# ====================
# RECORDS                                                                    // Module definition data.

.record _ESConcurrentModuleRequestsAnnotation {                              // Data prefixed with _ is fixed module data.
}

.record test {                                                               // One JS file corresponds to one module. It contains the module information, for example, location in the ARK bytecode file and whether it is CommonJS.
    u8 isCommonjs = 0x0
    u32 moduleRecordIdx = 0x203
    ......
}

# ====================
# METHODS                                                                    // Method definition data.

L_ESSlotNumberAnnotation:
    u32 slotNumberIdx { 0x0 }
.function any test.#*#show(any a0, any a1, any a2) <static> {                // This method is the show method in the source code, and it also indicates that it belongs to the test module.
    ldlexvar 0x0, 0x0
    ......
}

L_ESSlotNumberAnnotation:
    u32 slotNumberIdx { 0x3 }
.function any test.func_main_0(any a0, any a1, any a2) <static> {            // The method is automatically generated. The entire JS file can be regarded as a method named func_main_0.
    newlexenv 0x1
    ......
}

# ====================
# STRING                                                                     // Symbol table information

[offset:0x88, name_value:i]
```

Use the **--verbose** parameter to print more details such as the offset.


```text
ark_disasm.exe --verbose test.abc test.txt
```

Here are some examples of the output with **--verbose**:

```text
.record _ESSlotNumberAnnotation { # offset: 0x00cd, size: 0x0026 (38)                                  // This prints the location and size of the module within the ARK bytecode file.
}

.record test { # offset: 0x00f3, size: 0x0098 (152)                                                    // This prints the location of the module within the ARK bytecode file.
    u32 moduleRecordIdx = 0x203 # offset: 0x0144                                                   // This prints the location of the module information.
}
......
.function any test.#*#show(any a0, any a1, any a2) <static> { # offset: 0x0153, code offset: 0x0245    // This prints the location of the method information and the location of the instruction in the method.
#   CODE:
    ldlexvar 0x0, 0x0 # offset: 0x0249, [IMM4_IMM4].........[0x3c 0x00]                            // This prints the location of each command.
    ......
}
```
