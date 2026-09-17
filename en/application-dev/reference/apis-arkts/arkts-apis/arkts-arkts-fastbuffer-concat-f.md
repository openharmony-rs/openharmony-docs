# concat

## Modules to Import

```TypeScript
import { fastbuffer } from '@kit.ArkTS';
```

## concat

```TypeScript
function concat(list: FastBuffer[] | Uint8Array[], totalLength?: number): FastBuffer
```

Returns a new `FastBuffer` which is the result of concatenating all the `FastBuffer`instances in the `list` together.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| list | [FastBuffer](arkts-arkts-fastbuffer-fastbuffer-c.md)[] &#124; Uint8Array[] | Yes | Array of FastBuffer or Uint8Array instances to concatenate |
| totalLength | number | No | Total length of the FastBuffer instances when concatenated |

**Return value:**

| Type | Description |
| --- | --- |
| [FastBuffer](arkts-arkts-fastbuffer-fastbuffer-c.md) | Return a new allocated FastBuffer |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | Range error. Possible causes: The value of the parameter is not within the specified range. |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf1 = fastbuffer.from("1234");
let buf2 = fastbuffer.from("abcd");
let buf = fastbuffer.concat([buf1, buf2]);
console.info(buf.toString('hex'));
// Output: 3132333461626364
```
