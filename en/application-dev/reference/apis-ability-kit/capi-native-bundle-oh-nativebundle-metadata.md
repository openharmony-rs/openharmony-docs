# OH_NativeBundle_Metadata
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @memghaiyang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=850c7d4f71d6bc50d82f299a21bb9cea3a266f3d translatedAt=2026-09-03T08:58:43.251Z pushedAt=2026-09-05T10:47:30.121Z -->

```c
typedef struct OH_NativeBundle_Metadata {...} OH_NativeBundle_Metadata
```

## Overview

The struct describes the metadata information.

**Since**: 20

**Related module**: [Native_Bundle](capi-native-bundle.md)

**Header file**: [native_interface_bundle.h](capi-native-interface-bundle-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| char* name | Pointer to the name of the metadata.|
| char* value | Pointer to the value of the metadata.|
| char* resource | Pointer to the resource linked to the metadata.|
