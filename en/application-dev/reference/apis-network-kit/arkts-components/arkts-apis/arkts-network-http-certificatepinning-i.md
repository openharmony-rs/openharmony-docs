# CertificatePinning

```TypeScript
interface CertificatePinning
```

Defines the dynamic configuration of certificate pinning.

**Since:** 12

<!--Device-http-interface CertificatePinning--><!--Device-http-interface CertificatePinning-End-->

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { http } from '@kit.NetworkKit';
```

## hashAlgorithm

```TypeScript
hashAlgorithm: 'SHA-256'
```

Encryption algorithm. Currently, only SHA-256 is supported.

**Type:** 'SHA-256'

**Since:** 12

<!--Device-CertificatePinning-hashAlgorithm: 'SHA-256'--><!--Device-CertificatePinning-hashAlgorithm: 'SHA-256'-End-->

**System capability:** SystemCapability.Communication.NetStack

## publicKeyHash

```TypeScript
publicKeyHash: string
```

Certificate PIN of the string type.

**Type:** string

**Since:** 12

<!--Device-CertificatePinning-publicKeyHash: string--><!--Device-CertificatePinning-publicKeyHash: string-End-->

**System capability:** SystemCapability.Communication.NetStack
