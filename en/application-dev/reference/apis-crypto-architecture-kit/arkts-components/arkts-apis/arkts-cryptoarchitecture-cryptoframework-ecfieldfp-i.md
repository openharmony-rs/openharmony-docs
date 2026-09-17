# ECFieldFp

Defines the prime field of the elliptic curve. It is a child class of [ECField](arkts-cryptoarchitecture-cryptoframework-ecfield-i.md).

**Inheritance/Implementation:** ECFieldFp extends [ECField](arkts-cryptoarchitecture-cryptoframework-ecfield-i.md)

**Since:** 10

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

## Modules to Import

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## p

```TypeScript
p: bigint
```

Value of the prime number **p**.

**Type:** bigint

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API versions 10 to 11: SystemCapability.Security.CryptoFramework
