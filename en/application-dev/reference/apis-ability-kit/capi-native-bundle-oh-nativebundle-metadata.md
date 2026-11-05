# OH_NativeBundle_Metadata
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @memghaiyang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=e614db0ed9ef9e65ff9f340640f4a0fd5317e78d translatedAt=2026-11-04T09:48:52.346Z pushedAt=2026-11-04T09:52:41.312Z nl=1 -->

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
