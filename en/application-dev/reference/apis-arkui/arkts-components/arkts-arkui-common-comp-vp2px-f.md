# vp2px

## vp2px

```TypeScript
declare function vp2px(value: number): number
```

Converts a value in vp units to a value in px. By default, the virtual pixel ratio of the screen where the current UI instance is located is used for conversion. If no UI instance is available, the virtual pixel ratio of the default screen is used instead.

**Since:** 11

**Deprecated since:** 18

**Substitutes:** vp2px

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Value range of value: (-∞, +∞). |

**Return value:**

| Type | Description |
| --- | --- |
| number | Value range of the return value: (-∞, +∞). |
