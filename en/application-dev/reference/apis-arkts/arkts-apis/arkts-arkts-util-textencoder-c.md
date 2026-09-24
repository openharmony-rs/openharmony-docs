# TextEncoder

```TypeScript
class TextEncoder
```

Provides APIs to encode strings into byte arrays. Multiple encoding formats are supported. When **TextEncoder** is used for encoding, the number of bytes occupied by a character varies according to the encoding format. You must explicitly specify the encoding format to obtain the required encoding result.

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

A constructor used to create a **TextEncoder** object.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Examples**

```TypeScript
let textEncoder = new util.TextEncoder();
```

<a id="constructor-1"></a>

## constructor

```TypeScript
constructor(encoding?: string)
```

A constructor used to create a **TextEncoder** object.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| encoding | string | No | Encoding format. The default format is **'utf-8'**. |

**Examples**

```TypeScript
let textEncoder = new util.TextEncoder("utf-8");
```

## create

```TypeScript
static create(encoding?: string): TextEncoder
```

Creates a **TextEncoder** object.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| encoding | string | No | Encoding format. The default format is **'utf-8'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [TextEncoder](arkts-arkts-util-textencoder-c.md) | **TextEncoder** object. |

**Examples**

```TypeScript
let textEncoder = util.TextEncoder.create("utf-8");
```

## encode

```TypeScript
encode(input?: string): Uint8Array
```

Encodes the input content in to a Uint8Array object.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [encodeInto](#encodeinto)

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| input | string | No | String to encode. The default value is an empty string. |

**Return value:**

| Type | Description |
| --- | --- |
| Uint8Array | Uint8Array object obtained. |

**Examples**

```TypeScript
let textEncoder = new util.TextEncoder();
let result = textEncoder.encode("\uD800¥¥");
console.info("result = " + result);
// Output: result = 237,160,128,194,165,194,165
```

## encodeInto

```TypeScript
encodeInto(input?: string): Uint8Array
```

Encodes the input content into a Uint8Array object.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| input | string | No | String to encode. The default value is an empty string. If the input parameter is an empty string, the return value is undefined. |

**Return value:**

| Type | Description |
| --- | --- |
| Uint8Array | Uint8Array object obtained. |

**Examples**

```TypeScript
let textEncoder = new util.TextEncoder();
let result = textEncoder.encodeInto("\uD800¥¥");
console.info("result = " + result);
// Output: result = 237,160,128,194,165,194,165
```

<a id="encodeinto-1"></a>

## encodeInto

```TypeScript
encodeInto(input: string, dest: Uint8Array): { read: number; written: number }
```

Writes the generated UTF-8 encoded text to an array.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [encodeIntoUint8Array](#encodeintouint8array)

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| input | string | Yes | String to encode. |
| dest | Uint8Array | Yes | Uint8Array object used to store the UTF-8 encoded text. |

**Return value:**

| Type | Description |
| --- | --- |
| object | Object obtained. **read** indicates the number of encoded characters, and **written** indicates the number of bytes in the encoded characters. |

**Examples**

```TypeScript
let textEncoder = new util.TextEncoder();
let buffer = new ArrayBuffer(4);
let uint8 = new Uint8Array(buffer);
let result = textEncoder.encodeInto('abcd', uint8);
console.info("uint8 = " + uint8);
// Output: uint8 = 97,98,99,100
```

## encodeIntoUint8Array

```TypeScript
encodeIntoUint8Array(input: string, dest: Uint8Array): EncodeIntoUint8ArrayInfo
```

Encodes the input content and stores the result into a Uint8Array object.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| input | string | Yes | String to encode. |
| dest | Uint8Array | Yes | Uint8Array object used to store the UTF-8 encoded text. |

**Return value:**

| Type | Description |
| --- | --- |
| object | Return the object, where read represents the number of characters that have been encoded, and written represents the number of bytes occupied by the encoded characters.<br>**Since:** 9 - 10 |
| [EncodeIntoUint8ArrayInfo](arkts-arkts-util-encodeintouint8arrayinfo-i.md) | Object obtained. **read** indicates the number of encoded characters, and **written** indicates the number of bytes in the encoded characters.<br>**Since:** 11 |

**Examples**

```TypeScript
let textEncoder = new util.TextEncoder();
let buffer = new ArrayBuffer(4);
let uint8 = new Uint8Array(buffer);
let result = textEncoder.encodeIntoUint8Array('abcd', uint8);
console.info("uint8 = " + uint8);
// Output: uint8 = 97,98,99,100
console.info("result.read = " + result.read);
// Output: result.read = 4
console.info("result.written = " + result.written);
// Output: result.written = 4
```

## encoding

```TypeScript
readonly encoding = 'utf-8'
```

Encoding format.<br>The following formats are supported: utf-8, gb2312, gb18030, ibm866, iso-8859-1, iso-8859-2, iso-8859-3, iso-8859-4, iso-8859-5, iso-8859-6, iso-8859-7, iso-8859-8, iso-8859-8-i, iso-8859-10, iso-8859-13, iso-8859-14, iso-8859-15, koi8-r, koi8-u, macintosh, windows-874, windows-1250, windows-1251, windows-1252, windows-1253, windows-1254, windows-1255, windows-1256, windows-1257, windows-1258, gbk, big5, euc-jp, iso-2022- jp, shift_jis, euc-kr, x-mac-cyrillic, utf-16be, and utf-16le.<br>The default value is **'utf-8'**.

**Type:** 'utf-8'

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang
