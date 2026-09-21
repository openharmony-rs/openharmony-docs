# OH_ArkUI_GestureStyle

```c
typedef struct OH_ArkUI_GestureStyle OH_ArkUI_GestureStyle
```

## Overview

Defines a gesture style. {@link OH_ArkUI_GestureStyle_Create} can be used to create a gesture style object.<br>{@link OH_ArkUI_GestureStyle_Destroy} can be used to destroy the gesture style object.<br><br>After the object is created, the **OH_ArkUI_GestureStyle_RegisterOnXXXCallback** series APIs can be used to<br>register specific event callbacks. For example, you can use {@link OH_ArkUI_GestureStyle_RegisterOnClickCallback} to register a click event callback.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [styled_string.h](capi-styled-string-h.md)

