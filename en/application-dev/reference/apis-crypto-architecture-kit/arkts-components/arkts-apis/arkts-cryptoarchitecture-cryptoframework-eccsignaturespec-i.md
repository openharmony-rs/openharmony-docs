# EccSignatureSpec

```TypeScript
interface EccSignatureSpec
```

Represents the ECC/SM2 signature data that contains (r, s).

> **NOTE:** 
> 
> **r** and **s** are each 256 bits long.

**Since:** 20

<!--Device-cryptoFramework-interface EccSignatureSpec--><!--Device-cryptoFramework-interface EccSignatureSpec-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Signature

## Modules to Import

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## r

```TypeScript
r: bigint
```

Randomized value derived from the elliptic curve calculation using the ephemeral private key during signature generation.

**Type:** bigint

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-EccSignatureSpec-r: bigint--><!--Device-EccSignatureSpec-r: bigint-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Signature

## s

```TypeScript
s: bigint
```

Signature component, computed using the signer's private key, r, and the hashed message.

**Type:** bigint

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-EccSignatureSpec-s: bigint--><!--Device-EccSignatureSpec-s: bigint-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Signature
