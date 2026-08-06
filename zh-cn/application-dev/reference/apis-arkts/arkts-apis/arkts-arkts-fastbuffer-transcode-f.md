# transcode

## transcode

```TypeScript
function transcode(source: FastBuffer | Uint8Array, fromEnc: string, toEnc: string): FastBuffer
```

将FastBuffer或Uint8Array对象从fromEnc编码转换为toEnc编码。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-fastbuffer-function transcode(source: FastBuffer | Uint8Array, fromEnc: string, toEnc: string): FastBuffer--><!--Device-fastbuffer-function transcode(source: FastBuffer | Uint8Array, fromEnc: string, toEnc: string): FastBuffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| Uint8Array | 是 | 待转码的FastBuffer或Uint8Array实例，提供需要重新编码的源数据。 |
| fromEnc | string | 是 | 当前编码格式。支持的格式范围为BufferEncoding。传入空字符串时，表示使用编码格式'utf8'。 |
| toEnc | string | 是 | 目标编码。支持的格式范围为BufferEncoding。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 将当前编码转换成目标编码，并返回一个新的FastBuffer对象。 |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let newBuf = fastbuffer.transcode(fastbuffer.from('buffer'), 'utf-8', 'ascii');
console.info('newBuf = ' + newBuf.toString('ascii'));
// 输出结果：newBuf = buffer
```

