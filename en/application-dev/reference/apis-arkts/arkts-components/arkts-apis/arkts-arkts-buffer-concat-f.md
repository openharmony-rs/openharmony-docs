# concat

## Modules to Import

```TypeScript
import { buffer } from '@kit.ArkTS';
```

## concat

```TypeScript
function concat(list: Buffer[] | Uint8Array[], totalLength?: number): Buffer
```

Concatenates an array of **Buffer** objects of the specified length into a new object.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| list | Buffer[] &#124; Uint8Array[] | Yes | Array of objects to concatenate. |
| totalLength | number | No | Total length of bytes to be copied. The default value is **0**. |

**Return value:**

| Type | Description |
| --- | --- |
| Buffer | **Buffer** object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "length" is out of range. It must be &gt;= 0 and &lt;= uint32 max. Received value is: [length] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.from("1234");
let buf2 = buffer.from("abcd");
let buf = buffer.concat([buf1, buf2]);
console.info(buf.toString('hex'));
// Output: 3132333461626364
```
