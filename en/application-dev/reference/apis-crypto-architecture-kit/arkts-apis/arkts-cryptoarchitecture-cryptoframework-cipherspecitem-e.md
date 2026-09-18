# CipherSpecItem

Enumerates encryption and decryption parameters, which can be set by using [setCipherSpec](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#setcipherspec) and obtained by using [getCipherSpec](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#getcipherspec).

<br>Currently, only RSA and SM2 are supported. For details, see [Asymmetric Key Encryption and Decryption Algorithm Specifications](../../../security/CryptoArchitectureKit/crypto-encryption-decryption.md).

**Since:** 10

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Cipher
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## OAEP_MD_NAME_STR

```TypeScript
OAEP_MD_NAME_STR = 100
```

Message digest algorithm used with the PKCS1_OAEP padding mode in RSA.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Cipher
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## OAEP_MGF_NAME_STR

```TypeScript
OAEP_MGF_NAME_STR = 101
```

Mask generation algorithm used with the PKCS1_OAEP padding mode in RSA. Currently, only MGF1 is supported.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Cipher
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## OAEP_MGF1_MD_STR

```TypeScript
OAEP_MGF1_MD_STR = 102
```

Message digest algorithm for the MGF1 mask generation used with the PKCS1_OAEP padding mode in RSA.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Cipher
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## OAEP_MGF1_PSRC_UINT8ARR

```TypeScript
OAEP_MGF1_PSRC_UINT8ARR = 103
```

**pSource** byte stream used with the PKCS1_OAEP padding mode in RSA.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Cipher
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## SM2_MD_NAME_STR

```TypeScript
SM2_MD_NAME_STR = 104
```

Message digest algorithm used in SM2.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Cipher
- API version 11: SystemCapability.Security.CryptoFramework
