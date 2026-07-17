# Font

描述字型绘制时所使用的属性，如大小、字体等。

> **说明：**  
>  
> - 本模块使用屏幕物理像素单位px。  
>  
> - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**起始版本：** 11

<!--Device-drawing-class Font--><!--Device-drawing-class Font-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## countText

```TypeScript
countText(text: string): number
```

获取文本所表示的字符数量。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-countText(text: string): int--><!--Device-Font-countText(text: string): int-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 文本内容。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回文本所表示的字符数量，整数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## createPathForGlyph

```TypeScript
createPathForGlyph(index: number): Path
```

获取指定字形的路径轮廓。

**起始版本：** 18

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-createPathForGlyph(index: number): Path--><!--Device-Font-createPathForGlyph(index: number): Path-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 字形索引。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Path](arkts-arkgraphics2d-drawing-path-c.md) | 返回指定字形的路径轮廓。 |

## enableEmbolden

```TypeScript
enableEmbolden(isEmbolden: boolean): void
```

使能字型粗体。

**起始版本：** 11

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-enableEmbolden(isEmbolden: boolean): void--><!--Device-Font-enableEmbolden(isEmbolden: boolean): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEmbolden | boolean | 是 | 表示是否使能字型粗体。true表示使能，false表示不使能。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## enableLinearMetrics

```TypeScript
enableLinearMetrics(isLinearMetrics: boolean): void
```

使能字型的线性缩放。

**起始版本：** 11

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-enableLinearMetrics(isLinearMetrics: boolean): void--><!--Device-Font-enableLinearMetrics(isLinearMetrics: boolean): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isLinearMetrics | boolean | 是 | 表示是否使能字型的线性缩放。true表示使能，false表示不使能。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## enableSubpixel

```TypeScript
enableSubpixel(isSubpixel: boolean): void
```

使能字型亚像素级别的文字绘制，显示效果平滑。

**起始版本：** 11

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-enableSubpixel(isSubpixel: boolean): void--><!--Device-Font-enableSubpixel(isSubpixel: boolean): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isSubpixel | boolean | 是 | 表示是否使能字型亚像素级别的文字绘制。true表示使能，false表示不使能。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## getBounds

```TypeScript
getBounds(glyphs: Array<number>): Array<common2D.Rect>
```

获取字形数组中每个字形的边界矩形。

**起始版本：** 18

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-getBounds(glyphs: Array<number>): Array<common2D.Rect>--><!--Device-Font-getBounds(glyphs: Array<number>): Array<common2D.Rect>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| glyphs | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<number> | 是 | 字形索引数组，可由[textToGlyphs](arkts-arkgraphics2d-drawing-font-c.md#texttoglyphs-1)生成。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<common2D.Rect> | Array that holds the rectangular bounding boxes. |

## getEdging

```TypeScript
getEdging(): FontEdging
```

获取字型边缘效果。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-getEdging(): FontEdging--><!--Device-Font-getEdging(): FontEdging-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FontEdging](arkts-arkgraphics2d-drawing-fontedging-e.md) | 返回字型边缘效果。 |

## getHinting

```TypeScript
getHinting(): FontHinting
```

获取字型轮廓效果。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-getHinting(): FontHinting--><!--Device-Font-getHinting(): FontHinting-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FontHinting](arkts-arkgraphics2d-drawing-fonthinting-e.md) | 返回字型轮廓效果。 |

## getMetrics

```TypeScript
getMetrics(): FontMetrics
```

获取与字体关联的FontMetrics属性。

**起始版本：** 11

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-getMetrics(): FontMetrics--><!--Device-Font-getMetrics(): FontMetrics-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FontMetrics](arkts-arkgraphics2d-drawing-fontmetrics-i.md) | FontMetrics属性。 |

## getScaleX

```TypeScript
getScaleX(): number
```

获取字型在x轴方向上的缩放比例。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-getScaleX(): double--><!--Device-Font-getScaleX(): double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回字型在x轴方向上的缩放比例。 |

## getSize

```TypeScript
getSize(): number
```

获取字型大小。

**起始版本：** 11

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-getSize(): double--><!--Device-Font-getSize(): double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 字型大小，浮点数。 |

## getSkewX

```TypeScript
getSkewX(): number
```

获取字型在x轴方向上的倾斜度。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-getSkewX(): double--><!--Device-Font-getSkewX(): double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回字型在x轴方向上的倾斜度。 |

## getTextPath

```TypeScript
getTextPath(text: string, byteLength: number, x: number, y: number): Path
```

获取文字的轮廓路径。

**起始版本：** 18

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-getTextPath(text: string, byteLength: number, x: number, y: number): Path--><!--Device-Font-getTextPath(text: string, byteLength: number, x: number, y: number): Path-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 表示存储UTF-8 文本编码的字符。 |
| byteLength | number | 是 | 表示要获取对应文本路径的字节长度，按传入的字节长度和实际的文本字节大小之间的最小值来获取对应的文本路径。 |
| x | number | 是 | 表示文本在绘图区域内以原点为起始位置的X坐标。 |
| y | number | 是 | 表示文本在绘图区域内以原点为起始位置的Y坐标。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Path](arkts-arkgraphics2d-drawing-path-c.md) | 返回获取到的文本的路径轮廓。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

## getTypeface

```TypeScript
getTypeface(): Typeface
```

获取字体。

**起始版本：** 11

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-getTypeface(): Typeface--><!--Device-Font-getTypeface(): Typeface-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Typeface](arkts-arkgraphics2d-drawing-typeface-c.md) | 字体。 |

## getWidths

```TypeScript
getWidths(glyphs: Array<number>): Array<number>
```

获取字形数组中每个字形对应的宽度。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-getWidths(glyphs: Array<number>): Array<number>--><!--Device-Font-getWidths(glyphs: Array<number>): Array<number>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| glyphs | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<number> | 是 | 字形索引数组，可由[textToGlyphs](arkts-arkgraphics2d-drawing-font-c.md#texttoglyphs-1)生成。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<number> | 返回字形宽度数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## isBaselineSnap

```TypeScript
isBaselineSnap(): boolean
```

当前画布矩阵轴对齐时，获取字型基线是否与像素对齐的结果。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-isBaselineSnap(): boolean--><!--Device-Font-isBaselineSnap(): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回字型基线是否与像素对齐，true为对齐，false为没有对齐。 |

## isEmbeddedBitmaps

```TypeScript
isEmbeddedBitmaps(): boolean
```

获取字型是否转换成位图处理的结果。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-isEmbeddedBitmaps(): boolean--><!--Device-Font-isEmbeddedBitmaps(): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回字型是否转换成位图处理结果，true表示转换成位图处理，false表示不转换成位图处理。 |

## isEmbolden

```TypeScript
isEmbolden(): boolean
```

获取字型是否设置了粗体效果。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-isEmbolden(): boolean--><!--Device-Font-isEmbolden(): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回字型是否设置粗体效果的结果，true表示设置了粗体效果，false表示未设置粗体效果。 |

## isForceAutoHinting

```TypeScript
isForceAutoHinting(): boolean
```

获取字型轮廓是否自动调整的结果。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-isForceAutoHinting(): boolean--><!--Device-Font-isForceAutoHinting(): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回字型轮廓是否自动调整，true为自动调整，false为不自动调整。 |

## isLinearMetrics

```TypeScript
isLinearMetrics(): boolean
```

获取字型是否可以线性缩放。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-isLinearMetrics(): boolean--><!--Device-Font-isLinearMetrics(): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回字型是否可线性缩放的结果，true表示可线性缩放，false表示不可线性缩放。 |

## isSubpixel

```TypeScript
isSubpixel(): boolean
```

获取字型是否使用次像素渲染。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-isSubpixel(): boolean--><!--Device-Font-isSubpixel(): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回字型是否使用次像素渲染的结果，true表示使用，false表示不使用。 |

## isThemeFontFollowed

```TypeScript
isThemeFontFollowed(): boolean
```

获取字型中的字体是否跟随主题字体。默认不跟随。

**起始版本：** 15

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-isThemeFontFollowed(): boolean--><!--Device-Font-isThemeFontFollowed(): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回字型中的字体是否跟随主题字体的结果，true表示跟随主题字体，false表示不跟随主题字体。 |

## measureSingleCharacter

```TypeScript
measureSingleCharacter(text: string): number
```

测量单个字符的宽度。当前字型中的字体不支持待测量字符时，退化到使用系统字体测量字符宽度。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-measureSingleCharacter(text: string): double--><!--Device-Font-measureSingleCharacter(text: string): double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 待测量的单个字符，字符串的长度必须为1。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 字符的宽度，浮点数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

## measureSingleCharacterWithFeatures

```TypeScript
measureSingleCharacterWithFeatures(text: string, features: Array<FontFeature>): number
```

测量单个字符的宽度，字符带有字体特征。当前字型中的字体不支持待测量字符时，退化到使用系统字体测量字符宽度。

**起始版本：** 20

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-measureSingleCharacterWithFeatures(text: string, features: Array<FontFeature>): double--><!--Device-Font-measureSingleCharacterWithFeatures(text: string, features: Array<FontFeature>): double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 待测量的单个字符。字符串长度必须为1。 |
| features | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<FontFeature> | 是 | 字体特征对象数组。参数为空数组时使用TTF(TrueType Font)文件中预设的字体特征。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 字符的宽度，浮点数，单位为px。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [25900001](../errorcode-drawing.md#25900001-参数值异常) | Parameter error. Possible causes: Incorrect parameter range. |

## measureText

```TypeScript
measureText(text: string, encoding: TextEncoding): number
```

测量文本的宽度。

> **说明：**  
>  
> 此接口用于测量原始字符串的文本宽度，若想测量排版后的文本宽度，建议使用  
> [measure.measureText](../../../../reference/apis-arkui/arkts-apis-uicontext-measureutils.md#measuretext12)替代。

**起始版本：** 11

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-measureText(text: string, encoding: TextEncoding): double--><!--Device-Font-measureText(text: string, encoding: TextEncoding): double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 文本内容。 |
| encoding | [TextEncoding](arkts-arkgraphics2d-drawing-textencoding-e.md) | 是 | 编码格式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 文本的宽度，浮点数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## setBaselineSnap

```TypeScript
setBaselineSnap(isBaselineSnap: boolean): void
```

当前画布矩阵轴对齐时，设置字型基线是否与像素对齐。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-setBaselineSnap(isBaselineSnap: boolean): void--><!--Device-Font-setBaselineSnap(isBaselineSnap: boolean): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isBaselineSnap | boolean | 是 | 指示字型基线是否和像素对齐，true表示对齐，false表示不对齐。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## setEdging

```TypeScript
setEdging(edging: FontEdging): void
```

设置字型边缘效果。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-setEdging(edging: FontEdging): void--><!--Device-Font-setEdging(edging: FontEdging): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| edging | [FontEdging](arkts-arkgraphics2d-drawing-fontedging-e.md) | 是 | 字型边缘效果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

## setEmbeddedBitmaps

```TypeScript
setEmbeddedBitmaps(isEmbeddedBitmaps: boolean): void
```

设置字型是否转换成位图处理。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-setEmbeddedBitmaps(isEmbeddedBitmaps: boolean): void--><!--Device-Font-setEmbeddedBitmaps(isEmbeddedBitmaps: boolean): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEmbeddedBitmaps | boolean | 是 | 设置字型是否转换成位图处理，true表示转换成位图处理，false表示不转换成位图处理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## setForceAutoHinting

```TypeScript
setForceAutoHinting(isForceAutoHinting: boolean): void
```

设置是否自动调整字型轮廓。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-setForceAutoHinting(isForceAutoHinting: boolean): void--><!--Device-Font-setForceAutoHinting(isForceAutoHinting: boolean): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isForceAutoHinting | boolean | 是 | 是否自动调整字型轮廓，true为自动调整，false为不自动调整。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## setHinting

```TypeScript
setHinting(hinting: FontHinting): void
```

设置字型轮廓效果。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-setHinting(hinting: FontHinting): void--><!--Device-Font-setHinting(hinting: FontHinting): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hinting | [FontHinting](arkts-arkgraphics2d-drawing-fonthinting-e.md) | 是 | 字型轮廓效果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

## setScaleX

```TypeScript
setScaleX(scaleX: number): void
```

设置字型对象在x轴上的缩放比例。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-setScaleX(scaleX: double): void--><!--Device-Font-setScaleX(scaleX: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scaleX | number | 是 | 文本在x轴上的缩放比例，该参数为浮点数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## setSize

```TypeScript
setSize(textSize: number): void
```

设置字型大小。

**起始版本：** 11

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-setSize(textSize: double): void--><!--Device-Font-setSize(textSize: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| textSize | number | 是 | 字型大小，该参数为浮点数，为负数时字型大小会被置为0。字型大小为0时，绘制的文字不会显示。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

## setSkewX

```TypeScript
setSkewX(skewX: number): void
```

设置字型对象在x轴上的倾斜比例。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-setSkewX(skewX: double): void--><!--Device-Font-setSkewX(skewX: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| skewX | number | 是 | 文本在x轴上的倾斜比例，正数表示往左边倾斜，负数表示往右边倾斜，该参数为浮点数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## setThemeFontFollowed

```TypeScript
setThemeFontFollowed(followed: boolean): void
```

设置字型中的字体是否跟随主题字体。设置跟随主题字体后，若系统启用主题字体并且字型未被设置字体，字型会使用该主题字体。

**起始版本：** 15

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-setThemeFontFollowed(followed: boolean): void--><!--Device-Font-setThemeFontFollowed(followed: boolean): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| followed | boolean | 是 | 字型中的字体是否跟随主题字体，true表示跟随主题字体，false表示不跟随主题字体。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## setTypeface

```TypeScript
setTypeface(typeface: Typeface): void
```

为字型设置字体样式（包括字体名称、粗细、斜体等属性）。

**起始版本：** 11

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-setTypeface(typeface: Typeface): void--><!--Device-Font-setTypeface(typeface: Typeface): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| typeface | [Typeface](arkts-arkgraphics2d-drawing-typeface-c.md) | 是 | 字体样式，包括字体名称、粗细、斜体等属性。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## textToGlyphs

```TypeScript
textToGlyphs(text: string, glyphCount?: number): Array<number>
```

将文本转换为字形索引。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-textToGlyphs(text: string, glyphCount?: number): Array<number>--><!--Device-Font-textToGlyphs(text: string, glyphCount?: number): Array<number>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 文本字符串。 |
| glyphCount | number | 否 | 文本表示的字符数量，必须与[countText](arkts-arkgraphics2d-drawing-font-c.md#counttext-1)获取的值相等，默认为text的字符数量，该参数为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<number> | Array that holds the glyph indexes. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

