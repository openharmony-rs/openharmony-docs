# Transform

一种特殊的双工流，支持数据转换和结果输出。**Transform**类继承自[Duplex](arkts-arkts-stream-duplex-c.md#Duplex)，支持**Duplex**中的所有API。

**继承/实现关系：** Transform extends [Duplex](arkts-arkts-stream-duplex-c.md#Duplex)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-stream-class Transform--><!--Device-stream-class Transform-End-->

**系统能力：** SystemCapability.Utils.Lang

## constructor

```TypeScript
constructor()
```

创建**Transform**对象的构造函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Transform-constructor()--><!--Device-Transform-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

## 示例

```TypeScript
let transformStream = new stream.Transform();
```

## doFlush

```TypeScript
doFlush(callback: Function): void
```

在流结束时调用，用于处理剩余数据。使用异步回调返回结果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Transform-doFlush(callback: Function): void--><!--Device-Transform-doFlush(callback: Function): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Function | 是 | 回调函数。 |

## 示例

ArkTS-Dyn示例：

```TypeScript
class TestTransform extends stream.Transform {
  constructor() {
    super();
  }

  doTransform(chunk: string, encoding: string, callback: Function) {
    callback();
  }

  doFlush(callback: Function) {
    callback(null, "test");
  }
}

let transformStream = new TestTransform();
transformStream.end("my test");
transformStream.on("data", (data) => {
  console.info("data is", data.data); // data is test
});
```

ArkTS-Sta示例：

```TypeScript
class TestTransform extends stream.Transform {
  constructor() {
    super();
  }

  doTransform(chunk: string, encoding: string, callback: Function) {
    callback.unsafeCall();
  }

  doFlush(callback: Function) {
    callback.unsafeCall("test");
  }
}

let transformStream = new TestTransform();
transformStream.on("data", (data: Object) => {
  console.info("StreamTest data is", data); // 期望结果: data is test
});
transformStream.end("my test");
```

## doTransform

```TypeScript
doTransform(chunk: string, encoding: string, callback: Function): void
```

转换或处理输入的数据块，并通过回调通知处理完成。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Transform-doTransform(chunk: string, encoding: string, callback: Function): void--><!--Device-Transform-doTransform(chunk: string, encoding: string, callback: Function): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| chunk | string | 是 | 需要写入的数据。 |
| encoding | string | 是 | 字符编码类型。当前版本支持'utf8'、'gb18030'、'gbk'以及'gb2312'。 |
| callback | Function | 是 | 回调函数。 |

## 示例

ArkTS-Dyn示例：

```TypeScript
class TestTransform extends stream.Transform {
  constructor() {
    super();
  }

  doTransform(chunk: string, encoding: string, callback: Function) {
    let stringChunk = chunk.toString().toUpperCase();
    console.info("Transform test doTransform", stringChunk); // Transform test doTransform HELLO
    this.push(stringChunk);
    callback();
  }
}

let transformStream = new TestTransform();
transformStream.write("hello");
```

ArkTS-Sta示例：

```TypeScript
class TestTransform extends stream.Transform {
  constructor() {
    super();
  }

  doTransform(chunk: string, encoding: string, callback: Function) {
    let stringChunk = chunk.toString().toUpperCase();
    console.info("Transform test doTransform", stringChunk); // 期望结果: Transform test doTransform HELLO
    this.push(stringChunk);
    callback.unsafeCall();
  }
}

let transformStream = new TestTransform();
transformStream.write("hello");
```

