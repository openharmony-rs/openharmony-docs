# Poly1305ParamsSpec

```TypeScript
interface Poly1305ParamsSpec extends ParamsSpec
```

Encapsulates the parameters for encryption or decryption using the ChaCha20-Poly1305 AEAD mode, which requires a nonce, AAD, and an authentication tag. It is a child class of [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md) and used as a parameter in [init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init-3) for symmetric encryption or decryption.

<br>Applicable to [ChaCha20-Poly1305](../../../security/CryptoArchitectureKit/crypto-encryption-decryption.md#chacha20).

> **NOTE:** 
> 
> Before passing a value to
> [init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init-3), specify
> **algName** for its parent class [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md).
> 
> When the Poly1305 mode is used for encryption, you need to extract the last 16 bytes from the
> [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md) returned by
> [doFinal()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#dofinal-1) or
> [doFinalSync()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#dofinalsync) and use them as **authTag** in
> [Poly1305ParamsSpec](arkts-cryptoarchitecture-cryptoframework-poly1305paramsspec-i.md) for
> [init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init-3) or
> [initSync()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#initsync) during decryption.

**Inheritance/Implementation:** Poly1305ParamsSpec extends [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md)

**Since:** 22

**System capability:** SystemCapability.Security.CryptoFramework.Cipher

## Modules to Import

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## aad

```TypeScript
aad: DataBlob
```

Additional authenticated data.

**Type:** [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md)

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Security.CryptoFramework.Cipher

## authTag

```TypeScript
authTag: DataBlob
```

Authentication tag, which is of 16 bytes.

**Type:** [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md)

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Security.CryptoFramework.Cipher

## iv

```TypeScript
iv: DataBlob
```

Nonce (passed as the **iv** field), which is of 12 bytes.

**Type:** [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md)

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Security.CryptoFramework.Cipher
