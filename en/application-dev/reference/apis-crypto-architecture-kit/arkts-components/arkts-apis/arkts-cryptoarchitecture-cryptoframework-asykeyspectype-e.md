# AsyKeySpecType

Enumerates the key parameter types.

**Since:** 10

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## COMMON_PARAMS_SPEC

```TypeScript
COMMON_PARAMS_SPEC = 0
```

Common parameters of the public and private keys. You can use [generateKeyPair](arkts-cryptoarchitecture-cryptoframework-asykeygeneratorbyspec-i.md#generatekeypair) to randomly generate a key pair based on the parameters of this type.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## PRIVATE_KEY_SPEC

```TypeScript
PRIVATE_KEY_SPEC = 1
```

Parameter of the private key. You can use [generatePriKey](arkts-cryptoarchitecture-cryptoframework-asykeygeneratorbyspec-i.md#generateprikey) to generate a private key based on the parameters of this type.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## PUBLIC_KEY_SPEC

```TypeScript
PUBLIC_KEY_SPEC = 2
```

Parameter of the public key. You can use [generatePubKey](arkts-cryptoarchitecture-cryptoframework-asykeygeneratorbyspec-i.md#generatepubkey) to generate a public key based on the parameters of this type.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## KEY_PAIR_SPEC

```TypeScript
KEY_PAIR_SPEC = 3
```

Full parameters of the public and private keys. You can use [generateKeyPair](arkts-cryptoarchitecture-cryptoframework-asykeygeneratorbyspec-i.md#generatekeypair) to generate a key pair based on the parameters of this type.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework
