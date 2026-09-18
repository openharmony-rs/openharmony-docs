# stringify

## Modules to Import

```TypeScript
import { ArkTSUtils } from '@kit.ArkTS';
```

## stringify

```TypeScript
function stringify(value: Object | null | undefined): string
```

Converts an ArkTS value to a JavaScript Object Notation (JSON) string. Extra supports Map and Set.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object &#124; null &#124; undefined | Yes | The value to stringify.<br>**Since:** 18 |

**Return value:**

| Type | Description |
| --- | --- |
| string | The JSON string representation of the value. |
