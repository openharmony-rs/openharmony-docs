# rich_editor.h

## Overview

Defines a set of RichEditor enum and interface.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md) | OH_ArkUI_TextEditorSelectionMenuOptions | Defines the text selection menu options of the text editor. |
| [OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md) | OH_ArkUI_TextEditorPlaceholderOptions | Defines the hint text options when no content is entered in the text editor. |
| [OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md) | OH_ArkUI_TextEditorStyledStringController | Defines the attribute string controller of the text editor. |
| [OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md) | OH_ArkUI_TextEditorParagraphStyle | Defines the paragraph style of the text editor. |
| [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md) | OH_ArkUI_TextEditorTextStyle | Defines the text style of the text editor. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_ArkUI_HapticFeedbackMode](#oh_arkui_hapticfeedbackmode) | OH_ArkUI_HapticFeedbackMode | Enumerates vibration effect types. |
| [OH_ArkUI_TextEditorSpanType](#oh_arkui_texteditorspantype) | OH_ArkUI_TextEditorSpanType | Enumerates the span types of a custom text selection menu. |
| [OH_ArkUI_TextEditorResponseType](#oh_arkui_texteditorresponsetype) | OH_ArkUI_TextEditorResponseType | Enumerates the response types of a custom text selection menu. |
| [OH_ArkUI_TextMenuType](#oh_arkui_textmenutype) | OH_ArkUI_TextMenuType | Enumerates text menu types. |

### Function

| Name | Description |
| -- | -- |
| [OH_ArkUI_TextEditorPlaceholderOptions* OH_ArkUI_TextEditorPlaceholderOptions_Create()](#oh_arkui_texteditorplaceholderoptions_create) | Creates an option object for the placeholder text used when there is no input. When the object is no longer used, call [OH_ArkUI_TextEditorPlaceholderOptions_Destroy](capi-rich-editor-h.md#oh_arkui_texteditorplaceholderoptions_destroy) to destroy it. |
| [void OH_ArkUI_TextEditorPlaceholderOptions_Destroy(OH_ArkUI_TextEditorPlaceholderOptions* options)](#oh_arkui_texteditorplaceholderoptions_destroy) | Destroys the option object for the placeholder text used when there is no input. |
| [OH_ArkUI_TextEditorStyledStringController* OH_ArkUI_TextEditorStyledStringController_Create()](#oh_arkui_texteditorstyledstringcontroller_create) | Creates a styled string controller object for the text editor. When the object is no longer used, call [OH_ArkUI_TextEditorStyledStringController_Destroy](capi-rich-editor-h.md#oh_arkui_texteditorstyledstringcontroller_destroy) to destroy it. |
| [void OH_ArkUI_TextEditorStyledStringController_Destroy(OH_ArkUI_TextEditorStyledStringController* controller)](#oh_arkui_texteditorstyledstringcontroller_destroy) | Destroys the styled string controller object. |
| [OH_ArkUI_TextEditorParagraphStyle* OH_ArkUI_TextEditorParagraphStyle_Create()](#oh_arkui_texteditorparagraphstyle_create) | Creates a paragraph style object for the text editor. When the object is no longer used, call [OH_ArkUI_TextEditorParagraphStyle_Destroy](capi-rich-editor-h.md#oh_arkui_texteditorparagraphstyle_destroy) to destroy it. |
| [void OH_ArkUI_TextEditorParagraphStyle_Destroy(OH_ArkUI_TextEditorParagraphStyle* style)](#oh_arkui_texteditorparagraphstyle_destroy) | Destroys the paragraph style object. |
| [OH_ArkUI_TextEditorTextStyle* OH_ArkUI_TextEditorTextStyle_Create()](#oh_arkui_texteditortextstyle_create) | Creates a text style object. When the object is no longer used, call [OH_ArkUI_TextEditorTextStyle_Destroy](capi-rich-editor-h.md#oh_arkui_texteditortextstyle_destroy) to destroy it. |
| [void OH_ArkUI_TextEditorTextStyle_Destroy(OH_ArkUI_TextEditorTextStyle* style)](#oh_arkui_texteditortextstyle_destroy) | Destroys the text style object. |
| [OH_ArkUI_TextEditorSelectionMenuOptions* OH_ArkUI_TextEditorSelectionMenuOptions_Create()](#oh_arkui_texteditorselectionmenuoptions_create) | Creates a text selection menu option object of the text editor. When the object is no longer used, call [OH_ArkUI_TextEditorSelectionMenuOptions_Destroy](capi-rich-editor-h.md#oh_arkui_texteditorselectionmenuoptions_destroy) to destroy it. |
| [void OH_ArkUI_TextEditorSelectionMenuOptions_Destroy(OH_ArkUI_TextEditorSelectionMenuOptions* options)](#oh_arkui_texteditorselectionmenuoptions_destroy) | Destroys the text selection menu option object of the text editor. |

## Enum type description

### OH_ArkUI_HapticFeedbackMode

```c
enum OH_ArkUI_HapticFeedbackMode
```

**Description**

Enumerates vibration effect types.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

| Enum item | Description |
| -- | -- |
| OH_ARKUI_HAPTIC_FEEDBACK_MODE_DISABLED = 0 |  |
| OH_ARKUI_HAPTIC_FEEDBACK_MODE_ENABLED = 1 |  |
| OH_ARKUI_HAPTIC_FEEDBACK_MODE_AUTO = 2 |  |

### OH_ArkUI_TextEditorSpanType

```c
enum OH_ArkUI_TextEditorSpanType
```

**Description**

Enumerates the span types of a custom text selection menu.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

| Enum item | Description |
| -- | -- |
| OH_ARKUI_TEXT_EDITOR_SPAN_TYPE_TEXT = 0 |  |
| OH_ARKUI_TEXT_EDITOR_SPAN_TYPE_IMAGE = 1 |  |
| OH_ARKUI_TEXT_EDITOR_SPAN_TYPE_MIXED = 2 |  |
| OH_ARKUI_TEXT_EDITOR_SPAN_TYPE_BUILDER = 3 |  |
| OH_ARKUI_TEXT_EDITOR_SPAN_TYPE_DEFAULT = 4 |  |

### OH_ArkUI_TextEditorResponseType

```c
enum OH_ArkUI_TextEditorResponseType
```

**Description**

Enumerates the response types of a custom text selection menu.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

| Enum item | Description |
| -- | -- |
| OH_ARKUI_TEXT_EDITOR_RESPONSE_TYPE_RIGHT_CLICK = 0 |  |
| OH_ARKUI_TEXT_EDITOR_RESPONSE_TYPE_LONG_PRESS = 1 |  |
| OH_ARKUI_TEXT_EDITOR_RESPONSE_TYPE_SELECT = 2 |  |
| OH_ARKUI_TEXT_EDITOR_RESPONSE_TYPE_DEFAULT = 3 |  |

### OH_ArkUI_TextMenuType

```c
enum OH_ArkUI_TextMenuType
```

**Description**

Enumerates text menu types.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

| Enum item | Description |
| -- | -- |
| OH_ARKUI_TEXT_EDITOR_SELECTION_MENU = 0 |  |
| OH_ARKUI_TEXT_EDITOR_PREVIEW_MENU = 1 |  |


## Function description

### OH_ArkUI_TextEditorPlaceholderOptions_Create()

```c
OH_ArkUI_TextEditorPlaceholderOptions* OH_ArkUI_TextEditorPlaceholderOptions_Create()
```

**Description**

Creates an option object for the placeholder text used when there is no input. When the object is no longer used, call [OH_ArkUI_TextEditorPlaceholderOptions_Destroy](capi-rich-editor-h.md#oh_arkui_texteditorplaceholderoptions_destroy) to destroy it.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_TextEditorPlaceholderOptions*](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md) | Pointer to the [OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md) object. |

### OH_ArkUI_TextEditorPlaceholderOptions_Destroy()

```c
void OH_ArkUI_TextEditorPlaceholderOptions_Destroy(OH_ArkUI_TextEditorPlaceholderOptions* options)
```

**Description**

Destroys the option object for the placeholder text used when there is no input.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md)* options | Pointer to the [OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md) object. |

### OH_ArkUI_TextEditorStyledStringController_Create()

```c
OH_ArkUI_TextEditorStyledStringController* OH_ArkUI_TextEditorStyledStringController_Create()
```

**Description**

Creates a styled string controller object for the text editor. When the object is no longer used, call [OH_ArkUI_TextEditorStyledStringController_Destroy](capi-rich-editor-h.md#oh_arkui_texteditorstyledstringcontroller_destroy) to destroy it.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_TextEditorStyledStringController*](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md) | Pointer to the [OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md) object. |

### OH_ArkUI_TextEditorStyledStringController_Destroy()

```c
void OH_ArkUI_TextEditorStyledStringController_Destroy(OH_ArkUI_TextEditorStyledStringController* controller)
```

**Description**

Destroys the styled string controller object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)* controller | Pointer to the [OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md) object. |

### OH_ArkUI_TextEditorParagraphStyle_Create()

```c
OH_ArkUI_TextEditorParagraphStyle* OH_ArkUI_TextEditorParagraphStyle_Create()
```

**Description**

Creates a paragraph style object for the text editor. When the object is no longer used, call [OH_ArkUI_TextEditorParagraphStyle_Destroy](capi-rich-editor-h.md#oh_arkui_texteditorparagraphstyle_destroy) to destroy it.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_TextEditorParagraphStyle*](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md) | Pointer to the [OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md) object. |

### OH_ArkUI_TextEditorParagraphStyle_Destroy()

```c
void OH_ArkUI_TextEditorParagraphStyle_Destroy(OH_ArkUI_TextEditorParagraphStyle* style)
```

**Description**

Destroys the paragraph style object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)* style | Pointer to the [OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md) object. |

### OH_ArkUI_TextEditorTextStyle_Create()

```c
OH_ArkUI_TextEditorTextStyle* OH_ArkUI_TextEditorTextStyle_Create()
```

**Description**

Creates a text style object. When the object is no longer used, call [OH_ArkUI_TextEditorTextStyle_Destroy](capi-rich-editor-h.md#oh_arkui_texteditortextstyle_destroy) to destroy it.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_TextEditorTextStyle*](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md) | Pointer to the [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md) object. |

### OH_ArkUI_TextEditorTextStyle_Destroy()

```c
void OH_ArkUI_TextEditorTextStyle_Destroy(OH_ArkUI_TextEditorTextStyle* style)
```

**Description**

Destroys the text style object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md)* style | Pointer to the [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md) object. |

### OH_ArkUI_TextEditorSelectionMenuOptions_Create()

```c
OH_ArkUI_TextEditorSelectionMenuOptions* OH_ArkUI_TextEditorSelectionMenuOptions_Create()
```

**Description**

Creates a text selection menu option object of the text editor. When the object is no longer used, call [OH_ArkUI_TextEditorSelectionMenuOptions_Destroy](capi-rich-editor-h.md#oh_arkui_texteditorselectionmenuoptions_destroy) to destroy it.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_TextEditorSelectionMenuOptions*](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md) | Pointer to the [OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md) object. |

### OH_ArkUI_TextEditorSelectionMenuOptions_Destroy()

```c
void OH_ArkUI_TextEditorSelectionMenuOptions_Destroy(OH_ArkUI_TextEditorSelectionMenuOptions* options)
```

**Description**

Destroys the text selection menu option object of the text editor.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)* options | Pointer to the [OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md) object. |


