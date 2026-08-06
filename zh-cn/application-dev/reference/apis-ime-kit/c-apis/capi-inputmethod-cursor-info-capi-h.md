# inputmethod_cursor_info_capi.h

## 概述

提供光标信息对象的创建、销毁与读写方法。

**库：** libohinputmethod.so

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**起始版本：** 12

**相关模块：** [InputMethod](capi-inputmethod.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [InputMethod_CursorInfo](capi-inputmethod-inputmethod-cursorinfo.md) | InputMethod_CursorInfo | InputMethod_CursorInfo是光标信息的不透明类型（opaque type），用于描述文本输入时光标在物理屏幕上的位置和尺寸，包括光标的水平坐标（left）、垂直坐标（top）、宽度（width）和高度（height）。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [InputMethod_CursorInfo *OH_CursorInfo_Create(double left, double top, double width, double height)](#oh_cursorinfo_create) | 创建一个新的[InputMethod_CursorInfo](capi-inputmethod-inputmethod-cursorinfo.md)实例，初始化光标的位置和尺寸信息。 |
| [void OH_CursorInfo_Destroy(InputMethod_CursorInfo *cursorInfo)](#oh_cursorinfo_destroy) | 销毁一个[InputMethod_CursorInfo](capi-inputmethod-inputmethod-cursorinfo.md)实例，释放由Create函数分配的内存资源。 |
| [InputMethod_ErrorCode OH_CursorInfo_SetRect(InputMethod_CursorInfo *cursorInfo, double left, double top, double width, double height)](#oh_cursorinfo_setrect) | 设置光标信息内容，更新光标的位置和尺寸。适用于在已有的CursorInfo实例上修改光标信息，无需重新创建实例。 |
| [InputMethod_ErrorCode OH_CursorInfo_GetRect(InputMethod_CursorInfo *cursorInfo, double *left, double *top, double *width, double *height)](#oh_cursorinfo_getrect) | 获取光标信息内容，读取光标的位置和尺寸。 |

## 函数说明

### OH_CursorInfo_Create()

```c
InputMethod_CursorInfo *OH_CursorInfo_Create(double left, double top, double width, double height)
```

**描述**

创建一个新的[InputMethod_CursorInfo](capi-inputmethod-inputmethod-cursorinfo.md)实例，初始化光标的位置和尺寸信息。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| double left | 输入参数，光标靠左点相对于物理屏幕左侧的距离的绝对值。<br>*含义/功能：** 定义光标矩形区域的左边界在物理屏幕上的水平位置。<br>*使用场景：** 标识光标在屏幕上的水平起始位置，输入法据此定位光标区域。<br>*使用后效果：** 输入法根据left值确定光标的水平位置，实现键盘面板的光标跟随效果。<br>*参数单位：** px（物理像素）。<br>*取值范围：** ≥0。<br>*取值原则：** 必须为物理屏幕的绝对坐标值，不可使用相对坐标（如相对于父组件或窗口的坐标）。在多窗口场景下，仍需使用物理屏幕绝对坐标。<br>*生效机制：** 输入法服务将根据此值计算光标在屏幕上的实际位置。 |
| double top | 输入参数，光标顶点与物理屏幕上侧距离的绝对值。<br>*含义/功能：** 定义光标矩形区域的顶边界在物理屏幕上的垂直位置。<br>*使用场景：** 标识光标在屏幕上的垂直起始位置。<br>*使用后效果：** 输入法根据top值确定光标的垂直位置，用于键盘避让计算和候选词定位。<br>*参数单位：** px（物理像素）。<br>*取值范围：** ≥0。<br>*取值原则：** 必须为物理屏幕的绝对坐标值，不可使用相对坐标。 |
| double width | 输入参数，光标的宽度。<br>*含义/功能：** 定义光标矩形区域的宽度。<br>*使用场景：** 描述光标的水平尺寸，输入法据此判断光标区域大小。<br>*使用后效果：** 输入法根据光标宽度调整候选词区域的定位。<br>*参数单位：** px（物理像素）。<br>*取值范围：** ≥0。<br>*取值原则：** 通常设置为光标的实际显示宽度，单字符光标宽度通常为1-2px，选区光标宽度为选区文本的宽度。 |
| double height | 输入参数，光标的高度。<br>*含义/功能：** 定义光标矩形区域的高度。<br>*使用场景：** 描述光标的垂直尺寸，输入法据此判断光标区域大小和计算避让区域。<br>*使用后效果：** 输入法根据光标高度调整键盘面板的避让区域。<br>*参数单位：** px（物理像素）。<br>*取值范围：** ≥0。<br>*取值原则：** 通常设置为光标的实际显示高度，与文本行高一致。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_CursorInfo *](capi-inputmethod-inputmethod-cursorinfo.md) | 返回指针类型。<br>     <br>创建成功： 返回一个指向新创建的InputMethod_CursorInfo实例的指针，该指针有效且可用于后续操作。<br>     <br>创建失败： 返回NULL，可能的失败原因包括应用程序的地址空间耗尽（内存不足）。<br>     <br>NULL判断： 调用者必须在使用返回值前检查是否为NULL，若为NULL则不可使用该指针，应排查内存状况或稍后重试。<br>     <br>内存管理： 返回的指针由Create函数内部分配内存，调用者需通过OH_CursorInfo_Destroy释放，不可使用free()或其他方式释放。 |

### OH_CursorInfo_Destroy()

```c
void OH_CursorInfo_Destroy(InputMethod_CursorInfo *cursorInfo)
```

**描述**

销毁一个[InputMethod_CursorInfo](capi-inputmethod-inputmethod-cursorinfo.md)实例，释放由Create函数分配的内存资源。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [InputMethod_CursorInfo](capi-inputmethod-inputmethod-cursorinfo.md) *cursorInfo | 输入指针，表示指向即将被销毁的InputMethod_CursorInfo实例的指针。<br>*含义/功能：** 指定要销毁的CursorInfo实例，Destroy将释放该实例占用的内存资源。<br>*使用场景：** 在CursorInfo不再需要时调用，典型时机为NotifyCursorUpdate调用完成后或应用退出时。<br>*使用后效果：** cursorInfo指向的内存被释放，该指针不再有效。<br>*NULL指针处理：** 若cursorInfo为NULL，Destroy函数不做任何操作（安全处理），不会导致崩溃。但建议调用者避免传入NULL。<br>*内存释放责任：** 由调用者负责在适当时机调用Destroy释放内存。 |

### OH_CursorInfo_SetRect()

```c
InputMethod_ErrorCode OH_CursorInfo_SetRect(InputMethod_CursorInfo *cursorInfo, double left, double top, double width, double height)
```

**描述**

设置光标信息内容，更新光标的位置和尺寸。适用于在已有的CursorInfo实例上修改光标信息，无需重新创建实例。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [InputMethod_CursorInfo](capi-inputmethod-inputmethod-cursorinfo.md) *cursorInfo | 输入指针，表示指向InputMethod_CursorInfo实例的指针。<br>*含义/功能：** 指定要修改的CursorInfo实例。<br>*NULL指针处理：** 不可为NULL，传入NULL将返回IME_ERR_NULL_POINTER。<br>*前提条件：** 必须通过OH_CursorInfo_Create创建的有效实例。 |
| double left | 输入参数，光标靠左点与物理屏幕左侧距离的绝对值。<br>*含义/功能：** 定义光标矩形区域的左边界在物理屏幕上的水平位置。<br>*参数单位：** px（物理像素）。<br>*取值范围：** ≥0。<br>*取值原则：** 必须为物理屏幕的绝对坐标值，不可使用相对坐标。<br>*生效机制：** 设置后覆盖原有的left值，下次GetRect将返回新值。 |
| double top | 输入参数，光标顶点与物理屏幕上侧距离的绝对值。<br>*含义/功能：** 定义光标矩形区域的顶边界在物理屏幕上的垂直位置。<br>*参数单位：** px（物理像素）。<br>*取值范围：** ≥0。<br>*取值原则：** 必须为物理屏幕的绝对坐标值，不可使用相对坐标。 |
| double width | 输入参数，光标的宽度。<br>*参数单位：** px（物理像素）。<br>*取值范围：** ≥0。 |
| double height | 输入参数，光标的高度。<br>*参数单位：** px（物理像素）。<br>*取值范围：** ≥0。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | 返回一个特定的错误码。<br>     <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 表示成功。光标信息已更新。<br>     <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 非预期的空指针。cursorInfo为NULL时返回，调用前需确保cursorInfo为有效指针。<br>     <br>错误处理建议： 若返回IME_ERR_NULL_POINTER，检查cursorInfo是否为有效指针。具体错误码可以参考[InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode)。 |

### OH_CursorInfo_GetRect()

```c
InputMethod_ErrorCode OH_CursorInfo_GetRect(InputMethod_CursorInfo *cursorInfo, double *left, double *top, double *width, double *height)
```

**描述**

获取光标信息内容，读取光标的位置和尺寸。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [InputMethod_CursorInfo](capi-inputmethod-inputmethod-cursorinfo.md) *cursorInfo | 输入指针，表示指向InputMethod_CursorInfo实例的指针。<br>*含义/功能：** 指定要读取的CursorInfo实例。<br>*NULL指针处理：** 不可为NULL，传入NULL将返回IME_ERR_NULL_POINTER。<br>*前提条件：** 必须通过OH_CursorInfo_Create创建的有效实例。 |
| double *left | 输出指针，靠左点与物理屏幕左侧距离的绝对值。<br>*含义/功能：** 接收光标左边界的水平坐标值。<br>*参数单位：** px（物理像素）。<br>*输出值范围：** ≥0。<br>*NULL指针处理：** 不可为NULL，传入NULL将返回IME_ERR_NULL_POINTER。<br>*内存分配责任：** 由调用者分配double变量的内存，GetRect仅写入值，不分配内存。 |
| double *top | 输出指针，顶点与物理屏幕上侧距离的绝对值。<br>*含义/功能：** 接收光标顶边界的垂直坐标值。<br>*参数单位：** px（物理像素）。<br>*输出值范围：** ≥0。<br>*NULL指针处理：** 不可为NULL。<br>*内存分配责任：** 由调用者分配double变量的内存。 |
| double *width | 输出指针，光标的宽度。<br>*含义/功能：** 接收光标宽度值。<br>*参数单位：** px（物理像素）。<br>*输出值范围：** ≥0。<br>*NULL指针处理：** 不可为NULL。<br>*内存分配责任：** 由调用者分配double变量的内存。 |
| double *height | 输出指针，光标的高度。<br>*含义/功能：** 接收光标高度值。<br>*参数单位：** px（物理像素）。<br>*输出值范围：** ≥0。<br>*NULL指针处理：** 不可为NULL。<br>*内存分配责任：** 由调用者分配double变量的内存。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | 返回一个特定的错误码。<br>     <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 表示成功。left、top、width、height已被赋值为正确的光标信息。<br>     <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 非预期的空指针。cursorInfo、left、top、width或height为NULL时返回，调用前需确保所有参数均为有效指针。<br>     <br>错误处理建议： 若返回IME_ERR_NULL_POINTER，检查所有参数是否为有效指针；若返回IME_ERR_OK，四个输出参数即为正确的光标信息值。具体错误码可以参考<br>     [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode)。 |


