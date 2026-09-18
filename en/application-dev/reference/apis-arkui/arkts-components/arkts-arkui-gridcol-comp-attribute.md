# GridCol properties/events

In addition to the [universal attributes](arkts-arkui-commonmethod-c.md), the following attributes are supported.

The [universal events](arkts-arkui-commonmethod-c.md) are supported.

**Inheritance/Implementation:** GridColAttribute extends CommonMethod<GridColAttribute>

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## gridColOffset

```TypeScript
gridColOffset(value: number | GridColColumnOption)
```

Sets the number of offset columns relative to the original position of the component.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [GridColColumnOption](arkts-arkui-gridcolcolumnoption-i.md) | Yes | Number of offset columns relative to the previous child component of the grid<br>The value must be a non-negative integer. Default value: **0**.<br>Invalid values are treated as the default value. |

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
| value | number &#124; [GridColColumnOption](arkts-arkui-gridcolcolumnoption-i.md) | Yes | Sequence number of the component. Child components of the grid are sorted in ascending order based on their sequence numbers.<br>The value must be a non-negative integer. Default value: **0**.<br>Invalid values are treated as the default value. |

## span

```TypeScript
span(value: number | GridColColumnOption)
```

Sets the number of columns occupied by the component. If it is set to **0**, the element is not involved in layout calculation, that is, the element is not rendered.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [GridColColumnOption](arkts-arkui-gridcolcolumnoption-i.md) | Yes | Number of occupied columns.<br>The value must be a non-negative integer. Default value: **1**.<br>Invalid values are treated as the default value. |
