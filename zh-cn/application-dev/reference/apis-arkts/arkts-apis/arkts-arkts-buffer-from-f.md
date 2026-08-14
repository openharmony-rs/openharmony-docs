# from

## from

```TypeScript
function from(array: double[]): Buffer
```

根据指定数组创建新的Buffer对象，数组中的每个元素作为对应位置的字节存储。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-buffer-function from(array: double[]): Buffer--><!--Device-buffer-function from(array: double[]): Buffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| array | double[] | 是 | 由0~255范围内的整数组成的数组，用于根据数组内容创建新的Buffer对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Buffer](arkts-arkts-buffer-buffer-c.md) | 新的Buffer对象。 |

## 示例

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

创建与`arrayBuffer`共享内存的指定长度的Buffer对象。共享内存意味着Buffer与arrayBuffer引用同一块内存区域，对Buffer数据的修改将同步反映到arrayBuffer中，反之亦然（注意：此方式避免内存拷贝，提升性能，但需注意内存释放时机）。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-buffer-function from(arrayBuffer: ArrayBuffer | SharedArrayBuffer, byteOffset?: number, length?: number): Buffer--><!--Device-buffer-function from(arrayBuffer: ArrayBuffer | SharedArrayBuffer, byteOffset?: number, length?: number): Buffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arrayBuffer | ArrayBuffer \| SharedArrayBuffer | 是 | 用于创建Buffer的ArrayBuffer或SharedArrayBuffer对象。 |
| byteOffset | number | 否 | 字节偏移量。指定从arrayBuffer起始位置偏移的字节数，创建的Buffer从该偏移位置开始。默认值：0。 |
| length | number | 否 | 字节长度， 默认值:（arrayBuffer.byteLength - byteOffset）。在传入null时字节长度为0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Buffer](arkts-arkts-buffer-buffer-c.md) | 返回一个Buffer对象，该对象与入参对象`arrayBuffer`共享相同的内存区域。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[byteOffset/length]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [byteOffset/length] |

## 示例

```TypeScript
import { buffer, JSON } from '@kit.ArkTS';

let ab = new ArrayBuffer(10);
let buf = buffer.from(ab, 0, 2);
console.info(JSON.stringify(buf)); // {"type":"Buffer","data":[0,0]}
```


## from

```TypeScript
function from(arrayBuffer: ArrayBuffer, byteOffset?: int, length?: int): Buffer
```

创建ArrayBuffer的视图，不复制底层内存。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-buffer-function from(arrayBuffer: ArrayBuffer, byteOffset?: int, length?: int): Buffer--><!--Device-buffer-function from(arrayBuffer: ArrayBuffer, byteOffset?: int, length?: int): Buffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arrayBuffer | ArrayBuffer | 是 | 用于创建视图的ArrayBuffer。 |
| byteOffset | int | 否 | byteOffset [byteOffset = 0] 暴露的第一个字节的索引。 该值应为整数。 |
| length | int | 否 | length [length = arrayBuffer.byteLength - byteOffset] 暴露的字节数。 该值应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Buffer](arkts-arkts-buffer-buffer-c.md) | 返回ArrayBuffer的视图。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "[byteOffset/length]" is out of range. It must be >= [left range] and <= [right range]. Received value is: [byteOffset/length] |

## 示例

```TypeScript
import { buffer } from '@kit.ArkTS';

let ab = new ArrayBuffer(10);
let buf = buffer.from(ab, 0, 2);
console.info(JSON.stringify(buf)); // {"type":"Buffer","data":[0,0]}
```


## from

```TypeScript
function from(buffer: Buffer | Uint8Array): Buffer
```

当入参为Buffer对象时，创建新的Buffer对象并复制入参Buffer对象的数据，然后返回新对象。 基于Uint8Array对象的内存创建新的Buffer对象并返回，新Buffer与原Uint8Array共享同一底层ArrayBuffer内存区域。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-buffer-function from(buffer: Buffer | Uint8Array): Buffer--><!--Device-buffer-function from(buffer: Buffer | Uint8Array): Buffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buffer | [Buffer](arkts-arkts-buffer-buffer-c.md) \| Uint8Array | 是 | 用于创建新Buffer的Buffer或Uint8Array对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Buffer](arkts-arkts-buffer-buffer-c.md) | 新的Buffer对象。 |

## 示例

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
function from(object: Object, offsetOrEncoding: int | string, length: int): Buffer
```

根据指定的`object`类型数据，创建新的Buffer对象。当object的valueOf()返回ArrayBuffer时，按字节偏移量和长度创建Buffer；其他类型则根据编码格式将对象值转换为Buffer。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-buffer-function from(object: Object, offsetOrEncoding: int | string, length: int): Buffer--><!--Device-buffer-function from(object: Object, offsetOrEncoding: int | string, length: int): Buffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| object | Object | 是 | 支持Symbol.toPrimitive或valueOf()的对象，valueOf()或Symbol.toPrimitive的返回值支持string和ArrayBuffer等类型。 |
| offsetOrEncoding | int \| string | 是 | 字节偏移量或编码格式。当object的valueOf()返回值为ArrayBuffer时，作为字节偏移量；其他情况下作为编码格式。 |
| length | int | 是 | 字节长度（此入参仅在object的valueOf()返回值为ArrayBuffer时生效，取值范围：0 <= length <= ArrayBuffer.byteLength，超出范 围时报错: 10200001）。其他情况下可填任意number类型值，该参数不会对结果产生影响。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Buffer](arkts-arkts-buffer-buffer-c.md) | 返回新的Buffer对象。 |

## 示例

```TypeScript
import { buffer, JSON } from '@kit.ArkTS';

let buf = buffer.from(new String('this is a test'), 'utf8', 14);
console.info(JSON.stringify(buf)); // {"type":"Buffer","data":[116,104,105,115,32,105,115,32,97,32,116,101,115,116]}
```


## from

```TypeScript
function from(string: String, encoding?: BufferEncoding): Buffer
```

根据指定编码格式的字符串，创建新的Buffer对象，字符串按编码格式转换为字节序列存入Buffer。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-buffer-function from(string: String, encoding?: BufferEncoding): Buffer--><!--Device-buffer-function from(string: String, encoding?: BufferEncoding): Buffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| string | String | 是 | 要编码创建Buffer对象的字符串内容。 |
| encoding | BufferEncoding | 否 | 编码格式。默认值：'utf8'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Buffer](arkts-arkts-buffer-buffer-c.md) | 返回新的Buffer对象。 |

## 示例

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf1 = buffer.from('this is a test');
let buf2 = buffer.from('7468697320697320612074c3a97374', 'hex');

console.info(buf1.toString());
// 输出结果：this is a test
console.info(buf2.toString());
// 输出结果：this is a tést
```

