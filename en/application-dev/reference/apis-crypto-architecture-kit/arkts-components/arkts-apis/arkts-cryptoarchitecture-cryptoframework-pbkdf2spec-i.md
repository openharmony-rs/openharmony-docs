# PBKDF2Spec

```TypeScript
interface PBKDF2Spec extends KdfSpec
```

Defines the child class of [KdfSpec](arkts-cryptoarchitecture-cryptoframework-kdfspec-i.md). It is used as a parameter for PBKDF2 key derivation.

> **NOTE:** 
> 
> **password** is the original password. If **password** of the string type is used, pass in the actual data for
> key derivation, rather than a HexString or Base64-encoded value. In addition, the string must be encoded in
> UTF-8, as other encodings may alter the derivation outcome.

**Inheritance/Implementation:** PBKDF2Spec extends [KdfSpec](arkts-cryptoarchitecture-cryptoframework-kdfspec-i.md)

**Since:** 11

<!--Device-cryptoFramework-interface PBKDF2Spec extends KdfSpec--><!--Device-cryptoFramework-interface PBKDF2Spec extends KdfSpec-End-->

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Kdf
- API version 11: SystemCapability.Security.CryptoFramework

## Modules to Import

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## iterations

```TypeScript
iterations: number
```

Number of iterations. The value must be a positive integer.

**Type:** number

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-PBKDF2Spec-iterations: int--><!--Device-PBKDF2Spec-iterations: int-End-->

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Kdf
- API version 11: SystemCapability.Security.CryptoFramework

## keySize

```TypeScript
keySize: number
```

Length of the derived key, in bytes.

**Type:** number

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-PBKDF2Spec-keySize: int--><!--Device-PBKDF2Spec-keySize: int-End-->

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Kdf
- API version 11: SystemCapability.Security.CryptoFramework

## password

```TypeScript
password: string | Uint8Array
```

Original password entered by the user.

**Type:** string &#124; Uint8Array

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-PBKDF2Spec-password: string | Uint8Array--><!--Device-PBKDF2Spec-password: string | Uint8Array-End-->

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Kdf
- API version 11: SystemCapability.Security.CryptoFramework

## salt

```TypeScript
salt: Uint8Array
```

Salt value.

**Type:** Uint8Array

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-PBKDF2Spec-salt: Uint8Array--><!--Device-PBKDF2Spec-salt: Uint8Array-End-->

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Kdf
- API version 11: SystemCapability.Security.CryptoFramework
