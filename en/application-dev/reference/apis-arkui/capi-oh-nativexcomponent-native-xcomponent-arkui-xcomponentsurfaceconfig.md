# ArkUI_XComponentSurfaceConfig
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @pengzhiwen3-->
<!--Designer: @dutie123-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=86516607de4ae31b89a087b4feaa5c2b41c67026 translatedAt=2026-08-27T08:43:50.874Z pushedAt=2026-08-28T01:26:40.177Z -->

```c
typedef struct ArkUI_XComponentSurfaceConfig ArkUI_XComponentSurfaceConfig
```

## Overview

Defines the surface configuration for setting whether the surface held by the **XComponent** component is treated as opaque during rendering. This is applicable to scenarios that require high **XComponent** rendering performance. Setting the surface to opaque reduces rendering composition overhead and improves rendering performance. Note that the surface should be set to opaque only when all the content actually rendered on it is opaque; otherwise, rendering exceptions may occur.

**Since**: 22

**Related module**: [OH_NativeXComponent Native XComponent](capi-oh-nativexcomponent-native-xcomponent.md)

**Header file**: [native_interface_xcomponent.h](capi-native-interface-xcomponent-h.md)

