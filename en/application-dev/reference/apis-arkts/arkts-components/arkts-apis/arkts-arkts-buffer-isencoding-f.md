# isEncoding

## Modules to Import

```TypeScript
import { buffer } from '@kit.ArkTS';
```

## isEncoding

```TypeScript
function isEncoding(encoding: string): boolean
```

Checks whether the encoding format is supported.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-buffer-function isEncoding(encoding: string): boolean--><!--Device-buffer-function isEncoding(encoding: string): boolean-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| encoding | string | Yes | Encoding format. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the encoding format is supported; otherwise, **false** is returned. |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

console.info(buffer.isEncoding('utf-8').toString());
// Output: true
console.info(buffer.isEncoding('hex').toString());
// Output: true
console.info(buffer.isEncoding('utf/8').toString());
// Output: false
console.info(buffer.isEncoding('').toString());
// Output: false
```
