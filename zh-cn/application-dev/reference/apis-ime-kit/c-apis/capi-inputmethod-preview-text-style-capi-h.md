# inputmethod_preview_text_style_capi.h

## 概述

预上屏文本样式的头文件，提供PreviewTextStyle实例的创建、销毁与属性读写方法。PreviewTextStyle描述预上屏文本的下划线 样式和颜色，用于输入法设置带样式的预上屏文本时传递样式信息。Create/Destroy必须配对。 <br> <br>功能：创建和管理OH_InputMethod_PreviewTextStyle实例，用于描述预上屏文本的下划线样式（无下划线/实线/波浪线/虚线）和颜色 信息。颜色格式为0xRRGGBB，透明度通道（AA）无效，将被编辑器忽略。 <br> <br>使用场景：当输入法应用通过SetPreviewTextWithStyleFunc回调设置带样式的预上屏文本时，系统将构造PreviewTextStyle对象 并传递给应用，应用通过Get方法读取样式信息进行渲染。

**引用文件：** <inputmethod/inputmethod_preview_text_style_capi.h>

**库：** libohinputmethod.so

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**起始版本：** 26.1.0

**相关模块：** [InputMethod](capi-ime-kit-inputmethod.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md) | OH_InputMethod_PreviewTextStyle | OH_InputMethod_PreviewTextStyle是预上屏文本样式的不透明类型（opaque type），用于描述预上屏文本的下划线样式和颜色信息。 调用者不可直接访问其内部成员，仅可通过本头文件提供的函数接口进行操作。 <br> <br>用途：为输入法设置带样式的预上屏文本提供样式描述。包含以下属性： <br>- 下划线样式（underlineStyle）：枚举值，取值为[OH_InputMethod_UnderlineStyle](capi-inputmethod-types-capi-h.md#oh_inputmethod_underlinestyle)，默认值为 [OH_INPUTMETHOD_UNDERLINE_STYLE_NONE](capi-inputmethod-types-capi-h.md#oh_inputmethod_underlinestyle)。 <br>- 下划线颜色（underlineColor）：格式为0xRRGGBB，仅当hasUnderlineColor为true时有效。透明度通道（AA）无效，将被 编辑器忽略。 <br>- 是否显式设置颜色（hasUnderlineColor）：false表示跟随应用主题色。 <br> <br>生命周期管理： <br>- 创建方式：通过[OH_InputMethod_PreviewTextStyle_Create](#oh_inputmethod_previewtextstyle_create)函数创建，返回一个 新的OH_InputMethod_PreviewTextStyle实例指针。创建失败时返回NULL，可能原因为内存不足。 <br>- 销毁方式：通过[OH_InputMethod_PreviewTextStyle_Destroy](#oh_inputmethod_previewtextstyle_destroy)函数销毁，传入 要销毁的实例指针。销毁后指针不可再使用，建议将指针设置为NULL避免误用。 <br>- 配对关系：OH_InputMethod_PreviewTextStyle_Create与OH_InputMethod_PreviewTextStyle_Destroy必须配对使用，创建的对象 必须最终通过Destroy释放，否则会导致内存泄漏。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_InputMethod_PreviewTextStyle *OH_InputMethod_PreviewTextStyle_Create(void)](#oh_inputmethod_previewtextstyle_create) | 创建一个新的[OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md)实例。默认下划线样式为 [OH_INPUTMETHOD_UNDERLINE_STYLE_NONE](capi-inputmethod-types-capi-h.md#oh_inputmethod_underlinestyle)，默认下划线颜色为0，hasUnderlineColor为false。 <br> <br>使用场景：当需要构造预上屏文本样式对象时调用此函数。 <br> <br>生命周期管理：返回的对象必须通过[OH_InputMethod_PreviewTextStyle_Destroy](#oh_inputmethod_previewtextstyle_destroy) 销毁，Create与Destroy必须配对使用。未销毁会导致内存泄漏。 |
| [void OH_InputMethod_PreviewTextStyle_Destroy(OH_InputMethod_PreviewTextStyle *style)](#oh_inputmethod_previewtextstyle_destroy) | 销毁一个[OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md)实例。销毁后style指针不可再使用，建议将指针设置为NULL避免误用。 <br> <br>使用场景：当不再需要PreviewTextStyle实例时调用此函数释放内存。 <br> <br>生命周期管理：传入NULL时函数不做任何处理，不会导致崩溃。 |
| [InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_SetUnderlineStyle(OH_InputMethod_PreviewTextStyle *style, OH_InputMethod_UnderlineStyle underlineStyle)](#oh_inputmethod_previewtextstyle_setunderlinestyle) | 设置预上屏文本的下划线样式。 |
| [InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_GetUnderlineStyle(OH_InputMethod_PreviewTextStyle *style, OH_InputMethod_UnderlineStyle *underlineStyle)](#oh_inputmethod_previewtextstyle_getunderlinestyle) | 获取预上屏文本的下划线样式。 |
| [InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_SetUnderlineColor(OH_InputMethod_PreviewTextStyle *style, uint32_t underlineColor)](#oh_inputmethod_previewtextstyle_setunderlinecolor) | 设置预上屏文本的下划线颜色。颜色格式为0xRRGGBB，透明度通道（AA）无效，将被编辑器忽略。 调用此函数后，下划线颜色将被标记为已显式指定；之后调用[OH_InputMethod_PreviewTextStyle_HasUnderlineColor](capi-inputmethod-preview-text-style-capi-h.md#oh_inputmethod_previewtextstyle_hasunderlinecolor)时，其hasUnderlineColor输出参数将为true。 |
| [InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_GetUnderlineColor(OH_InputMethod_PreviewTextStyle *style, uint32_t *underlineColor)](#oh_inputmethod_previewtextstyle_getunderlinecolor) | 获取预上屏文本的下划线颜色。 |
| [InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_HasUnderlineColor(OH_InputMethod_PreviewTextStyle *style, bool *hasUnderlineColor)](#oh_inputmethod_previewtextstyle_hasunderlinecolor) | 从[OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md)中获取是否设置了下划线颜色。<br> 结果由是否调用过[OH_InputMethod_PreviewTextStyle_SetUnderlineColor](capi-inputmethod-preview-text-style-capi-h.md#oh_inputmethod_previewtextstyle_setunderlinecolor)决定。若已调用过则hasUnderlineColor输出true，否则输出false。 |

## 函数说明

### OH_InputMethod_PreviewTextStyle_Create()

```c
OH_InputMethod_PreviewTextStyle *OH_InputMethod_PreviewTextStyle_Create(void)
```

**描述：**

创建一个新的[OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md)实例。默认下划线样式为 [OH_INPUTMETHOD_UNDERLINE_STYLE_NONE](capi-inputmethod-types-capi-h.md#oh_inputmethod_underlinestyle)，默认下划线颜色为0，hasUnderlineColor为false。 <br> <br>使用场景：当需要构造预上屏文本样式对象时调用此函数。 <br> <br>生命周期管理：返回的对象必须通过[OH_InputMethod_PreviewTextStyle_Destroy](#oh_inputmethod_previewtextstyle_destroy) 销毁，Create与Destroy必须配对使用。未销毁会导致内存泄漏。

<!--Device-OH_InputMethod_PreviewTextStyle *OH_InputMethod_PreviewTextStyle_Create(void)--><!--Device-OH_InputMethod_PreviewTextStyle *OH_InputMethod_PreviewTextStyle_Create(void)-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**起始版本：** 26.1.0

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_InputMethod_PreviewTextStyle *](capi-inputmethod-oh-inputmethod-previewtextstyle.md) | 如果创建成功，返回一个指向新创建的[OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md)实例的指针。如果创建失败，返回NULL，可能的失败原因有内存不足。 |

### OH_InputMethod_PreviewTextStyle_Destroy()

```c
void OH_InputMethod_PreviewTextStyle_Destroy(OH_InputMethod_PreviewTextStyle *style)
```

**描述：**

销毁一个[OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md)实例。销毁后style指针不可再使用，建议将指针设置为NULL避免误用。 <br> <br>使用场景：当不再需要PreviewTextStyle实例时调用此函数释放内存。 <br> <br>生命周期管理：传入NULL时函数不做任何处理，不会导致崩溃。

<!--Device-void OH_InputMethod_PreviewTextStyle_Destroy(OH_InputMethod_PreviewTextStyle *style)--><!--Device-void OH_InputMethod_PreviewTextStyle_Destroy(OH_InputMethod_PreviewTextStyle *style)-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md) *style | [in] 输入指针，表示指向即将被销毁的[OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md)实例的指针。若传入NULL，函数不做任何处理。 |

### OH_InputMethod_PreviewTextStyle_SetUnderlineStyle()

```c
InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_SetUnderlineStyle(OH_InputMethod_PreviewTextStyle *style, OH_InputMethod_UnderlineStyle underlineStyle)
```

**描述：**

设置预上屏文本的下划线样式。

<!--Device-InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_SetUnderlineStyle(OH_InputMethod_PreviewTextStyle *style, OH_InputMethod_UnderlineStyle underlineStyle)--><!--Device-InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_SetUnderlineStyle(OH_InputMethod_PreviewTextStyle *style, OH_InputMethod_UnderlineStyle underlineStyle)-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md) *style | [in] 输入指针，指向即将被设置的[OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md)实例的指针。不可为NULL。 |
| [OH_InputMethod_UnderlineStyle](capi-inputmethod-types-capi-h.md#oh_inputmethod_underlinestyle) underlineStyle | [in] 输入参数，下划线样式，参见[OH_InputMethod_UnderlineStyle](capi-inputmethod-types-capi-h.md#oh_inputmethod_underlinestyle)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | 返回一个特定的错误码。<ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 表示成功。</li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 非预期的空指针。</li> <li>具体错误码可以参考[InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode)。</li> </ul> |

### OH_InputMethod_PreviewTextStyle_GetUnderlineStyle()

```c
InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_GetUnderlineStyle(OH_InputMethod_PreviewTextStyle *style, OH_InputMethod_UnderlineStyle *underlineStyle)
```

**描述：**

获取预上屏文本的下划线样式。

<!--Device-InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_GetUnderlineStyle(OH_InputMethod_PreviewTextStyle *style, OH_InputMethod_UnderlineStyle *underlineStyle)--><!--Device-InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_GetUnderlineStyle(OH_InputMethod_PreviewTextStyle *style, OH_InputMethod_UnderlineStyle *underlineStyle)-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md) *style | [in] 输入指针，指向被读取的[OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md)实例的指针。不可为NULL。 |
| [OH_InputMethod_UnderlineStyle](capi-inputmethod-types-capi-h.md#oh_inputmethod_underlinestyle) *underlineStyle | [out] 输出指针，用于返回下划线样式。不可为NULL。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | 返回一个特定的错误码。<ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 表示成功。</li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 非预期的空指针。</li> <li>具体错误码可以参考[InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode)。</li> </ul> |

### OH_InputMethod_PreviewTextStyle_SetUnderlineColor()

```c
InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_SetUnderlineColor(OH_InputMethod_PreviewTextStyle *style, uint32_t underlineColor)
```

**描述：**

设置预上屏文本的下划线颜色。颜色格式为0xRRGGBB，透明度通道（AA）无效，将被编辑器忽略。 调用此函数后，下划线颜色将被标记为已显式指定；之后调用[OH_InputMethod_PreviewTextStyle_HasUnderlineColor](capi-inputmethod-preview-text-style-capi-h.md#oh_inputmethod_previewtextstyle_hasunderlinecolor)时，其hasUnderlineColor输出参数将为true。

<!--Device-InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_SetUnderlineColor(OH_InputMethod_PreviewTextStyle *style, uint32_t underlineColor)--><!--Device-InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_SetUnderlineColor(OH_InputMethod_PreviewTextStyle *style, uint32_t underlineColor)-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md) *style | [in] 输入指针，指向即将被设置的[OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md)实例的指针。不可为NULL。 |
| uint32_t underlineColor | [in] 输入参数，下划线颜色，格式为0xRRGGBB。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | 返回一个特定的错误码。<ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 表示成功。</li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 非预期的空指针。</li> <li>具体错误码可以参考[InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode)。</li> </ul> |

### OH_InputMethod_PreviewTextStyle_GetUnderlineColor()

```c
InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_GetUnderlineColor(OH_InputMethod_PreviewTextStyle *style, uint32_t *underlineColor)
```

**描述：**

获取预上屏文本的下划线颜色。

<!--Device-InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_GetUnderlineColor(OH_InputMethod_PreviewTextStyle *style, uint32_t *underlineColor)--><!--Device-InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_GetUnderlineColor(OH_InputMethod_PreviewTextStyle *style, uint32_t *underlineColor)-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md) *style | [in] 输入指针，指向被读取的[OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md)实例的指针。不可为NULL。 |
| uint32_t *underlineColor | [out] 输出指针，用于返回下划线颜色，格式为0xRRGGBB。不可为NULL。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | 返回一个特定的错误码。<ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 表示成功。</li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 非预期的空指针。</li> <li>具体错误码可以参考[InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode)。</li> </ul> |

### OH_InputMethod_PreviewTextStyle_HasUnderlineColor()

```c
InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_HasUnderlineColor(OH_InputMethod_PreviewTextStyle *style, bool *hasUnderlineColor)
```

**描述：**

从[OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md)中获取是否设置了下划线颜色。<br> 结果由是否调用过[OH_InputMethod_PreviewTextStyle_SetUnderlineColor](capi-inputmethod-preview-text-style-capi-h.md#oh_inputmethod_previewtextstyle_setunderlinecolor)决定。若已调用过则hasUnderlineColor输出true，否则输出false。

<!--Device-InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_HasUnderlineColor(OH_InputMethod_PreviewTextStyle *style, bool *hasUnderlineColor)--><!--Device-InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_HasUnderlineColor(OH_InputMethod_PreviewTextStyle *style, bool *hasUnderlineColor)-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md) *style | [in] 输入指针，指向被读取的[OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md)实例的指针。不可为NULL。 |
| bool *hasUnderlineColor | [out] 输出指针，用于返回是否设置了下划线颜色。不可为NULL。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | 返回一个特定的错误码。<ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 表示成功。</li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 非预期的空指针。</li> <li>具体错误码可以参考[InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode)。</li> </ul> |


