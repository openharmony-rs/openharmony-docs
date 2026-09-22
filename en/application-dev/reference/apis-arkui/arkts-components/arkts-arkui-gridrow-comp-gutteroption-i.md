# GutterOption

```TypeScript
declare interface GutterOption
```

Provides the gutter options for the grid layout to define the spacing between child components in different directions.

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## x

```TypeScript
x?: Length | GridRowSizeOption
```

Horizontal gutter between child components in the grid. Value range: a number or string greater than or equal to 0.

Default value: **0vp**.

Invalid value: the default value is used.

Unit: vp

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md) &#124; [GridRowSizeOption](arkts-arkui-gridrow-comp-gridrowsizeoption-i.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## y

```TypeScript
y?: Length | GridRowSizeOption
```

Vertical gutter between child components in the grid. Value range: a number or string greater than or equal to 0.

Default value: **0vp**.

Invalid value: the default value is used.

Unit: vp

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md) &#124; [GridRowSizeOption](arkts-arkui-gridrow-comp-gridrowsizeoption-i.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
