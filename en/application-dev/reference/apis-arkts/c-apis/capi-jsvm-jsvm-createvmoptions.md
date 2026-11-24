# JSVM_CreateVMOptions

```c
typedef struct JSVM_CreateVMOptions {...} JSVM_CreateVMOptions
```

## Overview

Create the JavaScript VM with init option.

<!--Device-typedef struct JSVM_CreateVMOptions {...} JSVM_CreateVMOptions--><!--Device-typedef struct JSVM_CreateVMOptions {...} JSVM_CreateVMOptions-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 11

**Related module**: [JSVM](capi-arkts-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| size_t maxOldGenerationSize | optional limits of memory use of the vm.<br><!--Device-size_t maxOldGenerationSize--><!--Device-size_t maxOldGenerationSize-End--> |
| size_t maxYoungGenerationSize | optional limits of memory use of the vm.<br><!--Device-size_t maxYoungGenerationSize--><!--Device-size_t maxYoungGenerationSize-End--> |
| size_t initialOldGenerationSize | optional limits of memory use of the vm.<br><!--Device-size_t initialOldGenerationSize--><!--Device-size_t initialOldGenerationSize-End--> |
| size_t initialYoungGenerationSize | optional limits of memory use of the vm.<br><!--Device-size_t initialYoungGenerationSize--><!--Device-size_t initialYoungGenerationSize-End--> |
| const char* snapshotBlobData | Optional startup snapshot data.<br><!--Device-const char* snapshotBlobData--><!--Device-const char* snapshotBlobData-End--> |
| size_t snapshotBlobSize | Optional size of the startup snapshot data.<br><!--Device-size_t snapshotBlobSize--><!--Device-size_t snapshotBlobSize-End--> |
| bool isForSnapshotting | Whether the VM is used for creating snapshot.<br><!--Device-bool isForSnapshotting--><!--Device-bool isForSnapshotting-End--> |


