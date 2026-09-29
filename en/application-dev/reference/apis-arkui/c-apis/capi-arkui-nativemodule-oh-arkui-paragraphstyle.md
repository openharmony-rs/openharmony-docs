# OH_ArkUI_ParagraphStyle

```c
typedef struct OH_ArkUI_ParagraphStyle OH_ArkUI_ParagraphStyle
```

## Overview

Defines a paragraph style for uniformly setting the text alignment, line break, truncation, and other layout behaviors when building rich text paragraphs. It applies to scenarios that require fine-grained layout control over paragraphs, for example, setting the paragraph alignment in a rich text editor, and controlling the line break and truncation of long text in a news reader.<br> Call [OH_ArkUI_ParagraphStyle_Create](capi-styled-string-h.md#oh_arkui_paragraphstyle_create) to create the corresponding paragraph style object.<br> Call [OH_ArkUI_ParagraphStyle_Destroy](capi-styled-string-h.md#oh_arkui_paragraphstyle_destroy) to destroy the paragraph style object.<br> After the object is created, call the <b>OH_ArkUI_ParagraphStyle_SetXXX</b> series APIs to set specific styles, for example, call [OH_ArkUI_ParagraphStyle_SetTextAlign](capi-styled-string-h.md#oh_arkui_paragraphstyle_settextalign) to set the text alignment. If the object fails to be created (a null pointer is returned) or the object has been destroyed, calling the <b>SetXXX</b> series APIs will not take effect.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [styled_string.h](capi-styled-string-h.md)

