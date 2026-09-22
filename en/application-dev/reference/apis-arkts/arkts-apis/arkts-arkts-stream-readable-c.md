# Readable

```TypeScript
export class Readable
```

Stream from which data can be read. A readable stream is used to read data from a source, such as a file or a network socket.

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

A constructor used to create a **Readable** object.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Examples**

```TypeScript
let readableStream = new stream.Readable();
```

<a id="constructor-1"></a>

## constructor

```TypeScript
constructor(options: ReadableOptions)
```

A constructor used to create a **Readable** object.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ReadableOptions](arkts-arkts-stream-readableoptions-i.md) | Yes | Options in the **Readable** constructor. |

**Examples**

```TypeScript
let option : stream.ReadableOptions = {
  encoding : 'utf-8'
};
let readableStream = new stream.Readable(option);
```

## doInitialize

```TypeScript
doInitialize(callback: Function): void
```

You need to implement this API. It is called when the readable stream calls on for the first time. This API uses an asynchronous callback to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Function | Yes | Callback function. |

**Examples**

```TypeScript
class MyReadable extends stream.Readable {
  doInitialize(callback: Function) {
    super.doInitialize(callback);
    console.info("Readable doInitialize"); // Readable doInitialize
}

  doRead(size: number) {
  }
}

let myReadable = new MyReadable();
myReadable.on('data', () => {
});
```

## doRead

```TypeScript
doRead(size: number): void
```

A data read API that needs to be implemented in child classes.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | number | Yes | Number of bytes to read. Value range: 0 &lt;= size &lt;= Number.MAX_VALUE |

**Examples**

```TypeScript
class TestReadable extends stream.Readable {
  constructor() {
    super();
  }

  doRead(size: number) {
    console.info("doRead called"); // doRead called
  }
}

let readable = new TestReadable();
readable.on('data', () => {
});
```

## isPaused

```TypeScript
isPaused(): boolean
```

Checks whether the readable stream is paused. The stream is paused after [pause()](#pause) is called and resumes from the paused state after [resume()](#resume) is called.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the stream is paused; otherwise, **false** is returned. |

**Examples**

```TypeScript
class TestReadable extends stream.Readable {
  constructor() {
    super();
  }

  doRead(size: number) {
  }
}

let readableStream = new TestReadable();
console.info("Readable isPaused", readableStream.isPaused()); // Readable isPaused false
readableStream.pause();
console.info("Readable isPaused", readableStream.isPaused()); // Readable isPaused true
```

## off

```TypeScript
off(event: string, callback?: Callback<emitter.EventData>): void
```

Unregisters an event processing callback used to listen for different events on the readable stream.

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
class TestReadable extends stream.Readable {
  constructor() {
    super();
  }

  doRead(size: number) {
  }
}

let readable = new TestReadable();

function read() {
  console.info("read() called");
}

readable.setEncoding('utf8');
readable.on('readable', read);
readable.off('readable');
readable.push('test');
// After off is used to unregister the listening of the readable stream events, the read function is not called and "read() called" is not printed.
```

## on

```TypeScript
on(event: string, callback: Callback<emitter.EventData>): void
```

Registers an event processing callback to listen for different events on the readable stream.

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
class TestReadable extends stream.Readable {
  constructor() {
    super();
  }

  doRead(size: number) {
    throw new Error('Simulated error');
  }
}

let readable = new TestReadable();
readable.push('test');
readable.on('error', () => {
  console.info("error event called"); // error event called
});
```

## pause

```TypeScript
pause(): Readable
```

Pauses the readable stream in flowing mode. You can use **isPaused** to check whether the stream is paused.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [Readable](arkts-arkts-stream-readable-c.md) | Current **Readable** object. |

**Examples**

```TypeScript
class TestReadable extends stream.Readable {
  constructor() {
    super();
  }

  doRead(size: number) {
  }
}

let readableStream = new TestReadable();
readableStream.pause();
console.info("Readable test pause", readableStream.isPaused()); // Readable test pause true
```

## pipe

```TypeScript
pipe(destination: Writable, options?: Object): Writable
```

Attaches a writable stream to the readable stream to implement automatic data transmission.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| destination | [Writable](arkts-arkts-stream-writable-c.md) | Yes | Writable stream that receives data. |
| options | Object | No | Reserved. |

**Return value:**

| Type | Description |
| --- | --- |
| [Writable](arkts-arkts-stream-writable-c.md) | Current **Writable** object. |

**Examples**

```TypeScript
class TestReadable extends stream.Readable {
  constructor() {
    super();
  }

  doRead(size: number) {
    this.push('test');
    this.push(null);
  }
}

class TestWritable extends stream.Writable {
  constructor() {
    super();
  }

  doWrite(chunk: string | Uint8Array, encoding: string, callback: Function) {
    console.info("Readable test pipe", chunk); // Readable test pipe test
    callback();
  }
}

let readable = new TestReadable();
let writable = new TestWritable();
readable.pipe(writable);
```

## push

```TypeScript
push(chunk: Uint8Array | string | undefined | null, encoding?: string): boolean
```

Pushes data into the buffer of the readable stream.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| chunk | Uint8Array &#124; string &#124; undefined &#124; null | Yes | Data to read.<br> There has been a compatibility change since API version 22. In API version 21 and earlier versions, the type is `Uint8Array &#124; string &#124; null`.<br>**Since:** 23 |
| encoding | string | No | Encoding format. The default value is **'utf8'**. Currently, **'utf8'**, **'gb18030'**, **'gbk'**, and **'gb2312'** are supported. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether there is space in the buffer of the readable stream. The value **true** means that there is still space in the buffer, and **false** means that the buffer is full. If **null** is passed, **false** is always returned, indicating that no data chunk is available for pushing. |

**Examples**

```TypeScript
class TestReadable extends stream.Readable {
  constructor() {
    super();
  }

  doRead(size: number) {
  }
}

let readable = new TestReadable();
let testData = 'Hello world';
readable.push(testData);
console.info("Readable push test", readable.readableLength); // Readable push test 11
```

## read

```TypeScript
read(size?: number): string | null
```

Reads data from the buffer of the readable stream and returns the read data. If no data is read, **null** is returned.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | number | No | Number of bytes to read. The default value is **undefined**. |

**Return value:**

| Type | Description |
| --- | --- |
| string &#124; null | Data read from the readable stream. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200038](../errorcode-utils.md#10200038-doread-is-not-implemented) | The doRead method has not been implemented. |

**Examples**

```TypeScript
class TestReadable extends stream.Readable {
  constructor() {
    super();
  }

  doRead(size: number) {
  }
}

let readableStream = new TestReadable();
readableStream.push('test');
readableStream.pause();
let dataChunk = readableStream.read();
console.info('Readable data is', dataChunk); // Readable data is test
```

## resume

```TypeScript
resume(): Readable
```

Resumes an explicitly paused readable stream. You can use **isPaused** to check whether the stream is paused.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [Readable](arkts-arkts-stream-readable-c.md) | Current **Readable** object. |

**Examples**

```TypeScript
class TestReadable extends stream.Readable {
  constructor() {
    super();
  }

  doRead(size: number) {
  }
}

let readableStream = new TestReadable();
readableStream.resume();
console.info("Readable test resume", !readableStream.isPaused()); // After a successful switching, the log "Readable test resume true" is displayed.
```

## setEncoding

```TypeScript
setEncoding(encoding?: string): boolean
```

Sets an encoding format for the readable stream. If the buffer contains data, setting the encoding format is not allowed, and **false** is returned.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| encoding | string | No | Encoding format. The default value is **'utf8'**. Currently, **'utf8'**, **'gb18030'**, **'gbk'**, and **'gb2312'** are supported. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Operation result. The value **true** is returned if the setting is successful; otherwise, **false** is returned. |

**Examples**

```TypeScript
class TestReadable extends stream.Readable {
  constructor() {
    super();
  }

  doRead(size: number) {
  }
}

let readableStream = new TestReadable();
let result = readableStream.setEncoding('utf8');
console.info("Readable result", result); // Readable result true
```

## unpipe

```TypeScript
unpipe(destination?: Writable): Readable
```

Detaches a writable stream previously attached to the readable stream.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| destination | [Writable](arkts-arkts-stream-writable-c.md) | No | Writable stream to detach. The default value is **undefined**. |

**Return value:**

| Type | Description |
| --- | --- |
| [Readable](arkts-arkts-stream-readable-c.md) | Current **Readable** object. |

**Examples**

```TypeScript
class TestReadable extends stream.Readable {
  constructor() {
    super();
  }

  doRead(size: number) {
    this.push('test');
    this.push(null);
  }
}

class TestWritable extends stream.Writable {
  constructor() {
    super();
  }

  doWrite(chunk: string | Uint8Array, encoding: string, callback: Function) {
    callback();
  }
}

let readable = new TestReadable();
let writable = new TestWritable();
readable.pipe(writable);
readable.unpipe(writable);
readable.on('data', () => {
  console.info("Readable test unpipe data event triggered");
});
// After successful detaching, the data event is not triggered and "Readable test unpipe data event triggered" is not printed.
```

## readable

```TypeScript
get readable(): boolean
```

Is true if it is safe to call readable.read(), which means the stream has not been destroyed or emitted 'error' or 'end'.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## readableEncoding

```TypeScript
get readableEncoding(): string | null
```

Getter for the property encoding of a given Readable stream. The encoding property can be set using the readable.setEncoding() method.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## readableEnded

```TypeScript
get readableEnded(): boolean
```

Whether all data has been generated.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## readableFlowing

```TypeScript
get readableFlowing(): boolean | null
```

This property reflects the current state of the readable stream null/true/false.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## readableHighWatermark

```TypeScript
get readableHighWatermark(): number
```

Returns the value of highWatermark passed when creating this Readable.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## readableLength

```TypeScript
get readableLength(): number
```

Size of the data that can be read, in bytes or objects.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## readableObjectMode

```TypeScript
get readableObjectMode(): boolean
```

Returns boolean indicating whether it is in ObjectMode.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang
