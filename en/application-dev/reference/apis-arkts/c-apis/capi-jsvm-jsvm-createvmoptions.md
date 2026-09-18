# JSVM_CreateVMOptions

```c
typedef struct JSVM_CreateVMOptions {...} JSVM_CreateVMOptions
```

## Overview

Create the JavaScript VM with init option.

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| size_t maxOldGenerationSize | optional limits of memory use of the vm. |
| size_t maxYoungGenerationSize | optional limits of memory use of the vm. |
| size_t initialOldGenerationSize | optional limits of memory use of the vm. |
| size_t initialYoungGenerationSize | optional limits of memory use of the vm. |
| const char* snapshotBlobData | Optional startup snapshot data. |
| size_t snapshotBlobSize | Optional size of the startup snapshot data. |
| bool isForSnapshotting | Whether the VM is used for creating snapshot. |


