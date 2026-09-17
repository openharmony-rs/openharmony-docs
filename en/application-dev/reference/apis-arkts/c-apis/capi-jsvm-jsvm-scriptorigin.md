# JSVM_ScriptOrigin

```c
typedef struct JSVM_ScriptOrigin {...} JSVM_ScriptOrigin
```

## Overview

Source code information.

**Since**: 12

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const char* sourceMapUrl | Sourcemap url. |
| const char* resourceName | Resource name. |
| size_t resourceLineOffset | Resource line offset. |
| size_t resourceColumnOffset | Resource column offset. |


