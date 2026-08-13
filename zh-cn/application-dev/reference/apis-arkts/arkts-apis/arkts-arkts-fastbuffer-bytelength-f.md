# byteLength

## byteLength

```TypeScript
function byteLength(value: string | FastBuffer | TypedArray | DataView | ArrayBuffer | SharedArrayBuffer, encoding?: BufferEncoding): number
```

根据不同的编码格式，返回指定内容的字节数。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-fastbuffer-function byteLength(value: string | FastBuffer | TypedArray | DataView | ArrayBuffer | SharedArrayBuffer, encoding?: BufferEncoding): number--><!--Device-fastbuffer-function byteLength(value: string | FastBuffer | TypedArray | DataView | ArrayBuffer | SharedArrayBuffer, encoding?: BufferEncoding): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| [FastBuffer](arkts-arkts-fastbuffer-fastbuffer-c.md) \| TypedArray \| DataView \| ArrayBuffer \| SharedArrayBuffer | 是 | 指定用于计算字节长度的内容。 |
| encoding | BufferEncoding | 否 | 编码格式。默认值：'utf8'。传入无法识别的encoding会抛出TypeError。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回指定内容的字节数。 |

## 示例

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let str = 'hello world';
console.info(`${str}: ${str.length} characters, ${fastbuffer.byteLength(str, 'utf-8')} bytes`);
// 输出结果：hello world: 11 characters, 11 bytes

str = '\u00bd + \u00bc = \u00be';
console.info(`${str}: ${str.length} characters, ${fastbuffer.byteLength(str, 'utf-8')} bytes`);
// 输出结果：½ + ¼ = ¾: 9 characters, 12 bytes
```

