# Transform

A special duplex stream that supports data conversion and result output. The **Transform** class inherits from [Duplex](arkts-arkts-stream-duplex-c.md) and supports all the APIs in **Duplex**.

**Inheritance/Implementation:** Transform extends [Duplex](arkts-arkts-stream-duplex-c.md)

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

A constructor used to create a **Transform** object.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Examples**

```TypeScript
let transform = new stream.Transform();
```

## doFlush

```TypeScript
doFlush(callback: Function): void
```

Called at the end of the stream to process the remaining data. This API uses an asynchronous callback to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Function | Yes | Callback function. |

**Examples**

```TypeScript
class TestTransform extends stream.Transform {
  constructor() {
    super();
  }

  doTransform(chunk: string, encoding: string, callback: Function) {
    callback();
  }

  doFlush(callback: Function) {
    callback(null, 'test');
  }
}

let transform = new TestTransform();
transform.end('my test');
transform.on('data', (data) => {
  console.info("data is", data.data); // data is test
});
```

## doTransform

```TypeScript
doTransform(chunk: string, encoding: string, callback: Function): void
```

Converts or processes input data chunks and uses a callback to notify that the processing is complete.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| chunk | string | Yes | Data to write. |
| encoding | string | Yes | Encoding format. Currently, **'utf8'**, **'gb18030'**, **'gbk'**, and **'gb2312'** are supported. |
| callback | Function | Yes | Callback function. |

**Examples**

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
