# ArkUI_ContextHandle

```c
typedef struct ArkUI_ContextHandle ArkUI_ContextHandle
```

## Overview

Defines the pointer to the context object of ArkUI on the native side, which is used to represent the UI context of the page where the component is located. You can obtain the pointer through OH_ArkUI_GetContextByNode or OH_ArkUI_GetContextFromNapiValue and use the pointer as the context input parameter for APIs such as UI task scheduling, animation, and focus control.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [common_type.h](capi-common-type-h.md)

