# rich_editor.h

## Overview

Defines structs, enumerations, and APIs related to <b>RichEditor</b>. <b>RichEditor</b> provides rich text editing capabilities, supporting custom text selection menus, styled string controllers, paragraph and text style settings, and haptic feedback control. It is suitable for scenarios where rich text editing and custom interaction menus need to be implemented in applications.

**Library**: libace_ndk.z.so

**Since**: 24

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md) | OH_ArkUI_TextEditorSelectionMenuOptions | Defines the text selection menu options of a text editor, which are used to customize the content of the text selection menu. It supports you in adding, replacing, or removing menu items based on service requirements, and is applicable to scenarios that require text operation menu customization, such as adding custom operation items like "Translate", "Search", and "Share", or replacing the default menu options. |
| [OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md) | OH_ArkUI_TextEditorPlaceholderOptions | Defines the placeholder text options for a text editor when there is no input. When the text editor content is empty, the placeholder text is displayed based on these options. After the user enters content, the placeholder text is automatically hidden. This is applicable to scenarios where input guidance needs to be provided for users. |
| [OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md) | OH_ArkUI_TextEditorStyledStringController | Defines the styled string controller of a text editor, which supports operations such as setting and obtaining a styled string, setting an input style, and controlling the cursor. It can be used to adjust the cursor position, set the selection, obtain the preview text, and perform backward deletion. |
| [OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md) | OH_ArkUI_TextEditorParagraphStyle | Defines the paragraph style of a text editor, which describes the formatting attributes of paragraphs in a text editor. You can call related APIs to set and obtain the paragraph style. It applies to scenarios where style attributes such as the paragraph alignment, indentation, and line spacing need to be set. |
| [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md) | OH_ArkUI_TextEditorTextStyle | Defines the text style of a text editor, which supports the setting of text attributes such as the font, color, and size. It applies to scenarios where the content style of a text editor needs to be controlled, helping you flexibly customize the display effect of text in the editor. For example, in a rich text editor, you can set styles such as the font, color, and size for different paragraphs or text. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_ArkUI_HapticFeedbackMode](#oh_arkui_hapticfeedbackmode) | OH_ArkUI_HapticFeedbackMode | Enumerates vibration effect types. |
| [OH_ArkUI_TextEditorSpanType](#oh_arkui_texteditorspantype) | OH_ArkUI_TextEditorSpanType | Enumerates the span types of a custom text selection menu, which are used to identify the span type of the text selection menu in the text editor. Different span types correspond to different content structures, affecting the display and interaction behavior of the custom menu. For example, the <b>OH_ARKUI_TEXT_EDITOR_SPAN_TYPE_TEXT</b> type is used when the user selects only text content, the <b>OH_ARKUI_TEXT_EDITOR_SPAN_TYPE_MIXED</b> type is used when the selection contains mixed content such as text and images, and the <b>OH_ARKUI_TEXT_EDITOR_SPAN_TYPE_BUILDER</b> type is used when a custom menu item layout is required. |
| [OH_ArkUI_TextEditorResponseType](#oh_arkui_texteditorresponsetype) | OH_ArkUI_TextEditorResponseType | Enumerates the response types of a custom text selection menu, which are used to identify the interaction method that triggers the menu pop-up. Different response types correspond to different user operations (such as right-click, long press, and mouse-based selection), allowing different menu content to be customized based on the response type. |
| [OH_ArkUI_TextMenuType](#oh_arkui_textmenutype) | OH_ArkUI_TextMenuType | Enumerates text menu types, which are used to distinguish different types of pop-up menus in the text editor, including the text selection menu and the preview menu. Different menu types correspond to different interaction scenarios and menu display modes. For example, the text selection menu pops up when the user selects text and is used for text operations such as copy and delete; the preview menu pops up when the user long-presses an image and is used to trigger image content drag preview as well as copy and deletion operations. |
| [OH_ArkUI_TextEditorType](#oh_arkui_texteditortype) | OH_ArkUI_TextEditorType | Enumerates the text editor input types. |

### Function

| Name | Description |
| -- | -- |
| [OH_ArkUI_TextEditorPlaceholderOptions* OH_ArkUI_TextEditorPlaceholderOptions_Create()](#oh_arkui_texteditorplaceholderoptions_create) | Creates an option object for the placeholder text used when there is no input. When the object is no longer used, call [OH_ArkUI_TextEditorPlaceholderOptions_Destroy](capi-rich-editor-h.md#oh_arkui_texteditorplaceholderoptions_destroy) to destroy it. |
| [void OH_ArkUI_TextEditorPlaceholderOptions_Destroy(OH_ArkUI_TextEditorPlaceholderOptions* options)](#oh_arkui_texteditorplaceholderoptions_destroy) | Destroys the option object for the placeholder text used when there is no input. |
| [OH_ArkUI_TextEditorStyledStringController* OH_ArkUI_TextEditorStyledStringController_Create()](#oh_arkui_texteditorstyledstringcontroller_create) | Creates a styled string controller object, which is used to control the styled string of the text editor when rich text content needs to be managed through styled strings (such as mixed layout of text and images, dynamic setting of paragraph or character styles, and other scenarios). When the object is no longer used, call [OH_ArkUI_TextEditorStyledStringController_Destroy](capi-rich-editor-h.md#oh_arkui_texteditorstyledstringcontroller_destroy) to destroy it. |
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

Enumerates the span types of a custom text selection menu, which are used to identify the span type of the text selection menu in the text editor. Different span types correspond to different content structures, affecting the display and interaction behavior of the custom menu. For example, the <b>OH_ARKUI_TEXT_EDITOR_SPAN_TYPE_TEXT</b> type is used when the user selects only text content, the <b>OH_ARKUI_TEXT_EDITOR_SPAN_TYPE_MIXED</b> type is used when the selection contains mixed content such as text and images, and the <b>OH_ARKUI_TEXT_EDITOR_SPAN_TYPE_BUILDER</b> type is used when a custom menu item layout is required.

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

Enumerates the response types of a custom text selection menu, which are used to identify the interaction method that triggers the menu pop-up. Different response types correspond to different user operations (such as right-click, long press, and mouse-based selection), allowing different menu content to be customized based on the response type.

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

Enumerates text menu types, which are used to distinguish different types of pop-up menus in the text editor, including the text selection menu and the preview menu. Different menu types correspond to different interaction scenarios and menu display modes. For example, the text selection menu pops up when the user selects text and is used for text operations such as copy and delete; the preview menu pops up when the user long-presses an image and is used to trigger image content drag preview as well as copy and deletion operations.

**Since**: 24

| Enum item | Description |
| -- | -- |
| OH_ARKUI_TEXT_EDITOR_SELECTION_MENU = 0 |  |
| OH_ARKUI_TEXT_EDITOR_PREVIEW_MENU = 1 |  |

### OH_ArkUI_TextEditorType

```c
enum OH_ArkUI_TextEditorType
```

**Description**

Enumerates the text editor input types.

**Since**: 26.2.0

| Enum item | Description |
| -- | -- |
| OH_ARKUI_TEXT_EDITOR_TYPE_NORMAL = 0 | Normal input mode.<br>**Since**: 26.2.0 |
| OH_ARKUI_TEXT_EDITOR_TYPE_NUMBER = 2 | Number input mode.<br>**Since**: 26.2.0 |
| OH_ARKUI_TEXT_EDITOR_TYPE_PHONE_NUMBER = 3 | Phone number input mode.<br>**Since**: 26.2.0 |
| OH_ARKUI_TEXT_EDITOR_TYPE_EMAIL = 5 | Email address input mode.<br>**Since**: 26.2.0 |
| OH_ARKUI_TEXT_EDITOR_TYPE_PASSWORD = 7 | Password input mode.<br>**Since**: 26.2.0 |
| OH_ARKUI_TEXT_EDITOR_TYPE_NUMBER_PASSWORD = 8 | Numeric password input mode.<br>**Since**: 26.2.0 |
| OH_ARKUI_TEXT_EDITOR_TYPE_SCREEN_LOCK_PASSWORD = 9 | Lock screen password input mode.<br>**Since**: 26.2.0 |
| OH_ARKUI_TEXT_EDITOR_TYPE_USER_NAME = 10 | Username input mode.<br>**Since**: 26.2.0 |
| OH_ARKUI_TEXT_EDITOR_TYPE_NEW_PASSWORD = 11 | New password input mode.<br>**Since**: 26.2.0 |
| OH_ARKUI_TEXT_EDITOR_TYPE_NUMBER_DECIMAL = 12 | Number input mode with a decimal point.<br>**Since**: 26.2.0 |
| OH_ARKUI_TEXT_EDITOR_TYPE_ONE_TIME_CODE = 14 | One time code input mode.<br>**Since**: 26.2.0 |


## Function description

### OH_ArkUI_TextEditorPlaceholderOptions_Create()

```c
OH_ArkUI_TextEditorPlaceholderOptions* OH_ArkUI_TextEditorPlaceholderOptions_Create()
```

**Description**

Creates an option object for the placeholder text used when there is no input. When the object is no longer used, call [OH_ArkUI_TextEditorPlaceholderOptions_Destroy](capi-rich-editor-h.md#oh_arkui_texteditorplaceholderoptions_destroy) to destroy it.

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

Creates a styled string controller object, which is used to control the styled string of the text editor when rich text content needs to be managed through styled strings (such as mixed layout of text and images, dynamic setting of paragraph or character styles, and other scenarios). When the object is no longer used, call [OH_ArkUI_TextEditorStyledStringController_Destroy](capi-rich-editor-h.md#oh_arkui_texteditorstyledstringcontroller_destroy) to destroy it.

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

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)* options | Pointer to the [OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md) object. |


