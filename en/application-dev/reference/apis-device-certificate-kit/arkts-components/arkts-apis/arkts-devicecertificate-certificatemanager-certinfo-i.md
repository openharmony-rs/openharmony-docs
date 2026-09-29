# CertInfo

```TypeScript
export interface CertInfo
```

Represents detailed information about a certificate.

**Since:** 11

<!--Device-certificateManager-export interface CertInfo--><!--Device-certificateManager-export interface CertInfo-End-->

**System capability:** SystemCapability.Security.CertificateManager

## Modules to Import

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

## cert

```TypeScript
cert: Uint8Array
```

Binary data of a certificate. The value contains up to 8196 bytes.

**Type:** Uint8Array

**Since:** 11

<!--Device-CertInfo-cert: Uint8Array--><!--Device-CertInfo-cert: Uint8Array-End-->

**System capability:** SystemCapability.Security.CertificateManager

## certAlias

```TypeScript
certAlias: string
```

Alias of a certificate. The value contains up to 128 bytes.

**Type:** string

**Since:** 11

<!--Device-CertInfo-certAlias: string--><!--Device-CertInfo-certAlias: string-End-->

**System capability:** SystemCapability.Security.CertificateManager

## fingerprintSha256

```TypeScript
fingerprintSha256: string
```

Fingerprint of a certificate. The value contains up to 128 bytes.

**Type:** string

**Since:** 11

<!--Device-CertInfo-fingerprintSha256: string--><!--Device-CertInfo-fingerprintSha256: string-End-->

**System capability:** SystemCapability.Security.CertificateManager

## issuerName

```TypeScript
issuerName: string
```

Name of the certificate issuer. The value contains up to 256 bytes.

**Type:** string

**Since:** 11

<!--Device-CertInfo-issuerName: string--><!--Device-CertInfo-issuerName: string-End-->

**System capability:** SystemCapability.Security.CertificateManager

## notAfter

```TypeScript
notAfter: string
```

Expiry date of a certificate. The value contains up to 32 bytes.

**Type:** string

**Since:** 11

<!--Device-CertInfo-notAfter: string--><!--Device-CertInfo-notAfter: string-End-->

**System capability:** SystemCapability.Security.CertificateManager

## notBefore

```TypeScript
notBefore: string
```

Start date of a certificate. The value contains up to 32 bytes.

**Type:** string

**Since:** 11

<!--Device-CertInfo-notBefore: string--><!--Device-CertInfo-notBefore: string-End-->

**System capability:** SystemCapability.Security.CertificateManager

## serial

```TypeScript
serial: string
```

Serial number of a certificate. The value contains up to 64 bytes. The value is a hexadecimal string, for example, **62C2CB4DE8405E96**.

**Type:** string

**Since:** 11

<!--Device-CertInfo-serial: string--><!--Device-CertInfo-serial: string-End-->

**System capability:** SystemCapability.Security.CertificateManager

## state

```TypeScript
state: boolean
```

Certificate state. The value **true** indicates that the certificate is enabled, and **false** means the opposite.

**Type:** boolean

**Since:** 11

<!--Device-CertInfo-state: boolean--><!--Device-CertInfo-state: boolean-End-->

**System capability:** SystemCapability.Security.CertificateManager

## subjectName

```TypeScript
subjectName: string
```

Name of the certificate subject. The value contains up to 1024 bytes.

**Type:** string

**Since:** 11

<!--Device-CertInfo-subjectName: string--><!--Device-CertInfo-subjectName: string-End-->

**System capability:** SystemCapability.Security.CertificateManager

## uri

```TypeScript
uri: string
```

Unique identifier of a certificate. The value contains up to 256 bytes.

**Type:** string

**Since:** 11

<!--Device-CertInfo-uri: string--><!--Device-CertInfo-uri: string-End-->

**System capability:** SystemCapability.Security.CertificateManager
