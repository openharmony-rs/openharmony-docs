# OH_InputMethod_PreviewTextStyle

```c
typedef struct OH_InputMethod_PreviewTextStyle OH_InputMethod_PreviewTextStyle
```

## 概述

OH_InputMethod_PreviewTextStyle是预上屏文本样式的不透明类型（opaque type），用于描述预上屏文本的下划线样式和颜色信息。 调用者不可直接访问其内部成员，仅可通过本头文件提供的函数接口进行操作。 <br> <br>用途：为输入法设置带样式的预上屏文本提供样式描述。包含以下属性： <br>- 下划线样式（underlineStyle）：枚举值，取值为[OH_InputMethod_UnderlineStyle](capi-inputmethod-types-capi-h.md#oh_inputmethod_underlinestyle)，默认值为 [OH_INPUTMETHOD_UNDERLINE_STYLE_NONE](capi-inputmethod-types-capi-h.md#oh_inputmethod_underlinestyle)。 <br>- 下划线颜色（underlineColor）：格式为0xRRGGBB，仅当hasUnderlineColor为true时有效。透明度通道（AA）无效，将被 编辑器忽略。 <br>- 是否显式设置颜色（hasUnderlineColor）：false表示跟随应用主题色。 <br> <br>生命周期管理： <br>- 创建方式：通过[OH_InputMethod_PreviewTextStyle_Create](#oh_inputmethod_previewtextstyle_create)函数创建，返回一个 新的OH_InputMethod_PreviewTextStyle实例指针。创建失败时返回NULL，可能原因为内存不足。 <br>- 销毁方式：通过[OH_InputMethod_PreviewTextStyle_Destroy](#oh_inputmethod_previewtextstyle_destroy)函数销毁，传入 要销毁的实例指针。销毁后指针不可再使用，建议将指针设置为NULL避免误用。 <br>- 配对关系：OH_InputMethod_PreviewTextStyle_Create与OH_InputMethod_PreviewTextStyle_Destroy必须配对使用，创建的对象 必须最终通过Destroy释放，否则会导致内存泄漏。

<!--Device-typedef struct OH_InputMethod_PreviewTextStyle OH_InputMethod_PreviewTextStyle--><!--Device-typedef struct OH_InputMethod_PreviewTextStyle OH_InputMethod_PreviewTextStyle-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**起始版本：** 26.1.0

**相关模块：** [InputMethod](capi-ime-kit-inputmethod.md)

**所在头文件：** [inputmethod_preview_text_style_capi.h](capi-inputmethod-preview-text-style-capi-h.md)

