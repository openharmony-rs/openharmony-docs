# isBuffer

## Modules to Import

```TypeScript
import { fastbuffer } from '@kit.ArkTS';
```

## isBuffer

```TypeScript
function isBuffer(obj: Object): boolean
```

Returns true if obj is a FastBuffer, false otherwise

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| obj | Object | Yes | The object to check if it's a FastBuffer |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | true or false |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let result = fastbuffer.isBuffer(fastbuffer.alloc(10)); // 10: fastbuffer size
console.info("result = " + result);
// Output: result = true
let result1 = fastbuffer.isBuffer(fastbuffer.from('foo'));
console.info("result1 = " + result1);
// Output: result1 = true
let result2 = fastbuffer.isBuffer('a string');
console.info("result2 = " + result2);
// Output: result2 = false
let result3 = fastbuffer.isBuffer([]);
console.info("result3 = " + result3);
// Output: result3 = false
let result4 = fastbuffer.isBuffer(new Uint8Array(1024));
console.info("result4 = " + result4);
// Output: result4 = false
```
