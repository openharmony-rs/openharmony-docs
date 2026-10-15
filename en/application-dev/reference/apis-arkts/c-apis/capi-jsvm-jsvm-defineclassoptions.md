# JSVM_DefineClassOptions

```c
typedef struct JSVM_DefineClassOptions {...} JSVM_DefineClassOptions
```

## Overview

DefineClass options.

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 18

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| JSVM_DefineClassOptionsId id | DefineClass option id. |
| content.ptr | for option value with pointer type. |
| content.num | for option value with integer type |
| content.boolean | for option value with bool type |


