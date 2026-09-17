# KemEncapResult

Represents the encapsulation result of the KEM.

**Since:** 26.0.0

**System capability:** SystemCapability.Security.CryptoFramework.Cipher

## Modules to Import

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## sharedSecret

```TypeScript
sharedSecret: Uint8Array
```

Indicates the shared secret key of the KEM.

**Type:** Uint8Array

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.CryptoFramework.Cipher

## wrappedKey

```TypeScript
wrappedKey: Uint8Array
```

Indicates the wrapped key of the KEM, which is the ciphertext of the KEM.

**Type:** Uint8Array

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.CryptoFramework.Cipher
