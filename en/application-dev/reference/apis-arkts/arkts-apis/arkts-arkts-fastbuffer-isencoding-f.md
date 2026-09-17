# isEncoding

## Modules to Import

```TypeScript
import { fastbuffer } from '@kit.ArkTS';
```

## isEncoding

```TypeScript
function isEncoding(encoding: string): boolean
```

Returns true if encoding is the name of a supported character encoding, or false otherwise.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| encoding | string | Yes | The character encoding name to validate |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | true or false |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

console.info(fastbuffer.isEncoding('utf-8').toString());
// Output: true
console.info(fastbuffer.isEncoding('hex').toString());
// Output: true
console.info(fastbuffer.isEncoding('utf/8').toString());
// Output: false
console.info(fastbuffer.isEncoding('').toString());
// Output: false
```
