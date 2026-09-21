# SliderBlockStyle

```TypeScript
declare interface SliderBlockStyle
```

Slider组件滑块形状参数。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## image

```TypeScript
image?: ResourceStr
```

设置滑块图片资源。

图片显示区域大小由blockSize属性控制，请勿输入尺寸过大的图片。

**类型：** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shape

```TypeScript
shape?: CircleAttribute | EllipseAttribute | PathAttribute | RectAttribute
```

设置滑块使用的自定义形状。

**类型：** [CircleAttribute](arkts-arkui-circle-comp-attribute.md) &#124; [EllipseAttribute](arkts-arkui-ellipse-comp-attribute.md) &#124; [PathAttribute](arkts-arkui-path-comp-attribute.md) &#124; [RectAttribute](arkts-arkui-rect-comp-attribute.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: SliderBlockType
```

滑块形状。

默认值：SliderBlockType.DEFAULT，使用圆形滑块。

**类型：** [SliderBlockType](arkts-arkui-slider-comp-sliderblocktype-e.md)

**默认值：** 
- API版本11+：SliderBlockType.DEFAULT - indicating the round slider.

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
