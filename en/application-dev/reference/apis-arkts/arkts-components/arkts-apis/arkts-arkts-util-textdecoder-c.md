# TextDecoder

```TypeScript
class TextDecoder
```

Provides APIs to decode byte arrays into strings. It supports multiple formats, including UTF-8, UTF-16LE, UTF-16BE, ISO-8859, and Windows-1251.

**Since:** 7

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { util } from '@kit.ArkTS';
```

## constructor

```TypeScript
constructor()
```

A constructor used to create a **TextDecoder** object.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Examples**

```TypeScript
let textDecoder = new util.TextDecoder();
let retStr = textDecoder.encoding;
console.info('retStr = ' + retStr);
// Output: retStr = utf-8
```

<a id="constructor-1"></a>

## constructor

```TypeScript
constructor(encoding?: string, options?: { fatal?: boolean; ignoreBOM?: boolean })
```

A constructor used to create a **TextDecoder** object.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [create](#create)

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| encoding | string | No | Encoding format. The default format is **'utf-8'**. |
| options | { fatal?: boolean; ignoreBOM?: boolean } | No | Decoding-related options, which include **fatal** and **ignoreBOM**. |

**Examples**

```TypeScript
let textDecoder = new util.TextDecoder("utf-8",{ignoreBOM: true});
```

## create

```TypeScript
static create(encoding?: string, options?: TextDecoderOptions): TextDecoder
```

Creates a **TextDecoder** object. It provides the same function as the deprecated argument constructor.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| encoding | string | No | Encoding format. The default format is **'utf-8'**.<br>**Since:** 11 |
| options | [TextDecoderOptions](arkts-arkts-util-textdecoderoptions-i.md) | No | Decoding-related options, which include **fatal** and **ignoreBOM**.<br>**Since:** 11 |

**Return value:**

| Type | Description |
| --- | --- |
| [TextDecoder](arkts-arkts-util-textdecoder-c.md) | **TextDecoder** object created. |

**Examples**

```TypeScript
let textDecoderOptions: util.TextDecoderOptions = {
  fatal: false,
  ignoreBOM : true
}
let textDecoder = util.TextDecoder.create('utf-8', textDecoderOptions);
let retStr = textDecoder.encoding;
console.info('retStr = ' + retStr);
// Output: retStr = utf-8
```

## decode

```TypeScript
decode(input: Uint8Array, options?: { stream?: false }): string
```

Decodes the input content into a string.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [decodeToString](#decodetostring)

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| input | Uint8Array | Yes | Uint8Array object to decode. |
| options | { stream?: false } | No | Decoding-related options. |

**Return value:**

| Type | Description |
| --- | --- |
| string | String obtained. |

**Examples**

```TypeScript
let textDecoder = new util.TextDecoder("utf-8",{ignoreBOM: true});
let uint8 = new Uint8Array(6);
uint8[0] = 0xEF;
uint8[1] = 0xBB;
uint8[2] = 0xBF;
uint8[3] = 0x61;
uint8[4] = 0x62;
uint8[5] = 0x63;
console.info("input num:");
let retStr = textDecoder.decode(uint8, {stream: false});
console.info("retStr = " + retStr);
// Output: retStr = abc
```

## decodeToString

```TypeScript
decodeToString(input: Uint8Array, options?: DecodeToStringOptions): string
```

Decodes the input content into a string.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| input | Uint8Array | Yes | Uint8Array object to decode. |
| options | [DecodeToStringOptions](arkts-arkts-util-decodetostringoptions-i.md) | No | Decoding-related options. The default value is **undefined**. |

**Return value:**

| Type | Description |
| --- | --- |
| string | String obtained. |

**Examples**

```TypeScript
let textDecoderOptions: util.TextDecoderOptions = {
  fatal: false,
  ignoreBOM : true
}
let decodeToStringOptions: util.DecodeToStringOptions = {
  stream: false
}
let textDecoder = util.TextDecoder.create('utf-8', textDecoderOptions);
let uint8 = new Uint8Array([0xEF, 0xBB, 0xBF, 0x61, 0x62, 0x63]);
let retStr = textDecoder.decodeToString(uint8, decodeToStringOptions);
console.info("retStr = " + retStr);
// Output: retStr = abc
```

## decodeWithStream

```TypeScript
decodeWithStream(input: Uint8Array, options?: DecodeWithStreamOptions): string
```

Decodes the input content into a string. If **input** is an empty array, **undefined** is returned.

**Since:** 9

**Deprecated since:** 12

**Substitutes:** [decodeToString](#decodetostring)

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| input | Uint8Array | Yes | Uint8Array object to decode. |
| options | [DecodeWithStreamOptions](arkts-arkts-util-decodewithstreamoptions-i.md) | No | Decoding-related options.<br>**Since:** 11 |

**Return value:**

| Type | Description |
| --- | --- |
| string | String obtained. |

**Examples**

```TypeScript
let textDecoderOptions: util.TextDecoderOptions = {
  fatal: false,
  ignoreBOM : true
}
let decodeWithStreamOptions: util.DecodeWithStreamOptions = {
  stream: false
}
let textDecoder = util.TextDecoder.create('utf-8', textDecoderOptions);
let uint8 = new Uint8Array(6);
uint8[0] = 0xEF;
uint8[1] = 0xBB;
uint8[2] = 0xBF;
uint8[3] = 0x61;
uint8[4] = 0x62;
uint8[5] = 0x63;
console.info("input num:");
let retStr = textDecoder.decodeWithStream(uint8, decodeWithStreamOptions);
console.info("retStr = " + retStr);
// Output: retStr = abc
```

## encoding

```TypeScript
readonly encoding: string
```

Encoding format.<br>The following formats are supported: utf-8, ibm866, iso-8859-2, iso-8859-3, iso-8859-4, iso-8859-5, iso-8859-6, iso-8859-7, iso-8859-8, iso-8859-8-i, iso-8859-10, iso-8859-13, iso-8859-14, iso-8859-15, koi8 -r, koi8-u, macintosh, windows-874, windows-1250, windows-1251, windows-1252, windows-1253, windows-1254, windows -1255, windows-1256, windows-1257, windows-1258, x-mac-cyrillic, gbk, gb18030, big5, euc-jp, iso-2022-jp, shift_jis, euc-kr, utf-16be, utf-16le, gb2312, and iso-8859-1.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## fatal

```TypeScript
readonly fatal: boolean
```

Whether to display fatal errors. The value **true** means to display fatal errors, and **false** means the opposite.

**Type:** boolean

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## ignoreBOM

```TypeScript
readonly ignoreBOM = false
```

Whether to ignore the byte order marker (BOM). The default value is **false**, which indicates that the result contains the BOM.

**Type:** false

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang
