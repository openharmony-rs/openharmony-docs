# from

## Modules to Import

```TypeScript
import { fastbuffer } from '@kit.ArkTS';
```

## from

```TypeScript
function from(array: number[]): FastBuffer
```

Allocates a new FastBuffer using an array of bytes in the range 0 – 255. Array entries outside that range will be truncated to fit into it.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| array | number[] | Yes | An array of bytes (integers in 0-255 range) |

**Return value:**

| Type | Description |
| --- | --- |
| [FastBuffer](arkts-arkts-fastbuffer-fastbuffer-c.md) | Return a new allocated FastBuffer |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0x62, 0x75, 0x66, 0x66, 0x65, 0x72]);
console.info(buf.toString('hex'));
// Output: 627566666572
```


<a id="from-1"></a>

## from

```TypeScript
function from(arrayBuffer: ArrayBuffer | SharedArrayBuffer, byteOffset?: number, length?: number): FastBuffer
```

This creates a view of the ArrayBuffer without copying the underlying memory.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| arrayBuffer | ArrayBuffer &#124; SharedArrayBuffer | Yes | The ArrayBuffer or SharedArrayBuffer to create a view from |
| byteOffset | number | No | byteOffset [byteOffset = 0] Index of first byte to expose |
| length | number | No | length [length = arrayBuffer.byteLength - byteOffset] Number of bytes to expose |

**Return value:**

| Type | Description |
| --- | --- |
| [FastBuffer](arkts-arkts-fastbuffer-fastbuffer-c.md) | Return a view of the ArrayBuffer |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | Range error. Possible causes: The value of the parameter is not within the specified range. |
| [10200068](../errorcode-utils.md#10200068-using-a-released-or-detached-arraybuffer) | The underlying ArrayBuffer is null or detach. |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let ab = new ArrayBuffer(10);
let buf = fastbuffer.from(ab, 0, 2);
console.info(buf.length.toString());
// Output: 2
```


<a id="from-2"></a>

## from

```TypeScript
function from(buffer: FastBuffer | Uint8Array): FastBuffer
```

Copies the passed buffer data onto a new FastBuffer instance.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| buffer | [FastBuffer](arkts-arkts-fastbuffer-fastbuffer-c.md) &#124; Uint8Array | Yes | The buffer to copy data from |

**Return value:**

| Type | Description |
| --- | --- |
| [FastBuffer](arkts-arkts-fastbuffer-fastbuffer-c.md) | Return a new allocated FastBuffer |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200068](../errorcode-utils.md#10200068-using-a-released-or-detached-arraybuffer) | The underlying ArrayBuffer is null or detach. |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

// Create a FastBuffer object of the FastBuffer type.
let buf1 = fastbuffer.from('buffer');
let buf2 = fastbuffer.from(buf1);
console.info(buf2.toString());
// Output: buffer

// Create a FastBuffer object of the Uint8Array type to ensure memory sharing between objects.
let uint8Array = new Uint8Array(10);
let buf3 = fastbuffer.from(uint8Array);
buf3.fill(1)
console.info("uint8Array:", uint8Array)
// Output: 1,1,1,1,1,1,1,1,1,1
```


<a id="from-3"></a>

## from

```TypeScript
function from(value: string, encoding?: BufferEncoding): FastBuffer
```

Creates a new FastBuffer containing string. The encoding parameter identifies the character encoding to be used when converting string into bytes.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes | The string to encode into a FastBuffer |
| encoding | BufferEncoding | No | encoding [encoding='utf8'] The encoding of string |

**Return value:**

| Type | Description |
| --- | --- |
| [FastBuffer](arkts-arkts-fastbuffer-fastbuffer-c.md) | Return a new FastBuffer containing string |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf1 = fastbuffer.from('this is a test');
let buf2 = fastbuffer.from('7468697320697320612074c3a97374', 'hex');

console.info(buf1.toString());
// Output: this is a test
console.info(buf2.toString());
// Output: this is a tést
```
