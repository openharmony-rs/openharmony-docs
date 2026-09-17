# Writable

Stream to which data can be written. A writable stream allows data to be written to a target, which can be a file, an HTTP response, a standard output, another stream, or the like.

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

A constructor used to create a **Writable** object.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Examples**

```TypeScript
let writableStream = new stream.Writable();
```

## cork

```TypeScript
cork(): boolean
```

Forces subsequent writes to be buffered. This API is called to optimize the performance of continuous write operations. After this API is called, the value of **writableCorked** is incremented by one. It is recommended that this API be used in pair with [uncork()](#uncork).

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Operation result. **true** means successful; **false** otherwise. |

**Examples**

```TypeScript
class TestWritable extends stream.Writable {
  constructor() {
    super();
  }

  doWrite(chunk: string | Uint8Array, encoding: string, callback: Function) {
    callback();
  }
}

let writableStream = new TestWritable();
let result = writableStream.cork();
console.info("Writable cork result", result); // Writable cork result true
```

## doInitialize

```TypeScript
doInitialize(callback: Function): void
```

You need to implement this API but do not call it directly. It is automatically called during the initialization of the writable stream. This API uses an asynchronous callback to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Function | Yes | Callback function. |

**Examples**

```TypeScript
class MyWritable extends stream.Writable {
  doInitialize(callback: Function) {
    super.doInitialize(callback);
    console.info("Writable doInitialize"); // Writable doInitialize
  }

  doWrite(chunk: string | Uint8Array, encoding: string, callback: Function) {
    super.doWrite(chunk, encoding, callback);
  }
}

new MyWritable();
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
class TestWritable extends stream.Writable {
  constructor() {
    super();
  }

  doWrite(chunk: string | Uint8Array, encoding: string, callback: Function) {
    console.info("Writable chunk is", chunk); // Writable chunk is data
    callback();
  }
}

let writableStream = new TestWritable();
writableStream.write('data', 'utf8');
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
class TestWritable extends stream.Writable {
  constructor() {
    super();
  }

  doWritev(chunks: string[] | Uint8Array[], callback: Function) {
    console.info("Writable chunk", chunks);
    callback();
  }
  // Writable chunk data1
  // Writable chunk data2
}

let writableStream = new TestWritable();
writableStream.write('data1', 'utf8');
writableStream.write('data2', 'utf8');
writableStream.uncork();
writableStream.end();
```

## end

```TypeScript
end(chunk?: string | Uint8Array, encoding?: string, callback?: Function): Writable
```

Ends the writing process in a writable stream. If the value of **writableCorked** is greater than 0, the value is set to **0** and the remaining data in the buffer is output. If the **chunk** parameter is passed, it is treated as the final data chunk and written using either the **write** or **doWrite** API, based on the current execution context. If **doWrite** is used for writing, the validity check of the **encoding** parameter depends on **doWrite**. If **end** is used alone (without **write**) and the **chunk** parameter is passed, the data is written through **doWrite**. This API uses an asynchronous callback to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| chunk | string &#124; Uint8Array | No | Data to write. The default value is **undefined**. |
| encoding | string | No | Encoding format. The default value is **'utf8'**. Currently, **'utf8'**, **'gb18030'**, **'gbk'**, and **'gb2312'** are supported. |
| callback | Function | No | Callback used to return the result. |

**Return value:**

| Type | Description |
| --- | --- |
| [Writable](arkts-arkts-stream-writable-c.md) | Current **Writable** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200035](../errorcode-utils.md#10200035-dowrite-is-not-implemented) | The doWrite method has not been implemented. |

**Examples**

```TypeScript
class TestWritable extends stream.Writable {
  constructor() {
    super();
  }

  doWrite(chunk: string | Uint8Array, encoding: string, callback: Function) {
    console.info("Writable chunk is", chunk);
    callback();
  }
  // Writable chunk is test
  // Writable chunk is finish
}

let writableStream = new TestWritable();
writableStream.write('test', 'utf8');
writableStream.end('finish', 'utf8', () => {
  console.info("Writable is end"); // Writable is end
});
```

## off

```TypeScript
off(event: string, callback?: Callback<emitter.EventData>): void
```

Unregisters an event processing callback used to listen for different events on the writable stream.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | string | Yes | Type of the event. The following events are supported: |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[emitter.EventData](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-emitter-eventdata-i.md)&gt; | No | Callback function. |

**Examples**

```TypeScript
class TestWritable extends stream.Writable {
  constructor() {
    super();
 }

  doWrite(chunk: string | Uint8Array, encoding: string, callback: Function) {
    callback();
  }
}

let writableStream = new TestWritable();
let testListenerCalled = false;
let testListener = () => {
  testListenerCalled = true;
};
writableStream.on('finish', testListener);
writableStream.off('finish');
writableStream.write('test');
writableStream.end();
setTimeout(() => {
  console.info("Writable off test", testListenerCalled.toString()); // Writable off test false
}, 0);
```

## on

```TypeScript
on(event: string, callback: Callback<emitter.EventData>): void
```

Registers an event processing callback to listen for different events on the writable stream.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | string | Yes | Type of the event. The following events are supported: |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[emitter.EventData](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-emitter-eventdata-i.md)&gt; | Yes | Callback function used to return the event data. |

**Examples**

```TypeScript
class TestWritable extends stream.Writable {
  constructor() {
    super();
  }

  doWrite(chunk: string | Uint8Array, encoding: string, callback: Function) {
    callback(new Error());
  }
}

let callbackCalled = false;
let writable = new TestWritable();
writable.on('error', () => {
  console.info("Writable event test", callbackCalled.toString()); // Writable event test false
});
writable.write('hello', 'utf8', () => {
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
class TestWritable extends stream.Writable {
  constructor() {
    super();
  }

  doWrite(chunk: string | Uint8Array, encoding: string, callback: Function) {
    callback();
  }
}

let writableStream = new TestWritable();
let result = writableStream.setDefaultEncoding('utf8');
console.info("Writable is result", result); // Writable is result true
```

## uncork

```TypeScript
uncork(): boolean
```

Releases the cork state, flushing the buffered data and writing it to the target location. After this API is called, the value of **writableCorked** is decremented by one. If the value reaches **0**, the stream is no longer in the cork state. Otherwise, the stream is still in the cork state. It is recommended that this API be used in pair with [cork()](#cork).

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Operation result. **true** means successful; **false** otherwise. |

**Examples**

```TypeScript
class TestWritable extends stream.Writable {
  constructor() {
    super();
  }

  doWrite(chunk: string | Uint8Array, encoding: string, callback: Function) {
    callback();
  }
}

let writableStream = new TestWritable();
writableStream.cork();
writableStream.write('data1', 'utf8');
writableStream.write('data2', 'utf8');
writableStream.uncork();
writableStream.end();
writableStream.on('finish', () => {
  console.info("all Data is End"); // all Data is End
});
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
| boolean | Whether there is space in the buffer of the writable stream. The value **true** means that there is still space in the buffer. The value **false** means that the buffer is full, and you are not advised to continue writing data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200035](../errorcode-utils.md#10200035-dowrite-is-not-implemented) | The doWrite method has not been implemented. |
| [10200036](../errorcode-utils.md#10200036-write-operation-is-still-performed-after-the-stream-ends) | The stream has been ended. |
| [10200037](../errorcode-utils.md#10200037-callback-is-invoked-multiple-times) | The callback is invoked multiple times consecutively. |

**Examples**

```TypeScript
class TestWritable extends stream.Writable {
  constructor() {
    super();
  }

  doWrite(chunk: string | Uint8Array, encoding: string, callback: Function) {
    console.info("Writable chunk is", chunk); // Writable chunk is test
    callback();
  }
}

let writableStream = new TestWritable();
writableStream.write('test', 'utf8');
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
