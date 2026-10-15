# ArkUI_XComponentSurfaceConfig
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @pengzhiwen3-->
<!--Designer: @dutie123-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=5a5f201351bc507eed1f4198e52fee2b1f6735cb translatedAt=2026-10-10T10:37:58.381Z pushedAt=2026-10-15T02:37:53.401Z -->

```c
typedef struct ArkUI_XComponentSurfaceConfig ArkUI_XComponentSurfaceConfig
```

## Overview

Defines the surface configuration for setting whether the surface held by the **XComponent** component is treated as opaque during rendering. This is applicable to scenarios that require high **XComponent** rendering performance. Setting the surface to opaque reduces rendering composition overhead and improves rendering performance. Note that the surface should be set to opaque only when all the content actually rendered on it is opaque; otherwise, rendering exceptions may occur.

**Since**: 22

**Related module**: [OH_NativeXComponent Native XComponent](capi-oh-nativexcomponent-native-xcomponent.md)

**Header file**: [native_interface_xcomponent.h](capi-native-interface-xcomponent-h.md)

