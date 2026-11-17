# inputmethod_preview_text_style_capi.h
<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @codexu62-->
<!--Designer: @zhaolinglan-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->

## 概述

提供预上屏样式对象的创建、销毁以及属性的访问接口。对象为不透明类型，应用不能直接读写成员。

**引用文件：** \<inputmethod/inputmethod_preview_text_style_capi.h>

**库：** libohinputmethod.so

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**起始版本：** 26.1.0

**相关模块：** [InputMethod](capi-inputmethod.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md) | OH_InputMethod_PreviewTextStyle | 预上屏样式对象。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_InputMethod_PreviewTextStyle_Create()](#oh_inputmethod_previewtextstyle_create) | 创建预上屏样式对象。 |
| [OH_InputMethod_PreviewTextStyle_Destroy()](#oh_inputmethod_previewtextstyle_destroy) | 销毁由Create创建的样式对象。 |
| [OH_InputMethod_PreviewTextStyle_SetUnderlineStyle()](#oh_inputmethod_previewtextstyle_setunderlinestyle) | 设置下划线样式。 |
| [OH_InputMethod_PreviewTextStyle_GetUnderlineStyle()](#oh_inputmethod_previewtextstyle_getunderlinestyle) | 获取下划线样式。 |
| [OH_InputMethod_PreviewTextStyle_SetUnderlineColor()](#oh_inputmethod_previewtextstyle_setunderlinecolor) | 设置下划线颜色，颜色格式为0xRRGGBB。透明度通道无效，由编辑框忽略。 |
| [OH_InputMethod_PreviewTextStyle_GetUnderlineColor()](#oh_inputmethod_previewtextstyle_getunderlinecolor) | 获取对象保存的颜色值。 |
| [OH_InputMethod_PreviewTextStyle_HasUnderlineColor()](#oh_inputmethod_previewtextstyle_hasunderlinecolor) | 查询颜色是否被显式设置。 |

## 函数说明

### OH_InputMethod_PreviewTextStyle_Create()

```c
OH_InputMethod_PreviewTextStyle *OH_InputMethod_PreviewTextStyle_Create(void)
```

**描述**

创建预上屏样式对象。默认样式为NONE，颜色为0，颜色未显式设置。

**起始版本：** 26.1.0

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md) * | 新建的样式对象。创建失败时返回NULL。 |

### OH_InputMethod_PreviewTextStyle_Destroy()

```c
void OH_InputMethod_PreviewTextStyle_Destroy(OH_InputMethod_PreviewTextStyle *style)
```

**描述**

销毁由Create创建的样式对象。传入NULL时不执行操作。释放后不得继续访问该指针。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| style | 待销毁的对象。 |

### OH_InputMethod_PreviewTextStyle_SetUnderlineStyle()

```c
InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_SetUnderlineStyle(
    OH_InputMethod_PreviewTextStyle *style, OH_InputMethod_UnderlineStyle underlineStyle)
```

**描述**

设置下划线样式。可用值见[OH_InputMethod_UnderlineStyle](capi-inputmethod-types-capi-h.md#oh_inputmethod_underlinestyle)。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| style | 样式对象，不得为NULL。 |
| underlineStyle | 下划线样式，使用枚举中定义的值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | IME_ERR_OK：成功。IME_ERR_NULL_POINTER：传入了非预期的空指针。 |

### OH_InputMethod_PreviewTextStyle_GetUnderlineStyle()

```c
InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_GetUnderlineStyle(
    OH_InputMethod_PreviewTextStyle *style, OH_InputMethod_UnderlineStyle *underlineStyle)
```

**描述**

获取下划线样式。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| style | 样式对象，不得为NULL。 |
| underlineStyle | 输出参数，存放下划线样式，不得为NULL。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | IME_ERR_OK：成功。IME_ERR_NULL_POINTER：传入了非预期的空指针。 |

### OH_InputMethod_PreviewTextStyle_SetUnderlineColor()

```c
InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_SetUnderlineColor(
    OH_InputMethod_PreviewTextStyle *style, uint32_t underlineColor)
```

**描述**

设置下划线颜色，颜色格式为0xRRGGBB。透明度通道无效，由编辑框忽略。调用成功后颜色被标记为显式设置，HasUnderlineColor输出true；颜色为0时也适用。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| style | 样式对象，不得为NULL。 |
| underlineColor | 下划线颜色。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | IME_ERR_OK：成功。IME_ERR_NULL_POINTER：传入了非预期的空指针。 |

### OH_InputMethod_PreviewTextStyle_GetUnderlineColor()

```c
InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_GetUnderlineColor(
    OH_InputMethod_PreviewTextStyle *style, uint32_t *underlineColor)
```

**描述**

获取对象保存的颜色值。颜色是否已显式设置应通过HasUnderlineColor查询，不能以颜色值是否为0判断。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| style | 样式对象，不得为NULL。 |
| underlineColor | 输出参数，存放颜色值，不得为NULL。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | IME_ERR_OK：成功。IME_ERR_NULL_POINTER：传入了非预期的空指针。 |

### OH_InputMethod_PreviewTextStyle_HasUnderlineColor()

```c
InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_HasUnderlineColor(
    OH_InputMethod_PreviewTextStyle *style, bool *hasUnderlineColor)
```

**描述**

查询颜色是否被显式设置。Create创建的对象输出false；调用SetUnderlineColor成功后输出true。本接口仅查询，不修改颜色状态。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| style | 样式对象，不得为NULL。 |
| hasUnderlineColor | 输出参数，true表示已显式设置颜色，false表示未设置，不得为NULL。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | IME_ERR_OK：成功。IME_ERR_NULL_POINTER：传入了非预期的空指针。 |
