# ScrollableBarModeOptions

```TypeScript
interface ScrollableBarModeOptions
```

Defines a layout style object of the tab bar in Scrollable mode.

**Since:** 10

<!--Device-unnamed-interface ScrollableBarModeOptions--><!--Device-unnamed-interface ScrollableBarModeOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## margin

```TypeScript
margin?: Dimension
```

Left and right margins of the tab bar in Scrollable mode (percentage setting is not supported).

Default value: **0.0**

Unit: vp

Value range: [0, +∞). When the value is set to less than 0, the default value is used.

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScrollableBarModeOptions-margin?: Dimension--><!--Device-ScrollableBarModeOptions-margin?: Dimension-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## nonScrollableLayoutStyle

```TypeScript
nonScrollableLayoutStyle?: LayoutStyle
```

Arrangement of tabs when not scrolling in Scrollable mode. This attribute is valid only in horizontal mode.

Default value: **LayoutStyle.ALWAYS_CENTER**

**Type:** [LayoutStyle](arkts-arkui-tabs-comp-layoutstyle-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScrollableBarModeOptions-nonScrollableLayoutStyle?: LayoutStyle--><!--Device-ScrollableBarModeOptions-nonScrollableLayoutStyle?: LayoutStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
