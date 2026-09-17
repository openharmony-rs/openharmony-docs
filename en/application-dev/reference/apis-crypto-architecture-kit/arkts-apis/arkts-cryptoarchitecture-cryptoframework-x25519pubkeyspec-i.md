# X25519PubKeySpec

Defines a child class of [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md) used to specify the parameters of the public key in the X25519 algorithm.

<br>To generate a key based on key parameters, pass it to [createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md) to create a key generator.

**Inheritance/Implementation:** X25519PubKeySpec extends [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)

**Since:** 11

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

Public key **pk** in the X25519 algorithm.

**Type:** bigint

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API version 11: SystemCapability.Security.CryptoFramework
