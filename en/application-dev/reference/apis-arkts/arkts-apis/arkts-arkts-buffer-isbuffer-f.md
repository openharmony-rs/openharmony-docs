# isBuffer

## Modules to Import

```TypeScript
import { buffer } from '@kit.ArkTS';
```

## isBuffer

```TypeScript
function isBuffer(obj: Object): boolean
```

Checks whether the specified object is a **Buffer** object.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| obj | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the object is a **Buffer** object; otherwise, **false** is returned. |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let result = buffer.isBuffer(buffer.alloc(10)); // 10: buffer size
console.info("result = " + result);
// Output: result = true
let result1 = buffer.isBuffer(buffer.from('foo'));
console.info("result1 = " + result1);
// Output: result1 = true
let result2 = buffer.isBuffer('a string');
console.info("result2 = " + result2);
// Output: result2 = false
let result3 = buffer.isBuffer([]);
console.info("result3 = " + result3);
// Output: result3 = false
let result4 = buffer.isBuffer(new Uint8Array(1024));
console.info("result4 = " + result4);
// Output: result4 = false
```
