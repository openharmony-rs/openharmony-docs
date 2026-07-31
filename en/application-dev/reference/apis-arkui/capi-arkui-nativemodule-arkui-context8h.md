# ArkUI_Context\*
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct ArkUI_Context* ArkUI_ContextHandle
```

## Overview

Defines the pointer to the context object of ArkUI on the native side, which is used to represent the UI context of the page where the component is located. You can obtain the pointer through [OH_ArkUI_GetContextByNode](capi-native-node-h.md#oh_arkui_getcontextbynode) or [OH_ArkUI_GetContextFromNapiValue](capi-native-node-napi-h.md#oh_arkui_getcontextfromnapivalue) and use the pointer as the context input parameter for APIs such as UI task scheduling, animation, and focus control.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_type.h](capi-native-type-h.md)
