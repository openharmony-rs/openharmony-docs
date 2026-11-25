# OH_NativeBundle_ElementName
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @memghaiyang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=6273e0cee115a95082fe5ceee9943e85a85ead90 translatedAt=2026-11-04T09:48:46.990Z pushedAt=2026-11-04T09:52:33.930Z nl=1 -->

```c
struct OH_NativeBundle_ElementName {...}
typedef struct OH_NativeBundle_ElementName OH_NativeBundle_ElementName
```

## Overview

The struct describes the elementName information.

**Since**: 13

**Related module**: [Native_Bundle](capi-native-bundle.md)

**Header file**: [native_interface_bundle.h](capi-native-interface-bundle-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| char* bundleName | Pointer to the bundle name of the application.|
| char* moduleName | Pointer to the module name.|
| char* abilityName | Ability name. |
