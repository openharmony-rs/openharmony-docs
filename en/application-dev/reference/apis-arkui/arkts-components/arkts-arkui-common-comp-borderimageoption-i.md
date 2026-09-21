# BorderImageOption

```TypeScript
declare interface BorderImageOption
```

Border image option

@interface BorderImageOption

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fill

```TypeScript
fill?: boolean
```

Whether to fill the center of the border image. true: Fill the center of the border image. false: Do not fill the center of the border image.

**Type:** boolean

**Default:** false

**Since:** 11

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## outset

```TypeScript
outset?: Length | EdgeWidths | LocalizedEdgeWidths
```

Amount by which the border image is extended beyond the border box.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md) &#124; EdgeWidths &#124; [LocalizedEdgeWidths](../arkts-apis/arkts-arkui-localizededgewidths-i.md)

**Default:** 0

**Since:** 12

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## repeat

```TypeScript
repeat?: RepeatMode
```

Repeat mode of the source image's slices on the border.

**Type:** [RepeatMode](arkts-arkui-common-comp-repeatmode-e.md)

**Default:** RepeatMode.Stretch

**Since:** 11

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## slice

```TypeScript
slice?: Length | EdgeWidths | LocalizedEdgeWidths
```

Slice width of the upper left corner, upper right corner, lower left corner, and lower right corner of the border image.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md) &#124; EdgeWidths &#124; [LocalizedEdgeWidths](../arkts-apis/arkts-arkui-localizededgewidths-i.md)

**Default:** 0

**Since:** 12

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## source

```TypeScript
source?: string | Resource | LinearGradient
```

Source or gradient color of the border image. When the type is string, this parameter sets the border image source. For details about how to reference image resources, see Loading Image Resources.

<p>&lt;strong&gt;NOTE&lt;/strong&gt;: <br>The border image source applies only to container components, such as Row, Column, and Flex. </p>

**Type:** string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) &#124; [LinearGradient](arkts-arkui-common-comp-lineargradient-i.md)

**Since:** 11

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Length | EdgeWidths | LocalizedEdgeWidths
```

Width of the border image.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md) &#124; EdgeWidths &#124; [LocalizedEdgeWidths](../arkts-apis/arkts-arkui-localizededgewidths-i.md)

**Default:** 0

**Since:** 12

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
