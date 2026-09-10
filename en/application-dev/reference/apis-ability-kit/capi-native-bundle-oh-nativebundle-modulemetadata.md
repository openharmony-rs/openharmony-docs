# OH_NativeBundle_ModuleMetadata
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @memghaiyang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=1bd317f06f1afd85920306c4a4cf71333749080f translatedAt=2026-09-03T08:59:18.167Z pushedAt=2026-09-05T10:47:30.124Z -->

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
