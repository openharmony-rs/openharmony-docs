# StringDecoder

Provides the capability of decoding binary streams into strings. The following encoding types are supported: utf-8, iso-8859-2, koi8-r, macintosh, windows-1250, windows-1251, gbk, gb18030, big5, utf-16be, and UTF-16le.

**Since:** 12

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { util } from '@kit.ArkTS';
```

## constructor

```TypeScript
constructor(encoding?: string)
```

Constructor used to create a **StringDecoder** instance.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| encoding | string | No | Encoding type of the input data. The default value is **utf-8**. |

**Examples**

```TypeScript
let decoder = new util.StringDecoder();
```

## end

```TypeScript
end(chunk?: string | Uint8Array): string
```

Ends the decoding process and returns any remaining input stored in the internal buffer as a string.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| chunk | string &#124; Uint8Array | No | String to decode. The default value is **undefined**. |

**Return value:**

| Type | Description |
| --- | --- |
| string | String decoded. |

**Examples**

```TypeScript
let decoder = new util.StringDecoder('utf-8');
let input = new Uint8Array([0xE4, 0xBD, 0xA0, 0xE5, 0xA5, 0xBD]);
const writeString = decoder.write(input.slice(0, 5));
const endString = decoder.end(input.slice(5));
console.info("writeString:", writeString);
// Output: writeString: Hello
console.info("endString:", endString);
// Output: endString: World
```

## write

```TypeScript
write(chunk: string | Uint8Array): string
```

Decodes a string. Any incomplete multi-byte characters at the end of Uint8Array are filtered out from the returned string and stored in an internal buffer for the next call.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| chunk | string &#124; Uint8Array | Yes | String to decode. Decoding is performed based on the input encoding type. If the input is of the Uint8Array type, decoding is performed normally. If the input is of the string type, the parameter is directly returned. |

**Return value:**

| Type | Description |
| --- | --- |
| string | String decoded. |

**Examples**

```TypeScript
let decoder = new util.StringDecoder('utf-8');
let input =  new Uint8Array([0xE4, 0xBD, 0xA0, 0xE5, 0xA5, 0xBD]);
const decoded = decoder.write(input);
console.info("decoded:", decoded);
// Output: decoded: Hello, World
```
