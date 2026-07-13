# inputmethod_text_avoid_info_capi.h

## 概述

提供输入框避让信息对象的创建、销毁与读写方法，用于在软键盘弹起时动态调整输入框的位置，避免遮挡输入内容。

**库：** libohinputmethod.so

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**起始版本：** 12

**相关模块：** [InputMethod](capi-inputmethod.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) | InputMethod_TextAvoidInfo | 输入框避让信息结构体，描述编辑框在物理屏幕上的位置和高度信息。输入法框架根据TextAvoidInfo中的positionY和height计算避让区域，使编辑框在软键盘弹起时能够自动上移或调整布局，确保输入区域不被键盘遮挡，保证用户可见并可操作输入内容。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [InputMethod_TextAvoidInfo *OH_TextAvoidInfo_Create(double positionY, double height)](#oh_textavoidinfo_create) | 创建一个新的[InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md)实例。该函数根据指定的Y坐标和高度创建一个避让信息对象，用于描述编辑框在物理屏幕上的位置和尺寸。 |
| [void OH_TextAvoidInfo_Destroy(InputMethod_TextAvoidInfo *info)](#oh_textavoidinfo_destroy) | 销毁一个[InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md)实例，释放其占用的内存资源。 |
| [InputMethod_ErrorCode OH_TextAvoidInfo_SetPositionY(InputMethod_TextAvoidInfo *info, double positionY)](#oh_textavoidinfo_setpositiony) | 设置[InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md)中的Y坐标值。Y坐标值表示输入框顶点与物理屏幕上侧距离的绝对值。 |
| [InputMethod_ErrorCode OH_TextAvoidInfo_SetHeight(InputMethod_TextAvoidInfo *info, double height)](#oh_textavoidinfo_setheight) | 设置[InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md)中的高度值。高度值表示编辑框在屏幕上占据的垂直像素尺寸。 |
| [InputMethod_ErrorCode OH_TextAvoidInfo_GetPositionY(InputMethod_TextAvoidInfo *info, double *positionY)](#oh_textavoidinfo_getpositiony) | 从[InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md)获取Y坐标值。Y坐标值即输入框顶点与物理屏幕上侧距离的绝对值。 |
| [InputMethod_ErrorCode OH_TextAvoidInfo_GetHeight(InputMethod_TextAvoidInfo *info, double *height)](#oh_textavoidinfo_getheight) | 从[InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md)获取高度值。高度值表示编辑框在屏幕上占据的垂直像素尺寸。 |

## 函数说明

### OH_TextAvoidInfo_Create()

```c
InputMethod_TextAvoidInfo *OH_TextAvoidInfo_Create(double positionY, double height)
```

**描述**

创建一个新的[InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md)实例。该函数根据指定的Y坐标和高度创建一个避让信息对象，用于描述编辑框在物理屏幕上的位置和尺寸。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| double positionY | 表示输入框位置的Y坐标值，单位px。Y坐标值即输入框顶点与物理屏幕上侧距离的绝对值，单位px。取值范围≥0，建议使用物理屏幕的实际坐标值。若传入负值，创建仍会成功，但该值在实际避让计算中无意义。 |
| double height | 表示输入框高度，单位px。取值范围≥0，建议使用编辑框的实际像素高度。若传入负值，创建仍会成功，但该值在实际避让计算中无意义。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_TextAvoidInfo *](capi-inputmethod-inputmethod-textavoidinfo.md) | 如果创建成功，返回一个指向新创建的[InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md)实例的指针。调用方必须负责该实例的生命周期管理，使用完毕后调用<br>     [OH_TextAvoidInfo_Destroy](capi-inputmethod-text-avoid-info-capi-h.md#oh_textavoidinfo_destroy)销毁实例以释放内存。<br>     <br>如果创建失败，返回NULL。可能的失败原因：内存分配不足（应用地址空间满）。对NULL指针的后续操作（如Set/Get函数）将返回IME_ERR_NULL_POINTER。 |

### OH_TextAvoidInfo_Destroy()

```c
void OH_TextAvoidInfo_Destroy(InputMethod_TextAvoidInfo *info)
```

**描述**

销毁一个[InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md)实例，释放其占用的内存资源。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) *info | 表示指向即将被销毁的[InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md)实例的指针。若传入NULL，函数不执行任何操作，安全返回。建议销毁后将指针置为NULL以避免误用悬空指针。 |

### OH_TextAvoidInfo_SetPositionY()

```c
InputMethod_ErrorCode OH_TextAvoidInfo_SetPositionY(InputMethod_TextAvoidInfo *info, double positionY)
```

**描述**

设置[InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md)中的Y坐标值。Y坐标值表示输入框顶点与物理屏幕上侧距离的绝对值。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) *info | 指向即将被设置值的[InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md)实例的指针。不允许传入NULL指针，否则返回IME_ERR_NULL_POINTER。 |
| double positionY | Y坐标值，即输入框顶点与物理屏幕上侧距离的绝对值，单位px。取值范围≥0，建议使用物理屏幕的实际坐标值。传入负值不会报错，但在实际避让计算中无意义。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | 返回一个特定的错误码。<br>     <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 表示成功。<br>     <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 非预期的空指针，info参数为NULL。<br>     <br>具体错误码可以参考 [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode)。 |

### OH_TextAvoidInfo_SetHeight()

```c
InputMethod_ErrorCode OH_TextAvoidInfo_SetHeight(InputMethod_TextAvoidInfo *info, double height)
```

**描述**

设置[InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md)中的高度值。高度值表示编辑框在屏幕上占据的垂直像素尺寸。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) *info | 指向即将被设置值的[InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md)实例的指针。不允许传入NULL指针，否则返回IME_ERR_NULL_POINTER。 |
| double height | 高度值，单位px。取值范围≥0，建议使用编辑框的实际像素高度。传入负值不会报错，但在实际避让计算中无意义。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | 返回一个特定的错误码。<br>     <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 表示成功。<br>     <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 非预期的空指针，info参数为NULL。<br>     <br>具体错误码可以参考 [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode)。 |

### OH_TextAvoidInfo_GetPositionY()

```c
InputMethod_ErrorCode OH_TextAvoidInfo_GetPositionY(InputMethod_TextAvoidInfo *info, double *positionY)
```

**描述**

从[InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md)获取Y坐标值。Y坐标值即输入框顶点与物理屏幕上侧距离的绝对值。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) *info | 指向即将被获取值的[InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md)实例的指针。不允许传入NULL指针，否则返回IME_ERR_NULL_POINTER。 |
| double *positionY | 输出参数，用于接收Y坐标值，即输入框顶点与物理屏幕上侧距离的绝对值，单位px。此参数为输出指针，调用方需分配double类型变量的内存并将其地址传入。不允许传入NULL指针，否则返回IME_ERR_NULL_POINTER。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | 返回一个特定的错误码。<br>     <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 表示成功，positionY指针指向的内存已被写入Y坐标值。<br>     <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 非预期的空指针，info或positionY参数为NULL。<br>     <br>具体错误码可以参考 [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode)。 |

### OH_TextAvoidInfo_GetHeight()

```c
InputMethod_ErrorCode OH_TextAvoidInfo_GetHeight(InputMethod_TextAvoidInfo *info, double *height)
```

**描述**

从[InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md)获取高度值。高度值表示编辑框在屏幕上占据的垂直像素尺寸。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) *info | 指向即将被获取值的[InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md)实例的指针。不允许传入NULL指针，否则返回IME_ERR_NULL_POINTER。 |
| double *height | 输出参数，用于接收输入框高度，单位px。此参数为输出指针，调用方需分配double类型变量的内存并将其地址传入。不允许传入NULL指针，否则返回IME_ERR_NULL_POINTER。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | 返回一个特定的错误码。<br>     <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 表示成功，height指针指向的内存已被写入高度值。<br>     <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 非预期的空指针，info或height参数为NULL。<br>     <br>具体错误码可以参考 [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode)。 |


