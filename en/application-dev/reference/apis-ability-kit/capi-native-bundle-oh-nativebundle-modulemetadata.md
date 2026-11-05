# OH_NativeBundle_ModuleMetadata
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @memghaiyang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=5b5c8c53025a3325cca30785dd91b54558d445fc translatedAt=2026-11-04T09:49:31.744Z pushedAt=2026-11-04T09:52:46.230Z nl=1 -->

```c
typedef struct OH_NativeBundle_ModuleMetadata {...} OH_NativeBundle_ModuleMetadata
```

## Overview

The struct describes the metadata of a module.

**Since**: 20

**Related module**: [Native_Bundle](capi-native-bundle.md)

**Header file**: [native_interface_bundle.h](capi-native-interface-bundle-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| char* moduleName | Pointer to the module name.|
| [OH_NativeBundle_Metadata*](capi-native-bundle-oh-nativebundle-metadata.md) metadataArray | Pointer to an array containing the module's metadata.|
| size_t metadataArraySize | Size of the metadata array of the module. It must be used together with metadataArray and should be equal to the actual number of elements in the metadataArray array. An incorrect value may cause array out-of-bounds access or abnormal data access. |
