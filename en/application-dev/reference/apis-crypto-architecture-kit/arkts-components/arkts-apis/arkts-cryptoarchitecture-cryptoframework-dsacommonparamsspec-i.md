# DSACommonParamsSpec

Defines a child class of [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md) used to specify the common parameters of the public and private keys in the DSA algorithm. It can be used to randomly generate a public or private key.

<br>To generate a key based on key parameters, pass it to [createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md) to create a key generator.

**Inheritance/Implementation:** DSACommonParamsSpec extends [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)

**Since:** 10

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## Modules to Import

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## g

```TypeScript
g: bigint
```

Parameter **g** in the DSA algorithm.

**Type:** bigint

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## p

```TypeScript
p: bigint
```

Prime modulus **p** in the DSA algorithm.

**Type:** bigint

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## q

```TypeScript
q: bigint
```

Parameter **q**, prime factor of (p - 1) in the DSA algorithm.

**Type:** bigint

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework
