# byteLength

## Modules to Import

```TypeScript
import { fastbuffer } from '@kit.ArkTS';
```

## byteLength

```TypeScript
function byteLength(value: string | FastBuffer | TypedArray | DataView | ArrayBuffer | SharedArrayBuffer, encoding?: BufferEncoding): number
```

Returns the byte length of a string when encoded using `encoding`. This is not the same as [`String.prototype.length`], which does not account for the encoding that is used to convert the string into bytes.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string &#124; [FastBuffer](arkts-arkts-fastbuffer-fastbuffer-c.md) &#124; TypedArray &#124; DataView &#124; ArrayBuffer &#124; SharedArrayBuffer | Yes | Target string. |
| encoding | BufferEncoding | No | Encoding format of the string. The default value is 'utf8'. |

**Return value:**

| Type | Description |
| --- | --- |
| number | The number of bytes contained within `string` |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let str = 'hello world';
console.info(`${str}: ${str.length} characters, ${fastbuffer.byteLength(str, 'utf-8')} bytes`);
// Output: hello world: 11 characters, 11 bytes

str = '\u00bd + \u00bc = \u00be';
console.info(`${str}: ${str.length} characters, ${fastbuffer.byteLength(str, 'utf-8')} bytes`);
// Output: ½ + ¼ = ¾: 9 characters, 12 bytes
```
