# X963KdfSpec

```TypeScript
interface X963KdfSpec extends KdfSpec
```

Defines the child class of [KdfSpec](arkts-cryptoarchitecture-cryptoframework-kdfspec-i.md). It is a parameter for X963KDF key derivation function (KDF).

> **NOTE:** 
> 
> **key** is the original key material entered by the user.

**Inheritance/Implementation:** X963KdfSpec extends [KdfSpec](arkts-cryptoarchitecture-cryptoframework-kdfspec-i.md)

**Since:** 22

<!--Device-cryptoFramework-interface X963KdfSpec extends KdfSpec--><!--Device-cryptoFramework-interface X963KdfSpec extends KdfSpec-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Kdf

## Modules to Import

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## info

```TypeScript
info: Uint8Array
```

Shared information.

**Type:** Uint8Array

**Since:** 22

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-X963KdfSpec-info: Uint8Array--><!--Device-X963KdfSpec-info: Uint8Array-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Kdf

## key

```TypeScript
key: string | Uint8Array
```

Key material.

**Type:** string &#124; Uint8Array

**Since:** 22

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-X963KdfSpec-key: string | Uint8Array--><!--Device-X963KdfSpec-key: string | Uint8Array-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Kdf

## keySize

```TypeScript
keySize: number
```

Length of the derived key, in bytes. The value must be a positive integer.

**Type:** number

**Since:** 22

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-X963KdfSpec-keySize: int--><!--Device-X963KdfSpec-keySize: int-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Kdf
