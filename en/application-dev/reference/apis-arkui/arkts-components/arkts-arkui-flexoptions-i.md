# FlexOptions

Describes the layout and alignment of child components within the **Flex** component.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## alignContent

```TypeScript
alignContent?: FlexAlign
```

Alignment mode of multiple lines when there is extra space along the cross axis. This parameter is valid only when **wrap** is set to **Wrap** or **WrapReverse**. If an invalid value is passed, the default value will be used. Default value: **FlexAlign.Start**.

**Type:** [FlexAlign](../arkts-apis/arkts-arkui-flexalign-e.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## alignItems

```TypeScript
alignItems?: ItemAlign
```

Alignment mode of the child components in the **Flex** component along the cross axis. If an invalid value is passed, the default value will be used. Default value: **ItemAlign.Start**.

**Type:** [ItemAlign](../arkts-apis/arkts-arkui-itemalign-e.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: FlexDirection
```

Direction in which child components are arranged in the **Flex** component, that is, the direction of the main axis. If an invalid value is passed, the default value will be used. Default value: **FlexDirection.Row**.

**Type:** [FlexDirection](../arkts-apis/arkts-arkui-flexdirection-e.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## justifyContent

```TypeScript
justifyContent?: FlexAlign
```

Alignment mode of the child components in the **Flex** component along the main axis. If an invalid value is passed, the default value will be used. Default value: **FlexAlign.Start**.

**Type:** [FlexAlign](../arkts-apis/arkts-arkui-flexalign-e.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
space?: FlexSpaceOptions
```

Spacing between child components along the main axis or cross axis of the **Flex** component. Invalid values are treated as the default value. This parameter does not take effect if the value specified is a negative number or percentage, or if **justifyContent** is set to **FlexAlign.SpaceBetween**, **FlexAlign.SpaceAround**, or **FlexAlign.SpaceEvenly**. Default value: **{main: LengthMetrics.px(0), cross: LengthMetrics.px(0)}**.

**Type:** [FlexSpaceOptions](arkts-arkui-flexspaceoptions-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## wrap

```TypeScript
wrap?: FlexWrap
```

Whether the **Flex** component has a single line or multiple lines. If an invalid value is passed, the default value will be used.  
> **NOTE:** 
> 
> When wrapped onto multiple lines, the child elements on the new line are stacked in the direction based on the
> cross axis direction. Default value: **FlexWrap.NoWrap**.

**Type:** [FlexWrap](../arkts-apis/arkts-arkui-flexwrap-e.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
