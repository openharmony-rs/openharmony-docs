# from

## Modules to Import

```TypeScript
import { buffer } from '@kit.ArkTS';
```

## from

```TypeScript
function from(array: number[]): Buffer
```

Creates a **Buffer** object with the specified array.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| array | number[] | Yes | Array to create a **Buffer** object. |

**Return value:**

| Type | Description |
| --- | --- |
| Buffer | **Buffer** object created. |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0x62, 0x75, 0x66, 0x66, 0x65, 0x72]);
console.info(buf.toString('hex'));
// Output: 627566666572
```

```TypeScript
import { buffer, JSON } from '@kit.ArkTS';

let ab = new ArrayBuffer(10);
let buf = buffer.from(ab, 0, 2);
console.info(JSON.stringify(buf)); // {"type":"Buffer","data":[0,0]}
```

```TypeScript
import { buffer } from '@kit.ArkTS';

// Create a Buffer object of the Buffer type.
let buf1 = buffer.from('buffer');
let buf2 = buffer.from(buf1);

// Create a Buffer object of the Uint8Array type to ensure memory sharing between objects.
let uint8Array = new Uint8Array(10);
let buf3 = buffer.from(uint8Array);
buf3.fill(1);
console.info("uint8Array:", uint8Array);
// Output: 1,1,1,1,1,1,1,1,1,1
```

```TypeScript
import { buffer, JSON } from '@kit.ArkTS';

let buf = buffer.from(new String('this is a test'), 'utf8', 14);
console.info(JSON.stringify(buf)); // {"type":"Buffer","data":[116,104,105,115,32,105,115,32,97,32,116,101,115,116]}
```

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.from('this is a test');
let buf2 = buffer.from('7468697320697320612074c3a97374', 'hex');

console.info(buf1.toString());
// Output: this is a test
console.info(buf2.toString());
// Output: this is a tést
```


## from

```TypeScript
function from(arrayBuffer: ArrayBuffer | SharedArrayBuffer, byteOffset?: number, length?: number): Buffer
```

Creates a **Buffer** object of the specified length that shares memory with ArrayBuffer.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| arrayBuffer | ArrayBuffer &#124; SharedArrayBuffer | Yes | **ArrayBuffer** or **SharedArrayBuffer** object whose memory is to be shared. |
| byteOffset | number | No | Byte offset. The default value is **0**. |
| length | number | No | Length of the **Buffer** object to create, in bytes. The default value is **arrayBuffer.byteLength** minus **byteOffset**. |

**Return value:**

| Type | Description |
| --- | --- |
| Buffer | **Buffer** object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "[byteOffset/length]" is out of range. It must be &gt;= [left range] and &lt;= [right range]. Received value is: [byteOffset/length] |

**Examples**

See [from](#from)


## from

```TypeScript
function from(buffer: Buffer | Uint8Array): Buffer
```

Copies the data of a passed **Buffer** object to create a new **Buffer** object and returns the new one. Creates a **Buffer** object based on the memory of a passed **Uint8Array** object and returns the new object, maintaining the memory association of the data.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| buffer | Buffer &#124; Uint8Array | Yes | Target object. |

**Return value:**

| Type | Description |
| --- | --- |
| Buffer | **Buffer** object created. |

**Examples**

See [from](#from)


## from

```TypeScript
function from(object: Object, offsetOrEncoding: number | string, length: number): Buffer
```

Creates a **Buffer** object based on the specified object.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| object | Object | Yes | Object that supports **Symbol.toPrimitive** or **valueOf()**. |
| offsetOrEncoding | number &#124; string | Yes | Byte offset or encoding format. |
| length | number | Yes | Length of the **Buffer** object to create, in bytes. This parameter is valid only when the return value of **valueOf()** of **object** is **ArrayBuffer**. Value range: 0 &lt;= length &lt;= ArrayBuffer.byteLength. Error 10200001 is reported if a value outside this range is reported. In other cases, you can set this parameter to any value of the number type. This parameter does not affect the result. |

**Return value:**

| Type | Description |
| --- | --- |
| Buffer | **Buffer** object created. |

**Examples**

See [from](#from)


## from

```TypeScript
function from(string: String, encoding?: BufferEncoding): Buffer
```

Creates a **Buffer** object based on a string in the given encoding format.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| string | String | Yes | String. |
| encoding | BufferEncoding | No | Encoding format. The default value is **'utf8'**. |

**Return value:**

| Type | Description |
| --- | --- |
| Buffer | **Buffer** object created. |

**Examples**

See [from](#from)
