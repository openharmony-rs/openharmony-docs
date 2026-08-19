# Font

Font类用于描述字型绘制时所使用的属性（如大小、字体、粗细、倾斜、缩放等），并支持文本测量、字形转换、路径轮廓获取、主题字体跟随等能力。 > **说明：** > > - 本模块使用屏幕物理像素单位px。 > > - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**起始版本：** 23

<!--Device-drawing-class Font--><!--Device-drawing-class Font-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## countText

```TypeScript
countText(text: string): int
```

获取文本所表示的字符数量。

**起始版本：** 23

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-countText(text: string): int--><!--Device-Font-countText(text: string): int-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 待计数的文本内容。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回文本所表示的字符数量，整数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |

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
| index | number | 是 | 字形索引，可由 [textToGlyphs](#texttoglyphs)生成。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Path | 返回指定字形的路径轮廓。 |

## createPathForGlyph

```TypeScript
createPathForGlyph(index: int): Path | undefined
```

获取指定字形的路径轮廓。

**起始版本：** 23

<!--Device-Font-createPathForGlyph(index: int): Path | undefined--><!--Device-Font-createPathForGlyph(index: int): Path | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 字形索引，可由 [textToGlyphs](#texttoglyphs)生成。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Path | 返回指定字形的路径轮廓。获取失败时返回undefined。 |

## enableEmbolden

```TypeScript
enableEmbolden(isEmbolden: boolean): void
```

使能字型粗体。

**起始版本：** 23

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
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |

## enableLinearMetrics

```TypeScript
enableLinearMetrics(isLinearMetrics: boolean): void
```

使能字型的线性缩放。

**起始版本：** 23

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
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |

## enableSubpixel

```TypeScript
enableSubpixel(isSubpixel: boolean): void
```

使能字型亚像素级别的文字绘制，显示效果平滑。

**起始版本：** 23

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
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |

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
| glyphs | Array&lt;number&gt; | 是 | 字形索引数组，可由 [textToGlyphs](#texttoglyphs)生成。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;common2D.Rect&gt; | 返回字形边界矩形数组。 |

## getBounds

```TypeScript
getBounds(glyphs: Array<int>): Array<common2D.Rect> | undefined
```

获取字形数组中每个字形的边界矩形。

**起始版本：** 23

<!--Device-Font-getBounds(glyphs: Array<int>): Array<common2D.Rect> | undefined--><!--Device-Font-getBounds(glyphs: Array<int>): Array<common2D.Rect> | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| glyphs | Array&lt;int&gt; | 是 | 字形索引数组，可由 [textToGlyphs](#texttoglyphs)生成。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;common2D.Rect&gt; | 返回字形边界矩形数组。 |

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

## getEdging

```TypeScript
getEdging(): FontEdging | undefined
```

获取字型边缘效果。

**起始版本：** 23

<!--Device-Font-getEdging(): FontEdging | undefined--><!--Device-Font-getEdging(): FontEdging | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FontEdging](arkts-arkgraphics2d-drawing-fontedging-e.md) | 返回字型边缘效果。获取失败时返回undefined。 |

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

## getHinting

```TypeScript
getHinting(): FontHinting | undefined
```

获取字型轮廓效果。

**起始版本：** 23

<!--Device-Font-getHinting(): FontHinting | undefined--><!--Device-Font-getHinting(): FontHinting | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FontHinting](arkts-arkgraphics2d-drawing-fonthinting-e.md) | 返回字型轮廓效果。获取失败时返回undefined。 |

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
| [FontMetrics](arkts-arkgraphics2d-drawing-fontmetrics-i.md) | 与字体关联的度量属性对象。 |

## getMetrics

```TypeScript
getMetrics(): FontMetrics | undefined
```

获取与字体关联的FontMetrics属性。

**起始版本：** 23

<!--Device-Font-getMetrics(): FontMetrics | undefined--><!--Device-Font-getMetrics(): FontMetrics | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FontMetrics](arkts-arkgraphics2d-drawing-fontmetrics-i.md) | 与字体关联的度量属性对象。获取失败时返回undefined。 |

## getScaleX

```TypeScript
getScaleX(): double
```

获取字型在x轴方向上的缩放比例。

**起始版本：** 23

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-getScaleX(): double--><!--Device-Font-getScaleX(): double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | 返回字型在x轴方向上的缩放比例。 |

## getSize

```TypeScript
getSize(): double
```

获取字型大小。

**起始版本：** 23

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-getSize(): double--><!--Device-Font-getSize(): double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | 返回字型大小，浮点数。单位为物理像素px。 |

## getSkewX

```TypeScript
getSkewX(): double
```

获取字型在x轴方向上的倾斜比例。

**起始版本：** 23

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-getSkewX(): double--><!--Device-Font-getSkewX(): double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | 返回字型在x轴方向上的倾斜比例。 |

## getTextPath

```TypeScript
getTextPath(text: string, byteLength: number, x: number, y: number): Path
```

获取文字的路径轮廓。

**起始版本：** 18

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-getTextPath(text: string, byteLength: number, x: number, y: number): Path--><!--Device-Font-getTextPath(text: string, byteLength: number, x: number, y: number): Path-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 表示以UTF-8格式编码的文本字符串。 |
| byteLength | number | 是 | 表示要获取对应文本路径的字节长度。按传入的字节长度和实际的文本字节大小之间的最小值来获取对应的文本路径。 |
| x | number | 是 | 表示文本在绘图区域内以原点为起始位置的X坐标。单位为物理像素px。 |
| y | number | 是 | 表示文本在绘图区域内以原点为起始位置的Y坐标。单位为物理像素px。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Path | 返回获取到的文本的路径轮廓。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; 3. Parameter verification failed. |

## getTextPath

```TypeScript
getTextPath(text: string, byteLength: int, x: double, y: double): Path | undefined
```

获取文字的路径轮廓。

**起始版本：** 23

<!--Device-Font-getTextPath(text: string, byteLength: int, x: double, y: double): Path | undefined--><!--Device-Font-getTextPath(text: string, byteLength: int, x: double, y: double): Path | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 表示以UTF-8格式编码的文本字符串。 |
| byteLength | int | 是 | 表示要获取对应文本路径的字节长度。按传入的字节长度和实际的文本字节大小之间的最小值来获取对应的文本路径。 |
| x | double | 是 | 表示文本在绘图区域内以原点为起始位置的X坐标。单位为物理像素px。 |
| y | double | 是 | 表示文本在绘图区域内以原点为起始位置的Y坐标。单位为物理像素px。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Path | 返回获取到的文本的路径轮廓。获取失败时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; 3. Parameter verification failed. |

## getTextPathWithFallback

```TypeScript
getTextPathWithFallback(text: string, byteLength: number, x: number, y: number): Path
```

获取文字的轮廓路径，支持字体回退能力。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Font-getTextPathWithFallback(text: string, byteLength: number, x: number, y: number): Path--><!--Device-Font-getTextPathWithFallback(text: string, byteLength: number, x: number, y: number): Path-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 表示以UTF-8格式编码的文本字符串。 |
| byteLength | number | 是 | 表示要获取对应文本路径的字节长度，按传入的字节长度和实际的文本字节大小之间的最小值来获取对应的文本路径。 |
| x | number | 是 | 表示文本在绘图区域内以原点为起始位置的X坐标。单位为物理像素px。 |
| y | number | 是 | 表示文本在绘图区域内以原点为起始位置的Y坐标。单位为物理像素px。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Path | 返回获取到的文本路径轮廓。路径对象创建失败时返回undefined。 |

## getTextPathWithFallback

```TypeScript
getTextPathWithFallback(text: string, byteLength: int, x: double, y: double): Path | undefined
```

获取文字的轮廓路径，支持字体回退能力。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Font-getTextPathWithFallback(text: string, byteLength: int, x: double, y: double): Path | undefined--><!--Device-Font-getTextPathWithFallback(text: string, byteLength: int, x: double, y: double): Path | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 表示以UTF-8格式编码的文本字符串。 |
| byteLength | int | 是 | 表示要获取对应文本路径的字节长度，按传入的字节长度和实际的文本字节大小之间的最小值来获取对应的文本路径。 |
| x | double | 是 | 表示文本在绘图区域内以原点为起始位置的X坐标。单位为物理像素px。 |
| y | double | 是 | 表示文本在绘图区域内以原点为起始位置的Y坐标。单位为物理像素px。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Path | 返回获取到的文本路径轮廓。路径对象创建失败时返回undefined。 |

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

## getTypeface

```TypeScript
getTypeface(): Typeface | undefined
```

获取字体。

**起始版本：** 23

<!--Device-Font-getTypeface(): Typeface | undefined--><!--Device-Font-getTypeface(): Typeface | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Typeface](arkts-arkgraphics2d-drawing-typeface-c.md) | 字体。获取失败时返回undefined。 |

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
| glyphs | Array&lt;number&gt; | 是 | 字形索引数组，可由 [textToGlyphs](#texttoglyphs)生成。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;number&gt; | 返回字形宽度数组，浮点数。单位为物理像素px。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |

## getWidths

```TypeScript
getWidths(glyphs: Array<int>): Array<double> | undefined
```

获取字形数组中每个字形对应的宽度。

**起始版本：** 23

<!--Device-Font-getWidths(glyphs: Array<int>): Array<double> | undefined--><!--Device-Font-getWidths(glyphs: Array<int>): Array<double> | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| glyphs | Array&lt;int&gt; | 是 | 字形索引数组，可由 [textToGlyphs](#texttoglyphs)生成。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;double&gt; | 返回字形宽度数组，浮点数。单位为物理像素px。获取失败时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |

## isBaselineSnap

```TypeScript
isBaselineSnap(): boolean
```

当前画布矩阵轴对齐时，获取字型基线是否与像素对齐的结果。

**起始版本：** 23

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-isBaselineSnap(): boolean--><!--Device-Font-isBaselineSnap(): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回字型基线是否与像素对齐，true表示对齐，false表示不对齐。 |

## isEmbeddedBitmaps

```TypeScript
isEmbeddedBitmaps(): boolean
```

获取字型是否使用内嵌位图渲染的结果。

**起始版本：** 23

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-isEmbeddedBitmaps(): boolean--><!--Device-Font-isEmbeddedBitmaps(): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回字型是否使用内嵌位图渲染的结果，true表示使用内嵌位图字形，false表示不转换成位图处理。 |

## isEmbolden

```TypeScript
isEmbolden(): boolean
```

获取字型是否设置了粗体效果。

**起始版本：** 23

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

获取字型是否自动调整轮廓以优化渲染效果的结果。

**起始版本：** 23

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-isForceAutoHinting(): boolean--><!--Device-Font-isForceAutoHinting(): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回字型是否自动调整轮廓以优化渲染效果的结果，true为自动调整，false为不自动调整。 |

## isLinearMetrics

```TypeScript
isLinearMetrics(): boolean
```

获取字型是否可以线性缩放。

**起始版本：** 23

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

获取字型是否使用亚像素渲染。

**起始版本：** 23

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-isSubpixel(): boolean--><!--Device-Font-isSubpixel(): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回字型是否使用亚像素渲染的结果，true表示使用，false表示不使用。 |

## isThemeFontFollowed

```TypeScript
isThemeFontFollowed(): boolean
```

获取字型中的字体是否跟随主题字体。默认不跟随。

**起始版本：** 23

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-isThemeFontFollowed(): boolean--><!--Device-Font-isThemeFontFollowed(): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回字型中的字体是否跟随主题字体的结果，true表示跟随主题字体，false表示不跟随主题字体。 |

## measureSingleCharacter

```TypeScript
measureSingleCharacter(text: string): double
```

测量单个字符的宽度。当前字型中的字体不支持待测量字符时，退化到使用系统字体测量字符宽度。

**起始版本：** 23

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
| double | 字符的宽度，浮点数。单位为物理像素px。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; 3. Parameter verification failed. |

## measureSingleCharacterWithFeatures

```TypeScript
measureSingleCharacterWithFeatures(text: string, features: Array<FontFeature>): double
```

测量单个字符的宽度，字符带有字体特征。当前字型中的字体不支持待测量字符时，退化到使用系统字体测量字符宽度。

**起始版本：** 24

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-measureSingleCharacterWithFeatures(text: string, features: Array<FontFeature>): double--><!--Device-Font-measureSingleCharacterWithFeatures(text: string, features: Array<FontFeature>): double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 待测量的单个字符。字符串长度必须为1。 |
| features | Array&lt;FontFeature&gt; | 是 | 字体特征对象数组。参数为空数组时使用TTF（TrueType Font）文件中预设的字体特征。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | 字符的宽度，浮点数。单位为物理像素px。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [25900001](../errorcode-drawing.md#25900001-参数值异常) | Parameter error. Possible causes: Incorrect parameter range. |

## measureText

```TypeScript
measureText(text: string, encoding: TextEncoding): double
```

测量文本的宽度。 > **说明：** > > 此接口用于测量原始字符串的文本宽度，若想测量排版后的文本宽度，建议使用 > [measure.measureText](../../../reference/apis-arkui/arkts-apis-uicontext-measureutils.md#measuretext12)替代。

**起始版本：** 23

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-measureText(text: string, encoding: TextEncoding): double--><!--Device-Font-measureText(text: string, encoding: TextEncoding): double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 待测量的文本内容，将按encoding指定的编码方式进行解析。 |
| encoding | TextEncoding | 是 | 指定文本的编码格式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | 文本的宽度，浮点数。单位为物理像素px。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |

## setBaselineSnap

```TypeScript
setBaselineSnap(isBaselineSnap: boolean): void
```

当前画布矩阵轴对齐时，设置字型基线是否与像素对齐。

**起始版本：** 23

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-setBaselineSnap(isBaselineSnap: boolean): void--><!--Device-Font-setBaselineSnap(isBaselineSnap: boolean): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isBaselineSnap | boolean | 是 | 表示字型基线是否与像素对齐，true表示对齐，false表示不对齐。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |

## setEdging

```TypeScript
setEdging(edging: FontEdging): void
```

设置字型边缘效果。

**起始版本：** 23

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
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; 3. Parameter verification failed. |

## setEmbeddedBitmaps

```TypeScript
setEmbeddedBitmaps(isEmbeddedBitmaps: boolean): void
```

设置字型是否使用字体文件中内嵌的位图字形进行渲染。

**起始版本：** 23

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-setEmbeddedBitmaps(isEmbeddedBitmaps: boolean): void--><!--Device-Font-setEmbeddedBitmaps(isEmbeddedBitmaps: boolean): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEmbeddedBitmaps | boolean | 是 | 设置字型是否使用字体文件中内嵌的位图字形进行渲染，true表示使用内嵌位图字形，false表示不转换成位图处理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |

## setForceAutoHinting

```TypeScript
setForceAutoHinting(isForceAutoHinting: boolean): void
```

设置是否自动调整字型轮廓以优化渲染效果。

**起始版本：** 23

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-setForceAutoHinting(isForceAutoHinting: boolean): void--><!--Device-Font-setForceAutoHinting(isForceAutoHinting: boolean): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isForceAutoHinting | boolean | 是 | 是否自动调整字型轮廓以优化渲染效果，true为自动调整，false为不自动调整。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |

## setHinting

```TypeScript
setHinting(hinting: FontHinting): void
```

设置字型轮廓效果。

**起始版本：** 23

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
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; 3. Parameter verification failed. |

## setScaleX

```TypeScript
setScaleX(scaleX: double): void
```

设置字型在x轴方向上的缩放比例。

**起始版本：** 23

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-setScaleX(scaleX: double): void--><!--Device-Font-setScaleX(scaleX: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scaleX | double | 是 | 字型在x轴上的缩放比例，该参数为浮点数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |

## setSize

```TypeScript
setSize(textSize: double): void
```

设置字型大小。

**起始版本：** 23

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-setSize(textSize: double): void--><!--Device-Font-setSize(textSize: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| textSize | double | 是 | 字型大小。该参数为浮点数，为负数时会被置为0，为0时绘制的文字不会显示。单位为物理像素px。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; 3. Parameter verification failed. |

## setSkewX

```TypeScript
setSkewX(skewX: double): void
```

设置字型在x轴方向上的倾斜比例。

**起始版本：** 23

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Font-setSkewX(skewX: double): void--><!--Device-Font-setSkewX(skewX: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| skewX | double | 是 | 字型在x轴方向上的倾斜比例，正数表示向左倾斜，负数表示向右倾斜，该参数为浮点数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |

## setThemeFontFollowed

```TypeScript
setThemeFontFollowed(followed: boolean): void
```

设置字型中的字体是否跟随主题字体。设置跟随主题字体后，若系统启用主题字体并且字型未被设置字体，字型会使用该主题字体。

**起始版本：** 23

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
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |

## setTypeface

```TypeScript
setTypeface(typeface: Typeface): void
```

为字型设置字体样式（包括字体名称、粗细、斜体等属性）。

**起始版本：** 23

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
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |

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
| text | string | 是 | 待转换为字形索引的文本字符串。 |
| glyphCount | number | 否 | 文本表示的字符数量，该参数为整数。传入时必须与[countText](#counttext)获取的值相等，不传入时默认为 text表示的字符数量。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;number&gt; | 返回转换得到的字形索引数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |

## textToGlyphs

```TypeScript
textToGlyphs(text: string, glyphCount?: int): Array<int> | undefined
```

将文本转换为字形索引。

**起始版本：** 23

<!--Device-Font-textToGlyphs(text: string, glyphCount?: int): Array<int> | undefined--><!--Device-Font-textToGlyphs(text: string, glyphCount?: int): Array<int> | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 待转换为字形索引的文本字符串。 |
| glyphCount | int | 否 | 文本表示的字符数量，必须与[countText](#counttext)获取的值相等。 当不传该参数，或者glyphCount传入undefined时，默认为text的字符数量，该参数为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;int&gt; | 返回转换得到的字形索引数组。创建失败时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |

