# ArkUI_Context

```c
typedef struct ArkUI_Context ArkUI_Context
```

## Overview

Defines a context object of the ArkUI native UI, which is used to represent the UI context of the page where the component is located. The pointer type is [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md). You can obtain the context using [OH_ArkUI_GetContextByNode](capi-native-node-h.md#oh_arkui_getcontextbynode) and use it as the input parameter for APIs such as dragging, animation, and UI task scheduling.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-others-arkui-nativemodule.md)

**Header file**: [common_type.h](capi-common-type-h.md)

