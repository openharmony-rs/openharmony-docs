# CanvasRenderer

Canvas渲染器，用于绘制形状、文本、图片等对象。

**继承/实现关系：** CanvasRenderer extends [CanvasPath](arkts-na-canvas-canvaspath-c.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class CanvasRenderer--><!--Device-unnamed-export declare class CanvasRenderer-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## beginPath

```TypeScript
beginPath(): void
```

创建一个新的绘制路径。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-beginPath(): void--><!--Device-CanvasRenderer-beginPath(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## clearRect

```TypeScript
clearRect(x: double, y: double, w: double, h: double): void
```

删除指定区域内的绘制内容。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-clearRect(x: double, y: double, w: double, h: double): void--><!--Device-CanvasRenderer-clearRect(x: double, y: double, w: double, h: double): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | double | 是 | 指定矩形上的左上角x坐标。异常值undefined、null、NaN或Infinity按无效值处理， 不进行绘制。默认单位：vp |
| y | double | 是 | 指定矩形上的左上角y坐标。异常值undefined、null、NaN或Infinity按无效值处理， 不进行绘制。默认单位：vp |
| w | double | 是 | 指定矩形的宽度。异常值undefined、null、NaN或Infinity按无效值处理， 不进行绘制。默认单位：vp |
| h | double | 是 | 指定矩形的高度。异常值undefined、null、NaN或Infinity按无效值处理， 不进行绘制。默认单位：vp |

## clip

```TypeScript
clip(fillRule?: CanvasFillRule): void
```

设置当前路径为剪切路径。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-clip(fillRule?: CanvasFillRule): void--><!--Device-CanvasRenderer-clip(fillRule?: CanvasFillRule): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fillRule | [CanvasFillRule](arkts-na-canvasfillrule-t.md) | 否 | 指定要剪切对象的规则。可选参数为："nonzero"，"evenodd"。 异常值undefined或null按默认值处理。默认值："nonzero" |

## clip

```TypeScript
clip(path: Path2D, fillRule?: CanvasFillRule): void
```

设置指定路径为剪切路径。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-clip(path: Path2D, fillRule?: CanvasFillRule): void--><!--Device-CanvasRenderer-clip(path: Path2D, fillRule?: CanvasFillRule): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | [Path2D](arkts-na-canvas-path2d-c.md) | 是 | Path2D剪切路径。异常值undefined或null按无效值处理。 |
| fillRule | [CanvasFillRule](arkts-na-canvasfillrule-t.md) | 否 | 指定要剪切对象的规则。可选参数为："nonzero"，"evenodd"。 异常值undefined或null按默认值处理。默认值："nonzero" |

## createConicGradient

```TypeScript
createConicGradient(startAngle: double, x: double, y: double): CanvasGradient
```

创建一个圆锥渐变色。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-createConicGradient(startAngle: double, x: double, y: double): CanvasGradient--><!--Device-CanvasRenderer-createConicGradient(startAngle: double, x: double, y: double): CanvasGradient-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| startAngle | double | 是 | 开始渐变的角度。角度测量从中心右侧水平开始，顺时针移动。 异常值undefined和null按0处理，NaN和Infinity按无效值处理。单位：弧度 |
| x | double | 是 | 圆锥渐变的中心x轴坐标。异常值undefined和null按0处理， NaN和Infinity按无效值处理。默认单位：vp |
| y | double | 是 | 圆锥渐变的中心y轴坐标。异常值undefined和null按0处理， NaN和Infinity按无效值处理。默认单位：vp |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CanvasGradient](arkts-na-canvas-canvasgradient-c.md) | 新的CanvasGradient对象，用于在canvas上创建渐变效果。 |

## createImageData

```TypeScript
createImageData(sw: double, sh: double): ImageData
```

创建新的、空白的、指定大小的ImageData对象。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-createImageData(sw: double, sh: double): ImageData--><!--Device-CanvasRenderer-createImageData(sw: double, sh: double): ImageData-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sw | double | 是 | ImageData的宽度。异常值undefined、null、NaN和Infinity按0处理。默认单位：vp |
| sh | double | 是 | ImageData的高度。异常值undefined、null、NaN和Infinity按0处理。默认单位：vp |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ImageData](arkts-na-canvas-imagedata-c.md) | 新的ImageData对象。 |

## createImageData

```TypeScript
createImageData(imageData: ImageData): ImageData
```

根据一个现有的ImageData对象重新创建一个宽、高相同的ImageData对象（不会复制图像数据）。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-createImageData(imageData: ImageData): ImageData--><!--Device-CanvasRenderer-createImageData(imageData: ImageData): ImageData-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| imageData | [ImageData](arkts-na-canvas-imagedata-c.md) | 是 | 现有的ImageData对象。异常值undefined和null按width和height为0的ImageData处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ImageData](arkts-na-canvas-imagedata-c.md) | 新的ImageData对象。 |

## createLinearGradient

```TypeScript
createLinearGradient(x0: double, y0: double, x1: double, y1: double): CanvasGradient
```

创建一个线性渐变色。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-createLinearGradient(x0: double, y0: double, x1: double, y1: double): CanvasGradient--><!--Device-CanvasRenderer-createLinearGradient(x0: double, y0: double, x1: double, y1: double): CanvasGradient-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x0 | double | 是 | 起点的x轴坐标。异常值undefined和null会导致此接口返回undefined， NaN和Infinity按无效值处理。默认单位：vp |
| y0 | double | 是 | 起点的y轴坐标。异常值undefined和null会导致此接口返回undefined， NaN和Infinity按无效值处理。默认单位：vp |
| x1 | double | 是 | 终点的x轴坐标。异常值undefined和null会导致此接口返回undefined， NaN和Infinity按无效值处理。默认单位：vp |
| y1 | double | 是 | 终点的y轴坐标。异常值undefined和null会导致此接口返回undefined， NaN和Infinity按无效值处理。默认单位：vp |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CanvasGradient](arkts-na-canvas-canvasgradient-c.md) | 新的CanvasGradient对象，用于在canvas上创建渐变效果。 |

## createPattern

```TypeScript
createPattern(image: ImageBitmap, repetition: string | null): CanvasPattern | null
```

通过指定图像和重复方式创建图片填充的模板。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-createPattern(image: ImageBitmap, repetition: string | null): CanvasPattern | null--><!--Device-CanvasRenderer-createPattern(image: ImageBitmap, repetition: string | null): CanvasPattern | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| image | [ImageBitmap](arkts-na-canvas-imagebitmap-c.md) | 是 | 图源对象。异常值undefined或null按无效值处理。 |
| repetition | string \| null | 是 | 设置图像重复的方式： 'repeat'：沿x轴和y轴重复绘制图像； 'repeat-x'：沿x轴重复绘制图像； 'repeat-y'：沿y轴重复绘制图像； 'no-repeat'：不重复绘制图像； 'clamp'：在原始边界外绘制时，超出部分使用边缘的颜色绘制； 'mirror'：沿x轴和y轴重复翻转绘制图像。 异常值undefined或null按无效值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CanvasPattern](arkts-na-canvas-canvaspattern-i.md) | 通过指定图像和重复方式创建图片填充的模板对象。 |

## createRadialGradient

```TypeScript
createRadialGradient(x0: double, y0: double, r0: double, x1: double, y1: double, r1: double): CanvasGradient
```

创建一个径向渐变色。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-createRadialGradient(x0: double, y0: double, r0: double, x1: double, y1: double, r1: double): CanvasGradient--><!--Device-CanvasRenderer-createRadialGradient(x0: double, y0: double, r0: double, x1: double, y1: double, r1: double): CanvasGradient-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x0 | double | 是 | 起始圆的x轴坐标。异常值undefined和null会导致此接口返回undefined， NaN和Infinity按无效值处理。默认单位：vp |
| y0 | double | 是 | 起始圆的y轴坐标。异常值undefined和null会导致此接口返回undefined， NaN和Infinity按无效值处理。默认单位：vp |
| r0 | double | 是 | 起始圆的半径。必须是非负且有限的。 异常值undefined和null会导致此接口返回undefined，NaN和Infinity按无效值处理。默认单位：vp |
| x1 | double | 是 | 终点圆的x轴坐标。异常值undefined和null会导致此接口返回undefined， NaN和Infinity按无效值处理。默认单位：vp |
| y1 | double | 是 | 终点圆的y轴坐标。异常值undefined和null会导致此接口返回undefined， NaN和Infinity按无效值处理。默认单位：vp |
| r1 | double | 是 | 终点圆的半径。必须为非负且有限的。 异常值undefined和null会导致此接口返回undefined，NaN和Infinity按无效值处理。默认单位：vp |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CanvasGradient](arkts-na-canvas-canvasgradient-c.md) | 新的CanvasGradient对象，用于在canvas上创建渐变效果。 |

## drawImage

```TypeScript
drawImage(image: ImageBitmap | PixelMap, dx: double, dy: double): void
```

进行图像绘制。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-drawImage(image: ImageBitmap | PixelMap, dx: double, dy: double): void--><!--Device-CanvasRenderer-drawImage(image: ImageBitmap | PixelMap, dx: double, dy: double): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| image | [ImageBitmap](arkts-na-canvas-imagebitmap-c.md) \| [PixelMap](../../apis-arkui/arkts-components/arkts-arkui-pixelmap-t.md) | 是 | 图片资源。异常值undefined或null按无效值处理，不进行绘制。 |
| dx | double | 是 | 绘制区域左上角在x轴的位置。异常值undefined或null按0处理，NaN和Infinity按无效值处理， 不进行绘制。默认单位：vp |
| dy | double | 是 | 绘制区域左上角在y轴的位置。异常值undefined或null按0处理，NaN和Infinity按无效值处理， 不进行绘制。默认单位：vp |

## drawImage

```TypeScript
drawImage(image: ImageBitmap | PixelMap, dx: double, dy: double, dw: double, dh: double): void
```

将图像拉伸或压缩绘制。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-drawImage(image: ImageBitmap | PixelMap, dx: double, dy: double, dw: double, dh: double): void--><!--Device-CanvasRenderer-drawImage(image: ImageBitmap | PixelMap, dx: double, dy: double, dw: double, dh: double): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| image | [ImageBitmap](arkts-na-canvas-imagebitmap-c.md) \| [PixelMap](../../apis-arkui/arkts-components/arkts-arkui-pixelmap-t.md) | 是 | 图片资源。异常值undefined或null按无效值处理，不进行绘制。 |
| dx | double | 是 | 绘制区域左上角在x轴的位置。异常值undefined或null按0处理，NaN和Infinity按无效值处理， 不进行绘制。默认单位：vp |
| dy | double | 是 | 绘制区域左上角在y轴的位置。异常值undefined或null按0处理，NaN和Infinity按无效值处理， 不进行绘制。默认单位：vp |
| dw | double | 是 | 绘制区域的宽度。当绘制区域的宽度和裁剪图像的宽度不一致时， 将图像宽度拉伸或压缩为绘制区域的宽度。负数、异常值undefined或null按0处理， NaN和Infinity按无效值处理，不进行绘制。默认单位：vp |
| dh | double | 是 | 绘制区域的高度。当绘制区域的高度和裁剪图像的高度不一致时， 将图像高度拉伸或压缩为绘制区域的高度。负数、异常值undefined或null按0处理， NaN和Infinity按无效值处理，不进行绘制。默认单位：vp |

## drawImage

```TypeScript
drawImage(image: ImageBitmap | PixelMap, sx: double, sy: double, sw: double, sh: double, dx: double, dy: double,
    dw: double, dh: double): void
```

将图像裁剪后拉伸或压缩绘制。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-drawImage(image: ImageBitmap | PixelMap, sx: double, sy: double, sw: double, sh: double, dx: double, dy: double,    dw: double, dh: double): void--><!--Device-CanvasRenderer-drawImage(image: ImageBitmap | PixelMap, sx: double, sy: double, sw: double, sh: double, dx: double, dy: double,    dw: double, dh: double): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| image | [ImageBitmap](arkts-na-canvas-imagebitmap-c.md) \| [PixelMap](../../apis-arkui/arkts-components/arkts-arkui-pixelmap-t.md) | 是 | 图片资源。异常值undefined或null按无效值处理，不进行绘制。 |
| sx | double | 是 | 裁切源图像时距离源图像左上角的x坐标值。异常值undefined或null按0处理， NaN和Infinity按无效值处理，不进行绘制。默认单位：vp |
| sy | double | 是 | 裁切源图像时距离源图像左上角的y坐标值。异常值undefined或null按0处理， NaN和Infinity按无效值处理，不进行绘制。默认单位：vp |
| sw | double | 是 | 裁切源图像时需要裁切的宽度。负数、异常值undefined或null按0处理， NaN和Infinity按无效值处理，不进行绘制。默认单位：vp |
| sh | double | 是 | 裁切源图像时需要裁切的高度。负数、异常值undefined或null按0处理， NaN和Infinity按无效值处理，不进行绘制。默认单位：vp |
| dx | double | 是 | 绘制区域左上角在x轴的位置。异常值undefined或null按0处理， NaN和Infinity按无效值处理，不进行绘制。默认单位：vp |
| dy | double | 是 | 绘制区域左上角在y轴的位置。异常值undefined或null按0处理， NaN和Infinity按无效值处理，不进行绘制。默认单位：vp |
| dw | double | 是 | 绘制区域的宽度。负数、异常值undefined或null按0处理， NaN和Infinity按无效值处理，不进行绘制。当绘制区域的宽度和裁剪图像的宽度不一致时， 将图像宽度拉伸或压缩为绘制区域的宽度。默认单位：vp |
| dh | double | 是 | 绘制区域的高度。负数、异常值undefined或null按0处理， NaN和Infinity按无效值处理，不进行绘制。当绘制区域的高度和裁剪图像的高度不一致时， 将图像高度拉伸或压缩为绘制区域的高度。默认单位：vp |

## fill

```TypeScript
fill(fillRule?: CanvasFillRule): void
```

对当前路径进行填充。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-fill(fillRule?: CanvasFillRule): void--><!--Device-CanvasRenderer-fill(fillRule?: CanvasFillRule): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fillRule | [CanvasFillRule](arkts-na-canvasfillrule-t.md) | 否 | 指定要填充对象的规则。可选参数为："nonzero"，"evenodd"。 异常值undefined或null按默认值处理。默认值："nonzero" |

## fill

```TypeScript
fill(path: Path2D, fillRule?: CanvasFillRule): void
```

对指定路径进行填充。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-fill(path: Path2D, fillRule?: CanvasFillRule): void--><!--Device-CanvasRenderer-fill(path: Path2D, fillRule?: CanvasFillRule): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | [Path2D](arkts-na-canvas-path2d-c.md) | 是 | Path2D填充路径。异常值undefined或null按无效值处理。 |
| fillRule | [CanvasFillRule](arkts-na-canvasfillrule-t.md) | 否 | 指定要填充对象的规则。可选参数为："nonzero"，"evenodd"。 异常值undefined或null按默认值处理。默认值："nonzero" |

## fillRect

```TypeScript
fillRect(x: double, y: double, w: double, h: double): void
```

填充一个矩形。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-fillRect(x: double, y: double, w: double, h: double): void--><!--Device-CanvasRenderer-fillRect(x: double, y: double, w: double, h: double): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | double | 是 | 指定矩形左上角点的x坐标。异常值undefined、null、NaN或Infinity按无效值处理， 不进行绘制。默认单位：vp |
| y | double | 是 | 指定矩形左上角点的y坐标。异常值undefined、null、NaN或Infinity按无效值处理， 不进行绘制。默认单位：vp |
| w | double | 是 | 指定矩形的宽度。异常值undefined、null、NaN或Infinity按无效值处理， 不进行绘制。默认单位：vp |
| h | double | 是 | 指定矩形的高度。异常值undefined、null、NaN或Infinity按无效值处理， 不进行绘制。默认单位：vp |

## fillText

```TypeScript
fillText(text: string, x: double, y: double, maxWidth?: double): void
```

绘制填充类文本。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-fillText(text: string, x: double, y: double, maxWidth?: double): void--><!--Device-CanvasRenderer-fillText(text: string, x: double, y: double, maxWidth?: double): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 需要绘制的文本内容。异常值undefined或null按无效值处理，不进行绘制。 |
| x | double | 是 | 文本绘制起点的x轴坐标。异常值undefined、null、NaN或Infinity按无效值处理， 不进行绘制。默认单位：vp |
| y | double | 是 | 文本绘制起点的y轴坐标。异常值undefined、null、NaN或Infinity按无效值处理， 不进行绘制。默认单位：vp |
| maxWidth | double | 否 | 指定文本允许的最大宽度。异常值null按无效值处理，不进行绘制， undefined、NaN或Infinity按默认值处理。默认值：不限制宽度。默认单位：vp |

## getImageData

```TypeScript
getImageData(sx: double, sy: double, sw: double, sh: double): ImageData
```

以当前canvas指定区域内的像素创建ImageData对象。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-getImageData(sx: double, sy: double, sw: double, sh: double): ImageData--><!--Device-CanvasRenderer-getImageData(sx: double, sy: double, sw: double, sh: double): ImageData-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sx | double | 是 | 需要输出的区域的左上角x坐标。异常值undefined、null、NaN和Infinity按0处理。 默认单位：vp |
| sy | double | 是 | 需要输出的区域的左上角y坐标。异常值undefined、null、NaN和Infinity按0处理。 默认单位：vp |
| sw | double | 是 | 需要输出的区域的宽度。异常值undefined、null、NaN和Infinity按0处理。默认单位：vp |
| sh | double | 是 | 需要输出的区域的高度。异常值undefined、null、NaN和Infinity按0处理。默认单位：vp |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ImageData](arkts-na-canvas-imagedata-c.md) | 新的ImageData对象。 |

## getLineDash

```TypeScript
getLineDash(): double[]
```

获得当前画布的虚线样式。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-getLineDash(): double[]--><!--Device-CanvasRenderer-getLineDash(): double[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double[] | 返回数组，该数组用来描述线段如何交替和间距长度。默认单位：vp |

## getPixelMap

```TypeScript
getPixelMap(sx: double, sy: double, sw: double, sh: double): PixelMap | undefined
```

以当前canvas指定区域内的像素创建PixelMap对象。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-getPixelMap(sx: double, sy: double, sw: double, sh: double): PixelMap | undefined--><!--Device-CanvasRenderer-getPixelMap(sx: double, sy: double, sw: double, sh: double): PixelMap | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sx | double | 是 | 需要输出的区域的左上角x坐标。异常值undefined、null、NaN和Infinity按0处理。 默认单位：vp |
| sy | double | 是 | 需要输出的区域的左上角y坐标。异常值undefined、null、NaN和Infinity按0处理。 默认单位：vp |
| sw | double | 是 | 需要输出的区域的宽度。异常值undefined、null、NaN和Infinity按0处理。默认单位：vp |
| sh | double | 是 | 需要输出的区域的高度。异常值undefined、null、NaN和Infinity按0处理。默认单位：vp |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PixelMap](../../apis-arkui/arkts-components/arkts-arkui-pixelmap-t.md) | 新的PixelMap对象。 |

## getTransform

```TypeScript
getTransform(): Matrix2D
```

获取当前被应用到上下文的转换矩阵。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-getTransform(): Matrix2D--><!--Device-CanvasRenderer-getTransform(): Matrix2D-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Matrix2D](../../apis-arkui/arkts-apis/arkts-arkui-matrix2d-c.md) | 当前被应用到上下文的转换矩阵。 |

## measureText

```TypeScript
measureText(text: string): TextMetrics
```

该方法返回一个文本测算的对象，通过该对象可以获取指定文本的宽度值。不同设备上获取的宽度值可能不同。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-measureText(text: string): TextMetrics--><!--Device-CanvasRenderer-measureText(text: string): TextMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 需要进行测量的文本。传入异常值undefined或null时按"undefined"或"null"计算。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TextMetrics](arkts-na-canvas-textmetrics-i.md) | 文本的尺寸信息。 |

## putImageData

```TypeScript
putImageData(imageData: ImageData, dx: double | string, dy: double | string): void
```

使用ImageData数据填充新的矩形区域。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-putImageData(imageData: ImageData, dx: double | string, dy: double | string): void--><!--Device-CanvasRenderer-putImageData(imageData: ImageData, dx: double | string, dy: double | string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| imageData | [ImageData](arkts-na-canvas-imagedata-c.md) | 是 | 包含像素值的ImageData对象。 异常值undefined或null按无效值处理，不进行绘制。 |
| dx | double \| string | 是 | 填充区域在x轴方向的偏移量。 异常值undefined、null、NaN和Infinity按0处理。默认单位：vp |
| dy | double \| string | 是 | 填充区域在y轴方向的偏移量。 异常值undefined、null、NaN和Infinity按0处理。默认单位：vp |

## putImageData

```TypeScript
putImageData(imageData: ImageData, dx: double | string, dy: double | string, dirtyX: double | string,
    dirtyY: double | string, dirtyWidth: double | string, dirtyHeight: double | string): void
```

使用ImageData数据裁剪后填充至新的矩形区域。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-putImageData(imageData: ImageData, dx: double | string, dy: double | string, dirtyX: double | string,    dirtyY: double | string, dirtyWidth: double | string, dirtyHeight: double | string): void--><!--Device-CanvasRenderer-putImageData(imageData: ImageData, dx: double | string, dy: double | string, dirtyX: double | string,    dirtyY: double | string, dirtyWidth: double | string, dirtyHeight: double | string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| imageData | [ImageData](arkts-na-canvas-imagedata-c.md) | 是 | 包含像素值的ImageData对象。 异常值undefined或null按无效值处理，不进行绘制。 |
| dx | double \| string | 是 | 填充区域在x轴方向的偏移量。 异常值undefined、null、NaN和Infinity按0处理。默认单位：vp |
| dy | double \| string | 是 | 填充区域在y轴方向的偏移量。 异常值undefined、null、NaN和Infinity按0处理。默认单位：vp |
| dirtyX | double \| string | 是 | 源图像数据矩形裁切范围左上角距离源图像左上角的x轴偏移量。 异常值undefined、null、NaN和Infinity按0处理。默认单位：vp |
| dirtyY | double \| string | 是 | 源图像数据矩形裁切范围左上角距离源图像左上角的y轴偏移量。 异常值undefined、null、NaN和Infinity按0处理。默认单位：vp |
| dirtyWidth | double \| string | 是 | 源图像数据矩形裁切范围的宽度。 异常值undefined、null、NaN和Infinity按0处理。默认单位：vp |
| dirtyHeight | double \| string | 是 | 源图像数据矩形裁切范围的高度。 异常值undefined、null、NaN和Infinity按0处理。默认单位：vp |

## reset

```TypeScript
reset(): void
```

将CanvasRenderingContext2D重置为其默认状态，清除后台缓冲区、绘制状态栈、绘制路径和样式。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-reset(): void--><!--Device-CanvasRenderer-reset(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## resetTransform

```TypeScript
resetTransform(): void
```

使用单位矩阵重新设置当前矩阵。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-resetTransform(): void--><!--Device-CanvasRenderer-resetTransform(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## restore

```TypeScript
restore(): void
```

恢复保存的绘图上下文。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-restore(): void--><!--Device-CanvasRenderer-restore(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## restoreLayer

```TypeScript
restoreLayer(): void
```

恢复图像变换和裁剪状态至saveLayer前的状态，并将图层绘制在canvas上。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-restoreLayer(): void--><!--Device-CanvasRenderer-restoreLayer(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## rotate

```TypeScript
rotate(angle: double): void
```

针对当前坐标轴进行顺时针旋转。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-rotate(angle: double): void--><!--Device-CanvasRenderer-rotate(angle: double): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| angle | double | 是 | 设置顺时针旋转的弧度值，可以通过 degree Math.PI / 180 将角度转换为弧度值。 单位：弧度 |

## save

```TypeScript
save(): void
```

将当前状态放入栈中，保存canvas的全部状态，通常在需要保存绘制状态时调用。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-save(): void--><!--Device-CanvasRenderer-save(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## saveLayer

```TypeScript
saveLayer(): void
```

创建一个图层。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-saveLayer(): void--><!--Device-CanvasRenderer-saveLayer(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scale

```TypeScript
scale(x: double, y: double): void
```

设置canvas画布的缩放变换属性，后续的绘制操作将按照缩放比例进行缩放。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-scale(x: double, y: double): void--><!--Device-CanvasRenderer-scale(x: double, y: double): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | double | 是 | 设置水平方向的缩放值。 |
| y | double | 是 | 设置垂直方向的缩放值。 |

## setLineDash

```TypeScript
setLineDash(segments: double[]): void
```

设置画布的虚线样式。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-setLineDash(segments: double[]): void--><!--Device-CanvasRenderer-setLineDash(segments: double[]): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| segments | double[] | 是 | 描述线段如何交替和线段间距长度的数组。 异常值undefined或null按无效值处理。默认单位：vp |

## setPixelMap

```TypeScript
setPixelMap(value?: PixelMap): void
```

将当前传入PixelMap对象绘制在画布上。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-setPixelMap(value?: PixelMap): void--><!--Device-CanvasRenderer-setPixelMap(value?: PixelMap): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [PixelMap](../../apis-arkui/arkts-components/arkts-arkui-pixelmap-t.md) | 否 | 包含像素值的PixelMap对象。 异常值undefined和null按无效值处理，不进行绘制。默认值：null |

## setTransform

```TypeScript
setTransform(a: double, b: double, c: double, d: double, e: double, f: double): void
```

setTransform方法使用的参数和transform()方法相同，但setTransform()方法会重置现有的变换矩阵 并创建新的变换矩阵。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-setTransform(a: double, b: double, c: double, d: double, e: double, f: double): void--><!--Device-CanvasRenderer-setTransform(a: double, b: double, c: double, d: double, e: double, f: double): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| a | double | 是 | scaleX：指定水平缩放值，支持设置负数。 |
| b | double | 是 | skewY：指定垂直倾斜值，支持设置负数。 |
| c | double | 是 | skewX：指定水平倾斜值，支持设置负数。 |
| d | double | 是 | scaleY：指定垂直缩放值，支持设置负数。 |
| e | double | 是 | translateX：指定水平移动值，支持设置负数。默认单位：vp |
| f | double | 是 | translateY：指定垂直移动值，支持设置负数。默认单位：vp |

## setTransform

```TypeScript
setTransform(transform?: Matrix2D): void
```

以Matrix2D对象为模板重置现有的变换矩阵并创建新的变换矩阵。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-setTransform(transform?: Matrix2D): void--><!--Device-CanvasRenderer-setTransform(transform?: Matrix2D): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| transform | [Matrix2D](../../apis-arkui/arkts-apis/arkts-arkui-matrix2d-c.md) | 否 | 变换矩阵。异常值undefined或null按无效值处理。默认值：null |

## stroke

```TypeScript
stroke(path?: Path2D): void
```

根据指定的路径，进行边框绘制操作。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-stroke(path?: Path2D): void--><!--Device-CanvasRenderer-stroke(path?: Path2D): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | [Path2D](arkts-na-canvas-path2d-c.md) | 否 | 需要绘制的Path2D。异常值undefined或null按无效值处理，不进行绘制。 |

## strokeRect

```TypeScript
strokeRect(x: double, y: double, w: double, h: double): void
```

绘制具有边框的矩形，矩形内部不填充。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-strokeRect(x: double, y: double, w: double, h: double): void--><!--Device-CanvasRenderer-strokeRect(x: double, y: double, w: double, h: double): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | double | 是 | 指定矩形的左上角x坐标。异常值undefined、null、NaN或Infinity按无效值处理， 不进行绘制。默认单位：vp |
| y | double | 是 | 指定矩形的左上角y坐标。异常值undefined、null、NaN或Infinity按无效值处理， 不进行绘制。默认单位：vp |
| w | double | 是 | 指定矩形的宽度。异常值undefined、null、NaN或Infinity按无效值处理， 不进行绘制。默认单位：vp |
| h | double | 是 | 指定矩形的高度。异常值undefined、null、NaN或Infinity按无效值处理， 不进行绘制。默认单位：vp |

## strokeText

```TypeScript
strokeText(text: string, x: double, y: double, maxWidth?: double): void
```

绘制描边类文本。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-strokeText(text: string, x: double, y: double, maxWidth?: double): void--><!--Device-CanvasRenderer-strokeText(text: string, x: double, y: double, maxWidth?: double): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 需要绘制的文本内容。异常值undefined或null按无效值处理，不进行绘制。 |
| x | double | 是 | 文本绘制起点的x轴坐标。异常值undefined、null、NaN或Infinity按无效值处理， 不进行绘制。默认单位：vp |
| y | double | 是 | 文本绘制起点的y轴坐标。异常值undefined、null、NaN或Infinity按无效值处理， 不进行绘制。默认单位：vp |
| maxWidth | double | 否 | 需要绘制的文本的最大宽度。异常值null按无效值处理，不进行绘制， undefined、NaN或Infinity按默认值处理。默认单位：vp。默认值：不限制宽度。 |

## transferFromImageBitmap

```TypeScript
transferFromImageBitmap(bitmap: ImageBitmap): void
```

显示给定的ImageBitmap对象。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-transferFromImageBitmap(bitmap: ImageBitmap): void--><!--Device-CanvasRenderer-transferFromImageBitmap(bitmap: ImageBitmap): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bitmap | [ImageBitmap](arkts-na-canvas-imagebitmap-c.md) | 是 | 待显示的ImageBitmap对象。 |

## transform

```TypeScript
transform(a: double, b: double, c: double, d: double, e: double, f: double): void
```

transform方法对应一个变换矩阵，想对一个图形进行变化的时候，只要设置此变换矩阵相应的参数， 对图形的各个定点的坐标分别乘以这个矩阵，就能得到新的定点的坐标。矩阵变换效果可叠加。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-transform(a: double, b: double, c: double, d: double, e: double, f: double): void--><!--Device-CanvasRenderer-transform(a: double, b: double, c: double, d: double, e: double, f: double): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| a | double | 是 | 变换矩阵中第一行第一列的单元格。scaleX：指定水平缩放值，支持设置负数。 |
| b | double | 是 | 变换矩阵第二行第一列的单元格。skewY：指定垂直倾斜值，支持设置负数。 |
| c | double | 是 | 变换矩阵第一行第二列的单元格。skewX：指定水平倾斜值，支持设置负数。 |
| d | double | 是 | 变换矩阵第二行第二列的单元格。scaleY：指定垂直缩放值，支持设置负数。 |
| e | double | 是 | 变换矩阵第一行第三列的单元格。translateX：指定水平移动值， 支持设置负数。默认单位：vp |
| f | double | 是 | 变换矩阵第二行第三列的单元格。translateY：指定垂直移动值， 支持设置负数。默认单位：vp |

## translate

```TypeScript
translate(x: double, y: double): void
```

移动当前坐标系的原点。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderer-translate(x: double, y: double): void--><!--Device-CanvasRenderer-translate(x: double, y: double): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | double | 是 | 设置水平平移量。默认单位：vp |
| y | double | 是 | 设置竖直平移量。默认单位：vp |

