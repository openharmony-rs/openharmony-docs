# ArkUI_Context
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=6fb11341546ce57d31a849bc70cdf0bbc85a01fd translatedAt=2026-11-23T06:56:18.876Z pushedAt=2026-11-24T09:19:43.216Z nl=1 -->

```c
typedef struct ArkUI_Context ArkUI_Context
```

## Overview

Defines an ArkUI native UI context instance object, used to represent the UIContext of the page where the component is located. Its pointer type is [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md). You can obtain the corresponding context through [OH_ArkUI_GetContextByNode](capi-native-node-h.md#oh_arkui_getcontextbynode) and use it as the context input parameter of the APIs for drag operations, animations, and UI task scheduling.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [common_type.h](capi-common-type-h.md)
