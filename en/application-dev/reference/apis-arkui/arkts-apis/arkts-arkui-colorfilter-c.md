# ColorFilter

Defines a color filter with a 4 x 5 matrix.

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(value: number[])
```

Constructor of ColorFilter, which creates a color filter with a 4\*5 matrix.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number[] | Yes | Value of the 4\*5 color matrix, [m\*n] matrix value at row m and column n. The matrix is row-major. |
