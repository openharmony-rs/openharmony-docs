# JSVM_CreateVMOptions

<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=93671cc034f483d1b8e032e6aa319b90dbbd1186 translatedAt=2026-06-18T08:21:07.215Z pushedAt=2026-06-18T09:19:01.911Z -->

```c
typedef struct {...} JSVM_CreateVMOptions
```

## Overview

Defines options for creating a JavaScript VM.

**Use scenario:** Customizing JavaScript virtual machine memory configurations for applications, using snapshot functionality to accelerate virtual machine startup, and operating in embedded or resource-constrained environments with special requirements for virtual machine memory usage.

**System capability:** SystemCapability.ArkCompiler.JSVM

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| size_t maxOldGenerationSize | Maximum size of the old-generation memory.|
| size_t maxYoungGenerationSize | Maximum size of the young-generation memory.|
| size_t initialOldGenerationSize | Initial size of the old-generation memory.|
| size_t initialYoungGenerationSize | Initial size of the young-generation memory.|
| const char* snapshotBlobData | Startup snapshot data.|
| size_t snapshotBlobSize | Size of the startup snapshot data.|
| bool isForSnapshotting | Whether the VM is used for snapshotting. If the value is **true**, VM is used for snapshotting. If the value is **false**, VM is not used for snapshotting.|