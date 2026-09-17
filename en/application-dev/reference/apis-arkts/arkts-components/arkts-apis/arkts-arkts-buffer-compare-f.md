# compare

## Modules to Import

```TypeScript
import { buffer } from '@kit.ArkTS';
```

## compare

```TypeScript
function compare(buf1: Buffer | Uint8Array, buf2: Buffer | Uint8Array): -1 | 0 | 1
```

Compares two **Buffer** objects. This API is used for sorting **Buffer** objects.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| buf1 | Buffer &#124; Uint8Array | Yes | **Buffer** object to compare. |
| buf2 | Buffer &#124; Uint8Array | Yes | **Buffer** object to compare. |

**Return value:**

| Type | Description |
| --- | --- |
| -1 &#124; 0 &#124; 1 | Returns **0** if **buf1** is the same as **buf2**.<br>Returns **1** if **buf1** comes after **buf2** when sorted. <br>Returns **-1** if **buf1** comes before **buf2** when sorted. |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.from('1234');
let buf2 = buffer.from('0123');
let res = buffer.compare(buf1, buf2);

console.info(Number(res).toString());
// Output: 1
```
