# ImageAttachment

```TypeScript
declare class ImageAttachment
```

Describes the image attachment.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(value: ImageAttachmentInterface)
```

A constructor used to create an image object.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ImageAttachmentInterface](arkts-arkui-imageattachmentinterface-i.md) | Yes | Image attachment options. |

<a id="constructor-1"></a>

## constructor

```TypeScript
constructor(attachment: Optional<AttachmentType>)
```

A constructor used to create an image object. Compared to the constructor with a **value** type parameter, this constructor with an **attachment** type parameter supports images of **undefined** and [ResourceStr](arkts-arkui-resourcestr-t.md) types.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| attachment | [Optional](../arkts-components/arkts-arkui-common-comp-optional-t.md)&lt;[AttachmentType](arkts-arkui-attachmenttype-t.md)&gt; | Yes | Image attachment, which can be of type PixelMap or [ResourceStr](arkts-arkui-resourcestr-t.md). |

## colorFilter

```TypeScript
readonly colorFilter?: ColorFilterType
```

Image color filter of the styled string.

**Type:** [ColorFilterType](arkts-arkui-colorfiltertype-t.md)

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## layoutStyle

```TypeScript
readonly layoutStyle?: ImageAttachmentLayoutStyle
```

Image layout of the styled string.

**Type:** [ImageAttachmentLayoutStyle](arkts-arkui-imageattachmentlayoutstyle-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## objectFit

```TypeScript
readonly objectFit?: ImageFit
```

Image scale type of the styled string.

**Type:** [ImageFit](arkts-arkui-imagefit-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## resizable

```TypeScript
readonly resizable?: ResizableOptions
```

Resizable image options of the styled string.

**Type:** [ResizableOptions](../arkts-components/arkts-arkui-image-comp-resizableoptions-i.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
readonly size?: SizeOptions
```

Image size of the styled string.

Number-type values use px as the unit.

**Type:** [SizeOptions](arkts-arkui-sizeoptions-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## sizeInVp

```TypeScript
readonly sizeInVp?: SizeOptions
```

Image size of the styled string.

Number-type values use vp as the unit.

If **ImageAttachment** is set to a negative value or **undefined**, **undefined** is returned.

**Type:** [SizeOptions](arkts-arkui-sizeoptions-i.md)

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## supportSvg2

```TypeScript
readonly supportSvg2?: boolean
```

Whether to enable [enhanced SVG tag parsing capabilities](../../../reference/apis-arkui/arkui-ts/ts-image-svg2-capabilities.md).

**true**: Enable enhanced SVG tag parsing. **false**: Use original SVG tag parsing.

Default value: **false**

**Type:** boolean

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
readonly value: PixelMap
```

Image data source of the styled string.

**Type:** [PixelMap](../arkts-components/arkts-arkui-common-comp-pixelmap-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## verticalAlign

```TypeScript
readonly verticalAlign?: ImageSpanAlignment
```

Image alignment mode of the styled string.

**Type:** [ImageSpanAlignment](arkts-arkui-imagespanalignment-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
