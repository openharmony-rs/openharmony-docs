# errnoToString

## Modules to Import

```TypeScript
import { util } from '@kit.ArkTS';
```

## errnoToString

```TypeScript
function errnoToString(errno: number): string
```

Obtains detailed information about a system error code.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| errno | number | Yes | Error code generated. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Detailed information about the error code. |

**Examples**

```TypeScript
let errnum = -1; // -1 is a system error code.
let result = util.errnoToString(errnum);
console.info("result = " + result);
// Output: result = operation not permitted
```
