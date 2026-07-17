# picker.h

## 概述

为NativeNode API提供Picker节点类型定义。

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ARKUI_TextPickerRangeContent](capi-arkui-nativemodule-arkui-textpickerrangecontent.md) | ARKUI_TextPickerRangeContent | 定义单列滑动数据选择器支持的选项内容结构体，包含文本和图片资源。 |
| [ARKUI_TextPickerCascadeRangeContent](capi-arkui-nativemodule-arkui-textpickercascaderangecontent.md) | ARKUI_TextPickerCascadeRangeContent | 定义多列联动滑动数据选择器的结构体。 |
| [ArkUI_PickerIndicatorBackground](capi-arkui-nativemodule-arkui-pickerindicatorbackground.md) | ArkUI_PickerIndicatorBackground | Defines the style parameter of the background-style indicator of the selected item. |
| [ArkUI_PickerIndicatorDivider](capi-arkui-nativemodule-arkui-pickerindicatordivider.md) | ArkUI_PickerIndicatorDivider | Defines the style parameter of the divider-style indicator. |
| [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md) | ArkUI_PickerIndicatorStyle | 选中项指示器的样式。 |
| [ArkUI_TextPickerRangeContentArray](capi-arkui-nativemodule-arkui-textpickerrangecontentarray.md) | ArkUI_TextPickerRangeContentArray | 定义文本选择器的数据选择列表。 |
| [ArkUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md) | ArkUI_TextCascadePickerRangeContentArray | 定义多列联动数据选择器的数组。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_DatePickerMode](#arkui_datepickermode) | ArkUI_DatePickerMode | 定义日期选择器列显示模式的枚举值。 |
| [ArkUI_TextPickerRangeType](#arkui_textpickerrangetype) | ArkUI_TextPickerRangeType | 定义滑动选择文本选择器输入类型。 |
| [ArkUI_CalendarAlignment](#arkui_calendaralignment) | ArkUI_CalendarAlignment | 日历选择器与入口组件之间的对齐模式类型。 |
| [ArkUI_PickerIndicatorType](#arkui_pickerindicatortype) | ArkUI_PickerIndicatorType | 选择器的选中指示器类型。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [ArkUI_TextPickerRangeContentArray* OH_ArkUI_TextPickerRangeContentArray_Create(int32_t length)](#oh_arkui_textpickerrangecontentarray_create) | 创建{@link TextPickerRangeContent}数组的对象。 |
| [void OH_ArkUI_TextPickerRangeContentArray_SetIconAtIndex(ArkUI_TextPickerRangeContentArray* handle, char* icon, int32_t index)](#oh_arkui_textpickerrangecontentarray_seticonatindex) | 设置TextPickerRangeContent数组指定位置的icon数据。 |
| [void OH_ArkUI_TextPickerRangeContentArray_SetTextAtIndex(ArkUI_TextPickerRangeContentArray* handle, char* text, int32_t index)](#oh_arkui_textpickerrangecontentarray_settextatindex) | 设置TextPickerRangeContent数组指定位置的text数据。 |
| [void OH_ArkUI_TextPickerRangeContentArray_Destroy(ArkUI_TextPickerRangeContentArray* handle)](#oh_arkui_textpickerrangecontentarray_destroy) | 删除TextPickerRangeContent数组对象。 |
| [ArkUI_TextCascadePickerRangeContentArray* OH_ArkUI_TextCascadePickerRangeContentArray_Create(int32_t length)](#oh_arkui_textcascadepickerrangecontentarray_create) | 创建{@link TextCascadePickerRangeContent}数组对象。 |
| [void OH_ArkUI_TextCascadePickerRangeContentArray_SetTextAtIndex(ArkUI_TextCascadePickerRangeContentArray* handle, char* text, int32_t index)](#oh_arkui_textcascadepickerrangecontentarray_settextatindex) | 设置TextCascadePickerRangeContent数组指定位置的text数据。 |
| [void OH_ArkUI_TextCascadePickerRangeContentArray_SetChildAtIndex(ArkUI_TextCascadePickerRangeContentArray* handle, ArkUI_TextCascadePickerRangeContentArray* child, int32_t index)](#oh_arkui_textcascadepickerrangecontentarray_setchildatindex) | 设置TextCascadePickerRangeContent数组指定位置的child数据。 |
| [void OH_ArkUI_TextCascadePickerRangeContentArray_Destroy(ArkUI_TextCascadePickerRangeContentArray* handle)](#oh_arkui_textcascadepickerrangecontentarray_destroy) | 删除TextCascadePickerRangeContent数组对象。 |
| [ArkUI_PickerIndicatorStyle* OH_ArkUI_PickerIndicatorStyle_Create(ArkUI_PickerIndicatorType type)](#oh_arkui_pickerindicatorstyle_create) | 创建选中项指示器的样式实例。 |
| [void OH_ArkUI_PickerIndicatorStyle_Dispose(ArkUI_PickerIndicatorStyle* style)](#oh_arkui_pickerindicatorstyle_dispose) | Disposes of the style instance of the selected item indicator. |

## 枚举类型说明

### ArkUI_DatePickerMode

```c
enum ArkUI_DatePickerMode
```

**描述**

定义日期选择器列显示模式的枚举值。

**起始版本：** 18

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_DATEPICKER_MODE_DATE = 0 |  |
| ARKUI_DATEPICKER_YEAR_AND_MONTH = 1 |  |
| ARKUI_DATEPICKER_MONTH_AND_DAY = 2 |  |

### ArkUI_TextPickerRangeType

```c
enum ArkUI_TextPickerRangeType
```

**描述**

定义滑动选择文本选择器输入类型。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_TEXTPICKER_RANGETYPE_SINGLE = 0 |  |
| ARKUI_TEXTPICKER_RANGETYPE_MULTI = 1 |  |
| ARKUI_TEXTPICKER_RANGETYPE_RANGE_CONTENT = 2 |  |
| ARKUI_TEXTPICKER_RANGETYPE_CASCADE_RANGE_CONTENT = 3 |  |

### ArkUI_CalendarAlignment

```c
enum ArkUI_CalendarAlignment
```

**描述**

日历选择器与入口组件之间的对齐模式类型。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_CALENDAR_ALIGNMENT_START = 0 |  |
| ARKUI_CALENDAR_ALIGNMENT_CENTER = 1 |  |
| ARKUI_CALENDAR_ALIGNMENT_END = 2 |  |

### ArkUI_PickerIndicatorType

```c
enum ArkUI_PickerIndicatorType
```

**描述**

选择器的选中指示器类型。

**起始版本：** 23

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_PICKER_INDICATOR_BACKGROUND = 0 |  |
| ARKUI_PICKER_INDICATOR_DIVIDER = 1 |  |


## 函数说明

### OH_ArkUI_TextPickerRangeContentArray_Create()

```c
ArkUI_TextPickerRangeContentArray* OH_ArkUI_TextPickerRangeContentArray_Create(int32_t length)
```

**描述**

创建{@link TextPickerRangeContent}数组的对象。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t length | 指定TextPickerRangeContent数组的长度。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_TextPickerRangeContentArray*](capi-arkui-nativemodule-arkui-textpickerrangecontentarray.md) | 返回指向TextPickerRangeContent空数组的指针。 |

### OH_ArkUI_TextPickerRangeContentArray_SetIconAtIndex()

```c
void OH_ArkUI_TextPickerRangeContentArray_SetIconAtIndex(ArkUI_TextPickerRangeContentArray* handle, char* icon, int32_t index)
```

**描述**

设置TextPickerRangeContent数组指定位置的icon数据。

>**说明：** 
>If an icon was already set at <b>index</b>, the previous buffer is released before assigning the new value.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextPickerRangeContentArray](capi-arkui-nativemodule-arkui-textpickerrangecontentarray.md)* handle | 指向TextPickerRangeContent数组的指针。 |
| char* icon | 图标路径。 |
| int32_t index | 数组索引，从0开始。 |

### OH_ArkUI_TextPickerRangeContentArray_SetTextAtIndex()

```c
void OH_ArkUI_TextPickerRangeContentArray_SetTextAtIndex(ArkUI_TextPickerRangeContentArray* handle, char* text, int32_t index)
```

**描述**

设置TextPickerRangeContent数组指定位置的text数据。

>**说明：** 
>If text was already set at <b>index</b>, the previous buffer is released before assigning the new value.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextPickerRangeContentArray](capi-arkui-nativemodule-arkui-textpickerrangecontentarray.md)* handle | 指向TextPickerRangeContent数组的指针。 |
| char* text | 文本内容。 |
| int32_t index | 数组位置，从0开始。 |

### OH_ArkUI_TextPickerRangeContentArray_Destroy()

```c
void OH_ArkUI_TextPickerRangeContentArray_Destroy(ArkUI_TextPickerRangeContentArray* handle)
```

**描述**

删除TextPickerRangeContent数组对象。

>**说明：** 
>After this call, <b>handle</b> must not be used. Do not pass pointers that were not returned by
 *     [OH_ArkUI_TextPickerRangeContentArray_Create](capi-picker-h.md#oh_arkui_textpickerrangecontentarray_create).

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextPickerRangeContentArray](capi-arkui-nativemodule-arkui-textpickerrangecontentarray.md)* handle | 指向TextPickerRangeContent数组的指针。 |

### OH_ArkUI_TextCascadePickerRangeContentArray_Create()

```c
ArkUI_TextCascadePickerRangeContentArray* OH_ArkUI_TextCascadePickerRangeContentArray_Create(int32_t length)
```

**描述**

创建{@link TextCascadePickerRangeContent}数组对象。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t length | 指向TextPickerRangeContent数组的长度。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_TextCascadePickerRangeContentArray*](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md) | 返回指向TextCascadePickerRangeContent空数组的指针。 |

### OH_ArkUI_TextCascadePickerRangeContentArray_SetTextAtIndex()

```c
void OH_ArkUI_TextCascadePickerRangeContentArray_SetTextAtIndex(ArkUI_TextCascadePickerRangeContentArray* handle, char* text, int32_t index)
```

**描述**

设置TextCascadePickerRangeContent数组指定位置的text数据。

>**说明：** 
>If text was already set at <b>index</b>, the previous buffer is released before assigning the new value.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md)* handle | 指向TextCascadePickerRangeContentHandle的指针。 |
| char* text | 文本内容。 |
| int32_t index | 数组位置，从0开始。 |

### OH_ArkUI_TextCascadePickerRangeContentArray_SetChildAtIndex()

```c
void OH_ArkUI_TextCascadePickerRangeContentArray_SetChildAtIndex(ArkUI_TextCascadePickerRangeContentArray* handle, ArkUI_TextCascadePickerRangeContentArray* child, int32_t index)
```

**描述**

设置TextCascadePickerRangeContent数组指定位置的child数据。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md)* handle | 指向TextCascadePickerRangeContentHandle的指针。 |
| [ArkUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md)* child | 子节点数组指针。 |
| int32_t index | 数组位置，从0开始。 |

### OH_ArkUI_TextCascadePickerRangeContentArray_Destroy()

```c
void OH_ArkUI_TextCascadePickerRangeContentArray_Destroy(ArkUI_TextCascadePickerRangeContentArray* handle)
```

**描述**

删除TextCascadePickerRangeContent数组对象。

>**说明：** 
>Do not call [OH_ArkUI_TextCascadePickerRangeContentArray_Destroy](capi-picker-h.md#oh_arkui_textcascadepickerrangecontentarray_destroy) on a <b>child</b> while
 *     it is still stored in a parent's {@code children}.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md)* handle | 指向TextCascadePickerRangeContentHandle的指针。 |

### OH_ArkUI_PickerIndicatorStyle_Create()

```c
ArkUI_PickerIndicatorStyle* OH_ArkUI_PickerIndicatorStyle_Create(ArkUI_PickerIndicatorType type)
```

**描述**

创建选中项指示器的样式实例。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_PickerIndicatorType](capi-picker-h.md#arkui_pickerindicatortype) type | 选择器选中项样式枚举类型。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_PickerIndicatorStyle*](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md) | [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md)实例。如果返回空指针，表示创建失败，失败原因可能是地址空间已满或类型不支持。 |

### OH_ArkUI_PickerIndicatorStyle_Dispose()

```c
void OH_ArkUI_PickerIndicatorStyle_Dispose(ArkUI_PickerIndicatorStyle* style)
```

**描述**

Disposes of the style instance of the selected item indicator.

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md)* style | Pointer to the [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md) instance to be disposed of. |


