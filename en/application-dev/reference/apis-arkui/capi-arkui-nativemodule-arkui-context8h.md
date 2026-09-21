# ArkUI_Context*
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=a306693f0f46e5633c549769b8338f6bd7c191f4 translatedAt=2026-09-18T11:28:30.176Z pushedAt=2026-09-20T08:04:18.569Z -->

```c
typedef struct ArkUI_Context* ArkUI_ContextHandle
```

## Overview

Defines the pointer to the context object of ArkUI on the native side, which is used to represent the UI context of the page where the component is located. You can obtain the pointer through [OH_ArkUI_GetContextByNode](capi-native-node-h.md#oh_arkui_getcontextbynode) or [OH_ArkUI_GetContextFromNapiValue](capi-native-node-napi-h.md#oh_arkui_getcontextfromnapivalue) and use it as the context input parameter for APIs such as UI task scheduling, animation, and focus control.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_type.h](capi-native-type-h.md)
