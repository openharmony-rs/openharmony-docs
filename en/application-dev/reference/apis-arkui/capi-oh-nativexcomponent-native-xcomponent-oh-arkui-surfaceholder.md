# OH_ArkUI_SurfaceHolder
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @pengzhiwen3-->
<!--Designer: @dutie123-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=beada53a308464a4f981a52e4c6d5aeda1c1e48a translatedAt=2026-08-27T08:44:51.896Z pushedAt=2026-08-28T01:31:18.895Z -->

```c
typedef struct OH_ArkUI_SurfaceHolder OH_ArkUI_SurfaceHolder
```

## Overview

Defines **OH_ArkUI_SurfaceHolder**, which is used to encapsulate and manage the surface of the native **XComponent** component, providing access to and operation on the underlying rendering surface. An instance can be created through the [OH_ArkUI_SurfaceHolder_Create](capi-native-interface-xcomponent-h.md#oh_arkui_surfaceholder_create) API, which is suitable for scenarios where custom rendering is required on the native side or where connection with graphics/media components is needed.

**Since**: 19

**Related module**: [OH_NativeXComponent Native XComponent](capi-oh-nativexcomponent-native-xcomponent.md)

**Header file**: [native_interface_xcomponent.h](capi-native-interface-xcomponent-h.md)

