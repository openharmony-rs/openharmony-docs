# OH_ArkUI_LetterSpacingStyle

```c
typedef struct OH_ArkUI_LetterSpacingStyle OH_ArkUI_LetterSpacingStyle
```

## Overview

Defines a letter spacing style, which is used to set the letter spacing of text to optimize the layout effect. It applies to scenarios where text is too densely arranged and difficult to read and the letter spacing needs to be adjusted, improving text readability and layout aesthetics.<br> Call [OH_ArkUI_LetterSpacingStyle_Create](capi-styled-string-h.md#oh_arkui_letterspacingstyle_create) to create a letter spacing style object.<br> After the object is created, call [OH_ArkUI_LetterSpacingStyle_SetLetterSpacing](capi-styled-string-h.md#oh_arkui_letterspacingstyle_setletterspacing) to set the specific letter spacing value. For details about the value selection principle, see the description of this API.<br> Call [OH_ArkUI_LetterSpacingStyle_GetLetterSpacing](capi-styled-string-h.md#oh_arkui_letterspacingstyle_getletterspacing) to obtain the letter spacing value.<br> When the object is no longer used, call [OH_ArkUI_LetterSpacingStyle_Destroy](capi-styled-string-h.md#oh_arkui_letterspacingstyle_destroy) to destroy it. If creation fails, do not call the preceding APIs.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [styled_string.h](capi-styled-string-h.md)

