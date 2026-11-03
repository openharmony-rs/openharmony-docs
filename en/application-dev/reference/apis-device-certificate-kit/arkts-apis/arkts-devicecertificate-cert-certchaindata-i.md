# CertChainData

```TypeScript
interface CertChainData
```

Defines the certificate chain data, which is passed in as input parameters during certificate chain verification.

**Since:** 9

<!--Device-cert-interface CertChainData--><!--Device-cert-interface CertChainData-End-->

**System capability:** SystemCapability.Security.Cert

## Modules to Import

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## count

```TypeScript
count: number
```

Number of certificates.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CertChainData-count: int--><!--Device-CertChainData-count: int-End-->

**System capability:** SystemCapability.Security.Cert

## data

```TypeScript
data: Uint8Array
```

Certificate data, which is a combination of the certificate length (2 bytes) and data. For example, **08ABCDEFGH07ABCDEFG** indicates that the first certificate is an 8-byte certificate, followed by 8-byte certificate data. The second certificate is a 7-byte certificate, followed by 7-byte certificate data.

**Type:** Uint8Array

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CertChainData-data: Uint8Array--><!--Device-CertChainData-data: Uint8Array-End-->

**System capability:** SystemCapability.Security.Cert

## encodingFormat

```TypeScript
encodingFormat: EncodingFormat
```

Encoding format.

**Type:** [EncodingFormat](arkts-devicecertificate-cert-encodingformat-e.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CertChainData-encodingFormat: EncodingFormat--><!--Device-CertChainData-encodingFormat: EncodingFormat-End-->

**System capability:** SystemCapability.Security.Cert
