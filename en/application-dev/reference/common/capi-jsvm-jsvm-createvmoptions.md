# JSVM_CreateVMOptions
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou; @string_sz-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

## Overview

Defines options for creating a JavaScript VM.

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
| bool isForSnapshotting | Whether the VM is used for snapshotting.|
