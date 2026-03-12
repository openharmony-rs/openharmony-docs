# JSVM_CompileOptions
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou; @string_sz-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

```c
typedef struct {...} JSVM_CompileOptions
```

## Overview

Defines a struct that represents the type of the elements in **options** of [OH_JSVM_CompileScriptWithOptions](capi-jsvm-h.md#oh_jsvm_compilescriptwithoptions).

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
