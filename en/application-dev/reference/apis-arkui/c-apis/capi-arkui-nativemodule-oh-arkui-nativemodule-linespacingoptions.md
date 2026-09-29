# OH_ArkUI_NativeModule_LineSpacingOptions

```c
typedef struct OH_ArkUI_NativeModule_LineSpacingOptions OH_ArkUI_NativeModule_LineSpacingOptions
```

## Overview

Defines a text line spacing option object, which is used to set whether the text line spacing takes effect only between lines. You can create a line spacing option object by calling [OH_ArkUI_NativeModule_LineSpacingOptions_Create](capi-text-h.md#oh_arkui_nativemodule_linespacingoptions_create). After the object is used, you must call [OH_ArkUI_NativeModule_LineSpacingOptions_Destroy](capi-text-h.md#oh_arkui_nativemodule_linespacingoptions_destroy) to destroy it and release resources. The two APIs must be used in pairs; otherwise, a memory leak occurs. After the object is created, you can call [OH_ArkUI_NativeModule_LineSpacingOptions_SetOnlyBetweenLines](capi-text-h.md#oh_arkui_nativemodule_linespacingoptions_setonlybetweenlines) to set whether the line spacing takes effect only between lines, and call [OH_ArkUI_NativeModule_LineSpacingOptions_GetOnlyBetweenLines](capi-text-h.md#oh_arkui_nativemodule_linespacingoptions_getonlybetweenlines) to obtain the line spacing configuration. This struct is applicable to scenarios that require precise control over the display effect of text line spacing, such as text display where no line spacing is added to the first and last lines.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [text.h](capi-text-h.md)

