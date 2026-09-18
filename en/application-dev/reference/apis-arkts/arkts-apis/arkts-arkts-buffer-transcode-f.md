# transcode

## Modules to Import

```TypeScript
import { buffer } from '@kit.ArkTS';
```

## transcode

```TypeScript
function transcode(source: Buffer | Uint8Array, fromEnc: string, toEnc: string): Buffer
```

Transcodes a **Buffer** or **Uint8Array** object from one encoding format to another.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| source | Buffer &#124; Uint8Array | Yes | Instance object. |
| fromEnc | string | Yes | Current encoding format. For details about the supported formats, see [BufferEncoding](arkts-arkts-buffer-bufferencoding-t.md). |
| toEnc | string | Yes | Target encoding format. For details about the supported formats, see [BufferEncoding](arkts-arkts-buffer-bufferencoding-t.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Buffer | New **Buffer** object in the target encoding format. |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let newBuf = buffer.transcode(buffer.from('€'), 'utf-8', 'ascii');
console.info("newBuf = " + newBuf.toString('ascii'));
// Output: newBuf = ,
```
