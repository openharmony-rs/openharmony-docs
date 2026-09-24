# OH_ArkUI_SpanStyle

```c
typedef struct OH_ArkUI_SpanStyle OH_ArkUI_SpanStyle
```

## Overview

Defines a styled string style.<br> {@link OH_ArkUI_SpanStyle_Create} can be used to create a styled<br>string style object.<br> {@link OH_ArkUI_SpanStyle_Destroy} can be used to destroy the styled string style<br>object.<br> After the object is created, {@link OH_ArkUI_SpanStyle_SetStart} and<br>{@link OH_ArkUI_SpanStyle_SetLength} can be used to set the usage scope of the style.<br> After the object is<br>created, the **OH_ArkUI_SpanStyle_SetXXXStyle** series APIs can be used to set the specific styles that take effect.<br>For example, you can use {@link OH_ArkUI_SpanStyle_SetTextStyle} to set the font style.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [styled_string.h](capi-styled-string-h.md)

