# Duplex

既可读又可写的流。双工流允许数据双向传输，即可读可写。 **Duplex**类继承自[Readable](arkts-arkts-stream-readable-c.md)，支持**Readable**中的所有API。

**继承/实现关系：** Duplex extends [Readable](arkts-arkts-stream-readable-c.md)

**起始版本：** 12

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor()
```

创建**Duplex**对象的构造函数。

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

强制将后续写入的数据缓存起来。调用此API可优化连续写入操作的性能。调用此API后，**writableCorked**的值加1。建议与[uncork()](arkts-arkts-stream-writable-c.md#uncork)配合使用。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回设置cork状态是否成功。true表示设置成功，false表示设置失败。 |

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

## doWrite

```TypeScript
doWrite(chunk: string | Uint8Array, encoding: string, callback: Function): void
```

数据写出接口是一个由开发者实现的函数，在数据被写出时自动调用，而不需要开发者手动调用。使用callback异步回调。

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

数据分批写出接口是一个由开发者实现的函数，在数据被写出时自动调用，而不需要开发者手动调用。使用callback异步回调。

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

结束双工流的写入过程。如果**writableCorked**的值大于0，则将其置为**0**，并输出缓冲区中的剩余数据。如果传入**chunk**参数，则将其视为最后一个数据块，根据当前执行上下文使用**write**或**doWrite** API写入。如果使用**doWrite**写入，**encoding**参数的有效性检查由**doWrite**决定。如果单独使用**end**（不使用**write**）且传入**chunk**参数，则数据通过**doWrite**写入。使用异步回调返回结果。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| chunk | string \| Uint8Array | 否 | 需要写入的数据。默认值为undefined。 |
| encoding | string | 否 | 编码格式。默认值为**'utf8'**。目前支持**'utf8'**、**'gb18030'**、**'gbk'**和**'gb2312'**。 |
| callback | Function | 否 | 回调函数。传入时异步调用，不传入时，不调用回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Writable](arkts-arkts-stream-writable-c.md) | 返回可写流对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200039](../errorcode-utils.md#10200039-dotransform接口未实现) | The doTransform method has not been implemented for a class that inherits from Transform. |

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

## setDefaultEncoding

```TypeScript
setDefaultEncoding(encoding?: string): boolean
```

设置双工流的默认字符编码类型，确保在读取数据时正确解析字符。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| encoding | string | 否 | 需要设置的默认字符编码类型。默认值是'utf8'，当前版本支持'utf8'、'gb18030'、'gbk'以及'gb2312'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回是否设置成功。true表示设置成功，false表示设置失败。 |

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

释放cork状态，刷新缓冲区中的数据并写入目标位置。调用此API后，**writableCorked**的值减1。如果值变为**0**，则流不再处于cork状态；否则，流仍处于cork状态。建议与[cork()](arkts-arkts-stream-writable-c.md#cork)配合使用。

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

向流的缓冲区写入数据。使用异步回调返回结果。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| chunk | string \| Uint8Array | 否 | 需要写入的数据。默认值为undefined。当前版本不支持传入null、undefined和空字符串，会抛出异常。 |
| encoding | string | 否 | 编码格式。默认值为**'utf8'**。目前支持**'utf8'**、**'gb18030'**、**'gbk'**和**'gb2312'**。 |
| callback | Function | 否 | 回调函数，用于在数据写入完成后执行特定逻辑。传入callback时，数据写入缓冲区后会调用该回调函数；不传入时，不调用回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 可写流的缓冲区中是否还有空间。true表示缓冲区还有空间，false表示流的内部缓冲区数据量已达到设定水位线，不建议继续写入，如果连续调用写入函数，数据仍会被添加到缓冲区中， 直到内存溢出为止。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200036](../errorcode-utils.md#10200036-流已经结束仍进行写操作) | The stream has been ended. |
| [10200037](../errorcode-utils.md#10200037-多次调用callback) | The callback is invoked multiple times consecutively. |
| [10200039](../errorcode-utils.md#10200039-dotransform接口未实现) | The doTransform method has not been implemented for a class that inherits from Transform. |

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

表示双工流是否处于可写状态。true表示当前流是可写的，false表示流当前不再接受写入操作。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## writableCorked

```TypeScript
get writableCorked(): number
```

表示双工流cork状态计数。值大于0时，双工流处于强制写入缓冲区状态，值为0时，该状态解除。使用cork()方法时计数加一，使用uncork()方法时计数减一，使用end()方法时计数清零。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## writableEnded

```TypeScript
get writableEnded(): boolean
```

表示当前双工流的end()是否被调用，该状态不代表数据已经全部写入。true表示end()已被调用，false表示end()未被调用。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## writableFinished

```TypeScript
get writableFinished(): boolean
```

表示当前双工流是否处于写入完成状态。true表示当前流已处于写入完成状态，false表示当前流的写入操作可能还在进行中。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## writableHighWatermark

```TypeScript
get writableHighWatermark(): number
```

定义双工流的写模式下缓冲区数据量的水位线大小。当前版本不支持开发者自定义修改设置水位线大小。调用write()写入后，若缓冲区数据量达到该值，write()会返回false。默认值为16 * 1024字节。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## writableLength

```TypeScript
get writableLength(): number
```

表示双工流缓冲区中待写入的字节数。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## writableObjectMode

```TypeScript
get writableObjectMode(): boolean
```

用于指定双工流的写模式是否以对象模式工作。true表示流的写模式被配置为对象模式，false表示流的写模式处于非对象模式。当前版本只支持原始数据（字符串和Uint8Array），返回值为false。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang
