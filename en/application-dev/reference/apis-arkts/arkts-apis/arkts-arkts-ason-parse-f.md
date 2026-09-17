# parse

## Modules to Import

```TypeScript
import { ArkTSUtils } from '@kit.ArkTS';
```

## parse

```TypeScript
function parse(text: string, reviver?: Transformer, options?: ParseOptions): ISendable | null
```

Converts a JavaScript Object Notation (JSON) string into an ArkTS Value.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | A valid JSON string. |
| reviver | [Transformer](arkts-arkts-ason-transformer-t.md) | No | A function that transforms the results. |
| options | [ParseOptions](arkts-arkts-ason-parseoptions-i.md) | No | The config of parse. |

**Return value:**

| Type | Description |
| --- | --- |
| [ISendable](arkts-arkts-ason-isendable-t.md) &#124; null | Return an ArkTS Value. |
