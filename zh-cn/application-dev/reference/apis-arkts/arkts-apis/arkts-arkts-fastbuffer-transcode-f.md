# transcode

## transcode

```TypeScript
function transcode(source: FastBuffer | Uint8Array, fromEnc: string, toEnc: string): FastBuffer
```

将FastBuffer或Uint8Array对象从fromEnc编码转换为toEnc编码。适用于需要在不同编码格式之间转换数据的场景。例如，将UTF-8编码的数据转换为Latin1编码，以便在仅支持ASCII的系统中处理。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-fastbuffer-function transcode(source: FastBuffer | Uint8Array, fromEnc: string, toEnc: string): FastBuffer--><!--Device-fastbuffer-function transcode(source: FastBuffer | Uint8Array, fromEnc: string, toEnc: string): FastBuffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | [FastBuffer](arkts-arkts-fastbuffer-fastbuffer-c.md) \| Uint8Array | 是 | 需要进行编码转换的源数据对象，将从fromEnc编码转换为toEnc编码。 |
| fromEnc | string | 是 | 当前编码格式。支持的格式范围为'ascii' \| 'utf8' \| 'utf16le' \| 'ucs2' \| 'latin1' \| 'binary'。传入空字符串时， 表示使用编码格式'utf8'。 |
| toEnc | string | 是 | 目标编码。支持的格式范围为'ascii' \| 'utf8' \| 'utf16le' \| 'ucs2' \| 'latin1' \| 'binary'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FastBuffer](arkts-arkts-fastbuffer-fastbuffer-c.md) | 将当前编码转换成目标编码，并返回一个新的FastBuffer对象。 |

## 示例

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let newBuf = fastbuffer.transcode(fastbuffer.from('buffer'), 'utf-8', 'ascii');
console.info('newBuf = ' + newBuf.toString('ascii'));
// 输出结果：newBuf = buffer
```

