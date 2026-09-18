# CertAbstract

Represents brief information about a certificate.

**Since:** 11

**System capability:** SystemCapability.Security.CertificateManager

## Modules to Import

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

## certAlias

```TypeScript
certAlias: string
```

Alias of a certificate. The value contains up to 128 bytes.

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
