# @ohos.fastbuffer (FastBuffer)

<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @Malzahar-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=58e0aac1ecb6b253638163c0254ed24f4d229ae6 translatedAt=2026-08-25T13:24:58.757Z pushedAt=2026-08-26T09:11:01.882Z -->

A **FastBuffer** object is a more efficient buffer container for representing a byte sequence of a fixed length. It is used to store binary data.

When the **FastBuffer** object is constructed using **from**, only the parameters of the FastBuffer, Uint8Array, string, Array, ArrayBuffer, and SharedArrayBuffer types are supported.

FastBuffer is recommended if high-performance processing of large binary data (such as images, file transfer, and network communication) is required.

> **NOTE**
>
> The initial APIs of this module are supported since API version 20. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> Container classes, implemented in static languages, have restrictions on storage locations and properties, and do not support custom properties or methods.

## Modules to Import

```ts
import { fastbuffer } from '@kit.ArkTS';
```

## BufferEncoding

type BufferEncoding = 'ascii' | 'utf8' | 'utf-8' | 'utf16le' | 'ucs2' | 'ucs-2' | 'base64' | 'base64url' | 'latin1' | 'binary' | 'hex'

Enumerates the supported encoding formats.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

| Type   | Description                |
| ------- | -------------------- |
| 'ascii' | ASCII format.|
| 'utf8' | UTF-8 format.|
| 'utf-8' | UTF-8 format.|
| 'utf16le' | UTF-16LE format.|
| 'ucs2' | Alias of UTF-16LE.|
| 'ucs-2' | Alias of UTF-16LE.|
| 'base64' | Base64 format.|
| 'base64url' | Base64URL format.|
| 'latin1' | Alias of iso-8859-1, which is backward compatible with the ASCII format.|
| 'binary' | Binary format.|
| 'hex' | Hexadecimal format.|

## fastbuffer.alloc

alloc(size: number, fill?: string | FastBuffer | number, encoding?: BufferEncoding): FastBuffer

Creates a FastBuffer object of the specified byte length and initializes it. After the call, each byte of the FastBuffer object is filled with the specified fill value. If fill is not specified, the default value 0 is used.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| size | number | Yes| Size of the **FastBuffer** object to create, in bytes. Value range: 0 <= size <= UINT32_MAX|
| fill | string&nbsp;\|&nbsp;[FastBuffer](#fastbuffer)&nbsp;\|&nbsp;number | No | Value to fill into the new buffer. Default value: 0. |
| encoding | [BufferEncoding](#bufferencoding) | No| Encoding format (valid only when **fill** is a string). The default value is **'utf8'**. If an unrecognized encoding format is passed, TypeError is thrown.|

**Return value**

| Type| Description|
| -------- | -------- |
| [FastBuffer](#fastbuffer) | **FastBuffer** object created.|

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

// Create a FastBuffer object with a length of 5, filled with 0 by default.
let buf1 = fastbuffer.alloc(5);
console.info(buf1.toString());
// Output result: 00000
// Create a FastBuffer object with a length of 5, filled with the character 'a'.
let buf2 = fastbuffer.alloc(5, 'a');
// Create a FastBuffer object with a length of 11, filled using base64 encoding.
let buf3 = fastbuffer.alloc(11, 'aGVsbG8gd29ybGQ=', 'base64');
console.info(buf2.toString());
// Output: aaaaa
console.info(buf3.toString());
// Output: hello world
```

## fastbuffer.allocUninitializedFromPool

allocUninitializedFromPool(size: number): FastBuffer

Creates an uninitialized FastBuffer object of the specified size from the buffer pool. Call [fill](#fill) to initialize the object.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| size | number | Yes| Size of the **FastBuffer** object to create, in bytes. Value range: 0 <= size <= UINT32_MAX|

**Return value**

| Type| Description|
| -------- | -------- |
| [FastBuffer](#fastbuffer) | Uninitialized FastBuffer instance. |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(10);
buf.fill(0);
// "buf":[0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
```

## fastbuffer.allocUninitialized

allocUninitialized(size: number): FastBuffer

Creates an uninitialized FastBuffer object of the specified size. Call [fill](#fill) to initialize the object.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| size | number | Yes|Size of the **FastBuffer** object to create, in bytes. Value range: 0 <= size <= UINT32_MAX|

**Return value**

| Type| Description|
| -------- | -------- |
| [FastBuffer](#fastbuffer) | Uninitialized **FastBuffer** object.|

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitialized(10);
buf.fill(0);
// "buf":[0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
```

## fastbuffer.byteLength

byteLength(value: string | FastBuffer | TypedArray | DataView | ArrayBuffer | SharedArrayBuffer, encoding?: BufferEncoding): number

Returns the number of bytes of the specified content based on different encoding formats.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | string&nbsp;\|&nbsp;[FastBuffer](#fastbuffer)&nbsp;\|&nbsp;TypedArray&nbsp;\|&nbsp;DataView&nbsp;\|&nbsp;ArrayBuffer&nbsp;\|&nbsp;SharedArrayBuffer | Yes | Specifies the content used to calculate the byte length. |
| encoding | [BufferEncoding](#bufferencoding) | No | Encoding format (only meaningful when `value` is a string). Default value: 'utf8'. Passing an unrecognized encoding throws a TypeError. |

**Return value**

| Type| Description|
| -------- | -------- |
| number | Returns the number of bytes of the specified content. |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let str = 'hello world';
console.info(`${str}: ${str.length} characters, ${fastbuffer.byteLength(str, 'utf-8')} bytes`);
// Output: hello world: 11 characters, 11 bytes

str = '\u00bd + \u00bc = \u00be';
console.info(`${str}: ${str.length} characters, ${fastbuffer.byteLength(str, 'utf-8')} bytes`);
// Output: ½ + ¼ = ¾: 9 characters, 12 bytes
```

## fastbuffer.compare

compare(buf1: FastBuffer | Uint8Array, buf2: FastBuffer | Uint8Array): -1 | 0 | 1

Compares two **FastBuffer** objects. This API is used for sorting **FastBuffer** objects.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| buf1 | [FastBuffer](#fastbuffer)&nbsp;\|&nbsp;Uint8Array | Yes| First object to compare.|
| buf2 | [FastBuffer](#fastbuffer)&nbsp;\|&nbsp;Uint8Array | Yes| Second object to compare.|

**Return value**

| Type| Description|
| -------- | -------- |
| -1&nbsp;\|&nbsp;0&nbsp;\|&nbsp;1 | Returns **0** if **buf1** is the same as **buf2**.<br>Returns **1** if **buf1** comes after **buf2** when sorted.<br>Returns **-1** if **buf1** comes before **buf2** when sorted.|

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200068 | The underlying ArrayBuffer is null or detach. |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf1 = fastbuffer.from('1234');
let buf2 = fastbuffer.from('0123');
let compareResult = fastbuffer.compare(buf1, buf2);

console.info(Number(compareResult).toString());
// Output: 1
```

## fastbuffer.concat

concat(list: FastBuffer[] | Uint8Array[], totalLength?: number): FastBuffer

Copies and concatenates the content of the specified byte length in the array, and returns a new FastBuffer object.

If the total length of all objects in the array exceeds **totalLength**, the length of the returned result will be truncated to **totalLength**.

If the total length of all objects in the array is less than **totalLength**, the excess part of the returned result will be padded with zeros.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| list | [FastBuffer](#fastbuffer)[]&nbsp;\|&nbsp;Uint8Array[] | Yes | Array of FastBuffer or Uint8Array instances to be concatenated. The contents of all objects in the array are copied to the new FastBuffer object in sequence. |
| totalLength | number | No | Total byte length to copy. The default value is the sum of the lengths of all objects in the array. Value range: 0 <= totalLength <= UINT32_MAX. |

**Return value**

| Type| Description|
| -------- | -------- |
| [FastBuffer](#fastbuffer) | **FastBuffer** object created.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | Range error. Possible causes: The value of the parameter is not within the specified range. |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf1 = fastbuffer.from('1234');
let buf2 = fastbuffer.from('abcd');
let buf = fastbuffer.concat([buf1, buf2]);
console.info(buf.toString('hex'));
// Output: 3132333461626364
```

## fastbuffer.from

from(array: number[]): FastBuffer

Creates a **FastBuffer** object with the specified array.

**System capability**: SystemCapability.Utils.Lang

**Atomic service API**: This API can be used in atomic services since API version 20.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| array | number[] | Yes | Specified array. The value range of each element in the array is [0, 255]. |

**Return value**

| Type| Description|
| -------- | -------- |
| [FastBuffer](#fastbuffer) | **FastBuffer** object created.|

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0x62, 0x75, 0x66, 0x66, 0x65, 0x72]);
console.info(buf.toString('hex'));
// Output: 627566666572
```

## fastbuffer.from

from(arrayBuffer: ArrayBuffer | SharedArrayBuffer, byteOffset?: number, length?: number): FastBuffer

Creates a **FastBuffer** object of the specified length that shares memory with `ArrayBuffer`.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| arrayBuffer | ArrayBuffer&nbsp;\|&nbsp;SharedArrayBuffer | Yes | The underlying ArrayBuffer or SharedArrayBuffer used to create the FastBuffer object. The created FastBuffer shares the same memory area with this object. |
| byteOffset | number | No| Byte offset. The default value is **0**.|
| length | number | No | Byte length. Default value: (arrayBuffer.byteLength - byteOffset). Value range: 0 <= length <= arrayBuffer.byteLength - byteOffset. When null is passed, a FastBuffer object with length 0 is returned. |

**Return value**

| Type| Description|
| -------- | -------- |
| [FastBuffer](#fastbuffer) | Returns a FastBuffer object that shares the same memory area with the input parameter `arrayBuffer`. Modifying the data of the FastBuffer object will synchronously modify the data at the corresponding position in the original ArrayBuffer, and modifying the data of the original ArrayBuffer will also synchronously modify the data at the corresponding position in the FastBuffer. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | Range error. Possible causes: The value of the parameter is not within the specified range. |
| 10200068 | The underlying ArrayBuffer is null or detach. |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let arrayBuffer = new ArrayBuffer(10);
let buf = fastbuffer.from(arrayBuffer, 0, 2);
console.info(buf.length.toString());
// Output: 2
```

## fastbuffer.from

from(buffer: FastBuffer | Uint8Array): FastBuffer

When the input parameter is a **FastBuffer** object, a new **FastBuffer** object is created and the input data is copied. The data of the new and old objects are independent and do not affect each other.

When the input parameter is a **Uint8Array** object, a new **FastBuffer** object is created based on its memory. The two objects maintain memory association, and modifying the data of either object synchronously affects the other object.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| buffer | [FastBuffer](#fastbuffer)&nbsp;\|&nbsp;Uint8Array | Yes | Source data used to create a new FastBuffer object. When the input parameter is a FastBuffer, its data is copied to create a new object; when the input parameter is a Uint8Array, a new object is created based on its memory and the memory association is maintained. |

**Return value**

| Type| Description|
| -------- | -------- |
| [FastBuffer](#fastbuffer) | **FastBuffer** object created.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 10200068 | The underlying ArrayBuffer is null or detach. |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

// Create a FastBuffer object from a string.
let buf1 = fastbuffer.from('buffer');
// Create a new FastBuffer object with the FastBuffer object type.
let buf2 = fastbuffer.from(buf1);
console.info(buf2.toString());
// Output: buffer

// Create a FastBuffer object of the Uint8Array type to ensure memory sharing between objects.
let uint8Array = new Uint8Array(10);
let buf3 = fastbuffer.from(uint8Array);
// Modify buf3 to verify memory sharing: after buf3 is modified, uint8Array changes synchronously.
buf3.fill(1);
console.info('uint8Array:', uint8Array);
// Output: 1,1,1,1,1,1,1,1,1,1
```

## fastbuffer.from

from(value: string, encoding?: BufferEncoding): FastBuffer

Creates a **FastBuffer** object based on a string in the given encoding format.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | string | Yes | String used to create the FastBuffer object. |
| encoding | [BufferEncoding](#bufferencoding) | No| Encoding format. The default value is **'utf8'**. If an unrecognized encoding format is passed, TypeError is thrown.|

**Return value**

| Type| Description|
| -------- | -------- |
| [FastBuffer](#fastbuffer) | **FastBuffer** object created.|

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

// Create a FastBuffer object from a normal string.
let buf1 = fastbuffer.from('this is a test');
// Create a FastBuffer object from a hex-encoded string.
let buf2 = fastbuffer.from('7468697320697320612074c3a97374', 'hex');

console.info(buf1.toString());
// Output: this is a test
console.info(buf2.toString());
// Output: this is a tést
```

## fastbuffer.isBuffer

isBuffer(obj: Object): boolean

Checks whether the specified object is a **FastBuffer** object.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| obj | Object | Yes | Object to determine whether it is a FastBuffer. |

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Check result. The value **true** is returned if the object is a **FastBuffer** object; otherwise, **false** is returned.|

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let allocResult = fastbuffer.isBuffer(fastbuffer.alloc(10)); // 10: fastbuffer size
console.info('allocResult = ' + allocResult);
// Output result: allocResult = true
let fromResult = fastbuffer.isBuffer(fastbuffer.from('foo'));
console.info('fromResult = ' + fromResult);
// Output result: fromResult = true
let stringResult = fastbuffer.isBuffer('a string');
console.info('stringResult = ' + stringResult);
// Output result: stringResult = false
let arrayResult = fastbuffer.isBuffer([]);
console.info('arrayResult = ' + arrayResult);
// Output result: arrayResult = false
let uint8ArrayResult = fastbuffer.isBuffer(new Uint8Array(1024));
console.info('uint8ArrayResult = ' + uint8ArrayResult);
// Output result: uint8ArrayResult = false
```

## fastbuffer.isEncoding

isEncoding(encoding: string): boolean

Checks whether the encoding format is supported.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| encoding | string | Yes | Encoding format to be determined whether it is supported. |

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Check result. The value **true** is returned if the encoding format is supported; otherwise, **false** is returned.|

**Example**

```ts
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

## fastbuffer.transcode

transcode(source: FastBuffer | Uint8Array, fromEnc: string, toEnc: string): FastBuffer

Converts a **FastBuffer** or **Uint8Array** object from the fromEnc encoding to the toEnc encoding. It is applicable to scenarios where data needs to be converted between different encoding formats. For example, convert UTF-8 encoded data to Latin1 encoding for processing in systems that support only ASCII.

This API supports the following encoding formats: 'ascii', 'utf8', 'utf16le', 'ucs2', 'latin1', and 'binary'.

**System capability**: SystemCapability.Utils.Lang

**Atomic service API**: This API can be used in atomic services since API version 20.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| source | [FastBuffer](#fastbuffer)&nbsp;\|&nbsp;Uint8Array | Yes | Source data object that requires encoding conversion, which will be converted from the fromEnc encoding to the toEnc encoding. |
| fromEnc | string | Yes | Current encoding format. The supported format range is 'ascii' \| 'utf8' \| 'utf16le' \| 'ucs2' \| 'latin1' \| 'binary'. When an empty string is passed, the encoding format 'utf8' is used. |
| toEnc | string | Yes | Target encoding. The supported format range is 'ascii' \| 'utf8' \| 'utf16le' \| 'ucs2' \| 'latin1' \| 'binary'. |

**Return value**

| Type| Description|
| -------- | -------- |
| [FastBuffer](#fastbuffer) | New **FastBuffer** object in the target encoding format.|

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let newBuf = fastbuffer.transcode(fastbuffer.from('buffer'), 'utf-8', 'ascii');
console.info('newBuf = ' + newBuf.toString('ascii'));
// Output: newBuf = buffer
```

## FastBuffer

### Properties

**System capability**: SystemCapability.Utils.Lang

**Atomic service API**: This API can be used in atomic services since API version 20.

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| length | number | Yes| No| Length of the **FastBuffer** object, in bytes.|
| buffer | ArrayBuffer | Yes | No | The ArrayBuffer object corresponding to the underlying FastBuffer. |
| byteOffset | number | Yes | No | The offset of the underlying ArrayBuffer of the current FastBuffer. |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from('1236');
console.info(JSON.stringify(buf.length));
// Output: 4
let arrayBuffer = buf.buffer;
console.info(JSON.stringify(new Uint8Array(arrayBuffer)));
// Output: {"0":49,"1":50,"2":51,"3":54}
console.info(JSON.stringify(buf.byteOffset));
// Output: 0
```

### compare

compare(target: FastBuffer | Uint8Array, targetStart?: number, targetEnd?: number, sourceStart?: number, sourceEnd?: number): -1 | 0 | 1

Compares the current **this** object with the **target** object and returns the comparison result.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| target | [FastBuffer](#fastbuffer)&nbsp;\|&nbsp;Uint8Array | Yes| Target **FastBuffer** object to compare.|
| targetStart | number | No | Offset to start in the `target` instance. Default value: 0. Value range: 0 <= targetStart <= target.length. |
| targetEnd | number | No| Offset to the end of the data to compare in the target **FastBuffer** object (not inclusive). The default value is the length of the target **FastBuffer** object. Value range: 0 <= targetEnd <= target.length|
| sourceStart | number | No| Offset to the start of the data to compare in this **FastBuffer** object. The default value is **0**. Value range: 0 <= sourceStart <= this.length|
| sourceEnd | number | No| Offset to the end of the data to compare in this **FastBuffer** object (not inclusive). The default value is the length of this **FastBuffer** object. Value range: 0 <= sourceEnd <= this.length|

**Return value**

| Type| Description|
| -------- | -------- |
| -1 \| 0 \| 1 | Comparison result.<br>-1: This object comes before the target object when sorted.<br>0: The two objects are the same.<br>1: This object comes after the target object when sorted.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | Range error. Possible causes: The value of the parameter is not within the specified range. |
| 10200068 | The underlying ArrayBuffer is null or detach. |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf1 = fastbuffer.from([1, 2, 3, 4, 5, 6, 7, 8, 9]);
let buf2 = fastbuffer.from([5, 6, 7, 8, 9, 1, 2, 3, 4]);

// Compare buf1[0,4) with buf2[5,9). The result 0 indicates they are identical.
console.info(buf1.compare(buf2, 5, 9, 0, 4).toString());
// Output: 0
// Compare buf1[4,end) with buf2[0,6). The result -1 indicates buf1 comes first.
console.info(buf1.compare(buf2, 0, 6, 4).toString());
// Output: -1
// Compare buf1[5,end) with buf2[5,6). The result 1 indicates buf1 comes last.
console.info(buf1.compare(buf2, 5, 6, 5).toString());
// Output: 1
```

### copy

copy(target: FastBuffer| Uint8Array, targetStart?: number, sourceStart?: number, sourceEnd?: number): number

Copies data at the specified position in this **FastBuffer** object to the specified position in another **FastBuffer** object.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| target | [FastBuffer](#fastbuffer)&nbsp;\|&nbsp;Uint8Array | Yes| **FastBuffer** or **Uint8Array** object to which data is copied.|
| targetStart | number | No| Offset to the start position in the target object where data is copied. The default value is **0**. Value range: 0 <= targetStart <= UINT32_MAX|
| sourceStart | number | No | Offset in the `this` instance from which copying starts. Default value: 0. Value range: 0 <= sourceStart <= UINT32_MAX. |
| sourceEnd | number | No| Offset to the end position in this **FastBuffer** object (not inclusive). The default value is the length of this **FastBuffer** object. Value range: 0 <= sourceEnd <= this.length|

**Return value**

| Type| Description|
| -------- | -------- |
| number |  Total length of the data copied, in bytes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | Range error. Possible causes: The value of the parameter is not within the specified range. |
| 10200068 | The underlying ArrayBuffer is null or detach. |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

// Create an uninitialized FastBuffer object as the copy source.
let buf1 = fastbuffer.allocUninitializedFromPool(26);
// Create a FastBuffer object filled with '!' as the copy destination.
let buf2 = fastbuffer.allocUninitializedFromPool(26).fill('!');
// Write ASCII characters a-z to buf1.
for (let i = 0; i < 26; i++) {
  buf1.writeInt8(i + 97, i);
}
// Copy bytes 16 to 20 of buf1 to the position starting at byte 8 of buf2.
buf1.copy(buf2, 8, 16, 20);
console.info(buf2.toString('ascii', 0, 25));
// Output: !!!!!!!!qrst!!!!!!!!!!!!!
```

### entries

entries(): IterableIterator&lt;[number,&nbsp;number]&gt;

Returns an iterator containing key values and value values, where the key is the byte index position and the value is the byte value at that position.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| IterableIterator&lt;[number,&nbsp;number]&gt; |  Iterator that contains the key and value, both of which are of the number type.|

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

// Create a FastBuffer object.
let buf = fastbuffer.from('buffer');
// Obtain the entries iterator.
let entryIterator = buf.entries();
// Obtain the first element of the iterator.
let nextEntry: IteratorResult<[number, number]> = entryIterator.next();
// Iterate through the iterator to output each [key, value] pair.
while (!nextEntry.done) {
  console.info('fastbuffer: ' + nextEntry.value);
  /*
  Output result: fastbuffer: 0,98
           fastbuffer: 1,117
           fastbuffer: 2,102
           fastbuffer: 3,102
           fastbuffer: 4,101
           fastbuffer: 5,114
   */
  nextEntry = entryIterator.next();
}
```

### equals

equals(otherBuffer: Uint8Array | FastBuffer): boolean

Checks whether this **FastBuffer** object is the same as another **FastBuffer** object.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| otherBuffer | Uint8Array&nbsp;\|&nbsp;[FastBuffer](#fastbuffer) | Yes | Target object for comparison. |

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Check result. The value **true** is returned if the two objects are equal byte by byte; otherwise, **false** is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 10200068 | The underlying ArrayBuffer is null or detach. |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf1 = fastbuffer.from('ABC');
let buf2 = fastbuffer.from('414243', 'hex');
let buf3 = fastbuffer.from('ABCD');

console.info(buf1.equals(buf2).toString());
// Output: true
console.info(buf1.equals(buf3).toString());
// Output: false
```

### fill

fill(value: string | FastBuffer | Uint8Array | number, offset?: number, end?: number, encoding?: BufferEncoding): FastBuffer

Fills the data at the specified position of the current object with `value`. When the length of `value` is less than the range to be filled, `value` is repeated cyclically for filling, and the filled **FastBuffer** object is returned.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | string&nbsp;\|&nbsp;[FastBuffer](#fastbuffer)&nbsp;\|&nbsp;Uint8Array&nbsp;\|&nbsp;number | Yes | Value used for filling. |
| offset | number | No| Offset to the start position in this **FastBuffer** object where data is filled. The default value is **0**. Value range: 0 <= offset <= this.length|
| end | number | No| Offset to the end position in this **FastBuffer** object (not inclusive). The default value is the length of this **FastBuffer** object. Value range: 0 <= end <= this.length|
| encoding | [BufferEncoding](#bufferencoding) | No| Encoding format (valid only when **value** is a string). The default value is **'utf8'**. If an unrecognized encoding format is passed, TypeError is thrown.|

**Return value**

| Type| Description|
| -------- | -------- |
| [FastBuffer](#fastbuffer) | **FastBuffer** object filled with the specified value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | Range error. Possible causes: The value of the parameter is not within the specified range. |
| 10200068 | The underlying ArrayBuffer is null or detach. |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let filledBuffer = fastbuffer.allocUninitializedFromPool(50).fill('h');
console.info(filledBuffer.toString());
// Output: hhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhh
```

### includes

includes(value: string | number | FastBuffer | Uint8Array, byteOffset?: number, encoding?: BufferEncoding): boolean

Checks whether this **FastBuffer** object contains the specified value.

If **byteOffset** is a positive number, the offset is calculated from 0. If **byteOffset** is a negative number, the offset is calculated from the end.

If **byteOffset** is greater than or equal to **this.length**, **false** is returned. If **byteOffset** is less than or equal to **-this.length**, the system checks whether the value exists in the entire FastBuffer.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | string&nbsp;\|&nbsp;number&nbsp;\|&nbsp;[FastBuffer](#fastbuffer)&nbsp;\|&nbsp;Uint8Array | Yes | Content to search. |
| byteOffset | number | No | Byte offset. If byteOffset is positive, the offset is calculated from 0; if negative, it is calculated from the end. Default value: 0. |
| encoding | [BufferEncoding](#bufferencoding) | No | Character encoding format (only meaningful when `value` is a string). Default value: 'utf8'. Passing an unrecognized encoding throws a TypeError. |

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Check result. The value **true** is returned if the object contains the specified value; otherwise, **false** is returned.|

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from('this is a buffer');
console.info(buf.includes('this').toString());
// Output: true
console.info(buf.includes('be').toString());
// Output: false
```

### indexOf

indexOf(value: string | number | FastBuffer | Uint8Array, byteOffset?: number, encoding?: BufferEncoding): number

Obtains the index of the first occurrence of the specified value in this **FastBuffer** object. If no match is found, **-1** is returned.

If **byteOffset** is a positive number, the offset is calculated from 0. If **byteOffset** is a negative number, the offset is calculated from the end.

If **byteOffset** is greater than or equal to **this.length**, **-1** is returned. If **byteOffset** is less than or equal to **-this.length**, the index of the first occurrence of the specified value in the FastBuffer is returned.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | string&nbsp;\|&nbsp;number&nbsp;\|&nbsp;[FastBuffer](#fastbuffer)&nbsp;\|&nbsp;Uint8Array | Yes | Content to search. |
| byteOffset | number | No| Number of bytes to skip before starting to check data. If **byteOffset** is a positive number, the offset is calculated from 0. If **byteOffset** is a negative number, the offset is calculated from the end. The default value is **0**.|
| encoding | [BufferEncoding](#bufferencoding) | No | Character encoding format (meaningful only when `value` is a string). Default value: 'utf8'. Passing an unrecognized encoding throws a TypeError. |

**Return value**

| Type| Description|
| -------- | -------- |
| number | Returns the position of the first occurrence. If `value` is not contained, -1 is returned. |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from('this is a buffer');
console.info(buf.indexOf('this').toString());
// Output: 0
console.info(buf.indexOf('is').toString());
// Output: 2
```

### keys

keys(): IterableIterator&lt;number&gt;

Returns an iterator containing key values, where the key is the byte index position, ranging from 0 to length-1.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
|  IterableIterator&lt;number&gt; | Iterator created.|

**Example**

```ts
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

### values

values(): IterableIterator&lt;number&gt;

Returns an iterator containing the byte values of the **FastBuffer**.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| IterableIterator&lt;number&gt; | Iterator containing the value of each byte in the FastBuffer. |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf1 = fastbuffer.from('buffer');
let valueIterator = buf1.values();
let nextValue:IteratorResult<number> = valueIterator.next();
while (!nextValue.done) {
  console.info(nextValue.value.toString());
  /*
  Output result: 98
           117
           102
           102
           101
           114
   */
  nextValue = valueIterator.next();
}
```

### lastIndexOf

lastIndexOf(value: string | number | FastBuffer | Uint8Array, byteOffset?: number, encoding?: BufferEncoding): number

Obtains the index of the last occurrence of the specified value in this **FastBuffer** object. If no match is found, **-1** is returned.

If **byteOffset** is a positive number, the offset is calculated from 0. If **byteOffset** is a negative number, the offset is calculated from the end.

If **byteOffset** is greater than or equal to **this.length**, the index of the last occurrence of the specified value in the FastBuffer is returned. If **byteOffset** is less than or equal to **this.length**, **-1** is returned.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | string&nbsp;\|&nbsp;number&nbsp;\|&nbsp;[FastBuffer](#fastbuffer)&nbsp;\|&nbsp;Uint8Array | Yes | Content to search. |
| byteOffset | number | No| Number of bytes to skip before starting to check data. If **byteOffset** is a positive number, the offset is calculated from 0. If **byteOffset** is a negative number, the offset is calculated from the end. The default value is **this.length - 1**.|
| encoding | [BufferEncoding](#bufferencoding) | No | Character encoding format (only meaningful when `value` is a string). Default value: 'utf8'. Passing an unrecognized encoding throws a TypeError. |

**Return value**

| Type| Description|
| -------- | -------- |
| number | Index of the last occurrence of the `value`. If the object does not contain `value`, -1 is returned. |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from('this buffer is a buffer');
console.info(buf.lastIndexOf('this').toString());
// Output: 0
console.info(buf.lastIndexOf('buffer').toString());
// Output: 17
```

### readBigInt64BE

readBigInt64BE(offset?: number): bigint

Reads a 64-bit, big-endian, signed big integer from this **FastBuffer** object at the specified offset.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| offset | number | No| Offset. The default value is **0**. Value range: 0 <= offset <= this.length - 8|

**Return value**

| Type| Description|
| -------- | -------- |
| bigint | Data read.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 8. Received value is: [offset]. |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0x63, 0x64, 0x65, 0x66, 0x67, 0x68, 0x69, 0x70,
  0x71, 0x72, 0x73, 0x74, 0x75, 0x76, 0x77, 0x78]);
console.info(buf.readBigInt64BE(0).toString());
// Output: 7161960797921896816
```

### readBigInt64LE

readBigInt64LE(offset?: number): bigint

Reads a 64-bit, little-endian, signed big integer from this **FastBuffer** object at the specified offset.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| offset | number | No| Offset. The default value is **0**. Value range: 0 <= offset <= this.length - 8|

**Return value**

| Type| Description|
| -------- | -------- |
| bigint | Data read.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 8. Received value is: [offset]. |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0x63, 0x64, 0x65, 0x66, 0x67, 0x68, 0x69, 0x70,
  0x71, 0x72, 0x73, 0x74, 0x75, 0x76, 0x77, 0x78]);
console.info(buf.readBigInt64LE(0).toString());
// Output: 8100120198111388771
```

### readBigUInt64BE

readBigUInt64BE(offset?: number): bigint

Reads a 64-bit, big-endian, unsigned big integer from this **FastBuffer** object at the specified offset.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| offset | number | No| Offset. The default value is **0**. Value range: 0 <= offset <= this.length - 8|

**Return value**

| Type| Description|
| -------- | -------- |
| bigint | Data read.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 8. Received value is: [offset]. |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0x63, 0x64, 0x65, 0x66, 0x67, 0x68, 0x69, 0x70,
  0x71, 0x72, 0x73, 0x74, 0x75, 0x76, 0x77, 0x78]);
console.info(buf.readBigUInt64BE(0).toString());
// Output: 7161960797921896816
```

### readBigUInt64LE

readBigUInt64LE(offset?: number): bigint

Reads a 64-bit, little-endian, unsigned big integer from this **FastBuffer** object at the specified offset.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| offset | number | No| Offset. The default value is **0**. Value range: 0 <= offset <= this.length - 8|

**Return value**

| Type| Description|
| -------- | -------- |
| bigint | Data read.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 8. Received value is: [offset]. |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0x63, 0x64, 0x65, 0x66, 0x67, 0x68, 0x69, 0x70,
  0x71, 0x72, 0x73, 0x74, 0x75, 0x76, 0x77, 0x78]);
console.info(buf.readBigUInt64LE(0).toString());
// Output: 8100120198111388771
```

### readDoubleBE

readDoubleBE(offset?: number): number

Reads a 64-bit, big-endian, double-precision floating-point number from this **FastBuffer** object at the specified offset.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| offset | number | No| Offset. The default value is **0**. Value range: 0 <= offset <= this.length - 8|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Data read.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 8. Received value is: [offset]. |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([1, 2, 3, 4, 5, 6, 7, 8]);
console.info(buf.readDoubleBE(0).toString());
// Output: 8.20788039913184e-304
```

### readDoubleLE

readDoubleLE(offset?: number): number

Reads a 64-bit, little-endian, double-precision floating-point number from this **FastBuffer** object at the specified offset.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| offset | number | No| Offset. The default value is **0**. Value range: 0 <= offset <= this.length - 8|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Data read.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 8. Received value is: [offset]. |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([1, 2, 3, 4, 5, 6, 7, 8]);
console.info(buf.readDoubleLE(0).toString());
// Output: 5.447603722011605e-270
```

### readFloatBE

readFloatBE(offset?: number): number

Reads a 32-bit, big-endian, single-precision floating-point number from this **FastBuffer** object at the specified offset.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| offset | number | No| Offset. The default value is **0**. Value range: 0 <= offset <= this.length - 4|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Data read.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 4. Received value is: [offset]. |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([1, 2, 3, 4, 5, 6, 7, 8]);
console.info(buf.readFloatBE(0).toString());
// Output: 2.387939260590663e-38
```

### readFloatLE

readFloatLE(offset?: number): number

Reads a 32-bit, little-endian, single-precision floating-point number from this **FastBuffer** object at the specified offset.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| offset | number | No| Offset. The default value is **0**. Value range: 0 <= offset <= this.length - 4|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Data read.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 4. Received value is: [offset]. |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([1, 2, 3, 4, 5, 6, 7, 8]);
console.info(buf.readFloatLE(0).toString());
// Output: 1.539989614439558e-36
```

### readInt8

readInt8(offset?: number): number

Reads an 8-bit signed integer from this **FastBuffer** object at the specified offset.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| offset | number | No| Offset. The default value is **0**. Value range: 0 <= offset <= this.length - 1|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Data read.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 1. Received value is: [offset]. |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([-1, 5]);
console.info(buf.readInt8(0).toString());
// Output: -1
console.info(buf.readInt8(1).toString());
// Output: 5
```

### readInt16BE

readInt16BE(offset?: number): number

Reads a 16-bit, big-endian, signed integer from this **FastBuffer** object at the specified offset.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| offset | number | No| Offset. The default value is **0**. Value range: 0 <= offset <= this.length - 2|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Data read.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 2. Received value is: [offset]. |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0, 5]);
console.info(buf.readInt16BE(0).toString());
// Output: 5
```

### readInt16LE

readInt16LE(offset?: number): number

Reads a 16-bit, little-endian, signed integer from this **FastBuffer** object at the specified offset.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| offset | number | No| Offset. The default value is **0**. Value range: 0 <= offset <= this.length - 2|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Data read.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 2. Received value is: [offset]. |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0, 5]);
console.info(buf.readInt16LE(0).toString());
// Output: 1280
```

### readInt32BE

readInt32BE(offset?: number): number

Reads a 32-bit, big-endian, signed integer from this **FastBuffer** object at the specified offset.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| offset | number | No| Offset. The default value is **0**. Value range: 0 <= offset <= this.length - 4|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Data read.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 4. Received value is: [offset]. |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0, 0, 0, 5]);
console.info(buf.readInt32BE(0).toString());
// Output: 5
```

### readInt32LE

readInt32LE(offset?: number): number

Reads a 32-bit, little-endian, signed integer from this **FastBuffer** object at the specified offset.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| offset | number | No| Offset. The default value is **0**. Value range: 0 <= offset <= this.length - 4|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Data read.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 |  The value of "offset" is out of range. It must be >= 0 and <= buf.length - 4. Received value is: [offset]. |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0, 0, 0, 5]);
console.info(buf.readInt32LE(0).toString());
// Output: 83886080
```

### readIntBE

readIntBE(offset: number, byteLength: number): number

Reads the specified number of bytes from this **FastBuffer** object at the specified offset, and interprets the result as a big-endian, two's complement signed value that supports up to 48 bits of precision.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| offset | number | Yes| Offset. The default value is **0**. Value range: 0 <= offset <= this.length - byteLength|
| byteLength | number | Yes| Number of bytes to read. Value range: 1 <= byteLength <= 6|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Data read.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from('ab');
let num = buf.readIntBE(0, 1);
console.info(num.toString());
// Output: 97
```

### readIntLE

readIntLE(offset: number, byteLength: number): number

Reads the specified number of bytes from this **FastBuffer** object at the specified offset and interprets the result as a little-endian, two's complement signed value that supports up to 48 bits of precision.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| offset | number | Yes| Offset. The default value is **0**. Value range: 0 <= offset <= this.length - byteLength|
| byteLength | number | Yes| Number of bytes to read. Value range: 1 <= byteLength <= 6|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Data read.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0x12, 0x34, 0x56, 0x78, 0x90, 0xab]);
console.info(buf.readIntLE(0, 6).toString(16));
// Output: -546f87a9cbee
```

### readUInt8

readUInt8(offset?: number): number

Reads an 8-bit unsigned integer from the specified `offset`.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| offset | number | No| Offset. The default value is **0**. Value range: 0 <= offset <= this.length - 1|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Data read.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 1. Received value is: [offset]. |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([1, -2]);
console.info(buf.readUInt8(0).toString());
// Output: 1
console.info(buf.readUInt8(1).toString());
// Output: 254
```

### readUInt16BE

readUInt16BE(offset?: number): number

Reads a 16-bit, big-endian, unsigned integer from this **FastBuffer** object at the specified offset.

**System capability**: SystemCapability.Utils.Lang

**Atomic service API**: This API can be used in atomic services since API version 20.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| offset | number | No| Offset. The default value is **0**. Value range: 0 <= offset <= this.length - 2|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Data read.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 2. Received value is: [offset]. |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0x12, 0x34, 0x56]);
console.info(buf.readUInt16BE(0).toString(16));
// Output: 1234
console.info(buf.readUInt16BE(1).toString(16));
// Output: 3456
```

### readUInt16LE

readUInt16LE(offset?: number): number

Reads an unsigned little-endian 16-bit integer from the specified `offset`.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| offset | number | No| Offset. The default value is **0**. Value range: 0 <= offset <= this.length - 2|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Data read.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 2. Received value is: [offset]. |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0x12, 0x34, 0x56]);
console.info(buf.readUInt16LE(0).toString(16));
// Output: 3412
console.info(buf.readUInt16LE(1).toString(16));
// Output: 5634
```

### readUInt32BE

readUInt32BE(offset?: number): number

Reads an unsigned big-endian 32-bit integer from the specified `offset`.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| offset | number | No| Offset. The default value is **0**. Value range: 0 <= offset <= this.length - 4|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Data read.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 4. Received value is: [offset]. |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0x12, 0x34, 0x56, 0x78]);
console.info(buf.readUInt32BE(0).toString(16));
// Output: 12345678
```

### readUInt32LE

readUInt32LE(offset?: number): number

Reads an unsigned, little-endian 32-bit integer from the specified `offset`.

**System capability**: SystemCapability.Utils.Lang

**Atomic service API**: This API can be used in atomic services since API version 20.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| offset | number | No| Offset. The default value is **0**. Value range: 0 <= offset <= this.length - 4|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Data read.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 4. Received value is: [offset]. |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0x12, 0x34, 0x56, 0x78]);
console.info(buf.readUInt32LE(0).toString(16));
// Output: 78563412
```

### readUIntBE

readUIntBE(offset: number, byteLength: number): number

Reads `byteLength` bytes from the specified `offset` and interprets the result as an unsigned, big-endian integer with up to 48 bits of precision.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| offset | number | Yes | Offset. Value range: 0 <= offset <= this.length - byteLength. |
| byteLength | number | Yes | Number of bytes to read. Value range: 1 <= byteLength <= 6. |

**Return value**

| Type| Description|
| -------- | -------- |
| number | Data read. If the offset is a decimal, undefined is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0x12, 0x34, 0x56, 0x78, 0x90, 0xab]);
console.info(buf.readUIntBE(0, 6).toString(16));
// Output: 1234567890ab
```

### readUIntLE

readUIntLE(offset: number, byteLength: number): number

Reads `byteLength` bytes from the specified `offset` and interprets the result as an unsigned, little-endian integer with up to 48 bits of precision.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| offset | number | Yes | Offset. Value range: 0 <= offset <= this.length - byteLength. |
| byteLength | number | Yes| Number of bytes to read. Value range: 1 <= byteLength <= 6|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Data read. If the offset is a decimal, undefined is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0x12, 0x34, 0x56, 0x78, 0x90, 0xab]);
console.info(buf.readUIntLE(0, 6).toString(16));
// Output: ab9078563412
```

### subarray

subarray(start?: number, end?: number): FastBuffer

Extracts and returns the data at the specified position of the current object. The returned FastBuffer object shares the same memory area as the original object, and modifying the data of either object affects the other.

**System capability**: SystemCapability.Utils.Lang

**Atomic service API**: This API can be used in atomic services since API version 20.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| start | number | No| Offset to the start position in this **FastBuffer** object where data is truncated. The default value is **0**.|
| end | number | No | End position of the interception (excluding the end position). Default value: byte length of the current object. Value range: start <= end <= this.length. When null is passed in, a FastBuffer object with a length of 0 is returned. |

**Return value**

| Type| Description|
| -------- | -------- |
| FastBuffer | **FastBuffer** object created.|

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf1 = fastbuffer.allocUninitializedFromPool(26);

for (let i = 0; i < 26; i++) {
  buf1.writeInt8(i + 97, i);
}
const buf2 = buf1.subarray(0, 3);
console.info(buf2.toString('ascii', 0, buf2.length));
// Output: abc
```

### swap16

swap16(): FastBuffer

Swaps the byte order of the current object in units of 16-bit unsigned integers.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| FastBuffer | **FastBuffer** object swapped.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200009 | The fastbuffer size must be a multiple of 16-bits. |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf1 = fastbuffer.from([0x1, 0x2, 0x3, 0x4, 0x5, 0x6, 0x7, 0x8]);
console.info(buf1.toString('hex'));
// Output: 0102030405060708
buf1.swap16();
console.info(buf1.toString('hex'));
// Output: 0201040306050807
```

### swap32

swap32(): FastBuffer

Converts this **FastBuffer** object into an array of unsigned 32-bit integers and swaps the byte order in place.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| FastBuffer | **FastBuffer** object swapped.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200009 | The fastbuffer size must be a multiple of 32-bits. |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf1 = fastbuffer.from([0x1, 0x2, 0x3, 0x4, 0x5, 0x6, 0x7, 0x8]);
console.info(buf1.toString('hex'));
// Output: 0102030405060708
buf1.swap32();
console.info(buf1.toString('hex'));
// Output: 0403020108070605
```

### swap64

swap64(): FastBuffer

Converts this **FastBuffer** object into an array of unsigned 64-bit integers and swaps the byte order in place.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| FastBuffer | **FastBuffer** object swapped.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200009 | The fastbuffer size must be a multiple of 64-bits. |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf1 = fastbuffer.from([0x1, 0x2, 0x3, 0x4, 0x5, 0x6, 0x7, 0x8]);
console.info(buf1.toString('hex'));
// Output: 0102030405060708
buf1.swap64();
console.info(buf1.toString('hex'));
// Output: 0807060504030201
```

### toJSON

toJSON(): Object

Converts the FastBuffer to JSON and returns it.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| Object | JSON object.|

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf1 = fastbuffer.from([0x1, 0x2, 0x3, 0x4, 0x5]);
let jsonResult = buf1.toJSON();
console.info(JSON.stringify(jsonResult));
// Output: {"type":"FastBuffer","data":[1,2,3,4,5]}
```

### toString

toString(encoding?: string, start?: number, end?: number): string

Converts the data at the specified position in this **FastBuffer** object into a string in the specified encoding format.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| encoding | string | No | Character encoding format. For the supported format range, see [BufferEncoding](#bufferencoding). Default value: 'utf8'. |
| start  | number | No|  Offset to the start position of the data to convert. The default value is **0**.|
| end  | number | No |  End position. Default value: this.length. |

**Return value**

| Type| Description|
| -------- | -------- |
| string | String. When the value of **start** is greater than or equal to **this.length** or **start** is greater than **end**, an empty string is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 10200068 | The underlying ArrayBuffer is null or detach. |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf1 = fastbuffer.allocUninitializedFromPool(26);
for (let i = 0; i < 26; i++) {
  buf1.writeInt8(i + 97, i);
}
console.info(buf1.toString('utf-8'));
// Output: abcdefghijklmnopqrstuvwxyz
```

### write

write(str: string, offset?: number, length?: number, encoding?: string): number

Writes a string in the specified encoding at the `offset` of the FastBuffer object. The maximum number of bytes written is `length`, and the actual number of bytes written depends on the number of bytes after the string is encoded.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| str | string | Yes | String to write to the FastBuffer. |
| offset | number | No| Offset. The default value is **0**.|
| length | number | No| Maximum number of bytes to write. The default value is **this.length - offset**.|
| encoding | string | No | Character encoding format. For the supported format range, see [BufferEncoding](#bufferencoding). Default value: 'utf8'. |

**Return value**

| Type| Description|
| -------- | -------- |
| number | Number of bytes written.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | Range error. Possible causes: The value of the parameter is not within the specified range. |
| 10200068 | The underlying ArrayBuffer is null or detach. |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.alloc(256);
let bytesWritten = buf.write('\u00bd + \u00bc = \u00be', 0);
console.info(`${bytesWritten} bytes: ${buf.toString('utf-8', 0, bytesWritten)}`);
// Output: 12 bytes: ½ + ¼ = ¾

let buf1 = fastbuffer.alloc(10);
let length = buf1.write('abcd', 8);
console.info('length = ' + length);
// Output: length = 2
```

### writeBigInt64BE

writeBigInt64BE(value: bigint, offset?: number): number

Writes a 64-bit, big-endian, signed big integer to this **FastBuffer** object at the specified offset.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | bigint | Yes | Data to write to FastBuffer. Value range: -INT64_MAX <= value <= INT64_MAX. |
| offset | number | No| Offset. The default value is **0**. Value range: 0 <= offset <= this.length - 8|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Offset plus the number of written bytes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(8);
let result = buf.writeBigInt64BE(BigInt(0x0102030405060708), 0);
console.info('result = ' + result);
// Output: result = 8
```

### writeBigInt64LE

writeBigInt64LE(value: bigint, offset?: number): number

Writes a 64-bit, little-endian, signed big integer to this **FastBuffer** object at the specified offset.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | bigint | Yes | Data to write to the FastBuffer. Value range: -INT64_MAX <= value <= INT64_MAX. |
| offset | number | No| Offset. The default value is **0**. Value range: 0 <= offset <= this.length - 8|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Offset plus the number of written bytes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(8);
let result = buf.writeBigInt64LE(BigInt(0x0102030405060708), 0);
console.info('result = ' + result);
// Output: result = 8
```

### writeBigUInt64BE

writeBigUInt64BE(value: bigint, offset?: number): number

Writes unsigned, big-endian 64-bit BigUInt data at the `offset` of the FastBuffer object.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | bigint | Yes | Data to write to the FastBuffer. Value range: 0 <= value <= UINT64_MAX. |
| offset | number | No| Offset. The default value is **0**. Value range: 0 <= offset <= this.length - 8|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Offset plus the number of written bytes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(8);
let result = buf.writeBigUInt64BE(BigInt(0xdecafafecacefade), 0);
console.info('result = ' + result);
// Output: result = 8
```

### writeBigUInt64LE

writeBigUInt64LE(value: bigint, offset?: number): number

Writes a 64-bit, little-endian, unsigned big integer to this **FastBuffer** object at the specified offset.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| value | bigint | Yes | Data to write to the FastBuffer. Value range: 0 <= value <= UINT64_MAX. |
| offset | number | No | Offset. Default value: 0. Value range: 0 <= offset <= this.length - 8. |

**Return value**

| Type| Description|
| -------- | -------- |
| number | Offset plus the number of written bytes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(8);
let result = buf.writeBigUInt64LE(BigInt(0xdecafafecacefade), 0);
console.info('result = ' + result);
// Output: result = 8
```

### writeDoubleBE

writeDoubleBE(value: number, offset?: number): number

Writes a 64-bit, big-endian, double-precision floating-point number to this **FastBuffer** object at the specified offset.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | number | Yes | Data to write to the FastBuffer. Value range: -DOUBLE_MAX <= value <= DOUBLE_MAX. |
| offset | number | No| Offset. The default value is **0**. Value range: 0 <= offset <= this.length - 8|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Offset plus the number of written bytes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 8. Received value is: [offset] |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(8);
let result = buf.writeDoubleBE(123.456, 0);
console.info('result = ' + result);
// Output: result = 8
```

### writeDoubleLE

writeDoubleLE(value: number, offset?: number): number

Writes a 64-bit, little-endian, double-precision floating-point number to this **FastBuffer** object at the specified offset.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | number | Yes | Data to write to the FastBuffer. Value range: -DOUBLE_MAX <= value <= DOUBLE_MAX. |
| offset | number | No| Offset. The default value is **0**. Value range: 0 <= offset <= this.length - 8|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Offset plus the number of written bytes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 8. Received value is: [offset] |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(8);
let result = buf.writeDoubleLE(123.456, 0);
console.info('result = ' + result);
// Output: result = 8
```

### writeFloatBE

writeFloatBE(value: number, offset?: number): number

Writes a 32-bit, big-endian, single-precision floating-point number to this **FastBuffer** object at the specified offset.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | number | Yes | Data to write to the FastBuffer. Value range: -FLOAT_MAX <= value <= FLOAT_MAX. |
| offset | number | No| Offset. The default value is **0**. Value range: 0 <= offset <= this.length - 4|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Offset plus the number of written bytes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 4. Received value is: [offset] |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(8);
let result = buf.writeFloatBE(3.1415, 0);
console.info('result = ' + result);
// Output: result = 4
```

### writeFloatLE

writeFloatLE(value: number, offset?: number): number

Writes a 32-bit, little-endian, single-precision floating-point number to this **FastBuffer** object at the specified offset.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | number | Yes | Data to write to the FastBuffer. Value range: -FLOAT_MAX <= value <= FLOAT_MAX. |
| offset | number | No| Offset. The default value is **0**. Value range: 0 <= offset <= this.length - 4|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Offset plus the number of written bytes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "offset" is out of range. It must be >= 0 and <= buf.length - 4. Received value is: [offset] |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(8);
let result = buf.writeFloatLE(3.1415, 0);
console.info('result = ' + result);
// Output: result = 4
```

### writeInt8

writeInt8(value: number, offset?: number): number

Writes an 8-bit signed integer to this **FastBuffer** object at the specified offset.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | number | Yes | Data to write to the FastBuffer. Value range: -INT8_MAX <= value <= INT8_MAX. |
| offset | number | No| Offset. The default value is **0**. Value range: 0 <= offset <= this.length - 1|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Offset plus the number of written bytes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(2);
let result = buf.writeInt8(2, 0);
console.info('result = ' + result);
// Output: result = 1
let result1 = buf.writeInt8(-2, 1);
console.info('result1 = ' + result1);
// Output: result1 = 2
```

### writeInt16BE

writeInt16BE(value: number, offset?: number): number

Writes a 16-bit, big-endian, signed integer to this **FastBuffer** object at the specified offset.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | number | Yes | Data to write to the FastBuffer. Value range: -INT16_MAX <= value <= INT16_MAX. |
| offset | number | No| Offset. The default value is **0**. Value range: 0 <= offset <= this.length - 2|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Offset plus the number of written bytes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(2);
let result = buf.writeInt16BE(0x0102, 0);
console.info('result = ' + result);
// Output: result = 2
```

### writeInt16LE

writeInt16LE(value: number, offset?: number): number

Writes a 16-bit, little-endian, signed integer to this **FastBuffer** object at the specified offset.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | number | Yes | Data to write to the FastBuffer. Value range: -INT16_MAX <= value <= INT16_MAX. |
| offset | number | No| Offset. The default value is **0**. Value range: 0 <= offset <= this.length - 2|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Offset plus the number of written bytes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(2);
let result = buf.writeInt16LE(0x0304, 0);
console.info('result = ' + result);
// Output: result = 2
```

### writeInt32BE

writeInt32BE(value: number, offset?: number): number

Writes a 32-bit, big-endian, signed integer to this **FastBuffer** object at the specified offset.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | number | Yes | Data to write to the FastBuffer. Value range: -INT32_MAX <= value <= INT32_MAX. |
| offset | number | No| Offset. The default value is **0**. Value range: 0 <= offset <= this.length - 4|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Offset plus the number of written bytes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(4);
let result = buf.writeInt32BE(0x01020304, 0);
console.info('result = ' + result);
// Output: result = 4
```

### writeInt32LE

writeInt32LE(value: number, offset?: number): number

Writes a 32-bit, little-endian, signed integer to this **FastBuffer** object at the specified offset.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | number | Yes | Data to write to the FastBuffer. Value range: -INT32_MAX <= value <= INT32_MAX. |
| offset | number | No| Offset. The default value is **0**. Value range: 0 <= offset <= this.length - 4|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Offset plus the number of written bytes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(4);
let result = buf.writeInt32LE(0x05060708, 0);
console.info('result = ' + result);
// Output: result = 4
```

### writeIntBE

writeIntBE(value: number, offset: number, byteLength: number): number

Writes a big-endian signed value of the specified length to this **FastBuffer** object at the specified offset.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | number | Yes | Data to write to the FastBuffer. Value range: -2^(8×byteLength-1) ≤ value ≤ 2^(8×byteLength-1)-1. |
| offset | number | Yes | Offset. Default value: 0. Value range: 0 <= offset <= this.length - byteLength. When null or undefined is passed in, the offset is 0. |
| byteLength | number | Yes | Number of bytes to write. Value range: 1 <= byteLength <= 6. |

**Return value**

| Type| Description|
| -------- | -------- |
| number | Offset plus the number of written bytes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(6);
let result = buf.writeIntBE(0x1234567890ab, 0, 6);
console.info('result = ' + result);
// Output: result = 6
```

### writeIntLE

writeIntLE(value: number, offset: number, byteLength: number): number

Writes a little-endian signed value of the specified length to this **FastBuffer** object at the specified offset.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | number | Yes | Data to write to the FastBuffer. Value range: -2^(8×byteLength-1) ≤ value ≤ 2^(8×byteLength-1)-1. |
| offset | number | Yes | Offset. Default value: 0. Value range: 0 <= offset <= this.length - byteLength. When null or undefined is passed in, the offset is 0. |
| byteLength | number | Yes | Number of bytes to write. Value range: 1 <= byteLength <= 6. |

**Return value**

| Type| Description|
| -------- | -------- |
| number | Offset plus the number of written bytes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(6);
let result = buf.writeIntLE(0x1234567890ab, 0, 6);
console.info('result = ' + result);
// Output: result = 6
```

### writeUInt8

writeUInt8(value: number, offset?: number): number

Writes an 8-bit unsigned integer to this **FastBuffer** object at the specified offset.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | number | Yes | Data to write to the FastBuffer. Value range: 0 <= value <= UINT8_MAX. |
| offset | number | No| Offset. The default value is **0**. Value range: 0 <= offset <= this.length - 1|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Offset plus the number of written bytes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(4);
let result = buf.writeUInt8(0x3, 0);
console.info('result = ' + result);
// Output: result = 1
let result1 = buf.writeUInt8(0x4, 1);
console.info('result1 = ' + result1);
// Output: result1 = 2
let result2 = buf.writeUInt8(0x23, 2);
console.info('result2 = ' + result2);
// Output: result2 = 3
let result3 = buf.writeUInt8(0x42, 3);
console.info('result3 = ' + result3);
// Output: result3 = 4
```

### writeUInt16BE

writeUInt16BE(value: number, offset?: number): number

Writes a 16-bit, big-endian, unsigned integer to this **FastBuffer** object at the specified offset.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | number | Yes | Data to write to the FastBuffer. Value range: 0 <= value <= UINT16_MAX. |
| offset | number | No | Offset. Default value: 0. Value range: 0 <= offset <= this.length - 2. |

**Return value**

| Type| Description|
| -------- | -------- |
| number | Offset plus the number of written bytes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(4);
let result = buf.writeUInt16BE(0xdead, 0);
console.info('result = ' + result);
// Output: result = 2
let result1 = buf.writeUInt16BE(0xbeef, 2);
console.info('result1 = ' + result1);
// Output: result1 = 4
```

### writeUInt16LE

writeUInt16LE(value: number, offset?: number): number

Writes a 16-bit, little-endian, unsigned integer to this **FastBuffer** object at the specified offset.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | number | Yes | Data to write to the FastBuffer. Value range: 0 <= value <= UINT16_MAX. |
| offset | number | No| Offset. The default value is **0**. Value range: 0 <= offset <= this.length - 2|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Offset plus the number of written bytes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(4);
let result = buf.writeUInt16LE(0xdead, 0);
console.info('result = ' + result);
// Output: result = 2
let result1 = buf.writeUInt16LE(0xbeef, 2);
console.info('result1 = ' + result1);
// Output: result1 = 4
```

### writeUInt32BE

writeUInt32BE(value: number, offset?: number): number

Writes a 32-bit, big-endian, unsigned integer to this **FastBuffer** object at the specified offset.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | number | Yes | Data to write to the FastBuffer. Value range: 0 <= value <= UINT32_MAX. |
| offset | number | No| Offset. The default value is **0**. Value range: 0 <= offset <= this.length - 4|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Offset plus the number of written bytes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(4);
let result = buf.writeUInt32BE(0xfeedface, 0);
console.info('result = ' + result);
// Output: result = 4
```

### writeUInt32LE

writeUInt32LE(value: number, offset?: number): number

Writes a 32-bit, little-endian, unsigned integer to this **FastBuffer** object at the specified offset.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | number | Yes | Data to write to the FastBuffer. Value range: 0 <= value <= UINT32_MAX. |
| offset | number | No| Offset. The default value is **0**. Value range: 0 <= offset <= this.length - 4|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Offset plus the number of written bytes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(4);
let result = buf.writeUInt32LE(0xfeedface, 0);
console.info('result = ' + result);
// Output: result = 4
```

### writeUIntBE

writeUIntBE(value: number, offset: number, byteLength: number): number

Writes an unsigned big-endian value of the specified length to this **FastBuffer** object at the specified offset.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | number | Yes | Data to write to the FastBuffer. Value range: 0 ≤ value ≤ 2^(8×byteLength)-1. |
| offset | number | Yes | Offset. Default value: 0. Value range: 0 <= offset <= this.length - byteLength. When null or undefined is passed in, the offset is 0. |
| byteLength | number | Yes | Number of bytes to write. Value range: 1 <= byteLength <= 6. |

**Return value**

| Type| Description|
| -------- | -------- |
| number | Offset plus the number of written bytes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(6);
let result = buf.writeUIntBE(0x1234567890ab, 0, 6);
console.info('result = ' + result);
// Output: result = 6
```

### writeUIntLE

writeUIntLE(value: number, offset: number, byteLength: number): number

Writes an unsigned little-endian value of the specified length to this **FastBuffer** object at the specified offset.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | number | Yes | Data to write to the FastBuffer. Value range: 0 ≤ value ≤ 2^(8×byteLength)-1. |
| offset | number | Yes | Offset. Default value: 0. Value range: 0 <= offset <= this.length - byteLength. When null or undefined is passed in, the offset is 0. |
| byteLength | number | Yes | Number of bytes to write. Value range: 1 <= byteLength <= 6. |

**Return value**

| Type| Description|
| -------- | -------- |
| number | Offset plus the number of written bytes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "[param]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [param] |

**Example**

```ts
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(6);
let result = buf.writeUIntLE(0x1234567890ab, 0, 6);
console.info('result = ' + result);
// Output: result = 6
```