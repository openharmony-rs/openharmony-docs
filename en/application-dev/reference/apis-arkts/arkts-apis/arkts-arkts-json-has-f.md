# has

## Modules to Import

```TypeScript
import { JSON } from '@kit.ArkTS';
```

## has

```TypeScript
function has(obj: object, property: string): boolean
```

Checks whether an ArkTS object contains a key. This API can be used for related operations after [JSON.parse](arkts-arkts-json-parse-f.md) is called to parse a JSON string. This API supports only valid JSON strings whose outermost layer is in dictionary format (in braces instead of square brackets).

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| obj | object | Yes | ArkTS object. |
| property | string | Yes | Key to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Return true if the key is in the object, otherwise return false. |
