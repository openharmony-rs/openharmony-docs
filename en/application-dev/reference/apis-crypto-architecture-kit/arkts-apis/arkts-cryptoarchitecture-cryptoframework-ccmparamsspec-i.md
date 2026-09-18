# CcmParamsSpec

Encapsulates the parameters for encryption or decryption using the CCM AEAD mode, which requires an IV, AAD, and an authentication tag. It is a child class of [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md) and used as a parameter in [init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init) for symmetric encryption or decryption.

<br>Applies to the CCM mode.

> **NOTE:** 
> 
> Before passing a value to
> [init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init), specify
> **algName** for its parent class [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md).

**Inheritance/Implementation:** CcmParamsSpec extends [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md)

**Since:** 9

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Cipher
- API versions 9 to 11: SystemCapability.Security.CryptoFramework

## Modules to Import

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## aad

```TypeScript
aad: DataBlob
```

AAD for encryption and decryption. The AAD value contains 1 to 2,048 bytes.

**Type:** [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Cipher
- API versions 9 to 11: SystemCapability.Security.CryptoFramework

## authTag

```TypeScript
authTag: DataBlob
```

Authentication tag, which is of 12 bytes.

<br>When CCM mode is used for encryption, you need to extract the last 12 bytes from the [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md) returned by [doFinal()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#dofinal) or [doFinalSync()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#dofinalsync) and use them as **authTag** in **CcmParamsSpec** for [init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init) or [initSync()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#initsync) during decryption.

**Type:** [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Cipher
- API versions 9 to 11: SystemCapability.Security.CryptoFramework

## iv

```TypeScript
iv: DataBlob
```

IV for encryption and decryption. Only 7 bytes are supported. If the length of the input **iv** parameter exceeds 7 bytes, the excess part will be truncated.

**Type:** [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Cipher
- API versions 9 to 11: SystemCapability.Security.CryptoFramework
