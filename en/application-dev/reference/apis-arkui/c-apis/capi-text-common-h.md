# text_common.h

## Overview

Defines common text enumerations and APIs, covering text alignment, decoration line styles, copy and paste, overflow handling, line break policies, and menu customization. It is applicable to scenarios such as text boxes and text display, helping you flexibly control text styles and interaction behavior while reducing development complexity.

**Library**: libace_ndk.z.so

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) | ArkUI_StyledString_Descriptor | Defines the styled string descriptor object supported by the text component, which is used for style setting and management of text content. It applies to scenarios such as rich text display and style customization. |
| [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-showcounterconfig.md) | ArkUI_ShowCounterConfig | Defines the counter configuration of a text input box for managing character counting. It applies to scenarios where character count limits and real-time prompts are required for user input, helping users track input progress and prevent exceeding the character limit. |
| [ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md) | ArkUI_TextContentBaseController | Defines a text content base controller, providing content control capabilities for text components and supporting operations such as obtaining, setting, and updating text content. It is suitable for scenarios that require dynamic content management and real-time control of text components, helping you manage text display content more flexibly. |
| [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md) | ArkUI_TextMenuItem | Defines a text menu item, used to represent a single menu item in a text selection menu. This struct supports setting attributes such as the title, icon, and enabled state of the menu item. It is applicable to scenarios where you need to customize text selection menu content and menu item extension, helping you flexibly customize the text selection menu. |
| [ArkUI_TextMenuItemArray](capi-arkui-nativemodule-arkui-textmenuitemarray.md) | ArkUI_TextMenuItemArray | Defines an array of text menu items, which carries data of multiple text menu items in a text selection menu or context menu scenario. |
| [ArkUI_TextEditMenuOptions](capi-arkui-nativemodule-arkui-texteditmenuoptions.md) | ArkUI_TextEditMenuOptions | Defines editable text menu extension options, used to extend the functionality of the text editing menu. It is applicable to scenarios where you need to customize text editing menu operations. |
| [ArkUI_TextSelectionMenuOptions](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md) | ArkUI_TextSelectionMenuOptions | Defines the options of a custom text selection menu, supporting custom configuration of menu content, styles, and behavior. It is applicable to scenarios where the text selection menu interaction needs to be customized. |
| [OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md) | OH_ArkUI_DecorationStyleOptions | Defines decoration style options, which are used to add decorative line effects to text. You can set the type (such as underline, strikethrough, and overline), style (such as solid, dashed, and wavy), and color of the decorative line. Typical use cases include adding an underline to link text, adding a strikethrough to deleted content, and adding an overline to important text. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_TextAlignment](#arkui_textalignment) | ArkUI_TextAlignment | Enumerates text horizontal alignment styles. |
| [ArkUI_TextVerticalAlignment](#arkui_textverticalalignment) | ArkUI_TextVerticalAlignment | Enumerates text vertical alignment styles. |
| [ArkUI_TextContentAlign](#arkui_textcontentalign) | ArkUI_TextContentAlign | Enumerates vertical alignment styles in the text content area. |
| [ArkUI_TextDirection](#arkui_textdirection) | ArkUI_TextDirection | Enumerates text layout directions. |
| [ArkUI_EnterKeyType](#arkui_enterkeytype) | ArkUI_EnterKeyType | Enumerates the types of the **Enter** key for single-line text input. |
| [ArkUI_TextDecorationType](#arkui_textdecorationtype) | ArkUI_TextDecorationType | Enumerates text decoration types. |
| [ArkUI_TextDecorationStyle](#arkui_textdecorationstyle) | ArkUI_TextDecorationStyle | Enumerates text decoration styles. |
| [ArkUI_TextCase](#arkui_textcase) | ArkUI_TextCase | Enumerates text cases. |
| [ArkUI_TextCopyOptions](#arkui_textcopyoptions) | ArkUI_TextCopyOptions | Enumerates copy options, which define whether copy and paste is allowed for text content. |
| [ArkUI_TextOverflow](#arkui_textoverflow) | ArkUI_TextOverflow | Enumerates the display modes when the text is too long. |
| [ArkUI_WordBreak](#arkui_wordbreak) | ArkUI_WordBreak | Enumerates word break rules. |
| [ArkUI_EllipsisMode](#arkui_ellipsismode) | ArkUI_EllipsisMode | Enumerates ellipsis positions. |
| [ArkUI_KeyboardAppearance](#arkui_keyboardappearance) | ArkUI_KeyboardAppearance | Enumerates the appearance of the keyboard when the text box is focused. |
| [ArkUI_TextMenuItemId](#arkui_textmenuitemid) | ArkUI_TextMenuItemId | Enumerates the IDs of text menu items. |
| [OH_ArkUI_LineBreakStrategy](#oh_arkui_linebreakstrategy) | OH_ArkUI_LineBreakStrategy | Enumerates line break policies. |
| [OH_ArkUI_StrokeJoinStyle](#oh_arkui_strokejoinstyle) | OH_ArkUI_StrokeJoinStyle | Enumerates the join styles of a text stroke. |
| [ArkUI_TextSpanType](#arkui_textspantype) | ArkUI_TextSpanType | Enumerates the text span type. |
| [ArkUI_TextResponseType](#arkui_textresponsetype) | ArkUI_TextResponseType | Enumerates the response types of a custom text selection menu. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*ArkUI_TextCreateMenuCallback)(ArkUI_TextMenuItemArray* items, void* userData)](#arkui_textcreatemenucallback) | ArkUI_TextCreateMenuCallback |  |
| [typedef void (\*ArkUI_TextPrepareMenuCallback)(ArkUI_TextMenuItemArray* items, void* userData)](#arkui_textpreparemenucallback) | ArkUI_TextPrepareMenuCallback |  |
| [typedef bool (\*ArkUI_TextMenuItemClickCallback)(const ArkUI_TextMenuItem* item, int32_t start, int32_t end, void* userData)](#arkui_textmenuitemclickcallback) | ArkUI_TextMenuItemClickCallback |  |
| [ArkUI_ShowCounterConfig* OH_ArkUI_ShowCounterConfig_Create()](#oh_arkui_showcounterconfig_create) | - | Creates a text input counter configuration object. When this object is no longer used, call [OH_ArkUI_ShowCounterConfig_Dispose](capi-text-common-h.md#oh_arkui_showcounterconfig_dispose) to dispose of it. |
| [void OH_ArkUI_ShowCounterConfig_Dispose(ArkUI_ShowCounterConfig* config)](#oh_arkui_showcounterconfig_dispose) | - | Disposes of the text input counter configuration object created by [OH_ArkUI_ShowCounterConfig_Create](capi-text-common-h.md#oh_arkui_showcounterconfig_create). |
| [void OH_ArkUI_ShowCounterConfig_SetCounterTextColor(ArkUI_ShowCounterConfig* config, uint32_t color)](#oh_arkui_showcounterconfig_setcountertextcolor) | - | Sets the text color of the counter when the text input has not reached the maximum character limit. If this API is not called, the default color is **0x66182431**, displayed as gray. |
| [void OH_ArkUI_ShowCounterConfig_SetCounterTextOverflowColor(ArkUI_ShowCounterConfig* config, uint32_t color)](#oh_arkui_showcounterconfig_setcountertextoverflowcolor) | - | Sets the text color of the counter when the text input exceeds the maximum character limit. If this API is not called, the default color is **0x99FA2A2D**, displayed as red. |
| [uint32_t OH_ArkUI_ShowCounterConfig_GetCounterTextColor(ArkUI_ShowCounterConfig* config)](#oh_arkui_showcounterconfig_getcountertextcolor) | - | Obtains the text color of the counter when the text input has not reached the maximum character limit. |
| [uint32_t OH_ArkUI_ShowCounterConfig_GetCounterTextOverflowColor(ArkUI_ShowCounterConfig* config)](#oh_arkui_showcounterconfig_getcountertextoverflowcolor) | - | Obtains the text color of the counter when the text input exceeds the maximum character limit. |
| [ArkUI_TextMenuItem* OH_ArkUI_TextMenuItem_Create()](#oh_arkui_textmenuitem_create) | - | Creates a text menu item object for customizing the text selection menu or extending the system menu. It is applicable when custom menu items need to be added, such as sharing to a specific platform or performing custom editing operations. When this object is no longer used, call [OH_ArkUI_TextMenuItem_Dispose](capi-text-common-h.md#oh_arkui_textmenuitem_dispose) to dispose of it. |
| [void OH_ArkUI_TextMenuItem_Dispose(ArkUI_TextMenuItem* textMenuItem)](#oh_arkui_textmenuitem_dispose) | - | Disposes of the text menu item object created by [OH_ArkUI_TextMenuItem_Create](capi-text-common-h.md#oh_arkui_textmenuitem_create). |
| [ArkUI_TextEditMenuOptions* OH_ArkUI_TextEditMenuOptions_Create()](#oh_arkui_texteditmenuoptions_create) | - | Creates a text menu extension object for extending the text editing menu functionality. It is applicable when custom menu items need to be added to the text editing component, such as inserting special characters or performing quick formatting. When this object is no longer used, call [OH_ArkUI_TextEditMenuOptions_Dispose](capi-text-common-h.md#oh_arkui_texteditmenuoptions_dispose) to dispose of it. |
| [void OH_ArkUI_TextEditMenuOptions_Dispose(ArkUI_TextEditMenuOptions* editMenuOptions)](#oh_arkui_texteditmenuoptions_dispose) | - | Disposes of the text menu extension object created by [OH_ArkUI_TextEditMenuOptions_Create](capi-text-common-h.md#oh_arkui_texteditmenuoptions_create). |
| [ArkUI_TextSelectionMenuOptions* OH_ArkUI_TextSelectionMenuOptions_Create()](#oh_arkui_textselectionmenuoptions_create) | - | Creates a custom text selection menu object for configuring the content and behavior of the text selection menu. It is applicable when the text selection menu needs to be fully customized, such as replacing the default menu and adding application-specific operations. When this object is no longer used, call [OH_ArkUI_TextSelectionMenuOptions_Dispose](capi-text-common-h.md#oh_arkui_textselectionmenuoptions_dispose) to dispose of it. |
| [void OH_ArkUI_TextSelectionMenuOptions_Dispose(ArkUI_TextSelectionMenuOptions* selectionMenuOptions)](#oh_arkui_textselectionmenuoptions_dispose) | - | Disposes of the custom text selection menu object created by [OH_ArkUI_TextSelectionMenuOptions_Create](capi-text-common-h.md#oh_arkui_textselectionmenuoptions_create). |
| [ArkUI_TextContentBaseController* OH_ArkUI_TextContentBaseController_Create()](#oh_arkui_textcontentbasecontroller_create) | - | Creates a text content base controller object. When this object is no longer used, call [OH_ArkUI_TextContentBaseController_Dispose](capi-text-common-h.md#oh_arkui_textcontentbasecontroller_dispose) to dispose of it. |
| [void OH_ArkUI_TextContentBaseController_Dispose(ArkUI_TextContentBaseController* controller)](#oh_arkui_textcontentbasecontroller_dispose) | - | Disposes of the text content base controller object created by [OH_ArkUI_TextContentBaseController_Create](capi-text-common-h.md#oh_arkui_textcontentbasecontroller_create). |
| [void OH_ArkUI_TextContentBaseController_DeleteBackward(ArkUI_TextContentBaseController* controller)](#oh_arkui_textcontentbasecontroller_deletebackward) | - | Deletes the character before the cursor in editing state; deletes the last character of the text box component in other states. |
| [void OH_ArkUI_TextContentBaseController_ScrollToVisible(ArkUI_TextContentBaseController *controller, int32_t start, int32_t end)](#oh_arkui_textcontentbasecontroller_scrolltovisible) | - | Passes the start and end indexes to the bound text box component, and scrolls the text within the range to the visible area. |
| [OH_ArkUI_DecorationStyleOptions* OH_ArkUI_DecorationStyleOptions_Create()](#oh_arkui_decorationstyleoptions_create) | - | Creates a decoration style object for setting the type, style, and color of text decorative lines. It is applicable when decoration effects such as underlines or strikethroughs need to be added to text, for example, in rich text editors, hyperlink text, or price tags. When this object is no longer used, call [OH_ArkUI_DecorationStyleOptions_Destroy](capi-text-common-h.md#oh_arkui_decorationstyleoptions_destroy) to destroy it. |
| [void OH_ArkUI_DecorationStyleOptions_Destroy(OH_ArkUI_DecorationStyleOptions* options)](#oh_arkui_decorationstyleoptions_destroy) | - | Destroys the decoration style object created by [OH_ArkUI_DecorationStyleOptions_Create](capi-text-common-h.md#oh_arkui_decorationstyleoptions_create). |

## Enum type description

### ArkUI_TextAlignment

```c
enum ArkUI_TextAlignment
```

**Description**

Enumerates text horizontal alignment styles.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_TEXT_ALIGNMENT_START = 0 | Aligned with the start. |
| ARKUI_TEXT_ALIGNMENT_CENTER | Horizontally centered. |
| ARKUI_TEXT_ALIGNMENT_END | Aligned with the end. |
| ARKUI_TEXT_ALIGNMENT_JUSTIFY | Aligned with both margins. |
| ARKUI_TEXT_ALIGNMENT_LEFT_TO_RIGHT = 4 |  |
| ARKUI_TEXT_ALIGNMENT_RIGHT_TO_LEFT = 5 |  |

### ArkUI_TextVerticalAlignment

```c
enum ArkUI_TextVerticalAlignment
```

**Description**

Enumerates text vertical alignment styles.

**Since**: 20

| Enum item | Description |
| -- | -- |
| ARKUI_TEXT_VERTICAL_ALIGNMENT_BASELINE = 0 | Aligned to the baseline. |
| ARKUI_TEXT_VERTICAL_ALIGNMENT_BOTTOM | Bottom aligned. |
| ARKUI_TEXT_VERTICAL_ALIGNMENT_CENTER | Center aligned. |
| ARKUI_TEXT_VERTICAL_ALIGNMENT_TOP | Top aligned. |

### ArkUI_TextContentAlign

```c
enum ArkUI_TextContentAlign
```

**Description**

Enumerates vertical alignment styles in the text content area.

**Since**: 21

| Enum item | Description |
| -- | -- |
| ARKUI_TEXT_CONTENT_ALIGN_TOP = 0 | Top aligned. |
| ARKUI_TEXT_CONTENT_ALIGN_CENTER = 1 | Center aligned. |
| ARKUI_TEXT_CONTENT_ALIGN_BOTTOM = 2 | Bottom aligned. |

### ArkUI_TextDirection

```c
enum ArkUI_TextDirection
```

**Description**

Enumerates text layout directions.

**Since**: 23

| Enum item | Description |
| -- | -- |
| ARKUI_TEXT_DIRECTION_LTR = 0 | The text direction is left to right. |
| ARKUI_TEXT_DIRECTION_RTL = 1 | The text direction is right to left. |
| ARKUI_TEXT_DIRECTION_DEFAULT = 2 | The text direction follows the component layout. |
| ARKUI_TEXT_DIRECTION_AUTO = 3 | The text direction follows the actual text. |

### ArkUI_EnterKeyType

```c
enum ArkUI_EnterKeyType
```

**Description**

Enumerates the types of the **Enter** key for single-line text input.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_ENTER_KEY_TYPE_GO = 2 | The Enter key is labeled "Go." |
| ARKUI_ENTER_KEY_TYPE_SEARCH = 3 | The Enter key is labeled "Search." |
| ARKUI_ENTER_KEY_TYPE_SEND | The Enter key is labeled "Send." |
| ARKUI_ENTER_KEY_TYPE_NEXT | The Enter key is labeled "Next." |
| ARKUI_ENTER_KEY_TYPE_DONE | The Enter key is labeled "Done." |
| ARKUI_ENTER_KEY_TYPE_PREVIOUS | The Enter key is labeled "Previous." |
| ARKUI_ENTER_KEY_TYPE_NEW_LINE | The Enter key is labeled "New Line." |

### ArkUI_TextDecorationType

```c
enum ArkUI_TextDecorationType
```

**Description**

Enumerates text decoration types.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_TEXT_DECORATION_TYPE_NONE = 0 | No text decoration. |
| ARKUI_TEXT_DECORATION_TYPE_UNDERLINE | Line under the text. |
| ARKUI_TEXT_DECORATION_TYPE_OVERLINE | Line over the text. |
| ARKUI_TEXT_DECORATION_TYPE_LINE_THROUGH | Line through the text. |

### ArkUI_TextDecorationStyle

```c
enum ArkUI_TextDecorationStyle
```

**Description**

Enumerates text decoration styles.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_TEXT_DECORATION_STYLE_SOLID = 0 | Single solid line. |
| ARKUI_TEXT_DECORATION_STYLE_DOUBLE | Double solid line. |
| ARKUI_TEXT_DECORATION_STYLE_DOTTED | Dotted line. |
| ARKUI_TEXT_DECORATION_STYLE_DASHED | Dashed line. |
| ARKUI_TEXT_DECORATION_STYLE_WAVY | Wavy line. |

### ArkUI_TextCase

```c
enum ArkUI_TextCase
```

**Description**

Enumerates text cases.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_TEXT_CASE_NORMAL = 0 | The original case of the text is retained. |
| ARKUI_TEXT_CASE_LOWER | All letters in the text are in lowercase. |
| ARKUI_TEXT_CASE_UPPER | All letters in the text are in uppercase. |

### ArkUI_TextCopyOptions

```c
enum ArkUI_TextCopyOptions
```

**Description**

Enumerates copy options, which define whether copy and paste is allowed for text content.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_TEXT_COPY_OPTIONS_NONE = 0 | Copy is not allowed. |
| ARKUI_TEXT_COPY_OPTIONS_IN_APP | Intra-application copy is allowed. |
| ARKUI_TEXT_COPY_OPTIONS_LOCAL_DEVICE | Intra-device copy is allowed. |
| ARKUI_TEXT_COPY_OPTIONS_CROSS_DEVICE | Cross-device copy is allowed. |

### ArkUI_TextOverflow

```c
enum ArkUI_TextOverflow
```

**Description**

Enumerates the display modes when the text is too long.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_TEXT_OVERFLOW_NONE = 0 | Extra-long text is not clipped. |
| ARKUI_TEXT_OVERFLOW_CLIP | Extra-long text is clipped. |
| ARKUI_TEXT_OVERFLOW_ELLIPSIS | An ellipsis (...) is used to represent text overflow. |
| ARKUI_TEXT_OVERFLOW_MARQUEE | Text continuously scrolls when text overflow occurs. |

### ArkUI_WordBreak

```c
enum ArkUI_WordBreak
```

**Description**

Enumerates word break rules.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_WORD_BREAK_NORMAL = 0 | Word breaks can occur between any two characters for Chinese, Japanese, and Korean (CJK) text, but can occur only at a space character for non-CJK text (such as English). |
| ARKUI_WORD_BREAK_BREAK_ALL | Word breaks can occur between any two characters for non-CJK text. CJK text behavior is the same as for <b>NORMAL</b>. |
| ARKUI_WORD_BREAK_BREAK_WORD | This option has the same effect as <b>BREAK_ALL</b> for non-CJK text, except that if it preferentially wraps lines at appropriate characters (for example, spaces) whenever possible. CJK text behavior is the same as for <b>NORMAL</b>. |
| ARKUI_WORD_BREAK_HYPHENATION | Line breaks can occur between any two syllabic units for non-CJK text. CJK text behavior is the same as for <b>NORMAL</b>.<br>**Since**: 18 |

### ArkUI_EllipsisMode

```c
enum ArkUI_EllipsisMode
```

**Description**

Enumerates ellipsis positions.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_ELLIPSIS_MODE_START = 0 | An ellipsis is used at the start of the line of text. |
| ARKUI_ELLIPSIS_MODE_CENTER | An ellipsis is used at the center of the line of text. |
| ARKUI_ELLIPSIS_MODE_END | An ellipsis is used at the end of the line of text. |
| ARKUI_ELLIPSIS_MODE_MULTILINE_START | An ellipsis is used at the start of the line of text for multiline and single line.<br>**Since**: 24 |
| ARKUI_ELLIPSIS_MODE_MULTILINE_CENTER | An ellipsis is used at the center of the line of text for multiline and single line.<br>**Since**: 24 |

### ArkUI_KeyboardAppearance

```c
enum ArkUI_KeyboardAppearance
```

**Description**

Enumerates the appearance of the keyboard when the text box is focused.

**Since**: 15

| Enum item | Description |
| -- | -- |
| ARKUI_KEYBOARD_APPEARANCE_NONE_IMMERSIVE = 0 |  |
| ARKUI_KEYBOARD_APPEARANCE_IMMERSIVE = 1 |  |
| ARKUI_KEYBOARD_APPEARANCE_LIGHT_IMMERSIVE = 2 |  |
| ARKUI_KEYBOARD_APPEARANCE_DARK_IMMERSIVE = 3 |  |

### ArkUI_TextMenuItemId

```c
enum ArkUI_TextMenuItemId
```

**Description**

Enumerates the IDs of text menu items.

**Since**: 22

| Enum item | Description |
| -- | -- |
| ARKUI_TEXT_MENU_ITEM_ID_CUT = 0 | Indicates the TextMenuItemId to copy and delete the currently selected text. |
| ARKUI_TEXT_MENU_ITEM_ID_COPY = 1 | Indicates the TextMenuItemId to copy the currently selected text to the clipboard. |
| ARKUI_TEXT_MENU_ITEM_ID_PASTE = 2 | Indicates the TextMenuItemId to copy the current contents of the clipboard into the text view. |
| ARKUI_TEXT_MENU_ITEM_ID_SELECT_ALL = 3 | Indicates the TextMenuItemId to select all text in a text view. |
| ARKUI_TEXT_MENU_ITEM_ID_COLLABORATION_SERVICE = 4 | Indicates the TextMenuItemId for collaboration service menu items. |
| ARKUI_TEXT_MENU_ITEM_ID_CAMERA_INPUT = 5 | Indicates the TextMenuItemId to recognize the text in the picture and input it into the text view. |
| ARKUI_TEXT_MENU_ITEM_ID_AI_WRITER = 6 | Indicates the TextMenuItemId to help with text creation by invoking large models. |
| ARKUI_TEXT_MENU_ITEM_ID_TRANSLATE = 7 | Indicates the TextMenuItemId to translate the selected content. |
| ARKUI_TEXT_MENU_ITEM_ID_SEARCH = 8 | Indicates the TextMenuItemId to search the selected content. |
| ARKUI_TEXT_MENU_ITEM_ID_SHARE = 9 | Indicates the TextMenuItemId to share the selected content. |
| ARKUI_TEXT_MENU_ITEM_ID_URL = 10 | Indicates the TextMenuItemId to open url. |
| ARKUI_TEXT_MENU_ITEM_ID_EMAIL = 11 | Indicates the TextMenuItemId to open email. |
| ARKUI_TEXT_MENU_ITEM_ID_PHONE_NUMBER = 12 | Indicates the TextMenuItemId to call the phone number. |
| ARKUI_TEXT_MENU_ITEM_ID_ADDRESS = 13 | Indicates the TextMenuItemId to open map. |
| ARKUI_TEXT_MENU_ITEM_ID_DATA_TIME = 14 | Indicates the TextMenuItemId to open calendar. |
| ARKUI_TEXT_MENU_ITEM_ID_ASK_AI = 15 | Indicates the TextMenuItemId for asking AI. |
| ARKUI_TEXT_MENU_ITEM_ID_AUTO_FILL = 16 |  |
| ARKUI_TEXT_MENU_ITEM_ID_PASSWORD_VAULT = 17 |  |
| ARKUI_TEXT_MENU_ITEM_ID_APP_RESERVED_BEGIN = 10000 | Inclusive begin of app-reserved ID range. |
| ARKUI_TEXT_MENU_ITEM_ID_APP_RESERVED_END = 20000 | Inclusive end of app-reserved ID range. |

### OH_ArkUI_LineBreakStrategy

```c
enum OH_ArkUI_LineBreakStrategy
```

**Description**

Enumerates line break policies.

**Since**: 24

| Enum item | Description |
| -- | -- |
| OH_ARKUI_LINE_BREAK_STRATEGY_GREEDY = 0 |  |
| OH_ARKUI_LINE_BREAK_STRATEGY_HIGH_QUALITY = 1 |  |
| OH_ARKUI_LINE_BREAK_STRATEGY_BALANCE = 2 |  |

### OH_ArkUI_StrokeJoinStyle

```c
enum OH_ArkUI_StrokeJoinStyle
```

**Description**

Enumerates the join styles of a text stroke.

**Since**: 26.2.0

| Enum item | Description |
| -- | -- |
| OH_ARKUI_STROKE_JOIN_STYLE_MITER_JOIN = 0 |  |
| OH_ARKUI_STROKE_JOIN_STYLE_ROUND_JOIN = 1 |  |
| OH_ARKUI_STROKE_JOIN_STYLE_BEVEL_JOIN = 2 |  |

### ArkUI_TextSpanType

```c
enum ArkUI_TextSpanType
```

**Description**

Enumerates the text span type.

**Since**: 22

| Enum item | Description |
| -- | -- |
| ARKUI_TEXT_SPAN_TYPE_TEXT = 0 | The span type only contains text. |
| ARKUI_TEXT_SPAN_TYPE_IMAGE = 1 | The span type only contains image. |
| ARKUI_TEXT_SPAN_TYPE_MIXED = 2 | The span type contains both text and image. |
| ARKUI_TEXT_SPAN_TYPE_DEFAULT = 3 | When no other types are explicitly specified, this type will be matched. When this type is registered but TEXT, IMAGE, or MIXED types are not registered, this type will be triggered and displayed for those registered types. |

### ArkUI_TextResponseType

```c
enum ArkUI_TextResponseType
```

**Description**

Enumerates the response types of a custom text selection menu.

**Since**: 22

| Enum item | Description |
| -- | -- |
| ARKUI_TEXT_RESPONSE_TYPE_RIGHT_CLICK = 0 | The response type of right click. |
| ARKUI_TEXT_RESPONSE_TYPE_LONG_PRESS = 1 | The response type of long press. |
| ARKUI_TEXT_RESPONSE_TYPE_SELECT = 2 | The response type of select by mouse. |
| ARKUI_TEXT_RESPONSE_TYPE_DEFAULT = 3 | When no other types are explicitly specified, this type will be matched. When this type is registered but RIGHT_CLICK, LONG_PRESS, or SELECT types are not registered, this type will be triggered and displayed for right-click, long press, and mouse selection actions. |


## Function description

### ArkUI_TextCreateMenuCallback()

```c
typedef void (*ArkUI_TextCreateMenuCallback)(ArkUI_TextMenuItemArray* items, void* userData)
```

**Description**

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMenuItemArray](capi-arkui-nativemodule-arkui-textmenuitemarray.md)* items | Pointer to the **ArkUI_TextMenuItemArray** object, which is created and released by the system. You can call OH_ArkUI_TextMenuItemArray_Insert and OH_ArkUI_TextMenuItemArray_Erase to modify the array in the callback. |
| void* userData | Pointer to the user-defined data, which is passed by you when registering the callback and returned as-is when the callback is triggered. It is used to obtain context data in the callback. The value **null**<br>indicates that no custom data is passed. |

### ArkUI_TextPrepareMenuCallback()

```c
typedef void (*ArkUI_TextPrepareMenuCallback)(ArkUI_TextMenuItemArray* items, void* userData)
```

**Description**

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMenuItemArray](capi-arkui-nativemodule-arkui-textmenuitemarray.md)* items | Pointer to the **ArkUI_TextMenuItemArray** object, which is created and released by the system. You can call OH_ArkUI_TextMenuItemArray_Insert and OH_ArkUI_TextMenuItemArray_Erase to modify the array in the callback. |
| void* userData | Pointer to the user-defined data, which is passed by you when registering the callback and returned as-is when the callback is triggered. It is used to obtain context data in the callback. The value **null**<br>means no custom data is passed. |

### ArkUI_TextMenuItemClickCallback()

```c
typedef bool (*ArkUI_TextMenuItemClickCallback)(const ArkUI_TextMenuItem* item, int32_t start, int32_t end, void* userData)
```

**Description**

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)* item | The menu item click. |
| int32_t start | The start offset of the selected content. |
| int32_t end | The end offset of the selected content. |
| void* userData | The user data. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | bool Return True, the event is consumed, false otherwise. |

### OH_ArkUI_ShowCounterConfig_Create()

```c
ArkUI_ShowCounterConfig* OH_ArkUI_ShowCounterConfig_Create()
```

**Description**

Creates a text input counter configuration object. When this object is no longer used, call [OH_ArkUI_ShowCounterConfig_Dispose](capi-text-common-h.md#oh_arkui_showcounterconfig_dispose) to dispose of it.

**Since**: 22

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ShowCounterConfig*](capi-arkui-nativemodule-arkui-showcounterconfig.md) | Pointer to the text input counter configuration object. |

### OH_ArkUI_ShowCounterConfig_Dispose()

```c
void OH_ArkUI_ShowCounterConfig_Dispose(ArkUI_ShowCounterConfig* config)
```

**Description**

Disposes of the text input counter configuration object created by [OH_ArkUI_ShowCounterConfig_Create](capi-text-common-h.md#oh_arkui_showcounterconfig_create).

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-showcounterconfig.md)* config | Pointer to the text input counter configuration object to be disposed of. |

### OH_ArkUI_ShowCounterConfig_SetCounterTextColor()

```c
void OH_ArkUI_ShowCounterConfig_SetCounterTextColor(ArkUI_ShowCounterConfig* config, uint32_t color)
```

**Description**

Sets the text color of the counter when the text input has not reached the maximum character limit. If this API is not called, the default color is **0x66182431**, displayed as gray.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-showcounterconfig.md)* config | Pointer to the text input counter configuration object. It must be created using **<br>OH_ArkUI_ShowCounterConfig_Create()** before use. |
| uint32_t color | Text color of the counter when the text input has not reached the maximum character limit, in 0xARGB format. |

### OH_ArkUI_ShowCounterConfig_SetCounterTextOverflowColor()

```c
void OH_ArkUI_ShowCounterConfig_SetCounterTextOverflowColor(ArkUI_ShowCounterConfig* config, uint32_t color)
```

**Description**

Sets the text color of the counter when the text input exceeds the maximum character limit. If this API is not called, the default color is **0x99FA2A2D**, displayed as red.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-showcounterconfig.md)* config | Pointer to the text input counter configuration object. |
| uint32_t color | Text color of the counter when the text input exceeds the maximum character limit, in 0xARGB format. |

### OH_ArkUI_ShowCounterConfig_GetCounterTextColor()

```c
uint32_t OH_ArkUI_ShowCounterConfig_GetCounterTextColor(ArkUI_ShowCounterConfig* config)
```

**Description**

Obtains the text color of the counter when the text input has not reached the maximum character limit.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-showcounterconfig.md)* config | Pointer to the text input counter configuration object. |

**Returns**:

| Type | Description |
| -- | -- |
| uint32_t | Text color of the counter when the text input has not reached the maximum character limit, in 0xARGB format. **0** is returned if the color is not set using [OH_ArkUI_ShowCounterConfig_SetCounterTextColor](capi-text-common-h.md#oh_arkui_showcounterconfig_setcountertextcolor); otherwise, the set color value is returned. |

### OH_ArkUI_ShowCounterConfig_GetCounterTextOverflowColor()

```c
uint32_t OH_ArkUI_ShowCounterConfig_GetCounterTextOverflowColor(ArkUI_ShowCounterConfig* config)
```

**Description**

Obtains the text color of the counter when the text input exceeds the maximum character limit.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-showcounterconfig.md)* config | Pointer to the text input counter configuration object. |

**Returns**:

| Type | Description |
| -- | -- |
| uint32_t | Text color of the counter when the text input exceeds the maximum character limit, in 0xARGB format. **0** is returned if the color is not set using [OH_ArkUI_ShowCounterConfig_SetCounterTextOverflowColor](capi-text-common-h.md#oh_arkui_showcounterconfig_setcountertextoverflowcolor); otherwise, the set color value is returned. |

### OH_ArkUI_TextMenuItem_Create()

```c
ArkUI_TextMenuItem* OH_ArkUI_TextMenuItem_Create()
```

**Description**

Creates a text menu item object for customizing the text selection menu or extending the system menu. It is applicable when custom menu items need to be added, such as sharing to a specific platform or performing custom editing operations. When this object is no longer used, call [OH_ArkUI_TextMenuItem_Dispose](capi-text-common-h.md#oh_arkui_textmenuitem_dispose) to dispose of it.

**Since**: 22

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_TextMenuItem*](capi-arkui-nativemodule-arkui-textmenuitem.md) | Pointer to the text menu item object, used to represent a single menu item in the text selection menu. |

### OH_ArkUI_TextMenuItem_Dispose()

```c
void OH_ArkUI_TextMenuItem_Dispose(ArkUI_TextMenuItem* textMenuItem)
```

**Description**

Disposes of the text menu item object created by [OH_ArkUI_TextMenuItem_Create](capi-text-common-h.md#oh_arkui_textmenuitem_create).

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)* textMenuItem | Pointer to the **ArkUI_TextMenuItem** object. |

### OH_ArkUI_TextEditMenuOptions_Create()

```c
ArkUI_TextEditMenuOptions* OH_ArkUI_TextEditMenuOptions_Create()
```

**Description**

Creates a text menu extension object for extending the text editing menu functionality. It is applicable when custom menu items need to be added to the text editing component, such as inserting special characters or performing quick formatting. When this object is no longer used, call [OH_ArkUI_TextEditMenuOptions_Dispose](capi-text-common-h.md#oh_arkui_texteditmenuoptions_dispose) to dispose of it.

**Since**: 22

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_TextEditMenuOptions*](capi-arkui-nativemodule-arkui-texteditmenuoptions.md) | Pointer to the text menu extension object, used to extend the functionality of the text editing menu. |

### OH_ArkUI_TextEditMenuOptions_Dispose()

```c
void OH_ArkUI_TextEditMenuOptions_Dispose(ArkUI_TextEditMenuOptions* editMenuOptions)
```

**Description**

Disposes of the text menu extension object created by [OH_ArkUI_TextEditMenuOptions_Create](capi-text-common-h.md#oh_arkui_texteditmenuoptions_create).

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextEditMenuOptions](capi-arkui-nativemodule-arkui-texteditmenuoptions.md)* editMenuOptions | Pointer to the **ArkUI_TextEditMenuOptions** object. |

### OH_ArkUI_TextSelectionMenuOptions_Create()

```c
ArkUI_TextSelectionMenuOptions* OH_ArkUI_TextSelectionMenuOptions_Create()
```

**Description**

Creates a custom text selection menu object for configuring the content and behavior of the text selection menu. It is applicable when the text selection menu needs to be fully customized, such as replacing the default menu and adding application-specific operations. When this object is no longer used, call [OH_ArkUI_TextSelectionMenuOptions_Dispose](capi-text-common-h.md#oh_arkui_textselectionmenuoptions_dispose) to dispose of it.

**Since**: 22

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_TextSelectionMenuOptions*](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md) | Pointer to the custom text selection menu object, used for custom configuration of menu content, styles, and behavior. |

### OH_ArkUI_TextSelectionMenuOptions_Dispose()

```c
void OH_ArkUI_TextSelectionMenuOptions_Dispose(ArkUI_TextSelectionMenuOptions* selectionMenuOptions)
```

**Description**

Disposes of the custom text selection menu object created by [OH_ArkUI_TextSelectionMenuOptions_Create](capi-text-common-h.md#oh_arkui_textselectionmenuoptions_create).

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextSelectionMenuOptions](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md)* selectionMenuOptions | Pointer to the **ArkUI_TextSelectionMenuOptions** object. |

### OH_ArkUI_TextContentBaseController_Create()

```c
ArkUI_TextContentBaseController* OH_ArkUI_TextContentBaseController_Create()
```

**Description**

Creates a text content base controller object. When this object is no longer used, call [OH_ArkUI_TextContentBaseController_Dispose](capi-text-common-h.md#oh_arkui_textcontentbasecontroller_dispose) to dispose of it.

**Since**: 23

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_TextContentBaseController*](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md) | Pointer to the text content base controller object, used for content control of text components, supporting operations such as obtaining, setting, and updating text content. |

### OH_ArkUI_TextContentBaseController_Dispose()

```c
void OH_ArkUI_TextContentBaseController_Dispose(ArkUI_TextContentBaseController* controller)
```

**Description**

Disposes of the text content base controller object created by [OH_ArkUI_TextContentBaseController_Create](capi-text-common-h.md#oh_arkui_textcontentbasecontroller_create).

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| {ArkUI_TextContentBaseController*} | controller Pointer to the controller object to be disposed. |

### OH_ArkUI_TextContentBaseController_DeleteBackward()

```c
void OH_ArkUI_TextContentBaseController_DeleteBackward(ArkUI_TextContentBaseController* controller)
```

**Description**

Deletes the character before the cursor in editing state; deletes the last character of the text box component in other states.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| {ArkUI_TextContentBaseController*} | controller Pointer to the configuration object to be modified. |

### OH_ArkUI_TextContentBaseController_ScrollToVisible()

```c
void OH_ArkUI_TextContentBaseController_ScrollToVisible(ArkUI_TextContentBaseController *controller, int32_t start, int32_t end)
```

**Description**

Passes the start and end indexes to the bound text box component, and scrolls the text within the range to the visible area.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| {ArkUI_TextContentBaseController*} | controller Pointer to the configuration object to be modified. |
| {int32_t} | start Start text index. The start index must be less than or equal to the end index. Otherwise, the API call is invalid. The value range is [0, Total length of the text in the text box]. If the start index is less than 0, the start index is regarded as 0. If the start index is greater than the total length, the start indexis regarded as the total length. |
| {int32_t} | end End text index. The end index must be greater than or equal to the start index. Otherwise, the API call is invalid. The value range is [0, Total length of the text in the text box]. If the end index is less than 0, the end index is regarded as 0. If the end index is greater than the total length, the end index is regarded as the total length. |

### OH_ArkUI_DecorationStyleOptions_Create()

```c
OH_ArkUI_DecorationStyleOptions* OH_ArkUI_DecorationStyleOptions_Create()
```

**Description**

Creates a decoration style object for setting the type, style, and color of text decorative lines. It is applicable when decoration effects such as underlines or strikethroughs need to be added to text, for example, in rich text editors, hyperlink text, or price tags. When this object is no longer used, call [OH_ArkUI_DecorationStyleOptions_Destroy](capi-text-common-h.md#oh_arkui_decorationstyleoptions_destroy) to destroy it.

**Since**: 24

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_DecorationStyleOptions*](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md) | Pointer to the decoration style object, used to define the decorative line style. |

### OH_ArkUI_DecorationStyleOptions_Destroy()

```c
void OH_ArkUI_DecorationStyleOptions_Destroy(OH_ArkUI_DecorationStyleOptions* options)
```

**Description**

Destroys the decoration style object created by [OH_ArkUI_DecorationStyleOptions_Create](capi-text-common-h.md#oh_arkui_decorationstyleoptions_create).

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md)* options | Pointer to the option object to be destroyed. |


