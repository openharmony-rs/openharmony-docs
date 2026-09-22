# text_common.h

## Overview

Defines a set of text common enum and interface.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) | ArkUI_StyledString_Descriptor | Define the data objects of styled string supported by text components. |
| [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-showcounterconfig.md) | ArkUI_ShowCounterConfig | Defines the textField's counter configuration. |
| [ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md) | ArkUI_TextContentBaseController | Defines the text content base controller. |
| [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md) | ArkUI_TextMenuItem | Defines the text menu item for edit menu item. |
| [ArkUI_TextMenuItemArray](capi-arkui-nativemodule-arkui-textmenuitemarray.md) | ArkUI_TextMenuItemArray | Defines text menu item array. |
| [ArkUI_TextEditMenuOptions](capi-arkui-nativemodule-arkui-texteditmenuoptions.md) | ArkUI_TextEditMenuOptions | Defines the text menu item for edit menu options. |
| [ArkUI_TextSelectionMenuOptions](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md) | ArkUI_TextSelectionMenuOptions | Defines the selection menu. |
| [OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md) | OH_ArkUI_DecorationStyleOptions | Defines decoration style options. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_TextAlignment](#arkui_textalignment) | ArkUI_TextAlignment | Enumerates the text alignment mode. |
| [ArkUI_TextVerticalAlignment](#arkui_textverticalalignment) | ArkUI_TextVerticalAlignment | Enumerates text vertical alignment styles. |
| [ArkUI_TextContentAlign](#arkui_textcontentalign) | ArkUI_TextContentAlign | Enumerates text content align styles. |
| [ArkUI_TextDirection](#arkui_textdirection) | ArkUI_TextDirection | Enumerates the text text direction. |
| [ArkUI_EnterKeyType](#arkui_enterkeytype) | ArkUI_EnterKeyType | Enumerates the types of the Enter key for a single-line text box. |
| [ArkUI_TextDecorationType](#arkui_textdecorationtype) | ArkUI_TextDecorationType | Enumerates the text decoration types. |
| [ArkUI_TextDecorationStyle](#arkui_textdecorationstyle) | ArkUI_TextDecorationStyle | Enumerates the text decoration styles. |
| [ArkUI_TextCase](#arkui_textcase) | ArkUI_TextCase | Enumerates the text cases. |
| [ArkUI_TextCopyOptions](#arkui_textcopyoptions) | ArkUI_TextCopyOptions | Defines whether copy and paste is allowed for text content. |
| [ArkUI_TextOverflow](#arkui_textoverflow) | ArkUI_TextOverflow | Enumerates the display modes when the text is too long. |
| [ArkUI_WordBreak](#arkui_wordbreak) | ArkUI_WordBreak | Enumerates the word break rules. |
| [ArkUI_EllipsisMode](#arkui_ellipsismode) | ArkUI_EllipsisMode | Enumerates the ellipsis positions. |
| [ArkUI_KeyboardAppearance](#arkui_keyboardappearance) | ArkUI_KeyboardAppearance | Defines the keyboard style of input box |
| [ArkUI_TextMenuItemId](#arkui_textmenuitemid) | ArkUI_TextMenuItemId | Enumerates the text menu item id. |
| [OH_ArkUI_LineBreakStrategy](#oh_arkui_linebreakstrategy) | OH_ArkUI_LineBreakStrategy | Enumerates line break policies. |
| [OH_ArkUI_StrokeJoinStyle](#oh_arkui_strokejoinstyle) | OH_ArkUI_StrokeJoinStyle | Enumerates the join styles of a text stroke. |
| [ArkUI_TextSpanType](#arkui_textspantype) | ArkUI_TextSpanType | Enumerates the text span type. |
| [ArkUI_TextResponseType](#arkui_textresponsetype) | ArkUI_TextResponseType | Enumerates the text response type. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*ArkUI_TextCreateMenuCallback)(ArkUI_TextMenuItemArray* items, void* userData)](#arkui_textcreatemenucallback) | ArkUI_TextCreateMenuCallback |  |
| [typedef void (\*ArkUI_TextPrepareMenuCallback)(ArkUI_TextMenuItemArray* items, void* userData)](#arkui_textpreparemenucallback) | ArkUI_TextPrepareMenuCallback |  |
| [typedef bool (\*ArkUI_TextMenuItemClickCallback)(const ArkUI_TextMenuItem* item, int32_t start, int32_t end, void* userData)](#arkui_textmenuitemclickcallback) | ArkUI_TextMenuItemClickCallback |  |
| [ArkUI_ShowCounterConfig* OH_ArkUI_ShowCounterConfig_Create()](#oh_arkui_showcounterconfig_create) | - | Creates a configuration object for textField's counter. |
| [void OH_ArkUI_ShowCounterConfig_Dispose(ArkUI_ShowCounterConfig* config)](#oh_arkui_showcounterconfig_dispose) | - | Disposes a configuration object for textField's counter. |
| [void OH_ArkUI_ShowCounterConfig_SetCounterTextColor(ArkUI_ShowCounterConfig* config, uint32_t color)](#oh_arkui_showcounterconfig_setcountertextcolor) | - | Sets the color of counter when textField hasn't wanted to exceed the maximum character count. |
| [void OH_ArkUI_ShowCounterConfig_SetCounterTextOverflowColor(ArkUI_ShowCounterConfig* config, uint32_t color)](#oh_arkui_showcounterconfig_setcountertextoverflowcolor) | - | Sets the color of counter when textField wants to exceed the maximum character count. |
| [uint32_t OH_ArkUI_ShowCounterConfig_GetCounterTextColor(ArkUI_ShowCounterConfig* config)](#oh_arkui_showcounterconfig_getcountertextcolor) | - | Gets the color of counter when textField hasn't wanted to exceed the maximum character count. |
| [uint32_t OH_ArkUI_ShowCounterConfig_GetCounterTextOverflowColor(ArkUI_ShowCounterConfig* config)](#oh_arkui_showcounterconfig_getcountertextoverflowcolor) | - | Gets the color of counter when textField wants to exceed the maximum character count. |
| [ArkUI_TextMenuItem* OH_ArkUI_TextMenuItem_Create()](#oh_arkui_textmenuitem_create) | - | Create an object of the text edit menu item. |
| [void OH_ArkUI_TextMenuItem_Dispose(ArkUI_TextMenuItem* textMenuItem)](#oh_arkui_textmenuitem_dispose) | - | Dispose an object of the text edit menu options. |
| [ArkUI_TextEditMenuOptions* OH_ArkUI_TextEditMenuOptions_Create()](#oh_arkui_texteditmenuoptions_create) | - | Create an object of the text edit menu options. |
| [void OH_ArkUI_TextEditMenuOptions_Dispose(ArkUI_TextEditMenuOptions* editMenuOptions)](#oh_arkui_texteditmenuoptions_dispose) | - | Dispose an object of the text edit menu options. |
| [ArkUI_TextSelectionMenuOptions* OH_ArkUI_TextSelectionMenuOptions_Create()](#oh_arkui_textselectionmenuoptions_create) | - | Create an object of the text selection menu options. |
| [void OH_ArkUI_TextSelectionMenuOptions_Dispose(ArkUI_TextSelectionMenuOptions* selectionMenuOptions)](#oh_arkui_textselectionmenuoptions_dispose) | - | Dispose an object of the text selection menu options. |
| [ArkUI_TextContentBaseController* OH_ArkUI_TextContentBaseController_Create()](#oh_arkui_textcontentbasecontroller_create) | - | Create an object of the text content base controller. |
| [void OH_ArkUI_TextContentBaseController_Dispose(ArkUI_TextContentBaseController* controller)](#oh_arkui_textcontentbasecontroller_dispose) | - | Dispose an object of the text content base controller. |
| [void OH_ArkUI_TextContentBaseController_DeleteBackward(ArkUI_TextContentBaseController* controller)](#oh_arkui_textcontentbasecontroller_deletebackward) | - | Delete the character before the caret of the input field component in editing state. Otherwise, delete the last character of the input field component. |
| [void OH_ArkUI_TextContentBaseController_ScrollToVisible(ArkUI_TextContentBaseController *controller, int32_t start, int32_t end)](#oh_arkui_textcontentbasecontroller_scrolltovisible) | - | Scroll the input field component to make the specified content visible. |
| [OH_ArkUI_DecorationStyleOptions* OH_ArkUI_DecorationStyleOptions_Create()](#oh_arkui_decorationstyleoptions_create) | - | Creates a decorative line style object. When the object is no longer used, call [OH_ArkUI_DecorationStyleOptions_Destroy](capi-text-common-h.md#oh_arkui_decorationstyleoptions_destroy) to destroy it. |
| [void OH_ArkUI_DecorationStyleOptions_Destroy(OH_ArkUI_DecorationStyleOptions* options)](#oh_arkui_decorationstyleoptions_destroy) | - | Destroys the decorative line style object. |

## Enum type description

### ArkUI_TextAlignment

```c
enum ArkUI_TextAlignment
```

**Description**

Enumerates the text alignment mode.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

Enumerates text content align styles.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

Enumerates the text text direction.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

Enumerates the types of the Enter key for a single-line text box.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

Enumerates the text decoration types.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

Enumerates the text decoration styles.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

Enumerates the text cases.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

Defines whether copy and paste is allowed for text content.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

Enumerates the word break rules.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_WORD_BREAK_NORMAL = 0 | Word breaks can occur between any two characters for Chinese, Japanese, and Korean (CJK) text, but can occur |
| ARKUI_WORD_BREAK_BREAK_ALL | Word breaks can occur between any two characters for non-CJK text. CJK text behavior is the same as for |
| ARKUI_WORD_BREAK_BREAK_WORD | This option has the same effect as <b>BREAK_ALL</b> for non-CJK text, except that if it preferentially wraps lines at appropriate characters (for example, spaces) whenever possible. |
| ARKUI_WORD_BREAK_HYPHENATION | Line breaks can occur between any two syllabic units for non-CJK text. CJK text behavior is the same as for <b>NORMAL</b>.<br>**Since**: 18 |

### ArkUI_EllipsisMode

```c
enum ArkUI_EllipsisMode
```

**Description**

Enumerates the ellipsis positions.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_ELLIPSIS_MODE_START = 0 | An ellipsis is used at the start of the line of text. |
| ARKUI_ELLIPSIS_MODE_CENTER | An ellipsis is used at the center of the line of text. |
| ARKUI_ELLIPSIS_MODE_END | An ellipsis is used at the end of the line of text. |
| ARKUI_ELLIPSIS_MODE_MULTILINE_START | An ellipsis is used at the start of the line of text for multiline and single line. @since 24 |
| ARKUI_ELLIPSIS_MODE_MULTILINE_CENTER | An ellipsis is used at the center of the line of text for multiline and single line. @since 24 |

### ArkUI_KeyboardAppearance

```c
enum ArkUI_KeyboardAppearance
```

**Description**

Defines the keyboard style of input box

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

Enumerates the text menu item id.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

Enumerates the text response type.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMenuItemArray](capi-arkui-nativemodule-arkui-textmenuitemarray.md)\* items | The framework creates and owns the array. In callback: the developer can modify the array by calling {@link OH_ArkUI_TextMenuItemArray_Insert},<br>    {@link OH_ArkUI_TextMenuItemArray_Erase}, or similar APIs. The developer must not free the array instance. |
| void\* userData | User defined data. |

### ArkUI_TextPrepareMenuCallback()

```c
typedef void (*ArkUI_TextPrepareMenuCallback)(ArkUI_TextMenuItemArray* items, void* userData)
```

**Description**

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMenuItemArray](capi-arkui-nativemodule-arkui-textmenuitemarray.md)\* items | The framework creates and owns the array. In callback: the developer can modify the array by calling {@link OH_ArkUI_TextMenuItemArray_Insert},<br>    {@link OH_ArkUI_TextMenuItemArray_Erase}, or similar APIs. The developer must not free the array instance. |
| void\* userData | User defined data. |

### ArkUI_TextMenuItemClickCallback()

```c
typedef bool (*ArkUI_TextMenuItemClickCallback)(const ArkUI_TextMenuItem* item, int32_t start, int32_t end, void* userData)
```

**Description**

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)\* item | The menu item click. |
| int32_t start | The start offset of the selected content. |
| int32_t end | The end offset of the selected content. |
| void\* userData | The user data. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | bool Return True, the event is consumed, false otherwise. |

### OH_ArkUI_ShowCounterConfig_Create()

```c
ArkUI_ShowCounterConfig* OH_ArkUI_ShowCounterConfig_Create()
```

**Description**

Creates a configuration object for textField's counter.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ShowCounterConfig*](capi-arkui-nativemodule-arkui-showcounterconfig.md) | A pointer to the configuration object. |

### OH_ArkUI_ShowCounterConfig_Dispose()

```c
void OH_ArkUI_ShowCounterConfig_Dispose(ArkUI_ShowCounterConfig* config)
```

**Description**

Disposes a configuration object for textField's counter.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-showcounterconfig.md)* config | Pointer to the configuration object to be disposed. |

### OH_ArkUI_ShowCounterConfig_SetCounterTextColor()

```c
void OH_ArkUI_ShowCounterConfig_SetCounterTextColor(ArkUI_ShowCounterConfig* config, uint32_t color)
```

**Description**

Sets the color of counter when textField hasn't wanted to exceed the maximum character count.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-showcounterconfig.md)* config | Pointer to the configuration object to be modified. |
| uint32_t color | The color of the counter when textField hasn't wanted to exceed the maximum character count, in 0xARGB format. |

### OH_ArkUI_ShowCounterConfig_SetCounterTextOverflowColor()

```c
void OH_ArkUI_ShowCounterConfig_SetCounterTextOverflowColor(ArkUI_ShowCounterConfig* config, uint32_t color)
```

**Description**

Sets the color of counter when textField wants to exceed the maximum character count.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-showcounterconfig.md)* config | Pointer to the configuration object to be modified. |
| uint32_t color | The color of the counter when textField wants to exceed the maximum character count, in 0xARGB format. |

### OH_ArkUI_ShowCounterConfig_GetCounterTextColor()

```c
uint32_t OH_ArkUI_ShowCounterConfig_GetCounterTextColor(ArkUI_ShowCounterConfig* config)
```

**Description**

Gets the color of counter when textField hasn't wanted to exceed the maximum character count.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-showcounterconfig.md)* config | Pointer to the configuration object. |

**Returns**:

| Type | Description |
| -- | -- |
| uint32_t | Returns the color of the counter when textField hasn't wanted to exceed the maximum character count, in 0xARGB format. |

### OH_ArkUI_ShowCounterConfig_GetCounterTextOverflowColor()

```c
uint32_t OH_ArkUI_ShowCounterConfig_GetCounterTextOverflowColor(ArkUI_ShowCounterConfig* config)
```

**Description**

Gets the color of counter when textField wants to exceed the maximum character count.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-showcounterconfig.md)* config | Pointer to the configuration object. |

**Returns**:

| Type | Description |
| -- | -- |
| uint32_t | Returns the color of the counter when textField wants to exceed the maximum character count, in 0xARGB format. |

### OH_ArkUI_TextMenuItem_Create()

```c
ArkUI_TextMenuItem* OH_ArkUI_TextMenuItem_Create()
```

**Description**

Create an object of the text edit menu item.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_TextMenuItem*](capi-arkui-nativemodule-arkui-textmenuitem.md) | A pointer to the ArkUI_TextMenuItem. |

### OH_ArkUI_TextMenuItem_Dispose()

```c
void OH_ArkUI_TextMenuItem_Dispose(ArkUI_TextMenuItem* textMenuItem)
```

**Description**

Dispose an object of the text edit menu options.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)* textMenuItem | Pointer to the ArkUI_TextMenuItem object to be disposed. |

### OH_ArkUI_TextEditMenuOptions_Create()

```c
ArkUI_TextEditMenuOptions* OH_ArkUI_TextEditMenuOptions_Create()
```

**Description**

Create an object of the text edit menu options.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_TextEditMenuOptions*](capi-arkui-nativemodule-arkui-texteditmenuoptions.md) | A pointer to the ArkUI_TextEditMenuOptions. |

### OH_ArkUI_TextEditMenuOptions_Dispose()

```c
void OH_ArkUI_TextEditMenuOptions_Dispose(ArkUI_TextEditMenuOptions* editMenuOptions)
```

**Description**

Dispose an object of the text edit menu options.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextEditMenuOptions](capi-arkui-nativemodule-arkui-texteditmenuoptions.md)* editMenuOptions | Pointer to the ArkUI_TextEditMenuOptions object to be disposed. |

### OH_ArkUI_TextSelectionMenuOptions_Create()

```c
ArkUI_TextSelectionMenuOptions* OH_ArkUI_TextSelectionMenuOptions_Create()
```

**Description**

Create an object of the text selection menu options.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_TextSelectionMenuOptions*](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md) | A pointer to the ArkUI_TextSelectionMenuOptions. |

### OH_ArkUI_TextSelectionMenuOptions_Dispose()

```c
void OH_ArkUI_TextSelectionMenuOptions_Dispose(ArkUI_TextSelectionMenuOptions* selectionMenuOptions)
```

**Description**

Dispose an object of the text selection menu options.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextSelectionMenuOptions](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md)* selectionMenuOptions | Pointer to the ArkUI_TextSelectionMenuOptions object to be disposed. |

### OH_ArkUI_TextContentBaseController_Create()

```c
ArkUI_TextContentBaseController* OH_ArkUI_TextContentBaseController_Create()
```

**Description**

Create an object of the text content base controller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_TextContentBaseController*](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md) | A pointer to the controller object. |

### OH_ArkUI_TextContentBaseController_Dispose()

```c
void OH_ArkUI_TextContentBaseController_Dispose(ArkUI_TextContentBaseController* controller)
```

**Description**

Dispose an object of the text content base controller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

Delete the character before the caret of the input field component in editing state. Otherwise, delete the last character of the input field component.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

Scroll the input field component to make the specified content visible.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| {ArkUI_TextContentBaseController*} | controller Pointer to the configuration object to be modified. |
| {int32_t} | start The start offset of the content to be made visible. |
| {int32_t} | end The end offset of the content to be made visible |

### OH_ArkUI_DecorationStyleOptions_Create()

```c
OH_ArkUI_DecorationStyleOptions* OH_ArkUI_DecorationStyleOptions_Create()
```

**Description**

Creates a decorative line style object. When the object is no longer used, call [OH_ArkUI_DecorationStyleOptions_Destroy](capi-text-common-h.md#oh_arkui_decorationstyleoptions_destroy) to destroy it.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_DecorationStyleOptions*](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md) | Pointer to the [OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md) object. |

### OH_ArkUI_DecorationStyleOptions_Destroy()

```c
void OH_ArkUI_DecorationStyleOptions_Destroy(OH_ArkUI_DecorationStyleOptions* options)
```

**Description**

Destroys the decorative line style object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md)* options | Pointer to the option object to be destroyed. |


