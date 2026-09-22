# GridRowOptions

```TypeScript
declare interface GridRowOptions
```

Defines layout options of the **GridRow** container.

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## breakpoints

```TypeScript
breakpoints?: BreakPoints
```

Used to set the monotonically increasing array of breakpoint positions, and the reference object for breakpoint switching (based on the app window or container size).

Default value: **{value: ["320vp", "600vp", "840vp"], reference: BreakpointsReference.WindowSize}**

Invalid value: The default value is used.

Unit: vp

**Type:** [BreakPoints](arkts-arkui-gridrow-comp-breakpoints-i.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## columns

```TypeScript
columns?: number | GridRowColumnOption
```

Number of layout columns.

The value must be a positive integer.

- Before API version 20: The default value is **12**.  
- Since API version 20: The default value is **{ xs: 2, sm: 4, md: 8, lg: 12, xl: 12, xxl: 12 }**.

Invalid value: The default value is used.

**Type:** number &#124; [GridRowColumnOption](arkts-arkui-gridrow-comp-gridrowcolumnoption-i.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: GridRowDirection
```

Grid layout arrangement direction. Supports **Row** (row-wise arrangement, suitable for conventional LTR layouts) and **RowReverse** (reverse row-wise arrangement, suitable for RTL layouts or scenarios requiring reverse arrangement).

Default value: **GridRowDirection.Row**

Invalid value: The default value is used.

**Type:** [GridRowDirection](arkts-arkui-gridrow-comp-gridrowdirection-e.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## gutter

```TypeScript
gutter?: Length | GutterOption
```

Grid layout gutter.

Default value: **0vp**

Invalid value: The default value is used.

Unit: vp

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md) &#124; [GutterOption](arkts-arkui-gridrow-comp-gutteroption-i.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
