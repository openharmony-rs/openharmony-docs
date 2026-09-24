# GridColOptions

```TypeScript
declare interface GridColOptions
```

Defines the options of the **GridCol** component.

The values of `span`, `offset`, and `order` attributes are inherited in the sequence of **xs**, **sm**, **md**, **lg**, **xl**, and **xxl**. If no value is set for a breakpoint, the value is obtained from the previous breakpoint.

Since API version 20, the inheritance rules for `span` are described in [GridColColumnOption](arkts-arkui-gridcol-comp-gridcolcolumnoption-i.md), while the inheritance rules for `offset` and `order` remain unchanged.

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: number | GridColColumnOption
```

Number of columns by which the grid child component is offset from its original position. If offset is set to **0**, no offset is applied.

The value is a non-negative integer. The default value is **0**.

If an illegal value is set, the default value is used.

**Type:** number &#124; [GridColColumnOption](arkts-arkui-gridcol-comp-gridcolcolumnoption-i.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## order

```TypeScript
order?: number | GridColColumnOption
```

Sequence number of the element. Grid child components are sorted in ascending order based on their sequence numbers.

The value is a non-negative integer. The default value is **0**.

If an illegal value is set, the default value is used.

**NOTE:** 

When child components do not have **order** set or have the same **order**, they are displayed in code order.

When some child components have **order** set and others do not, the child components without **order** are placed first in sequence, and those with **order** are sorted in ascending order.

**Type:** number &#124; [GridColColumnOption](arkts-arkui-gridcol-comp-gridcolcolumnoption-i.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## span

```TypeScript
span?: number | GridColColumnOption
```

Number of columns occupied by the grid child component in the grid container component. If span is set to **0**, the element does not participate in layout calculation, that is, it is not rendered.

The value is a non-negative integer. The default value is **1**.

If an illegal value is set, the default value is used.

**Type:** number &#124; [GridColColumnOption](arkts-arkui-gridcol-comp-gridcolcolumnoption-i.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
