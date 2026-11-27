# ArkUI_Context*
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=f003098b54e4ade8c39948901851665b18d3ac5a translatedAt=2026-11-23T06:56:54.050Z pushedAt=2026-11-24T09:20:50.216Z nl=1 -->

```c
typedef struct ArkUI_Context* ArkUI_ContextHandle
```

## Overview

Defines a pointer to the ArkUI context instance object on the native side, used to represent the UIContext of the page where the component is located. You can obtain this pointer through [OH_ArkUI_GetContextByNode](capi-native-node-h.md#oh_arkui_getcontextbynode) or [OH_ArkUI_GetContextFromNapiValue](capi-native-node-napi-h.md#oh_arkui_getcontextfromnapivalue) and use it as the context input parameter of APIs for UI task scheduling, animations, and focus control.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [common_type.h](capi-common-type-h.md)
