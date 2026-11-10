# JSVM_DefineClassOptions

```c
typedef struct JSVM_DefineClassOptions {...} JSVM_DefineClassOptions
```

## Overview

DefineClass options.

<!--Device-typedef struct JSVM_DefineClassOptions {...} JSVM_DefineClassOptions--><!--Device-typedef struct JSVM_DefineClassOptions {...} JSVM_DefineClassOptions-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 18

**Related module**: [JSVM](capi-arkts-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [JSVM_DefineClassOptionsId](capi-jsvm-types-h.md#jsvm_defineclassoptionsid) id | DefineClass option id. |
| content | option content. |
| content.ptr | for option value with pointer type. |
| content.num | for option value with integer type |
| content.boolean | for option value with bool type |


