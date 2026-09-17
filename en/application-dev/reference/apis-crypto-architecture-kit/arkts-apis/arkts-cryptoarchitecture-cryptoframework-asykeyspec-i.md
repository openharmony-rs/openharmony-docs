# AsyKeySpec

Defines the asymmetric key parameters for creating a key generator. You need to construct a child class object and pass it to [createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md) to create a key generator. When constructing a child class object, use little-endian format for RSA keys and use big-endian format and positive numbers for other key parameters of the bigint type.

**Since:** 10

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## Modules to Import

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## algName

```TypeScript
algName: string
```

Asymmetric key algorithm, for example, **RSA**, **DSA**, **ECC**, **SM2**, **Ed25519**, **X25519**, or **DH**.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## specType

```TypeScript
specType: AsyKeySpecType
```

Key parameter type, which is used to distinguish public and private key parameters.

**Type:** [AsyKeySpecType](arkts-cryptoarchitecture-cryptoframework-asykeyspectype-e.md)

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework
