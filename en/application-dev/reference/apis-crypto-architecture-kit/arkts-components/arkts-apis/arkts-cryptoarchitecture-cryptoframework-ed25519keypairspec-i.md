# ED25519KeyPairSpec

```TypeScript
interface ED25519KeyPairSpec extends AsyKeySpec
```

Defines a child class of [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md) used to specify full parameters of the public and private keys in the Ed25519 algorithm.

<br>To generate a key based on key parameters, pass it to [createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md) to create a key generator.

**Inheritance/Implementation:** ED25519KeyPairSpec extends [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)

**Since:** 11

<!--Device-cryptoFramework-interface ED25519KeyPairSpec extends AsyKeySpec--><!--Device-cryptoFramework-interface ED25519KeyPairSpec extends AsyKeySpec-End-->

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API version 11: SystemCapability.Security.CryptoFramework

## Modules to Import

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## pk

```TypeScript
pk: bigint
```

Public key **pk** in the Ed25519 algorithm.

**Type:** bigint

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ED25519KeyPairSpec-pk: bigint--><!--Device-ED25519KeyPairSpec-pk: bigint-End-->

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API version 11: SystemCapability.Security.CryptoFramework

## sk

```TypeScript
sk: bigint
```

Private key **sk** in the Ed25519 algorithm.

**Type:** bigint

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ED25519KeyPairSpec-sk: bigint--><!--Device-ED25519KeyPairSpec-sk: bigint-End-->

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API version 11: SystemCapability.Security.CryptoFramework
