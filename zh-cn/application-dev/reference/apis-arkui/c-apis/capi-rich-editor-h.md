# rich_editor.h

## 概述

Defines a set of RichEditor enum and interface.

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 24

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md) | OH_ArkUI_TextEditorSelectionMenuOptions | 定义文本编辑器的文本选择菜单选项。 |
| [OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md) | OH_ArkUI_TextEditorPlaceholderOptions | 定义文本编辑器中没有输入内容时的提示文本选项。 |
| [OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md) | OH_ArkUI_TextEditorStyledStringController | 定义文本编辑器的属性字符串控制器。 |
| [OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md) | OH_ArkUI_TextEditorParagraphStyle | 定义文本编辑器的段落样式。 |
| [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md) | OH_ArkUI_TextEditorTextStyle | 定义文本编辑器的文本样式。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_ArkUI_HapticFeedbackMode](#oh_arkui_hapticfeedbackmode) | OH_ArkUI_HapticFeedbackMode | 枚举振动效果类型。 |
| [OH_ArkUI_TextEditorSpanType](#oh_arkui_texteditorspantype) | OH_ArkUI_TextEditorSpanType | 自定义文本选择菜单span类型枚举。 |
| [OH_ArkUI_TextEditorResponseType](#oh_arkui_texteditorresponsetype) | OH_ArkUI_TextEditorResponseType | 自定义文本选择菜单响应类型枚举。 |
| [OH_ArkUI_TextMenuType](#oh_arkui_textmenutype) | OH_ArkUI_TextMenuType | 文本菜单类型枚举。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorPlaceholderOptions* OH_ArkUI_TextEditorPlaceholderOptions_Create()](#oh_arkui_texteditorplaceholderoptions_create) | 为无输入时使用的占位符文本创建选项对象。当对象不再是使用时，调用[OH_ArkUI_TextEditorPlaceholderOptions_Destroy](capi-rich-editor-h.md#oh_arkui_texteditorplaceholderoptions_destroy)将其销毁。 |
| [void OH_ArkUI_TextEditorPlaceholderOptions_Destroy(OH_ArkUI_TextEditorPlaceholderOptions* options)](#oh_arkui_texteditorplaceholderoptions_destroy) | 销毁没有输入时使用的占位符文本的选项对象。 |
| [OH_ArkUI_TextEditorStyledStringController* OH_ArkUI_TextEditorStyledStringController_Create()](#oh_arkui_texteditorstyledstringcontroller_create) | 为文本编辑器创建一个带样式的字符串控制器对象。当对象不再使用时，调用[OH_ArkUI_TextEditorStyledStringController_Destroy](capi-rich-editor-h.md#oh_arkui_texteditorstyledstringcontroller_destroy)来销毁它。 |
| [void OH_ArkUI_TextEditorStyledStringController_Destroy(OH_ArkUI_TextEditorStyledStringController* controller)](#oh_arkui_texteditorstyledstringcontroller_destroy) | 销毁样式化的字符串控制器对象。 |
| [OH_ArkUI_TextEditorParagraphStyle* OH_ArkUI_TextEditorParagraphStyle_Create()](#oh_arkui_texteditorparagraphstyle_create) | 为文本编辑器创建段落样式对象。当对象不再使用时，调用[OH_ArkUI_TextEditorParagraphStyle_Destroy](capi-rich-editor-h.md#oh_arkui_texteditorparagraphstyle_destroy)来销毁它。 |
| [void OH_ArkUI_TextEditorParagraphStyle_Destroy(OH_ArkUI_TextEditorParagraphStyle* style)](#oh_arkui_texteditorparagraphstyle_destroy) | 销毁段落样式对象。 |
| [OH_ArkUI_TextEditorTextStyle* OH_ArkUI_TextEditorTextStyle_Create()](#oh_arkui_texteditortextstyle_create) | 创建文本样式对象。当对象不再使用时，调用[OH_ArkUI_TextEditorTextStyle_Destroy](capi-rich-editor-h.md#oh_arkui_texteditortextstyle_destroy)来销毁它。 |
| [void OH_ArkUI_TextEditorTextStyle_Destroy(OH_ArkUI_TextEditorTextStyle* style)](#oh_arkui_texteditortextstyle_destroy) | 销毁文本样式对象。 |
| [OH_ArkUI_TextEditorSelectionMenuOptions* OH_ArkUI_TextEditorSelectionMenuOptions_Create()](#oh_arkui_texteditorselectionmenuoptions_create) | 创建文本编辑器的文本选择菜单选项对象。当对象不再使用时，调用[OH_ArkUI_TextEditorSelectionMenuOptions_Destroy](capi-rich-editor-h.md#oh_arkui_texteditorselectionmenuoptions_destroy)来销毁它。 |
| [void OH_ArkUI_TextEditorSelectionMenuOptions_Destroy(OH_ArkUI_TextEditorSelectionMenuOptions* options)](#oh_arkui_texteditorselectionmenuoptions_destroy) | 销毁文本编辑器的文本选择菜单选项对象。 |

## 枚举类型说明

### OH_ArkUI_HapticFeedbackMode

```c
enum OH_ArkUI_HapticFeedbackMode
```

**描述**

枚举振动效果类型。

**起始版本：** 24

| 枚举项 | 描述 |
| -- | -- |
| OH_ARKUI_HAPTIC_FEEDBACK_MODE_DISABLED = 0 |  |
| OH_ARKUI_HAPTIC_FEEDBACK_MODE_ENABLED = 1 |  |
| OH_ARKUI_HAPTIC_FEEDBACK_MODE_AUTO = 2 |  |

### OH_ArkUI_TextEditorSpanType

```c
enum OH_ArkUI_TextEditorSpanType
```

**描述**

自定义文本选择菜单span类型枚举。

**起始版本：** 24

| 枚举项 | 描述 |
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

**描述**

自定义文本选择菜单响应类型枚举。

**起始版本：** 24

| 枚举项 | 描述 |
| -- | -- |
| OH_ARKUI_TEXT_EDITOR_RESPONSE_TYPE_RIGHT_CLICK = 0 |  |
| OH_ARKUI_TEXT_EDITOR_RESPONSE_TYPE_LONG_PRESS = 1 |  |
| OH_ARKUI_TEXT_EDITOR_RESPONSE_TYPE_SELECT = 2 |  |
| OH_ARKUI_TEXT_EDITOR_RESPONSE_TYPE_DEFAULT = 3 |  |

### OH_ArkUI_TextMenuType

```c
enum OH_ArkUI_TextMenuType
```

**描述**

文本菜单类型枚举。

**起始版本：** 24

| 枚举项 | 描述 |
| -- | -- |
| OH_ARKUI_TEXT_EDITOR_SELECTION_MENU = 0 |  |
| OH_ARKUI_TEXT_EDITOR_PREVIEW_MENU = 1 |  |


## 函数说明

### OH_ArkUI_TextEditorPlaceholderOptions_Create()

```c
OH_ArkUI_TextEditorPlaceholderOptions* OH_ArkUI_TextEditorPlaceholderOptions_Create()
```

**描述**

为无输入时使用的占位符文本创建选项对象。当对象不再是使用时，调用[OH_ArkUI_TextEditorPlaceholderOptions_Destroy](capi-rich-editor-h.md#oh_arkui_texteditorplaceholderoptions_destroy)将其销毁。

**起始版本：** 24

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_ArkUI_TextEditorPlaceholderOptions*](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md) | 指向[OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md)对象的指针。 |

### OH_ArkUI_TextEditorPlaceholderOptions_Destroy()

```c
void OH_ArkUI_TextEditorPlaceholderOptions_Destroy(OH_ArkUI_TextEditorPlaceholderOptions* options)
```

**描述**

销毁没有输入时使用的占位符文本的选项对象。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md)* options | 指向[OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md)对象的指针。 |

### OH_ArkUI_TextEditorStyledStringController_Create()

```c
OH_ArkUI_TextEditorStyledStringController* OH_ArkUI_TextEditorStyledStringController_Create()
```

**描述**

为文本编辑器创建一个带样式的字符串控制器对象。当对象不再使用时，调用[OH_ArkUI_TextEditorStyledStringController_Destroy](capi-rich-editor-h.md#oh_arkui_texteditorstyledstringcontroller_destroy)来销毁它。

**起始版本：** 24

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_ArkUI_TextEditorStyledStringController*](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md) | 指向[OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)对象的指针。 |

### OH_ArkUI_TextEditorStyledStringController_Destroy()

```c
void OH_ArkUI_TextEditorStyledStringController_Destroy(OH_ArkUI_TextEditorStyledStringController* controller)
```

**描述**

销毁样式化的字符串控制器对象。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)* controller | 指向[OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)对象的指针。 |

### OH_ArkUI_TextEditorParagraphStyle_Create()

```c
OH_ArkUI_TextEditorParagraphStyle* OH_ArkUI_TextEditorParagraphStyle_Create()
```

**描述**

为文本编辑器创建段落样式对象。当对象不再使用时，调用[OH_ArkUI_TextEditorParagraphStyle_Destroy](capi-rich-editor-h.md#oh_arkui_texteditorparagraphstyle_destroy)来销毁它。

**起始版本：** 24

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_ArkUI_TextEditorParagraphStyle*](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md) | 指向[OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)对象的指针。 |

### OH_ArkUI_TextEditorParagraphStyle_Destroy()

```c
void OH_ArkUI_TextEditorParagraphStyle_Destroy(OH_ArkUI_TextEditorParagraphStyle* style)
```

**描述**

销毁段落样式对象。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)* style | 指向[OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)对象的指针。 |

### OH_ArkUI_TextEditorTextStyle_Create()

```c
OH_ArkUI_TextEditorTextStyle* OH_ArkUI_TextEditorTextStyle_Create()
```

**描述**

创建文本样式对象。当对象不再使用时，调用[OH_ArkUI_TextEditorTextStyle_Destroy](capi-rich-editor-h.md#oh_arkui_texteditortextstyle_destroy)来销毁它。

**起始版本：** 24

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_ArkUI_TextEditorTextStyle*](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md) | 指向[OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md)对象的指针。 |

### OH_ArkUI_TextEditorTextStyle_Destroy()

```c
void OH_ArkUI_TextEditorTextStyle_Destroy(OH_ArkUI_TextEditorTextStyle* style)
```

**描述**

销毁文本样式对象。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md)* style | 指向[OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md)对象的指针。 |

### OH_ArkUI_TextEditorSelectionMenuOptions_Create()

```c
OH_ArkUI_TextEditorSelectionMenuOptions* OH_ArkUI_TextEditorSelectionMenuOptions_Create()
```

**描述**

创建文本编辑器的文本选择菜单选项对象。当对象不再使用时，调用[OH_ArkUI_TextEditorSelectionMenuOptions_Destroy](capi-rich-editor-h.md#oh_arkui_texteditorselectionmenuoptions_destroy)来销毁它。

**起始版本：** 24

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_ArkUI_TextEditorSelectionMenuOptions*](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md) | 指向[OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)对象的指针。 |

### OH_ArkUI_TextEditorSelectionMenuOptions_Destroy()

```c
void OH_ArkUI_TextEditorSelectionMenuOptions_Destroy(OH_ArkUI_TextEditorSelectionMenuOptions* options)
```

**描述**

销毁文本编辑器的文本选择菜单选项对象。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)* options | 指向[OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)对象的指针。 |


