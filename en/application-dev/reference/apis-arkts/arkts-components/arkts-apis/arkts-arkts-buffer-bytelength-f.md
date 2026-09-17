# byteLength

## Modules to Import

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

Obtains the number of bytes of a string based on the encoding format.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| string | string &#124; Buffer &#124; TypedArray &#124; DataView &#124; ArrayBuffer &#124; SharedArrayBuffer | Yes | Target string. |
| encoding | BufferEncoding | No | Encoding format. The default value is **'utf8'**. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of bytes of the string. |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let str = '\u00bd + \u00bc = \u00be';
console.info(`${str}: ${str.length} characters, ${buffer.byteLength(str, 'utf-8')} bytes`);
// Output: ½ + ¼ = ¾: 9 characters, 12 bytes
```
