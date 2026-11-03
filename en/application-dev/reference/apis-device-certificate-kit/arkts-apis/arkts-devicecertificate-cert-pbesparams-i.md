# PbesParams

```TypeScript
interface PbesParams
```

Enumerates PBES algorithm parameters. Currently, only PBES2 is supported.

**Since:** 21

<!--Device-cert-interface PbesParams--><!--Device-cert-interface PbesParams-End-->

**System capability:** SystemCapability.Security.Cert

## Modules to Import

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## encryptionAlgorithm

```TypeScript
encryptionAlgorithm?: PbesEncryptionAlgorithm
```

PBES algorithm type. The default value is **AES_256_CBC**.

**Type:** [PbesEncryptionAlgorithm](arkts-devicecertificate-cert-pbesencryptionalgorithm-e.md)

**Default:** PbesEncryptionAlgorithm.AES_256_CBC

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

<!--Device-PbesParams-encryptionAlgorithm?: PbesEncryptionAlgorithm--><!--Device-PbesParams-encryptionAlgorithm?: PbesEncryptionAlgorithm-End-->

**System capability:** SystemCapability.Security.Cert

## iterations

```TypeScript
iterations?: number
```

Number of iterations. The default value is **2048**.

**Type:** number

**Default:** 2048

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

<!--Device-PbesParams-iterations?: int--><!--Device-PbesParams-iterations?: int-End-->

**System capability:** SystemCapability.Security.Cert

## saltLen

```TypeScript
saltLen?: number
```

Salt length. The default value is **16**, and the minimum value is **8**.

**Type:** number

**Default:** 16

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

<!--Device-PbesParams-saltLen?: int--><!--Device-PbesParams-saltLen?: int-End-->

**System capability:** SystemCapability.Security.Cert
