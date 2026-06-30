# picker.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @luoying_ace_admin-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->

## 概述

为NativeNode API提供Picker节点类型定义。

**引用文件：** <arkui/picker.h>

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**相关示例：** <!--RP1-->[native_type_sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeType/native_type_sample)<!--RP1End-->

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ARKUI_TextPickerRangeContent](capi-arkui-nativemodule-arkui-textpickerrangecontent.md) | ARKUI_TextPickerRangeContent | 定义单列滑动数据选择器支持的图片资源结构体。 |
| [ARKUI_TextPickerCascadeRangeContent](capi-arkui-nativemodule-arkui-textpickercascaderangecontent.md) | ARKUI_TextPickerCascadeRangeContent | 定义多列联动滑动数据选择器的结构体。 |
| [ArkUI_PickerIndicatorBackground](capi-arkui-nativemodule-arkui-pickerindicatorbackground.md) | ArkUI_PickerIndicatorBackground | 背景样式指示器的样式参数。 |
| [ArkUI_PickerIndicatorDivider](capi-arkui-nativemodule-arkui-pickerindicatordivider.md) | ArkUI_PickerIndicatorDivider | 分割线样式指示器的样式参数。 |
| [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md) | ArkUI_PickerIndicatorStyle | 选中项指示器的样式。 |
| [ArkUI_TextPickerRangeContentArray](capi-arkui-nativemodule-arkui-textpickerrangecontentarray.md) | ArkUI_TextPickerRangeContentArray | 定义文本选择器的数据选择列表。 |
| [ArkUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md) | ArkUI_TextCascadePickerRangeContentArray | 定义多列联动数据选择器的列表。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_DatePickerMode](#arkui_datepickermode) | ArkUI_DatePickerMode | 定义日期选择器列显示模式的枚举值。 |
| [ArkUI_TextPickerRangeType](#arkui_textpickerrangetype) | ArkUI_TextPickerRangeType | 定义滑动选择文本选择器输入类型。 |
| [ArkUI_CalendarAlignment](#arkui_calendaralignment) | ArkUI_CalendarAlignment | 日历选择器与入口组件对齐方式。 |
| [ArkUI_PickerIndicatorType](#arkui_pickerindicatortype) | ArkUI_PickerIndicatorType | 选择器的选中指示器类型。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [ArkUI_TextPickerRangeContentArray* OH_ArkUI_TextPickerRangeContentArray_Create(int32_t length)](#oh_arkui_textpickerrangecontentarray_create) | 创建TextPickerRangeContent数组的对象。 |
| [void OH_ArkUI_TextPickerRangeContentArray_SetIconAtIndex(ArkUI_TextPickerRangeContentArray* handle, char* icon, int32_t index)](#oh_arkui_textpickerrangecontentarray_seticonatindex) | 设置TextPickerRangeContent数组指定位置的icon数据。 |
| [void OH_ArkUI_TextPickerRangeContentArray_SetTextAtIndex(ArkUI_TextPickerRangeContentArray* handle, char* text, int32_t index)](#oh_arkui_textpickerrangecontentarray_settextatindex) | 设置TextPickerRangeContent数组指定位置的text数据。 |
| [void OH_ArkUI_TextPickerRangeContentArray_Destroy(ArkUI_TextPickerRangeContentArray* handle)](#oh_arkui_textpickerrangecontentarray_destroy) | 删除TextPickerRangeContent数组对象。 |
| [ArkUI_TextCascadePickerRangeContentArray* OH_ArkUI_TextCascadePickerRangeContentArray_Create(int32_t length)](#oh_arkui_textcascadepickerrangecontentarray_create) | 创建TextCascadePickerRangeContent数组对象。 |
| [void OH_ArkUI_TextCascadePickerRangeContentArray_SetTextAtIndex (ArkUI_TextCascadePickerRangeContentArray* handle, char* text, int32_t index)](#oh_arkui_textcascadepickerrangecontentarray_settextatindex) | 设置TextCascadePickerRangeContent数组指定位置的text数据。 |
| [void OH_ArkUI_TextCascadePickerRangeContentArray_SetChildAtIndex (ArkUI_TextCascadePickerRangeContentArray* handle, ArkUI_TextCascadePickerRangeContentArray* child, int32_t index)](#oh_arkui_textcascadepickerrangecontentarray_setchildatindex) | 设置TextCascadePickerRangeContent数组指定位置的child数据。 |
| [void OH_ArkUI_TextCascadePickerRangeContentArray_Destroy (ArkUI_TextCascadePickerRangeContentArray* handle)](#oh_arkui_textcascadepickerrangecontentarray_destroy) | 删除TextCascadePickerRangeContent数组对象。 |
| [ArkUI_PickerIndicatorStyle* OH_ArkUI_PickerIndicatorStyle_Create(ArkUI_PickerIndicatorType type)](#oh_arkui_pickerindicatorstyle_create) | 创建选中项指示器的样式实例。 |
| [void  OH_ArkUI_PickerIndicatorStyle_Dispose(ArkUI_PickerIndicatorStyle* style)](#oh_arkui_pickerindicatorstyle_dispose) | 销毁选中项指示器的样式实例。 |

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
| ARKUI_DATEPICKER_MODE_DATE = 0 | 默认值。日期列显示年、月、日三列。 |
| ARKUI_DATEPICKER_YEAR_AND_MONTH = 1 | 日期列显示年、月二列。 |
| ARKUI_DATEPICKER_MONTH_AND_DAY = 2 | 日期列显示月、日二列。 |

### ArkUI_TextPickerRangeType

```c
enum ArkUI_TextPickerRangeType
```

**描述**

定义滑动选择文本选择器输入类型。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_TEXTPICKER_RANGETYPE_SINGLE = 0 | 单列数据选择器。 |
| ARKUI_TEXTPICKER_RANGETYPE_MULTI = 1 | 多列数据选择器。 |
| ARKUI_TEXTPICKER_RANGETYPE_RANGE_CONTENT = 2 | 支持图片资源的单列数据选择器。 |
| ARKUI_TEXTPICKER_RANGETYPE_CASCADE_RANGE_CONTENT = 3 | 支持联动的多列数据选择器。 |

### ArkUI_CalendarAlignment

```c
enum ArkUI_CalendarAlignment
```

**描述**

日历选择器与入口组件对齐方式。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_CALENDAR_ALIGNMENT_START = 0 | 选择器和入口组件左对齐方式。 |
| ARKUI_CALENDAR_ALIGNMENT_CENTER = 1 | 选择器和入口组件居中对齐方式。 |
| ARKUI_CALENDAR_ALIGNMENT_END = 2 | 选择器和入口组件右对齐方式。 |

### ArkUI_PickerIndicatorType

``` c
enum ArkUI_PickerIndicatorType
```

**描述**

选择器的选中指示器类型。

**起始版本：** 23

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_PICKER_INDICATOR_BACKGROUND  = 0 | 背景样式。 |
| ARKUI_PICKER_INDICATOR_DIVIDER  = 1 | 分割线样式。 |

## 函数说明

### OH_ArkUI_TextPickerRangeContentArray_Create()

```c
ArkUI_TextPickerRangeContentArray* OH_ArkUI_TextPickerRangeContentArray_Create(int32_t length)
```

**描述**

创建[TextPickerRangeContent](capi-arkui-nativemodule-arkui-textpickerrangecontentarray.md)数组的对象。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t length | 指定TextPickerRangeContent数组的长度。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_TextPickerRangeContentArray](capi-arkui-nativemodule-arkui-textpickerrangecontentarray.md)* | 返回指向TextPickerRangeContent空数组的指针。 |

### OH_ArkUI_TextPickerRangeContentArray_SetIconAtIndex()

```c
void OH_ArkUI_TextPickerRangeContentArray_SetIconAtIndex(ArkUI_TextPickerRangeContentArray* handle, char* icon, int32_t index)
```

**描述**

设置TextPickerRangeContent数组指定位置的icon数据。

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

创建[TextCascadePickerRangeContent](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md)数组对象。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t length | 指向TextPickerRangeContent数组的长度。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md)* | 返回指向TextCascadePickerRangeContent空数组的指针。 |

### OH_ArkUI_TextCascadePickerRangeContentArray_SetTextAtIndex()

```c
void OH_ArkUI_TextCascadePickerRangeContentArray_SetTextAtIndex(ArkUI_TextCascadePickerRangeContentArray* handle, char* text, int32_t index)
```

**描述**

设置TextCascadePickerRangeContent数组指定位置的text数据。

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

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md)* handle | 指向TextCascadePickerRangeContentHandle的指针。 |

### OH_ArkUI_PickerIndicatorStyle_Create()

``` c
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
| [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md)* | [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md)实例。如果返回空指针，表示创建失败，失败原因可能是地址空间已满或类型不支持。 |

### OH_ArkUI_PickerIndicatorStyle_Dispose()

``` c
void OH_ArkUI_PickerIndicatorStyle_Dispose(ArkUI_PickerIndicatorStyle* style)
```

**描述**

销毁选中项指示器的样式实例。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md)* style | 要销毁的[ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md)实例。 |
