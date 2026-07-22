# Image属性/事件

Image为图片组件，常用于在应用中显示图片。Image支持加载[PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)、[ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)和[DrawableDescriptor](arkts-arkui-drawabledescriptor-t.md)类型的数据源，支持png、jpg、jpeg、bmp、svg、webp、gif、heif和tiff类型的图片格式，不支持apng和svga格式。
> **说明：**
> - 从API version 23开始，图片类型新增支持tiff格式。  
>  
> - 该组件从API版本26.0.0开始支持[WithTheme](../arkts-apis/arkts-with_theme.md)。  
>  
> - 使用快捷组合键对Image组件复制时，Image组件必须处于获焦状态，如何获焦请参考[设置组件是否可获焦]  
> (../../../ui/arkts-common-events-focus-event.md#设置组件是否可获焦)。Image组件默认不获焦，  
> 需将[focusable](arkts-arkui-commonmethod-c.md#focusable)属性设置为true，即可使用Tab键将焦点切换到组件上，再将  
> [focusOnTouch](arkts-arkui-commonmethod-c.md#focusontouch)属性设置为true，即可实现点击获焦。  
>  
> - 图片格式支持SVG图源，SVG标签文档请参考[SVG标签说明](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)。  
>  
> - 动图的播放依赖于Image节点的可见性变化，其默认行为是不播放的。当节点可见时，  
> 通过回调启动动画，当节点不可见时，停止动画。  
> 可见性状态的判断是通过[onVisibleAreaChange]  
> {@link CommonMethod#onVisibleAreaChange(ratios: Array<number>, event: VisibleAreaChangeCallback)}  
> 事件触发的，当可见阈值ratios大于0时，表明Image处于可见状态。  
>  
> - Image组件播放GIF动图时，帧时长取自GIF文件中各帧的delay time字段。当某帧的时长值小于等于0时，  
> 系统会将其修正为100ms；  
> 当某帧的时长值大于0时，系统直接使用该原始值，不做最小帧时长限制。  
>  
> - 如果图片加载过程中出现白色块，请参考[Image白块问题解决方案]  
> (https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-image-white-lump-solution)。  
> 如果图片加载时间过长，  
> 请参考[预置图片资源加载优化]  
> (https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-texture-compression-improve-  
> performance#section91526132216)。  
>

**继承/实现关系：** ImageAttribute extends [CommonMethod<ImageAttribute>](CommonMethod<ImageAttribute>)

**起始版本：** 7

<!--Device-unnamed-declare class ImageAttribute extends CommonMethod<ImageAttribute>--><!--Device-unnamed-declare class ImageAttribute extends CommonMethod<ImageAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## alt

```TypeScript
alt(value: string | Resource | PixelMap)
```

设置图片加载过程中显示的占位图。

占位图支持使用[objectFit](ImageAttribute#objectFit)设置填充效果，与图片的填充效果一致。

当组件的参数类型为[AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md)时设置该属性不生效。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageAttribute-alt(value: string | Resource | PixelMap): ImageAttribute--><!--Device-ImageAttribute-alt(value: string | Resource | PixelMap): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| Resource \| PixelMap | 是 | 设置图片加载过程中显示的占位图，支持本地图片（png、jpg、bmp、svg、gif和heif类型），支持[PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)类型图片，不支持网络图片。   - 支持`Base64`字符串。   - 支持file://路径前缀的字符串，应用沙箱URI：file://<bundleName>/<sandboxPath>。应用沙箱路径URI构造可参考[constructor](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-fileuri-c.md#constructor)。沙箱路径需要使用[fileUri.getUriFromPath(path)](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-geturifrompath-f.md#geturifrompath)方法将路径转换为应用沙箱URI，然后传入显示。同时需要保证目录包路径下的文件有可读权限。默认值：null由有效值（可正常解析并加载的图片资源）切换为无效值（无法解析或加载的图片路径）时，组件保持显示此前成功加载的图片内容，不进行清除或重置操作。<br>**起始版本：** 12 |

## alt

```TypeScript
alt(src: ResourceStr | PixelMap | ImageAlt)
```

设置图片加载过程中和加载失败时的占位图。
> **说明：**  
>  
> 通过[ImageAlt](arkts-arkui-imagealt-i.md)配置占位图时，Image会根据用户配置的加载过程中和加载失败的占位图源生效，  
> 未配置时默认不显示。

占位图支持使用[objectFit](ImageAttribute#objectFit)设置填充效果，与图片的填充效果一致。

当组件的参数类型为[AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md)时设置该属性不生效。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageAttribute-alt(src: ResourceStr | PixelMap | ImageAlt): ImageAttribute--><!--Device-ImageAttribute-alt(src: ResourceStr | PixelMap | ImageAlt): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) \| PixelMap \| ImageAlt | 是 | 设置图片加载过程中和加载失败时的占位图，支持本地图片（png、jpg、bmp、svg、gif和heif类型），支持[PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)类型图片，不支持网络图片。   - 支持`Base64`字符串。   - 支持file://路径前缀的字符串，应用沙箱URI：file://<bundleName>/<sandboxPath>。应用沙箱路径URI构造可参考[constructor](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-fileuri-c.md#constructor)。沙箱路径需要使用[fileUri.getUriFromPath(path)](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-geturifrompath-f.md#geturifrompath)方法将路径转换为应用沙箱URI，然后传入显示。同时需要保证目录包路径下的文件有可读权限。 |

## antialiased

```TypeScript
antialiased(isAntialiased: Optional<boolean>)
```

设置位图图片边缘是否开启抗锯齿。未通过该接口设置时，默认不开启抗锯齿。SVG类型图片不支持该属性。
> **说明：**  
>  
> 如果图片设置了背景色属性([backgroundColor](arkts-arkui-commonmethod-c.md#backgroundcolor))，  
> 图片的抗锯齿属性  
> 设置为true不会影响背景色的锯齿效果。  
>  
> 和[resizable](ImageAttribute#resizable)一起使用时，该属性不生效。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ImageAttribute-antialiased(isAntialiased: Optional<boolean>): ImageAttribute--><!--Device-ImageAttribute-antialiased(isAntialiased: Optional<boolean>): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isAntialiased | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 设置位图图片边缘是否开启抗锯齿。<br/>true表示开启边缘抗锯齿；false表示不开启边缘抗锯齿。设置为undefined时，不开启边缘抗锯齿。 |

## autoResize

```TypeScript
autoResize(value: boolean)
```

设置图片解码过程中是否对图源自动缩放。降采样解码时图片的部分信息丢失，因此可能会导致图片质量的下降（如：出现锯齿），这时可以选择把autoResize设为false，按原图尺寸解码，提升显示效果，但会增加内存占用。

原图尺寸和显示尺寸不匹配时，图片都会出现些许的失真、模糊。最佳清晰度配置建议：

图片缩小显示时：.autoResize(false) + .interpolation(.Medium)

图片放大显示时：.interpolation(.High)

当组件的参数类型为[AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md)和SVG时设置该属性不生效。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageAttribute-autoResize(value: boolean): ImageAttribute--><!--Device-ImageAttribute-autoResize(value: boolean): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 图片解码过程中是否对图源自动缩放。设置为true时，组件会根据显示区域的尺寸决定用于绘制的图源尺寸，有利于减少内存占用。如原图大小为800x1200，而显示区域大小为200x200，则图片会降采样解码到200x300的尺寸（实际计算过程中会依赖缩放和填充类型的配置，从而得到的计算结果会有差异），从而大幅度节省图片占用的内存。默认值：false，false表示关闭图源自动缩放，true表示开启图源自动缩放。 |

## colorFilter

```TypeScript
colorFilter(value: ColorFilter | DrawingColorFilter)
```

为图像设置颜色滤镜效果。

设置该属性时，[renderMode](ImageAttribute#renderMode)属性设置不生效。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageAttribute-colorFilter(value: ColorFilter | DrawingColorFilter): ImageAttribute--><!--Device-ImageAttribute-colorFilter(value: ColorFilter | DrawingColorFilter): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ColorFilter](../arkts-apis/arkts-arkui-colorfilter-c.md) \| DrawingColorFilter | 是 | 1. 给图像设置颜色滤镜效果，入参为一个的4x5的RGBA转换矩阵。 |

## colorFilter

```TypeScript
colorFilter(value: ColorFilter | DrawingColorFilter | ResourceColor)
```

为图像设置颜色滤镜效果。

设置该属性时，[renderMode](ImageAttribute#renderMode)属性设置不生效。

当值为[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)类型时，它将被转换为带有混合模式的[DrawingColorFilter](arkts-arkui-drawingcolorfilter-t.md)。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageAttribute-colorFilter(value: ColorFilter | DrawingColorFilter | ResourceColor): ImageAttribute--><!--Device-ImageAttribute-colorFilter(value: ColorFilter | DrawingColorFilter | ResourceColor): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ColorFilter](../arkts-apis/arkts-arkui-colorfilter-c.md) \| DrawingColorFilter \| ResourceColor | 是 | 图像颜色的滤镜值。[ColorFilter](../arkts-apis/arkts-arkui-colorfilter-c.md)、[DrawingColorFilter](arkts-arkui-drawingcolorfilter-t.md)类型及SVG图源的相关说明，请参考[colorFilter](ImageAttribute#colorFilter(value: ColorFilter \| DrawingColorFilter))的接口说明。[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)类型的输入颜色值，默认按照[DrawingColorFilter](arkts-arkui-drawingcolorfilter-t.md).[createBlendModeColorFilter](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-drawing-colorfilter-c.md#createblendmodecolorfilter)的SRC_ATOP模式进行绘制。 |

## contentTransition

```TypeScript
contentTransition(transition: ContentTransitionEffect)
```

图片内容发生变化时，触发过渡动效。

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-ImageAttribute-contentTransition(transition: ContentTransitionEffect): ImageAttribute--><!--Device-ImageAttribute-contentTransition(transition: ContentTransitionEffect): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| transition | [ContentTransitionEffect](arkts-arkui-contenttransitioneffect-c.md) | 是 | 过渡动效的类型。其中取值为ContentTransitionEffect.OPACITY表示淡入淡出效果，取值为ContentTransitionEffect.IDENTITY表示无动画效果。默认值：ContentTransitionEffect.IDENTITY设置为undefined或null时，取默认值ContentTransitionEffect.IDENTITY。**说明**：对动态图片资源不生效。 |

## copyOption

```TypeScript
copyOption(value: CopyOptions)
```

设置图片是否可复制。当copyOption设置为非CopyOptions.None时，支持使用长按、鼠标右击、快捷组合键'CTRL+C'等方式进行复制。SVG图片不支持复制。

当组件的参数类型为[AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md)时设置该属性不生效。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageAttribute-copyOption(value: CopyOptions): ImageAttribute--><!--Device-ImageAttribute-copyOption(value: CopyOptions): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [CopyOptions](../arkts-apis/arkts-arkui-copyoptions-e.md) | 是 | 图片是否可复制。<br/>默认值：CopyOptions.None |

## draggable

```TypeScript
draggable(value: boolean)
```

设置组件默认拖拽效果。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ImageAttribute-draggable(value: boolean): ImageAttribute--><!--Device-ImageAttribute-draggable(value: boolean): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 组件默认拖拽效果，设置为true时，组件可拖拽，绑定的长按手势不生效。API version 9及之前，默认值为false。API version 10及之后，默认值为true。若用户需要设置自定义手势，则需要将draggable设置为false。设置为false之后，拖拽类事件不再触发。 |

## dynamicRangeMode

```TypeScript
dynamicRangeMode(value: DynamicRangeMode)
```

设置期望展示的图像动态范围。SVG类型图源不支持该属性。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ImageAttribute-dynamicRangeMode(value: DynamicRangeMode): ImageAttribute--><!--Device-ImageAttribute-dynamicRangeMode(value: DynamicRangeMode): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [DynamicRangeMode](arkts-arkui-dynamicrangemode-e.md) | 是 | 图像显示的动态范围。<br/>默认值：DynamicRangeMode.STANDARD |

## enableAnalyzer

```TypeScript
enableAnalyzer(enable: boolean)
```

设置组件支持AI分析，当前支持主体识别、文字识别和对象查找等功能。<!--RP3--><!--RP3End-->

不能和[overlay](arkts-arkui-commonmethod-c.md#overlay)属性同时使用，两者同时设置时overlay中[CustomBuilder](../../../reference/apis-arkui/arkui-ts/ts-types.md#custombuilder8)属性将失效。该特性依赖设备能力。

分析图像要求是静态非矢量图，即svg、gif等图像类型不支持分析，支持传入[PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)进行分析，目前仅支持[RGBA_8888](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmapformat-e.md)类型，使用方式见[示例5（开启图像AI分析）](../../../reference/apis-arkui/arkui-ts/ts-basic-components-image.md#示例5开启图像ai分析)。

[alt](ImageAttribute#alt(value: string | Resource | PixelMap))占位图不支持分析，[objectRepeat](ImageAttribute#objectRepeat)属性仅在取值为ImageRepeat.NoRepeat时支持分析，隐私遮罩属性[obscured](arkts-arkui-commonmethod-c.md#obscured)打开时不支持分析。

基于完整原始图像进行分析，设置[clip](arkts-arkui-commonmethod-c.md#clip)、[margin](arkts-arkui-commonmethod-c.md#margin)、[borderRadius](arkts-arkui-commonmethod-c.md#borderradius)、[position](arkts-arkui-commonmethod-c.md#position)和[objectFit](ImageAttribute#objectFit)属性导致图像显示不完整，或使用[renderMode](ImageAttribute#renderMode)设置蒙层，仍基于完整原始图像进行分析。 [copyOption](ImageAttribute#copyOption)属性不影响AI分析功能。

当组件的参数类型为[AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md)时设置该属性不生效。
> **说明：**  
>  
> - 需要配置权限：ohos.permission.INTERNET。  
>  
> - 从API version 12开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ImageAttribute-enableAnalyzer(enable: boolean): ImageAttribute--><!--Device-ImageAttribute-enableAnalyzer(enable: boolean): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | Image组件是否支持AI分析。设置为true时，Image组件支持AI分析。设置为false时，Image组件不支持AI分析。默认值：false |

## fillColor

```TypeScript
fillColor(value: ResourceColor)
```

设置填充颜色。仅对SVG图源生效，设置后会替换SVG图片中所有可绘制元素的填充颜色。如需对png图片进行修改颜色，可以使用[colorFilter](ImageAttribute#colorFilter(value: ColorFilter | DrawingColorFilter))。

当组件的参数类型为[AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md)时设置该属性不生效。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageAttribute-fillColor(value: ResourceColor): ImageAttribute--><!--Device-ImageAttribute-fillColor(value: ResourceColor): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 设置填充颜色。**说明：**默认不对组件进行填充。当传入异常值时，系统将使用默认的主题色：浅色模式下为黑色，深色模式下为白色。从API version 21开始，当[supportSvg2](ImageAttribute#supportSvg2)设置为true时，fillColor依赖SVG图源中fill属性的参数配置。当SVG图源中fill属性为'none'时，fillColor不生效。当supportSvg2设置为false时，fillColor生效，替换SVG图片中所有可绘制元素的填充颜色。 |

## fillColor

```TypeScript
fillColor(color: ResourceColor | ColorContent)
```

设置填充颜色。仅对SVG图源生效，设置后会替换SVG图片中所有可绘制元素的填充颜色。如需对png图片进行修改颜色，可以使用[colorFilter](ImageAttribute#colorFilter(value: ColorFilter | DrawingColorFilter))。如果想重置填充颜色可以传入[ColorContent](arkts-arkui-colorcontent-c.md)类型。

当组件的参数类型为[AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md)时设置该属性不生效。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-ImageAttribute-fillColor(color: ResourceColor | ColorContent): ImageAttribute--><!--Device-ImageAttribute-fillColor(color: ResourceColor | ColorContent): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) \| ColorContent | 是 | 设置填充颜色。 <br/>**说明：**<br/>默认不对组件进行填充。当传入异常值时，系统将使用默认的主题色：浅色模式下为黑色，深色模式下为白色。从API version 21开始，当[supportSvg2](ImageAttribute#supportSvg2)设置为true时，fillColor依赖SVG图源中fill属性的参数配置。当SVG图源中fill属性为'none'时，fillColor不生效。 |

## fillColor

```TypeScript
fillColor(color: ResourceColor | ColorContent | ColorMetrics)
```

设置填充颜色。仅对SVG图源生效，设置后会替换SVG图片中所有可绘制元素的填充颜色。如需对png图片进行修改颜色，可以使用[colorFilter](ImageAttribute#colorFilter(value: ColorFilter | DrawingColorFilter))。如果想重置填充颜色可以传入[ColorContent](arkts-arkui-colorcontent-c.md)类型。支持通过传入[ColorMetrics](../arkts-apis/arkts-arkui-graphics-colormetrics-c.md)类型设置P3色域颜色值<!--Del-->，从API version 24开始，支持BT2020色域颜色值<!--DelEnd-->，可在支持高色域的设备上获得更丰富的色彩表现。

当组件的参数类型为[AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md)时设置该属性不生效。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ImageAttribute-fillColor(color: ResourceColor | ColorContent | ColorMetrics): ImageAttribute--><!--Device-ImageAttribute-fillColor(color: ResourceColor | ColorContent | ColorMetrics): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) \| ColorContent \| ColorMetrics | 是 | 设置填充颜色。**说明：**默认不对组件进行填充。当传入异常值时，系统将使用默认的主题色：浅色模式下为黑色，深色模式下为白色。从API version 21开始，当[supportSvg2](ImageAttribute#supportSvg2)设置为true时，fillColor依赖SVG图源中fill属性的参数配置。当SVG图源中fill属性为'none'时，fillColor不生效。 |

## fitOriginalSize

```TypeScript
fitOriginalSize(value: boolean)
```

设置图片的显示尺寸是否跟随图源尺寸。

图片组件已设置width、height属性时，fitOriginalSize属性不生效。

当组件的参数类型为[AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md)时设置该属性不生效。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageAttribute-fitOriginalSize(value: boolean): ImageAttribute--><!--Device-ImageAttribute-fitOriginalSize(value: boolean): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 图片的显示尺寸是否跟随图源尺寸。默认值：false **说明：**当不设置fitOriginalSize或者设置fitOriginalSize为false时，组件显示大小不跟随图源大小。当设置fitOriginalSize为true时，组件显示大小跟随图源大小。 |

## hdrBrightness

```TypeScript
hdrBrightness(brightness: number)
```

设置组件在显示HDR图片时的亮度。

SVG类型图源不支持该属性。

该属性与[dynamicRangeMode](ImageAttribute#dynamicRangeMode)属性同时设置时，[dynamicRangeMode](ImageAttribute#dynamicRangeMode)属性不生效。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-ImageAttribute-hdrBrightness(brightness: number): ImageAttribute--><!--Device-ImageAttribute-hdrBrightness(brightness: number): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| brightness | number | 是 | 用于调整组件展示HDR图片的亮度，该接口仅对HDR图源生效。默认值：1.0取值范围：[0.0，1.0]，小于0和大于1.0时取1.0。0表示图片按照SDR亮度显示，1.0表示图片按照当前允许的最高HDR亮度显示。 |

## imageMatrix

```TypeScript
imageMatrix(matrix: ImageMatrix)
```

设置图片的变换矩阵。通过[ImageMatrix](ImageAttribute#imageMatrix)对象使用平移、旋转、缩放等函数，实现宫格缩略图的最佳呈现。SVG类型图源不支持该属性。

设置[resizable](ImageAttribute#resizable)、[objectRepeat](ImageAttribute#objectRepeat)属性时，该属性设置不生效。该属性只针对图源做处理，不会触发Image组件的回调事件。

该属性与[objectFit](ImageAttribute#objectFit)属性强关联，仅在[objectFit](ImageAttribute#objectFit)属性设置为ImageFit.MATRIX时生效。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-ImageAttribute-imageMatrix(matrix: ImageMatrix): ImageAttribute--><!--Device-ImageAttribute-imageMatrix(matrix: ImageMatrix): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| matrix | [ImageMatrix](arkts-arkui-imagematrix-t.md) | 是 | 图片的变换矩阵。 |

## interpolation

```TypeScript
interpolation(value: ImageInterpolation)
```

定义图片插值效果。用于优化图片缩放时的锯齿问题。SVG类型图源不支持该属性。

当组件的参数类型为[AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md)时设置该属性不生效。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageAttribute-interpolation(value: ImageInterpolation): ImageAttribute--><!--Device-ImageAttribute-interpolation(value: ImageInterpolation): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ImageInterpolation](arkts-arkui-imageinterpolation-e.md) | 是 | 图片的插值效果。默认值：ImageInterpolation.Low设置undefined时，取值为ImageInterpolation.None。 |

## matchTextDirection

```TypeScript
matchTextDirection(value: boolean)
```

设置图片是否跟随系统语言方向，在RTL语言环境下显示镜像翻转显示效果。

当组件的参数类型为[AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md)时设置该属性不生效。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageAttribute-matchTextDirection(value: boolean): ImageAttribute--><!--Device-ImageAttribute-matchTextDirection(value: boolean): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 图片是否跟随系统语言方向。默认值：false，false表示图片不跟随系统语言方向，true表示图片跟随系统语言方向，在RTL语言环境下显示镜像翻转显示效果。 |

## objectFit

```TypeScript
objectFit(value: ImageFit)
```

设置图片的填充效果。未通过该接口设置时，默认为ImageFit.Cover，保持宽高比进行缩小或者放大。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageAttribute-objectFit(value: ImageFit): ImageAttribute--><!--Device-ImageAttribute-objectFit(value: ImageFit): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ImageFit](../arkts-apis/arkts-arkui-imagefit-e.md) | 是 | 图片的填充效果。 |

## objectRepeat

```TypeScript
objectRepeat(value: ImageRepeat)
```

设置图片的重复样式，从中心点向两边重复，剩余空间不足放下一张图片时会截断。SVG类型图源不支持该属性。

当组件的参数类型为[AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md)时设置该属性不生效。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageAttribute-objectRepeat(value: ImageRepeat): ImageAttribute--><!--Device-ImageAttribute-objectRepeat(value: ImageRepeat): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ImageRepeat](../arkts-apis/arkts-arkui-imagerepeat-e.md) | 是 | 图片的重复样式。<br/>默认值：ImageRepeat.NoRepeat |

## onComplete

```TypeScript
onComplete(
    callback: (event?: {
      /**
       * The width of the image source.
       *
       ****/
      /**
       * The width of the image source.
       *
       *****/
      /**
       * The width of the image source.
       *
       ******/
      /**
       * The width of the image source.
       *
       *******/
      width: number;
      /**
       * The height of the image source.
       *
       ****/
      /**
       * The height of the image source.
       *
       *****/
      /**
       * The height of the image source.
       *
       ******/
      /**
       * The height of the image source.
       *
       *******/
      height: number;
      /**
       * The width of the component source.
       *
       ****/
      /**
       * The width of the component source.
       *
       *****/
      /**
       * The width of the component source.
       *
       ******/
      /**
       * The width of the component source.
       *
       *******/
      componentWidth: number;
      /**
       * The height of the component source.
       *
       ****/
      /**
       * The height of the component source.
       *
       *****/
      /**
       * The height of the component source.
       *
       ******/
      /**
       * The height of the component source.
       *
       *******/
      componentHeight: number;
      /**
       * The value of the status of the image being loaded successfully.
       * If the returned status value is 0, the image data is successfully loaded.
       * If the returned status value is 1, the image is successfully decoded.
       *
       ****/
      /**
       * The value of the status of the image being loaded successfully.
       * If the returned status value is 0, the image data is successfully loaded.
       * If the returned status value is 1, the image is successfully decoded.
       *
       *****/
      /**
       * The value of the status of the image being loaded successfully.
       * If the returned status value is 0, the image data is successfully loaded.
       * If the returned status value is 1, the image is successfully decoded.
       *
       ******/
      /**
       * The value of the status of the image being loaded successfully.
       * If the returned status value is 0, the image data is successfully loaded.
       * If the returned status value is 1, the image is successfully decoded.
       *
       *******/
      loadingStatus: number;
      /**
       * The width of the picture that is actually drawn.
       *
       *******/
      /**
       * The width of the picture that is actually drawn.
       *
       ********/
      contentWidth: number;
      /**
       * The height of the picture that is actually drawn.
       *
       *******/
      /**
       * The height of the picture that is actually drawn.
       *
       ********/
      contentHeight: number;
      /**
       * The actual draw is offset from the x-axis of the component itself.
       *
       *******/
      /**
       * The actual draw is offset from the x-axis of the component itself.
       *
       ********/
      contentOffsetX: number;
      /**
       * The actual draw is offset from the y-axis of the component itself.
       *
       *******/
      /**
       * The actual draw is offset from the y-axis of the component itself.
       *
       ********/
      contentOffsetY: number;
    }) => void,
  )
```

Triggered when an image is successfully loaded or decoded.The size of the image source that is successfully loaded is returned, in pixels.

<p><strong>NOTE</strong>:<br>This event is not triggered if the parameter type of the component is AnimatedDrawableDescriptor.</p>

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageAttribute-onComplete(    callback: (event?: {      /**       * The width of the image source.       *       ****/      /**       * The width of the image source.       *       *****/      /**       * The width of the image source.       *       ******/      /**       * The width of the image source.       *       *******/      width: number;      /**       * The height of the image source.       *       ****/      /**       * The height of the image source.       *       *****/      /**       * The height of the image source.       *       ******/      /**       * The height of the image source.       *       *******/      height: number;      /**       * The width of the component source.       *       ****/      /**       * The width of the component source.       *       *****/      /**       * The width of the component source.       *       ******/      /**       * The width of the component source.       *       *******/      componentWidth: number;      /**       * The height of the component source.       *       ****/      /**       * The height of the component source.       *       *****/      /**       * The height of the component source.       *       ******/      /**       * The height of the component source.       *       *******/      componentHeight: number;      /**       * The value of the status of the image being loaded successfully.       * If the returned status value is 0, the image data is successfully loaded.       * If the returned status value is 1, the image is successfully decoded.       *       ****/      /**       * The value of the status of the image being loaded successfully.       * If the returned status value is 0, the image data is successfully loaded.       * If the returned status value is 1, the image is successfully decoded.       *       *****/      /**       * The value of the status of the image being loaded successfully.       * If the returned status value is 0, the image data is successfully loaded.       * If the returned status value is 1, the image is successfully decoded.       *       ******/      /**       * The value of the status of the image being loaded successfully.       * If the returned status value is 0, the image data is successfully loaded.       * If the returned status value is 1, the image is successfully decoded.       *       *******/      loadingStatus: number;      /**       * The width of the picture that is actually drawn.       *       *******/      /**       * The width of the picture that is actually drawn.       *       ********/      contentWidth: number;      /**       * The height of the picture that is actually drawn.       *       *******/      /**       * The height of the picture that is actually drawn.       *       ********/      contentHeight: number;      /**       * The actual draw is offset from the x-axis of the component itself.       *       *******/      /**       * The actual draw is offset from the x-axis of the component itself.       *       ********/      contentOffsetX: number;      /**       * The actual draw is offset from the y-axis of the component itself.       *       *******/      /**       * The actual draw is offset from the y-axis of the component itself.       *       ********/      contentOffsetY: number;    }) => void,  ): ImageAttribute--><!--Device-ImageAttribute-onComplete(    callback: (event?: {      /**       * The width of the image source.       *       ****/      /**       * The width of the image source.       *       *****/      /**       * The width of the image source.       *       ******/      /**       * The width of the image source.       *       *******/      width: number;      /**       * The height of the image source.       *       ****/      /**       * The height of the image source.       *       *****/      /**       * The height of the image source.       *       ******/      /**       * The height of the image source.       *       *******/      height: number;      /**       * The width of the component source.       *       ****/      /**       * The width of the component source.       *       *****/      /**       * The width of the component source.       *       ******/      /**       * The width of the component source.       *       *******/      componentWidth: number;      /**       * The height of the component source.       *       ****/      /**       * The height of the component source.       *       *****/      /**       * The height of the component source.       *       ******/      /**       * The height of the component source.       *       *******/      componentHeight: number;      /**       * The value of the status of the image being loaded successfully.       * If the returned status value is 0, the image data is successfully loaded.       * If the returned status value is 1, the image is successfully decoded.       *       ****/      /**       * The value of the status of the image being loaded successfully.       * If the returned status value is 0, the image data is successfully loaded.       * If the returned status value is 1, the image is successfully decoded.       *       *****/      /**       * The value of the status of the image being loaded successfully.       * If the returned status value is 0, the image data is successfully loaded.       * If the returned status value is 1, the image is successfully decoded.       *       ******/      /**       * The value of the status of the image being loaded successfully.       * If the returned status value is 0, the image data is successfully loaded.       * If the returned status value is 1, the image is successfully decoded.       *       *******/      loadingStatus: number;      /**       * The width of the picture that is actually drawn.       *       *******/      /**       * The width of the picture that is actually drawn.       *       ********/      contentWidth: number;      /**       * The height of the picture that is actually drawn.       *       *******/      /**       * The height of the picture that is actually drawn.       *       ********/      contentHeight: number;      /**       * The actual draw is offset from the x-axis of the component itself.       *       *******/      /**       * The actual draw is offset from the x-axis of the component itself.       *       ********/      contentOffsetX: number;      /**       * The actual draw is offset from the y-axis of the component itself.       *       *******/      /**       * The actual draw is offset from the y-axis of the component itself.       *       ********/      contentOffsetY: number;    }) => void,  ): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (event?: {       /**        * The width of the image source.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @since 7        */       /**        * The width of the image source.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @since 9        * @form        */       /**        * The width of the image source.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @crossplatform        * @since 10        * @form        */       /**        * The width of the image source.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @crossplatform        * @atomicservice        * @since 11        * @form        */       width: number;       /**        * The height of the image source.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @since 7        */       /**        * The height of the image source.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @since 9        * @form        */       /**        * The height of the image source.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @crossplatform        * @since 10        * @form        */       /**        * The height of the image source.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @crossplatform        * @atomicservice        * @since 11        * @form        */       height: number;       /**        * The width of the component source.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @since 7        */       /**        * The width of the component source.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @since 9        * @form        */       /**        * The width of the component source.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @crossplatform        * @since 10        * @form        */       /**        * The width of the component source.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @crossplatform        * @atomicservice        * @since 11        * @form        */       componentWidth: number;       /**        * The height of the component source.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @since 7        */       /**        * The height of the component source.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @since 9        * @form        */       /**        * The height of the component source.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @crossplatform        * @since 10        * @form        */       /**        * The height of the component source.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @crossplatform        * @atomicservice        * @since 11        * @form        */       componentHeight: number;       /**        * The value of the status of the image being loaded successfully.        * If the returned status value is 0, the image data is successfully loaded.        * If the returned status value is 1, the image is successfully decoded.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @since 7        */       /**        * The value of the status of the image being loaded successfully.        * If the returned status value is 0, the image data is successfully loaded.        * If the returned status value is 1, the image is successfully decoded.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @since 9        * @form        */       /**        * The value of the status of the image being loaded successfully.        * If the returned status value is 0, the image data is successfully loaded.        * If the returned status value is 1, the image is successfully decoded.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @crossplatform        * @since 10        * @form        */       /**        * The value of the status of the image being loaded successfully.        * If the returned status value is 0, the image data is successfully loaded.        * If the returned status value is 1, the image is successfully decoded.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @crossplatform        * @atomicservice        * @since 11        * @form        */       loadingStatus: number;       /**        * The width of the picture that is actually drawn.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @stagemodelonly        * @crossplatform        * @since 10        * @form        */       /**        * The width of the picture that is actually drawn.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @stagemodelonly        * @crossplatform        * @atomicservice        * @since 11        * @form        */       contentWidth: number;       /**        * The height of the picture that is actually drawn.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @stagemodelonly        * @crossplatform        * @since 10        * @form        */       /**        * The height of the picture that is actually drawn.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @stagemodelonly        * @crossplatform        * @atomicservice        * @since 11        * @form        */       contentHeight: number;       /**        * The actual draw is offset from the x-axis of the component itself.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @stagemodelonly        * @crossplatform        * @since 10        * @form        */       /**        * The actual draw is offset from the x-axis of the component itself.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @stagemodelonly        * @crossplatform        * @atomicservice        * @since 11        * @form        */       contentOffsetX: number;       /**        * The actual draw is offset from the y-axis of the component itself.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @stagemodelonly        * @crossplatform        * @since 10        * @form        */       /**        * The actual draw is offset from the y-axis of the component itself.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @stagemodelonly        * @crossplatform        * @atomicservice        * @since 11        * @form        */       contentOffsetY: number;     }) =&gt; void | 是 |  |

## onError

```TypeScript
onError(callback: ImageErrorCallback)
```

图片加载异常时触发该回调。

当组件的参数类型为[AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md)时该事件不触发。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageAttribute-onError(callback: ImageErrorCallback): ImageAttribute--><!--Device-ImageAttribute-onError(callback: ImageErrorCallback): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ImageErrorCallback](arkts-arkui-imageerrorcallback-t.md) | 是 | 图片加载异常时触发的回调。**说明：**建议开发者使用此回调，可快速确认图片加载失败时的具体原因，参见[ImageError](arkts-arkui-imageerror-i.md)的错误信息详细介绍。<br>**起始版本：** 11 |

## onFinish

```TypeScript
onFinish(event: () => void)
```

当加载的源文件为带动效的SVG格式图片时，SVG动效播放完成时会触发这个回调。如果动效为无限循环动效，则不会触发这个回调。

仅支持SVG格式的图片。当组件的参数类型为[AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md)时该事件不触发。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageAttribute-onFinish(event: () => void): ImageAttribute--><!--Device-ImageAttribute-onFinish(event: () => void): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () =&gt; void | 是 | 当加载的源文件为带动效的SVG格式图片时，SVG动效播放完成时会触发这个回调。如果动效为无限循环动效，则不会触发这个回调。 |

## orientation

```TypeScript
orientation(orientation: ImageRotateOrientation) : ImageAttribute
```

设置图像内容的显示方向。

该属性对[alt](ImageAttribute#alt(value: string | Resource | PixelMap))占位图不生效。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageAttribute-orientation(orientation: ImageRotateOrientation) : ImageAttribute--><!--Device-ImageAttribute-orientation(orientation: ImageRotateOrientation) : ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| orientation | [ImageRotateOrientation](arkts-arkui-imagerotateorientation-e.md) | 是 | 图像内容的显示方向。仅支持静态位图的显示。如果需要显示携带旋转角度信息或翻转信息的图片，建议使用ImageRotateOrientation.AUTO进行设置。默认值：ImageRotateOrientation.UP<br/>设置为undefined或null时，取值为ImageRotateOrientation.AUTO。 |

## privacySensitive

```TypeScript
privacySensitive(supported: boolean)
```

设置是否支持卡片敏感隐私信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageAttribute-privacySensitive(supported: boolean): ImageAttribute--><!--Device-ImageAttribute-privacySensitive(supported: boolean): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| supported | boolean | 是 | 是否支持卡片敏感隐私信息。默认值为false，表示不支持卡片敏感隐私信息，当设置为true时，隐私模式下图片将显示为半透明底板样式。**说明：**设置null则不敏感。<br/>进入隐私模式需要卡片框架支持。 |

## renderMode

```TypeScript
renderMode(value: ImageRenderMode)
```

设置图片的渲染模式。SVG类型图源不支持该属性。

设置[ColorFilter](ImageAttribute#colorFilter(value: ColorFilter | DrawingColorFilter))时，该属性设置不生效。

当组件的参数类型为[AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md)时设置该属性不生效。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageAttribute-renderMode(value: ImageRenderMode): ImageAttribute--><!--Device-ImageAttribute-renderMode(value: ImageRenderMode): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ImageRenderMode](arkts-arkui-imagerendermode-e.md) | 是 | 图片的渲染模式为原色或黑白。<br/>默认值：ImageRenderMode.Original |

## resizable

```TypeScript
resizable(value: ResizableOptions)
```

设置图像拉伸时可调整大小的图像选项。拉伸对拖拽缩略图以及占位图有效。

设置合法的 [ResizableOptions](arkts-arkui-resizableoptions-i.md) 时，objectRepeat属性、antialiased属性和orientation属性设置不生效。

当设置 top +bottom 大于原图的高或者 left + right 大于原图的宽时[ResizableOptions](arkts-arkui-resizableoptions-i.md) 属性设置不生效。

当组件的参数类型为[AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md)和SVG时设置该属性不生效。
> **说明：**  
>  
> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ImageAttribute-resizable(value: ResizableOptions): ImageAttribute--><!--Device-ImageAttribute-resizable(value: ResizableOptions): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResizableOptions](arkts-arkui-resizableoptions-i.md) | 是 | 图像拉伸时可调整大小的图像选项。 |

## sourceSize

```TypeScript
sourceSize(value: ImageSourceSize)
```

设置图片解码尺寸。仅在目标尺寸小于图源尺寸时生效。SVG类型图源和PixelMap资源不支持该属性。

当组件的参数类型为[AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md)时设置该属性不生效。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageAttribute-sourceSize(value: ImageSourceSize): ImageAttribute--><!--Device-ImageAttribute-sourceSize(value: ImageSourceSize): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ImageSourceSize](arkts-arkui-imagesourcesize-i.md) | 是 | 图片解码尺寸参数，降低图片的分辨率，常用于需要让图片显示尺寸比组件尺寸更小的场景。和[objectFit](ImageAttribute#objectFit)接口的ImageFit.None配合使用时可在组件内显示小图。<br>**起始版本：** 18 |

## supportSvg2

```TypeScript
supportSvg2(enable: boolean) : ImageAttribute
```

开启或关闭[SVG标签解析能力增强功能](../../../reference/apis-arkui/arkui-ts/ts-image-svg2-capabilities.md)，开启后相关SVG图片显示效果会有变化。

Image组件创建后，不支持动态修改该属性的值。

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本21开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageAttribute-supportSvg2(enable: boolean) : ImageAttribute--><!--Device-ImageAttribute-supportSvg2(enable: boolean) : ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 控制是否开启SVG标签解析能力增强功能。默认值：false<br>true：支持SVG解析新能力；false：保持原有SVG解析能力。 |

## syncLoad

```TypeScript
syncLoad(value: boolean)
```

设置是否同步加载图片。建议加载尺寸较小的本地图片时将syncLoad设为true，因为耗时较短，在主线程上执行即可。

当组件的参数类型为[AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md)时设置该属性不生效。

如果加载图片时出现闪烁，设置syncLoad为true。详情请参见[并发优化](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-click-to-click-response-optimization#section715115119192)。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageAttribute-syncLoad(value: boolean): ImageAttribute--><!--Device-ImageAttribute-syncLoad(value: boolean): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否同步加载图片，默认是异步加载。同步加载时阻塞UI线程，不会显示占位图。<br/>默认值：false，false表示异步加载图片，true表示同步加载图片。阻塞主线程超过6s将导致AppFreeze，具体参考[AppFreeze（应用冻屏）检测](../../../dfx/appfreeze-guidelines.md)。 |

