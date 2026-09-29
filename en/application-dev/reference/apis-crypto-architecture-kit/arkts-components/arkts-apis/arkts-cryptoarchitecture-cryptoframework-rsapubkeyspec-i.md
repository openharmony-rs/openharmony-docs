# RSAPubKeySpec

```TypeScript
interface RSAPubKeySpec extends AsyKeySpec
```

Defines a child class of [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md) used to specify the parameters of the public key in the RSA algorithm.

<br>To generate a key based on key parameters, pass it to [createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md) to create a key generator.

**Inheritance/Implementation:** RSAPubKeySpec extends [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)

**Since:** 10

<!--Device-cryptoFramework-interface RSAPubKeySpec extends AsyKeySpec--><!--Device-cryptoFramework-interface RSAPubKeySpec extends AsyKeySpec-End-->

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## Modules to Import

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## params

```TypeScript
params: RSACommonParamsSpec
```

Common parameters of the public and private keys in the RSA algorithm.

**Type:** [RSACommonParamsSpec](arkts-cryptoarchitecture-cryptoframework-rsacommonparamsspec-i.md)

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-RSAPubKeySpec-params: RSACommonParamsSpec--><!--Device-RSAPubKeySpec-params: RSACommonParamsSpec-End-->

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## pk

```TypeScript
pk: bigint
```

Public key **pk** in the RSA algorithm.

**Type:** bigint

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-RSAPubKeySpec-pk: bigint--><!--Device-RSAPubKeySpec-pk: bigint-End-->

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework
