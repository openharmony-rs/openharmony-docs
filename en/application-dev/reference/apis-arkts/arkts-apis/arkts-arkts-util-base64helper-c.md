# Base64Helper

Provides encoding and decoding for Base64 and Base64URL. The Base64 encoding table contains 64 characters, which are the uppercase letters (A-Z), lowercase letters (a-z), digits (0-9), and the special characters plus sign (+) and slash (/). During encoding, the original data is divided into groups of three bytes, and each group contains a 6-bit number. Then, the corresponding characters in the Base64 encoding table are used to represent these numbers. If the last group contains only one or two bytes, the equal sign (=) is used for padding. The Base64URL encoding table contains 64 characters, which are the uppercase letters (A-Z), lowercase letters (a-z), digits (0-9), and the special characters plus sign (+) and slash (/). The Base64URL encoding result does not contain equal signs (=).

**Since:** 9

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { util } from '@kit.ArkTS';
```

## constructor

```TypeScript
constructor()
```

A constructor used to create a **Base64Helper** instance.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Examples**

```TypeScript
let base64 = new util.Base64Helper();
```

## decode

```TypeScript
decode(src: Uint8Array | string, options?: Type): Promise<Uint8Array>
```

Decodes the input content into a Uint8Array object. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | Uint8Array &#124; string | Yes | Uint8Array object or string to decode. |
| options | [Type](arkts-arkts-util-type-e.md) | No | Decoding format.<br>The following values are available:<br>- **util.Type.BASIC** (default): Base64 decoding.<br>- **util.Type.MIME**: Base64 decoding. The input parameter **src** contains carriage return characters and newline characters.<br>- **util.Type.BASIC_URL_SAFE**: Base64URL decoding.<br>   - **util.Type.MIME_URL_SAFE**: Base64 URL decoding. The input parameter **src** contains carriage return   characters and newline characters.<br>**Since:** 10 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise used to return the Uint8Array object obtained. |

**Examples**

```TypeScript
let base64Helper = new util.Base64Helper();
let array = 'TWFuaXNkaXN0aW5ndWlzaGVkbm90b25seWJ5aGlzcmVhc29uYnV0Ynl0aGlzc2luZ3VsYXJwYXNz\r\naW9uZnJvbW90aGVyYW5pbWFsc3doaWNoaXNhbHVzdG9mdGhlbWluZGV4Y2VlZHN0aGVzaG9ydHZl\r\naGVtZW5jZW9mYW55Y2FybmFscGxlYXN1cmU=\r\n';
base64Helper.decode(array, util.Type.MIME).then((val) => {
  console.info(val.toString());
  /*
  Output: 77,97,110,105,115,100,105,115,116,105,110,103,117,105,115,104,101,100,110,111,116,111,110,108,121,98,121,104,105,115,114,101,97,115,111,110,98,117,116,98,121,116,104,105,115,115,105,110,103,117,108,97,114,112,97,115,115,105,111,110,102,114,111,109,111,116,104,101,114,97,110,105,109,97,108,115,119,104,105,99,104,105,115,97,108,117,115,116,111,102,116,104,101,109,105,110,100,101,120,99,101,101,100,115,116,104,101,115,104,111,114,116,118,101,104,101,109,101,110,99,101,111,102,97,110,121,99,97,114,110,97,108,112,108,101,97,115,117,114,101
  */
})
```

## decodeSync

```TypeScript
decodeSync(src: Uint8Array | string, options?: Type): Uint8Array
```

Decodes a string into a Uint8Array object. This API returns the result synchronously.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | Uint8Array &#124; string | Yes | Uint8Array object or string to decode. |
| options | [Type](arkts-arkts-util-type-e.md) | No | Decoding format.<br>The following values are available:<br>- **util.Type.BASIC** (default): Base64 decoding.<br>- **util.Type.MIME**: Base64 decoding. The input parameter **src** contains carriage return characters and newline characters.<br>- **util.Type.BASIC_URL_SAFE**: Base64URL decoding.<br>   - **util.Type.MIME_URL_SAFE**: Base64 URL decoding. The input parameter **src** contains carriage return   characters and newline characters.<br>**Since:** 10 |

**Return value:**

| Type | Description |
| --- | --- |
| Uint8Array | Uint8Array object obtained. |

**Examples**

```TypeScript
let base64Helper = new util.Base64Helper();
let buff = 'TWFuaXNkaXN0aW5ndWlzaGVkbm90b25seWJ5aGlzcmVhc29uYnV0Ynl0aGlzc2luZ3VsYXJwYXNz\r\naW9uZnJvbW90aGVyYW5pbWFsc3doaWNoaXNhbHVzdG9mdGhlbWluZGV4Y2VlZHN0aGVzaG9ydHZl\r\naGVtZW5jZW9mYW55Y2FybmFscGxlYXN1cmU=\r\n';
let result = base64Helper.decodeSync(buff, util.Type.MIME);
console.info("result = " + result);
/*
Output: result = 77,97,110,105,115,100,105,115,116,105,110,103,117,105,115,104,101,100,110,111,116,111,110,108,121,98,121,104,105,115,114,101,97,115,111,110,98,117,116,98,121,116,104,105,115,115,105,110,103,117,108,97,114,112,97,115,115,105,111,110,102,114,111,109,111,116,104,101,114,97,110,105,109,97,108,115,119,104,105,99,104,105,115,97,108,117,115,116,111,102,116,104,101,109,105,110,100,101,120,99,101,101,100,115,116,104,101,115,104,111,114,116,118,101,104,101,109,101,110,99,101,111,102,97,110,121,99,97,114,110,97,108,112,108,101,97,115,117,114,101
*/
```

## encode

```TypeScript
encode(src: Uint8Array, options?: Type): Promise<Uint8Array>
```

Encodes the input content into a Uint8Array object. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | Uint8Array | Yes | Uint8Array object to encode. |
| options | [Type](arkts-arkts-util-type-e.md) | No | Encoding format.<br>The following values are available:<br>- **util.Type.BASIC** (default): Base64 encoding.<br>- **util.Type.BASIC_URL_SAFE**: Base64URL encoding.<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise used to return the Uint8Array object obtained. |

**Examples**

```TypeScript
let base64Helper = new util.Base64Helper();
let array = new Uint8Array([115,49,51]);
base64Helper.encode(array).then((val) => {
  console.info(val.toString());
  // Output: 99,122,69,122
})
```

## encodeSync

```TypeScript
encodeSync(src: Uint8Array, options?: Type): Uint8Array
```

Encodes the input content into a Uint8Array object.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | Uint8Array | Yes | Uint8Array object to encode. |
| options | [Type](arkts-arkts-util-type-e.md) | No | Encoding format.<br>The following values are available:<br>- **util.Type.BASIC** (default): Base64 encoding.<br>- **util.Type.BASIC_URL_SAFE**: Base64URL encoding.<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| Uint8Array | Uint8Array object obtained. |

**Examples**

```TypeScript
let base64Helper = new util.Base64Helper();
let array = new Uint8Array([115,49,51]);
let result = base64Helper.encodeSync(array);
console.info("result = " + result);
// Output: result = 99,122,69,122
```

## encodeToString

```TypeScript
encodeToString(src: Uint8Array, options?: Type): Promise<string>
```

Encodes the input content into a string. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | Uint8Array | Yes | Uint8Array object to encode. |
| options | [Type](arkts-arkts-util-type-e.md) | No | Encoding format.<br>The following values are available:<br>- **util.Type.BASIC** (default): Base64 encoding. The return value does not contain carriage return characters or newline characters.<br>- **util.Type.MIME**: Base64 encoding. Each line of the return value contains a maximum of 76 characters and ends with '\r\n'.<br>- **util.Type.BASIC_URL_SAFE**: Base64URL encoding. The return value does not contain carriage return characters or newline characters.<br>- **util.Type.MIME_URL_SAFE**: Base64URL encoding. Each line in the return value contains a maximum of 76 characters and ends with '\r\n'.<br>**Since:** 10 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the string obtained. |

**Examples**

```TypeScript
let base64Helper = new util.Base64Helper();
let array = new Uint8Array([77,97,110,105,115,100,105,115,116,105,110,103,117,105,115,104,101,100,110,111,116,111,110,108,121,98,121,104,105,115,114,101,97,115,111,110,98,117,116,98,121,116,104,105,115,115,105,110,103,117,108,97,114,112,97,115,115,105,111,110,102,114,111,109,111,116,104,101,114,97,110,105,109,97,108,115,119,104,105,99,104,105,115,97,108,117,115,116,111,102,116,104,101,109,105,110,100,101,120,99,101,101,100,115,116,104,101,115,104,111,114,116,118,101,104,101,109,101,110,99,101,111,102,97,110,121,99,97,114,110,97,108,112,108,101,97,115,117,114,101]);
base64Helper.encodeToString(array, util.Type.MIME).then((val) => {
  console.info(val);
  /*
  Output: TWFuaXNkaXN0aW5ndWlzaGVkbm90b25seWJ5aGlzcmVhc29uYnV0Ynl0aGlzc2luZ3VsYXJwYXNz
  aW9uZnJvbW90aGVyYW5pbWFsc3doaWNoaXNhbHVzdG9mdGhlbWluZGV4Y2VlZHN0aGVzaG9ydHZl
  aGVtZW5jZW9mYW55Y2FybmFscGxlYXN1cmU=
  */

})
```

## encodeToStringSync

```TypeScript
encodeToStringSync(src: Uint8Array, options?: Type): string
```

Performs Base64 encoding on the input Uint8Array byte array and returns a string. This method supports multiple encoding formats, including standard Base64 encoding, MIME-compliant Base64 encoding (with line breaks), and URL- safe Base64 encoding.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | Uint8Array | Yes | Uint8Array object to encode. |
| options | [Type](arkts-arkts-util-type-e.md) | No | Encoding format.<br>The following values are available:<br>- **util.Type.BASIC** (default): Base64 encoding. The return value does not contain carriage return characters or newline characters.<br>- **util.Type.MIME**: Base64 encoding. If the return value exceeds 76 characters, a line break is inserted every 76 characters, and each line ends with '\r\n'. If the return value is fewer than 76 characters, an exception is thrown.<br>- **util.Type.BASIC_URL_SAFE**: Base64URL encoding. The return value does not contain carriage return characters or newline characters.<br>- **util.Type.MIME_URL_SAFE**: Base64 URL encoding. Each line in the return value contains a maximum of 76 characters and ends with '\r\n'.<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| string | String obtained. |

**Examples**

```TypeScript
// MIME encoding
let base64Helper = new util.Base64Helper();
let array =
  new Uint8Array([77, 97, 110, 105, 115, 100, 105, 115, 116, 105, 110, 103, 117, 105, 115, 104, 101, 100, 110, 111, 116,
    111, 110, 108, 121, 98, 121, 104, 105, 115, 114, 101, 97, 115, 111, 110, 98, 117, 116, 98, 121, 116, 104, 105, 115,
    115, 105, 110, 103, 117, 108, 97, 114, 112, 97, 115, 115, 105, 111, 110, 102, 114, 111, 109, 111, 116, 104, 101,
    114, 97, 110, 105, 109, 97, 108, 115, 119, 104, 105, 99, 104, 105, 115, 97, 108, 117, 115, 116, 111, 102, 116, 104,
    101, 109, 105, 110, 100, 101, 120, 99, 101, 101, 100, 115, 116, 104, 101, 115, 104, 111, 114, 116, 118, 101, 104,
    101, 109, 101, 110, 99, 101, 111, 102, 97, 110, 121, 99, 97, 114, 110, 97, 108, 112, 108, 101, 97, 115, 117, 114,
    101]);
let result = base64Helper.encodeToStringSync(array, util.Type.MIME);
console.info("result = " + result);
/*
// Output: result = TWFuaXNkaXN0aW5ndWlzaGVkbm90b25seWJ5aGlzcmVhc29uYnV0Ynl0aGlzc2luZ3VsYXJwYXNz
aW9uZnJvbW90aGVyYW5pbWFsc3doaWNoaXNhbHVzdG9mdGhlbWluZGV4Y2VlZHN0aGVzaG9ydHZl
aGVtZW5jZW9mYW55Y2FybmFscGxlYXN1cmU=
*/

// BASIC encoding
let base64Helper = new util.Base64Helper();
let array =
  new Uint8Array([77, 97, 110, 105, 115, 100, 105, 115, 116, 105, 110, 103, 117, 105, 115, 104, 101, 100, 110, 111, 116,
    111, 110, 108, 121, 98, 121, 104, 105, 115, 114, 101, 97, 115, 111, 110, 98, 117, 116, 98, 121, 116, 104, 105, 115,
    115, 105, 110, 103, 117, 108, 97, 114, 112, 97, 115, 115, 105, 111, 110, 102, 114, 111, 109, 111, 116, 104, 101,
    114, 97, 110, 105, 109, 97, 108, 115, 119, 104, 105, 99, 104, 105, 115, 97, 108, 117, 115, 116, 111, 102, 116, 104,
    101, 109, 105, 110, 100, 101, 120, 99, 101, 101, 100, 115, 116, 104, 101, 115, 104, 111, 114, 116, 118, 101, 104,
    101, 109, 101, 110, 99, 101, 111, 102, 97, 110, 121, 99, 97, 114, 110, 97, 108, 112, 108, 101, 97, 115, 117, 114,
    101]);
let result = base64Helper.encodeToStringSync(array, util.Type.BASIC);
console.info("result = " + result);
/*
Output: result = TWFuaXNkaXN0aW5ndWlzaGVkbm90b25seWJ5aGlzcmVhc29uYnV0Ynl0aGlzc2luZ3VsYXJwYXNzaW9uZnJvbW90aGVyYW5pbWFsc3doaWNoaXNhbHVzdG9mdGhlbWluZGV4Y2VlZHN0aGVzaG9ydHZlaGVtZW5jZW9mYW55Y2FybmFscGxlYXN1cmU=
*/

// MIME_URL_SAFE encoding
let base64Helper = new util.Base64Helper();
let array =
  new Uint8Array([77, 97, 110, 105, 115, 100, 105, 115, 116, 105, 110, 103, 117, 105, 115, 104, 101, 100, 110, 111, 116,
    111, 110, 108, 121, 98, 121, 104, 105, 115, 114, 101, 97, 115, 111, 110, 98, 117, 116, 98, 121, 116, 104, 105, 115,
    115, 105, 110, 103, 117, 108, 97, 114, 112, 97, 115, 115, 105, 111, 110, 102, 114, 111, 109, 111, 116, 104, 101,
    114, 97, 110, 105, 109, 97, 108, 115, 119, 104, 105, 99, 104, 105, 115, 97, 108, 117, 115, 116, 111, 102, 116, 104,
    101, 109, 105, 110, 100, 101, 120, 99, 101, 101, 100, 115, 116, 104, 101, 115, 104, 111, 114, 116, 118, 101, 104,
    101, 109, 101, 110, 99, 101, 111, 102, 97, 110, 121, 99, 97, 114, 110, 97, 108, 112, 108, 101, 97, 115, 117, 114,
    101]);
let result = base64Helper.encodeToStringSync(array, util.Type.BASIC_URL_SAFE);
console.info("result = " + result);
/*
Output: result = TWFuaXNkaXN0aW5ndWlzaGVkbm90b25seWJ5aGlzcmVhc29uYnV0Ynl0aGlzc2luZ3VsYXJwYXNzaW9uZnJvbW90aGVyYW5pbWFsc3doaWNoaXNhbHVzdG9mdGhlbWluZGV4Y2VlZHN0aGVzaG9ydHZlaGVtZW5jZW9mYW55Y2FybmFscGxlYXN1cmU
*/
// MIME_URL_SAFE encoding
let base64Helper = new util.Base64Helper();
let array =
  new Uint8Array([77, 97, 110, 105, 115, 100, 105, 115, 116, 105, 110, 103, 117, 105, 115, 104, 101, 100, 110, 111, 116,
    111, 110, 108, 121, 98, 121, 104, 105, 115, 114, 101, 97, 115, 111, 110, 98, 117, 116, 98, 121, 116, 104, 105, 115,
    115, 105, 110, 103, 117, 108, 97, 114, 112, 97, 115, 115, 105, 111, 110, 102, 114, 111, 109, 111, 116, 104, 101,
    114, 97, 110, 105, 109, 97, 108, 115, 119, 104, 105, 99, 104, 105, 115, 97, 108, 117, 115, 116, 111, 102, 116, 104,
    101, 109, 105, 110, 100, 101, 120, 99, 101, 101, 100, 115, 116, 104, 101, 115, 104, 111, 114, 116, 118, 101, 104,
    101, 109, 101, 110, 99, 101, 111, 102, 97, 110, 121, 99, 97, 114, 110, 97, 108, 112, 108, 101, 97, 115, 117, 114,
    101]);
let result = base64Helper.encodeToStringSync(array, util.Type.MIME_URL_SAFE);
console.info("result = " + result);
/*
// Output: result = TWFuaXNkaXN0aW5ndWlzaGVkbm90b25seWJ5aGlzcmVhc29uYnV0Ynl0aGlzc2luZ3VsYXJwYXNz
aW9uZnJvbW90aGVyYW5pbWFsc3doaWNoaXNhbHVzdG9mdGhlbWluZGV4Y2VlZHN0aGVzaG9ydHZl
aGVtZW5jZW9mYW55Y2FybmFscGxlYXN1cmU
*/
```
