# OH_ArkUI_SurfaceCallback
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @pengzhiwen3-->
<!--Designer: @dutie123-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=33898b66eb6c0bf66810bb0d90faa36b55a4ad07 translatedAt=2026-11-18T09:11:47.666Z pushedAt=2026-11-20T02:05:44.495Z nl=1 -->

```c
typedef struct OH_ArkUI_SurfaceCallback OH_ArkUI_SurfaceCallback
```

## Overview

Defines the surface lifecycle callback. When the surface of the **XComponent** component is created, destroyed, or resized, the corresponding callback is triggered. When the application window switches between the foreground and background, causing the surface to be shown or hidden, the corresponding callback is triggered (the show/hide callback capability is supported since API version 20). You can obtain the surface pointer in the callback and perform custom rendering (for example, OpenGL ES rendering, Vulkan rendering, or video decoding and rendering).

**Since**: 19

**Related module**: [OH_NativeXComponent Native XComponent](capi-oh-nativexcomponent-native-xcomponent.md)

**Header file**: [native_interface_xcomponent.h](capi-native-interface-xcomponent-h.md)

