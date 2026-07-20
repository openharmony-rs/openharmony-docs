# Blob

将数据处理为blob类型。

**起始版本：** 9

<!--Device-buffer-class Blob--><!--Device-buffer-class Blob-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { buffer } from '@kit.ArkTS';
```

<a id="arraybuffer"></a>
## arrayBuffer

```TypeScript
arrayBuffer(): Promise<ArrayBuffer>
```

将Blob数据放入ArrayBuffer中返回，使用Promise进行异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Blob-arrayBuffer(): Promise<ArrayBuffer>--><!--Device-Blob-arrayBuffer(): Promise<ArrayBuffer>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ArrayBuffer&gt; | Promise对象，返回包含Blob数据的ArrayBuffer。 |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let blob: buffer.Blob = new buffer.Blob(['a', 'b', 'c']);
let pro = blob.arrayBuffer();
pro.then((val: ArrayBuffer) => {
  let uint8Array: Uint8Array = new Uint8Array(val);
  console.info(uint8Array.toString());
  // 输出结果：97,98,99
});

```

<a id="constructor"></a>
## constructor

```TypeScript
constructor(sources: string[] | ArrayBuffer[] | TypedArray[] | DataView[] | Blob[], options?: Object)
```

Blob的构造函数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Blob-constructor(sources: string[] | ArrayBuffer[] | TypedArray[] | DataView[] | Blob[], options?: Object)--><!--Device-Blob-constructor(sources: string[] | ArrayBuffer[] | TypedArray[] | DataView[] | Blob[], options?: Object)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sources | string[] \| ArrayBuffer[] \| TypedArray[] \| DataView[] \| Blob[] | 是 | Blob实例的数据源。 |
| options | Object | 否 | options：<br/>- **endings**：含义为结束符'\n'的字符串如何被输出，值为'native'或'transparent'。'native'代表行结束符会跟随系统。'transparent'代表会保持Blob中保存的结束符不变。默认值：'transparent'。<br/>   - **type**：Blob内容类型。其目的是让类型传达数据的MIME媒体类型，但是不执行类型格式的验证。默认值：''。 |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let blob: buffer.Blob  = new buffer.Blob(['a', 'b', 'c']);

class option {
  endings: string = "";
  type: string = "";
}
let o1: option = {endings:'native', type: 'MIME'}
let blob1: buffer.Blob = new buffer.Blob(['a', 'b', 'c'], o1);

```

<a id="slice"></a>
## slice

```TypeScript
slice(start?: number, end?: number, type?: string): Blob
```

创建并返回一个包含原Blob对象中指定长度数据的新Blob对象。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Blob-slice(start?: int, end?: int, type?: string): Blob--><!--Device-Blob-slice(start?: int, end?: int, type?: string): Blob-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | number | 否 | 起始位置。默认值：0。 |
| end | number | 否 | 结束位置。默认值：原Blob对象中的数据长度。 |
| type | string | 否 | 内容类型。默认值：''。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Blob](arkts-arkts-buffer-blob-c.md) | 新的Blob实例对象。 |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let blob: buffer.Blob = new buffer.Blob(['a', 'b', 'c']);
let blob2 = blob.slice(0, 2);
let blob3 = blob.slice(0, 2, "MIME");
console.info("type:", blob3.type); // type: MIME

```

<a id="text"></a>
## text

```TypeScript
text(): Promise<string>
```

使用utf8解码并返回字符串。使用Promise进行异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Blob-text(): Promise<string>--><!--Device-Blob-text(): Promise<string>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回以utf8解码后的字符串。 |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let blob: buffer.Blob = new buffer.Blob(['a', 'b', 'c']);
let pro = blob.text();
pro.then((val: string) => {
  console.info(val);
  // 输出结果：abc
});

```

## size

```TypeScript
get size(): number
```

Blob实例的总字节大小。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Blob-get size(): int--><!--Device-Blob-get size(): int-End-->

**系统能力：** SystemCapability.Utils.Lang

## type

```TypeScript
get type(): string
```

Blob实例的内容类型。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Blob-get type(): string--><!--Device-Blob-get type(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

