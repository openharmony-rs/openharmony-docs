# compare

## Modules to Import

```TypeScript
import { fastbuffer } from '@kit.ArkTS';
```

## compare

```TypeScript
function compare(buf1: FastBuffer | Uint8Array, buf2: FastBuffer | Uint8Array): -1 | 0 | 1
```

Compares buf1 to buf2

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| buf1 | [FastBuffer](arkts-arkts-fastbuffer-fastbuffer-c.md) &#124; Uint8Array | Yes | First buffer for comparison |
| buf2 | [FastBuffer](arkts-arkts-fastbuffer-fastbuffer-c.md) &#124; Uint8Array | Yes | Second buffer for comparison |

**Return value:**

| Type | Description |
| --- | --- |
| -1 &#124; 0 &#124; 1 | 0 is returned if target is the same as buf 1 is returned if target should come before buf when sorted. -1 is returned if target should come after buf when sorted. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200068](../errorcode-utils.md#10200068-using-a-released-or-detached-arraybuffer) | The underlying ArrayBuffer is null or detach. |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf1 = fastbuffer.from('1234');
let buf2 = fastbuffer.from('0123');
let res = fastbuffer.compare(buf1, buf2);

console.info(Number(res).toString());
// Output: 1
```
