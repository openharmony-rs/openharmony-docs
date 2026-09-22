# GcmParamsSpec

```TypeScript
interface GcmParamsSpec extends ParamsSpec
```

Encapsulates the parameters for encryption or decryption using the GCM AEAD mode, which requires an IV, AAD, and an authentication tag. It is a child class of [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md) and used as a parameter in [init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init-3) for symmetric encryption or decryption.

<br>Applies to the GCM mode.

> **NOTE:** 
> 
> 1. Before passing a value to [init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init-3), specify
> **algName** for its parent class [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md).
> 2. If **aad** is not required or the **aad** length is 0, you can set its **data** attribute to an empty Uint8Array in the **aad: { data: new Uint8Array() }** format when constructing **GcmParamsSpec**.

**Inheritance/Implementation:** GcmParamsSpec extends [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md)

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

Additional authentication data (AAD), which is of 0 to INT_MAX bytes.

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

Authentication tag, which is of 16 bytes.

<br>When GCM mode is used for encryption, you need to extract the last 16 bytes from the [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md) returned by [doFinal()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#dofinal-1) or [doFinalSync()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#dofinalsync) and use them as **authTag** in **GcmParamsSpec** for [init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init-3) or [initSync()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#initsync).

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

IV, which is of 1 to 128 bytes. A 12-byte IV is commonly used.

**Type:** [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Cipher
- API versions 9 to 11: SystemCapability.Security.CryptoFramework
