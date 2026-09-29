# JSVM_DefineClassOptions

```c
typedef union JSVM_DefineClassOptions {...} JSVM_DefineClassOptions
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
| void* ptr | for option value with pointer type. |
| int num | for option value with integer type |
| bool boolean;
 } content | for option value with bool type |


