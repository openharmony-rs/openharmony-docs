# FlexOptions

```TypeScript
declare interface FlexOptions
```

Describes the layout and alignment of child components within the **Flex** component.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## alignContent

```TypeScript
alignContent?: FlexAlign
```

Alignment of multiple lines of content when there is extra space on the cross axis. This attribute takes effect only when wrap is set to **Wrap** or **WrapReverse**.

Default value: **FlexAlign.Start**

Invalid values are handled as the default value.

The options are as follows:

- **Start**: Aligned with the start edge.  
- **Center**: Center alignment.  
- **End**: Aligned with the end edge.  
- **SpaceBetween**: Aligned with both edges, with equal spacing between lines.  
- **SpaceAround:** Equal spacing on both sides of each line.  
- **SpaceEvenly**: Equal spacing between lines and at both ends.

**Type:** [FlexAlign](../arkts-apis/arkts-arkui-flexalign-e.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## alignItems

```TypeScript
alignItems?: ItemAlign
```

Alignment of all child components on the cross axis of the **Flex** container. After this attribute is set, child components are positioned along the cross axis according to the specified alignment.

Default value: **ItemAlign.Start**

Invalid values are handled as the default value.

The options are as follows:

- **Auto**: Uses the alignment of the parent container.  
- **Start**: Aligned with the start edge.  
- **Center**: Center alignment.  
- **End**: Aligned with the end edge.  
- **Stretch**: Stretched to fill the container.  
- **Baseline**: Aligned with the baseline.

**Type:** [ItemAlign](../arkts-apis/arkts-arkui-itemalign-e.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: FlexDirection
```

Direction in which child components are arranged in the **Flex** container, that is, the direction of the main axis. After this attribute is set, child components are arranged along the main axis in the specified direction.

Default value: **FlexDirection.Row**

Invalid values are handled as the default value.

The options are as follows:

- **Row**: The main axis runs horizontally, starting from the left.  
- **RowReverse**: The main axis runs horizontally, starting from the right.  
- **Column**: The main axis runs vertically, starting from the top.  
- **ColumnReverse**: The main axis runs vertically, starting from the bottom.

The starting positions of **Row** and **RowReverse** are affected by the **direction** attribute of the container.

**Type:** [FlexDirection](../arkts-apis/arkts-arkui-flexdirection-e.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## justifyContent

```TypeScript
justifyContent?: FlexAlign
```

Alignment of all child components on the main axis of the **Flex** container. After this attribute is set, child components are distributed and arranged along the main axis according to the specified alignment.

Default value: **FlexAlign.Start**

Invalid values are handled as the default value.

The options are as follows:

- **Start**: Aligned with the start edge.  
- **Center**: Center alignment.  
- **End**: Aligned with the end edge.  
- **SpaceBetween**: Aligned with both edges, with equal spacing between child components.  
- **SpaceAround**: Equal spacing on both sides of each child component.  
- **SpaceEvenly**: Equal spacing between child components and at both ends.

**Note:** When **justifyContent** is set to **SpaceBetween**, **SpaceAround**, or **SpaceEvenly**, the **space** parameter does not take effect.

**Type:** [FlexAlign](../arkts-apis/arkts-arkui-flexalign-e.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
space?: FlexSpaceOptions
```

Spacing between child components in the **Flex** container on the main axis and cross axis. It contains two attributes: **main** and **cross**. Pass this parameter when you need to adjust the spacing between child components. If not passed, there is no spacing between child components.

Default value: **{main: LengthMetrics.px(0), cross: LengthMetrics.px(0)}**

Invalid values are handled as the default value.

When **space.main** or **space.cross** is a negative value, or when **justifyContent** is set to **FlexAlign.SpaceBetween**, **FlexAlign.SpaceAround**, or **FlexAlign.SpaceEvenly**, the **space** parameter does not take effect. The **main** attribute takes effect in both single-line and multi-line layouts, while the **cross** attribute takes effect only when **wrap** is set to **Wrap** or **WrapReverse** (multi-line layout).

**Type:** [FlexSpaceOptions](arkts-arkui-flex-comp-flexspaceoptions-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## wrap

```TypeScript
wrap?: FlexWrap
```

Whether the **Flex** container has a single line/column or multiple lines/columns. After this attribute is set, child components are laid out in the container according to the specified wrap mode.

Default value: **FlexWrap.NoWrap**

Invalid values are handled as the default value.

The options are as follows:

- **NoWrap**: No wrapping. Child components are truncated if their total width exceeds the container width.  
- **Wrap**: Wrapping is enabled. The first line is at the top.  
- **WrapReverse**: Wrapping is enabled. The first line is at the bottom.

**Note:** In multi-line layout, the stacking direction of new lines is determined by the cross axis direction.

**Type:** [FlexWrap](../arkts-apis/arkts-arkui-flexwrap-e.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
