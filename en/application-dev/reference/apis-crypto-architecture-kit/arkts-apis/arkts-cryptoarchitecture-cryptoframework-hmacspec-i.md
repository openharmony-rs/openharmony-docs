# HmacSpec

```TypeScript
interface HmacSpec extends MacSpec
```

Represents the child class of [MacSpec](arkts-cryptoarchitecture-cryptoframework-macspec-i.md). It is used as an input parameter for HMAC computation.

> **NOTE:** 
> 
> **mdName** specifies the HMAC message digest algorithm. It is mandatory.

**Inheritance/Implementation:** HmacSpec extends [MacSpec](arkts-cryptoarchitecture-cryptoframework-macspec-i.md)

**Since:** 18

**System capability:** SystemCapability.Security.CryptoFramework.Mac

## Modules to Import

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## mdName

```TypeScript
mdName: string
```

Message digest algorithm.

**Type:** string

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Security.CryptoFramework.Mac
