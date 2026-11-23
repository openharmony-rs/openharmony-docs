# ArkUI_NodeAttributeType (Rich Text Component Attribute)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiangyuan6; @carnivore233-->
<!--Designer: @xiangyuan6; @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=49817ad6d3bdeb32b10cdb1744df526125ae30ce translatedAt=2026-11-18T08:49:54.088Z pushedAt=2026-11-19T03:43:01.296Z nl=1 -->

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

## NODE_TEXT_EDITOR_TYPE

```c
NODE_TEXT_EDITOR_TYPE = 22031
```

Text editor type of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| .value[0].i32 | Text editor type. The parameter type is [OH_ArkUI_TextEditorType](capi-rich-editor-h.md#oh_arkui_texteditortype). The default value is **OH_ARKUI_TEXT_EDITOR_TYPE_NORMAL**. |

**Returns**

| Type | Description |
| -- | -- |
| .value[0].i32 | Text editor type. The parameter type is [OH_ArkUI_TextEditorType](capi-rich-editor-h.md#oh_arkui_texteditortype). |

## NODE_TEXT_EDITOR_SHOW_PASSWORD_ICON

```c
NODE_TEXT_EDITOR_SHOW_PASSWORD_ICON = 22032
```

Whether to display the password icon at the end of the text in password input mode. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| .value[0].i32 | Whether to display the password icon at the end of the text. The value **true** indicates to display the password icon, and **false** indicates the opposite. |

**Returns**

| Type | Description |
| -- | -- |
| .value[0].i32 | Whether the password icon is displayed at the end of the text. The value **1** indicates the password icon is displayed, and **0** indicates the opposite. |

## NODE_TEXT_EDITOR_ENABLE_AUTO_FILL

```c
NODE_TEXT_EDITOR_ENABLE_AUTO_FILL = 22034
```

Whether to enable autofill for the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0


**Parameters**

| Name | Description |
| -- | -- |
| .value[0].i32 | Whether to enable autofill. The default value is **0**. **1** indicates to enable, and **0** indicates to disable. |

**Returns**

| Type | Description |
| -- | -- |
| .value[0].i32 | Whether autofill is enabled. The value **1** means autofill is enabled, and **0** means the opposite. |

## NODE_TEXT_EDITOR_CONTENT_TYPE

```c
NODE_TEXT_EDITOR_CONTENT_TYPE = 22035
```

Autofill type of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0


**Parameters**

| Name | Description |
| -- | -- |
| .value[0].i32 | Autofill type. The parameter type is [ArkUI_TextInputContentType](capi-text-input-h.md#arkui_textinputcontenttype), used to specify the content type in autofill scenarios. For specific enumerated values and application scenarios, see [ArkUI_TextInputContentType](capi-text-input-h.md#arkui_textinputcontenttype). |

**Returns**

| Type | Description |
| -- | -- |
| .value[0].i32 | Autofill type. The parameter type is [ArkUI_TextInputContentType](capi-text-input-h.md#arkui_textinputcontenttype), used to determine the autofilled content type. |

## NODE_TEXT_EDITOR_PASSWORD_RULES

```c
NODE_TEXT_EDITOR_PASSWORD_RULES = 22036
```

Rules for generating passwords. When autofill is used, these rules are transparently transmitted to Password Vault for generating a new password. This attribute is set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0


**Parameters**

| Name | Description |
| -- | -- |
| .string | Rules for generating passwords, which are transparently passed to the password vault to control new password generation when autofill is triggered. |

**Returns**

| Type | Description |
| -- | -- |
| .string | Rules for generating passwords. |

## NODE_TEXT_EDITOR_ENABLE_FILL_ANIMATION

```c
NODE_TEXT_EDITOR_ENABLE_FILL_ANIMATION  = 22037
```

Whether to enable the autofill animation of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0


**Parameters**

| Name | Description |
| -- | -- |
| .value[0].i32 | Whether to enable the autofill animation. The value **1** means to enable the autofill animation, and **0** means the opposite. The default value is **1**. |

**Returns**

| Type | Description |
| -- | -- |
| .value[0].i32 | Whether the autofill animation is enabled. The value **1** means the autofill animation is enabled, and **0** means the opposite. |

## NODE_TEXT_EDITOR_SHOW_UNDERLINE

```c
NODE_TEXT_EDITOR_SHOW_UNDERLINE = 22038
```

Whether to display the underline in the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0


**Parameters**

| Name | Description |
| -- | -- |
| .value[0].i32 | Whether to display the underline. The value **1** indicates to display, and **0** indicates the opposite. The default value is **0**. |

**Returns**

| Type | Description |
| -- | -- |
| .value[0].i32 | Whether the underline is displayed. The value **1** indicates the underline is displayed, and **0** indicates the opposite. |

## NODE_TEXT_EDITOR_UNDERLINE_COLOR

```c
NODE_TEXT_EDITOR_UNDERLINE_COLOR = 22039
```

Underline color, which can be set when the underline is enabled. This attribute can be set, reset, and obtained as required through APIs.<br>
This attribute takes effect only after the **NODE_TEXT_EDITOR_SHOW_UNDERLINE** attribute is set to **1** to enable the underline.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0


**Parameters**

| Name | Description |
| -- | -- |
| .value[0].u32 | Color of the underline applied to the text being typed in, in 0xARGB format. |
| .value[1].u32 | Color of the underline applied to the text in the normal state, in 0xARGB format. |
| .value[2].u32 | Color of the underline applied to the text when an error is detected, in 0xARGB format. |
| .value[3].u32 | Color of the underline applied to the text when the underline is disabled, in 0xARGB format. |

**Returns**

| Type | Description |
| -- | -- |
| .value[0].u32 | Color of the underline applied to the text being typed in, in 0xARGB format. |
| .value[1].u32 | Color of the underline applied to the text in the normal state, in 0xARGB format. |
| .value[2].u32 | Color of the underline applied to the text when an error is detected, in 0xARGB format. |
| .value[3].u32 | Color of the underline applied to the text when the underline is disabled, in 0xARGB format. |

## NODE_TEXT_EDITOR_CARET_STYLE

```c
NODE_TEXT_EDITOR_CARET_STYLE = 22040
```

Caret width of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0


**Parameters**

| Name | Description |
| -- | -- |
| .value[0].f32 | Caret width, in vp. |

**Returns**

| Type | Description |
| -- | -- |
| .value[0].f32 | Caret width, in vp. |

## NODE_TEXT_EDITOR_SELECT_ALL

```c
NODE_TEXT_EDITOR_SELECT_ALL = 22041
```

Whether to select all text in the initial state for the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs.<br>
Select-all is triggered only when the component gains focus for the first time and completes the layout phase. Select-all is not performed when the window regains focus.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0


**Parameters**

| Name | Description |
| -- | -- |
| .value[0].i32 | Whether to select all text. The default value is **0**. The value **1** means to select all text, and **0** means the opposite. |

**Returns**

| Type | Description |
| -- | -- |
| .value[0].i32 | Whether all text is selected. **1** means all text is selected, and **0** means the opposite. |

## NODE_TEXT_EDITOR_BLUR_ON_SUBMIT

```c
NODE_TEXT_EDITOR_BLUR_ON_SUBMIT = 22042
```

Whether the **TextEditor** component loses focus upon submission. This attribute can be set, reset, and obtained as required through APIs.<br>
This attribute takes effect only when **EnterKeyType** is set to **NEW_LINE** and the **Enter** key is pressed: when set to **1**, the keyboard is closed and the component loses focus, and no new line is inserted; when set to **0**, a new line is inserted and the component does not lose focus.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0


**Parameters**

| Name | Description |
| -- | -- |
| .value[0].i32 | Whether to lose focus upon submission. The default value is **0**. The value **1** indicates to lose focus, and **0** indicates the opposite. |

**Returns**

| Type | Description |
| -- | -- |
| .value[0].i32 | Whether focus is lost upon submission. The value **1** indicates focus is lost, and **0** indicates the opposite. |

## NODE_TEXT_EDITOR_CONTENT_RECT

```c
NODE_TEXT_EDITOR_CONTENT_RECT = 22043
```

Position and size of the content editing area of the **TextEditor** component. This attribute only can be obtained through APIs as required.<br>
The format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is as follows.<br>

**Since**: 26.1.0


**Returns**

| Type | Description |
| -- | -- |
| .value[0].f32 | X-axis offset of the content editing area, in px. |
| .value[1].f32 | Y-axis offset of the content editing area, in px. |
| .value[2].f32 | Width of the content editing area, in px. |
| .value[3].f32 | Height of the content editing area, in px. |

## NODE_TEXT_EDITOR_SELECTION_MENU_HIDDEN

```c
NODE_TEXT_EDITOR_SELECTION_MENU_HIDDEN = 22044
```

Whether to hide the selection menu of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs.<br>
When set to **1**, the selection menu is not displayed on long press, double-click, or right-click, but the selection handles are not affected.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0


**Parameters**

| Name | Description |
| -- | -- |
| .value[0].i32 | Whether to hide the selection menu. The default value is **0**. The value **1** indicates to hide, and **0** indicates the opposite. |

**Returns**

| Type | Description |
| -- | -- |
| .value[0].i32 | Whether the selection menu is hidden. The value **1** indicates the selection menu is hidden, and **0** indicates the opposite. |

## NODE_TEXT_EDITOR_ENABLE_SKIP_PREVIEW_LONG_PRESS

```c
NODE_TEXT_EDITOR_ENABLE_SKIP_PREVIEW_LONG_PRESS = 22045
```

Whether the **TextEditor** component skips the state for long-pressing to preview and directly enters the editing state. This attribute can be set, reset, and obtained as required through APIs.<br>
When set to **1**, the component directly enters the editing state (the keyboard pops up and the caret blinks) after a long press, skipping the preview state. The double-click behavior is not affected.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0


**Parameters**

| Name | Description |
| -- | -- |
| .value[0].i32 | Whether to skip the state for long-pressing to preview. The default value is **0**. The value **1** indicates to skip, and **0** indicates the opposite. |

**Returns**

| Type | Description |
| -- | -- |
| .value[0].i32 | Whether the state for long-pressing to preview is skipped. The value **1** indicates the state is skipped, and **0** indicates the opposite. |

## NODE_TEXT_EDITOR_CANCEL_BUTTON

```c
NODE_TEXT_EDITOR_CANCEL_BUTTON = 22046
```

Cancel button style of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0


**Parameters**

| Name | Description |
| -- | -- |
| .value[0].i32 | Button style. The parameter type is [ArkUI_CancelButtonStyle](capi-text-input-h.md#arkui_cancelbuttonstyle). The default value is **ARKUI_CANCELBUTTON_STYLE_INPUT**, which indicates the cancel button input style. |
| .value[1]?.f32 | Icon size, in vp. Value range: [0, +∞). When a negative value is passed, the setting does not take effect. When not passed, the default icon size of the system is used. |
| .value[2]?.u32 | Button icon color, in 0xARGB format, for example, **0xFFFF0000** indicates red. When not passed, the default icon color of the system is used. |
| ?.string | Button icon address. The value is the local address of an image, for example, **/pages/icon.png**. When not passed, the default clear icon of the system is used. |

**Returns**

| Type | Description |
| -- | -- |
| .value[0].i32 | Button style. The parameter type is [ArkUI_CancelButtonStyle](capi-text-input-h.md#arkui_cancelbuttonstyle). |
| .value[1].f32 | Button icon size, in vp. |
| .value[2].u32 | Button icon color, in 0xARGB format. |
| .string | Button icon address. |

## NODE_TEXT_EDITOR_SHOW_COUNTER

```c
NODE_TEXT_EDITOR_SHOW_COUNTER = 22047
```

Whether to show a counter and its style when the number of characters entered in the **TextEditor** component exceeds a threshold. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| .value[0].i32 | Whether to show a counter. The value **1** to show; **0** otherwise. |
| .value[1]?.f32 | Percentage of the number of characters that can be entered to the maximum number of characters allowed. When the percentage exceeds this value, the counter is shown. The value range is [1, 100]. If the value is a decimal, it is rounded down. If the value is out of the range, the attribute setting does not take effect. The default value is **-1**, indicating the counter is always shown. |
| .value[2]?.i32 | Whether to highlight the border when the number of entered characters exceeds the maximum. The value **1** means to highlight; **0** otherwise. The default value is **1**. |
| .object | Counter configuration. The configuration attributes are the color of the counter when the number of characters entered in the text box does not reach the maximum and the color of the counter when the number of characters entered in the text box exceeds the maximum. The parameter type is [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-textshowcounterconfig.md). |

**Returns**

| Type | Description |
| -- | -- |
| .value[0].i32 | Whether the counter is shown. The value **1** means the counter is shown, and **0** means the opposite. |
| .value[1].f32 | Percentage of the number of characters that can be entered to the maximum number of characters allowed. When the percentage exceeds this value, the counter is shown. The value range is [1, 100]. |
| .value[2].i32 | Whether the border is highlighted when the number of entered characters exceeds the maximum. The value **1** indicates that the border is highlighted; **0** otherwise. |
| .object | Counter configuration. The configuration attributes are the color of the counter when the number of characters entered in the text box does not reach the maximum and the color of the counter when the number of characters entered in the text box exceeds the maximum. The parameter type is [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-textshowcounterconfig.md). |

## NODE_TEXT_EDITOR_INPUT_FILTER

```c
NODE_TEXT_EDITOR_INPUT_FILTER = 22048
```

Input filter regular expression of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs.<br>
This attribute takes effect only in **StyledString** mode (including single-line and multi-line modes), that is, the mode after [NODE_TEXT_EDITOR_STYLED_STRING_CONTROLLER](#node_text_editor_styled_string_controller) is set.<br>
When this attribute and [NODE_TEXT_EDITOR_MAX_LENGTH](#node_text_editor_max_length) are set at the same time, the filtering priority is as follows: **NODE_TEXT_EDITOR_INPUT_FILTER** is used to perform filtering first, and then **NODE_TEXT_EDITOR_MAX_LENGTH** is used to perform truncation.<br>
When the regular expression changes, the existing content is silently re-filtered (consistent with the **TextInput** behavior).<br>
Non-character content (**ImageSpan**/**SymbolSpan**/**BuilderSpan**) is treated as the \uFFFC character during regular expression matching.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0


**Parameters**

| Name | Description |
| -- | -- |
| .string | Regular expression, used to filter user input. Input matching the expression is allowed to be displayed, and input not matching is filtered out. Set this parameter when it is necessary to restrict users to inputting only characters in a specific format. For example, "[a-zA-Z]" allows only letters, and "[0-9]" allows only digits. An empty string is equivalent to not setting the filter. |

**Returns**

| Type | Description |
| -- | -- |
| .string | String of the currently set input filter regular expression. |
