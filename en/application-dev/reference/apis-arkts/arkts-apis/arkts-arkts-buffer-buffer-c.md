# Buffer

```TypeScript
class Buffer
```

The Buffer object is a method of handling buffers dedicated to binary data.

**Since:** 9

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { buffer } from '@kit.ArkTS';
```

## compare

```TypeScript
compare(
      target: Buffer | Uint8Array,
      targetStart?: number,
      targetEnd?: number,
      sourceStart?: number,
      sourceEnd?: number
    ): -1 | 0 | 1
```

Compares this **Buffer** object with another object.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | Buffer &#124; Uint8Array | Yes | Target **Buffer** object to compare. |
| targetStart | number | No | Offset to the start of the data to compare in the target **Buffer** object. The default value is **0**. |
| targetEnd | number | No | Offset to the end of the data to compare in the target **Buffer** object (not inclusive). The default value is the length of the target **Buffer** object. |
| sourceStart | number | No | Offset to the start of the data to compare in this **Buffer** object. The default value is **0**. |
| sourceEnd | number | No | Offset to the end of the data to compare in this **Buffer** object (not inclusive). The default value is the length of this **Buffer** object. |

**Return value:**

| Type | Description |
| --- | --- |
| -1 &#124; 0 &#124; 1 | Comparison result. The value **0** is returned if the two **Buffer** objects are the same; **1** is returned if this object comes after the target object when sorted; **-1** is returned if this object comes before the target object when sorted. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[targetStart/targetEnd/sourceStart/sourceEnd]" is out of range. It must be &gt;= 0 and &lt;= [right range]. Received value is: [targetStart/targetEnd/sourceStart/sourceEnd] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.from([1, 2, 3, 4, 5, 6, 7, 8, 9]);
let buf2 = buffer.from([5, 6, 7, 8, 9, 1, 2, 3, 4]);

console.info(buf1.compare(buf2, 5, 9, 0, 4).toString());
// Output: 0
console.info(buf1.compare(buf2, 0, 6, 4).toString());
// Output: -1
console.info(buf1.compare(buf2, 5, 6, 5).toString());
// Output: 1
```

## copy

```TypeScript
copy(target: Buffer | Uint8Array, targetStart?: number, sourceStart?: number, sourceEnd?: number): number
```

Copies data at the specified position in this **Buffer** object to the specified position in another **Buffer** object.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | Buffer &#124; Uint8Array | Yes | **Buffer** or **Uint8Array** object to which data is copied. |
| targetStart | number | No | Offset to the start position in the target object where data is copied. The default value is **0**. |
| sourceStart | number | No | Offset to the start position in this **Buffer** object where data is copied. The default value is **0**. |
| sourceEnd | number | No | Offset to the end position in this **Buffer** object (not inclusive). The default value is the length of this **Buffer** object. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Total length of the data copied, in bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[targetStart/sourceStart/sourceEnd]" is out of range. It must be &gt;= 0. Received value is: [targetStart/sourceStart/sourceEnd] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.allocUninitializedFromPool(26);
let buf2 = buffer.allocUninitializedFromPool(26).fill('!');

for (let i = 0; i < 26; i++) {
  buf1.writeInt8(i + 97, i);
}

buf1.copy(buf2, 8, 16, 20);
console.info(buf2.toString('ascii', 0, 25));
// Output: !!!!!!!!qrst!!!!!!!!!!!!!
```

## entries

```TypeScript
entries(): IterableIterator<[number, number]>
```

Creates and returns an iterator that contains key-value pairs of this **Buffer** object.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;[number, number]&gt; | Iterator that contains the key and value, both of which are of the number type.<br>**Since:** 9 - 10 |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;[number, number]&gt; | <br>**Since:** 11 |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from('buffer');
let pair = buf.entries();
let next: IteratorResult<Object[]> = pair.next();
while (!next.done) {
  console.info("buffer: " + next.value);
  /*
  Output: buffer: 0,98
           buffer: 1,117
           buffer: 2,102
           buffer: 3,102
           buffer: 4,101
           buffer: 5,114
   */
  next = pair.next();
}
```

## equals

```TypeScript
equals(otherBuffer: Uint8Array | Buffer): boolean
```

Checks whether this **Buffer** object is the same as another **Buffer** object.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| otherBuffer | Uint8Array &#124; Buffer | Yes | **Buffer** object to compare. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the two objects are the same; otherwise, **false** is returned. |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.from('ABC');
let buf2 = buffer.from('414243', 'hex');
let buf3 = buffer.from('ABCD');

console.info(buf1.equals(buf2).toString());
// Output: true
console.info(buf1.equals(buf3).toString());
// Output: false
```

## fill

```TypeScript
fill(
      value: string | Buffer | Uint8Array | number,
      offset?: number,
      end?: number,
      encoding?: BufferEncoding
    ): Buffer
```

Fills this **Buffer** object at the specified position. By default, data is filled cyclically.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string &#124; Buffer &#124; Uint8Array &#124; number | Yes | Value to fill.<br>**Since:** 11 |
| offset | number | No | Offset to the start position in this **Buffer** object where data is filled. The default value is **0**. |
| end | number | No | Offset to the end position in this **Buffer** object (not inclusive). The default value is the length of this **Buffer** object. |
| encoding | BufferEncoding | No | Encoding format (valid only when **value** is a string). The default value is **'utf8'**. |

**Return value:**

| Type | Description |
| --- | --- |
| Buffer | **Buffer** object filled with the specified value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[offset/end]" is out of range. It must be &gt;= 0 and &lt;= [right range]. Received value is: [offset/end] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let b = buffer.allocUninitializedFromPool(50).fill('h');
console.info(b.toString());
// Output: hhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhh
```

## includes

```TypeScript
includes(value: string | number | Buffer | Uint8Array, byteOffset?: number, encoding?: BufferEncoding): boolean
```

Checks whether this **Buffer** object contains the specified value.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string &#124; number &#124; Buffer &#124; Uint8Array | Yes | Value to match.<br>**Since:** 11 |
| byteOffset | number | No | Number of bytes to skip before starting to check data. If the offset is a negative number, data is checked from the end of the **Buffer** object. The default value is **0**. |
| encoding | BufferEncoding | No | Encoding format (valid only when **value** is a string). The default value is **'utf8'**. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the object contains the specified value; otherwise, **false** is returned. |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from('this is a buffer');
console.info(buf.includes('this').toString());
// Output: true
console.info(buf.includes('be').toString());
// Output: false
```

## indexOf

```TypeScript
indexOf(value: string | number | Buffer | Uint8Array, byteOffset?: number, encoding?: BufferEncoding): number
```

Obtains the index of the first occurrence of the specified value in this **Buffer** object. If no match is found, **-1** is returned.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string &#124; number &#124; Buffer &#124; Uint8Array | Yes | Value to match.<br>**Since:** 11 |
| byteOffset | number | No | Number of bytes to skip before starting to check data. If the offset is a negative number, data is checked from the end of the **Buffer** object. The default value is **0**. |
| encoding | BufferEncoding | No | Encoding format (valid only when **value** is a string). The default value is **'utf8'**. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Index obtained. |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from('this is a buffer');
console.info(buf.indexOf('this').toString());
// Output: 0
console.info(buf.indexOf('is').toString());
// Output: 2
```

## keys

```TypeScript
keys(): IterableIterator<number>
```

Creates and returns an iterator that contains the keys of this **Buffer** object.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;number&gt; | Iterator created. |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from('buffer');
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
lastIndexOf(value: string | number | Buffer | Uint8Array, byteOffset?: number, encoding?: BufferEncoding): number
```

Obtains the index of the last occurrence of the specified value in this **Buffer** object. If no match is found, **-1** is returned.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string &#124; number &#124; Buffer &#124; Uint8Array | Yes | Value to match.<br>**Since:** 11 |
| byteOffset | number | No | Number of bytes to skip before starting to check data. If the offset is a negative number, data is checked from the end of the **Buffer** object. The default value is the length of this **Buffer** object. |
| encoding | BufferEncoding | No | Encoding format (valid only when **value** is a string). The default value is **'utf8'**. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Index obtained. |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from('this buffer is a buffer');
console.info(buf.lastIndexOf('this').toString());
// Output: 0
console.info(buf.lastIndexOf('buffer').toString());
// Output: 17
```

## readBigInt64BE

```TypeScript
readBigInt64BE(offset?: number): bigint
```

Reads a 64-bit, big-endian, signed big integer from this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | No | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - 8 |

**Return value:**

| Type | Description |
| --- | --- |
| bigint | Data read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 8. Received value is: [offset] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0x63, 0x64, 0x65, 0x66, 0x67, 0x68, 0x69, 0x70,
  0x71, 0x72, 0x73, 0x74, 0x75, 0x76, 0x77, 0x78]);
console.info(buf.readBigInt64BE(0).toString());
// Output: 7161960797921896816

let buf1 = buffer.allocUninitializedFromPool(8);
let result = buf1.writeBigInt64BE(BigInt(0x0102030405060708), 0);
console.info("result = " + result);
// Output: result = 8
```

## readBigInt64LE

```TypeScript
readBigInt64LE(offset?: number): bigint
```

Reads a 64-bit, little-endian, signed big integer from this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | No | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - 8 |

**Return value:**

| Type | Description |
| --- | --- |
| bigint | Data read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 8. Received value is: [offset] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0x63, 0x64, 0x65, 0x66, 0x67, 0x68, 0x69, 0x70,
  0x71, 0x72, 0x73, 0x74, 0x75, 0x76, 0x77, 0x78]);
console.info(buf.readBigUInt64LE(0).toString());
// Output: 8100120198111388771

let buf1 = buffer.allocUninitializedFromPool(8);
let result = buf1.writeBigUInt64BE(BigInt(0xdecafafecacefade), 0);
console.info("result = " + result);
// Output: result = 8
```

## readBigUInt64BE

```TypeScript
readBigUInt64BE(offset?: number): bigint
```

Reads a 64-bit, big-endian, unsigned big integer from this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | No | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - 8 |

**Return value:**

| Type | Description |
| --- | --- |
| bigint | Data read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 8. Received value is: [offset] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0x63, 0x64, 0x65, 0x66, 0x67, 0x68, 0x69, 0x70,
  0x71, 0x72, 0x73, 0x74, 0x75, 0x76, 0x77, 0x78]);
console.info(buf.readBigUInt64BE(0).toString());
// Output: 7161960797921896816
let buf1 = buffer.allocUninitializedFromPool(8);
let result = buf1.writeBigUInt64BE(BigInt(0xdecafafecacefade), 0);
console.info("result = " + result);
// Output: result = 8
```

## readBigUInt64LE

```TypeScript
readBigUInt64LE(offset?: number): bigint
```

Reads a 64-bit, little-endian, unsigned big integer from this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | No | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - 8 |

**Return value:**

| Type | Description |
| --- | --- |
| bigint | Data read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 8. Received value is: [offset] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0x63, 0x64, 0x65, 0x66, 0x67, 0x68, 0x69, 0x70,
  0x71, 0x72, 0x73, 0x74, 0x75, 0x76, 0x77, 0x78]);
console.info(buf.readBigUInt64LE(0).toString());
// Output: 8100120198111388771

let buf1 = buffer.allocUninitializedFromPool(8);
let result = buf1.writeBigUInt64BE(BigInt(0xdecafafecacefade), 0);
console.info("result = " + result);
// Output: result = 8
```

## readDoubleBE

```TypeScript
readDoubleBE(offset?: number): number
```

Reads a 64-bit, big-endian, double-precision floating-point number from this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | No | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - 8 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Data read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 8. Received value is: [offset] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([1, 2, 3, 4, 5, 6, 7, 8]);
console.info(buf.readDoubleBE(0).toString());
// Output: 8.20788039913184e-304
let buf1 = buffer.allocUninitializedFromPool(8);
let result = buf1.writeDoubleBE(123.456, 0);
console.info("result = " + result);
// Output: result = 8
```

## readDoubleLE

```TypeScript
readDoubleLE(offset?: number): number
```

Reads a 64-bit, little-endian, double-precision floating-point number from this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | No | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - 8 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Data read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 8. Received value is: [offset] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([1, 2, 3, 4, 5, 6, 7, 8]);
console.info(buf.readDoubleLE(0).toString());
// Output: 5.447603722011605e-270
let buf1 = buffer.allocUninitializedFromPool(8);
let result = buf1.writeDoubleLE(123.456, 0);
console.info("result = " + result);
// Output: result = 8
```

## readFloatBE

```TypeScript
readFloatBE(offset?: number): number
```

Reads a 32-bit, big-endian, single-precision floating-point number from this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | No | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - 4 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Data read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 4. Received value is: [offset] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([1, 2, 3, 4, 5, 6, 7, 8]);
console.info(buf.readFloatBE(0).toString());
// Output: 2.387939260590663e-38
let buf1 = buffer.allocUninitializedFromPool(4);
let result = buf1.writeFloatBE(0xcabcbcbc, 0);
console.info("result = " + result);
// Output: result = 4
```

## readFloatLE

```TypeScript
readFloatLE(offset?: number): number
```

Reads a 32-bit, little-endian, single-precision floating-point number from this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | No | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - 4 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Data read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 4. Received value is: [offset] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([1, 2, 3, 4, 5, 6, 7, 8]);
console.info(buf.readFloatLE(0).toString());
// Output: 1.539989614439558e-36
let buf1 = buffer.allocUninitializedFromPool(4);
let result = buf1.writeFloatLE(0xcabcbcbc, 0);
console.info("result = " + result);
// Output: result = 4
```

## readInt16BE

```TypeScript
readInt16BE(offset?: number): number
```

Reads a 16-bit, big-endian, signed integer from this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | No | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - 2 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Data read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 2. Received value is: [offset] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0, 5]);
console.info(buf.readInt16BE(0).toString());
// Output: 5
let buf1 = buffer.alloc(2);
let result = buf1.writeInt16BE(0x1234, 0);
console.info("result = " + result);
// Output: result = 2
```

## readInt16LE

```TypeScript
readInt16LE(offset?: number): number
```

Reads a 16-bit, little-endian, signed integer from this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | No | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - 2 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Data read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 2. Received value is: [offset] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0, 5]);
console.info(buf.readInt16LE(0).toString());
// Output: 1280
let buf1 = buffer.alloc(2);
let result = buf1.writeInt16BE(0x1234, 0);
console.info("result = " + result);
// Output: result = 2
```

## readInt32BE

```TypeScript
readInt32BE(offset?: number): number
```

Reads a 32-bit, big-endian, signed integer from this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | No | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - 4 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Data read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 4. Received value is: [offset] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0, 0, 0, 5]);
console.info(buf.readInt32BE(0).toString());
// Output: 5
let buf1 = buffer.alloc(4);
let result = buf1.writeInt32BE(0x12345678, 0);
console.info("result = " + result);
// Output: result = 4
```

## readInt32LE

```TypeScript
readInt32LE(offset?: number): number
```

Reads a 32-bit, little-endian, signed integer from this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | No | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - 4 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Data read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 4. Received value is: [offset] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0, 0, 0, 5]);
console.info(buf.readInt32LE(0).toString());
// Output: 83886080
let buf1 = buffer.alloc(4);
let result = buf1.writeInt32BE(0x12345678, 0);
console.info("result = " + result);
// Output: result = 4
```

## readInt8

```TypeScript
readInt8(offset?: number): number
```

Reads an 8-bit signed integer from this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | No | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - 1 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Data read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 1. Received value is: [offset] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([-1, 5]);
console.info(buf.readInt8(0).toString());
// Output: 0
console.info(buf.readInt8(1).toString());
// Output: 5
let buf1 = buffer.allocUninitializedFromPool(2);
let result = buf1.writeInt8(0x12);
console.info("result = " + result);
// Output: result = 1
```

## readIntBE

```TypeScript
readIntBE(offset: number, byteLength: number): number
```

Reads the specified number of bytes from this **Buffer** object at the specified offset, and interprets the result as a big-endian, two's complement signed value that supports up to 48 bits of precision.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | Yes | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - byteLength |
| byteLength | number | Yes | Number of bytes to read. Value range: 1 &lt;= byteLength &lt;= 6 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Data read. If the offset is a decimal, undefined is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from("ab");
let num = buf.readIntBE(0, 1);
console.info(num.toString());
// Output: 97
let buf1 = buffer.allocUninitializedFromPool(6);
let result = buf1.writeIntBE(0x123456789011, 0, 6);
console.info("result = " + result);
// Output: result = 6
```

## readIntLE

```TypeScript
readIntLE(offset: number, byteLength: number): number
```

Reads the specified number of bytes from this **Buffer** object at the specified offset and interprets the result as a little-endian, two's complement signed value that supports up to 48 bits of precision.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | Yes | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - byteLength |
| byteLength | number | Yes | Number of bytes to read. Value range: 1 &lt;= byteLength &lt;= 6 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Data read. If the offset is a decimal, undefined is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0x12, 0x34, 0x56, 0x78, 0x90, 0xab]);
console.info(buf.readIntLE(0, 6).toString(16));
// Output: -546f87a9cbee
let buf1 = buffer.allocUninitializedFromPool(6);
let result = buf1.writeIntLE(0x123456789011, 0, 6);
console.info("result = " + result);
// Output: result = 6
```

## readUInt16BE

```TypeScript
readUInt16BE(offset?: number): number
```

Reads a 16-bit, big-endian, unsigned integer from this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | No | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - 2 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Data read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 2. Received value is: [offset] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0x12, 0x34, 0x56]);
console.info(buf.readUInt16BE(0).toString(16));
// Output: 1234
console.info(buf.readUInt16BE(1).toString(16));
// Output: 3456
let buf1 = buffer.allocUninitializedFromPool(4);
let result = buf1.writeUInt16BE(0x1234, 0);
console.info("result = " + result);
// Output: result = 2
```

## readUInt16LE

```TypeScript
readUInt16LE(offset?: number): number
```

Reads a 16-bit, little-endian, unsigned integer from this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | No | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - 2 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Data read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 2. Received value is: [offset] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0x12, 0x34, 0x56]);
console.info(buf.readUInt16LE(0).toString(16));
// Output: 3412
console.info(buf.readUInt16LE(1).toString(16));
// Output: 5634
let buf1 = buffer.allocUninitializedFromPool(4);
let result = buf1.writeUInt16LE(0x1234, 0);
console.info("result = " + result);
// Output: result = 2
```

## readUInt32BE

```TypeScript
readUInt32BE(offset?: number): number
```

Reads a 32-bit, big-endian, unsigned integer from this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | No | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - 4 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Data read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 4. Received value is: [offset] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0x12, 0x34, 0x56, 0x78]);
console.info(buf.readUInt32BE(0).toString(16));
// Output: 12345678
let buf1 = buffer.allocUninitializedFromPool(4);
let result = buf1.writeUInt32BE(0x12345678, 0);
console.info("result = " + result);
// Output: result = 4
```

## readUInt32LE

```TypeScript
readUInt32LE(offset?: number): number
```

Reads a 32-bit, little-endian, unsigned integer from this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | No | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - 4 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Data read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 4. Received value is: [offset] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0x12, 0x34, 0x56, 0x78]);
console.info(buf.readUInt32LE(0).toString(16));
// Output: 78563412
let buf1 = buffer.allocUninitializedFromPool(4);
let result = buf1.writeUInt32LE(0x12345678, 0);
console.info("result = " + result);
// Output: result = 4
```

## readUInt8

```TypeScript
readUInt8(offset?: number): number
```

Reads an 8-bit unsigned integer from this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | No | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - 1 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Data read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 1. Received value is: [offset] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([1, -2]);
console.info(buf.readUInt8(0).toString());
// Output: 1
console.info(buf.readUInt8(1).toString());
// Output: 0
let buf1 = buffer.allocUninitializedFromPool(4);
let result = buf1.writeUInt8(0x42);
console.info("result = " + result);
// Output: result = 1
```

## readUIntBE

```TypeScript
readUIntBE(offset: number, byteLength: number): number
```

Reads the specified number of bytes from this **Buffer** object at the specified offset, and interprets the result as an unsigned, big-endian integer that supports up to 48 bits of precision.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | Yes | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - byteLength |
| byteLength | number | Yes | Number of bytes to read. Value range: 1 &lt;= byteLength &lt;= 6 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Data read. If the offset is a decimal, undefined is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0x12, 0x34, 0x56, 0x78, 0x90, 0xab]);
console.info(buf.readUIntBE(0, 6).toString(16));
// Output: 1234567890ab
let buf1 = buffer.allocUninitializedFromPool(4);
let result = buf1.writeUIntBE(0x13141516, 0, 4);
console.info("result = " + result);
// Output: result = 4
```

## readUIntLE

```TypeScript
readUIntLE(offset: number, byteLength: number): number
```

Reads the specified number of bytes from this **Buffer** object at the specified offset, and interprets the result as an unsigned, little-endian integer that supports up to 48 bits of precision.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | Yes | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - byteLength |
| byteLength | number | Yes | Number of bytes to read. Value range: 1 &lt;= byteLength &lt;= 6 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Data read. If the offset is a decimal, undefined is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0x12, 0x34, 0x56, 0x78, 0x90, 0xab]);
console.info(buf.readUIntLE(0, 6).toString(16));
// Output: ab9078563412
let buf1 = buffer.allocUninitializedFromPool(4);
let result = buf1.writeUIntLE(0x13141516, 0, 4);
console.info("result = " + result);
// Output: result = 4
```

## subarray

```TypeScript
subarray(start?: number, end?: number): Buffer
```

Truncates this **Buffer** object from the specified position to create a new **Buffer** object.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | number | No | Offset to the start position in this **Buffer** object where data is truncated. The default value is **0**. |
| end | number | No | Offset to the end position in this **Buffer** object (not inclusive). The default value is the length of this **Buffer** object. |

**Return value:**

| Type | Description |
| --- | --- |
| Buffer | **Buffer** object created. When the value of **start** or **end** is less than **0**, an empty buffer is returned. |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.allocUninitializedFromPool(26);

for (let i = 0; i < 26; i++) {
  buf1.writeInt8(i + 97, i);
}
const buf2 = buf1.subarray(0, 3);
console.info(buf2.toString('ascii', 0, buf2.length));
// Output: abc
```

## swap16

```TypeScript
swap16(): Buffer
```

Converts this **Buffer** object into an array of unsigned 16-bit integers and swaps the byte order in place.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| Buffer | **Buffer** object swapped. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200009](../errorcode-utils.md#10200009-buffer-size-error) | The buffer size must be a multiple of 16-bits |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.from([0x1, 0x2, 0x3, 0x4, 0x5, 0x6, 0x7, 0x8]);
console.info(buf1.toString('hex'));
// Output: 0102030405060708
buf1.swap16();
console.info(buf1.toString('hex'));
// Output: 0201040306050807
```

## swap32

```TypeScript
swap32(): Buffer
```

Converts this **Buffer** object into an array of unsigned 32-bit integers and swaps the byte order in place.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| Buffer | **Buffer** object swapped. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200009](../errorcode-utils.md#10200009-buffer-size-error) | The buffer size must be a multiple of 32-bits |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.from([0x1, 0x2, 0x3, 0x4, 0x5, 0x6, 0x7, 0x8]);
console.info(buf1.toString('hex'));
// Output: 0102030405060708
buf1.swap32();
console.info(buf1.toString('hex'));
// Output: 0403020108070605
```

## swap64

```TypeScript
swap64(): Buffer
```

Converts this **Buffer** object into an array of unsigned 64-bit integers and swaps the byte order in place.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| Buffer | **Buffer** object swapped. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200009](../errorcode-utils.md#10200009-buffer-size-error) | The buffer size must be a multiple of 64-bits |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.from([0x1, 0x2, 0x3, 0x4, 0x5, 0x6, 0x7, 0x8]);
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

Converts this **Buffer** object into a JSON object.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| Object | JSON object. |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.from([0x1, 0x2, 0x3, 0x4, 0x5]);
let obj = buf1.toJSON();
console.info(JSON.stringify(obj));
// Output: {"type":"Buffer","data":[1,2,3,4,5]}
```

## toString

```TypeScript
toString(encoding?: string, start?: number, end?: number): string
```

Converts the data at the specified position in this **Buffer** object into a string in the specified encoding format.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| encoding | string | No | Encoding format (valid only when **value** is a string). The default value is **'utf8'**. |
| start | number | No | Offset to the start position of the data to convert. The default value is **0**. |
| end | number | No | Offset to the end position of data. The default value is the length of this **Buffer** object. |

**Return value:**

| Type | Description |
| --- | --- |
| string | String. When the value of **start** is greater than or equal to **Buffer.length** or **start** is greater than **end**, an empty string is returned. |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.allocUninitializedFromPool(26);
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

Creates and returns an iterator that contains the values of this **Buffer** object.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;number&gt; | Iterator. |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.from('buffer');
let pair = buf1.values();
let next:IteratorResult<number> = pair.next();
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

Writes a string of the specified length to this **Buffer** object at the specified position in the given encoding format.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| str | string | Yes | String to write. |
| offset | number | No | Offset. The default value is **0**. |
| length | number | No | Maximum number of bytes to write. The default value is **Buffer.length** minus **offset**. |
| encoding | string | No | Encoding format of the string. The default value is **'utf8'**. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of bytes written. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[offset/length]" is out of range. It must be &gt;= 0 and &lt;= buf.length. Received value is: [offset/length] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.alloc(256);
let len = buf.write('\u00bd + \u00bc = \u00be', 0);
console.info(`${len} bytes: ${buf.toString('utf-8', 0, len)}`);
// Output: 12 bytes: ½ + ¼ = ¾

let buffer1 = buffer.alloc(10);
let length = buffer1.write('abcd', 8);
console.info("length = " + length);
// Output: length = 2
```

## writeBigInt64BE

```TypeScript
writeBigInt64BE(value: bigint, offset?: number): number
```

Writes a 64-bit, big-endian, signed big integer to this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | bigint | Yes | Data to write. |
| offset | number | No | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - 8 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Offset plus the number of written bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(8);
let result = buf.writeBigInt64BE(BigInt(0x0102030405060708), 0);
console.info("result = " + result);
// Output: result = 8
```

## writeBigInt64LE

```TypeScript
writeBigInt64LE(value: bigint, offset?: number): number
```

Writes a 64-bit, little-endian, signed big integer to this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | bigint | Yes | Data to write. |
| offset | number | No | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - 8 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Offset plus the number of written bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(8);
let result = buf.writeBigInt64LE(BigInt(0x0102030405060708), 0);
console.info("result = " + result);
// Output: result = 8
```

## writeBigUInt64BE

```TypeScript
writeBigUInt64BE(value: bigint, offset?: number): number
```

Writes a 64-bit, big-endian, signed big integer to this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | bigint | Yes | Data to write. |
| offset | number | No | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - 8 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Offset plus the number of written bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(8);
let result = buf.writeBigUInt64BE(BigInt(0xdecafafecacefade), 0);
console.info("result = " + result);
// Output: result = 8
```

## writeBigUInt64LE

```TypeScript
writeBigUInt64LE(value: bigint, offset?: number): number
```

Writes a 64-bit, little-endian, unsigned big integer to this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | bigint | Yes | Data to write. |
| offset | number | No | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - 8 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Offset plus the number of written bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(8);
let result = buf.writeBigUInt64LE(BigInt(0xdecafafecacefade), 0);
console.info("result = " + result);
// Output: result = 8
```

## writeDoubleBE

```TypeScript
writeDoubleBE(value: number, offset?: number): number
```

Writes a 64-bit, big-endian, double-precision floating-point number to this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Data to write. |
| offset | number | No | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - 8 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Offset plus the number of written bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 8. Received value is: [offset] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(8);
let result = buf.writeDoubleBE(123.456, 0);
console.info("result = " + result);
// Output: result = 8
```

## writeDoubleLE

```TypeScript
writeDoubleLE(value: number, offset?: number): number
```

Writes a 64-bit, little-endian, double-precision floating-point number to this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Data to write. |
| offset | number | No | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - 8 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Offset plus the number of written bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 8. Received value is: [offset] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(8);
let result = buf.writeDoubleLE(123.456, 0);
console.info("result = " + result);
// Output: result = 8
```

## writeFloatBE

```TypeScript
writeFloatBE(value: number, offset?: number): number
```

Writes a 32-bit, big-endian, single-precision floating-point number to this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Data to write. |
| offset | number | No | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - 4 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Offset plus the number of written bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 4. Received value is: [offset] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(8);
let result = buf.writeFloatBE(0xcafebabe, 0);
console.info("result = " + result);
// Output: result = 4
```

## writeFloatLE

```TypeScript
writeFloatLE(value: number, offset?: number): number
```

Writes a 32-bit, little-endian, single-precision floating-point number to this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Data to write. |
| offset | number | No | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - 4 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Offset plus the number of written bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "offset" is out of range. It must be &gt;= 0 and &lt;= buf.length - 4. Received value is: [offset] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(8);
let result = buf.writeFloatLE(0xcafebabe, 0);
console.info("result = " + result);
// Output: result = 4
```

## writeInt16BE

```TypeScript
writeInt16BE(value: number, offset?: number): number
```

Writes a 16-bit, big-endian, signed integer to this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Data to write. |
| offset | number | No | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - 2 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Offset plus the number of written bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(2);
let result = buf.writeInt16BE(0x0102, 0);
console.info("result = " + result);
// Output: result = 2
```

## writeInt16LE

```TypeScript
writeInt16LE(value: number, offset?: number): number
```

Writes a 16-bit, little-endian, signed integer to this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Data to write. |
| offset | number | No | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - 2 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Offset plus the number of written bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(2);
let result = buf.writeInt16LE(0x0304, 0);
console.info("result = " + result);
// Output: result = 2
```

## writeInt32BE

```TypeScript
writeInt32BE(value: number, offset?: number): number
```

Writes a 32-bit, big-endian, signed integer to this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Data to write. |
| offset | number | No | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - 4 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Offset plus the number of written bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(4);
let result = buf.writeInt32BE(0x01020304, 0);
console.info("result = " + result);
// Output: result = 4
```

## writeInt32LE

```TypeScript
writeInt32LE(value: number, offset?: number): number
```

Writes a 32-bit, little-endian, signed integer to this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Data to write. |
| offset | number | No | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - 4 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Offset plus the number of written bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(4);
let result = buf.writeInt32LE(0x05060708, 0);
console.info("result = " + result);
// Output: result = 4
```

## writeInt8

```TypeScript
writeInt8(value: number, offset?: number): number
```

Writes an 8-bit signed integer to this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Data to write. |
| offset | number | No | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - 1 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Offset plus the number of written bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(2);
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

Writes a big-endian signed value of the specified length to this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Data to write. |
| offset | number | Yes | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - byteLength |
| byteLength | number | Yes | Number of bytes to write. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Offset plus the number of written bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(6);
let result = buf.writeIntBE(0x1234567890ab, 0, 6);
console.info("result = " + result);
// Output: result = 6
```

## writeIntLE

```TypeScript
writeIntLE(value: number, offset: number, byteLength: number): number
```

Writes a little-endian signed value of the specified length to this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Data to write. |
| offset | number | Yes | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - byteLength |
| byteLength | number | Yes | Number of bytes to write. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Offset plus the number of written bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(6);
let result = buf.writeIntLE(0x1234567890ab, 0, 6);
console.info("result = " + result);
// Output: result = 6
```

## writeUInt16BE

```TypeScript
writeUInt16BE(value: number, offset?: number): number
```

Writes a 16-bit, big-endian, unsigned integer to this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Data to write. |
| offset | number | No | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - 2 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Offset plus the number of written bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(4);
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

Writes a 16-bit, little-endian, unsigned integer to this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Data to write. |
| offset | number | No | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - 2 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Offset plus the number of written bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(4);
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

Writes a 32-bit, big-endian, unsigned integer to this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Data to write. |
| offset | number | No | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - 4 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Offset plus the number of written bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(4);
let result = buf.writeUInt32BE(0xfeedface, 0);
console.info("result = " + result);
// Output: result = 4
```

## writeUInt32LE

```TypeScript
writeUInt32LE(value: number, offset?: number): number
```

Writes a 32-bit, little-endian, unsigned integer to this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Data to write. |
| offset | number | No | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - 4 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Offset plus the number of written bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(4);
let result = buf.writeUInt32LE(0xfeedface, 0);
console.info("result = " + result);
// Output: result = 4
```

## writeUInt8

```TypeScript
writeUInt8(value: number, offset?: number): number
```

Writes an 8-bit unsigned integer to this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Data to write. |
| offset | number | No | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - 1 |

**Return value:**

| Type | Description |
| --- | --- |
| number | Offset plus the number of written bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(4);
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

Writes an unsigned big-endian value of the specified length to this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Data to write. |
| offset | number | Yes | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - byteLength |
| byteLength | number | Yes | Number of bytes to write. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Offset plus the number of written bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(6);
let result = buf.writeUIntBE(0x1234567890ab, 0, 6);
console.info("result = " + result);
// Output: result = 6
```

## writeUIntLE

```TypeScript
writeUIntLE(value: number, offset: number, byteLength: number): number
```

Writes an unsigned little-endian value of the specified length to this **Buffer** object at the specified offset.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Data to write. |
| offset | number | Yes | Offset. The default value is **0**. Value range: 0 &lt;= offset &lt;= Buffer.length - byteLength |
| byteLength | number | Yes | Number of bytes to write. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Offset plus the number of written bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[param]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [param] |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(6);
let result = buf.writeUIntLE(0x1234567890ab, 0, 6);
console.info("result = " + result);
// Output: result = 6
```

## buffer

```TypeScript
buffer: ArrayBuffer
```

**ArrayBuffer** object.

**Type:** ArrayBuffer

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200013](../errorcode-utils.md#10200013-read-only-property) | Buffer cannot be set for the buffer that has only a getter. |

## byteOffset

```TypeScript
byteOffset: number
```

Offset of the **Buffer** object in the memory pool.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200013](../errorcode-utils.md#10200013-read-only-property) | ByteOffset cannot be set for the buffer that has only a getter. |

## length

```TypeScript
length: number
```

Length of the **Buffer** object, in bytes.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200013](../errorcode-utils.md#10200013-read-only-property) | Length cannot be set for the buffer that has only a getter. |
