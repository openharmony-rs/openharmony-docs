# ResourceImageAttachmentOptions

```TypeScript
declare interface ResourceImageAttachmentOptions
```

Defines the settings for images of the ResourceStr type.

**Since:** 15

<!--Device-unnamed-declare interface ResourceImageAttachmentOptions--><!--Device-unnamed-declare interface ResourceImageAttachmentOptions-End-->

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

<!--Device-ResourceImageAttachmentOptions-colorFilter?: ColorFilterType--><!--Device-ResourceImageAttachmentOptions-colorFilter?: ColorFilterType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## layoutStyle

```TypeScript
layoutStyle?: ImageAttachmentLayoutStyle
```

Image layout.

**Type:** [ImageAttachmentLayoutStyle](arkts-arkui-imageattachmentlayoutstyle-i.md)

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-ResourceImageAttachmentOptions-layoutStyle?: ImageAttachmentLayoutStyle--><!--Device-ResourceImageAttachmentOptions-layoutStyle?: ImageAttachmentLayoutStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## objectFit

```TypeScript
objectFit?: ImageFit
```

Scaling type of the image. The current enum type does not support **ImageFit.MATRIX**. For details about the enums and their descriptions, see **ImageFit**.

Default value: **ImageFit.Cover**.

**Type:** [ImageFit](arkts-arkui-imagefit-e.md)

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-ResourceImageAttachmentOptions-objectFit?: ImageFit--><!--Device-ResourceImageAttachmentOptions-objectFit?: ImageFit-End-->

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

<!--Device-ResourceImageAttachmentOptions-resizable?: ResizableOptions--><!--Device-ResourceImageAttachmentOptions-resizable?: ResizableOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## resourceValue

```TypeScript
resourceValue: Optional<ResourceStr>
```

Image data source.

**Type:** [Optional](../arkts-components/arkts-arkui-common-comp-optional-t.md)&lt;[ResourceStr](arkts-arkui-resourcestr-t.md)&gt;

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-ResourceImageAttachmentOptions-resourceValue: Optional<ResourceStr>--><!--Device-ResourceImageAttachmentOptions-resourceValue: Optional<ResourceStr>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: SizeOptions
```

Image size. Percentage values are not supported.

The default value of **size** depends on the value of **objectFit**. Different **objectFit** values correspond to different default size values.

**Type:** [SizeOptions](arkts-arkui-sizeoptions-i.md)

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-ResourceImageAttachmentOptions-size?: SizeOptions--><!--Device-ResourceImageAttachmentOptions-size?: SizeOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## supportSvg2

```TypeScript
supportSvg2?: boolean
```

Whether to enable [enhanced SVG tag parsing capabilities](../../../reference/apis-arkui/arkui-ts/ts-image-svg2-capabilities.md).

**true**: Enable enhanced SVG tag parsing. **false**: Use original SVG tag parsing.

Default value: **false**

**Type:** boolean

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-ResourceImageAttachmentOptions-supportSvg2?: boolean--><!--Device-ResourceImageAttachmentOptions-supportSvg2?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## syncLoad

```TypeScript
syncLoad?: boolean
```

Whether to load the image synchronously. By default, the image is loaded asynchronously. During synchronous loading, the UI thread is blocked and no placeholder image is displayed.

**true**: synchronous loading; **false**: asynchronous loading.

Default value: **false**

**Type:** boolean

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-ResourceImageAttachmentOptions-syncLoad?: boolean--><!--Device-ResourceImageAttachmentOptions-syncLoad?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## verticalAlign

```TypeScript
verticalAlign?: ImageSpanAlignment
```

Alignment of the image relative to the text. For details about the enums and their descriptions, see **ImageSpanAlignment**.

Default value: **ImageSpanAlignment.BOTTOM**.

**Type:** [ImageSpanAlignment](arkts-arkui-imagespanalignment-e.md)

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-ResourceImageAttachmentOptions-verticalAlign?: ImageSpanAlignment--><!--Device-ResourceImageAttachmentOptions-verticalAlign?: ImageSpanAlignment-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
