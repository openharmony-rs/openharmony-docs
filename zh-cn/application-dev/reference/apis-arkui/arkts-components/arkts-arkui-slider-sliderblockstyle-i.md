# SliderBlockStyle

Slider组件滑块形状参数。

**起始版本：** 10

<!--Device-unnamed-declare interface SliderBlockStyle--><!--Device-unnamed-declare interface SliderBlockStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## image

```TypeScript
image?: ResourceStr
```

设置滑块图片资源。

图片显示区域大小由blockSize属性控制，请勿输入尺寸过大的图片。

**类型：** ResourceStr

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SliderBlockStyle-image?: ResourceStr--><!--Device-SliderBlockStyle-image?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shape

```TypeScript
shape?: CircleAttribute | EllipseAttribute | PathAttribute | RectAttribute
```

设置滑块使用的自定义形状。

**类型：** CircleAttribute | EllipseAttribute | PathAttribute | RectAttribute

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SliderBlockStyle-shape?: CircleAttribute | EllipseAttribute | PathAttribute | RectAttribute--><!--Device-SliderBlockStyle-shape?: CircleAttribute | EllipseAttribute | PathAttribute | RectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: SliderBlockType
```

设置滑块形状。

默认值：SliderBlockType.DEFAULT，使用圆形滑块。

**类型：** SliderBlockType

**默认值：** SliderBlockType.DEFAULT - indicating the round slider. [since 11]

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SliderBlockStyle-type: SliderBlockType--><!--Device-SliderBlockStyle-type: SliderBlockType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

