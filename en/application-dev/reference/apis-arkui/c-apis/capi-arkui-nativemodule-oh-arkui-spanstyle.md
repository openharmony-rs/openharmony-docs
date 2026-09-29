# OH_ArkUI_SpanStyle

```c
typedef struct OH_ArkUI_SpanStyle OH_ArkUI_SpanStyle
```

## Overview

Defines a styled string style object, which is used to set style effects for text within a specified range of a styled string. It supports flexible combination of multiple style types and precise range specification, and is suitable for scenarios where different styles need to be applied to different segments of the same styled string to achieve rich text effects, for example, using different colors and font sizes for different message segments in a chat application, setting different styles for titles and body text in a news reader, and highlighting key content in a note-taking application.<br> Call [OH_ArkUI_SpanStyle_Create](capi-styled-string-h.md#oh_arkui_spanstyle_create) to create a styled string style object.<br> Call [OH_ArkUI_SpanStyle_Destroy](capi-styled-string-h.md#oh_arkui_spanstyle_destroy) to destroy the styled string style object.<br> After the object is created, call [OH_ArkUI_SpanStyle_SetStart](capi-styled-string-h.md#oh_arkui_spanstyle_setstart) and [OH_ArkUI_SpanStyle_SetLength](capi-styled-string-h.md#oh_arkui_spanstyle_setlength) to specify the range to which the style applies.<br> Call the <b>OH_ArkUI_SpanStyle_SetXXXStyle</b> series APIs to set the specific styles to take effect. The range specification and style settings must be used together for the styles to take effect within the specified range.<br> For example, call [OH_ArkUI_SpanStyle_SetTextStyle](capi-styled-string-h.md#oh_arkui_spanstyle_settextstyle) to set the font style effect. The configured <b>SpanStyle</b> must be added to the styled string to take effect.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [styled_string.h](capi-styled-string-h.md)

