# ImageSpan属性/事件

属性继承自[BaseSpan](arkts-arkui-basespan-c.md)，通用属性方法支持[尺寸设置](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)、[背景设置](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)、[边框设置](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)。

通用事件仅支持[点击控制事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)。还支持以下事件：

**继承/实现关系：** ImageSpanAttribute extends [BaseSpan<ImageSpanAttribute>]

**起始版本：** 10

<!--Device-unnamed-declare class ImageSpanAttribute extends BaseSpan<ImageSpanAttribute>--><!--Device-unnamed-declare class ImageSpanAttribute extends BaseSpan<ImageSpanAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## alt

```TypeScript
alt(value: PixelMap)
```

设置图片加载过程中显示的占位图。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ImageSpanAttribute-alt(value: PixelMap): ImageSpanAttribute--><!--Device-ImageSpanAttribute-alt(value: PixelMap): ImageSpanAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) | 是 | 设置图片加载过程中显示的占位图，支持[PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)类型。<br/>默认值：null |

## colorFilter

```TypeScript
colorFilter(filter: ColorFilter | DrawingColorFilter)
```

为图像设置颜色滤镜效果。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-ImageSpanAttribute-colorFilter(filter: ColorFilter | DrawingColorFilter): ImageSpanAttribute--><!--Device-ImageSpanAttribute-colorFilter(filter: ColorFilter | DrawingColorFilter): ImageSpanAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | [ColorFilter](../arkts-apis/arkts-arkui-colorfilter-c.md) \| DrawingColorFilter | 是 | 1. 给图像设置颜色滤镜效果，入参为一个4x5的RGBA转换矩阵。<br/>矩阵第一行表示R（红色）的向量值，第二行表示G（绿色）的向量值，第三行表示B（蓝色）的向量值，第四行表示A（透明度）的向量值，4行分别代表不同的RGBA的向量值。<br/>当矩阵对角线值为1，其余值为0时，保持图片原有色彩。<br/> **计算规则：**<br/>如果输入的滤镜矩阵为：<br/>![image-matrix-1](../../../reference/apis-arkui/arkui-ts/figures/image_matrix_1.png)<br/>像素点为[R, G, B, A]，色值的范围[0, 255]<br/>则过滤后的颜色为 [R’, G’, B’, A’]<br/>![image-matrix-2](../../../reference/apis-arkui/arkui-ts/figures/image_matrix_2.png)<br/>2. 支持@ohos.graphics.drawing的ColorFilter类型作为入参。<br/>**说明：** <br/>该接口中的DrawingColorFilter类型支持在原子化服务中使用。其中，svg类型的图源只对stroke属性生效。*@ohos.graphics.drawing** can be used as the input parameter.<br>**NOTE**<br>The DrawingColorfilter type can be used in atomic services. The SVG image source takes effect only for the stroke attribute. |

## objectFit

```TypeScript
objectFit(value: ImageFit)
```

设置图片的缩放类型。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ImageSpanAttribute-objectFit(value: ImageFit): ImageSpanAttribute--><!--Device-ImageSpanAttribute-objectFit(value: ImageFit): ImageSpanAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ImageFit](../arkts-apis/arkts-arkui-imagefit-e.md) | 是 | 图片的缩放类型。<br/>默认值：ImageFit.Cover |

## onComplete

```TypeScript
onComplete(callback: ImageCompleteCallback)
```

图片数据加载成功和解码成功时均触发该回调，返回成功加载的图片尺寸。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ImageSpanAttribute-onComplete(callback: ImageCompleteCallback): ImageSpanAttribute--><!--Device-ImageSpanAttribute-onComplete(callback: ImageCompleteCallback): ImageSpanAttribute-End-->

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

<!--Device-ImageSpanAttribute-onError(callback: ImageErrorCallback): ImageSpanAttribute--><!--Device-ImageSpanAttribute-onError(callback: ImageErrorCallback): ImageSpanAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ImageErrorCallback](arkts-arkui-imageerrorcallback-t.md) | 是 | 图片加载异常时触发的回调。 |

## supportSvg2

```TypeScript
supportSvg2(enable: Optional<boolean>)
```

开启或关闭[SVG标签解析能力增强功能](../../../reference/apis-arkui/arkui-ts/ts-image-svg2-capabilities.md)，开启后相关SVG图片显示效果会有变化。

ImageSpan组件创建后，不支持动态修改该属性的值。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ImageSpanAttribute-supportSvg2(enable: Optional<boolean>): ImageSpanAttribute--><!--Device-ImageSpanAttribute-supportSvg2(enable: Optional<boolean>): ImageSpanAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 控制是否开启[SVG标签解析能力增强功能](../../../reference/apis-arkui/arkui-ts/ts-image-svg2-capabilities.md)。<br>true：支持SVG解析新能力；false：保持原有SVG解析能力。<br>默认值：false |

## verticalAlign

```TypeScript
verticalAlign(value: ImageSpanAlignment)
```

设置图片基于行高的对齐方式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ImageSpanAttribute-verticalAlign(value: ImageSpanAlignment): ImageSpanAttribute--><!--Device-ImageSpanAttribute-verticalAlign(value: ImageSpanAlignment): ImageSpanAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ImageSpanAlignment](../arkts-apis/arkts-arkui-imagespanalignment-e.md) | 是 | 图片基于行高的对齐方式。<br />默认值：ImageSpanAlignment.BOTTOM |

