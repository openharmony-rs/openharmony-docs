# JSVM_VMInfo

```c
typedef struct JSVM_VMInfo {...} JSVM_VMInfo
```

## Overview

JavaScript VM info.

<!--Device-typedef struct JSVM_VMInfo {...} JSVM_VMInfo--><!--Device-typedef struct JSVM_VMInfo {...} JSVM_VMInfo-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 11

**Related module**: [JSVM](capi-arkts-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t apiVersion | The highest API version this VM supports.<br><!--Device-uint32_t apiVersion--><!--Device-uint32_t apiVersion-End--> |
| const char* engine | The engine name implementing the VM.<br><!--Device-const char* engine--><!--Device-const char* engine-End--> |
| const char* version | The version of the VM.<br><!--Device-const char* version--><!--Device-const char* version-End--> |
| uint32_t cachedDataVersionTag | The cached data version tag.<br><!--Device-uint32_t cachedDataVersionTag--><!--Device-uint32_t cachedDataVersionTag-End--> |


