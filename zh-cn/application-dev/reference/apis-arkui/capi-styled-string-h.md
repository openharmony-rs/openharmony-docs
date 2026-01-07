# styled_string.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hddgzw-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

## 概述

在Native侧定义ArkUIText组件的文本样式和文本布局管理器。

**引用文件：** <arkui/styled_string.h>

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**相关示例：** <!--RP1-->[StyledStringSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/StyledStringSample)<!--RP1End-->

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md) | ArkUI_StyledString | 定义文本组件支持的格式化字符串数据对象。 |
| [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md) | ArkUI_TextLayoutManager | 定义文本布局管理器对象。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [ArkUI_StyledString* OH_ArkUI_StyledString_Create(OH_Drawing_TypographyStyle* style, OH_Drawing_FontCollection* collection)](#oh_arkui_styledstring_create) | 创建指向ArkUI_StyledString对象的指针。 |
| [void OH_ArkUI_StyledString_Destroy(ArkUI_StyledString* handle)](#oh_arkui_styledstring_destroy) | 释放被ArkUI_StyledString对象占据的内存。 |
| [void OH_ArkUI_StyledString_PushTextStyle(ArkUI_StyledString* handle, OH_Drawing_TextStyle* style)](#oh_arkui_styledstring_pushtextstyle) | 将新的排版风格设置到当前格式化字符串样式栈顶。 |
| [void OH_ArkUI_StyledString_AddText(ArkUI_StyledString* handle, const char* content)](#oh_arkui_styledstring_addtext) | 基于当前格式化字符串样式设置对应的文本内容。 |
| [void OH_ArkUI_StyledString_PopTextStyle(ArkUI_StyledString* handle)](#oh_arkui_styledstring_poptextstyle) | 将当前格式化字符串对象中栈顶样式出栈。 |
| [OH_Drawing_Typography* OH_ArkUI_StyledString_CreateTypography(ArkUI_StyledString* handle)](#oh_arkui_styledstring_createtypography) | 基于格式字符串对象创建指向OH_Drawing_Typography对象的指针，用于提前进行文本测算排版。 |
| [void OH_ArkUI_StyledString_AddPlaceholder(ArkUI_StyledString* handle, OH_Drawing_PlaceholderSpan* placeholder)](#oh_arkui_styledstring_addplaceholder) | 设置占位符。 |
| [ArkUI_StyledString_Descriptor* OH_ArkUI_StyledString_Descriptor_Create(void)](#oh_arkui_styledstring_descriptor_create) | 创建属性字符串数据对象。 |
| [void OH_ArkUI_StyledString_Descriptor_Destroy(ArkUI_StyledString_Descriptor* descriptor)](#oh_arkui_styledstring_descriptor_destroy) | 释放被ArkUI_StyledString_Descriptor对象占据的内存。 |
| [int32_t OH_ArkUI_UnmarshallStyledStringDescriptor(uint8_t* buffer, size_t bufferSize, ArkUI_StyledString_Descriptor* descriptor)](#oh_arkui_unmarshallstyledstringdescriptor) | 将包含属性字符串信息的字节数组反序列化为属性字符串。 |
| [int32_t OH_ArkUI_MarshallStyledStringDescriptor(uint8_t* buffer, size_t bufferSize, ArkUI_StyledString_Descriptor* descriptor, size_t* resultSize)](#oh_arkui_marshallstyledstringdescriptor) | 将属性字符串信息序列化为字节数组。 |
| [const char* OH_ArkUI_ConvertToHtml(ArkUI_StyledString_Descriptor* descriptor)](#oh_arkui_converttohtml) | 将属性字符串信息转化成html。 |
| [void OH_ArkUI_TextLayoutManager_Dispose(ArkUI_TextLayoutManager* layoutManager)](#oh_arkui_textlayoutmanager_dispose) | 释放被文本布局管理器对象占据的内存。 |
| [ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetLineCount(ArkUI_TextLayoutManager* layoutManager, int32_t* outLineCount)](#oh_arkui_textlayoutmanager_getlinecount) | 获取文本行数。 |
| [ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetRectsForRange(ArkUI_TextLayoutManager* layoutManager, int32_t start, int32_t end, OH_Drawing_RectWidthStyle widthStyle, OH_Drawing_RectHeightStyle heightStyle, OH_Drawing_TextBox** outTextBoxes)](#oh_arkui_textlayoutmanager_getrectsforrange) | 获取给定的矩形区域宽度样式以及高度样式的规格下，文本中任意区间范围内的字符或占位符所占的绘制区域信息。 |
| [ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetGlyphPositionAtCoordinate(ArkUI_TextLayoutManager* layoutManager, double dx, double dy, OH_Drawing_PositionAndAffinity** outPos)](#oh_arkui_textlayoutmanager_getglyphpositionatcoordinate) | 获取距离给定坐标最近的字形的位置信息。 |
| [ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetLineMetrics(ArkUI_TextLayoutManager* layoutManager, int32_t lineNumber, OH_Drawing_LineMetrics* outMetrics)](#oh_arkui_textlayoutmanager_getlinemetrics) | 获取指定行的行信息、文本样式信息、以及字体属性信息。 |

## 函数说明

### OH_ArkUI_StyledString_Create()

```c
ArkUI_StyledString* OH_ArkUI_StyledString_Create(OH_Drawing_TypographyStyle* style, OH_Drawing_FontCollection* collection)
```

**描述：**

创建指向ArkUI_StyledString对象的指针。

**起始版本：** 12

**参数：**

| 参数项 | 描述                                                                                                                                                               |
| -- |------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [OH_Drawing_TypographyStyle](../apis-arkgraphics2d/capi-drawing-oh-drawing-typographystyle.md)* style | 指向OH_Drawing_TypographyStyle的指针，由[OH_Drawing_CreateTypographyStyle](../apis-arkgraphics2d/capi-drawing-text-typography-h.md#oh_drawing_createtypographystyle)获取。 |
| [OH_Drawing_FontCollection](../apis-arkgraphics2d/capi-drawing-oh-drawing-fontcollection.md)* collection | 指向OH_Drawing_FontCollection的指针，由[OH_Drawing_CreateFontCollection](../apis-arkgraphics2d/capi-drawing-font-collection-h.md)获取。                                                                                    |

**返回：**

| 类型                      | 说明 |
|-------------------------| -- |
| [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md)* | 创建指向ArkUI_StyledString对象的指针。如果对象返回空指针，表示创建失败，失败的原因是地址空间已满，或者是style，collection参数异常如空指针。 |

### OH_ArkUI_StyledString_Destroy()

```c
void OH_ArkUI_StyledString_Destroy(ArkUI_StyledString* handle)
```

**描述：**

释放被ArkUI_StyledString对象占据的内存。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md)* handle | 指向ArkUI_StyledString对象的指针。 |

### OH_ArkUI_StyledString_PushTextStyle()

```c
void OH_ArkUI_StyledString_PushTextStyle(ArkUI_StyledString* handle, OH_Drawing_TextStyle* style)
```

**描述：**

将新的排版风格设置到当前格式化字符串样式栈顶。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md)* handle | 指向ArkUI_StyledString对象的指针。 |
| [OH_Drawing_TextStyle](../apis-arkgraphics2d/capi-drawing-oh-drawing-textstyle.md)* style | 指向OH_Drawing_TextStyle对象的指针。 |

### OH_ArkUI_StyledString_AddText()

```c
void OH_ArkUI_StyledString_AddText(ArkUI_StyledString* handle, const char* content)
```

**描述：**

基于当前格式化字符串样式设置对应的文本内容。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md)* handle | 指向ArkUI_StyledString对象的指针。 |
| const char* content | 指向文本内容的指针。 |

### OH_ArkUI_StyledString_PopTextStyle()

```c
void OH_ArkUI_StyledString_PopTextStyle(ArkUI_StyledString* handle)
```

**描述：**

将当前格式化字符串对象中栈顶样式出栈。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md)* handle | 指向ArkUI_StyledString对象的指针。 |

### OH_ArkUI_StyledString_CreateTypography()

```c
OH_Drawing_Typography* OH_ArkUI_StyledString_CreateTypography(ArkUI_StyledString* handle)
```

**描述：**

基于格式字符串对象创建指向OH_Drawing_Typography对象的指针，用于提前进行文本测算排版。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md)* handle | 指向ArkUI_StyledString对象的指针。 |

**返回：**

| 类型                         | 说明 |
|----------------------------| -- |
| [OH_Drawing_Typography](../apis-arkgraphics2d/capi-drawing-oh-drawing-typography.md)* | 指向OH_Drawing_Typography对象的指针。如果对象返回空指针，表示创建失败，失败的原因可能是handle参数异常如空指针。 |

### OH_ArkUI_StyledString_AddPlaceholder()

```c
void OH_ArkUI_StyledString_AddPlaceholder(ArkUI_StyledString* handle, OH_Drawing_PlaceholderSpan* placeholder)
```

**描述：**

设置占位符。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md)* handle | 指向ArkUI_StyledString对象的指针。 |
| [OH_Drawing_PlaceholderSpan](../apis-arkgraphics2d/capi-drawing-oh-drawing-placeholderspan.md)* placeholder | 指向OH_Drawing_PlaceholderSpan对象的指针。 |

### OH_ArkUI_StyledString_Descriptor_Create()

```c
ArkUI_StyledString_Descriptor* OH_ArkUI_StyledString_Descriptor_Create(void)
```

**描述：**

创建属性字符串数据对象。

**起始版本：** 14

**返回：**

| 类型                                 | 说明 |
|------------------------------------| -- |
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* | 指向ArkUI_StyledString_Descriptor对象的指针。 |

### OH_ArkUI_StyledString_Descriptor_Destroy()

```c
void OH_ArkUI_StyledString_Descriptor_Destroy(ArkUI_StyledString_Descriptor* descriptor)
```

**描述：**

释放被ArkUI_StyledString_Descriptor对象占据的内存。

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | 指向ArkUI_StyledString_Descriptor对象的指针。 |

### OH_ArkUI_UnmarshallStyledStringDescriptor()

```c
int32_t OH_ArkUI_UnmarshallStyledStringDescriptor(uint8_t* buffer, size_t bufferSize, ArkUI_StyledString_Descriptor* descriptor)
```

**描述：**

将包含属性字符串信息的字节数组反序列化为属性字符串。

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint8_t* buffer | 待反序列化的字节数组。 |
| size_t bufferSize | 字节数组长度。 |
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | 指向ArkUI_StyledString_Descriptor对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_MarshallStyledStringDescriptor()

```c
int32_t OH_ArkUI_MarshallStyledStringDescriptor(uint8_t* buffer, size_t bufferSize, ArkUI_StyledString_Descriptor* descriptor, size_t* resultSize)
```

**描述：**

将属性字符串信息序列化为字节数组。

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint8_t* buffer | 字节数组，用于存储属性字符串序列化后的数据。 |
| size_t bufferSize | 字节数组长度。 |
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | 指向ArkUI_StyledString_Descriptor对象的指针。 |
| size_t* resultSize | 属性字符串转换后的字节数组实际长度。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>        [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>        [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。<br>        [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](capi-native-type-h.md#arkui_errorcode) 无效的属性字符串。 |

### OH_ArkUI_ConvertToHtml()

```c
const char* OH_ArkUI_ConvertToHtml(ArkUI_StyledString_Descriptor* descriptor)
```

**描述：**

将属性字符串信息转化成html。

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | 指向ArkUI_StyledString_Descriptor对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| const char* | html。该指针由内部管理，在OH_ArkUI_StyledString_Descriptor_Destroy()时释放。 |

### OH_ArkUI_TextLayoutManager_Dispose()

```c
void OH_ArkUI_TextLayoutManager_Dispose(ArkUI_TextLayoutManager* layoutManager)
```

**描述**

释放被文本布局管理器对象占据的内存。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md)* layoutManager | 指向ArkUI_TextLayoutManager对象的指针。 |

### OH_ArkUI_TextLayoutManager_GetLineCount()

```c
ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetLineCount(ArkUI_TextLayoutManager* layoutManager, int32_t* outLineCount)
```

**描述**

获取文本行数。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md)* layoutManager | 指向ArkUI_TextLayoutManager对象的指针。 |
| int32_t* outLineCount | 文本行数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_TextLayoutManager_GetRectsForRange()

```c
ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetRectsForRange(ArkUI_TextLayoutManager* layoutManager, int32_t start, int32_t end, OH_Drawing_RectWidthStyle widthStyle, OH_Drawing_RectHeightStyle heightStyle, OH_Drawing_TextBox** outTextBoxes)
```

**描述**

获取给定的矩形区域宽度样式以及高度样式的规格下，文本中任意区间范围内的字符或占位符所占的绘制区域信息。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md)* layoutManager | 指向ArkUI_TextLayoutManager对象的指针。 |
| int32_t start | 起始位置索引，start取值需要大于等于0，否则会返回参数异常。 |
| int32_t end | 结束位置索引，end取值需要大于等于start，否则会返回参数异常。 |
| [OH_Drawing_RectWidthStyle](../apis-arkgraphics2d/capi-drawing-text-typography-h.md#oh_drawing_rectwidthstyle) widthStyle | 矩形区域宽度样式。 |
| [OH_Drawing_RectHeightStyle](../apis-arkgraphics2d/capi-drawing-text-typography-h.md#oh_drawing_rectheightstyle) heightStyle | 矩形区域高度样式。 |
| [OH_Drawing_TextBox](../apis-arkgraphics2d/capi-drawing-oh-drawing-textbox.md)** outTextBoxes | 指向OH_Drawing_TextBox对象的二级指针。 |

**返回：**

| 类型 | 说明 |
| ---- | --- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |


### OH_ArkUI_TextLayoutManager_GetGlyphPositionAtCoordinate()

```c
ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetGlyphPositionAtCoordinate(ArkUI_TextLayoutManager* layoutManager, double dx, double dy, OH_Drawing_PositionAndAffinity** outPos)
```

**描述**

获取距离给定坐标最近的字形的位置信息。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| ------ | --- |
| [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md)* layoutManager | 指向ArkUI_TextLayoutManager对象的指针。 |
| double dx | 相对于控件的x坐标，单位为px。 |
| double dy | 相对于控件的y坐标，单位为px。 |
| [OH_Drawing_PositionAndAffinity](../apis-arkgraphics2d/capi-drawing-oh-drawing-positionandaffinity.md)** outPos | 指向OH_Drawing_PositionAndAffinity对象的二级指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_TextLayoutManager_GetLineMetrics()

```c
ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetLineMetrics(ArkUI_TextLayoutManager* layoutManager, int32_t lineNumber, OH_Drawing_LineMetrics* outMetrics)
```

**描述**

获取指定行的行信息、文本样式信息、以及字体属性信息。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md)* layoutManager | 指向ArkUI_TextLayoutManager对象的指针。 |
| int32_t lineNumber | 指定行的行号索引，行号索引从0开始计数，lineNumber小于0或大于等于文本行数时会返回参数异常。 |
| [OH_Drawing_LineMetrics](../apis-arkgraphics2d/capi-drawing-oh-drawing-linemetrics.md)* outMetrics | 指向OH_Drawing_LineMetrics对象的指针。 |

**返回：**

| 类型 | 说明 |
| ---- | --- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |
