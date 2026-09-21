# GeometryInfo

```TypeScript
declare interface GeometryInfo extends SizeResult
```

Provides layout information of the parent component (a custom component). Inherits from [SizeResult](arkts-arkui-common-comp-sizeresult-i.md). In the **onMeasureSize** and **onPlaceChildren** methods, the **GeometryInfo** object can be obtained through the **selfLayoutInfo** parameter. It contains the border width, margin, and padding information of the parent component, which developers need to consider when calculating the layout of child components.

**Inheritance/Implementation:** GeometryInfo extends [SizeResult](arkts-arkui-common-comp-sizeresult-i.md)

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderWidth

```TypeScript
borderWidth: EdgeWidth
```

Border width of the parent component. Unit: vp.

**Type:** [EdgeWidth](../arkts-apis/arkts-arkui-edgewidth-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## margin

```TypeScript
margin: Margin
```

Margin of the parent component. Unit: vp.

**Type:** [Margin](../arkts-apis/arkts-arkui-margin-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## padding

```TypeScript
padding: Padding
```

Padding of the parent component. Unit: vp.

**Type:** Padding

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
