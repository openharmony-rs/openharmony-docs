# ImageAttachmentInterface

```TypeScript
declare interface ImageAttachmentInterface
```

Defines the ImageAttachmentInterface.

**Since:** 12

<!--Device-unnamed-declare interface ImageAttachmentInterface--><!--Device-unnamed-declare interface ImageAttachmentInterface-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## colorFilter

```TypeScript
colorFilter?: ColorFilterType
```

Color filter effect of the image in the styled string. If this parameter is not passed, no color filter is applied and the image is displayed in its original color.

**Type:** [ColorFilterType](arkts-arkui-colorfiltertype-t.md)

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-ImageAttachmentInterface-colorFilter?: ColorFilterType--><!--Device-ImageAttachmentInterface-colorFilter?: ColorFilterType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## layoutStyle

```TypeScript
layoutStyle?: ImageAttachmentLayoutStyle
```

Image layout. If this parameter is not passed, the default layout is used (the margin, padding, and corner radius are all 0).

**Type:** [ImageAttachmentLayoutStyle](arkts-arkui-imageattachmentlayoutstyle-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ImageAttachmentInterface-layoutStyle?: ImageAttachmentLayoutStyle--><!--Device-ImageAttachmentInterface-layoutStyle?: ImageAttachmentLayoutStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## objectFit

```TypeScript
objectFit?: ImageFit
```

Sets the scaling type of the image. The current enum type does not support **ImageFit.MATRIX**. For details about the enums, see **ImageFit**.

Default value: **ImageFit.Cover**

**Type:** [ImageFit](arkts-arkui-imagefit-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ImageAttachmentInterface-objectFit?: ImageFit--><!--Device-ImageAttachmentInterface-objectFit?: ImageFit-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## resizable

```TypeScript
resizable?: ResizableOptions
```

Resizable image options of the styled string.

**Type:** [ResizableOptions](../arkts-components/arkts-arkui-image-comp-resizableoptions-i.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-ImageAttachmentInterface-resizable?: ResizableOptions--><!--Device-ImageAttachmentInterface-resizable?: ResizableOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: SizeOptions
```

Image size. Percentage values are not supported.

The default value of size is related to the value of **objectFit**. Different **objectFit** values correspond to different default values of size. For example, when **objectFit** is **Cover**, the image height is the component height minus the top and bottom padding of the component, and the image width is the component width minus the left and right padding of the component.

**Type:** [SizeOptions](arkts-arkui-sizeoptions-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ImageAttachmentInterface-size?: SizeOptions--><!--Device-ImageAttachmentInterface-size?: SizeOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: PixelMap
```

Image data source.

**Type:** [PixelMap](../arkts-components/arkts-arkui-common-comp-pixelmap-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ImageAttachmentInterface-value: PixelMap--><!--Device-ImageAttachmentInterface-value: PixelMap-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## verticalAlign

```TypeScript
verticalAlign?: ImageSpanAlignment
```

Alignment of the image relative to the text.

Default value: **ImageSpanAlignment.BOTTOM**

**Type:** [ImageSpanAlignment](arkts-arkui-imagespanalignment-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ImageAttachmentInterface-verticalAlign?: ImageSpanAlignment--><!--Device-ImageAttachmentInterface-verticalAlign?: ImageSpanAlignment-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
