# alloc

## Modules to Import

```TypeScript
import { buffer } from '@kit.ArkTS';
```

## alloc

```TypeScript
function alloc(size: number, fill?: string | Buffer | number, encoding?: BufferEncoding): Buffer
```

Creates and initializes a **Buffer** object of the specified length.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | number | Yes | Size of the **Buffer** object to create, in bytes. |
| fill | string &#124; Buffer &#124; number | No | Value to be filled in the buffer. The default value is **0**.<br>**Since:** 9 - 10 |
| encoding | BufferEncoding | No | Encoding format (valid only when **fill** is a string). The default value is **'utf8'**. |

**Return value:**

| Type | Description |
| --- | --- |
| Buffer | **Buffer** object created. |

**Examples**

```TypeScript
import { buffer, JSON } from '@kit.ArkTS';

let buf1 = buffer.alloc(5);
console.info(JSON.stringify(buf1)); // {"type":"Buffer","data":[0,0,0,0,0]}

let buf2 = buffer.alloc(5, 'a');
console.info(JSON.stringify(buf2)); // {"type":"Buffer","data":[97,97,97,97,97]}

let buf3 = buffer.alloc(11, 'aGVsbG8gd29ybGQ=', 'base64');
console.info(JSON.stringify(buf3)); // {"type":"Buffer","data":[104,101,108,108,111,32,119,111,114,108,100]}
```
