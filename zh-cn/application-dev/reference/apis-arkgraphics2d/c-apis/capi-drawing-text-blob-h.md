# drawing_text_blob.h

## 概述

文件中定义了与文字相关的功能函数。 <br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**库：** libnative_drawing.so

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 11

**相关模块：** [Drawing](capi-drawing.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_Drawing_RunBuffer](capi-drawing-oh-drawing-runbuffer.md) | OH_Drawing_RunBuffer | 结构体用于描述一块内存，该内存用于存储文字和位置信息。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_Drawing_TextBlobBuilder* OH_Drawing_TextBlobBuilderCreate(void)](#oh_drawing_textblobbuildercreate) | 用于创建一个文本构造器对象。 |
| [OH_Drawing_TextBlob* OH_Drawing_TextBlobCreateFromText(const void* text, size_t byteLength, const OH_Drawing_Font* font, OH_Drawing_TextEncoding textEncoding)](#oh_drawing_textblobcreatefromtext) | 使用文本创建一个文本对象。 <br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。 <br>text、font任意一个为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER； <br>textEncoding不在枚举范围内返回OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE。 |
| [OH_Drawing_ErrorCode OH_Drawing_TextBlobCreateFromTextWithFallback(const void *text, uint32_t byteLength, const OH_Drawing_Font *font, OH_Drawing_TextEncoding textEncoding, OH_Drawing_TextBlob ***textBlobs, uint32_t *textBlobsCount)](#oh_drawing_textblobcreatefromtextwithfallback) | 使用文本创建一组文本对象，支持字体回退。 若当前字体的字形不支持某些字符时，会自动从系统中查找回退字体。每段连续且使用相同字体的字符会创建一个文本对象。 所有文本对象共享整个字符串的坐标系：每个文本对象的字形位置已包含前序文本的宽度，因此所有文本对象应在同一原点绘制。 |
| [OH_Drawing_TextBlob* OH_Drawing_TextBlobCreateFromPosText(const void* text, size_t byteLength, OH_Drawing_Point2D* point2D, const OH_Drawing_Font* font, OH_Drawing_TextEncoding textEncoding)](#oh_drawing_textblobcreatefrompostext) | 使用文本创建文本对象，文本对象中每个字符的坐标由OH_Drawing_Point2D数组中对应的坐标信息决定。 <br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。 <br>text、point2D、font任意一个为NULL或byteLength等于0时返回OH_DRAWING_ERROR_INVALID_PARAMETER； <br>textEncoding不在枚举范围内返回OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE。 |
| [OH_Drawing_ErrorCode OH_Drawing_TextBlobCreateFromPosTextWithFallback(const void *text, uint32_t byteLength, OH_Drawing_Point2D *point2D, const OH_Drawing_Font *font, OH_Drawing_TextEncoding textEncoding, OH_Drawing_TextBlob ***textBlobs, uint32_t *textBlobsCount)](#oh_drawing_textblobcreatefrompostextwithfallback) | 使用文本创建一组文本对象，支持字体回退。 若当前字体的字形不支持某些字符时，会自动从系统中查找回退字体。 每段连续且使用相同字体的字符会创建一个文本对象。文本对象中每个字符的坐标由OH_Drawing_Point2D数组中对应的坐标信息决定。 |
| [OH_Drawing_TextBlob* OH_Drawing_TextBlobCreateFromString(const char* str, const OH_Drawing_Font* font, OH_Drawing_TextEncoding textEncoding)](#oh_drawing_textblobcreatefromstring) | 使用字符串创建文本对象。 <br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。 <br>str、font任意一个为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER； <br>textEncoding不在枚举范围内返回OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE。 |
| [OH_Drawing_ErrorCode OH_Drawing_TextBlobCreateFromStringWithFallback(const char *str, const OH_Drawing_Font *font, OH_Drawing_TextEncoding textEncoding, OH_Drawing_TextBlob ***textBlobs, uint32_t *textBlobsCount)](#oh_drawing_textblobcreatefromstringwithfallback) | 使用字符串创建一组文本对象，支持字体回退。 若当前字体的字形不支持某些字符时，会自动从系统中查找回退字体。每段连续且使用相同字体的字符会创建一个文本对象。 所有文本对象共享整个字符串的坐标系：每个文本对象的字形位置已包含前序文本的宽度，因此所有文本对象应在同一原点绘制。 |
| [void OH_Drawing_TextBlobGetBounds(OH_Drawing_TextBlob* textBlob, OH_Drawing_Rect* rect)](#oh_drawing_textblobgetbounds) | 获取文本对象的边界范围。 <br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。 <br>textBlob、rect任意一个为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。 |
| [uint32_t OH_Drawing_TextBlobUniqueID(const OH_Drawing_TextBlob* textBlob)](#oh_drawing_textblobuniqueid) | 获取文本的标识符，该标识符是唯一的非零值。 <br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。 <br>textBlob为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。 |
| [const OH_Drawing_RunBuffer* OH_Drawing_TextBlobBuilderAllocRunPos(OH_Drawing_TextBlobBuilder* textBlobBuilder, const OH_Drawing_Font* font, int32_t count, const OH_Drawing_Rect* rect)](#oh_drawing_textblobbuilderallocrunpos) | 申请一块内存，用于存储文字和位置信息。返回的指针无需调用者管理，当调用[OH_Drawing_TextBlobBuilderMake](capi-drawing-text-blob-h.md#oh_drawing_textblobbuildermake)后禁止使用。 <br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。 <br>textBlobBuilder、font任意一个为NULL或者count小于等于0时返回OH_DRAWING_ERROR_INVALID_PARAMETER。 |
| [OH_Drawing_TextBlob* OH_Drawing_TextBlobBuilderMake(OH_Drawing_TextBlobBuilder* textBlobBuilder)](#oh_drawing_textblobbuildermake) | 用于从文本构造器中创建文本对象。 <br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。 <br>textBlobBuilder为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。 |
| [void OH_Drawing_TextBlobDestroy(OH_Drawing_TextBlob* textBlob)](#oh_drawing_textblobdestroy) | 用于销毁文本对象并回收该对象占用的内存。 |
| [void OH_Drawing_TextBlobBuilderDestroy(OH_Drawing_TextBlobBuilder* textBlobBuilder)](#oh_drawing_textblobbuilderdestroy) | 用于销毁文本构造器对象并回收该对象占用的内存。 |
| [OH_Drawing_ErrorCode OH_Drawing_TextBlobsArrayDestroy(OH_Drawing_TextBlob** textBlobs, uint32_t count)](#oh_drawing_textblobsarraydestroy) | 销毁OH_Drawing_TextBlob对象数组并回收该数组占用的内存。 本函数会销毁数组中的文本对象，并释放数组本身。count必须与创建数组时返回的数量完全一致，传入其他值将导致未定义行为。 |

## 函数说明

### OH_Drawing_TextBlobBuilderCreate()

```c
OH_Drawing_TextBlobBuilder* OH_Drawing_TextBlobBuilderCreate(void)
```

**描述：**

用于创建一个文本构造器对象。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 11

**返回值：**

| 类型 | 说明 |
| -- | -- |
| OH_Drawing_TextBlobBuilder* | 函数返回一个指针，指针指向创建的文本构造器对象。 |

### OH_Drawing_TextBlobCreateFromText()

```c
OH_Drawing_TextBlob* OH_Drawing_TextBlobCreateFromText(const void* text, size_t byteLength, const OH_Drawing_Font* font, OH_Drawing_TextEncoding textEncoding)
```

**描述：**

使用文本创建一个文本对象。 <br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。 <br>text、font任意一个为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER； <br>textEncoding不在枚举范围内返回OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const void* text | 指向文本的指针。 |
| size_t byteLength | 文本的字节长度。 |
| const OH_Drawing_Font* font | 指向字体对象OH_Drawing_Font的指针。 |
| OH_Drawing_TextEncoding textEncoding | 文本编码类型。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| OH_Drawing_TextBlob* | 函数返回一个指针，指针指向创建的文本对象OH_Drawing_TextBlob。 |

### OH_Drawing_TextBlobCreateFromTextWithFallback()

```c
OH_Drawing_ErrorCode OH_Drawing_TextBlobCreateFromTextWithFallback(const void *text, uint32_t byteLength, const OH_Drawing_Font *font, OH_Drawing_TextEncoding textEncoding, OH_Drawing_TextBlob ***textBlobs, uint32_t *textBlobsCount)
```

**描述：**

使用文本创建一组文本对象，支持字体回退。 若当前字体的字形不支持某些字符时，会自动从系统中查找回退字体。每段连续且使用相同字体的字符会创建一个文本对象。 所有文本对象共享整个字符串的坐标系：每个文本对象的字形位置已包含前序文本的宽度，因此所有文本对象应在同一原点绘制。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const void *text | [in] 指向文本的指针。 |
| uint32_t byteLength | [in] 文本长度，单位为字节。 |
| const OH_Drawing_Font *font | [in] 指向字型对象OH_Drawing_Font的指针。 |
| OH_Drawing_TextEncoding textEncoding | [in] 文本编码类型OH_Drawing_TextEncoding。 |
| OH_Drawing_TextBlob ***textBlobs | [out] 指向OH_Drawing_TextBlob对象数组的指针。作为出参使用。当不再需要时，使用[OH_Drawing_TextBlobsArrayDestroy](capi-drawing-text-blob-h.md#oh_drawing_textblobsarraydestroy)释放该数组。 |
| uint32_t *textBlobsCount | [out] 返回数组中文本对象的数量。作为出参使用。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| OH_Drawing_ErrorCode | 返回[OH_DRAWING_SUCCESS](capi-drawing-error-code-h.md#oh_drawing_errorcode) 表示执行成功。      <br>返回[OH_DRAWING_ERROR_INCORRECT_PARAMETER](capi-drawing-error-code-h.md#oh_drawing_errorcode) 表示参数text、font、textBlobs、textBlobsCount任意一个为空，或者byteLength为0。      <br>返回[OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE](capi-drawing-error-code-h.md#oh_drawing_errorcode) 表示textEncoding不在枚举范围内。      <br>返回[OH_DRAWING_ERROR_ALLOCATION_FAILED](capi-drawing-error-code-h.md#oh_drawing_errorcode) 表示数组内存分配失败。 |

### OH_Drawing_TextBlobCreateFromPosText()

```c
OH_Drawing_TextBlob* OH_Drawing_TextBlobCreateFromPosText(const void* text, size_t byteLength, OH_Drawing_Point2D* point2D, const OH_Drawing_Font* font, OH_Drawing_TextEncoding textEncoding)
```

**描述：**

使用文本创建文本对象，文本对象中每个字符的坐标由OH_Drawing_Point2D数组中对应的坐标信息决定。 <br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。 <br>text、point2D、font任意一个为NULL或byteLength等于0时返回OH_DRAWING_ERROR_INVALID_PARAMETER； <br>textEncoding不在枚举范围内返回OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const void* text | 指向文本的指针。 |
| size_t byteLength | 文本的字节长度。 |
| OH_Drawing_Point2D* point2D | 二维点OH_Drawing_Point2D数组首地址，数组个数由{@link drawing_font.h#OH_Drawing_FontCountText}的计算结果决定。 |
| const OH_Drawing_Font* font | 指向字体对象OH_Drawing_Font的指针。 |
| OH_Drawing_TextEncoding textEncoding | 文本编码类型OH_Drawing_TextEncoding。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| OH_Drawing_TextBlob* | 函数返回一个指针，指针指向创建的文本对象OH_Drawing_TextBlob。 |

### OH_Drawing_TextBlobCreateFromPosTextWithFallback()

```c
OH_Drawing_ErrorCode OH_Drawing_TextBlobCreateFromPosTextWithFallback(const void *text, uint32_t byteLength, OH_Drawing_Point2D *point2D, const OH_Drawing_Font *font, OH_Drawing_TextEncoding textEncoding, OH_Drawing_TextBlob ***textBlobs, uint32_t *textBlobsCount)
```

**描述：**

使用文本创建一组文本对象，支持字体回退。 若当前字体的字形不支持某些字符时，会自动从系统中查找回退字体。 每段连续且使用相同字体的字符会创建一个文本对象。文本对象中每个字符的坐标由OH_Drawing_Point2D数组中对应的坐标信息决定。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const void *text | [in] 指向文本的指针。 |
| uint32_t byteLength | [in] 文本长度，单位为字节。 |
| OH_Drawing_Point2D *point2D | [in] 二维点OH_Drawing_Point2D数组首地址，数组个数由[OH_Drawing_FontCountText](capi-drawing-font-h.md#oh_drawing_fontcounttext)的计算结果决定。 |
| const OH_Drawing_Font *font | [in] 指向字型对象OH_Drawing_Font的指针。 |
| OH_Drawing_TextEncoding textEncoding | [in] 文本编码类型OH_Drawing_TextEncoding。 |
| OH_Drawing_TextBlob ***textBlobs | [out] 指向OH_Drawing_TextBlob对象数组的指针。作为出参使用。当不再需要时，使用[OH_Drawing_TextBlobsArrayDestroy](capi-drawing-text-blob-h.md#oh_drawing_textblobsarraydestroy)释放该数组。 |
| uint32_t *textBlobsCount | [out] 返回数组中文本对象的数量。作为出参使用。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| OH_Drawing_ErrorCode | 返回[OH_DRAWING_SUCCESS](capi-drawing-error-code-h.md#oh_drawing_errorcode) 表示执行成功。      <br>返回[OH_DRAWING_ERROR_INCORRECT_PARAMETER](capi-drawing-error-code-h.md#oh_drawing_errorcode) 表示参数text、point2D、font、textBlobs、textBlobsCount任意一个为空，      或者byteLength为0。      <br>返回[OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE](capi-drawing-error-code-h.md#oh_drawing_errorcode) 表示textEncoding不在枚举范围内。      <br>返回[OH_DRAWING_ERROR_ALLOCATION_FAILED](capi-drawing-error-code-h.md#oh_drawing_errorcode) 表示数组内存分配失败。 |

### OH_Drawing_TextBlobCreateFromString()

```c
OH_Drawing_TextBlob* OH_Drawing_TextBlobCreateFromString(const char* str, const OH_Drawing_Font* font, OH_Drawing_TextEncoding textEncoding)
```

**描述：**

使用字符串创建文本对象。 <br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。 <br>str、font任意一个为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER； <br>textEncoding不在枚举范围内返回OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* str | 指向字符串的指针。 |
| const OH_Drawing_Font* font | 指向字体对象OH_Drawing_Font的指针。 |
| OH_Drawing_TextEncoding textEncoding | 文本编码类型OH_Drawing_TextEncoding。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| OH_Drawing_TextBlob* | 函数返回一个指针，指针指向创建的文本对象OH_Drawing_TextBlob。 |

### OH_Drawing_TextBlobCreateFromStringWithFallback()

```c
OH_Drawing_ErrorCode OH_Drawing_TextBlobCreateFromStringWithFallback(const char *str, const OH_Drawing_Font *font, OH_Drawing_TextEncoding textEncoding, OH_Drawing_TextBlob ***textBlobs, uint32_t *textBlobsCount)
```

**描述：**

使用字符串创建一组文本对象，支持字体回退。 若当前字体的字形不支持某些字符时，会自动从系统中查找回退字体。每段连续且使用相同字体的字符会创建一个文本对象。 所有文本对象共享整个字符串的坐标系：每个文本对象的字形位置已包含前序文本的宽度，因此所有文本对象应在同一原点绘制。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *str | [in] 指向字符串的指针。 |
| const OH_Drawing_Font *font | [in] 指向字型对象[OH_Drawing_Font](capi-drawing-oh-drawing-font.md)的指针。 |
| OH_Drawing_TextEncoding textEncoding | [in] 文本编码类型[OH_Drawing_TextEncoding](capi-drawing-types-h.md#oh_drawing_textencoding)。 |
| OH_Drawing_TextBlob ***textBlobs | [out] 指向OH_Drawing_TextBlob对象数组的指针。作为出参使用。当不再需要时，使用[OH_Drawing_TextBlobsArrayDestroy](capi-drawing-text-blob-h.md#oh_drawing_textblobsarraydestroy)释放该数组。 |
| uint32_t *textBlobsCount | [out] 返回数组中文本对象的数量。作为出参使用。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| OH_Drawing_ErrorCode | 返回[OH_DRAWING_SUCCESS](capi-drawing-error-code-h.md#oh_drawing_errorcode) 表示执行成功。      <br>返回[OH_DRAWING_ERROR_INCORRECT_PARAMETER](capi-drawing-error-code-h.md#oh_drawing_errorcode) 表示参数str、font、textBlobs、textBlobsCount任意一个为空。      <br>返回[OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE](capi-drawing-error-code-h.md#oh_drawing_errorcode) 表示textEncoding不在枚举范围内。 |

### OH_Drawing_TextBlobGetBounds()

```c
void OH_Drawing_TextBlobGetBounds(OH_Drawing_TextBlob* textBlob, OH_Drawing_Rect* rect)
```

**描述：**

获取文本对象的边界范围。 <br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。 <br>textBlob、rect任意一个为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_Drawing_TextBlob* textBlob | 指向文本对象OH_Drawing_TextBlob的指针。 |
| OH_Drawing_Rect* rect | 指向矩形对象OH_Drawing_Rect的指针，开发者可调用OH_Drawing_Rect接口创建。 |

### OH_Drawing_TextBlobUniqueID()

```c
uint32_t OH_Drawing_TextBlobUniqueID(const OH_Drawing_TextBlob* textBlob)
```

**描述：**

获取文本的标识符，该标识符是唯一的非零值。 <br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。 <br>textBlob为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const OH_Drawing_TextBlob* textBlob | 指向文本对象OH_Drawing_TextBlob的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| uint32_t | 返回文本对象的标识符。 |

### OH_Drawing_TextBlobBuilderAllocRunPos()

```c
const OH_Drawing_RunBuffer* OH_Drawing_TextBlobBuilderAllocRunPos(OH_Drawing_TextBlobBuilder* textBlobBuilder, const OH_Drawing_Font* font, int32_t count, const OH_Drawing_Rect* rect)
```

**描述：**

申请一块内存，用于存储文字和位置信息。返回的指针无需调用者管理，当调用[OH_Drawing_TextBlobBuilderMake](capi-drawing-text-blob-h.md#oh_drawing_textblobbuildermake)后禁止使用。 <br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。 <br>textBlobBuilder、font任意一个为NULL或者count小于等于0时返回OH_DRAWING_ERROR_INVALID_PARAMETER。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_Drawing_TextBlobBuilder* textBlobBuilder | 指向文本构造器对象的指针。 |
| const OH_Drawing_Font* font | 指向字体对象OH_Drawing_Font的指针。 |
| int32_t count | 文字的数量。 |
| const OH_Drawing_Rect* rect | 文本的边界框，为NULL表示不设置边界框。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [const OH_Drawing_RunBuffer*](capi-drawing-oh-drawing-runbuffer.md) | 返回一个指针，指针指向创建的文本位置信息。 |

### OH_Drawing_TextBlobBuilderMake()

```c
OH_Drawing_TextBlob* OH_Drawing_TextBlobBuilderMake(OH_Drawing_TextBlobBuilder* textBlobBuilder)
```

**描述：**

用于从文本构造器中创建文本对象。 <br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。 <br>textBlobBuilder为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_Drawing_TextBlobBuilder* textBlobBuilder | 指向文本构造器对象的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| OH_Drawing_TextBlob* | 函数返回一个指针，指针指向创建的文本对象OH_Drawing_TextBlob。 |

### OH_Drawing_TextBlobDestroy()

```c
void OH_Drawing_TextBlobDestroy(OH_Drawing_TextBlob* textBlob)
```

**描述：**

用于销毁文本对象并回收该对象占用的内存。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_Drawing_TextBlob* textBlob | 指向文本对象OH_Drawing_TextBlob的指针。 |

### OH_Drawing_TextBlobBuilderDestroy()

```c
void OH_Drawing_TextBlobBuilderDestroy(OH_Drawing_TextBlobBuilder* textBlobBuilder)
```

**描述：**

用于销毁文本构造器对象并回收该对象占用的内存。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_Drawing_TextBlobBuilder* textBlobBuilder | 指向文本构造器对象的指针。 |

### OH_Drawing_TextBlobsArrayDestroy()

```c
OH_Drawing_ErrorCode OH_Drawing_TextBlobsArrayDestroy(OH_Drawing_TextBlob** textBlobs, uint32_t count)
```

**描述：**

销毁OH_Drawing_TextBlob对象数组并回收该数组占用的内存。 本函数会销毁数组中的文本对象，并释放数组本身。count必须与创建数组时返回的数量完全一致，传入其他值将导致未定义行为。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_Drawing_TextBlob** textBlobs | [in] 指向OH_Drawing_TextBlob对象数组的指针。 |
| uint32_t count | [in] 数组的大小。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| OH_Drawing_ErrorCode | 返回[OH_DRAWING_SUCCESS](capi-drawing-error-code-h.md#oh_drawing_errorcode) 表示执行成功。  返回[OH_DRAWING_ERROR_INCORRECT_PARAMETER](capi-drawing-error-code-h.md#oh_drawing_errorcode) 表示textBlobs为空或者count为0。 |


