# HKDFSpec

```TypeScript
interface HKDFSpec extends KdfSpec
```

Defines the child class of [KdfSpec](arkts-cryptoarchitecture-cryptoframework-kdfspec-i.md). It is a parameter for HKDF key derivation.

> **NOTE:** 
> 
> **key** is the original key material entered by the user. An empty string can be passed in for **info** and
> **salt** based on the mode.
> 
> For example, if the mode is **EXTRACT_AND_EXPAND**, all parameter values must be passed in. If the mode is
> **EXTRACT_ONLY**, **info** can be empty. When **HKDFSpec** is constructed, pass in **null** to **info**.
> 
> The default mode is **EXTRACT_AND_EXPAND**. The value **HKDF|SHA256|EXTRACT_AND_EXPAND** is equivalent to
> **HKDF|SHA256**.

**Inheritance/Implementation:** HKDFSpec extends [KdfSpec](arkts-cryptoarchitecture-cryptoframework-kdfspec-i.md)

**Since:** 12

<!--Device-cryptoFramework-interface HKDFSpec extends KdfSpec--><!--Device-cryptoFramework-interface HKDFSpec extends KdfSpec-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Kdf

## Modules to Import

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## info

```TypeScript
info: Uint8Array
```

Information used to expand the key.

**Type:** Uint8Array

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-HKDFSpec-info: Uint8Array--><!--Device-HKDFSpec-info: Uint8Array-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Kdf

## key

```TypeScript
key: string | Uint8Array
```

Key material.

**Type:** string &#124; Uint8Array

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-HKDFSpec-key: string | Uint8Array--><!--Device-HKDFSpec-key: string | Uint8Array-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Kdf

## keySize

```TypeScript
keySize: number
```

Length of the derived key, in bytes.

**Type:** number

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-HKDFSpec-keySize: int--><!--Device-HKDFSpec-keySize: int-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Kdf

## salt

```TypeScript
salt: Uint8Array
```

Salt value.

**Type:** Uint8Array

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-HKDFSpec-salt: Uint8Array--><!--Device-HKDFSpec-salt: Uint8Array-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Kdf
