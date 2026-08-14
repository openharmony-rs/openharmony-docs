# byteLength

## byteLength

```TypeScript
function byteLength(
    string: string | Buffer | TypedArray | DataView | ArrayBuffer | SharedArrayBuffer,
    encoding?: BufferEncoding
  ): number
```

根据不同的编码格式，返回指定数据的字节数。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-buffer-function byteLength(    string: string | Buffer | TypedArray | DataView | ArrayBuffer | SharedArrayBuffer,    encoding?: BufferEncoding  ): number--><!--Device-buffer-function byteLength(    string: string | Buffer | TypedArray | DataView | ArrayBuffer | SharedArrayBuffer,    encoding?: BufferEncoding  ): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| string | string \| [Buffer](arkts-arkts-buffer-buffer-c.md) \| TypedArray \| DataView \| ArrayBuffer \| SharedArrayBuffer | 是 | 要计算字节长度的字符串或其他数据对象。 |
| encoding | BufferEncoding | 否 | 编码格式（string参数为string类型时才有意义）。默认值：'utf8'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回指定字符串的字节数。 |

## 示例

```TypeScript
import { buffer } from '@kit.ArkTS';

let str = '\u00bd + \u00bc = \u00be';
console.info(`${str}: ${str.length} characters, ${buffer.byteLength(str, 'utf-8')} bytes`);
// 输出结果：½ + ¼ = ¾: 9 characters, 12 bytes
```


## byteLength

```TypeScript
function byteLength(
    doc: string | Buffer | TypedArray | DataView | ArrayBuffer,
    encoding?: BufferEncoding
  ): int
```

根据不同的编码格式，返回指定数据的字节数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-buffer-function byteLength(    doc: string | Buffer | TypedArray | DataView | ArrayBuffer,    encoding?: BufferEncoding  ): int--><!--Device-buffer-function byteLength(    doc: string | Buffer | TypedArray | DataView | ArrayBuffer,    encoding?: BufferEncoding  ): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| doc | string \| [Buffer](arkts-arkts-buffer-buffer-c.md) \| TypedArray \| DataView \| ArrayBuffer | 是 | 要计算字节长度的字符串或其他数据对象。 |
| encoding | BufferEncoding | 否 | 编码格式。默认值：'utf8'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回指定字符串的字节数 |

## 示例

```TypeScript
import { buffer } from '@kit.ArkTS';

let str = '\u00bd + \u00bc = \u00be';
console.info(`${str}: ${str.length} characters, ${buffer.byteLength(str, 'utf-8')} bytes`);
// 输出结果：½ + ¼ = ¾: 9 characters, 12 bytes
```

