# Readable

可从中读取数据的流。可读流用于从源（如文件或网络套接字）读取数据。

**起始版本：** 12

<!--Device-stream-class Readable--><!--Device-stream-class Readable-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { stream } from '@kit.ArkTS';
```

<a id="constructor"></a>
## constructor

```TypeScript
constructor()
```

创建**Readable**对象的构造函数。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Readable-constructor()--><!--Device-Readable-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

**示例：**

```TypeScript
let readableStream = new stream.Readable();

```

<a id="constructor-1"></a>
## constructor

```TypeScript
constructor(options: ReadableOptions)
```

创建**Readable**对象的构造函数。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Readable-constructor(options: ReadableOptions)--><!--Device-Readable-constructor(options: ReadableOptions)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ReadableOptions](arkts-arkts-stream-readableoptions-i.md) | 是 | **Readable**构造函数中的选项。 |

**示例：**

```TypeScript
let option : stream.ReadableOptions = {
  encoding : "utf-8"
};
let readableStream = new stream.Readable(option);

```

<a id="doinitialize"></a>
## doInitialize

```TypeScript
doInitialize(callback: Function): void
```

需要由开发者实现此API。在可读流首次调用[on](stream.Writable#on(event: string, callback: Callback<emitter.EventData>))时调用此API。使用异步回调返回结果。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Readable-doInitialize(callback: Function): void--><!--Device-Readable-doInitialize(callback: Function): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Function | 是 | 回调函数。 |

**示例：**

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
myReadable.on("data", () => {
});

```

<a id="doread"></a>
## doRead

```TypeScript
doRead(size: number): void
```

数据读取API，需在子类中实现。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Readable-doRead(size: int): void--><!--Device-Readable-doRead(size: int): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | number | 是 | 待读取的字节数。取值范围：0 <= size <= Number.MAX_VALUE |

**示例：**

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
readable.on("data", () => {
});

```

<a id="ispaused"></a>
## isPaused

```TypeScript
isPaused(): boolean
```

检查可读流是否已暂停。流在调用[pause()](arkts-arkts-stream-readable-c.md#pause-1)后暂停，在调用[resume()](arkts-arkts-stream-readable-c.md#resume-1)后从暂停状态恢复。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Readable-isPaused(): boolean--><!--Device-Readable-isPaused(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。流已暂停返回**true**，否则返回**false**。 |

**示例：**

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

<a id="off"></a>
## off

```TypeScript
off(event: string, callback?: Callback<emitter.EventData>): void
```

取消注册用于监听可读流上不同事件的事件处理回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Readable-off(event: string, callback?: Callback<emitter.EventData>): void--><!--Device-Readable-off(event: string, callback?: Callback<emitter.EventData>): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | string | 是 | 事件类型。支持以下事件： |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;emitter.EventData&gt; | 否 | 回调函数。 |

**示例：**

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

readable.setEncoding("utf8");
readable.on("readable", read);
readable.off("readable");
readable.push("test");
// off注销对readable事件的监听后，read函数不会被调用，"read() called"也不会被打印

```

<a id="on"></a>
## on

```TypeScript
on(event: string, callback: Callback<emitter.EventData>): void
```

注册事件处理回调，以监听可读流上的不同事件。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Readable-on(event: string, callback: Callback<emitter.EventData>): void--><!--Device-Readable-on(event: string, callback: Callback<emitter.EventData>): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | string | 是 | 事件类型。支持以下事件： |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;emitter.EventData&gt; | 是 | 用于返回事件数据的回调函数。 |

**示例：**

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
readable.push("test");
readable.on("error", () => {
  console.info("error event called"); // error event called
});

```

<a id="pause"></a>
## pause

```TypeScript
pause(): Readable
```

暂停流动模式下的可读流。可以使用**isPaused**检查流是否已暂停。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Readable-pause(): Readable--><!--Device-Readable-pause(): Readable-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Readable](arkts-arkts-stream-readable-c.md) | 当前**Readable**对象。 |

**示例：**

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

<a id="pipe"></a>
## pipe

```TypeScript
pipe(destination: Writable, options?: Object): Writable
```

将一个可写流附加到可读流上，以实现数据的自动传输。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Readable-pipe(destination: Writable, options?: Object): Writable--><!--Device-Readable-pipe(destination: Writable, options?: Object): Writable-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| destination | [Writable](arkts-arkts-stream-writable-c.md) | 是 | 接收数据的可写流。 |
| options | Object | 否 | 预留参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Writable](arkts-arkts-stream-writable-c.md) | 当前**Writable**对象。 |

**示例：**

```TypeScript
class TestReadable extends stream.Readable {
  constructor() {
    super();
  }

  doRead(size: number) {
    this.push("test");
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

<a id="push"></a>
## push

```TypeScript
push(chunk: Uint8Array | string | undefined | null, encoding?: string): boolean
```

将数据推入可读流的缓冲区。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Readable-push(chunk: Uint8Array | string | undefined | null, encoding?: string): boolean--><!--Device-Readable-push(chunk: Uint8Array | string | undefined | null, encoding?: string): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| chunk | Uint8Array \| string \| undefined \| null | 是 | 待读取的数据。<br> 从API version 22起有兼容性变更。在API version 21及之前版本，类型为 `Uint8Array \| string \| null`。<br>**起始版本：** 23 |
| encoding | string | 否 | 编码格式。默认值为**'utf8'**。目前支持**'utf8'**、**'gb18030'**、**'gbk'**和**'gb2312'**。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示可读流缓冲区中是否还有空间。**true**表示缓冲区中还有空间；**false**表示缓冲区已满。如果传入**null**，则始终返回**false**，表示没有可推送的数据块。 |

**示例：**

```TypeScript
class TestReadable extends stream.Readable {
  constructor() {
    super();
  }

  doRead(size: number) {
  }
}

let readable = new TestReadable();
let testData = "Hello world";
readable.push(testData);
console.info("Readable push test", readable.readableLength); // Readable push test 11

```

<a id="read"></a>
## read

```TypeScript
read(size?: number): string | null
```

从可读流的缓冲区中读取数据，并返回读取的数据。如果没有读取到数据，则返回**null**。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Readable-read(size?: number): string | null--><!--Device-Readable-read(size?: number): string | null-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | number | 否 | 待读取的字节数。默认值为**undefined**。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 从可读流中读取的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200038](../errorcode-utils.md#10200038-doread接口未实现) | The doRead method has not been implemented. |

**示例：**

```TypeScript
class TestReadable extends stream.Readable {
  constructor() {
    super();
  }

  doRead(size: number) {
  }
}

let readableStream = new TestReadable();
readableStream.push("test");
readableStream.pause();
let dataChunk = readableStream.read();
console.info("Readable data is", dataChunk); // Readable data is test

```

<a id="resume"></a>
## resume

```TypeScript
resume(): Readable
```

恢复已显式暂停的可读流。可以使用**isPaused**检查流是否已暂停。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Readable-resume(): Readable--><!--Device-Readable-resume(): Readable-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Readable](arkts-arkts-stream-readable-c.md) | 当前**Readable**对象。 |

**示例：**

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
console.info("Readable test resume", !readableStream.isPaused()); // 切换流动模式成功时，此处日志将打印"Readable test resume true"

```

<a id="setencoding"></a>
## setEncoding

```TypeScript
setEncoding(encoding?: string): boolean
```

设置可读流的编码格式。如果缓冲区中包含数据，则不允许设置编码格式，并返回**false**。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Readable-setEncoding(encoding?: string): boolean--><!--Device-Readable-setEncoding(encoding?: string): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| encoding | string | 否 | 编码格式。默认值为**'utf8'**。目前支持**'utf8'**、**'gb18030'**、**'gbk'**和**'gb2312'**。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 操作结果。设置成功返回**true**，否则返回**false**。 |

**示例：**

```TypeScript
class TestReadable extends stream.Readable {
  constructor() {
    super();
  }

  doRead(size: number) {
  }
}

let readableStream = new TestReadable();
let result = readableStream.setEncoding("utf8");
console.info("Readable result", result); // Readable result true

```

<a id="unpipe"></a>
## unpipe

```TypeScript
unpipe(destination?: Writable): Readable
```

将之前附加到可读流的可写流分离。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Readable-unpipe(destination?: Writable): Readable--><!--Device-Readable-unpipe(destination?: Writable): Readable-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| destination | [Writable](arkts-arkts-stream-writable-c.md) | 否 | 待分离的可写流。默认值为**undefined**。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Readable](arkts-arkts-stream-readable-c.md) | 当前**Readable**对象。 |

**示例：**

```TypeScript
class TestReadable extends stream.Readable {
  constructor() {
    super();
  }

  doRead(size: number) {
    this.push("test");
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
readable.on("data", () => {
  console.info("Readable test unpipe data event triggered");
});
// unpipe成功断开连接之后，data事件将不会触发，不会打印"Readable test unpipe data event triggered"

```

## readable

```TypeScript
get readable(): boolean
```

如果调用readable.read()是安全的，返回true，即表示流未被销毁、未发出'error'或'end'。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Readable-get readable(): boolean--><!--Device-Readable-get readable(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

## readableEncoding

```TypeScript
get readableEncoding(): string | null
```

获取给定Readable流的encoding属性的getter。encoding属性可通过readable.setEncoding()方法设置。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Readable-get readableEncoding(): string | null--><!--Device-Readable-get readableEncoding(): string | null-End-->

**系统能力：** SystemCapability.Utils.Lang

## readableEnded

```TypeScript
get readableEnded(): boolean
```

是否已生成所有数据。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Readable-get readableEnded(): boolean--><!--Device-Readable-get readableEnded(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

## readableFlowing

```TypeScript
get readableFlowing(): boolean | null
```

此属性反映可读流的当前状态 null/true/false。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Readable-get readableFlowing(): boolean | null--><!--Device-Readable-get readableFlowing(): boolean | null-End-->

**系统能力：** SystemCapability.Utils.Lang

## readableHighWatermark

```TypeScript
get readableHighWatermark(): number
```

返回创建此Readable时传入的highWatermark的值。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Readable-get readableHighWatermark(): int--><!--Device-Readable-get readableHighWatermark(): int-End-->

**系统能力：** SystemCapability.Utils.Lang

## readableLength

```TypeScript
get readableLength(): number
```

可读取的数据大小，单位为字节或对象。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Readable-get readableLength(): int--><!--Device-Readable-get readableLength(): int-End-->

**系统能力：** SystemCapability.Utils.Lang

## readableObjectMode

```TypeScript
get readableObjectMode(): boolean
```

返回布尔值，表示是否处于ObjectMode。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Readable-get readableObjectMode(): boolean--><!--Device-Readable-get readableObjectMode(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

