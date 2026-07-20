# OffscreenCanvasRenderingContext2D

使用OffscreenCanvasRenderingContext2D在Canvas上进行离屏绘制，绘制对象可以是形状、文本、图片等。离屏绘制是指将需要绘制的内容先绘制在缓存区，然后将其转换成图片，一次性绘制到Canvas上。离屏绘制使用CPU进行绘制，绘制速度较慢，对绘制速度有要求的场景应避免使用离屏绘制。

> **说明：**  
>  
> OffscreenCanvasRenderingContext2D无法在ServiceExtensionAbility中使用，  
> ServiceExtensionAbility中建议使用  
> [Drawing模块](docroot://reference/apis-arkgraphics2d/arkts-apis-graphics-drawing.md)  
> 进行离屏绘制。  
>  
> beginPath、moveTo、lineTo、closePath、bezierCurveTo、quadraticCurveTo、arc、arcTo、ellipse、rect和  
> roundRect接口只能对OffscreenCanvasRenderingContext2D中的路径生效，无法对  
> [CanvasRenderingContext2D](docroot://reference/apis-arkui/arkui-ts/ts-canvasrenderingcontext2d.md)  
> 和[Path2D](docroot://reference/apis-arkui/arkui-ts/ts-components-canvas-path2d.md)  
> 对象中设置的路径生效。

**继承/实现关系：** OffscreenCanvasRenderingContext2D extends [CanvasRenderer](arkts-arkui-canvasrenderer-c.md)

**起始版本：** 8

<!--Device-unnamed-declare class OffscreenCanvasRenderingContext2D extends CanvasRenderer--><!--Device-unnamed-declare class OffscreenCanvasRenderingContext2D extends CanvasRenderer-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="constructor"></a>
## constructor

```TypeScript
constructor(width: number, height: number, settings?: RenderingContextSettings)
```

构造离屏Canvas画布对象，支持配置画布宽高和OffscreenCanvasRenderingContext2D对象的参数。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-OffscreenCanvasRenderingContext2D-constructor(width: number, height: number, settings?: RenderingContextSettings)--><!--Device-OffscreenCanvasRenderingContext2D-constructor(width: number, height: number, settings?: RenderingContextSettings)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | number | 是 | 离屏画布的宽度，默认单位：vp。<br>异常值NaN和Infinity按无效值处理。 |
| height | number | 是 | 离屏画布的高度，默认单位：vp。<br>异常值NaN和Infinity按无效值处理。 |
| settings | [RenderingContextSettings](arkts-arkui-renderingcontextsettings-c.md) | 否 | 用来配置OffscreenCanvasRenderingContext2D对象的参数，见RenderingContextSettings接口描述。<br>异常值undefined按RenderingContextSettings的默认值处理。<br>默认值：null。 |

<a id="constructor-1"></a>
## constructor

```TypeScript
constructor(width: number, height: number, settings?: RenderingContextSettings, unit?: LengthMetricsUnit)
```

构造离屏Canvas画布对象，支持配置画布宽高、OffscreenCanvasRenderingContext2D对象的参数和单位模式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-OffscreenCanvasRenderingContext2D-constructor(width: number, height: number, settings?: RenderingContextSettings, unit?: LengthMetricsUnit)--><!--Device-OffscreenCanvasRenderingContext2D-constructor(width: number, height: number, settings?: RenderingContextSettings, unit?: LengthMetricsUnit)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | number | 是 | 离屏画布的宽度，默认单位：vp。<br>异常值NaN和Infinity按无效值处理。 |
| height | number | 是 | 离屏画布的高度，默认单位：vp。<br>异常值NaN和Infinity按无效值处理。 |
| settings | [RenderingContextSettings](arkts-arkui-renderingcontextsettings-c.md) | 否 | 用来配置OffscreenCanvasRenderingContext2D对象的参数，见RenderingContextSettings接口描述。<br>异常值undefined按RenderingContextSettings的默认值处理。<br>默认值：null。 |
| unit | [LengthMetricsUnit](../arkts-apis/arkts-arkui-graphics-lengthmetricsunit-e.md) | 否 | 用来配置OffscreenCanvasRenderingContext2D对象的单位模式，配置后无法动态更改，配置方法同[CanvasRenderingContext2D](docroot://reference/apis-arkui/arkui-ts/ts-canvasrenderingcontext2d.md)。<br>异常值undefined、NaN和Infinity按默认值处理。<br>默认值：DEFAULT。 |

<a id="todataurl"></a>
## toDataURL

```TypeScript
toDataURL(type?: string, quality?: any): string
```

生成一个包含图片展示的URL，该接口存在内存拷贝行为，高耗时，应避免频繁使用。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-OffscreenCanvasRenderingContext2D-toDataURL(type?: string, quality?: any): string--><!--Device-OffscreenCanvasRenderingContext2D-toDataURL(type?: string, quality?: any): string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 否 | 用于指定图像格式。<br>可选参数为："image/png"，"image/jpeg"，"image/webp"。<br>异常值undefined或null按默认值处理。<br>默认值：image/png。 |
| quality | any | 否 | 在指定图片格式为image/jpeg或image/webp的情况下，可以从0到1的区间内选择图片的质量。如果超出取值范围，将会使用默认值0.92。<br>异常值undefined、null、NaN和Infinity按默认值处理。<br>默认值：0.92。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 图像的URL地址。 |

<a id="transfertoimagebitmap"></a>
## transferToImageBitmap

```TypeScript
transferToImageBitmap(): ImageBitmap
```

在离屏画布最近渲染的图像上创建一个ImageBitmap对象。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-OffscreenCanvasRenderingContext2D-transferToImageBitmap(): ImageBitmap--><!--Device-OffscreenCanvasRenderingContext2D-transferToImageBitmap(): ImageBitmap-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ImageBitmap](arkts-arkui-imagebitmap-c.md) | 存储离屏画布上渲染的像素数据。 |

