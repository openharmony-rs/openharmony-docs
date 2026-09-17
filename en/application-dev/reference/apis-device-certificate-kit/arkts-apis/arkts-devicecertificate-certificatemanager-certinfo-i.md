# CertInfo

Represents detailed information about a certificate.

**Since:** 11

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

**System capability:** SystemCapability.Security.CertificateManager

## certAlias

```TypeScript
certAlias: string
```

Alias of a certificate. The value contains up to 128 bytes.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Security.CertificateManager

## fingerprintSha256

```TypeScript
fingerprintSha256: string
```

Fingerprint of a certificate. The value contains up to 128 bytes.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Security.CertificateManager

## issuerName

```TypeScript
issuerName: string
```

Name of the certificate issuer. The value contains up to 256 bytes.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Security.CertificateManager

## notAfter

```TypeScript
notAfter: string
```

Expiry date of a certificate. The value contains up to 32 bytes.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Security.CertificateManager

## notBefore

```TypeScript
notBefore: string
```

Start date of a certificate. The value contains up to 32 bytes.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Security.CertificateManager

## serial

```TypeScript
serial: string
```

Serial number of a certificate. The value contains up to 64 bytes. The value is a hexadecimal string, for example, **62C2CB4DE8405E96**.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Security.CertificateManager

## state

```TypeScript
state: boolean
```

Certificate state. The value **true** indicates that the certificate is enabled, and **false** means the opposite.

**Type:** boolean

**Since:** 11

**System capability:** SystemCapability.Security.CertificateManager

## subjectName

```TypeScript
subjectName: string
```

Name of the certificate subject. The value contains up to 1024 bytes.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Security.CertificateManager

## uri

```TypeScript
uri: string
```

Unique identifier of a certificate. The value contains up to 256 bytes.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Security.CertificateManager
