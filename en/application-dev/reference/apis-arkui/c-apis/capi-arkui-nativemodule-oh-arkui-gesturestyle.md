# OH_ArkUI_GestureStyle

```c
typedef struct OH_ArkUI_GestureStyle OH_ArkUI_GestureStyle
```

## Overview

Defines a gesture style. It applies to scenarios where a gesture style needs to be configured and related event callbacks need to be received, making it easier for an application to manage gesture styles and event callbacks in a unified manner.<br> Call [OH_ArkUI_GestureStyle_Create](capi-styled-string-h.md#oh_arkui_gesturestyle_create) to create the corresponding gesture style object.<br> After the object is created, call the <b>OH_ArkUI_GestureStyle_RegisterOnXXXCallback</b> series APIs to register specific event callbacks, for example, call [OH_ArkUI_GestureStyle_RegisterOnClickCallback](capi-styled-string-h.md#oh_arkui_gesturestyle_registeronclickcallback) to register the click event callback.<br> After use, call [OH_ArkUI_GestureStyle_Destroy](capi-styled-string-h.md#oh_arkui_gesturestyle_destroy) to destroy the gesture style object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [styled_string.h](capi-styled-string-h.md)

