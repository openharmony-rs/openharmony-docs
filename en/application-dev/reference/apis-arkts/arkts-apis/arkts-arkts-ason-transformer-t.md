# Transformer

```TypeScript
type Transformer = (this: ISendable, key: string,
      value: ISendable | undefined | null) => ISendable | undefined | null
```

The type of conversion result function.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| this | [ISendable](arkts-arkts-ason-isendable-t.md) | Yes | The ISendable to which the parsed key value pair belongs. |
| key | string | Yes | Attribute name. |
| value | [ISendable](arkts-arkts-ason-isendable-t.md) &#124; undefined &#124; null | Yes | The value of the parsed key value pair. |

**Return value:**

| Type | Description |
| --- | --- |
| [ISendable](arkts-arkts-ason-isendable-t.md) &#124; undefined &#124; null | Return the modified ISendable or undefined or null. |
