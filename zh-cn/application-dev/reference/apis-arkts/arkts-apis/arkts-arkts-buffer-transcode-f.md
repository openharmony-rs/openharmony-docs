# transcode

## 导入模块

```TypeScript
import { buffer } from '@kit.ArkTS';
```

## transcode

```TypeScript
function transcode(source: Buffer | Uint8Array, fromEnc: string, toEnc: string): Buffer
```

将Buffer或Uint8Array对象从一种字符编码重新编码为另一种。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-buffer-function transcode(source: Buffer | Uint8Array, fromEnc: string, toEnc: string): Buffer--><!--Device-buffer-function transcode(source: Buffer | Uint8Array, fromEnc: string, toEnc: string): Buffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | Buffer \| Uint8Array | 是 | 实例对象。 |
| fromEnc | string | 是 | 当前编码。支持的格式范围为[BufferEncoding](arkts-arkts-buffer-bufferencoding-t.md)。 |
| toEnc | string | 是 | 目标编码。支持的格式范围为[BufferEncoding](arkts-arkts-buffer-bufferencoding-t.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Buffer](arkts-arkts-buffer-buffer-c.md) | 将当前编码转换成目标编码，并返回一个新的Buffer对象。 |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let newBuf = buffer.transcode(buffer.from('€'), 'utf-8', 'ascii');
console.info("newBuf = " + newBuf.toString('ascii'));
// 输出结果：newBuf = ,

```

