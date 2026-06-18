# JSVM_CompileOptions

<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=93671cc034f483d1b8e032e6aa319b90dbbd1186 translatedAt=2026-06-18T08:20:47.662Z pushedAt=2026-06-18T09:07:36.516Z -->

```c
typedef struct {...} JSVM_CompileOptions
```

## Overview

Defines a struct that represents the type of the elements in **options** of [OH_JSVM_CompileScriptWithOptions](capi-jsvm-h.md#oh_jsvm_compilescriptwithoptions).

**Use scenario:** Applying custom compilation settings for JS scripts, such as setting the compilation optimization level, enabling debug information, and configuring the module resolution strategy.

**System capability:** SystemCapability.ArkCompiler.JSVM

**Since**: 12

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member Variables

| Name                                                                           | Description           |
|-------------------------------------------------------------------------------|---------------|
| [JSVM_CompileOptionId](capi-jsvm-types-h.md#jsvm_compileoptionid) id | Compilation option ID.|
| content     | Union of the compilation option value corresponding to the ID.|
| content.ptr   | Pointer to the compilation option value.|
| content.num      | Used to store the compilation option value of the integer type.|
| content.boolean   | Used to store the compilation option value of the Boolean type.|