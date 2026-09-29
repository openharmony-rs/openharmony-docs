# SliderBlockStyle

```TypeScript
declare interface SliderBlockStyle
```

Describes the style of the slider in the block direction.

**Since:** 10

<!--Device-unnamed-declare interface SliderBlockStyle--><!--Device-unnamed-declare interface SliderBlockStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## image

```TypeScript
image?: ResourceStr
```

Image resource of the slider.

The size of the image display area is controlled by the **blockSize** attribute. Do not use an oversized image.

**Note:** This attribute takes effect only when **type** is set to **SliderBlockType.IMAGE**, and is mutually exclusive with the **shape** attribute. They cannot be used together.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SliderBlockStyle-image?: ResourceStr--><!--Device-SliderBlockStyle-image?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shape

```TypeScript
shape?: CircleAttribute | EllipseAttribute | PathAttribute | RectAttribute
```

Custom shape of the block.

**Note:** This attribute takes effect only when **type** is set to **SliderBlockType.SHAPE**, and is mutually exclusive with the **image** attribute. They cannot be used together.

**Type:** [CircleAttribute](arkts-arkui-circle-comp-attribute.md) &#124; [EllipseAttribute](arkts-arkui-ellipse-comp-attribute.md) &#124; [PathAttribute](arkts-arkui-path-comp-attribute.md) &#124; [RectAttribute](arkts-arkui-rect-comp-attribute.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SliderBlockStyle-shape?: CircleAttribute | EllipseAttribute | PathAttribute | RectAttribute--><!--Device-SliderBlockStyle-shape?: CircleAttribute | EllipseAttribute | PathAttribute | RectAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: SliderBlockType
```

Type of the slider.

Default Value: **SliderBlockType.DEFAULT**, indicating a circular slider.

**Type:** [SliderBlockType](arkts-arkui-slider-comp-sliderblocktype-e.md)

**Default:** 
- API version 11+: SliderBlockType.DEFAULT - indicating the round slider.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SliderBlockStyle-type: SliderBlockType--><!--Device-SliderBlockStyle-type: SliderBlockType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
