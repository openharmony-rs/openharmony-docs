# Duplex

A stream that is both readable and writable. A duplex stream allows data to be transmitted in two directions, that is, data can be read and written. The **Duplex** class inherits from [Readable](arkts-arkts-stream-readable-c.md) and supports all the APIs in **Readable**.

**Inheritance/Implementation:** Duplex extends [Readable](arkts-arkts-stream-readable-c.md)

**Since:** 12

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { stream } from '@kit.ArkTS';
```

## constructor

```TypeScript
constructor()
```

A constructor used to create a **Duplex** object.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Examples**

```TypeScript
let duplex = new stream.Duplex();
```

## cork

```TypeScript
cork(): boolean
```

Forces subsequent writes to be buffered. This API is called to optimize the performance of continuous write operations. After this API is called, the value of **writableCorked** is incremented by one. It is recommended that this API be used in pair with [uncork()](arkts-arkts-stream-writable-c.md#uncork).

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Operation result. **true** means successful; **false** otherwise. |

**Examples**

```TypeScript
let duplexStream = new stream.Duplex();
let result = duplexStream.cork();
console.info("duplexStream cork result", result); // duplexStream cork result true
```

## doWrite

```TypeScript
doWrite(chunk: string | Uint8Array, encoding: string, callback: Function): void
```

A data write API. You need to implement this API but do not call it directly. This API is automatically called when data is written. This API uses an asynchronous callback to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| chunk | string &#124; Uint8Array | Yes | Data to write. |
| encoding | string | Yes | Encoding format. Currently, **'utf8'**, **'gb18030'**, **'gbk'**, and **'gb2312'** are supported. |
| callback | Function | Yes | Callback function. |

**Examples**

```TypeScript
class TestDuplex extends stream.Duplex {
  constructor() {
    super();
  }

  doRead(size: number) {
  }

  doWrite(chunk: string | Uint8Array, encoding: string, callback: Function) {
    console.info("duplexStream chunk is", chunk); // duplexStream chunk is data
    callback();
  }
}

let duplexStream = new TestDuplex();
duplexStream.write('data', 'utf8');
```

## doWritev

```TypeScript
doWritev(chunks: string[] | Uint8Array[], callback: Function): void
```

A batch data write API. You need to implement this API but do not call it directly. This API is automatically called when data is written. This API uses an asynchronous callback to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| chunks | string[] &#124; Uint8Array[] | Yes | Data arrays to write in batches. |
| callback | Function | Yes | Callback function. |

**Examples**

```TypeScript
class TestDuplex extends stream.Duplex {
  constructor() {
    super();
  }

  doRead(size: number) {
  }

  doWrite(chunk: string | Uint8Array, encoding: string, callback: Function) {
    callback();
  }

  doWritev(chunks: string[] | Uint8Array[], callback: Function) {
    console.info("duplexStream chunk", chunks[0]); // duplexStream chunk data1
    callback();
  }
}

let duplexStream = new TestDuplex();
duplexStream.cork();
duplexStream.write('data1', 'utf8');
duplexStream.write('data2', 'utf8');
duplexStream.uncork();
duplexStream.end();
```

## end

```TypeScript
end(chunk?: string | Uint8Array, encoding?: string, callback?: Function): Writable
```

Ends the writing process in a duplex stream. If the value of **writableCorked** is greater than 0, the value is set to **0** and the remaining data in the buffer is output. If the **chunk** parameter is passed, it is treated as the final data chunk and written using either the **write** or **doWrite** API, based on the current execution context. If **doWrite** is used for writing, the validity check of the **encoding** parameter depends on **doWrite**. If **end** is used alone (without **write**) and the **chunk** parameter is passed, the data is written through **doWrite**. This API uses an asynchronous callback to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| chunk | string &#124; Uint8Array | No | Data to write. The default value is **undefined**. |
| encoding | string | No | Encoding format. The default value is **'utf8'**. Currently, **'utf8'**, **'gb18030'**, **'gbk'**, and **'gb2312'** are supported. |
| callback | Function | No | Callback used to return the result. It is not called by default. |

**Return value:**

| Type | Description |
| --- | --- |
| [Writable](arkts-arkts-stream-writable-c.md) | Current **Duplex** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200039](../errorcode-utils.md#10200039-dotransform-is-not-implemented) | The doTransform method has not been implemented for a class that inherits from Transform. |

**Examples**

```TypeScript
class TestDuplex extends stream.Duplex {
  constructor() {
    super();
  }

  doRead(size: number) {
  }

  doWrite(chunk: string | Uint8Array, encoding: string, callback: Function) {
  console.info("Duplex chunk is", chunk); // Duplex chunk is test
  callback();
  }
}

let duplexStream = new TestDuplex();
duplexStream.end('test', 'utf8', () => {
  console.info("Duplex is end"); // Duplex is end
});
```

## setDefaultEncoding

```TypeScript
setDefaultEncoding(encoding?: string): boolean
```

Sets the default encoding format for the writable stream.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| encoding | string | No | Default encoding format. The default value is **'utf8'**. Currently, **'utf8'**, **'gb18030'**, **'gbk'**, and **'gb2312'** are supported. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Operation result. **true** means successful; **false** otherwise. |

**Examples**

```TypeScript
class TestDuplex extends stream.Duplex {
  constructor() {
    super();
  }

  doRead(size: number) {
  }

  doWrite(chunk: string | Uint8Array, encoding: string, callback: Function) {
    callback();
  }
}

let duplexStream = new TestDuplex();
let result = duplexStream.setDefaultEncoding('utf8');
console.info("duplexStream is result", result); // duplexStream is result true
```

## uncork

```TypeScript
uncork(): boolean
```

Releases the cork state, flushing the buffered data and writing it to the target location. After this API is called, the value of **writableCorked** is decremented by one. If the value reaches **0**, the stream is no longer in the cork state. Otherwise, the stream is still in the cork state. It is recommended that this API be used in pair with [cork()](arkts-arkts-stream-writable-c.md#cork).

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Operation result. **true** means successful; **false** otherwise. |

**Examples**

```TypeScript
let dataWritten = '';
class TestDuplex extends stream.Duplex {
  constructor() {
    super();
  }

  doRead(size: number) {
  }

  doWrite(chunk: string | Uint8Array, encoding: string, callback: Function) {
    dataWritten += chunk;
    callback();
  }
}

let duplexStream = new TestDuplex();
duplexStream.cork();
duplexStream.write('a');
duplexStream.write('b');
duplexStream.uncork();
console.info("Duplex test uncork", dataWritten); // Duplex test uncork ab
```

## write

```TypeScript
write(chunk?: string | Uint8Array, encoding?: string, callback?: Function): boolean
```

Writes data to the buffer of the stream. This API uses an asynchronous callback to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| chunk | string &#124; Uint8Array | No | Data to write. It cannot be **null**, **undefined**, or an empty string. |
| encoding | string | No | Encoding format. The default value is **'utf8'**. Currently, **'utf8'**, **'gb18030'**, **'gbk'**, and **'gb2312'** are supported. |
| callback | Function | No | Callback used to return the result. It is not called by default. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether there is space in the buffer of the writable stream. The value **true** means that there is still space in the buffer. The value **false** means that the buffer is full, and you are not advised to continue writing data. If the write function is called continuously, data is still added to the buffer until the memory overflows. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200036](../errorcode-utils.md#10200036-write-operation-is-still-performed-after-the-stream-ends) | The stream has been ended. |
| [10200037](../errorcode-utils.md#10200037-callback-is-invoked-multiple-times) | The callback is invoked multiple times consecutively. |
| [10200039](../errorcode-utils.md#10200039-dotransform-is-not-implemented) | The doTransform method has not been implemented for a class that inherits from Transform. |

**Examples**

```TypeScript
class TestDuplex extends stream.Duplex {
  constructor() {
    super();
  }

  doRead(size: number) {
  }

  doWrite(chunk: string | Uint8Array, encoding: string, callback: Function) {
    console.info("duplexStream chunk is", chunk); // duplexStream chunk is test
    callback();
  }
}

let duplexStream = new TestDuplex();
let result = duplexStream.write('test', 'utf8');
console.info("duplexStream result", result); // duplexStream result true
```

## writable

```TypeScript
get writable(): boolean
```

Is true if it is safe to call writable.write(), which means the stream has not been destroyed, error or end.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## writableCorked

```TypeScript
get writableCorked(): number
```

Number of times writable.uncork() needs to be called in order to fully uncork the stream.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## writableEnded

```TypeScript
get writableEnded(): boolean
```

Whether Writable.end has been called.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## writableFinished

```TypeScript
get writableFinished(): boolean
```

Whether Writable.end has been called and all buffers have been flushed.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## writableHighWatermark

```TypeScript
get writableHighWatermark(): number
```

Value of highWatermark.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## writableLength

```TypeScript
get writableLength(): number
```

Size of data that can be flushed, in bytes or objects.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## writableObjectMode

```TypeScript
get writableObjectMode(): boolean
```

Returns boolean indicating whether it is in ObjectMode.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang
