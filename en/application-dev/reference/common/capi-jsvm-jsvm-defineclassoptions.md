# JSVM_DefineClassOptions
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou; @string_sz-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

```c
typedef struct {...} JSVM_DefineClassOptions
```

## Overview

Defines the options of a class.

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
