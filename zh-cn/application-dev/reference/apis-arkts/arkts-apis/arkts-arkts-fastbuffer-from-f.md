# from

## 导入模块

```TypeScript
import { fastbuffer } from '@kit.ArkTS';
```

## from

```TypeScript
function from(array: number[]): FastBuffer
```

根据指定数组创建新的FastBuffer对象。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-fastbuffer-function from(array: number[]): FastBuffer--><!--Device-fastbuffer-function from(array: number[]): FastBuffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| array | number[] | 是 | 指定数组，数组内各元素的取值范围为[0, 255]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FastBuffer](arkts-arkts-fastbuffer-fastbuffer-c.md) | 新的FastBuffer对象。 |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.from([0x62, 0x75, 0x66, 0x66, 0x65, 0x72]);
console.info(buf.toString('hex'));
// 输出结果：627566666572

```


## from

```TypeScript
function from(arrayBuffer: ArrayBuffer | SharedArrayBuffer, byteOffset?: number, length?: number): FastBuffer
```

创建与`arrayBuffer`共享内存的指定长度的FastBuffer对象。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-fastbuffer-function from(arrayBuffer: ArrayBuffer | SharedArrayBuffer, byteOffset?: number, length?: number): FastBuffer--><!--Device-fastbuffer-function from(arrayBuffer: ArrayBuffer | SharedArrayBuffer, byteOffset?: number, length?: number): FastBuffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arrayBuffer | ArrayBuffer \| SharedArrayBuffer | 是 | 实例对象。 |
| byteOffset | number | 否 | 字节偏移量，默认值：0。 |
| length | number | 否 | 字节长度，默认值：（arrayBuffer.byteLength - byteOffset）。取值范围：0 &lt;= length &lt;= arrayBuffer.byteLength - byteOffset。传入null时返回空FastBuffer。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FastBuffer](arkts-arkts-fastbuffer-fastbuffer-c.md) | 返回一个FastBuffer对象，该对象与入参对象`arrayBuffer`共享相同的内存区域。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | Range error. Possible causes:The value of the parameter is not within the specified range. |
| [10200068](../errorcode-utils.md#10200068-引用已释放或分离的arraybuffer) | The underlying ArrayBuffer is null or detach. |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let arrayBuffer = new ArrayBuffer(10);
let buf = fastbuffer.from(arrayBuffer, 0, 2);
console.info(buf.length.toString());
// 输出结果：2

```


## from

```TypeScript
function from(buffer: FastBuffer | Uint8Array): FastBuffer
```

当入参为FastBuffer对象时，创建新的FastBuffer对象并复制入参FastBuffer对象的数据，然后返回新对象。

当入参为Uint8Array对象时，基于Uint8Array对象的内存创建新的FastBuffer对象并返回，保持数据的内存关联。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-fastbuffer-function from(buffer: FastBuffer | Uint8Array): FastBuffer--><!--Device-fastbuffer-function from(buffer: FastBuffer | Uint8Array): FastBuffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buffer | FastBuffer \| Uint8Array | 是 | 对象数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FastBuffer](arkts-arkts-fastbuffer-fastbuffer-c.md) | 返回新的FastBuffer对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200068](../errorcode-utils.md#10200068-引用已释放或分离的arraybuffer) | The underlying ArrayBuffer is null or detach. |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

// 从字符串创建FastBuffer对象
let buf1 = fastbuffer.from('buffer');
// 以FastBuffer对象类型创建新的FastBuffer对象
let buf2 = fastbuffer.from(buf1);
console.info(buf2.toString());
// 输出结果：buffer

// 以Uint8Array对象类型进行创建FastBuffer对象，保持对象间内存共享
let uint8Array = new Uint8Array(10);
let buf3 = fastbuffer.from(uint8Array);
// 修改buf3以验证内存共享：buf3修改后uint8Array同步变化
buf3.fill(1);
console.info('uint8Array:', uint8Array);
// 输出结果：1,1,1,1,1,1,1,1,1,1

```


## from

```TypeScript
function from(value: string, encoding?: BufferEncoding): FastBuffer
```

根据指定编码格式的字符串，创建新的FastBuffer对象。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-fastbuffer-function from(value: string, encoding?: BufferEncoding): FastBuffer--><!--Device-fastbuffer-function from(value: string, encoding?: BufferEncoding): FastBuffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | 字符串。 |
| encoding | [BufferEncoding](arkts-arkts-fastbuffer-bufferencoding-t.md) | 否 | 编码格式。默认值：'utf8'。传入无法识别的encoding会抛出TypeError。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FastBuffer](arkts-arkts-fastbuffer-fastbuffer-c.md) | 返回新的FastBuffer对象。 |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

// 从普通字符串创建FastBuffer对象
let buf1 = fastbuffer.from('this is a test');
// 从hex编码字符串创建FastBuffer对象
let buf2 = fastbuffer.from('7468697320697320612074c3a97374', 'hex');

console.info(buf1.toString());
// 输出结果：this is a test
console.info(buf2.toString());
// 输出结果：this is a tést

```

