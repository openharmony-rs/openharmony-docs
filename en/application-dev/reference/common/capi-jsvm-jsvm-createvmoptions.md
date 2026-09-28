# JSVM_CreateVMOptions

<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=21434ce8d323ecbd7d67463989a2ef075be92cec translatedAt=2026-08-27T03:47:24.280Z pushedAt=2026-08-27T06:29:30.873Z -->

```c
typedef struct {...} JSVM_CreateVMOptions
```

## Overview

Defines options for creating a JavaScript VM.

**Use scenario**: Scenarios where an app needs to customize the memory configuration of a JavaScript VM, needs to use the snapshot feature to accelerate VM startup, or has special requirements on VM memory usage in embedded or resource-constrained environments.

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