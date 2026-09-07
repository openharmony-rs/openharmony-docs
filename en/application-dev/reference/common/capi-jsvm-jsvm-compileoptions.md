# JSVM_CompileOptions

<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=21434ce8d323ecbd7d67463989a2ef075be92cec translatedAt=2026-08-27T03:47:19.467Z pushedAt=2026-08-27T06:25:14.228Z -->

```c
typedef struct {...} JSVM_CompileOptions
```

## Overview

Defines a struct that represents the type of the elements in **options** of [OH_JSVM_CompileScriptWithOptions](capi-jsvm-h.md#oh_jsvm_compilescriptwithoptions).

**Usage scenario:** Used when custom compilation configuration is required for JS scripts, for example, setting the compilation optimization level, enabling debug information, and configuring the module resolution policy.

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