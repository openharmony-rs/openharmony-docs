# Cipher

Defines the cipher functions.

**Since:** 3

**Deprecated since:** 9

**Substitutes:** Cipher

**System capability:** SystemCapability.Security.Cipher

## Modules to Import

```TypeScript
import { Cipher, CipherAesOptions, CipherResponse, CipherRsaOptions } from '@kit.CryptoArchitectureKit';
```

## aes

```TypeScript
static aes(options: CipherAesOptions): void
```

Encrypts or decrypts data using AES.

**Since:** 3

**Deprecated since:** 9

**Substitutes:** Cipher

**System capability:** SystemCapability.Security.Cipher

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [CipherAesOptions](arkts-cryptoarchitecture-system-cipher-cipheraesoptions-i.md) | Yes | AES options. |

## rsa

```TypeScript
static rsa(options: CipherRsaOptions): void
```

Encrypts or decrypts data using RSA.

**Since:** 3

**Deprecated since:** 9

**Substitutes:** Cipher

**System capability:** SystemCapability.Security.Cipher

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [CipherRsaOptions](arkts-cryptoarchitecture-system-cipher-cipherrsaoptions-i.md) | Yes | RSA options. |
