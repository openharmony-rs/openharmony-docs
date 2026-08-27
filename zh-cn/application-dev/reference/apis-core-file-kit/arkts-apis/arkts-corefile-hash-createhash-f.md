# createHash

## 导入模块

```TypeScript
import { hash } from '@kit.CoreFileKit';
```

## createHash

```TypeScript
function createHash(algorithm: string): HashStream
```

创建并返回HashStream对象，用于生成哈希摘要。可以指定哈希计算采用的算法。HashStream采用流式处理机制，支持分批次更新数据，适用于大文件或数据流的哈希计算，避免一次性加载大文件到内存。

> **说明：**
> 
> HashStream采用流式处理机制，支持分批次更新数据，适用于大文件或数据流的哈希计算，避免一次性加载大文件到内存。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| algorithm | string | 是 | 哈希计算采用的算法。可选 "md5"、"sha1" 或 "sha256"。建议采用安全强度更高的 "sha256"。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [HashStream](arkts-corefile-hash-hashstream-c.md) | HashStream类的实例，用于生成哈希摘要。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error |
| 13900020 | Invalid argument |
| 13900042 | Unknown error |

**示例**

```TypeScript
// pages/xxx.ets
import { fileIo } from '@kit.CoreFileKit';

function hashFileWithStream() {
  const filePath = pathDir + "/test.txt";
  // 创建文件可读流
  const rs = fileIo.createReadStream(filePath);
  // 创建哈希流
  const hs = hash.createHash('sha256');
  rs.on('data', (emitData) => {
    const data = emitData?.data;
    hs.update(new Uint8Array(data?.split('').map((x: string) => x.charCodeAt(0))).buffer);
  });
  rs.on('close', async () => {
    const hashResult = hs.digest();
    const fileHash = await hash.hash(filePath, 'sha256');
    console.info(`Succeeded in calculating file hash. hashResult: ${hashResult}, fileHash: ${fileHash}`);
  });
}
```
