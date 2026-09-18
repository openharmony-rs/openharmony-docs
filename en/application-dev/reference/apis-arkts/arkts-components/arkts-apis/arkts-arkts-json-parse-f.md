# parse

## Modules to Import

```TypeScript
import { JSON } from '@kit.ArkTS';
```

## parse

```TypeScript
function parse(text: string, reviver?: Transformer, options?: ParseOptions): Object | null
```

Parses a JSON string into an ArkTS object or null.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Valid JSON string. |
| reviver | [Transformer](arkts-arkts-json-transformer-t.md) | No | Conversion function. This parameter can be used to modify the value generated after parsing. The default value is undefined. |
| options | [ParseOptions](arkts-arkts-json-parseoptions-i.md) | No | Parsing options. This parameter is used to control the type of the parsing result. The default value is undefined. |

**Return value:**

| Type | Description |
| --- | --- |
| Object &#124; null | Return an Object, array, string, number, boolean, or null value corresponding to JSON text. |
