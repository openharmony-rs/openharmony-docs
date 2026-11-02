# KemEncapResult

```TypeScript
interface KemEncapResult
```

Indicates the key encapsulation result.

**Since:** 26.0.0

<!--Device-cryptoFramework-interface KemEncapResult--><!--Device-cryptoFramework-interface KemEncapResult-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Cipher

## Modules to Import

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## sharedSecret

```TypeScript
sharedSecret: Uint8Array
```

Shared key generated during key encapsulation.

**Type:** Uint8Array

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-KemEncapResult-sharedSecret: Uint8Array--><!--Device-KemEncapResult-sharedSecret: Uint8Array-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Cipher

## wrappedKey

```TypeScript
wrappedKey: Uint8Array
```

Wrapped key generated during key encapsulation.

**Type:** Uint8Array

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-KemEncapResult-wrappedKey: Uint8Array--><!--Device-KemEncapResult-wrappedKey: Uint8Array-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Cipher
