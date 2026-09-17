# CipherRsaOptions

Defines the input parameters of **cipher.rsa()**.

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

## key

```TypeScript
key: string
```

RSA key. It is a public key in encryption and a private key in decryption.

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

The text to be encrypted must be a common text and cannot exceed the length calculated based on the formula (keySize/8 - 66). **keySize** indicates the key length. For example, if the key length is 1024 bytes, the text cannot exceed 62 bytes (1024/8 - 66 = 62). The text to be decrypted must be a binary value encoded in Base64. The default format is used for Base64 encoding.

**Type:** string

**Since:** 3

**Deprecated since:** 11

**Substitutes:** Cipher

**System capability:** SystemCapability.Security.Cipher

## transformation

```TypeScript
transformation?: string
```

RSA padding. The default value is **RSA/None/OAEPWithSHA256AndMGF1Padding**.

**Type:** string

**Since:** 3

**Deprecated since:** 11

**Substitutes:** Cipher

**System capability:** SystemCapability.Security.Cipher
