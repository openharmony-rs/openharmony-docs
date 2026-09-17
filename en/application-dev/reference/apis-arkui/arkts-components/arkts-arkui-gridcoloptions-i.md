# GridColOptions

Defines the options of the **GridCol** component.

The values of `span`, `offset`, and `order` attributes are inherited in the sequence of **xs**, **sm**, **md**, **lg**, **xl**, and **xxl**. If no value is set for a breakpoint, the value is obtained from the previous breakpoint.

Since API version 20, inheritance of the **span** property follows rules detailed in [GridColColumnOption](arkts-arkui-gridcolcolumnoption-i.md).

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: number | GridColColumnOption
```

Number of offset columns relative to the original position of the component.

The value must be a non-negative integer. Default value: **0**.

Invalid values are treated as the default value.

**Type:** number &#124; [GridColColumnOption](arkts-arkui-gridcolcolumnoption-i.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## order

```TypeScript
order?: number | GridColColumnOption
```

Sequence number of the component. Child components of the grid are sorted in ascending order based on their sequence numbers.

The value must be a non-negative integer. Default value: **0**.

Invalid values are treated as the default value.

**NOTE:** 

If a child component shares an **order** value with another child component or does not have **order** set, it is displayed based on its code sequence number.

If **order** is not set for all child components, those that have **order** set are displayed after those that do not and are sorted in ascending order based on the value.

**Type:** number &#124; [GridColColumnOption](arkts-arkui-gridcolcolumnoption-i.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## span

```TypeScript
span?: number | GridColColumnOption
```

Number of columns occupied by the component. If it is set to **0**, the component is not involved in layout calculation, that is, the component is not rendered.

The value must be a non-negative integer. Default value: **1**.

Invalid values are treated as the default value.

**Type:** number &#124; [GridColColumnOption](arkts-arkui-gridcolcolumnoption-i.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
