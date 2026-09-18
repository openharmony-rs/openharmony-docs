# CipherAesOptions

Defines the input parameters of **cipher.aes()**.

**Since:** 3

**Deprecated since:** 11

**Substitutes:** Cipher

**System capability:** SystemCapability.Security.Cipher

## Modules to Import

```TypeScript
import { Cipher, CipherAesOptions, CipherResponse, CipherRsaOptions } from '@kit.CryptoArchitectureKit';
```

## complete

```TypeScript
complete: () => void
```

Called when the execution is complete.

**Since:** 3

**Deprecated since:** 11

**Substitutes:** Cipher

**System capability:** SystemCapability.Security.Cipher

## fail

```TypeScript
fail: (data: string, code: number) => void
```

Called when data fails to be encrypted or decrypted.

**Since:** 3

**Deprecated since:** 11

**Substitutes:** Cipher

**System capability:** SystemCapability.Security.Cipher

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string | Yes |  |
| code | number | Yes |  |

## success

```TypeScript
success: (data: CipherResponse) => void
```

Called when data is encrypted or decrypted successfully.

**Since:** 3

**Deprecated since:** 11

**Substitutes:** Cipher

**System capability:** SystemCapability.Security.Cipher

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [CipherResponse](arkts-cryptoarchitecture-system-cipher-cipherresponse-i.md) | Yes |  |

## action

```TypeScript
action: string
```

Action to perform. The options are as follows:

1. **encrypt**: Encrypts data.
2. **decrypt**: Decrypts data.

**Type:** string

**Since:** 3

**Deprecated since:** 11

**Substitutes:** Cipher

**System capability:** SystemCapability.Security.Cipher

## iv

```TypeScript
iv?: string
```

Initialization vector (IV) for AES-based encryption and decryption. The value is a string encoded in Base64. The default value is the key value.

**Type:** string

**Since:** 3

**Deprecated since:** 11

**Substitutes:** Cipher

**System capability:** SystemCapability.Security.Cipher

## ivLen

```TypeScript
ivLen?: string
```

Length of the IV, in bytes. This field is reserved. The default value is **16**, which is the only value supported.

**Type:** string

**Since:** 3

**Deprecated since:** 11

**Substitutes:** Cipher

**System capability:** SystemCapability.Security.Cipher

## ivOffset

```TypeScript
ivOffset?: string
```

Offset of the IV for AES-based encryption and decryption. The default value is **0**, which is the only value supported.

**Type:** string

**Since:** 3

**Deprecated since:** 11

**Substitutes:** Cipher

**System capability:** SystemCapability.Security.Cipher

## key

```TypeScript
key: string
```

Key used for encryption or decryption. It is a Base64 encoded string.

**Type:** string

**Since:** 3

**Deprecated since:** 11

**Substitutes:** Cipher

**System capability:** SystemCapability.Security.Cipher

## text

```TypeScript
text: string
```

Text to be encrypted or decrypted.

The text to be encrypted must be common text. The text to be decrypted must be a binary value encoded in Base64. The default format is used for Base64 encoding.

**Type:** string

**Since:** 3

**Deprecated since:** 11

**Substitutes:** Cipher

**System capability:** SystemCapability.Security.Cipher

## transformation

```TypeScript
transformation?: string
```

Encryption mode and padding of the AES algorithm. The default value is **AES/CBC/PKCS5Padding**.

**Type:** string

**Since:** 3

**Deprecated since:** 11

**Substitutes:** Cipher

**System capability:** SystemCapability.Security.Cipher
