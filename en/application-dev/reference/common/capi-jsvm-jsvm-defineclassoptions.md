# JSVM_DefineClassOptions

<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=21434ce8d323ecbd7d67463989a2ef075be92cec translatedAt=2026-08-27T03:47:43.280Z pushedAt=2026-08-27T06:34:24.181Z -->

```c
typedef struct {...} JSVM_DefineClassOptions
```

## Overview

Defines the options of a class.

**System capability:** SystemCapability.ArkCompiler.JSVM

**Since**: 18

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member Variables

| Name                                                                           | Description           |
|-------------------------------------------------------------------------------|---------------|
| [JSVM_DefineClassOptionsId](capi-jsvm-types-h.md#jsvm_defineclassoptionsid) id | Option ID of a class.|
| content     | Union of the option value of a class corresponding to the ID.|
| content.ptr   | Pointer to the class option value.|
| content.num      | Used to store the class option value of the integer type.|
| content.boolean   | Used to store the class option value of the Boolean type.|