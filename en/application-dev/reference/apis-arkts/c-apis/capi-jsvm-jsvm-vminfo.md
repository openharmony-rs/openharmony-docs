# JSVM_VMInfo

```c
typedef struct JSVM_VMInfo {...} JSVM_VMInfo
```

## Overview

JavaScript VM info.

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t apiVersion | The highest API version this VM supports. |
| const char* engine | The engine name implementing the VM. |
| const char* version | The version of the VM. |
| uint32_t cachedDataVersionTag | The cached data version tag. |


