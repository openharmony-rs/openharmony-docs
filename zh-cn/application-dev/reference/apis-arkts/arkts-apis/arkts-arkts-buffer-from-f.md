# from

## 导入模块

```TypeScript
import { buffer } from '@kit.ArkTS';
```

## from

```TypeScript
function from(array: number[]): Buffer
```

根据指定数组创建新的Buffer对象。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-buffer-function from(array: double[]): Buffer--><!--Device-buffer-function from(array: double[]): Buffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| array | number[] | 是 | 指定数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Buffer](arkts-arkts-buffer-buffer-c.md) | 新的Buffer对象。 |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.from([0x62, 0x75, 0x66, 0x66, 0x65, 0x72]);
console.info(buf.toString('hex'));
// 输出结果：627566666572

```


## from

```TypeScript
function from(arrayBuffer: ArrayBuffer | SharedArrayBuffer, byteOffset?: number, length?: number): Buffer
```

创建与arrayBuffer共享内存的指定长度的Buffer对象。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-buffer-function from(arrayBuffer: ArrayBuffer | SharedArrayBuffer, byteOffset?: number, length?: number): Buffer--><!--Device-buffer-function from(arrayBuffer: ArrayBuffer | SharedArrayBuffer, byteOffset?: number, length?: number): Buffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arrayBuffer | ArrayBuffer \| SharedArrayBuffer | 是 | 实例对象，用于共享内存。 |
| byteOffset | number | 否 | 字节偏移量。默认值：0。 |
| length | number | 否 | 字节长度。默认值：（arrayBuffer.byteLength - byteOffset）。在传入null时字节长度为0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Buffer](arkts-arkts-buffer-buffer-c.md) | 返回一个Buffer对象，该对象与入参对象arrayBuffer共享相同的内存区域。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[byteOffset/length]" is out of range.It must be &gt;= [left range] and &lt;= [right range]. Received value is: [byteOffset/length] |

**示例：**

```TypeScript
import { buffer, JSON } from '@kit.ArkTS';

let ab = new ArrayBuffer(10);
let buf = buffer.from(ab, 0, 2);
console.info(JSON.stringify(buf)); // {"type":"Buffer","data":[0,0]}

```


## from

```TypeScript
function from(buffer: Buffer | Uint8Array): Buffer
```

当入参为Buffer对象时，创建新的Buffer对象并复制入参Buffer对象的数据，然后返回新对象。当入参为Uint8Array对象时，基于Uint8Array对象的内存创建新的Buffer对象并返回，保持数据的内存关联。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-buffer-function from(buffer: Buffer | Uint8Array): Buffer--><!--Device-buffer-function from(buffer: Buffer | Uint8Array): Buffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buffer | Buffer \| Uint8Array | 是 | 对象数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Buffer](arkts-arkts-buffer-buffer-c.md) | 新的Buffer对象。 |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

// 以Buffer对象类型进行创建新的Buffer对象
let buf1 = buffer.from('buffer');
let buf2 = buffer.from(buf1);

// 以Uint8Array对象类型进行创建Buffer对象，保持对象间内存共享
let uint8Array = new Uint8Array(10);
let buf3 = buffer.from(uint8Array);
buf3.fill(1);
console.info("uint8Array:", uint8Array);
// 输出结果：1,1,1,1,1,1,1,1,1,1

```


## from

```TypeScript
function from(object: Object, offsetOrEncoding: number | string, length: number): Buffer
```

根据指定的object类型数据，创建新的Buffer对象。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-buffer-function from(object: Object, offsetOrEncoding: int | string, length: int): Buffer--><!--Device-buffer-function from(object: Object, offsetOrEncoding: int | string, length: int): Buffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| object | Object | 是 | 支持Symbol.toPrimitive或valueOf()的对象。 |
| offsetOrEncoding | number \| string | 是 | 字节偏移量或编码格式。 |
| length | number | 是 | 字节长度（此入参仅在object的valueOf()返回值为ArrayBuffer时生效，取值范围：0 &lt;= length &lt;= ArrayBuffer.byteLength，超出范围时报错: 10200001）。其他情况下可填任意number类型值，该参数不会对结果产生影响。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Buffer](arkts-arkts-buffer-buffer-c.md) | 新的Buffer对象。 |

**示例：**

```TypeScript
import { buffer, JSON } from '@kit.ArkTS';

let buf = buffer.from(new String('this is a test'), 'utf8', 14);
console.info(JSON.stringify(buf)); // {"type":"Buffer","data":[116,104,105,115,32,105,115,32,97,32,116,101,115,116]}

```


## from

```TypeScript
function from(string: String, encoding?: BufferEncoding): Buffer
```

根据指定编码格式的字符串，创建新的Buffer对象。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-buffer-function from(string: String, encoding?: BufferEncoding): Buffer--><!--Device-buffer-function from(string: String, encoding?: BufferEncoding): Buffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| string | String | 是 | 字符串。 |
| encoding | [BufferEncoding](arkts-arkts-fastbuffer-bufferencoding-t.md) | 否 | 编码格式。默认值：'utf8'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Buffer](arkts-arkts-buffer-buffer-c.md) | 新的Buffer对象。 |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.from('this is a test');
let buf2 = buffer.from('7468697320697320612074c3a97374', 'hex');

console.info(buf1.toString());
// 输出结果：this is a test
console.info(buf2.toString());
// 输出结果：this is a tést

```

