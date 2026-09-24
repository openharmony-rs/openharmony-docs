# ScrollableBarModeOptions

```TypeScript
interface ScrollableBarModeOptions
```

Implements a **ScrollableBarModeOptions** object.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## margin

```TypeScript
margin?: Dimension
```

Left and right margin of the tab bar in scrollable mode. It cannot be set in percentage.

Default value: **0.0**

Unit: vp

Value range: [0, +∞)

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## nonScrollableLayoutStyle

```TypeScript
nonScrollableLayoutStyle?: LayoutStyle
```

Tab layout mode of the tab bar when not scrolling in scrollable mode.

Default value: **LayoutStyle.ALWAYS_CENTER**

**Type:** [LayoutStyle](arkts-arkui-tabs-comp-layoutstyle-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
