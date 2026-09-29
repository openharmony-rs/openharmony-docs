# ScryptSpec

```TypeScript
interface ScryptSpec extends KdfSpec
```

Defines the child class of [KdfSpec](arkts-cryptoarchitecture-cryptoframework-kdfspec-i.md). It is a parameter for scrypt key derivation function (KDF).

> **NOTE:** 
> 
> **passphrase** specifies the original password. If **passphrase** is of the string type, pass in the data used for
> key derivation rather than a string of the HexString or Base64 type. In addition, the string must be in UTF-8
> format. Otherwise, the key derived may be different from the one expected.

**Inheritance/Implementation:** ScryptSpec extends [KdfSpec](arkts-cryptoarchitecture-cryptoframework-kdfspec-i.md)

**Since:** 18

<!--Device-cryptoFramework-interface ScryptSpec extends KdfSpec--><!--Device-cryptoFramework-interface ScryptSpec extends KdfSpec-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Kdf

## Modules to Import

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## keySize

```TypeScript
keySize: number
```

Length of the derived key, in bytes. The value must be a positive integer.

**Type:** number

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-ScryptSpec-keySize: int--><!--Device-ScryptSpec-keySize: int-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Kdf

## maxMemory

```TypeScript
maxMemory: number
```

Maximum memory size, in bytes. The value must be a positive integer.

**Type:** number

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-ScryptSpec-maxMemory: long--><!--Device-ScryptSpec-maxMemory: long-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Kdf

## n

```TypeScript
n: number
```

CPU/memory cost parameter. The value must be a positive integer.

**Type:** number

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-ScryptSpec-n: long--><!--Device-ScryptSpec-n: long-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Kdf

## p

```TypeScript
p: number
```

Parallelization parameter. The value must be a positive integer.

**Type:** number

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-ScryptSpec-p: long--><!--Device-ScryptSpec-p: long-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Kdf

## passphrase

```TypeScript
passphrase: string | Uint8Array
```

Original password entered by the user.

**Type:** string &#124; Uint8Array

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-ScryptSpec-passphrase: string | Uint8Array--><!--Device-ScryptSpec-passphrase: string | Uint8Array-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Kdf

## r

```TypeScript
r: number
```

Block size. The value must be a positive integer.

**Type:** number

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-ScryptSpec-r: long--><!--Device-ScryptSpec-r: long-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Kdf

## salt

```TypeScript
salt: Uint8Array
```

Salt value.

**Type:** Uint8Array

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-ScryptSpec-salt: Uint8Array--><!--Device-ScryptSpec-salt: Uint8Array-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Kdf
