# Transform

一种特殊的双工流，支持数据转换和结果输出。**Transform**类继承自[Duplex](arkts-arkts-stream-duplex-c.md)，支持**Duplex**中的所有API。

**继承/实现关系：** Transform extends [Duplex](arkts-arkts-stream-duplex-c.md)

**起始版本：** 12

<!--Device-stream-class Transform extends Duplex--><!--Device-stream-class Transform extends Duplex-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { stream } from '@kit.ArkTS';
```

## constructor

```TypeScript
constructor()
```

创建**Transform**对象的构造函数。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Transform-constructor()--><!--Device-Transform-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

**示例：**

```TypeScript
let transform = new stream.Transform();

```

## doFlush

```TypeScript
doFlush(callback: Function): void
```

在流结束时调用，用于处理剩余数据。使用异步回调返回结果。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Transform-doFlush(callback: Function): void--><!--Device-Transform-doFlush(callback: Function): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Function | 是 | 回调函数。 |

**示例：**

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

let transform = new TestTransform();
transform.end("my test");
transform.on("data", (data) => {
  console.info("data is", data.data); // data is test
});

```

## doTransform

```TypeScript
doTransform(chunk: string, encoding: string, callback: Function): void
```

转换或处理输入的数据块，并通过回调通知处理完成。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Transform-doTransform(chunk: string, encoding: string, callback: Function): void--><!--Device-Transform-doTransform(chunk: string, encoding: string, callback: Function): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| chunk | string | 是 | 待写入的数据。 |
| encoding | string | 是 | 编码格式。目前支持**'utf8'**、**'gb18030'**、**'gbk'**和**'gb2312'**。 |
| callback | Function | 是 | 回调函数。 |

**示例：**

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

let tr = new TestTransform();
tr.write("hello");

```

