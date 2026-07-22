# ImageFilter

图像滤波器。
> **说明：**  
>  
> - 本Class首批接口从API version 12开始支持。  
>  
> - 本模块使用屏幕物理像素单位px。  
>  
> - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**起始版本：** 12

<!--Device-drawing-class ImageFilter--><!--Device-drawing-class ImageFilter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## createBlendImageFilter

```TypeScript
static createBlendImageFilter(mode: BlendMode, background: ImageFilter, foreground: ImageFilter): ImageFilter
```

按照指定的混合模式对两个滤波器进行叠加，生成一个新的滤波器。

**起始版本：** 20

<!--Device-ImageFilter-static createBlendImageFilter(mode: BlendMode, background: ImageFilter, foreground: ImageFilter): ImageFilter--><!--Device-ImageFilter-static createBlendImageFilter(mode: BlendMode, background: ImageFilter, foreground: ImageFilter): ImageFilter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [BlendMode](../../apis-arkui/arkts-components/arkts-arkui-blendmode-e.md) | 是 | 颜色混合模式。 |
| background | [ImageFilter](arkts-arkgraphics2d-drawing-imagefilter-c.md) | 是 | 在混合模式中作为目标色的滤波器。 |
| foreground | [ImageFilter](arkts-arkgraphics2d-drawing-imagefilter-c.md) | 是 | 在混合模式中作为源色的滤波器。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ImageFilter](arkts-arkgraphics2d-drawing-imagefilter-c.md) | 返回创建的图像滤波器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [25900001](../errorcode-drawing.md#25900001-参数值异常) | Parameter error. Possible causes: Incorrect parameter range. |

## createBlurImageFilter

```TypeScript
static createBlurImageFilter(sigmaX: number, sigmaY: number,
        tileMode: TileMode, imageFilter?: ImageFilter | null): ImageFilter
```

创建具有模糊效果的图像滤波器。

**起始版本：** 12

<!--Device-ImageFilter-static createBlurImageFilter(sigmaX: number, sigmaY: number,        tileMode: TileMode, imageFilter?: ImageFilter | null): ImageFilter--><!--Device-ImageFilter-static createBlurImageFilter(sigmaX: number, sigmaY: number,        tileMode: TileMode, imageFilter?: ImageFilter | null): ImageFilter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sigmaX | number | 是 | 表示沿x轴方向上高斯模糊的标准差，必须大于0，该参数为浮点数。 |
| sigmaY | number | 是 | 表示沿y轴方向上高斯模糊的标准差，必须大于0，该参数为浮点数。 |
| tileMode | [TileMode](arkts-arkgraphics2d-effectkit-tilemode-e.md) | 是 | 表示在边缘处应用的平铺模式。 |
| imageFilter | [ImageFilter](arkts-arkgraphics2d-drawing-imagefilter-c.md) \| null | 否 | 要与当前图像滤波器叠加的输入滤波器，默认为null，表示直接将当前图像滤波器作用于原始图像。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ImageFilter](arkts-arkgraphics2d-drawing-imagefilter-c.md) | 返回创建的图像滤波器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

## createComposeImageFilter

```TypeScript
static createComposeImageFilter(cOuter: ImageFilter, cInner: ImageFilter): ImageFilter
```

将两个图像滤波器进行级联生成新的图像滤波器，级联时会将第一级滤波器的输出作为第二级滤波器的输入，经过第二级滤波器处理后，输出最终的滤波结果。

**起始版本：** 20

<!--Device-ImageFilter-static createComposeImageFilter(cOuter: ImageFilter, cInner: ImageFilter): ImageFilter--><!--Device-ImageFilter-static createComposeImageFilter(cOuter: ImageFilter, cInner: ImageFilter): ImageFilter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cOuter | [ImageFilter](arkts-arkgraphics2d-drawing-imagefilter-c.md) | 是 | 在级联中，作为第二级的滤波器，处理第一级滤波器的输出。如果第二级滤波器为空，第一级滤波器不为空，最后输出第一级滤波器的结果。两级滤波器不能同时为空。 |
| cInner | [ImageFilter](arkts-arkgraphics2d-drawing-imagefilter-c.md) | 是 | 在级联中，作为第一级的滤波器，直接处理图像的原始内容。如果第一级滤波器为空，第二级滤波器不为空，最后输出第二级滤波器的结果。两级滤波器不能同时为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ImageFilter](arkts-arkgraphics2d-drawing-imagefilter-c.md) | 返回创建的图像滤波器。 |

## createFromColorFilter

```TypeScript
static createFromColorFilter(colorFilter: ColorFilter, imageFilter?: ImageFilter | null): ImageFilter
```

创建一个将颜色滤波器应用于传入的图像滤波器的图像滤波器。

**起始版本：** 12

<!--Device-ImageFilter-static createFromColorFilter(colorFilter: ColorFilter, imageFilter?: ImageFilter | null): ImageFilter--><!--Device-ImageFilter-static createFromColorFilter(colorFilter: ColorFilter, imageFilter?: ImageFilter | null): ImageFilter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| colorFilter | [ColorFilter](../../apis-arkui/arkts-apis/arkts-arkui-colorfilter-c.md) | 是 | 表示颜色滤波器。 |
| imageFilter | [ImageFilter](arkts-arkgraphics2d-drawing-imagefilter-c.md) \| null | 否 | 要与当前图像滤波器叠加的输入滤波器，默认为null，表示直接将当前图像滤波器作用于原始图像。<br>**起始版本：** 20 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ImageFilter](arkts-arkgraphics2d-drawing-imagefilter-c.md) | 返回创建的图像滤波器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## createFromImage

```TypeScript
static createFromImage(pixelmap: image.PixelMap, srcRect?: common2D.Rect | null, dstRect?: common2D.Rect | null): ImageFilter
```

基于给定的图像创建一个图像滤波器。此接口不建议用于录制类型的画布，会影响性能。

**起始版本：** 20

<!--Device-ImageFilter-static createFromImage(pixelmap: image.PixelMap, srcRect?: common2D.Rect | null, dstRect?: common2D.Rect | null): ImageFilter--><!--Device-ImageFilter-static createFromImage(pixelmap: image.PixelMap, srcRect?: common2D.Rect | null, dstRect?: common2D.Rect | null): ImageFilter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pixelmap | image.PixelMap | 是 | 图片对象。 |
| srcRect | common2D.Rect \| null | 否 | 可选参数，默认为空。图片要被此滤波器使用的像素区域，如果为空，则使用pixelmap全部区域。 |
| dstRect | common2D.Rect \| null | 否 | 可选参数，默认为空。要进行渲染的区域，如果为空，则和srcRect保持一致。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ImageFilter](arkts-arkgraphics2d-drawing-imagefilter-c.md) | 返回创建的图像滤波器。 |

## createFromShaderEffect

```TypeScript
static createFromShaderEffect(shader: ShaderEffect): ImageFilter
```

基于着色器创建一个图像滤波器。

**起始版本：** 20

<!--Device-ImageFilter-static createFromShaderEffect(shader: ShaderEffect): ImageFilter--><!--Device-ImageFilter-static createFromShaderEffect(shader: ShaderEffect): ImageFilter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| shader | [ShaderEffect](arkts-arkgraphics2d-drawing-shadereffect-c.md) | 是 | 表示应用于图像的着色器效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ImageFilter](arkts-arkgraphics2d-drawing-imagefilter-c.md) | 返回创建的图像滤波器。 |

## createOffsetImageFilter

```TypeScript
static createOffsetImageFilter(dx: number, dy: number, input?: ImageFilter | null): ImageFilter
```

创建一个偏移滤波器，将输入的滤波器按照指定向量进行平移。

**起始版本：** 20

<!--Device-ImageFilter-static createOffsetImageFilter(dx: number, dy: number, input?: ImageFilter | null): ImageFilter--><!--Device-ImageFilter-static createOffsetImageFilter(dx: number, dy: number, input?: ImageFilter | null): ImageFilter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dx | number | 是 | 水平方向的平移距离， 该参数为浮点数。 |
| dy | number | 是 | 竖直方向的平移距离， 该参数为浮点数。 |
| input | [ImageFilter](arkts-arkgraphics2d-drawing-imagefilter-c.md) \| null | 否 | 需进行平移的滤波器。默认为空，如果为空，则将无滤波效果的绘制结果进行平移。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ImageFilter](arkts-arkgraphics2d-drawing-imagefilter-c.md) | 返回创建的图像滤波器。 |

