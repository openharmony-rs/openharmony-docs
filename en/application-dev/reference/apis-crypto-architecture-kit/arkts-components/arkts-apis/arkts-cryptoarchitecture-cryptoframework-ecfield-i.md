# ECField

```TypeScript
interface ECField
```

Defines the field type of an elliptic curve. Currently, only the **Fp** field is supported.

**Since:** 10

<!--Device-cryptoFramework-interface ECField--><!--Device-cryptoFramework-interface ECField-End-->

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## Modules to Import

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## fieldType

```TypeScript
fieldType: string
```

Type of the elliptic curve field. Currently, only **Fp** is supported.

**Type:** string

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ECField-fieldType: string--><!--Device-ECField-fieldType: string-End-->

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework
