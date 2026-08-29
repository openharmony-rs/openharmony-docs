# ImageSpan属性/事件

属性继承自[BaseSpan](arkts-arkui-basespan-c.md)，通用属性方法支持尺寸设置、背景设置、边框设置。通用事件仅支持点击控制事件。还支持以下事件：@extends CommonMethod&lt;ImageSpanAttribute&gt; [since 10 - 10] @extends BaseSpan&lt;ImageSpanAttribute&gt; [since 11]

**继承/实现关系：** ImageSpanAttribute extends BaseSpan\<ImageSpanAttribute>

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## alt

```TypeScript
alt(value: PixelMap)
```

设置图片加载过程中显示的占位图。未通过该接口设置时，默认为null，不显示占位图。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | PixelMap | 是 | 设置图片加载过程中显示的占位图，支持[PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)类型。 |

## colorFilter

```TypeScript
colorFilter(filter: ColorFilter | DrawingColorFilter)
```

为图像设置颜色滤镜效果。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | ColorFilter \| [DrawingColorFilter](arkts-arkui-drawingcolorfilter-t.md) | 是 | 1. 给图像设置颜色滤镜效果，入参为一个4x5的RGBA转换矩阵。  矩阵第一行用于计算R'（新的红色分量），第二行用于计算G'（新的绿色分量），第三行用于计算B'（新的蓝色分量），第四行用于计算A'（新的透明度分量），4行分别代表不同的RGBA的分量。 当矩阵对角线值为1，其余值为0时，保持图片原有色彩。     **计算规则：** 如果输入的滤镜矩阵为：  像素点为[R, G, B, A]，色值的范围[0, 255] 则过滤后的颜色为 [R’, G’, B’, A’]   2. 支持@ohos.graphics.drawing的ColorFilter类型作为入参。    **说明：** 该接口中的DrawingColorFilter类型支持在原子化服务中使用。其中，svg类型的图源只对stroke属性生效。*@ohos.graphics.drawing** can be used as the input parameter. **NOTE：**The DrawingColorfilter type can be used in atomic services. The SVG image source takes effect only for the stroke attribute. |

## objectFit

```TypeScript
objectFit(value: ImageFit)
```

设置图片的缩放类型。适用于控制图片在容器中显示方式的场景。未通过该接口设置时，默认缩放类型为ImageFit.Cover。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ImageFit](../arkts-apis/arkts-arkui-imagefit-e.md) | 是 | 图片的缩放类型。 |

## onComplete

```TypeScript
onComplete(callback: ImageCompleteCallback)
```

图片数据加载成功和解码成功时均触发该回调，返回成功加载的图片尺寸。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ImageCompleteCallback](arkts-arkui-imagecompletecallback-t.md) | 是 | 图片数据加载成功和解码成功时触发的回调。 |

## onError

```TypeScript
onError(callback: ImageErrorCallback)
```

图片加载异常时触发该回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ImageErrorCallback](arkts-arkui-imageerrorcallback-t.md) | 是 | 图片加载异常时触发的回调。 |

## resizable

```TypeScript
resizable(value: ResizableOptions)
```

设置图像拉伸时可调整大小的图像选项。拉伸对拖拽缩略图以及占位图有效。设置合法的 [ResizableOptions](arkts-arkui-resizableoptions-i.md) 时，objectRepeat属性、antialiased属性和orientation属性设置不生效。当设置 top +bottom 大于原图的高或者 left + right 大于原图的宽时 [ResizableOptions](arkts-arkui-resizableoptions-i.md) 属性设置不生效。当组件的参数类型为动图、[AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md)和SVG时设置该属性 不生效。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResizableOptions](arkts-arkui-resizableoptions-i.md) | 是 | 图像拉伸时可调整大小的图像选项。 |

## supportSvg2

```TypeScript
supportSvg2(enable: Optional<boolean>)
```

开启或关闭SVG标签解析能力增强功能，开启后支持SVG解析新能力，适用于需要使用 SVG新特性的场景；关闭则保持原有SVG解析能力，适用于兼容旧版本SVG图片显示的场景。未通过该接口设置时，默认保持原有SVG解析能力。ImageSpan组件创建后，不支持动态修改该属性的值。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 控制是否开启 SVG标签解析能力增强功能。 true：支持SVG解析新能力；false：保持原有SVG解析能力。 |

## verticalAlign

```TypeScript
verticalAlign(value: ImageSpanAlignment)
```

设置图片基于行高的对齐方式。适用于图文混排场景中调整图片与文字的垂直对齐效果。未通过该接口设置时，默认对齐方式为ImageSpanAlignment.BOTTOM。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ImageSpanAlignment](../arkts-apis/arkts-arkui-imagespanalignment-e.md) | 是 | 图片基于行高的对齐方式。 |
