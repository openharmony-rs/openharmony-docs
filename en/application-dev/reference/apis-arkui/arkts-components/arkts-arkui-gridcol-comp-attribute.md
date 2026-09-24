# GridCol properties/events

```TypeScript
declare class GridColAttribute extends CommonMethod<GridColAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp-commonmethod-c.md), the following attributes are supported.

The [universal events](arkts-arkui-common-comp-commonmethod-c.md) are supported.

**Inheritance/Implementation:** GridColAttribute extends CommonMethod<GridColAttribute>

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## gridColOffset

```TypeScript
gridColOffset(value: number | GridColColumnOption)
```

Sets the number of columns by which the grid child component is offset relative to its original position.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [GridColColumnOption](arkts-arkui-gridcol-comp-gridcolcolumnoption-i.md) | Yes | Number of columns offset relative to the original position. A value of **0** for **gridColOffset** indicates no offset. <br>The value is a non-negative integer, with a default value of **0**. <br>Illegal value: processed as the default value. <br>**Note:** This attribute has breakpoint inheritance. For details, see [GridColOptions](arkts-arkui-gridcol-comp-gridcoloptions-i.md). |

## order

```TypeScript
order(value: number | GridColColumnOption)
```

Sets the display order of the grid child component. Grid child components are sorted in ascending order based on their sequence numbers.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [GridColColumnOption](arkts-arkui-gridcol-comp-gridcolcolumnoption-i.md) | Yes | Element order number, sorted in ascending order based on the order numbers of grid child components. <br>The value is a non-negative integer. The default value is **0**. <br>Illegal value: handled as the default value. <br>**Note:** This attribute supports breakpoint inheritance. For details, see [GridColOptions](arkts-arkui-gridcol-comp-gridcoloptions-i.md). |

## span

```TypeScript
span(value: number | GridColColumnOption)
```

Sets the number of columns occupied by the grid child component. After the call is successful, the grid child component occupies a grid area of the corresponding width based on the set column count. A span of **0** indicates that the element does not participate in layout calculation, meaning it will not be rendered.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [GridColColumnOption](arkts-arkui-gridcol-comp-gridcolcolumnoption-i.md) | Yes | Number of occupied columns. If **span** is **0**, the element does not participate in layout calculation and is not rendered. <br>The value is a non-negative integer, and the default value is **1**. <br>Illegal value: processed as the default value. <br>**Note:** This attribute has breakpoint inheritance. For details, see [GridColOptions](arkts-arkui-gridcol-comp-gridcoloptions-i.md). Since API version 20, the default value inheritance rule has changed. For details, see [GridColColumnOption](arkts-arkui-gridcol-comp-gridcolcolumnoption-i.md). |
