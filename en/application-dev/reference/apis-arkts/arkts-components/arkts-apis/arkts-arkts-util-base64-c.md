# Base64

Decodes a string or Uint8Array containing Base64 data into a newly allocated Uint8Array.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [Base64Helper](arkts-arkts-util-base64helper-c.md)

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { util } from '@kit.ArkTS';
```

## constructor

```TypeScript
constructor()
```

A constructor used to create a **Base64** object.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [constructor](arkts-arkts-util-base64helper-c.md#constructor)

**System capability:** SystemCapability.Utils.Lang

**Examples**

```TypeScript
let base64 = new  util.Base64();
```

## decode

```TypeScript
decode(src: Uint8Array | string): Promise<Uint8Array>
```

Decodes the input content into a Uint8Array object. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [decode](arkts-arkts-util-base64helper-c.md#decode)

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | Uint8Array &#124; string | Yes | Uint8Array object or string to decode. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise used to return the Uint8Array object obtained. |

**Examples**

```TypeScript
let base64 = new util.Base64();
let array = new Uint8Array([99,122,69,122]);
base64.decode(array).then((val) => {
  console.info(val.toString());
  // Output: 115,49,51
})
```

## decodeSync

```TypeScript
decodeSync(src: Uint8Array | string): Uint8Array
```

Decodes the input content into a Uint8Array object.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [decodeSync](arkts-arkts-util-base64helper-c.md#decodesync)

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | Uint8Array &#124; string | Yes | Uint8Array object or string to decode. |

**Return value:**

| Type | Description |
| --- | --- |
| Uint8Array | Uint8Array object obtained. |

**Examples**

```TypeScript
let base64 = new util.Base64();
let buff = 'czEz';
let result = base64.decodeSync(buff);
console.info("result = " + result);
// Output: result = 115,49,51
```

## encode

```TypeScript
encode(src: Uint8Array): Promise<Uint8Array>
```

Encodes the input content into a Uint8Array object. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [encode](arkts-arkts-util-base64helper-c.md#encode)

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | Uint8Array | Yes | Uint8Array object to encode. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise used to return the Uint8Array object obtained. |

**Examples**

```TypeScript
let base64 = new util.Base64();
let array = new Uint8Array([115,49,51]);
base64.encode(array).then((val) => {
  console.info(val.toString());
  // Output: 99,122,69,122
})
```

## encodeSync

```TypeScript
encodeSync(src: Uint8Array): Uint8Array
```

Performs Base64 encoding on the input Uint8Array byte array and returns the encoded Uint8Array.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [encodeSync](arkts-arkts-util-base64helper-c.md#encodesync)

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | Uint8Array | Yes | Uint8Array object to encode. |

**Return value:**

| Type | Description |
| --- | --- |
| Uint8Array | Uint8Array object obtained. |

**Examples**

```TypeScript
let base64 = new util.Base64();
let array = new Uint8Array([115,49,51]);
let result = base64.encodeSync(array);
console.info("result = " + result);
// Output: result = 99,122,69,122
```

## encodeToString

```TypeScript
encodeToString(src: Uint8Array): Promise<string>
```

Encodes the input content into a string. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [encodeToString](arkts-arkts-util-base64helper-c.md#encodetostring)

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | Uint8Array | Yes | Uint8Array object to encode. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the string obtained. |

**Examples**

```TypeScript
let base64 = new util.Base64();
let array = new Uint8Array([115,49,51]);
base64.encodeToString(array).then((val) => {
    console.info(val);
    // Output: czEz
})
```

## encodeToStringSync

```TypeScript
encodeToStringSync(src: Uint8Array): string
```

Performs Base64 encoding on the input Uint8Array byte array and returns the encoded string.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [encodeToStringSync](arkts-arkts-util-base64helper-c.md#encodetostringsync)

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | Uint8Array | Yes | Uint8Array object to encode. |

**Return value:**

| Type | Description |
| --- | --- |
| string | String obtained. |

**Examples**

```TypeScript
let base64 = new util.Base64();
let array = new Uint8Array([115,49,51]);
let result = base64.encodeToStringSync(array);
console.info("result = " + result);
// Output: result = czEz
```
