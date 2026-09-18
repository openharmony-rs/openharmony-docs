# HashStream

The **HashStream** class is a utility for creating a message digest of data. You can use [createHash](../../../reference/apis-core-file-kit/js-apis-file-hash.md#hashcreatehash12) to create a **HashStream** instance.

**Inheritance/Implementation:** HashStream extends [stream.Transform](../../apis-arkts/arkts-apis/arkts-arkts-stream-transform-c.md)

**Since:** 12

**System capability:** SystemCapability.FileManagement.File.FileIO

## Modules to Import

```TypeScript
import { hash } from '@kit.CoreFileKit';
```

## digest

```TypeScript
digest(): string
```

Generates a message digest.

**Since:** 12

**System capability:** SystemCapability.FileManagement.File.FileIO

**Return value:**

| Type | Description |
| --- | --- |
| string | Hash value, which is a hexadecimal string consisting of digits and uppercase letters. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error |
| 13900042 | Unknown error |

**Examples**

```TypeScript
// Create a hash stream.
const hs = hash.createHash('sha256');
hs.update(new Uint8Array('1234567890'?.split('').map((x: string) => x.charCodeAt(0))).buffer);
hs.update(new Uint8Array('abcdefg'?.split('').map((x: string) => x.charCodeAt(0))).buffer);
const hashResult = hs.digest();
// 88A00F46836CD629D0B79DE98532AFDE3AEAD79A5C53E4848102F433046D0106
console.info(`hashResult: ${hashResult}`);
```

## update

```TypeScript
update(data: ArrayBuffer): void
```

Updates the data for generating a message digest. This API can be called multiple times.

**Since:** 12

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | ArrayBuffer | Yes | Data to be calculated. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error |
| 13900042 | Unknown error |

**Examples**

```TypeScript
// Create a hash stream.
const hs = hash.createHash('sha256');
hs.update(new Uint8Array('1234567890'?.split('').map((x: string) => x.charCodeAt(0))).buffer);
hs.update(new Uint8Array('abcdefg'?.split('').map((x: string) => x.charCodeAt(0))).buffer);
const hashResult = hs.digest();
// 88A00F46836CD629D0B79DE98532AFDE3AEAD79A5C53E4848102F433046D0106
console.info(`hashResult: ${hashResult}`);
```
