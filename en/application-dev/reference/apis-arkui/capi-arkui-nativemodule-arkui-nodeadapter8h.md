# ArkUI_NodeAdapter*
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=c132cb02982e3d21dab23387c45e2aaf4eba6cc3 translatedAt=2026-09-20T09:18:37.520Z pushedAt=2026-09-21T12:25:18.432Z -->

```c
typedef struct ArkUI_NodeAdapter* ArkUI_NodeAdapterHandle
```

## Overview

Defines the pointer to a component adapter object, which is used for lazy loading of elements in scrollable components. This is applicable to scenarios where a large amount of scrollable content needs to be loaded on demand. It prevents all elements from being created at once, reducing memory usage and improving scrolling performance.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)
