# ArkUI_NodeAttributeType (Rich Text Component Attribute)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiangyuan6; @carnivore233-->
<!--Designer: @xiangyuan6; @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=7b2fe8ea97c19740abb5e459d74af77596c35112 translatedAt=2026-08-25T02:24:06.655Z pushedAt=2026-08-26T10:44:05.546Z -->

```c
enum ArkUI_NodeAttributeType
```

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side for rich text components, used to customize the appearance, interaction behavior, and layout effects of the **TextEditor** component to meet differentiated configuration requirements for rich text editors in different service scenarios.

**Since**: 24

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

## NODE_TEXT_EDITOR_ENTER_KEY_TYPE

```c
NODE_TEXT_EDITOR_ENTER_KEY_TYPE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_EDITOR = 22000
```

Type of the **Enter** key of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Type of the **Enter** key. The parameter type is [ArkUI_EnterKeyType](capi-text-common-h.md#arkui_enterkeytype). The default value is **ARKUI_ENTER_KEY_TYPE_NEW_LINE**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Type of the **Enter** key. The parameter type is [ArkUI_EnterKeyType](capi-text-common-h.md#arkui_enterkeytype).|

## NODE_TEXT_EDITOR_CARET_COLOR

```c
NODE_TEXT_EDITOR_CARET_COLOR = 22001
```

Caret color of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Caret color, in 0xARGB format, for example, **0xFFFF0000** indicates red. The color follows the system theme color by default. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Caret color, in 0xARGB format, for example, **0xFFFF0000** indicates red. The color follows the system theme color by default. |

## NODE_TEXT_EDITOR_SCROLL_BAR_COLOR

```c
NODE_TEXT_EDITOR_SCROLL_BAR_COLOR = 22002
```

Scroll bar color of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| .data[0].u32 | Scroll bar color, in 0xARGB format, for example, **0xFFFF0000** indicates red. The color follows the system theme color by default. |

**Returns**

| Type| Description|
| -- | -- |
| .data[0].u32 | Scroll bar color, in 0xARGB format, for example, **0xFFFF0000** indicates red. The color follows the system theme color by default. |

## NODE_TEXT_EDITOR_BAR_STATE

```c
NODE_TEXT_EDITOR_BAR_STATE = 22003
```

Scroll bar state of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Scroll bar state. The parameter type is [ArkUI_BarState](capi-scroll-h.md#arkui_barstate). The default value is **ARKUI_BAR_STATE_AUTO**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Scroll bar state. The parameter type is [ArkUI_BarState](capi-scroll-h.md#arkui_barstate).|

## NODE_TEXT_EDITOR_ENABLE_DATA_DETECTOR

```c
NODE_TEXT_EDITOR_ENABLE_DATA_DETECTOR = 22004
```

Whether to enable text entity recognition for the **TextEditor** component. When enabled, entities such as phone numbers, email addresses, and URLs in the text are automatically recognized and marked as interactive content. Used together with the **NODE_TEXT_EDITOR_DATA_DETECTOR_CONFIG** attribute, the recognition types and interaction behavior can be customized. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable text entity recognition. The value **1** indicates to enable text entity recognition, and **0** indicates the opposite. The default value is **0**. It is recommended to set this attribute in scenarios where entity information in the text needs to be automatically recognized and highlighted. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether text entity recognition is enabled. **1** indicates enabled, and **0** indicates disabled. |

## NODE_TEXT_EDITOR_DATA_DETECTOR_CONFIG

```c
NODE_TEXT_EDITOR_DATA_DETECTOR_CONFIG = 22005
```

Text entity recognition configuration of the **TextEditor** component. When set, the recognition types and entity display styles can be configured, and whether to enable the long-press preview feature can be selected. This attribute is used together with the **NODE_TEXT_EDITOR_ENABLE_DATA_DETECTOR** attribute. This attribute can be set and reset as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute is as follows.<br>

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| .object | Text entity detection configuration. After it is set, you can specify the text entity types to be recognized (such as phone numbers, email addresses, and URLs) and the interaction behavior after recognition. This parameter is passed only after the text entity recognition feature is enabled (**NODE_TEXT_EDITOR_ENABLE_DATA_DETECTOR** is set to **1**) to customize the recognition types. When not passed, the system default recognition configuration is used. The parameter type is [ArkUI_TextDataDetectorConfig](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md). |

## NODE_TEXT_EDITOR_EDIT_MENU_OPTIONS

```c
NODE_TEXT_EDITOR_EDIT_MENU_OPTIONS = 22006
```

Extended menu options for the **TextEditor** component. This attribute can be set and reset as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute is as follows.<br>

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| .object | Extended menu options. After being set, you can customize the behavior of the default menu items or add custom option content. The parameter type is [ArkUI_TextEditMenuOptions](capi-arkui-nativemodule-arkui-texteditmenuoptions.md). |

## NODE_TEXT_EDITOR_PLACEHOLDER

```c
NODE_TEXT_EDITOR_PLACEHOLDER = 22007
```

Placeholder options when there is no input for the **TextEditor** component. This attribute can be set and reset as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute is as follows.<br>

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| .object | Placeholder options when there is no input. The parameter type is [ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md). When not passed, the editor does not display placeholder text when there is no input. |

## NODE_TEXT_EDITOR_STYLED_STRING_CONTROLLER

```c
NODE_TEXT_EDITOR_STYLED_STRING_CONTROLLER = 22008
```

Styled string controller of the **TextEditor** component. This attribute can be set as required through APIs. After it is set, the content, caret, selection, input style, and editing state in the **TextEditor** component can be managed through the controller.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute is as follows.<br>

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| .object | Styled string controller. The parameter type is [ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md).|

## NODE_TEXT_EDITOR_ENABLE_PREVIEW_TEXT

```c
NODE_TEXT_EDITOR_ENABLE_PREVIEW_TEXT = 22009
```

Whether to enable preview text for the **TextEditor** component. When enabled, the pinyin and stroke characters entered during the input method input process are displayed within the component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable preview text. The value **1** indicates to enable preview text, and **0** indicates the opposite. The default value is **1**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether preview text is enabled. The value **1** indicates preview text is enabled, and **0** indicates the opposite.|

## NODE_TEXT_EDITOR_LAYOUT_MANAGER

```c
NODE_TEXT_EDITOR_LAYOUT_MANAGER = 22010
```

**TextLayoutManager** of the **TextEditor** component. After it is obtained, the layout information of the text, such as the number of lines, line height, and content offset, can be queried through the layout manager. This attribute can be obtained as required through APIs.<br>
The format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is as follows.<br>

**Since**: 24

**Returns**

| Type| Description|
| -- | -- |
| .object | Layout manager, through which the layout information of the text can be queried. The parameter type is [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md). |

## NODE_TEXT_EDITOR_ENABLE_SELECTED_DATA_DETECTOR

```c
NODE_TEXT_EDITOR_ENABLE_SELECTED_DATA_DETECTOR = 22011
```

Whether to enable the AI menu for text selection and recognition of the TextEditor component, used to control whether the AI recognition menu is displayed when a special text entity is selected. This attribute can be set, reset, and obtained as required through APIs. When enabled, intelligent recognition and operation options can be provided based on the selected text content.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable the AI menu for text selection and recognition. The value **1** means to enable, and **0** means the opposite. The default value is **1**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the AI menu is enabled for text selection and recognition. **0** indicates disabled, and **1** indicates enabled. |

## NODE_TEXT_EDITOR_SELECTED_BACKGROUND_COLOR

```c
NODE_TEXT_EDITOR_SELECTED_BACKGROUND_COLOR = 22012
```

Background color of the selected content in the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| .data[0].u32 | Background color of the selected content, in 0xARGB format, for example, **0xFFFF0000** indicates red. The color follows the system theme color by default. |

**Returns**

| Type| Description|
| -- | -- |
| .data[0].u32 | Background color of the selected content, in 0xARGB format, for example, **0xFFFF0000** indicates red. The color follows the system theme color by default. |

## NODE_TEXT_EDITOR_ENABLE_KEYBOARD_ON_FOCUS

```c
NODE_TEXT_EDITOR_ENABLE_KEYBOARD_ON_FOCUS = 22013
```

Whether to enable the input method when the focus is obtained in a way other than by clicking in the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable the input method when the focus is obtained in a way other than clicking. The value **1** means to enable, and **0** means the opposite. The default value is **1**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the input method is enabled when the focus is obtained in a way other than clicking. The value **1** indicates the input method is enabled, and **0** indicates the input method is disabled.|

## NODE_TEXT_EDITOR_MAX_LENGTH

```c
NODE_TEXT_EDITOR_MAX_LENGTH = 22014
```

Maximum number of characters in the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Maximum number of characters allowed to be entered in the text editor. The value range is [0, +∞). Text input is blocked once this limit is exceeded. The input length is not limited when this parameter is set to **0**, a negative number, or not set. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Maximum number of characters allowed to be entered in the text editor. |

## NODE_TEXT_EDITOR_MAX_LINES

```c
NODE_TEXT_EDITOR_MAX_LINES = 22015
```

Maximum number of lines in the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Maximum number of lines in the text editor. The value range is (0, +∞). When set to 0, a negative number, or not set, the default value **UINT32_MAX** is used, which means no limit on the number of lines. It is recommended to set this parameter in scenarios where a fixed display height is required. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Maximum number of lines in the text editor. |

## NODE_TEXT_EDITOR_ENABLE_HAPTIC_FEEDBACK

```c
NODE_TEXT_EDITOR_ENABLE_HAPTIC_FEEDBACK = 22016
```

Whether to enable haptic feedback of the **TextEditor** component. When enabled, haptic feedback vibration responses are generated during interactive operations such as text drag and selection. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable haptic feedback in the text editor. The value **1** means to enable, and **0** means the opposite. The default value is **1**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether haptic feedback is enabled. The value **1** indicates haptic feedback is enabled, and **0** indicates the opposite. |

## NODE_TEXT_EDITOR_COPY_OPTIONS

```c
NODE_TEXT_EDITOR_COPY_OPTIONS = 22017
```

Copy options of the **TextEditor** component, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Copy options. The parameter type is [ArkUI_CopyOptions](capi-native-type-h.md#arkui_copyoptions). The default value is **ARKUI_COPY_OPTIONS_LOCAL_DEVICE**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Copy options. The parameter type is [ArkUI_CopyOptions](capi-native-type-h.md#arkui_copyoptions).|

## NODE_TEXT_EDITOR_KEYBOARD_APPEARANCE

```c
NODE_TEXT_EDITOR_KEYBOARD_APPEARANCE = 22018
```

Keyboard appearance of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Keyboard appearance. The parameter type is [ArkUI_KeyboardAppearance](capi-text-common-h.md#arkui_keyboardappearance). The default value is **ARKUI_KEYBOARD_APPEARANCE_NONE_IMMERSIVE**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Keyboard appearance currently set for the text editor. The parameter type is [ArkUI_KeyboardAppearance](capi-text-common-h.md#arkui_keyboardappearance). |

## NODE_TEXT_EDITOR_STOP_BACK_PRESS

```c
NODE_TEXT_EDITOR_STOP_BACK_PRESS = 22019
```

Whether the **TextEditor** component blocks the back key event from propagating to the upper layer. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to block the propagation of return events. The value **1** indicates to block, and **0** indicates the opposite. The default value is **0**. It is recommended to set this to **1** when the editor has unsaved content or when the back key needs to be intercepted to prevent accidental exit. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the propagation of return events is blocked. The value **1** indicates that the propagation of return events is blocked, and **0** indicates the opposite.|

## NODE_TEXT_EDITOR_ENABLE_AUTO_SPACING

```c
NODE_TEXT_EDITOR_ENABLE_AUTO_SPACING = 22020
```

Whether to enable automatic spacing for Chinese and Western characters in the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. It is applicable to editing scenarios with mixed Chinese and English content. When enabled, spacing is automatically added between Chinese and Western characters to improve the reading experience of mixed text.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable automatic spacing between Chinese and English characters. The value **1** indicates to enable, and **0** indicates the opposite. The default value is **0**. It is recommended to set this parameter to **1** in editing scenarios with mixed Chinese and English content to improve the reading experience of mixed text. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether automatic spacing is enabled between Chinese and English characters. The value **1** indicates automatic spacing is enabled, and **0** indicates the opposite.|

## NODE_TEXT_EDITOR_CUSTOM_KEYBOARD

```c
NODE_TEXT_EDITOR_CUSTOM_KEYBOARD = 22021
```

Custom keyboard of the **TextEditor** component. Pass this attribute when the system default keyboard needs to be replaced (for example, special input layouts such as a numeric keyboard or an emoji keyboard). When not passed, the system default keyboard is used. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| .object | Custom keyboard. The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md).|
| .value[0]?.i32 | Whether the custom keyboard supports content avoidance, that is, whether the page content automatically adjusts its position to avoid being covered by the keyboard when the keyboard is displayed. The value **0** indicates not supported, and **1** indicates supported. The default value is **0**. |

**Returns**

| Type| Description|
| -- | -- |
| .object | Custom keyboard. The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md).|
| .value[0].i32 | Whether the custom keyboard supports content avoidance, that is, whether the page content automatically adjusts its position to avoid being covered by the keyboard when the keyboard is displayed. The value **0** indicates not supported, and **1** indicates supported. |

## NODE_TEXT_EDITOR_BIND_SELECTION_MENU

```c
NODE_TEXT_EDITOR_BIND_SELECTION_MENU = 22022
```

Binds the custom text selection menu of the **TextEditor** component. This attribute can be set and reset as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute is as follows.<br>

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| .object | Custom text selection menu. When not passed, the system default text selection menu is used. The parameter type is [ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md). |

## NODE_TEXT_EDITOR_INCLUDE_FONT_PADDING

```c
NODE_TEXT_EDITOR_INCLUDE_FONT_PADDING = 22023
```

Whether to enable the anti-truncation spacing for the first and last lines of the **TextEditor** component. When enabled, spacing is added to the first and last lines to avoid text truncation. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to add spacing. The value **1** means to add spacing, and **0** means not to add spacing. The default value is **0**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether spacing is added. The value **1** means that spacing is added, and **0** means spacing is not added. |

## NODE_TEXT_EDITOR_FALLBACK_LINE_SPACING

```c
NODE_TEXT_EDITOR_FALLBACK_LINE_SPACING = 22024
```

Whether to enable line height adaptation of the **TextEditor** component. When multiple lines of text are overlaid, the line height can adapt based on the actual height of the text. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable line height adaptation. The value **1** means to enable, and **0** means the opposite. The default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether line height adaptation is enabled. The value **1** means line height adaptation is enabled, and **0** means the opposite.|

## NODE_TEXT_EDITOR_COMPRESS_LEADING_PUNCTUATION

```c
NODE_TEXT_EDITOR_COMPRESS_LEADING_PUNCTUATION = 22025
```

Whether to enable leading punctuation compression in the **TextEditor** component. When enabled, the punctuation at the beginning of a line reduces its occupied width to adjust the text layout alignment. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable leading punctuation compression. The value **1** means to enable, and **0** means the opposite. The default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether leading punctuation compression is enabled. The value **1** indicates that leading punctuation compression is enabled, and **0** indicates the opposite.|

## NODE_TEXT_EDITOR_SELECTED_DRAG_PREVIEW_STYLE

```c
NODE_TEXT_EDITOR_SELECTED_DRAG_PREVIEW_STYLE = 22026
```

Selected drag preview style of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| .object | Selected drag preview style. The parameter type is [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-textselecteddragpreviewstyle.md). Pass this parameter when you need to customize the preview effect when dragging selected text. When not passed, the system default drag preview style is used. |

**Returns**

| Type| Description|
| -- | -- |
| .object | Selected drag preview style. The parameter type is [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-textselecteddragpreviewstyle.md).|

## NODE_TEXT_EDITOR_SINGLE_LINE

```c
NODE_TEXT_EDITOR_SINGLE_LINE = 22027
```

Whether to enable the single-line mode of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. When enabled, the maximum number of lines set by the **NODE_TEXT_EDITOR_MAX_LINES** attribute no longer takes effect.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable the single-line mode. The value **1** means to enable, and **0** means the opposite. The default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the single-line mode is enabled. The value **1** indicates that the single-line mode is enabled, and **0** means the opposite.|

## NODE_TEXT_EDITOR_ORPHAN_CHAR_OPTIMIZATION

```c
NODE_TEXT_EDITOR_ORPHAN_CHAR_OPTIMIZATION = 22028
```

Whether to enable orphan character optimization during text layout in **TextEditor**. This attribute can be set, reset, and obtained as required through APIs. When enabled, line break positions are adjusted to avoid orphan characters as much as possible. It takes effect only when the [ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak) attribute is not set to **ARKUI_WORD_BREAK_BREAK_ALL**.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable orphan character optimization. The value **1** indicates to enable, and **0** indicates the opposite. The default value is **0**. This parameter takes effect only when the [ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak) attribute is not set to **ARKUI_WORD_BREAK_BREAK_ALL**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether orphan character optimization is enabled. The value **0** indicates disabled, and **1** indicates enabled. |

## NODE_TEXT_EDITOR_HORIZONTAL_SCROLLING

```c
NODE_TEXT_EDITOR_HORIZONTAL_SCROLLING = 22029
```

Whether to enable horizontal scrolling for the **TextEditor** component when the text width exceeds the content area width. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable horizontal scrolling. The value **1** means to enable, and **0** means the opposite. The default value is **0**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether horizontal scrolling is enabled. The value **1** means enabled, and **0** means the opposite. |

## NODE_TEXT_EDITOR_PUNCTUATION_OVERFLOW

```c
NODE_TEXT_EDITOR_PUNCTUATION_OVERFLOW = 22030
```

Whether to enable punctuation hanging at the end of a line for the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs.<br>
When enabled, a single punctuation mark at the end of a line overflows the layout width without wrapping, preventing the punctuation mark from wrapping to the beginning of the next line and thereby improving the text layout effect.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable punctuation hanging at the end of a line. The value **1** indicates to enable, and **0** indicates the opposite. The default value is **0**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether punctuation hanging at the end of a line is enabled. The value **1** means punctuation hanging is enabled, and **0** means the opposite. |