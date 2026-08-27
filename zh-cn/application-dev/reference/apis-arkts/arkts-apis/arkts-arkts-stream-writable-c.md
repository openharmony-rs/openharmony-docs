# Writable

可写入数据的流。可写流允许将数据写入到目标中，这个目标可以是文件、HTTP响应、标准输出、另一个流等。可写流采用缓冲区机制：数据通过write()写入缓冲区，缓冲区数据通过doWrite()自动写出到目标，开发者需实现doWrite以定义数据写出的具体行为。

**起始版本：** 12

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor()
```

**Writable**的构造函数。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**示例**

```TypeScript
let writableStream = new stream.Writable();
```

```TypeScript
let readableStream = new stream.Readable();
```

```TypeScript
let duplex = new stream.Duplex();
```

```TypeScript
let transformStream = new stream.Transform();
```

## cork

```TypeScript
cork(): boolean
```

强制将后续写入的数据缓存起来。调用此API可优化连续写入操作的性能。调用此API后，**writableCorked**的值加1。建议与[uncork()](#uncork)配合使用。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回设置cork状态是否成功。true表示成功，false表示失败。 |

**示例**

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

```TypeScript
let duplexStream = new stream.Duplex();
let result = duplexStream.cork();
console.info("duplexStream cork result", result); // duplexStream cork result true
```

## doInitialize

```TypeScript
doInitialize(callback: Function): void
```

需要由开发者实现此API，但不要直接调用。此API在可写流初始化期间自动调用。使用异步回调返回结果。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Function | 是 | 回调函数。 |

**示例**

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

## doWrite

```TypeScript
doWrite(chunk: string | Uint8Array, encoding: string, callback: Function): void
```

提供一个数据写出接口供开发者实现，该接口函数会在数据被成功写出时自动调用，无需手动触发。使用callback异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| chunk | string \| Uint8Array | 是 | 要写出的数据。 |
| encoding | string | 是 | 字符编码类型。当前版本支持'utf8'、'gb18030'、'gbk'以及'gb2312'。 |
| callback | Function | 是 | 回调函数。 |

**示例**

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
writableStream.write("data", "utf8");
```

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
duplexStream.write("data", "utf8");
```

## doWritev

```TypeScript
doWritev(chunks: string[] | Uint8Array[], callback: Function): void
```

提供一个数据批量写出接口供开发者实现，该接口函数会在数据被成功写出时自动调用，无需开发者手动触发。使用callback异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| chunks | string[] \| Uint8Array[] | 是 | 待批量写出的数据块数组。 |
| callback | Function | 是 | 回调函数。 |

**示例**

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
writableStream.write("data1", "utf8");
writableStream.write("data2", "utf8");
writableStream.uncork();
writableStream.end();
```

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
duplexStream.write("data1", "utf8");
duplexStream.write("data2", "utf8");
duplexStream.uncork();
duplexStream.end();
```

## end

```TypeScript
end(chunk?: string | Uint8Array, encoding?: string, callback?: Function): Writable
```

结束可写流的写入过程。如果**writableCorked**的值大于0，则将其置为**0**，并输出缓冲区中的剩余数据。如果传入**chunk**参数，则将其视为最后一个数据块，根据当前执行上下文使用**write**或**doWrite** API写入。如果使用**doWrite**写入，**encoding**参数的有效性检查由**doWrite**决定。如果单独使用**end**（不使用**write**）且传入**chunk**参数，则数据通过**doWrite**写入。使用异步回调返回结果。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| chunk | string \| Uint8Array | 否 | 待写入的数据。默认值为**undefined**。 |
| encoding | string | 否 | 编码格式。默认值为**'utf8'**。目前支持**'utf8'**、**'gb18030'**、**'gbk'**和**'gb2312'**。 |
| callback | Function | 否 | 用于返回结果的回调函数。传入时异步调用，不传入时，不调用回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Writable](arkts-arkts-stream-writable-c.md) | 返回当前可写流对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200035](../errorcode-utils.md#10200035-dowrite接口未实现) | The doWrite method has not been implemented. |

**示例**

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
writableStream.write("test", "utf8");
writableStream.end("finish", "utf8", () => {
  console.info("Writable is end"); // Writable is end
});
```

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
duplexStream.end("test", "utf8", () => {
  console.info("Duplex is end"); // Duplex is end
});
```

## off

```TypeScript
off(event: string, callback?: Callback<emitter.EventData>): void
```

移除通过on注册的事件处理函数。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | string | 是 | 事件回调类型，支持的事件包括：'close' \| 'drain' \| 'error' \| 'finish'。   - 'close'：完成end()调用，结束写入操作，触发该事件。   - 'drain'：在可写流缓冲区中数据清空时触发该事件。   - 'error'：在可写流发生异常时触发该事件。   - 'finish'：在数据缓冲区全部写入到目标后触发该事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;emitter.EventData&gt; | 否 | 指定事件的要注销的回调函数。不传入时注销指定事件的所有回调函数。 |

**示例**

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
writableStream.on("finish", testListener);
writableStream.off("finish");
writableStream.write("test");
writableStream.end();
setTimeout(() => {
  console.info("Writable off test", testListenerCalled.toString()); // Writable off test false
}, 0);
```

```TypeScript
class TestReadable extends stream.Readable {
  constructor() {
    super();
  }

  doRead(size: number) {
  }
}

let readableStream = new TestReadable();

function read() {
  console.info("read() called");
}

readableStream.setEncoding("utf8");
readableStream.on("readable", read);
readableStream.off("readable");
readableStream.push("test");
// off注销对readable事件的监听后，read函数不会被调用，"read() called"也不会被打印
```

## on

```TypeScript
on(event: string, callback: Callback<emitter.EventData>): void
```

注册事件处理函数来监听可写流上的不同事件。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | string | 是 | 事件回调类型，支持的事件包括：'close' \| 'drain' \| 'error' \| 'finish'。   - 'close'：完成end()调用，结束写入操作，触发该事件。   - 'drain'：在可写流缓冲区中数据清空时触发该事件。   - 'error'：在可写流发生异常时触发该事件。   - 'finish'：在数据缓冲区全部写入到目标后触发该事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;emitter.EventData&gt; | 是 | 回调函数，返回事件传输的数据。 |

**示例**

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
let writableStream = new TestWritable();
writableStream.on("error", () => {
  console.info("Writable event test", callbackCalled.toString()); // Writable event test false
});
writableStream.write("hello", "utf8", () => {
});
```

```TypeScript
class TestReadable extends stream.Readable {
  constructor() {
    super();
  }

  doRead(size: number) {
    throw new Error("Simulated error");
  }
}

let readableStream = new TestReadable();
readableStream.push("test");
readableStream.on("error", () => {
  console.error("error event called"); // error event called
});
```

## setDefaultEncoding

```TypeScript
setDefaultEncoding(encoding?: string): boolean
```

设置可写流的默认字符编码类型。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| encoding | string | 否 | 设置默认字符编码类型。默认值是'utf8'，当前版本支持'utf8'、'gb18030'、'gbk'以及'gb2312'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回是否设置成功。true表示成功，false表示失败。 |

**示例**

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
let result = writableStream.setDefaultEncoding("utf8");
console.info("Writable is result", result); // Writable is result true
```

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
let result = duplexStream.setDefaultEncoding("utf8");
console.info("duplexStream is result", result); // duplexStream is result true
```

## uncork

```TypeScript
uncork(): boolean
```

释放cork状态，刷新缓冲区中的数据并写入目标位置。调用此API后，**writableCorked**的值减1。如果值变为**0**，则流不再处于cork状态；否则，流仍处于cork状态。建议与[cork()](#cork)配合使用。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回解除cork状态是否成功。true表示成功，false表示失败。 |

**示例**

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
writableStream.write("data1", "utf8");
writableStream.write("data2", "utf8");
writableStream.uncork();
writableStream.end();
writableStream.on("finish", () => {
  console.info("all Data is End"); // all Data is End
});
```

```TypeScript
let dataWritten = "";
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
duplexStream.write("a");
duplexStream.write("b");
duplexStream.uncork();
console.info("Duplex test uncork", dataWritten); // Duplex test uncork ab
```

## write

```TypeScript
write(chunk?: string | Uint8Array, encoding?: string, callback?: Function): boolean
```

将数据写入流的缓冲区中。数据写入缓冲区后，当缓冲区数据被消耗时，会自动调用doWrite()将数据写出。使用callback异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| chunk | string \| Uint8Array | 否 | 需要写入的数据。默认值为undefined。当前版本不支持传入null、undefined和空字符串，会抛出异常。 |
| encoding | string | 否 | 字符编码类型。默认值是**'utf8'**，当前版本支持**'utf8'**、**'gb18030'**、**'gbk'**以及**'gb2312'**。 |
| callback | Function | 否 | 回调函数，用于在数据写入完成后执行特定逻辑。传入callback时，数据写入缓冲区后会调用该回调函数；不传入时，不调用回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 可写流的缓冲区中是否还有空间。**true**表示缓冲区还有空间，**false**表示流的内部缓冲区数据量已达到设定水位线，不建议继续写入以避免内存溢出。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200035](../errorcode-utils.md#10200035-dowrite接口未实现) | The doWrite method has not been implemented. |
| [10200036](../errorcode-utils.md#10200036-流已经结束仍进行写操作) | The stream has been ended. |
| [10200037](../errorcode-utils.md#10200037-多次调用callback) | The callback is invoked multiple times consecutively. |

**示例**

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
writableStream.write("test", "utf8");
```

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
let result = duplexStream.write("test", "utf8");
console.info("duplexStream result", result); // duplexStream result true
```

## writable

```TypeScript
get writable(): boolean
```

表示可写流是否处于可写状态。true表示流当前是可写的，false表示流当前不再接受写入操作。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## writableCorked

```TypeScript
get writableCorked(): number
```

表示可写流cork状态计数。值大于0时，可写流处于强制写入缓冲区状态；值为0时，该状态解除。使用cork()方法时计数加一，使用uncork()方法时计数减一，使用end()方法时计数清零。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## writableEnded

```TypeScript
get writableEnded(): boolean
```

表示当前可写流的end()是否被调用，该状态不代表数据已经全部写入。true表示end()已被调用，false表示end()未被调用。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## writableFinished

```TypeScript
get writableFinished(): boolean
```

表示当前可写流是否处于写入完成状态。true表示当前流已处于写入完成状态，false表示当前流的写入操作可能还在进行中。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## writableHighWatermark

```TypeScript
get writableHighWatermark(): number
```

定义可写流缓冲区数据量的水位线大小，单位：字节。当前版本不支持开发者自定义修改水位线大小。调用write()写入数据后，若缓冲区数据量达到该值，write()会返回false。默认值为16 * 1024字节。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## writableLength

```TypeScript
get writableLength(): number
```

表示可写流缓冲区中待写入的字节数。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## writableObjectMode

```TypeScript
get writableObjectMode(): boolean
```

表示可写流是否以对象模式工作。true表示流被配置为对象模式，false表示流处于非对象模式。当前版本只支持原始数据（字符串和Uint8Array），返回值为false。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang
