# SM2CipherTextSpec

```TypeScript
interface SM2CipherTextSpec
```

Represents the SM2 ciphertext parameters. You can use this object to generate SM2 ciphertext in ASN.1 format or obtain SM2 parameters from the SM2 ciphertext in ASN.1 format.

> **NOTE:** 
> 
> - **hashData** is a value obtained by applying the SM3 algorithm to the plaintext. It has a fixed length of 256bits.
> 
> - **cipherTextData** is the ciphertext with the same length as the plaintext.
> 
> - During the generation of ciphertext in C1C3C2 format, if the length of x (**C1_X**) or y (**C1_Y**) is less than 32 bytes, zeros must be added to the high-order bits to extend them to 32 bytes.

**Since:** 12

<!--Device-cryptoFramework-interface SM2CipherTextSpec--><!--Device-cryptoFramework-interface SM2CipherTextSpec-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Cipher

## Modules to Import

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## cipherTextData

```TypeScript
cipherTextData: Uint8Array
```

Indicates the ciphertext data, also known as C2.

**Type:** Uint8Array

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-SM2CipherTextSpec-cipherTextData: Uint8Array--><!--Device-SM2CipherTextSpec-cipherTextData: Uint8Array-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Cipher

## hashData

```TypeScript
hashData: Uint8Array
```

Indicates the hash data, also known as C3.

**Type:** Uint8Array

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-SM2CipherTextSpec-hashData: Uint8Array--><!--Device-SM2CipherTextSpec-hashData: Uint8Array-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Cipher

## xCoordinate

```TypeScript
xCoordinate: bigint
```

Indicates the x coordinate, also known as C1x.

**Type:** bigint

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-SM2CipherTextSpec-xCoordinate: bigint--><!--Device-SM2CipherTextSpec-xCoordinate: bigint-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Cipher

## yCoordinate

```TypeScript
yCoordinate: bigint
```

Indicates the y coordinate, also known as C1y.

**Type:** bigint

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-SM2CipherTextSpec-yCoordinate: bigint--><!--Device-SM2CipherTextSpec-yCoordinate: bigint-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Cipher
