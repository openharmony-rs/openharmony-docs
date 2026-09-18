# getErrorString

## Modules to Import

```TypeScript
import { util } from '@kit.ArkTS';
```

## getErrorString

```TypeScript
function getErrorString(errno: number): string
```

Obtains detailed information about a system error code.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [errnoToString](arkts-arkts-util-errnotostring-f.md)

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
let result = util.getErrorString(errnum);
console.info("result = " + result);
// Output: result = operation not permitted
```
