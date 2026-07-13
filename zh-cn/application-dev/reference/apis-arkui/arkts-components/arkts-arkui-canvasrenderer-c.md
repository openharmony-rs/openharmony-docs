# CanvasRenderer

CanvasRenderingContext2D对象与Canvas组件绑定后，可在Canvas组件上绘制，绘制对象可以是形状、文本、图片等。

> **说明：**
>
> * 建议使用时将CanvasRenderingContext2D对象与Canvas组件封装到同一个自定义组件中，保证两者一一对应且生命周期保持一致。
>
> * 本文绘制接口在调用时会存入被关联的Canvas组件的指令队列中。仅当当前帧进入渲染阶段且关联的Canvas组件处于可见状态时，
> 这些指令才会从队列中被提取并执行。因此，在Canvas组件不可见的情况下，应尽量避免频繁调用绘制接口，
> 以防止指令在队列中堆积，从而避免内存占用过大的问题。
>
> * Canvas组件的宽或高超过8000px时使用CPU渲染，会导致性能明显下降。

**继承/实现关系：** CanvasRenderer extends [CanvasPath](arkts-arkui-canvaspath-c.md)

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## beginPath

```TypeScript
beginPath(): void
```

创建一个绘制路径。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## clearRect

```TypeScript
clearRect(x: number, y: number, w: number, h: number): void
```

删除指定区域内的绘制内容。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | 指定矩形上的左上角x坐标。<br>异常值undefined、null、NaN或Infinity按无效值处理，不进行绘制。<br>默认单位：vp |
| y | number | 是 | 指定矩形上的左上角y坐标。<br>异常值undefined、null、NaN或Infinity按无效值处理，不进行绘制。<br>默认单位：vp |
| w | number | 是 | 指定矩形的宽度。<br>异常值undefined、null、NaN或Infinity按无效值处理，不进行绘制。<br>默认单位：vp |
| h | number | 是 | 指定矩形的高度。<br>异常值undefined、null、NaN或Infinity按无效值处理，不进行绘制。<br>默认单位：vp |

## clip

```TypeScript
clip(fillRule?: CanvasFillRule): void
```

设置当前路径为剪切路径。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fillRule | CanvasFillRule | 否 | 指定要剪切对象的规则。<br>可选参数为："nonzero"，"evenodd"。<br>异常值undefined或null按默认值处理。<br>默认值："nonzero" |

## clip

```TypeScript
clip(path: Path2D, fillRule?: CanvasFillRule): void
```

设置指定路径为剪切路径。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | Path2D | 是 | Path2D剪切路径。<br>异常值undefined或null按无效值处理。 |
| fillRule | CanvasFillRule | 否 | 指定要剪切对象的规则。<br>可选参数为："nonzero"，"evenodd"。<br>异常值undefined或null按默认值处理。<br>默认值："nonzero" |

## createConicGradient

```TypeScript
createConicGradient(
    startAngle: number,
    x: number,
    y: number
  ): CanvasGradient
```

创建一个锥形渐变。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| startAngle | number | 是 | 渐变起始角度。角度测量从中心右侧水平方向开始，顺时针移动。<br>异常值undefined或null按0处理。NaN和Infinity按无效值处理。<br>单位：弧度 |
| x | number | 是 | 锥形渐变圆心的x轴坐标。<br>异常值undefined或null按0处理。NaN和Infinity按无效值处理。<br>默认单位：vp |
| y | number | 是 | 锥形渐变圆心的y轴坐标。<br>异常值undefined或null按0处理。NaN和Infinity按无效值处理。<br>默认单位：vp |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| CanvasGradient | 新的CanvasGradient对象，用于在画布上创建渐变。 |

## createImageData

```TypeScript
createImageData(sw: number, sh: number): ImageData
```

创建一个指定大小的空白ImageData对象。此接口涉及耗时的内存拷贝，请避免频繁调用。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sw | number | 是 | ImageData对象的宽度。<br>异常值undefined、null、NaN和Infinity按0处理。<br>默认单位：vp |
| sh | number | 是 | ImageData对象的高度。<br>异常值undefined、null、NaN和Infinity按0处理。<br>默认单位：vp |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ImageData | 新的ImageData对象。 |

## createImageData

```TypeScript
createImageData(imageData: ImageData): ImageData
```

创建一个与已有ImageData对象具有相同宽高的ImageData对象。此接口涉及耗时的内存拷贝，请避免频繁调用。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| imageData | ImageData | 是 | 已有的ImageData对象。<br>异常值undefined和null按宽高为0的ImageData处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ImageData | 新的ImageData对象。 |

## createLinearGradient

```TypeScript
createLinearGradient(x0: number, y0: number, x1: number, y1: number): CanvasGradient
```

创建一个线性渐变。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x0 | number | 是 | 起点的x轴坐标。<br>异常值undefined或null时接口返回undefined。NaN和Infinity按无效值处理。<br>默认单位：vp |
| y0 | number | 是 | 起点的y轴坐标。<br>异常值undefined或null时接口返回undefined。NaN和Infinity按无效值处理。<br>默认单位：vp |
| x1 | number | 是 | 终点的x轴坐标。<br>异常值undefined或null时接口返回undefined。NaN和Infinity按无效值处理。<br>默认单位：vp |
| y1 | number | 是 | 终点的y轴坐标。<br>异常值undefined或null时接口返回undefined。NaN和Infinity按无效值处理。<br>默认单位：vp |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| CanvasGradient | 新的CanvasGradient对象，用于在画布上创建渐变。 |

## createPattern

```TypeScript
createPattern(image: ImageBitmap, repetition: string | null): CanvasPattern | null
```

根据指定的源图像和重复模式创建一个用于图像填充的模式。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| image | ImageBitmap | 是 | 图源对象，具体参考ImageBitmap对象。<br>异常值undefined或null按无效值处理。 |
| repetition | string \| null | 是 | 设置图像重复的方式：<br>'repeat'：沿x轴和y轴重复绘制图像；<br>'repeat-x'：沿x轴重复绘制图像；<br>'repeat-y'：沿y轴重复绘制图像；<br>'no-repeat'：不重复绘制图像；<br>'clamp'：在原始边界外绘制时，超出部分使用边缘的颜色绘制；<br>'mirror'：沿x轴和y轴重复翻转绘制图像。<br>异常值undefined或null按无效值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| CanvasPattern | 通过指定图像和重复方式创建图片填充的模板对象。 |

## createRadialGradient

```TypeScript
createRadialGradient(x0: number, y0: number, r0: number, x1: number, y1: number, r1: number): CanvasGradient
```

创建一个径向渐变。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x0 | number | 是 | 起始圆的圆心x轴坐标。<br>异常值undefined或null时接口返回undefined。NaN和Infinity按无效值处理。<br>默认单位：vp |
| y0 | number | 是 | 起始圆的圆心y轴坐标。<br>异常值undefined或null时接口返回undefined。NaN和Infinity按无效值处理。<br>默认单位：vp |
| r0 | number | 是 | 起始圆的半径，必须是非负有限数。<br>异常值undefined或null时接口返回undefined。NaN和Infinity按无效值处理。<br>默认单位：vp |
| x1 | number | 是 | 终止圆的圆心x轴坐标。<br>异常值undefined或null时接口返回undefined。NaN和Infinity按无效值处理。<br>默认单位：vp |
| y1 | number | 是 | 终止圆的圆心y轴坐标。<br>异常值undefined或null时接口返回undefined。NaN和Infinity按无效值处理。<br>默认单位：vp |
| r1 | number | 是 | 终止圆的半径，必须是非负有限数。<br>异常值undefined或null时接口返回undefined。NaN和Infinity按无效值处理。<br>默认单位：vp |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| CanvasGradient | 新的CanvasGradient对象，用于在画布上创建渐变。 |

## drawImage

```TypeScript
drawImage(image: ImageBitmap | PixelMap, dx: number, dy: number): void
```

在画布上绘制图像。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| image | ImageBitmap \| PixelMap | 是 | 图片资源，请参考ImageBitmap或PixelMap。<br>异常值undefined或null按无效值处理，不进行绘制。 |
| dx | number | 是 | 绘制区域左上角在x轴的位置。<br>异常值undefined或null按0处理，NaN和Infinity按无效值处理，不进行绘制。<br>默认单位：vp |
| dy | number | 是 | 绘制区域左上角在y轴的位置。<br>异常值undefined或null按0处理，NaN和Infinity按无效值处理，不进行绘制。<br>默认单位：vp |

## drawImage

```TypeScript
drawImage(image: ImageBitmap | PixelMap, dx: number, dy: number, dw: number, dh: number): void
```

将图像拉伸或压缩到指定尺寸后绘制。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| image | ImageBitmap \| PixelMap | 是 | 图片资源，请参考ImageBitmap或PixelMap。<br>异常值undefined或null按无效值处理，不进行绘制。 |
| dx | number | 是 | 绘制区域左上角在x轴的位置。<br>异常值undefined或null按0处理，NaN和Infinity按无效值处理，不进行绘制。<br>默认单位：vp |
| dy | number | 是 | 绘制区域左上角在y轴的位置。<br>异常值undefined或null按0处理，NaN和Infinity按无效值处理，不进行绘制。<br>默认单位：vp |
| dw | number | 是 | 绘制区域的宽度。当绘制区域的宽度和裁剪图像的宽度不一致时，将图像宽度拉伸或压缩为绘制区域的宽度。<br>负数、异常值undefined或null按0处理，NaN和Infinity按无效值处理，不进行绘制。<br>默认单位：vp |
| dh | number | 是 | 绘制区域的高度。当绘制区域的高度和裁剪图像的高度不一致时，将图像高度拉伸或压缩为绘制区域的高度。<br>负数、异常值undefined或null按0处理，NaN和Infinity按无效值处理，不进行绘制。<br>默认单位：vp |

## drawImage

```TypeScript
drawImage(
    image: ImageBitmap | PixelMap,
    sx: number,
    sy: number,
    sw: number,
    sh: number,
    dx: number,
    dy: number,
    dw: number,
    dh: number,
  ): void
```

将图像裁剪后拉伸或压缩到指定尺寸后绘制。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| image | ImageBitmap \| PixelMap | 是 | 图片资源，请参考ImageBitmap或PixelMap。<br>异常值undefined或null按无效值处理，不进行绘制。 |
| sx | number | 是 | 裁剪源图像时矩形左上角的x轴坐标。<br>异常值undefined或null按0处理，NaN和Infinity按无效值处理，不进行绘制。<br>默认单位：vp |
| sy | number | 是 | 裁剪源图像时矩形左上角的y轴坐标。<br>异常值undefined或null按0处理，NaN和Infinity按无效值处理，不进行绘制。<br>默认单位：vp |
| sw | number | 是 | 裁剪源图像的目标宽度。<br>负数、异常值undefined或null按0处理，NaN和Infinity按无效值处理，不进行绘制。<br>默认单位：vp |
| sh | number | 是 | 裁剪源图像的目标高度。<br>负数、异常值undefined或null按0处理，NaN和Infinity按无效值处理，不进行绘制。<br>默认单位：vp |
| dx | number | 是 | 绘制区域左上角在x轴的位置。<br>异常值undefined或null按0处理，NaN和Infinity按无效值处理，不进行绘制。<br>默认单位：vp |
| dy | number | 是 | 绘制区域左上角在y轴的位置。<br>异常值undefined或null按0处理，NaN和Infinity按无效值处理，不进行绘制。<br>默认单位：vp |
| dw | number | 是 | 绘制区域的宽度。当绘制区域的宽度和裁剪图像的宽度不一致时，将图像宽度拉伸或压缩为绘制区域的宽度。<br>负数、异常值undefined或null按0处理，NaN和Infinity按无效值处理，不进行绘制。<br>默认单位：vp |
| dh | number | 是 | 绘制区域的高度。当绘制区域的高度和裁剪图像的高度不一致时，将图像高度拉伸或压缩为绘制区域的高度。<br>负数、异常值undefined或null按0处理，NaN和Infinity按无效值处理，不进行绘制。<br>默认单位：vp |

## fill

```TypeScript
fill(fillRule?: CanvasFillRule): void
```

填充当前路径。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fillRule | CanvasFillRule | 否 | 指定要填充对象的规则。<br>可选参数为："nonzero"，"evenodd"。<br>异常值undefined或null按默认值处理。<br>默认值："nonzero" |

## fill

```TypeScript
fill(path: Path2D, fillRule?: CanvasFillRule): void
```

填充指定路径。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | Path2D | 是 | Path2D填充路径。<br>异常值undefined或null按无效值处理。 |
| fillRule | CanvasFillRule | 否 | 指定要填充对象的规则。<br>可选参数为："nonzero"，"evenodd"。<br>异常值undefined或null按默认值处理。<br>默认值："nonzero" |

## fillRect

```TypeScript
fillRect(x: number, y: number, w: number, h: number): void
```

填充一个矩形。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | 指定矩形左上角点的x坐标。<br>异常值undefined、null、NaN或Infinity按无效值处理，不进行绘制。<br>默认单位：vp |
| y | number | 是 | 指定矩形左上角点的y坐标。<br>异常值undefined、null、NaN或Infinity按无效值处理，不进行绘制。<br>默认单位：vp |
| w | number | 是 | 指定矩形的宽度。<br>异常值undefined、null、NaN或Infinity按无效值处理，不进行绘制。<br>默认单位：vp |
| h | number | 是 | 指定矩形的高度。<br>异常值undefined、null、NaN或Infinity按无效值处理，不进行绘制。<br>默认单位：vp |

## fillText

```TypeScript
fillText(text: string, x: number, y: number, maxWidth?: number): void
```

绘制填充类文本。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 需要绘制的文本内容。<br>异常值undefined或null按无效值处理，不进行绘制。 |
| x | number | 是 | 文本绘制起点的x轴坐标。<br>异常值undefined、null、NaN或Infinity按无效值处理，不进行绘制。<br>默认单位：vp |
| y | number | 是 | 文本绘制起点的y轴坐标。<br>异常值undefined、null、NaN或Infinity按无效值处理，不进行绘制。<br>默认单位：vp |
| maxWidth | number | 否 | 指定文本允许的最大宽度。<br>异常值null按无效值处理，不进行绘制，undefined、NaN或Infinity按默认值处理。<br>默认值：不限制宽度。<br>默认单位：vp |

## getImageData

```TypeScript
getImageData(sx: number, sy: number, sw: number, sh: number): ImageData
```

获取画布上指定区域内的像素数据创建一个ImageData对象。此接口涉及耗时的内存拷贝，请避免频繁调用。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sx | number | 是 | 输出区域左上角的x轴坐标。<br>异常值undefined、null、NaN和Infinity按0处理。<br>默认单位：vp |
| sy | number | 是 | 输出区域左上角的y轴坐标。<br>异常值undefined、null、NaN和Infinity按0处理。<br>默认单位：vp |
| sw | number | 是 | 输出区域的宽度。<br>异常值undefined、null、NaN和Infinity按0处理。<br>默认单位：vp |
| sh | number | 是 | 输出区域的高度。<br>异常值undefined、null、NaN和Infinity按0处理。<br>默认单位：vp |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ImageData | 新的ImageData对象。 |

## getLineDash

```TypeScript
getLineDash(): number[]
```

获取虚线样式。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number[] | @syscap SystemCapability.ArkUI.ArkUI.Full@FaAndStageModel@crossplatform |

## getPixelMap

```TypeScript
getPixelMap(sx: number, sy: number, sw: number, sh: number): PixelMap
```

获取画布上指定区域内的像素数据创建一个PixelMap对象。此接口涉及耗时的内存拷贝，请避免频繁调用。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sx | number | 是 | 输出区域左上角的x轴坐标。<br>异常值undefined、null、NaN和Infinity按0处理。<br>默认单位：vp |
| sy | number | 是 | 输出区域左上角的y轴坐标。<br>异常值undefined、null、NaN和Infinity按0处理。<br>默认单位：vp |
| sw | number | 是 | 输出区域的宽度。<br>异常值undefined、null、NaN和Infinity按0处理。<br>默认单位：vp |
| sh | number | 是 | 输出区域的高度。<br>异常值undefined、null、NaN和Infinity按0处理。<br>默认单位：vp |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PixelMap | PixelMap对象。 |

## getTransform

```TypeScript
getTransform(): Matrix2D
```

获取当前应用到上下文的变换矩阵。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Matrix2D | 当前被应用到上下文的转换矩阵。 |

## measureText

```TypeScript
measureText(text: string): TextMetrics
```

该方法返回一个文本测算的对象，通过该对象可以获取指定文本的宽度值。不同设备上获取的宽度值可能不同。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 需要进行测量的文本。<br>传入异常值undefined或null时按"undefined"或"null"计算。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| TextMetrics | 文本的尺寸信息。 |

## putImageData

```TypeScript
putImageData(imageData: ImageData, dx: number | string, dy: number | string): void
```

将一个ImageData对象放到画布上的矩形区域。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| imageData | ImageData | 是 | 含有像素数据的ImageData对象，用于放到画布上。<br>异常值undefined和null按无效值处理，不进行绘制。 |
| dx | number \| string | 是 | 画布上矩形区域的x轴偏移量。<br>异常值undefined、null、NaN和Infinity按0处理。<br>默认单位：vp |
| dy | number \| string | 是 | 画布上矩形区域的y轴偏移量。<br>异常值undefined、null、NaN和Infinity按0处理。<br>默认单位：vp |

## putImageData

```TypeScript
putImageData(
    imageData: ImageData,
    dx: number | string,
    dy: number | string,
    dirtyX: number | string,
    dirtyY: number | string,
    dirtyWidth: number | string,
    dirtyHeight: number | string
  ): void
```

将裁剪后的ImageData数据填充到新的矩形区域。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| imageData | ImageData | 是 | 含有像素数据的ImageData对象，用于放到画布上。<br>异常值undefined和null按无效值处理，不进行绘制。 |
| dx | number \| string | 是 | 画布上矩形区域的x轴偏移量。<br>异常值undefined、null、NaN和Infinity按0处理。<br>默认单位：vp |
| dy | number \| string | 是 | 画布上矩形区域的y轴偏移量。<br>异常值undefined、null、NaN和Infinity按0处理。<br>默认单位：vp |
| dirtyX | number \| string | 是 | 源图像矩形区域左上角相对于源图像左上角的x轴偏移量。<br>异常值undefined、null、NaN和Infinity按0处理。<br>默认单位：vp |
| dirtyY | number \| string | 是 | 源图像矩形区域左上角相对于源图像左上角的y轴偏移量。<br>异常值undefined、null、NaN和Infinity按0处理。<br>默认单位：vp |
| dirtyWidth | number \| string | 是 | 源图像裁剪矩形的宽度。<br>异常值undefined、null、NaN和Infinity按0处理。<br>默认单位：vp |
| dirtyHeight | number \| string | 是 | 源图像裁剪矩形的高度。<br>异常值undefined、null、NaN和Infinity按0处理。<br>默认单位：vp |

## reset

```TypeScript
reset(): void
```

将CanvasRenderingContext2D对象重置为默认状态，并清除背景缓冲区、绘制状态堆栈、已定义路径和样式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## resetTransform

```TypeScript
resetTransform(): void
```

重置当前变换矩阵为单位矩阵。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## restore

```TypeScript
restore(): void
```

恢复之前保存的绘制上下文。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## restoreLayer

```TypeScript
restoreLayer(): void
```

将图像变换和裁剪状态恢复到saveLayer之前的状态，然后将图层绘制到画布上。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## rotate

```TypeScript
rotate(angle: number): void
```

围绕坐标轴顺时针旋转画布。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| angle | number | 是 | 设置顺时针旋转的弧度值，可以通过 degree * Math.PI / 180 将角度转换为弧度值。<br>API version 18之前，设置NaN或Infinity时，在该方法后执行的绘制方法无法绘制；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的绘制方法正常绘制。<br>单位：弧度 |

## save

```TypeScript
save(): void
```

保存所有画布状态到栈中。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## saveLayer

```TypeScript
saveLayer(): void
```

保存当前图层。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scale

```TypeScript
scale(x: number, y: number): void
```

根据给定的缩放因子缩放画布。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | 设置水平方向的缩放值。<br>API version 18之前，设置NaN或Infinity时，在该方法后执行的绘制方法无法绘制；不支持设置0和负数，设置0、负数、null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、0、负数、null或undefined时当前接口不生效，其他传入有效参数的绘制方法正常绘制。 |
| y | number | 是 | 设置垂直方向的缩放值，不支持设置负数。<br>API version 18之前，设置NaN或Infinity时，在该方法后执行的绘制方法无法绘制；不支持设置0和负数，设置0、负数、null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、0、负数、null或undefined时当前接口不生效，其他传入有效参数的绘制方法正常绘制。 |

## setLineDash

```TypeScript
setLineDash(segments: number[]): void
```

设置虚线样式。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| segments | number[] | 是 | 一个数字数组，指定交替绘制线和间距的距离。<br>异常值undefined和null按无效值处理。<br>默认单位：vp |

## setPixelMap

```TypeScript
setPixelMap(value?: PixelMap): void
```

在画布上绘制输入的PixelMap对象。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | PixelMap | 否 | 含有像素值的PixelMap对象。<br>异常值undefined和null按无效值处理，不进行绘制。<br>默认值：null |

## setTransform

```TypeScript
setTransform(a: number, b: number, c: number, d: number, e: number, f: number): void
```

setTransform方法使用的参数和transform()方法相同，但setTransform()方法会重置现有的变换矩阵并创建新的变换矩阵。

> **说明：**
>
> 图形中各个点变换后的坐标可通过下方坐标计算公式计算。
>
> 变换后的坐标计算方式（x和y为变换前坐标，x'和y'为变换后坐标）：
>
> - x' = a * x + c * y + e
>
> - y' = b * x + d * y + f

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| a | number | 是 | scaleX：指定水平缩放值，支持设置负数。<br>API version 18之前，设置NaN或Infinity时，在该方法后执行的绘制方法无法绘制；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的绘制方法正常绘制。 |
| b | number | 是 | skewY：指定垂直倾斜值，支持设置负数。<br>API version 18之前，设置NaN或Infinity时，在该方法后执行的绘制方法无法绘制；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的绘制方法正常绘制。 |
| c | number | 是 | skewX：指定水平倾斜值，支持设置负数。<br>API version 18之前，设置NaN或Infinity时，在该方法后执行的绘制方法无法绘制；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的绘制方法正常绘制。 |
| d | number | 是 | scaleY：指定垂直缩放值，支持设置负数。<br>API version 18之前，设置NaN或Infinity时，在该方法后执行的绘制方法无法绘制；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的绘制方法正常绘制。 |
| e | number | 是 | translateX：指定水平移动值，支持设置负数。<br>API version 18之前，设置NaN或Infinity时，在该方法后执行的绘制方法无法绘制；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的绘制方法正常绘制。<br>默认单位：vp |
| f | number | 是 | translateY：指定垂直移动值，支持设置负数。<br>API version 18之前，设置NaN或Infinity时，在该方法后执行的绘制方法无法绘制；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的绘制方法正常绘制。<br>默认单位：vp |

## setTransform

```TypeScript
setTransform(transform?: Matrix2D): void
```

以Matrix2D对象为模板重置现有的变换矩阵并创建新的变换矩阵。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| transform | Matrix2D | 否 | 变换矩阵。<br>异常值undefined或null按无效值处理。<br>默认值：null |

## stroke

```TypeScript
stroke(): void
```

描边当前路径。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## stroke

```TypeScript
stroke(path: Path2D): void
```

描边指定路径。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | Path2D | 是 | 需要绘制的Path2D。<br>异常值undefined或null按无效值处理，不进行绘制。 |

## strokeRect

```TypeScript
strokeRect(x: number, y: number, w: number, h: number): void
```

绘制具有边框的矩形，矩形内部不填充。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | 指定矩形的左上角x坐标。<br>异常值undefined、null、NaN或Infinity按无效值处理，不进行绘制。<br>默认单位：vp |
| y | number | 是 | 指定矩形的左上角y坐标。<br>异常值undefined、null、NaN或Infinity按无效值处理，不进行绘制。<br>默认单位：vp |
| w | number | 是 | 指定矩形的宽度。<br>异常值undefined、null、NaN或Infinity按无效值处理，不进行绘制。<br>默认单位：vp |
| h | number | 是 | 指定矩形的高度。<br>异常值undefined、null、NaN或Infinity按无效值处理，不进行绘制。<br>默认单位：vp |

## strokeText

```TypeScript
strokeText(text: string, x: number, y: number, maxWidth?: number): void
```

绘制描边类文本。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 需要绘制的文本内容。<br>异常值undefined或null按无效值处理，不进行绘制。 |
| x | number | 是 | 文本绘制起点的x轴坐标。<br>异常值undefined、null、NaN或Infinity按无效值处理，不进行绘制。<br>默认单位：vp |
| y | number | 是 | 文本绘制起点的y轴坐标。<br>异常值undefined、null、NaN或Infinity按无效值处理，不进行绘制。<br>默认单位：vp |
| maxWidth | number | 否 | 需要绘制的文本的最大宽度。<br>异常值null按无效值处理，不进行绘制，undefined、NaN或Infinity按默认值处理。<br>默认单位：vp<br>默认值：不限制宽度。 |

## transferFromImageBitmap

```TypeScript
transferFromImageBitmap(bitmap: ImageBitmap): void
```

显示指定的ImageBitmap对象。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bitmap | ImageBitmap | 是 | 需要显示的ImageBitmap对象。 |

## transform

```TypeScript
transform(a: number, b: number, c: number, d: number, e: number, f: number): void
```

transform方法对应一个变换矩阵，想对一个图形进行变化的时候，只要设置此变换矩阵相应的参数，
对图形的各个定点的坐标分别乘以这个矩阵，就能得到新的定点的坐标。矩阵变换效果可叠加。

> **说明：**
>
> 图形中各个点变换后的坐标可通过下方坐标计算公式计算。
>
> 变换后的坐标计算方式（x和y为变换前坐标，x'和y'为变换后坐标）：
>
> - x' = a * x + c * y + e
>
> - y' = b * x + d * y + f

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| a | number | 是 | 变换矩阵中第一行第一列的单元格。scaleX：指定水平缩放值，支持设置负数。<br>API version 18之前，设置NaN或Infinity时，在该方法后执行的绘制方法无法绘制；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的绘制方法正常绘制。 |
| b | number | 是 | 变换矩阵第二行第一列的单元格。skewY：指定垂直倾斜值，支持设置负数。<br>API version 18之前，设置NaN或Infinity时，在该方法后执行的绘制方法无法绘制；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的绘制方法正常绘制。 |
| c | number | 是 | 变换矩阵第一行第二列的单元格。skewX：指定水平倾斜值，支持设置负数。<br>API version 18之前，设置NaN或Infinity时，在该方法后执行的绘制方法无法绘制；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的绘制方法正常绘制。 |
| d | number | 是 | 变换矩阵第二行第二列的单元格。scaleY：指定垂直缩放值，支持设置负数。<br>API version 18之前，设置NaN或Infinity时，在该方法后执行的绘制方法无法绘制；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的绘制方法正常绘制。 |
| e | number | 是 | 变换矩阵第一行第三列的单元格。translateX：指定水平移动值，支持设置负数。<br>API version 18之前，设置NaN或Infinity时，在该方法后执行的绘制方法无法绘制；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的绘制方法正常绘制。<br>默认单位：vp |
| f | number | 是 | 变换矩阵第二行第三列的单元格。translateY：指定垂直移动值，支持设置负数。<br>API version 18之前，设置NaN或Infinity时，在该方法后执行的绘制方法无法绘制；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的绘制方法正常绘制。<br>默认单位：vp |

## translate

```TypeScript
translate(x: number, y: number): void
```

移动当前坐标系的原点。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | 设置水平平移量。<br>API version 18之前，设置NaN或Infinity时，在该方法后执行的绘制方法无法绘制；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的绘制方法正常绘制。<br>默认单位：vp |
| y | number | 是 | 设置竖直平移量。<br>API version 18之前，设置NaN或Infinity时，在该方法后执行的绘制方法无法绘制；设置null或undefined时，当前接口不生效。API version 18及以后，设置NaN、Infinity、null或undefined时当前接口不生效，其他传入有效参数的绘制方法正常绘制。<br>默认单位：vp |

## antialias

```TypeScript
antialias: boolean | undefined
```

用于设置绘制图形和文本时是否开启抗锯齿。设置此接口会覆盖[RenderingContextSettings](./renderingcontextsettings)中的抗锯齿效果，
未通过该接口设置时，默认值为undefined，与[RenderingContextSettings](./renderingcontextsettings)中的抗锯齿效果保持一致。

设置绘制图形和文本时是否开启抗锯齿。

**true**表示开启抗锯齿；**false**表示不开启抗锯齿。

值为**undefined**时，与[RenderingContextSettings](./renderingcontextsettings)中的抗锯齿效果保持一致。

**类型：** boolean | undefined

**默认值：** undefined

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本24开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction: CanvasDirection
```

用于设置绘制文字时使用的文字方向，此属性为只写属性，可通过赋值语句设置其值，
但无法通过读取操作获取其当前值，若尝试读取将返回undefined。

默认值：**"inherit"**

**类型：** CanvasDirection

**默认值：** inherit

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fillStyle

```TypeScript
fillStyle: string | number | CanvasGradient | CanvasPattern
```

指定绘制的填充色，此属性为只写属性，可通过赋值语句设置其值，但无法通过读取操作获取其当前值，若尝试读取将返回undefined。

- 类型为string时，表示设置填充区域的颜色，颜色格式参考[ResourceColor](../../../../reference/apis-arkui/arkui-ts/ts-types.md#resourcecolor)中string类型说明。

- 类型为number时，表示设置填充区域的颜色，不支持设置全透明色，颜色格式参考[ResourceColor](../../../../reference/apis-arkui/arkui-ts/ts-types.md#resourcecolor)中number类型说明。

- 类型为[CanvasGradient](./canvasgradient)时，表示渐变对象，使用[createLinearGradient](./createlineargradient)方法创建。

- 类型为[CanvasPattern](./canvaspattern)时，使用[createPattern](./createpattern)方法创建。

默认值：'#000000'（黑色）

异常值设置无效，保持设置前效果。

**类型：** string | number | CanvasGradient | CanvasPattern

**默认值：** #000000 (black)

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## filter

```TypeScript
filter: string
```

设置图像的滤镜，此属性为只写属性，可通过赋值语句设置其值，但无法通过读取操作获取其当前值，若尝试读取将返回undefined。

支持的滤镜效果如下：

- **'none'**: 无滤镜效果。
- **'blur(\<length>)'**：给图像设置高斯模糊，取值范围≥0，支持单位px、vp、rem，默认值：blur(0px)。
- **'brightness([\<number>\|\<percentage>])'**：给图片应用一种线性乘法，使其看起来更亮或更暗，支持数字和百分比参数，取值范围≥0，默认值：brightness(1)。
- **'contrast([\<number>\|\<percentage>])'**：调整图像的对比度，支持数字和百分比参数，取值范围≥0，默认值：contrast(1)。
- **'grayscale([\<number>\|\<percentage>])'**：将图像转换为灰度图像，支持数字和百分比参数，取值范围[0, 1]，默认值：grayscale(0)。
- **'hue-rotate(\<angle>)'**：给图像应用色相旋转，取值范围0deg-360deg，默认值：hue-rotate(0deg)。
- **'invert([\<number>\|\<percentage>])'**：反转输入图像，支持数字和百分比参数，取值范围[0, 1]，默认值：invert(0)。
- **'opacity([\<number>\|\<percentage>])'**：调整图像的透明程度，支持数字和百分比参数，取值范围[0, 1]，默认值：opacity(1)。
- **'saturate([\<number>\|\<percentage>])'**：转换图像饱和度，支持数字和百分比参数，取值范围≥0，默认值：saturate(1)。
- **'sepia([\<number>\|\<percentage>])'**：将图像转换为深褐色，支持数字和百分比参数，取值范围[0, 1]，默认值：sepia(0)。

**类型：** string

**默认值：** none

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## font

```TypeScript
font: string
```

设置文本绘制中的字体样式，此属性为只写属性，可通过赋值语句设置其值，
但无法通过读取操作获取其当前值，若尝试读取将返回undefined。

语法：ctx.font&nbsp;=&nbsp;'font-style&nbsp;font-weight&nbsp;font-size&nbsp;font-family'
<br>-&nbsp;font-style(可选)，用于指定字体样式，支持如下几种样式：'normal','italic'。
<br>-&nbsp;font-weight(可选)，用于指定字体的粗细，支持如下几种类型：'normal',&nbsp;'bold',
&nbsp;'bolder',&nbsp;'lighter',&nbsp;100,&nbsp;200,&nbsp;300,&nbsp;400,&nbsp;500,&nbsp;600,
&nbsp;700,&nbsp;800,&nbsp;900。
<br>-&nbsp;font-size(可选)，指定字号和行高，单位支持px、vp。使用时需要添加单位。
<br>-&nbsp;font-family(可选)，指定字体系列，支持如下几种类型：'sans-serif',&nbsp;'serif',
&nbsp;'monospace'。

从API version 20开始，支持通过该接口设置注册过的自定义字体（DevEco Studio的预览器不支持显示自定义字体）。
自定义字体注册有以下两种方式。
一种是通过ArkUI的异步接口
this.uiContext.getFont().[registerFont](../../../../reference/apis-arkui/arkts-apis-uicontext-font.md#registerfont)
注册，调用后立即绘制可能会导致自定义字体不生效。
另一种是直接调用字体引擎的
fontCollection.[loadFontSync](../../../../reference/apis-arkgraphics2d/js-apis-graphics-text.md#loadfontsync)
接口来注册自定义字体到字体引擎。在直接调用字体引擎接口注册自定义字体时，fontCollection的实例需要是
text.FontCollection.getGlobalInstance()，因为组件默认会从该实例加载字体。
如果使用其他实例，可能会导致自定义字体不生效。

**类型：** string

**默认值：** normal normal 14px sans-serif

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## globalAlpha

```TypeScript
globalAlpha: number
```

设置透明度，此属性为只写属性，可通过赋值语句设置其值，但无法通过读取操作获取其当前值，若尝试读取将返回undefined。

范围为[0.0, 1.0]，0.0为完全透明，1.0为完全不透明。若给定值小于0.0，则取值0.0；
若给定值大于1.0，则取值1.0。

API version 18之前，设置NaN或Infinity时，在该方法后执行的绘制方法无法绘制。
API version 18及以后，设置NaN或Infinity时当前接口不生效，其他传入有效参数的绘制方法正常绘制。

默认值：**1.0**

**类型：** number

**默认值：** 1.0

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## globalCompositeOperation

```TypeScript
globalCompositeOperation: string
```

设置合成操作的类型，此属性为只写属性，可通过赋值语句设置其值，但无法通过读取操作获取其当前值，若尝试读取将返回undefined。

类型字段可选值有'source-over'，'source-atop'，'source-in'，'source-out'，
'destination-over'，'destination-atop'，'destination-in'，'destination-out'，
'lighter'，'copy'，'xor'。

| 名称 | 描述 |
| ------ | ------ |
| source-over | 在现有绘制内容上显示新绘制内容，属于默认值。 |
| source-atop | 在现有绘制内容顶部显示新绘制内容。 |
| source-in | 在现有绘制内容中显示新绘制内容。 |
| source-out | 在现有绘制内容之外显示新绘制内容。 |
| destination-over | 在新绘制内容上方显示现有绘制内容。 |
| destination-atop | 在新绘制内容顶部显示现有绘制内容。 |
| destination-in | 在新绘制内容中显示现有绘制内容。 |
| destination-out | 在新绘制内容外显示现有绘制内容。 |
| lighter | 显示新绘制内容和现有绘制内容。 |
| copy | 显示新绘制内容而忽略现有绘制内容。 |
| xor | 使用异或操作对新绘制内容与现有绘制内容进行融合。 |

默认值：**'source-over'**

**类型：** string

**默认值：** source-over

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## imageSmoothingEnabled

```TypeScript
imageSmoothingEnabled: boolean
```

用于设置绘制图片时是否进行图像平滑度调整，true为启用，false为不启用，此属性为只写属性，
可通过赋值语句设置其值，但无法通过读取操作获取其当前值，若尝试读取将返回undefined。

默认值：**true**

**类型：** boolean

**默认值：** true

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## imageSmoothingQuality

```TypeScript
imageSmoothingQuality: ImageSmoothingQuality
```

imageSmoothingEnabled为true时，用于设置图像平滑度，此属性为只写属性，
可通过赋值语句设置其值，但无法通过读取操作获取其当前值，若尝试读取将返回undefined。

默认值：**"low"**

**类型：** ImageSmoothingQuality

**默认值：** low

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## letterSpacing

```TypeScript
letterSpacing: LengthMetrics | string
```

用于指定绘制文本时字母之间的间距，此属性为只写属性，可通过赋值语句设置其值，
但无法通过读取操作获取其当前值，若尝试读取将返回undefined。

当使用LengthMetrics时：

字间距按照指定的单位设置；

不支持FP、PERCENT和LPX（按无效值处理）；

支持负数和小数，设为小数时字间距不四舍五入。

当使用string时：

不支持设置百分比（按无效值处理）；

支持负数和小数，设为小数时字间距不四舍五入；

若letterSpacing的赋值未指定单位（例如：**letterSpacing='10'**），
且未指定LengthMetricsUnit时，默认单位设置为vp；

指定LengthMetricsUnit为px时，默认单位设置为px；

当letterSpacing的赋值指定单位时（例如：**letterSpacing='10vp'**），
字间距按照指定的单位设置。

默认值：**0**（输入无效值时，字间距设为默认值）

> **说明：**
>
> 推荐使用LengthMetrics，性能更好。

**类型：** LengthMetrics | string

**默认值：** 0vp

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## lineCap

```TypeScript
lineCap: CanvasLineCap
```

指定线端点的样式，此属性为只写属性，可通过赋值语句设置其值，但无法通过读取操作获取其当前值，若尝试读取将返回undefined。

**类型：** CanvasLineCap

**默认值：** butt

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## lineDashOffset

```TypeScript
lineDashOffset: number
```

设置画布的虚线偏移量，精度为float，仅当设置setLineDash时属性才生效，此属性为只写属性，
可通过赋值语句设置其值，但无法通过读取操作获取其当前值，若尝试读取将返回undefined。

API version 18之前，设置NaN或Infinity时，设置了虚线样式的线条绘制出来是实线。
API version 18及以后，设置NaN或Infinity时当前接口不生效，设置了虚线样式的线条绘制出来是虚线。

默认值：**0.0**

默认单位：vp

异常值NaN和Infinity按默认值处理。

**类型：** number

**默认值：** 0.0

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## lineJoin

```TypeScript
lineJoin: CanvasLineJoin
```

指定线段间相交的交点样式，此属性为只写属性，可通过赋值语句设置其值，但无法通过读取操作获取其当前值，若尝试读取将返回undefined。
<br>可选值为：
<br>- **'round'**：在线段相连处绘制一个扇形，扇形的圆角半径是线段的宽度。
<br>- **'bevel'**：在线段相连处使用三角形为底填充，每个部分矩形拐角独立。
<br>- **'miter'**：在相连部分的外边缘处进行延伸，使其相交于一点，形成一个菱形区域，
该属性可以通过设置miterLimit属性展现效果。
<br>默认值：**'miter'**

**类型：** CanvasLineJoin

**默认值：** miter

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## lineWidth

```TypeScript
lineWidth: number
```

设置绘制线条的宽度，此属性为只写属性，可通过赋值语句设置其值，但无法通过读取操作获取其当前值，若尝试读取将返回undefined。

默认值：**1**（px）

默认单位：vp

lineWidth取值不支持0和负数，0、负数和NaN按默认值处理，Infinity会导致lineWidth属性异常，不进行绘制。

**类型：** number

**默认值：** 1(px)

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## miterLimit

```TypeScript
miterLimit: number
```

设置斜接面限制值，该值指定了线条相交处内角和外角的距离，仅当设置了lineJoin为miter才生效，
此属性为只写属性，可通过赋值语句设置其值，但无法通过读取操作获取其当前值，若尝试读取将返回undefined。

默认值：**10px**

单位：px

miterLimit取值不支持0和负数，0、负数和NaN按默认值处理，Infinity会导致miterLimit属性异常。

**类型：** number

**默认值：** 10(px)

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shadowBlur

```TypeScript
shadowBlur: number
```

设置绘制阴影时的模糊级别，此属性为只写属性，可通过赋值语句设置其值，
但无法通过读取操作获取其当前值，若尝试读取将返回undefined。

值越大越模糊，精度为float，取值范围≥0。

默认值：**0.0**

单位：px

shadowBlur取值不支持负数，负数、NaN和Infinity按默认值处理。

**类型：** number

**默认值：** 0

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shadowColor

```TypeScript
shadowColor: string
```

设置绘制阴影时的阴影颜色，此属性为只写属性，可通过赋值语句设置其值，
但无法通过读取操作获取其当前值，若尝试读取将返回undefined。

颜色格式参考[ResourceColor](../../../../reference/apis-arkui/arkui-ts/ts-types.md#resourcecolor)中string类型说明。

默认值：透明黑色

**类型：** string

**默认值：** transparent black

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shadowOffsetX

```TypeScript
shadowOffsetX: number
```

设置绘制阴影时和原有对象的水平偏移值，此属性为只写属性，可通过赋值语句设置其值，
但无法通过读取操作获取其当前值，若尝试读取将返回undefined。

默认值：**0.0**

默认单位：vp

异常值NaN和Infinity按默认值处理。

**类型：** number

**默认值：** 0

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shadowOffsetY

```TypeScript
shadowOffsetY: number
```

设置绘制阴影时和原有对象的垂直偏移值，此属性为只写属性，可通过赋值语句设置其值，
但无法通过读取操作获取其当前值，若尝试读取将返回undefined。

默认值：**0.0**

默认单位：vp

异常值NaN和Infinity按默认值处理。

**类型：** number

**默认值：** 0

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeStyle

```TypeScript
strokeStyle: string | number | CanvasGradient | CanvasPattern
```

设置线条的颜色，此属性为只写属性，可通过赋值语句设置其值，但无法通过读取操作获取其当前值，若尝试读取将返回undefined。

- 类型为string时，表示设置线条使用的颜色，颜色格式参考[ResourceColor](../../../../reference/apis-arkui/arkui-ts/ts-types.md#resourcecolor)中string类型说明。

- 类型为number时，表示设置线条使用的颜色，不支持设置全透明色，颜色格式参考[ResourceColor](../../../../reference/apis-arkui/arkui-ts/ts-types.md#resourcecolor)中number类型说明。

- 类型为[CanvasGradient](./canvasgradient)时，表示渐变对象，使用[createLinearGradient](./createlineargradient)方法创建。

- 类型为[CanvasPattern](./canvaspattern)时，使用[createPattern](./createpattern)方法创建。

默认值：'#000000'（黑色）

异常值设置无效，保持设置前效果。

**类型：** string | number | CanvasGradient | CanvasPattern

**默认值：** #000000 (black)

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textAlign

```TypeScript
textAlign: CanvasTextAlign
```

设置文本绘制中的文本对齐方式，此属性为只写属性，可通过赋值语句设置其值，
但无法通过读取操作获取其当前值，若尝试读取将返回undefined。

ltr布局模式下'start'和'left'一致，rtl布局模式下'start'和'right'一致。

默认值：**'left'**

**类型：** CanvasTextAlign

**默认值：** left

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textBaseline

```TypeScript
textBaseline: CanvasTextBaseline
```

设置文本绘制中的水平对齐方式，此属性为只写属性，可通过赋值语句设置其值，但无法通过读取操作获取其当前值，若尝试读取将返回undefined。

默认值：**'alphabetic'**

**类型：** CanvasTextBaseline

**默认值：** alphabetic

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

