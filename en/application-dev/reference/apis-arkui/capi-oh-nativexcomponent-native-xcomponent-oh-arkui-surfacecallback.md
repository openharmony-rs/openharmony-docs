# OH_ArkUI_SurfaceCallback
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @pengzhiwen3-->
<!--Designer: @dutie123-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=beada53a308464a4f981a52e4c6d5aeda1c1e48a translatedAt=2026-08-27T08:43:59.826Z pushedAt=2026-08-28T01:29:30.059Z -->

```c
typedef struct OH_ArkUI_SurfaceCallback OH_ArkUI_SurfaceCallback
```

## Overview

Defines a surface lifecycle callback. When the surface of the **XComponent** component is created, destroyed, or resized, the corresponding callback is triggered. You can obtain the surface pointer in the callback and perform custom rendering (for example, OpenGL ES rendering, Vulkan rendering, or video decoding rendering).

**Since**: 19

**Related module**: [OH_NativeXComponent Native XComponent](capi-oh-nativexcomponent-native-xcomponent.md)

**Header file**: [native_interface_xcomponent.h](capi-native-interface-xcomponent-h.md)

