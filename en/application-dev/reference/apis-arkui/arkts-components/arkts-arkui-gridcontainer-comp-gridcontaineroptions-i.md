# GridContainerOptions

```TypeScript
declare interface GridContainerOptions
```

Defines the grid layout container configuration parameter object, used to set the number of columns, device width type, gutter, and margin for the **GridContainer** component.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** grid_col/GridColOptions and grid_row/GridRowOptions

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## columns

```TypeScript
columns?: number | "auto"
```

Total number of columns in the current layout. If set to a number, it must be a positive integer. When set to a number, a fixed-column layout is used. When set to **'auto'**, the system automatically determines the number of columns based on the device width type (XS: 2 columns, SM: 4 columns, MD: 8 columns, LG: 12 columns). If **0** or a negative number is passed, it is treated as not set, and the system automatically determines the number of columns.

Default value: **'auto'**

**Type:** number &#124; "auto"

**Since:** 7

**Deprecated since:** 9

**Substitutes:** grid_col/GridColOptions and grid_row/GridRowOptions

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## gutter

```TypeScript
gutter?: number | string
```

Gutter of the grid layout. Percentage values are not supported. When the type is number, the default unit is vp, with a value range of [0, +∞). If not set, it is automatically determined based on the device width type: 12 vp for XS, and 24 vp for SM, MD, and LG.

**Type:** number &#124; string

**Since:** 7

**Deprecated since:** 9

**Substitutes:** grid_col/GridColOptions and grid_row/GridRowOptions

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## margin

```TypeScript
margin?: number | string
```

Margin on both sides of the grid layout. Percentage values are not supported. When the type is number, the default unit is vp, with a value range of [0, +∞). If not set, it is automatically determined based on the device width type: 12 vp for XS, 24 vp for SM, 32 vp for MD, and 48 vp for LG.

**Type:** number &#124; string

**Since:** 7

**Deprecated since:** 9

**Substitutes:** grid_col/GridColOptions and grid_row/GridRowOptions

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## sizeType

```TypeScript
sizeType?: SizeType
```

Device width type for responsive layout.

Default value: **SizeType.Auto**

**Type:** [SizeType](arkts-arkui-gridcontainer-comp-sizetype-e.md)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** grid_col/GridColOptions and grid_row/GridRowOptions

**System capability:** SystemCapability.ArkUI.ArkUI.Full
