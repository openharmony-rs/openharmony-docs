# SliderBlockStyle

Slider组件滑块形状参数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface SliderBlockStyle--><!--Device-unnamed-export declare interface SliderBlockStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## image

```TypeScript
image?: ResourceStr
```

设置滑块图片资源。 图片显示区域大小由blockSize属性控制，请勿输入尺寸过大的图片。

**类型：** [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SliderBlockStyle-image?: ResourceStr--><!--Device-SliderBlockStyle-image?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shape

```TypeScript
shape?: CircleShape | EllipseShape | PathShape | RectShape
```

设置滑块使用的自定义形状。

**类型：** [CircleShape](../../apis-arkui/arkts-apis/arkts-arkui-arkui-shape-circleshape-c.md) \| [EllipseShape](../../apis-arkui/arkts-apis/arkts-arkui-arkui-shape-ellipseshape-c.md) \| [PathShape](../../apis-arkui/arkts-apis/arkts-arkui-arkui-shape-pathshape-c.md) \| [RectShape](../../apis-arkui/arkts-apis/arkts-arkui-arkui-shape-rectshape-c.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SliderBlockStyle-shape?: CircleShape | EllipseShape | PathShape | RectShape--><!--Device-SliderBlockStyle-shape?: CircleShape | EllipseShape | PathShape | RectShape-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: SliderBlockType
```

设置滑块形状。 默认值：SliderBlockType.DEFAULT，使用圆形滑块。

**类型：** [SliderBlockType](arkts-na-slider-sliderblocktype-e.md)

**默认值：** SliderBlockType.DEFAULT - indicating the round slider.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SliderBlockStyle-type: SliderBlockType--><!--Device-SliderBlockStyle-type: SliderBlockType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

