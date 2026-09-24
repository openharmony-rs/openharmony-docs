# FastBuffer

```TypeScript
class FastBuffer
```

The FastBuffer object is a method of handling buffers dedicated to binary data.

**Since:** 20

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { fastbuffer } from '@kit.ArkTS';
```

## compare

```TypeScript
compare(target: FastBuffer | Uint8Array, targetStart?: number, targetEnd?: number, sourceStart?: number, sourceEnd?: number): -1 | 0 | 1
```

Compares buf with target and returns a number indicating whether buf comes before, after, or is the same as target in sort order. Comparison is based on the actual sequence of bytes in each FastBuffer.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [FastBuffer](arkts-arkts-fastbuffer-fastbuffer-c.md) &#124; Uint8Array | Yes | The buffer to compare with this buffer |
| targetStart | number | No | targetStart [targetStart = 0] The offset within target at which to begin comparison |
| targetEnd | number | No | targetEnd [targetEnd = target.length] The offset within target at which to end comparison (not inclusive) |
| sourceStart | number | No | sourceStart [sourceStart = 0] The offset within buf at which to begin comparison |
| sourceEnd | number | No | sourceEnd [sourceEnd = buf.length] The offset within buf at which to end comparison (not inclusive) |

**Return value:**

| Type | Description |
| --- | --- |
| -1 &#124; 0 &#124; 1 | 0 is returned if target is the same as buf 1 is returned if target should come before buf when sorted. -1 is returned if target should come after buf when sorted. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | Range error. Possible causes: The value of the parameter is not within the specified range. |
| [10200068](../errorcode-utils.md#10200068-using-a-released-or-detached-arraybuffer) | The underlying ArrayBuffer is null or detach. |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf1 = fastbuffer.from([1, 2, 3, 4, 5, 6, 7, 8, 9]);
let buf2 = fastbuffer.from([5, 6, 7, 8, 9, 1, 2, 3, 4]);

console.info(buf1.compare(buf2, 5, 9, 0, 4).toString());
// Output: 0
console.info(buf1.compare(buf2, 0, 6, 4).toString());
// Output: -1
console.info(buf1.compare(buf2, 5, 6, 5).toString());
// Output: 1
```

## copy

```TypeScript
copy(target: FastBuffer | Uint8Array, targetStart?: number, sourceStart?: number, sourceEnd?: number): number
```

Copies data from a region of buf to a region in target, even if the target memory region overlaps with buf. If sourceEnd is greater than the length of the target, the length of the target shall prevail, and the extra part will not be overwritten.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [FastBuffer](arkts-arkts-fastbuffer-fastbuffer-c.md) &#124; Uint8Array | Yes | The buffer to copy data into |
| targetStart | number | No | targetStart [targetStart = 0] The offset within target at which to begin writing |
| sourceStart | number | No | sourceStart [sourceStart = 0] The offset within buf from which to begin copying |
| sourceEnd | number | No | sourceEnd [sourceEnd = buf.length] The offset within buf at which to stop copying (not inclusive) |

**Return value:**

| Type | Description |
| --- | --- |
| number | The number of bytes copied |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | Range error. Possible causes: The value of the parameter is not within the specified range. |
| [10200068](../errorcode-utils.md#10200068-using-a-released-or-detached-arraybuffer) | The underlying ArrayBuffer is null or detach. |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf1 = fastbuffer.allocUninitializedFromPool(26);
let buf2 = fastbuffer.allocUninitializedFromPool(26).fill('!');

for (let i = 0; i < 26; i++) {
  buf1.writeInt8(i + 97, i);
}

buf1.copy(buf2, 8, 16, 20);
console.info(buf2.toString('ascii', 0, 25));
// Output: !!!!!!!!qrst!!!!!!!!!!!!!
```

## entries

```TypeScript
entries(): IterableIterator<[
            number,
            number
        ]>
```

Creates and returns an iterator of [index, byte] pairs from the contents of buf.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;[number, number]&gt; |  |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from('buffer');
let pair = buf.entries();
let next: IteratorResult<Object[]> = pair.next();
while (!next.done) {
  console.info("fastbuffer: " + next.value);
  /*
  Output: buffer: 0,98
           fastbuffer: 1,117
           fastbuffer: 2,102
           fastbuffer: 3,102
           fastbuffer: 4,101
           fastbuffer: 5,114
  */
  next = pair.next();
}
```

## equals

```TypeScript
equals(otherBuffer: Uint8Array | FastBuffer): boolean
```

Returns true if both buf and otherBuffer have exactly the same bytes, false otherwise

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| otherBuffer | Uint8Array &#124; [FastBuffer](arkts-arkts-fastbuffer-fastbuffer-c.md) | Yes | The buffer to compare with this buffer for equality |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | true or false |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200068](../errorcode-utils.md#10200068-using-a-released-or-detached-arraybuffer) | The underlying ArrayBuffer is null or detach. |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf1 = fastbuffer.from('ABC');
let buf2 = fastbuffer.from('414243', 'hex');
let buf3 = fastbuffer.from('ABCD');

console.info(buf1.equals(buf2).toString());
// Output: true
console.info(buf1.equals(buf3).toString());
// Output: false
```

## fill

```TypeScript
fill(value: string | FastBuffer | Uint8Array | number, offset?: number, end?: number, encoding?: BufferEncoding): FastBuffer
```

Fills buf with the specified value. If the offset and end are not given, the entire buf will be filled.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string &#124; [FastBuffer](arkts-arkts-fastbuffer-fastbuffer-c.md) &#124; Uint8Array &#124; number | Yes | The value to fill into the buffer |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to fill buf |
| end | number | No | end [end = buf.length] Where to stop filling buf (not inclusive) |
| encoding | BufferEncoding | No | encoding [encoding='utf8'] The encoding for value if value is a string |

**Return value:**

| Type | Description |
| --- | --- |
| [FastBuffer](arkts-arkts-fastbuffer-fastbuffer-c.md) | A reference to buf |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | Range error. Possible causes: The value of the parameter is not within the specified range. |
| [10200068](../errorcode-utils.md#10200068-using-a-released-or-detached-arraybuffer) | The underlying ArrayBuffer is null or detach. |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let b = fastbuffer.allocUninitializedFromPool(50).fill('h');
console.info(b.toString());
// Output: hhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhh
```

## includes

```TypeScript
includes(value: string | number | FastBuffer | Uint8Array, byteOffset?: number, encoding?: BufferEncoding): boolean
```

Returns true if value was found in buf, false otherwise

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string &#124; number &#124; [FastBuffer](arkts-arkts-fastbuffer-fastbuffer-c.md) &#124; Uint8Array | Yes | The value to search for in the buffer |
| byteOffset | number | No | byteOffset [byteOffset = 0] Where to begin searching in buf. If negative, then offset is calculated from the end of buf |
| encoding | BufferEncoding | No | encoding [encoding='utf8'] If value is a string, this is its encoding |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | true or false |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from('this is a buffer');
console.info(buf.includes('this').toString());
// Output: true
console.info(buf.includes('be').toString());
// Output: false
```

## indexOf

```TypeScript
indexOf(value: string | number | FastBuffer | Uint8Array, byteOffset?: number, encoding?: BufferEncoding): number
```

The index of the first occurrence of value in buf

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string &#124; number &#124; [FastBuffer](arkts-arkts-fastbuffer-fastbuffer-c.md) &#124; Uint8Array | Yes | The value to find the index for in the buffer |
| byteOffset | number | No | byteOffset [byteOffset = 0] Where to begin searching in buf |
| encoding | BufferEncoding | No | encoding [encoding='utf8'] If value is a string, this is the encoding used to determine the binary representation of the string that will be searched for in buf |

**Return value:**

| Type | Description |
| --- | --- |
| number | The index of the first occurrence of value in buf, or -1 if buf does not contain value |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from('this is a buffer');
console.info(buf.indexOf('this').toString());
// Output: 0
console.info(buf.indexOf('is').toString());
// Output: 2
```

## keys

```TypeScript
keys(): IterableIterator<number>
```

Creates and returns an iterator of buf keys (indices).

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;number&gt; |  |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from('buffer');
let keys = buf.keys();
for (const key of keys) {
  console.info(key.toString());
}
/*
Output: 0
        1
        2
        3
        4
        5
*/
```

## lastIndexOf

```TypeScript
lastIndexOf(value: string | number | FastBuffer | Uint8Array, byteOffset?: number, encoding?: BufferEncoding): number
```

The index of the last occurrence of value in buf

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string &#124; number &#124; [FastBuffer](arkts-arkts-fastbuffer-fastbuffer-c.md) &#124; Uint8Array | Yes | The value to find the last index for in the buffer |
| byteOffset | number | No | byteOffset [byteOffset = 0] Where to begin searching in buf |
| encoding | BufferEncoding | No | encoding [encoding='utf8'] If value is a string, this is the encoding used to determine the binary representation of the string that will be searched for in buf |

**Return value:**

| Type | Description |
| --- | --- |
| number | The index of the last occurrence of value in buf, or -1 if buf does not contain value |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from('this buffer is a buffer');
console.info(buf.lastIndexOf('this').toString());
// Output: 0
console.info(buf.lastIndexOf('buffer').toString());
// Output: 17
```

## readBigInt64BE

```TypeScript
readBigInt64BE(offset?: number): bigint
```

Reads a signed, big-endian 64-bit integer from buf at the specified offset

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to read. Must satisfy: 0 &lt;= offset &lt;= buf.length - 8 |

**Return value:**

| Type | Description |
| --- | --- |
| bigint | Return a signed, big-endian 64-bit integer |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 8. Received value is: [offset] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0x63, 0x64, 0x65, 0x66, 0x67, 0x68, 0x69, 0x70,
  0x71, 0x72, 0x73, 0x74, 0x75, 0x76, 0x77, 0x78]);
console.info(buf.readBigInt64BE(0).toString());
// Output: 7161960797921896816
```

## readBigInt64LE

```TypeScript
readBigInt64LE(offset?: number): bigint
```

Reads a signed, little-endian 64-bit integer from buf at the specified offset

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to read. Must satisfy: 0 &lt;= offset &lt;= buf.length - 8 |

**Return value:**

| Type | Description |
| --- | --- |
| bigint | Return a signed, little-endian 64-bit integer |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 8. Received value is: [offset] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0x63, 0x64, 0x65, 0x66, 0x67, 0x68, 0x69, 0x70,
  0x71, 0x72, 0x73, 0x74, 0x75, 0x76, 0x77, 0x78]);
console.info(buf.readBigInt64LE(0).toString());
// Output: 8100120198111388771
```

## readBigUInt64BE

```TypeScript
readBigUInt64BE(offset?: number): bigint
```

Reads a unsigned, big-endian 64-bit integer from buf at the specified offset

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to read. Must satisfy: 0 &lt;= offset &lt;= buf.length - 8 |

**Return value:**

| Type | Description |
| --- | --- |
| bigint | Return a unsigned, big-endian 64-bit integer |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 8. Received value is: [offset] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0x63, 0x64, 0x65, 0x66, 0x67, 0x68, 0x69, 0x70,
  0x71, 0x72, 0x73, 0x74, 0x75, 0x76, 0x77, 0x78]);
console.info(buf.readBigUInt64BE(0).toString());
// Output: 7161960797921896816
```

## readBigUInt64LE

```TypeScript
readBigUInt64LE(offset?: number): bigint
```

Reads a unsigned, little-endian 64-bit integer from buf at the specified offset

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to read. Must satisfy: 0 &lt;= offset &lt;= buf.length - 8 |

**Return value:**

| Type | Description |
| --- | --- |
| bigint | Return a unsigned, little-endian 64-bit integer |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 8. Received value is: [offset] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0x63, 0x64, 0x65, 0x66, 0x67, 0x68, 0x69, 0x70,
  0x71, 0x72, 0x73, 0x74, 0x75, 0x76, 0x77, 0x78]);
console.info(buf.readBigUInt64LE(0).toString());
// Output: 8100120198111388771
```

## readDoubleBE

```TypeScript
readDoubleBE(offset?: number): number
```

Reads a 64-bit, big-endian double from buf at the specified offset

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to read. Must satisfy: 0 &lt;= offset &lt;= buf.length - 8 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Return a 64-bit, big-endian double |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 8. Received value is: [offset] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([1, 2, 3, 4, 5, 6, 7, 8]);
console.info(buf.readDoubleBE(0).toString());
// Output: 8.20788039913184e-304
```

## readDoubleLE

```TypeScript
readDoubleLE(offset?: number): number
```

Reads a 64-bit, little-endian double from buf at the specified offset

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to read. Must satisfy: 0 &lt;= offset &lt;= buf.length - 8 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Return a 64-bit, little-endian double |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 8. Received value is: [offset] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([1, 2, 3, 4, 5, 6, 7, 8]);
console.info(buf.readDoubleLE(0).toString());
// Output: 5.447603722011605e-270
```

## readFloatBE

```TypeScript
readFloatBE(offset?: number): number
```

Reads a 32-bit, big-endian float from buf at the specified offset

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to read. Must satisfy: 0 &lt;= offset &lt;= buf.length - 4 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Return a 32-bit, big-endian float |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 4. Received value is: [offset] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([1, 2, 3, 4, 5, 6, 7, 8]);
console.info(buf.readFloatBE(0).toString());
// Output: 2.387939260590663e-38
```

## readFloatLE

```TypeScript
readFloatLE(offset?: number): number
```

Reads a 32-bit, little-endian float from buf at the specified offset

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to read. Must satisfy: 0 &lt;= offset &lt;= buf.length - 4 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Return a 32-bit, little-endian float |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 4. Received value is: [offset] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([1, 2, 3, 4, 5, 6, 7, 8]);
console.info(buf.readFloatLE(0).toString());
// Output: 1.539989614439558e-36
```

## readInt16BE

```TypeScript
readInt16BE(offset?: number): number
```

Reads a signed, big-endian 16-bit integer from buf at the specified offset

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to read. Must satisfy: 0 &lt;= offset &lt;= buf.length - 2 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Return a signed, big-endian 16-bit integer |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 2. Received value is: [offset] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0, 5]);
console.info(buf.readInt16BE(0).toString());
// Output: 5
```

## readInt16LE

```TypeScript
readInt16LE(offset?: number): number
```

Reads a signed, little-endian 16-bit integer from buf at the specified offset

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to read. Must satisfy: 0 &lt;= offset &lt;= buf.length - 2 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Return a signed, little-endian 16-bit integer |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 2. Received value is: [offset] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0, 5]);
console.info(buf.readInt16LE(0).toString());
// Output: 1280
```

## readInt32BE

```TypeScript
readInt32BE(offset?: number): number
```

Reads a signed, big-endian 32-bit integer from buf at the specified offset

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to read. Must satisfy: 0 &lt;= offset &lt;= buf.length - 4 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Return a signed, big-endian 32-bit integer |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 4. Received value is: [offset] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0, 0, 0, 5]);
console.info(buf.readInt32BE(0).toString());
// Output: 5
```

## readInt32LE

```TypeScript
readInt32LE(offset?: number): number
```

Reads a signed, little-endian 32-bit integer from buf at the specified offset

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to read. Must satisfy: 0 &lt;= offset &lt;= buf.length - 4 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Return a signed, little-endian 32-bit integer |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 4. Received value is: [offset] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0, 0, 0, 5]);
console.info(buf.readInt32LE(0).toString());
// Output: 83886080
```

## readInt8

```TypeScript
readInt8(offset?: number): number
```

Reads a signed 8-bit integer from buf at the specified offset

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to read. Must satisfy: 0 &lt;= offset &lt;= buf.length - 1 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Return a signed 8-bit integer |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 1. Received value is: [offset] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([-1, 5]);
console.info(buf.readInt8(0).toString());
// Output: -1
console.info(buf.readInt8(1).toString());
// Output: 5
```

## readIntBE

```TypeScript
readIntBE(offset: number, byteLength: number): number
```

Reads byteLength number of bytes from buf at the specified offset and interprets the result as a big-endian, two's complement signed value supporting up to 48 bits of accuracy

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | Yes | Number of bytes to skip before starting to read. Must satisfy: 0 &lt;= offset &lt;= buf.length - byteLength |
| byteLength | number | Yes | Number of bytes to read. Must satisfy 0 &lt; byteLength &lt;= 6 |

**Return value:**

| Type | Description |
| --- | --- |
| number |  |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from("ab");
let num = buf.readIntBE(0, 1);
console.info(num.toString());
// Output: 97
```

## readIntLE

```TypeScript
readIntLE(offset: number, byteLength: number): number
```

Reads byteLength number of bytes from buf at the specified offset and interprets the result as a little-endian, two's complement signed value supporting up to 48 bits of accuracy.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | Yes | Number of bytes to skip before starting to read. Must satisfy: 0 &lt;= offset &lt;= buf.length - byteLength |
| byteLength | number | Yes | Number of bytes to read. Must satisfy 0 &lt; byteLength &lt;= 6 |

**Return value:**

| Type | Description |
| --- | --- |
| number |  |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0x12, 0x34, 0x56, 0x78, 0x90, 0xab]);
console.info(buf.readIntLE(0, 6).toString(16));
// Output: -546f87a9cbee
```

## readUInt16BE

```TypeScript
readUInt16BE(offset?: number): number
```

Reads an unsigned, big-endian 16-bit integer from buf at the specified offset

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to read. Must satisfy 0 &lt;= offset &lt;= buf.length - 2 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Reads an unsigned, big-endian 16-bit integer |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 2. Received value is: [offset] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0x12, 0x34, 0x56]);
console.info(buf.readUInt16BE(0).toString(16));
// Output: 1234
console.info(buf.readUInt16BE(1).toString(16));
// Output: 3456
```

## readUInt16LE

```TypeScript
readUInt16LE(offset?: number): number
```

Reads an unsigned, little-endian 16-bit integer from buf at the specified offset

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to read. Must satisfy 0 &lt;= offset &lt;= buf.length - 2 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Reads an unsigned, little-endian 16-bit integer |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 2. Received value is: [offset] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0x12, 0x34, 0x56]);
console.info(buf.readUInt16LE(0).toString(16));
// Output: 3412
console.info(buf.readUInt16LE(1).toString(16));
// Output: 5634
```

## readUInt32BE

```TypeScript
readUInt32BE(offset?: number): number
```

Reads an unsigned, big-endian 32-bit integer from buf at the specified offset

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to read. Must satisfy 0 &lt;= offset &lt;= buf.length - 4 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Reads an unsigned, big-endian 32-bit integer |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 4. Received value is: [offset] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0x12, 0x34, 0x56, 0x78]);
console.info(buf.readUInt32BE(0).toString(16));
// Output: 12345678
```

## readUInt32LE

```TypeScript
readUInt32LE(offset?: number): number
```

Reads an unsigned, little-endian 32-bit integer from buf at the specified offset

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to read. Must satisfy 0 &lt;= offset &lt;= buf.length - 4 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Reads an unsigned, little-endian 32-bit integer |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 4. Received value is: [offset] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0x12, 0x34, 0x56, 0x78]);
console.info(buf.readUInt32LE(0).toString(16));
// Output: 78563412
```

## readUInt8

```TypeScript
readUInt8(offset?: number): number
```

Reads an unsigned 8-bit integer from buf at the specified offset

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to read. Must satisfy 0 &lt;= offset &lt;= buf.length - 1 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Reads an unsigned 8-bit integer |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 1. Received value is: [offset] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([1, -2]);
console.info(buf.readUInt8(0).toString());
// Output: 1
console.info(buf.readUInt8(1).toString());
// Output: 254
```

## readUIntBE

```TypeScript
readUIntBE(offset: number, byteLength: number): number
```

Reads byteLength number of bytes from buf at the specified offset and interprets the result as an unsigned big-endian integer supporting up to 48 bits of accuracy.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | Yes | Number of bytes to skip before starting to read. Must satisfy: 0 &lt;= offset &lt;= buf.length - byteLength |
| byteLength | number | Yes | Number of bytes to read. Must satisfy 0 &lt; byteLength &lt;= 6 |

**Return value:**

| Type | Description |
| --- | --- |
| number |  |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0x12, 0x34, 0x56, 0x78, 0x90, 0xab]);
console.info(buf.readUIntBE(0, 6).toString(16));
// Output: 1234567890ab
```

## readUIntLE

```TypeScript
readUIntLE(offset: number, byteLength: number): number
```

Reads byteLength number of bytes from buf at the specified offset and interprets the result as an unsigned, little-endian integer supporting up to 48 bits of accuracy.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | Yes | Number of bytes to skip before starting to read. Must satisfy: 0 &lt;= offset &lt;= buf.length - byteLength |
| byteLength | number | Yes | Number of bytes to read. Must satisfy 0 &lt; byteLength &lt;= 6 |

**Return value:**

| Type | Description |
| --- | --- |
| number |  |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0x12, 0x34, 0x56, 0x78, 0x90, 0xab]);
console.info(buf.readUIntLE(0, 6).toString(16));
// Output: ab9078563412
```

## subarray

```TypeScript
subarray(start?: number, end?: number): FastBuffer
```

Returns a new FastBuffer that references the same memory as the original, but offset and cropped by the start and end indices.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | number | No | start [start = 0] Where the new FastBuffer will start |
| end | number | No | end [end = buf.length] Where the new FastBuffer will end (not inclusive) |

**Return value:**

| Type | Description |
| --- | --- |
| [FastBuffer](arkts-arkts-fastbuffer-fastbuffer-c.md) | Returns a new FastBuffer that references the same memory as the original |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf1 = fastbuffer.allocUninitializedFromPool(26);

for (let i = 0; i < 26; i++) {
  buf1.writeInt8(i + 97, i);
}
const buf2 = buf1.subarray(0, 3);
console.info(buf2.toString('ascii', 0, buf2.length));
// Output: abc
```

## swap16

```TypeScript
swap16(): FastBuffer
```

Interprets buf as an array of unsigned 16-bit integers and swaps the byte order in-place.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [FastBuffer](arkts-arkts-fastbuffer-fastbuffer-c.md) | A reference to buf |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200009](../errorcode-utils.md#10200009-buffer-size-error) | The fastbuffer size must be a multiple of 16-bits |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf1 = fastbuffer.from([0x1, 0x2, 0x3, 0x4, 0x5, 0x6, 0x7, 0x8]);
console.info(buf1.toString('hex'));
// Output: 0102030405060708
buf1.swap16();
console.info(buf1.toString('hex'));
// Output: 0201040306050807
```

## swap32

```TypeScript
swap32(): FastBuffer
```

Interprets buf as an array of unsigned 32-bit integers and swaps the byte order in-place.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [FastBuffer](arkts-arkts-fastbuffer-fastbuffer-c.md) | A reference to buf |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200009](../errorcode-utils.md#10200009-buffer-size-error) | The fastbuffer size must be a multiple of 32-bits |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf1 = fastbuffer.from([0x1, 0x2, 0x3, 0x4, 0x5, 0x6, 0x7, 0x8]);
console.info(buf1.toString('hex'));
// Output: 0102030405060708
buf1.swap32();
console.info(buf1.toString('hex'));
// Output: 0403020108070605
```

## swap64

```TypeScript
swap64(): FastBuffer
```

Interprets buf as an array of unsigned 64-bit integers and swaps the byte order in-place.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [FastBuffer](arkts-arkts-fastbuffer-fastbuffer-c.md) | A reference to buf |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200009](../errorcode-utils.md#10200009-buffer-size-error) | The fastbuffer size must be a multiple of 64-bits |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf1 = fastbuffer.from([0x1, 0x2, 0x3, 0x4, 0x5, 0x6, 0x7, 0x8]);
console.info(buf1.toString('hex'));
// Output: 0102030405060708
buf1.swap64();
console.info(buf1.toString('hex'));
// Output: 0807060504030201
```

## toJSON

```TypeScript
toJSON(): Object
```

Returns a JSON representation of buf

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| Object | Returns a JSON |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf1 = fastbuffer.from([0x1, 0x2, 0x3, 0x4, 0x5]);
let obj = buf1.toJSON();
console.info(JSON.stringify(obj));
// Output: {"type":"FastBuffer","data":[1,2,3,4,5]}
```

## toString

```TypeScript
toString(encoding?: string, start?: number, end?: number): string
```

Decodes buf to a string according to the specified character encoding in encoding

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| encoding | string | No | encoding [encoding='utf8'] The character encoding to use |
| start | number | No | start [start = 0] The byte offset to start decoding at |
| end | number | No | end [end = buf.length] The byte offset to stop decoding at (not inclusive) |

**Return value:**

| Type | Description |
| --- | --- |
| string |  |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200068](../errorcode-utils.md#10200068-using-a-released-or-detached-arraybuffer) | The underlying ArrayBuffer is null or detach. |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf1 = fastbuffer.allocUninitializedFromPool(26);
for (let i = 0; i < 26; i++) {
  buf1.writeInt8(i + 97, i);
}
console.info(buf1.toString('utf-8'));
// Output: abcdefghijklmnopqrstuvwxyz
```

## values

```TypeScript
values(): IterableIterator<number>
```

Creates and returns an iterator for buf values (bytes).

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;number&gt; |  |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf1 = fastbuffer.from('buffer');
let pair = buf1.values()
let next:IteratorResult<number> = pair.next()
while (!next.done) {
  console.info(next.value.toString());
  /*
  Output: 98
           117
           102
           102
           101
           114
  */
  next = pair.next();
}
```

## write

```TypeScript
write(str: string, offset?: number, length?: number, encoding?: string): number
```

Writes string to buf at offset according to the character encoding in encoding

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| str | string | Yes | The string to write into the buffer |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to write string |
| length | number | No | length [length = buf.length - offset] Maximum number of bytes to write (written bytes will not exceed buf.length - offset) |
| encoding | string | No | encoding [encoding='utf8'] The character encoding of string. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of bytes written. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | Range error. Possible causes: The value of the parameter is not within the specified range. |
| [10200068](../errorcode-utils.md#10200068-using-a-released-or-detached-arraybuffer) | The underlying ArrayBuffer is null or detach. |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.alloc(256);
let len = buf.write('\u00bd + \u00bc = \u00be', 0);
console.info(`${len} bytes: ${buf.toString('utf-8', 0, len)}`);
// Output: 12 bytes: ½ + ¼ = ¾

let buffer1 = fastbuffer.alloc(10);
let length = buffer1.write('abcd', 8);
console.info("length = " + length);
// Output: length = 2
```

## writeBigInt64BE

```TypeScript
writeBigInt64BE(value: bigint, offset?: number): number
```

Writes value to buf at the specified offset as big-endian.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | bigint | Yes | The 64-bit big-endian integer value to write |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to write. Must satisfy: 0 &lt;= offset &lt;= buf.length - 8 |

**Return value:**

| Type | Description |
| --- | --- |
| number | offset plus the number of bytes written |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(8);
let result = buf.writeBigInt64BE(BigInt(0x0102030405060708), 0);
console.info("result = " + result);
// Output: result = 8
```

## writeBigInt64LE

```TypeScript
writeBigInt64LE(value: bigint, offset?: number): number
```

Writes value to buf at the specified offset as little-endian.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | bigint | Yes | The 64-bit little-endian integer value to write |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to write. Must satisfy: 0 &lt;= offset &lt;= buf.length - 8 |

**Return value:**

| Type | Description |
| --- | --- |
| number | offset plus the number of bytes written |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(8);
let result = buf.writeBigInt64LE(BigInt(0x0102030405060708), 0);
console.info("result = " + result);
// Output: result = 8
```

## writeBigUInt64BE

```TypeScript
writeBigUInt64BE(value: bigint, offset?: number): number
```

Writes value to buf at the specified offset as big-endian.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | bigint | Yes | The unsigned 64-bit big-endian integer value to write |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to write. Must satisfy: 0 &lt;= offset &lt;= buf.length - 8 |

**Return value:**

| Type | Description |
| --- | --- |
| number | offset plus the number of bytes written |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(8);
let result = buf.writeBigUInt64BE(BigInt(0xdecafafecacefade), 0);
console.info("result = " + result);
// Output: result = 8
```

## writeBigUInt64LE

```TypeScript
writeBigUInt64LE(value: bigint, offset?: number): number
```

Writes value to buf at the specified offset as little-endian.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | bigint | Yes | The unsigned 64-bit little-endian integer value to write |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to write. Must satisfy: 0 &lt;= offset &lt;= buf.length - 8 |

**Return value:**

| Type | Description |
| --- | --- |
| number | offset plus the number of bytes written |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(8);
let result = buf.writeBigUInt64LE(BigInt(0xdecafafecacefade), 0);
console.info("result = " + result);
// Output: result = 8
```

## writeDoubleBE

```TypeScript
writeDoubleBE(value: number, offset?: number): number
```

Writes value to buf at the specified offset as big-endian.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | The 64-bit big-endian double value to write |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to write. Must satisfy: 0 &lt;= offset &lt;= buf.length - 8 |

**Return value:**

| Type | Description |
| --- | --- |
| number | offset plus the number of bytes written |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 8. Received value is: [offset] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(8);
let result = buf.writeDoubleBE(123.456, 0);
console.info("result = " + result);
// Output: result = 8
```

## writeDoubleLE

```TypeScript
writeDoubleLE(value: number, offset?: number): number
```

Writes value to buf at the specified offset as little-endian.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | The 64-bit little-endian double value to write |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to write. Must satisfy: 0 &lt;= offset &lt;= buf.length - 8 |

**Return value:**

| Type | Description |
| --- | --- |
| number | offset plus the number of bytes written |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 8. Received value is: [offset] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(8);
let result = buf.writeDoubleLE(123.456, 0);
console.info("result = " + result);
// Output: result = 8
```

## writeFloatBE

```TypeScript
writeFloatBE(value: number, offset?: number): number
```

Writes value to buf at the specified offset as big-endian.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | The 32-bit big-endian float value to write |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to write. Must satisfy: 0 &lt;= offset &lt;= buf.length - 4 |

**Return value:**

| Type | Description |
| --- | --- |
| number | offset plus the number of bytes written |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 4. Received value is: [offset] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(8);
let result = buf.writeFloatBE(3.1415, 0);
console.info("result = " + result);
// Output: result = 4
```

## writeFloatLE

```TypeScript
writeFloatLE(value: number, offset?: number): number
```

Writes value to buf at the specified offset as little-endian.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | The 32-bit little-endian float value to write |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to write. Must satisfy: 0 &lt;= offset &lt;= buf.length - 4 |

**Return value:**

| Type | Description |
| --- | --- |
| number | offset plus the number of bytes written |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 4. Received value is: [offset] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(8);
let result = buf.writeFloatLE(3.1415, 0);
console.info("result = " + result);
// Output: result = 4
```

## writeInt16BE

```TypeScript
writeInt16BE(value: number, offset?: number): number
```

Writes value to buf at the specified offset as big-endian. The value must be a valid signed 16-bit integer

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | The signed 16-bit big-endian integer value to write |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to write. Must satisfy: 0 &lt;= offset &lt;= buf.length - 2 |

**Return value:**

| Type | Description |
| --- | --- |
| number | offset plus the number of bytes written |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(2);
let result = buf.writeInt16BE(0x0102, 0);
console.info("result = " + result);
// Output: result = 2
```

## writeInt16LE

```TypeScript
writeInt16LE(value: number, offset?: number): number
```

Writes value to buf at the specified offset as little-endian. The value must be a valid signed 16-bit integer

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | The signed 16-bit little-endian integer value to write |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to write. Must satisfy: 0 &lt;= offset &lt;= buf.length - 2 |

**Return value:**

| Type | Description |
| --- | --- |
| number | offset plus the number of bytes written |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(2);
let result = buf.writeInt16LE(0x0304, 0);
console.info("result = " + result);
// Output: result = 2
```

## writeInt32BE

```TypeScript
writeInt32BE(value: number, offset?: number): number
```

Writes value to buf at the specified offset as big-endian. The value must be a valid signed 32-bit integer.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | The signed 32-bit big-endian integer value to write |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to write. Must satisfy: 0 &lt;= offset &lt;= buf.length - 4 |

**Return value:**

| Type | Description |
| --- | --- |
| number | offset plus the number of bytes written |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(4);
let result = buf.writeInt32BE(0x01020304, 0);
console.info("result = " + result);
// Output: result = 4
```

## writeInt32LE

```TypeScript
writeInt32LE(value: number, offset?: number): number
```

Writes value to buf at the specified offset as little-endian. The value must be a valid signed 32-bit integer.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | The signed 32-bit little-endian integer value to write |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to write. Must satisfy: 0 &lt;= offset &lt;= buf.length - 4 |

**Return value:**

| Type | Description |
| --- | --- |
| number | offset plus the number of bytes written |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(4);
let result = buf.writeInt32LE(0x05060708, 0);
console.info("result = " + result);
// Output: result = 4
```

## writeInt8

```TypeScript
writeInt8(value: number, offset?: number): number
```

Writes value to buf at the specified offset. value must be a valid signed 8-bit integer.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | The signed 8-bit integer value to write |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to write. Must satisfy: 0 &lt;= offset &lt;= buf.length - 1 |

**Return value:**

| Type | Description |
| --- | --- |
| number | offset plus the number of bytes written |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(2);
let result = buf.writeInt8(2, 0);
console.info("result = " + result);
// Output: result = 1
let result1 = buf.writeInt8(-2, 1);
console.info("result1 = " + result1);
// Output: result1 = 2
```

## writeIntBE

```TypeScript
writeIntBE(value: number, offset: number, byteLength: number): number
```

Writes byteLength bytes of value to buf at the specified offset as big-endian

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | The big-endian integer value to write |
| offset | number | Yes | Number of bytes to skip before starting to write. Must satisfy: 0 &lt;= offset &lt;= buf.length - byteLength |
| byteLength | number | Yes | Number of bytes to write. Must satisfy 0 &lt; byteLength &lt;= 6 |

**Return value:**

| Type | Description |
| --- | --- |
| number | offset plus the number of bytes written |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(6);
let result = buf.writeIntBE(0x1234567890ab, 0, 6);
console.info("result = " + result);
// Output: result = 6
```

## writeIntLE

```TypeScript
writeIntLE(value: number, offset: number, byteLength: number): number
```

Writes byteLength bytes of value to buf at the specified offset as little-endian

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | The little-endian integer value to write |
| offset | number | Yes | Number of bytes to skip before starting to write. Must satisfy: 0 &lt;= offset &lt;= buf.length - byteLength |
| byteLength | number | Yes | Number of bytes to write. Must satisfy 0 &lt; byteLength &lt;= 6 |

**Return value:**

| Type | Description |
| --- | --- |
| number | offset plus the number of bytes written |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(6);
let result = buf.writeIntLE(0x1234567890ab, 0, 6);
console.info("result = " + result);
// Output: result = 6
```

## writeUInt16BE

```TypeScript
writeUInt16BE(value: number, offset?: number): number
```

Writes value to buf at the specified offset as big-endian. The value must be a valid unsigned 16-bit integer.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | The unsigned 16-bit big-endian integer value to write |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to write. Must satisfy 0 &lt;= offset &lt;= buf.length - 2 |

**Return value:**

| Type | Description |
| --- | --- |
| number | offset plus the number of bytes written |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(4);
let result = buf.writeUInt16BE(0xdead, 0);
console.info("result = " + result);
// Output: result = 2
let result1 = buf.writeUInt16BE(0xbeef, 2);
console.info("result1 = " + result1);
// Output: result1 = 4
```

## writeUInt16LE

```TypeScript
writeUInt16LE(value: number, offset?: number): number
```

Writes value to buf at the specified offset as little-endian. The value must be a valid unsigned 16-bit integer.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | The unsigned 16-bit little-endian integer value to write |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to write. Must satisfy 0 &lt;= offset &lt;= buf.length - 2 |

**Return value:**

| Type | Description |
| --- | --- |
| number | offset plus the number of bytes written |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(4);
let result = buf.writeUInt16LE(0xdead, 0);
console.info("result = " + result);
// Output: result = 2
let result1 = buf.writeUInt16LE(0xbeef, 2);
console.info("result1 = " + result1);
// Output: result1 = 4
```

## writeUInt32BE

```TypeScript
writeUInt32BE(value: number, offset?: number): number
```

Writes value to buf at the specified offset as big-endian. The value must be a valid unsigned 32-bit integer.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | The unsigned 32-bit big-endian integer value to write |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to write. Must satisfy 0 &lt;= offset &lt;= buf.length - 4 |

**Return value:**

| Type | Description |
| --- | --- |
| number | offset plus the number of bytes written |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(4);
let result = buf.writeUInt32BE(0xfeedface, 0);
console.info("result = " + result);
// Output: result = 4
```

## writeUInt32LE

```TypeScript
writeUInt32LE(value: number, offset?: number): number
```

Writes value to buf at the specified offset as little-endian. The value must be a valid unsigned 32-bit integer.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | The unsigned 32-bit little-endian integer value to write |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to write. Must satisfy 0 &lt;= offset &lt;= buf.length - 4 |

**Return value:**

| Type | Description |
| --- | --- |
| number | offset plus the number of bytes written |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(4);
let result = buf.writeUInt32LE(0xfeedface, 0);
console.info("result = " + result);
// Output: result = 4
```

## writeUInt8

```TypeScript
writeUInt8(value: number, offset?: number): number
```

Writes value to buf at the specified offset. value must be a valid unsigned 8-bit integer

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | The unsigned 8-bit integer value to write |
| offset | number | No | offset [offset = 0] Number of bytes to skip before starting to write. Must satisfy 0 &lt;= offset &lt;= buf.length - 1 |

**Return value:**

| Type | Description |
| --- | --- |
| number | offset plus the number of bytes written |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(4);
let result = buf.writeUInt8(0x3, 0);
console.info("result = " + result);
// Output: result = 1
let result1 = buf.writeUInt8(0x4, 1);
console.info("result1 = " + result1);
// Output: result1 = 2
let result2 = buf.writeUInt8(0x23, 2);
console.info("result2 = " + result2);
// Output: result2 = 3
let result3 = buf.writeUInt8(0x42, 3);
console.info("result3 = " + result3);
// Output: result3 = 4
```

## writeUIntBE

```TypeScript
writeUIntBE(value: number, offset: number, byteLength: number): number
```

Writes byteLength bytes of value to buf at the specified offset as big-endian

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | The unsigned big-endian integer value to write |
| offset | number | Yes | Number of bytes to skip before starting to write. Must satisfy: 0 &lt;= offset &lt;= buf.length - byteLength |
| byteLength | number | Yes | Number of bytes to write. Must satisfy 0 &lt; byteLength &lt;= 6 |

**Return value:**

| Type | Description |
| --- | --- |
| number | offset plus the number of bytes written |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(6);
let result = buf.writeUIntBE(0x1234567890ab, 0, 6);
console.info("result = " + result);
// Output: result = 6
```

## writeUIntLE

```TypeScript
writeUIntLE(value: number, offset: number, byteLength: number): number
```

Writes byteLength bytes of value to buf at the specified offset as little-endian

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | The unsigned little-endian integer value to write |
| offset | number | Yes | Number of bytes to skip before starting to write. Must satisfy: 0 &lt;= offset &lt;= buf.length - byteLength |
| byteLength | number | Yes | Number of bytes to write. Must satisfy 0 &lt; byteLength &lt;= 6 |

**Return value:**

| Type | Description |
| --- | --- |
| number | offset plus the number of bytes written |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(6);
let result = buf.writeUIntLE(0x1234567890ab, 0, 6);
console.info("result = " + result);
// Output: result = 6
```

## buffer

```TypeScript
buffer: ArrayBuffer
```

The arraybuffer underlying the FastBuffer object

**Type:** ArrayBuffer

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

## byteOffset

```TypeScript
byteOffset: number
```

The byteOffset of the Buffers underlying ArrayBuffer object

**Type:** number

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

## length

```TypeScript
length: number
```

Returns the number of bytes in buf

**Type:** number

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang
