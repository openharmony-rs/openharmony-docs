# ArkUI_NodeAttributeType (Rich Text Component Attribute)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiangyuan6; @kangshihui-->
<!--Designer: @xiangyuan6; @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

```c
enum ArkUI_NodeAttributeType
```

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side for rich text components including **TextEditor**.

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
| .value[0].i32 | Type of the **Enter** key. The parameter type is [ArkUI_EnterKeyType](capi-native-type-h.md#arkui_enterkeytype). The default value is **ARKUI_ENTER_KEY_TYPE_NEW_LINE**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Type of the **Enter** key. The parameter type is [ArkUI_EnterKeyType](capi-native-type-h.md#arkui_enterkeytype).|

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
| .value[0].u32 | Caret color, in 0xARGB format. For example, **0xFFFF0000** indicates red.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Caret color, in 0xARGB format.|

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
| .data[0].u32 | Scroll bar color, in 0xARGB format.|

**Returns**

| Type| Description|
| -- | -- |
| .data[0].u32 | Scroll bar color, in 0xARGB format.|

## NODE_TEXT_EDITOR_BAR_STATE

```c
NODE_TEXT_EDITOR_BAR_STATE = 22003
```

Scroll bar display mode of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Scroll bar display mode of the text area. The parameter type is [ArkUI_BarState](capi-native-type-h.md#arkui_barstate). The default value is **ARKUI_BAR_STATE_AUTO**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Scroll bar display mode of the text area. The parameter type is [ArkUI_BarState](capi-native-type-h.md#arkui_barstate).|

## NODE_TEXT_EDITOR_ENABLE_DATA_DETECTOR

```c
NODE_TEXT_EDITOR_ENABLE_DATA_DETECTOR = 22004
```

Whether to enable text entity recognition for the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable text entity recognition. The value **1** indicates to enable text entity recognition, and **0** indicates the opposite. The default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether text entity recognition is enabled.|

## NODE_TEXT_EDITOR_DATA_DETECTOR_CONFIG

```c
NODE_TEXT_EDITOR_DATA_DETECTOR_CONFIG = 22005
```

Recognition configuration for the **TextEditor** component. This attribute can be set and reset as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute is as follows.<br>

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| .object | Recognition configuration. The parameter type is [ArkUI_TextDataDetectorConfig](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md).|

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
| .object | Extended menu options. The parameter type is [ArkUI_TextEditMenuOptions](capi-arkui-nativemodule-arkui-texteditmenuoptions.md).|

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
| .object | Placeholder options when there is no input. The parameter type is [ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md).|

## NODE_TEXT_EDITOR_STYLED_STRING_CONTROLLER

```c
NODE_TEXT_EDITOR_STYLED_STRING_CONTROLLER = 22008
```

Styled string controller of the **TextEditor** component. This attribute can be set as required through APIs.<br>
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

Whether to enable preview text for the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs.<br>
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

**TextLayoutManager** of the **TextEditor** component. This attribute can be obtained as required through APIs.<br>
The format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is as follows.<br>

**Since**: 24


**Returns**

| Type| Description|
| -- | -- |
| .object | Layout manager. The parameter type is [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md).|

## NODE_TEXT_EDITOR_ENABLE_SELECTED_DATA_DETECTOR

```c
NODE_TEXT_EDITOR_ENABLE_SELECTED_DATA_DETECTOR = 22011
```

Whether to enable the AI menu for text selection and recognition of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable the AI menu for text selection and recognition. The value **1** means to enable, and **0** means the opposite. The default value is **1**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the AI menu is enabled for text selection and recognition.|

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
| .data[0].u32 | Background color of the selected content, in 0xARGB format.|

**Returns**

| Type| Description|
| -- | -- |
| .data[0].u32 | Background color of the selected content, in 0xARGB format.|

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
| .value[0].i32 | Maximum number of characters.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Maximum number of characters.|

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
| .value[0].i32 | Maximum number of lines in the text editor.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Maximum number of lines in the text editor.|

## NODE_TEXT_EDITOR_ENABLE_HAPTIC_FEEDBACK

```c
NODE_TEXT_EDITOR_ENABLE_HAPTIC_FEEDBACK = 22016
```

Whether to enable haptic feedback of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable haptic feedback in the text editor. The value **1** means to enable, and **0** means the opposite. The default value is **1**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether haptic feedback is enabled. The value **1** indicates haptic feedback is enabled, and **0** indicates the opposite.|

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
| .value[0].i32 | Appearance of the keyboard. The parameter type is [ArkUI_KeyboardAppearance](capi-native-type-h.md#arkui_keyboardappearance). The default value is **ARKUI_KEYBOARD_APPEARANCE_NONE_IMMERSIVE**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Appearance of the keyboard. The parameter type is [ArkUI_KeyboardAppearance](capi-native-type-h.md#arkui_keyboardappearance).|

## NODE_TEXT_EDITOR_STOP_BACK_PRESS

```c
NODE_TEXT_EDITOR_STOP_BACK_PRESS = 22019
```

Whether the **TextEditor** component blocks the propagation of return events. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to block the propagation of return events. The value **1** indicates to block, and **0** indicates the opposite. The default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the propagation of return events is blocked. The value **1** indicates that the propagation of return events is blocked, and **0** indicates the opposite.|

## NODE_TEXT_EDITOR_ENABLE_AUTO_SPACING

```c
NODE_TEXT_EDITOR_ENABLE_AUTO_SPACING = 22020
```

Whether to enable automatic spacing for Chinese and Western characters in the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable automatic spacing. The value **1** means to enable, and **0** means the opposite. The default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether automatic spacing is enabled. The value **1** indicates automatic spacing is enabled, and **0** indicates the opposite.|

## NODE_TEXT_EDITOR_CUSTOM_KEYBOARD

```c
NODE_TEXT_EDITOR_CUSTOM_KEYBOARD = 22021
```

Custom keyboard of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| .object | Custom keyboard. The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md).|
| .value[0]?.i32 | Whether the custom keyboard supports avoidance. The value **0** indicates no, and the value **1** indicates yes. The default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .object | Custom keyboard. The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md).|
| .value[0].i32 | Whether the custom keyboard supports avoidance. The value **0** indicates no, and the value **1** indicates yes.|

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
| .object | Text selection menu. The parameter type is [ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md).|

## NODE_TEXT_EDITOR_INCLUDE_FONT_PADDING

```c
NODE_TEXT_EDITOR_INCLUDE_FONT_PADDING = 22023
```

Whether to add spacing to the first and last lines of the **TextEditor** component to prevent text truncation. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to add spacing. The value **1** means to add spacing, and **0** means not to add spacing. The default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether spacing is added. The value **1** means that spacing is added, and **0** means spacing is not added.|

## NODE_TEXT_EDITOR_FALLBACK_LINE_SPACING

```c
NODE_TEXT_EDITOR_FALLBACK_LINE_SPACING = 22024
```

Whether to enable line height adaptation of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs.<br>
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

Whether to enable punctuation compression for the beginning of a line in the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable punctuation compression. The value **1** means to enable, and **0** means the opposite. The default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether punctuation compression is enabled. The value **1** indicates that punctuation compression is enabled, and **0** indicates the opposite.|

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
| .object | Selected drag preview style. The parameter type is [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-textselecteddragpreviewstyle.md).|

**Returns**

| Type| Description|
| -- | -- |
| .object | Selected drag preview style. The parameter type is [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-textselecteddragpreviewstyle.md).|

## NODE_TEXT_EDITOR_SINGLE_LINE

```c
NODE_TEXT_EDITOR_SINGLE_LINE = 22027
```

Whether to enable the single-line mode of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs.<br>
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
