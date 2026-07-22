# byteLength

## 导入模块

```TypeScript
import { buffer } from '@kit.ArkTS';
```

## byteLength

```TypeScript
function byteLength(
    string: string | Buffer | TypedArray | DataView | ArrayBuffer | SharedArrayBuffer,
    encoding?: BufferEncoding
  ): number
```

根据不同的编码格式，返回指定字符串的字节数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-buffer-function byteLength(    string: string | Buffer | TypedArray | DataView | ArrayBuffer | SharedArrayBuffer,    encoding?: BufferEncoding  ): number--><!--Device-buffer-function byteLength(    string: string | Buffer | TypedArray | DataView | ArrayBuffer | SharedArrayBuffer,    encoding?: BufferEncoding  ): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| string | string \| Buffer \| TypedArray \| DataView \| ArrayBuffer \| SharedArrayBuffer | 是 | 指定字符串。 |
| encoding | [BufferEncoding](arkts-arkts-fastbuffer-bufferencoding-t.md) | 否 | 编码格式。默认值：'utf8'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回指定字符串的字节数。 |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let str = '\u00bd + \u00bc = \u00be';
console.info(`${str}: ${str.length} characters, ${buffer.byteLength(str, 'utf-8')} bytes`);
// 输出结果：½ + ¼ = ¾: 9 characters, 12 bytes

```

