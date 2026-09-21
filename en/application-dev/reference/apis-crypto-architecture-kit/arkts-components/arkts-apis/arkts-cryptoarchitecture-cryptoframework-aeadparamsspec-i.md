# AeadParamsSpec

```TypeScript
interface AeadParamsSpec extends ParamsSpec
```

Describes parameters in [init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init-3) for symmetric encryption and decryption using authenticated encryption with associated data (AEAD). It inherits from [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md).

<br>It is applicable to the CCM and GCM modes of [AES](../../../security/CryptoArchitectureKit/crypto-encryption-decryption.md#aes). <br>It is applicable to the GCM mode of [SM4](../../../security/CryptoArchitectureKit/crypto-encryption-decryption.md#sm4). <br>It is applicable to [ChaCha20-Poly1305](../../../security/CryptoArchitectureKit/crypto-encryption-decryption.md#chacha20).

> **NOTE:** 
> 
> When **AeadParamsSpec** is used for encryption in AES-CCM mode:
> - If the tag length is specified during encryption, the same length must be passed during decryption.
> 
> - In CCM mode, only one of [update](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#update) and [doFinal](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#dofinal) can be called for encryption or decryption, and each method can be called only once.

**Inheritance/Implementation:** AeadParamsSpec extends [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md)

**Since:** 26.0.0

**System capability:** SystemCapability.Security.CryptoFramework.Cipher

## Modules to Import

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## authenticatedData

```TypeScript
authenticatedData?: Uint8Array
```

Optional additional authenticated data.

**Type:** Uint8Array

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.CryptoFramework.Cipher

## nonce

```TypeScript
nonce: Uint8Array
```

Number used once.

> **NOTE:** 
> - For AES-CCM, the nonce length ranges from 7 to 13 bytes.
> - For AES-GCM, the nonce length ranges from 1 to 128 bytes, 12 bytes are recommended.
> - For SM4-GCM, the nonce length ranges from 1 to 128 bytes, 12 bytes are recommended.
> - For ChaCha20-Poly1305, the nonce length must be 12 bytes.

**Type:** Uint8Array

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.CryptoFramework.Cipher

## tagLen

```TypeScript
tagLen?: number
```

Authentication tag length, in bytes.

<br>For encryption, the tag will be added to the end of the ciphertext. <br>For decryption, the tag should be at the end of the ciphertext. <br>The value should be an integer.

> **NOTE:** 
> - For AES-CCM, the default value is 12. The supported values are 4, 6, 8, 10, 12, 14, and 16.
> - For AES-GCM, the default value is 16. The supported values are 4, 8, 12, 13, 14, 15, and 16.
> - For SM4-GCM, the default value is 16. The supported values are 4, 8, 12, 13, 14, 15, and 16.
> - For ChaCha20-Poly1305, the default value is 16. The supported value is 16.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.CryptoFramework.Cipher
