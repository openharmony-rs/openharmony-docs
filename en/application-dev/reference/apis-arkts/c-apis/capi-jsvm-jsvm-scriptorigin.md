# JSVM_ScriptOrigin

```c
typedef struct JSVM_ScriptOrigin {...} JSVM_ScriptOrigin
```

## Overview

Source code information.

<!--Device-typedef struct JSVM_ScriptOrigin {...} JSVM_ScriptOrigin--><!--Device-typedef struct JSVM_ScriptOrigin {...} JSVM_ScriptOrigin-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 12

**Related module**: [JSVM](capi-arkts-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const char* sourceMapUrl | Sourcemap url.<br><!--Device-const char* sourceMapUrl--><!--Device-const char* sourceMapUrl-End--> |
| const char* resourceName | Resource name.<br><!--Device-const char* resourceName--><!--Device-const char* resourceName-End--> |
| size_t resourceLineOffset | Resource line offset.<br><!--Device-size_t resourceLineOffset--><!--Device-size_t resourceLineOffset-End--> |
| size_t resourceColumnOffset | Resource column offset.<br><!--Device-size_t resourceColumnOffset--><!--Device-size_t resourceColumnOffset-End--> |


