# JSVM_CompileOptions

```c
typedef struct JSVM_CompileOptions {...} JSVM_CompileOptions
```

## Overview

Compile Options

**Since**: 12

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [JSVM_CompileOptionId](capi-jsvm-types-h.md#jsvm_compileoptionid) id | compile option id. |
| union | option content. |
| void *ptr | ptr type. |
| int num | int type. |
| bool boolean;
 } content | bool type. |


