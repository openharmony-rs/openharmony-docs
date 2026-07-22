# Duplex

既可读又可写的流。双工流允许数据双向传输，即可读可写。**Duplex**类继承自[Readable](arkts-arkts-stream-readableoptions-i.md)，支持**Readable**中的所有API。

**继承/实现关系：** Duplex extends [Readable](arkts-arkts-stream-readable-c.md)

**起始版本：** 12

<!--Device-stream-class Duplex extends Readable--><!--Device-stream-class Duplex extends Readable-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { stream } from '@kit.ArkTS';
```

## constructor

```TypeScript
constructor()
```

创建**Duplex**对象的构造函数。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Duplex-constructor()--><!--Device-Duplex-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

**示例：**

```TypeScript
let duplex = new stream.Duplex();

```

## cork

```TypeScript
cork(): boolean
```

强制将后续写入的数据缓存起来。调用此API可优化连续写入操作的性能。调用此API后，**writableCorked**的值加1。建议与[uncork()](arkts-arkts-stream-writable-c.md#uncork)配合使用。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Duplex-cork(): boolean--><!--Device-Duplex-cork(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 操作结果。**true**表示成功；**false**表示失败。 |

**示例：**

```TypeScript
let duplexStream = new stream.Duplex();
let result = duplexStream.cork();
console.info("duplexStream cork result", result); // duplexStream cork result true

```

## doWrite

```TypeScript
doWrite(chunk: string | Uint8Array, encoding: string, callback: Function): void
```

数据写入API。需要由开发者实现此API，但不要直接调用。此API在写入数据时自动调用。使用异步回调返回结果。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Duplex-doWrite(chunk: string | Uint8Array, encoding: string, callback: Function): void--><!--Device-Duplex-doWrite(chunk: string | Uint8Array, encoding: string, callback: Function): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| chunk | string \| Uint8Array | 是 | 待写入的数据。 |
| encoding | string | 是 | 编码格式。目前支持**'utf8'**、**'gb18030'**、**'gbk'**和**'gb2312'**。 |
| callback | Function | 是 | 回调函数。 |

**示例：**

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

批量数据写入API。需要由开发者实现此API，但不要直接调用。此API在写入数据时自动调用。使用异步回调返回结果。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Duplex-doWritev(chunks: string[] | Uint8Array[], callback: Function): void--><!--Device-Duplex-doWritev(chunks: string[] | Uint8Array[], callback: Function): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| chunks | string[] \| Uint8Array[] | 是 | 批量写入的数据数组。 |
| callback | Function | 是 | 回调函数。 |

**示例：**

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

<!--Device-Duplex-end(chunk?: string | Uint8Array, encoding?: string, callback?: Function): Writable--><!--Device-Duplex-end(chunk?: string | Uint8Array, encoding?: string, callback?: Function): Writable-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| chunk | string \| Uint8Array | 否 | 待写入的数据。默认值为**undefined**。 |
| encoding | string | 否 | 编码格式。默认值为**'utf8'**。目前支持**'utf8'**、**'gb18030'**、**'gbk'**和**'gb2312'**。 |
| callback | Function | 否 | 用于返回结果的回调函数。默认不调用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Writable](arkts-arkts-stream-writable-c.md) | 当前**Duplex**对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200039](../errorcode-utils.md#10200039-dotransform接口未实现) | The doTransform method has not been implemented for a class that inherits from Transform. |

**示例：**

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

设置可写流的默认编码格式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Duplex-setDefaultEncoding(encoding?: string): boolean--><!--Device-Duplex-setDefaultEncoding(encoding?: string): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| encoding | string | 否 | 默认编码格式。默认值为**'utf8'**。目前支持**'utf8'**、**'gb18030'**、**'gbk'**和**'gb2312'**。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 操作结果。**true**表示成功；**false**表示失败。 |

**示例：**

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

<!--Device-Duplex-uncork(): boolean--><!--Device-Duplex-uncork(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 操作结果。**true**表示成功；**false**表示失败。 |

**示例：**

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

<!--Device-Duplex-write(chunk?: string | Uint8Array, encoding?: string, callback?: Function): boolean--><!--Device-Duplex-write(chunk?: string | Uint8Array, encoding?: string, callback?: Function): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| chunk | string \| Uint8Array | 否 | 待写入的数据。不能为**null**、**undefined**或空字符串。 |
| encoding | string | 否 | 编码格式。默认值为**'utf8'**。目前支持**'utf8'**、**'gb18030'**、**'gbk'**和**'gb2312'**。 |
| callback | Function | 否 | 用于返回结果的回调函数。默认不调用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示可写流缓冲区中是否还有空间。**true**表示缓冲区中还有空间；**false**表示缓冲区已满，不建议继续写入数据。如果继续调用write函数，数据仍会添加到缓冲区，直到内存溢出。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200036](../errorcode-utils.md#10200036-流已经结束仍进行写操作) | The stream has been ended. |
| [10200037](../errorcode-utils.md#10200037-多次调用callback) | The callback is invoked multiple times consecutively. |
| [10200039](../errorcode-utils.md#10200039-dotransform接口未实现) | The doTransform method has not been implemented for a class that inherits from Transform. |

**示例：**

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

如果调用writable.write()是安全的，返回true，即表示流未被销毁、未出错或未结束。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Duplex-get writable(): boolean--><!--Device-Duplex-get writable(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

## writableCorked

```TypeScript
get writableCorked(): number
```

为完全释放流，需要调用writable.uncork()的次数。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Duplex-get writableCorked(): int--><!--Device-Duplex-get writableCorked(): int-End-->

**系统能力：** SystemCapability.Utils.Lang

## writableEnded

```TypeScript
get writableEnded(): boolean
```

是否已调用Writable.end。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Duplex-get writableEnded(): boolean--><!--Device-Duplex-get writableEnded(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

## writableFinished

```TypeScript
get writableFinished(): boolean
```

是否已调用Writable.end并刷新了所有缓冲区。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Duplex-get writableFinished(): boolean--><!--Device-Duplex-get writableFinished(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

## writableHighWatermark

```TypeScript
get writableHighWatermark(): number
```

highWatermark的值。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Duplex-get writableHighWatermark(): int--><!--Device-Duplex-get writableHighWatermark(): int-End-->

**系统能力：** SystemCapability.Utils.Lang

## writableLength

```TypeScript
get writableLength(): number
```

可刷新的数据大小，单位为字节或对象。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Duplex-get writableLength(): int--><!--Device-Duplex-get writableLength(): int-End-->

**系统能力：** SystemCapability.Utils.Lang

## writableObjectMode

```TypeScript
get writableObjectMode(): boolean
```

返回布尔值，表示是否处于ObjectMode。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Duplex-get writableObjectMode(): boolean--><!--Device-Duplex-get writableObjectMode(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

