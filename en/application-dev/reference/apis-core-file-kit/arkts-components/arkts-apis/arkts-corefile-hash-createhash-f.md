# createHash

## Modules to Import

```TypeScript
import { hash } from '@kit.CoreFileKit';
```

## createHash

```TypeScript
function createHash(algorithm: string): HashStream
```

Creates a **HashStream** instance, which can be used to generate a message digest (a hash value) using the given algorithm.

**Since:** 12

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| algorithm | string | Yes | Algorithm used to calculate the hash value. The value can be **md5**, **sha1**, or **sha256**. **sha256** is recommended for security purposes. |

**Return value:**

| Type | Description |
| --- | --- |
| [HashStream](arkts-corefile-hash-hashstream-c.md) | **HashStream** instance created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error |
| 13900020 | Invalid argument |
| 13900042 | Unknown error |

**Examples**

```TypeScript
// pages/xxx.ets
import { fileIo } from '@kit.CoreFileKit';

function hashFileWithStream() {
  const filePath = pathDir + "/test.txt";
  // Create a readable stream.
  const rs = fileIo.createReadStream(filePath);
  // Create a hash stream.
  const hs = hash.createHash('sha256');
  rs.on('data', (emitData) => {
    const data = emitData?.data;
    hs.update(new Uint8Array(data?.split('').map((x: string) => x.charCodeAt(0))).buffer);
  });
  rs.on('close', async () => {
    const hashResult = hs.digest();
    const fileHash = await hash.hash(filePath, 'sha256');
    console.info(`hashResult: ${hashResult}, fileHash: ${fileHash}`);
  });
}
```
