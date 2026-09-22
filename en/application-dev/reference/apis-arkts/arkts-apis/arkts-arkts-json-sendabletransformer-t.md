# SendableTransformer

```TypeScript
type SendableTransformer = (this: ISendable, key: string,
    value: ISendable | undefined | null) => ISendable | undefined | null
```

Defines the type of the conversion result function for Sendable JSON parsing.

When used as a parameter of [parseSendable](arkts-arkts-json-parsesendable-f.md), the function is called by each member of the parsed Sendable object, allowing for custom data processing or conversion during parsing.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| this | [ISendable](arkts-arkts-json-isendable-t.md) | Yes | The ISendable to which the parsed key-value pair belongs. |
| key | string | Yes | Attribute name. |
| value | [ISendable](arkts-arkts-json-isendable-t.md) &#124; undefined &#124; null | Yes | The value of the parsed key-value pair. |

**Return value:**

| Type | Description |
| --- | --- |
| [ISendable](arkts-arkts-json-isendable-t.md) &#124; undefined &#124; null | Return the modified ISendable, undefined, or null. |
