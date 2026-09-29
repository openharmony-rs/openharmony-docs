# KdfSpec

```TypeScript
interface KdfSpec
```

Defines the parameters of the key derivation function. When the key derivation function is used to derive a key, you need to construct and pass in a child class object of **KdfSpec**.

**Since:** 11

<!--Device-cryptoFramework-interface KdfSpec--><!--Device-cryptoFramework-interface KdfSpec-End-->

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Kdf
- API version 11: SystemCapability.Security.CryptoFramework

## Modules to Import

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## algName

```TypeScript
algName: string
```

Algorithm of the key derivation function, for example, **PBKDF2**.

**Type:** string

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-KdfSpec-algName: string--><!--Device-KdfSpec-algName: string-End-->

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Kdf
- API version 11: SystemCapability.Security.CryptoFramework
