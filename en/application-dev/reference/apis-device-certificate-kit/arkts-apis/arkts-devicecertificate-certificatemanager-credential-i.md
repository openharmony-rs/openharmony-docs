# Credential

Represents detailed information about a credential.

**Since:** 11

**System capability:** SystemCapability.Security.CertificateManager

## Modules to Import

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

## alias

```TypeScript
alias: string
```

Alias of a credential. The value contains up to 128 bytes.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Security.CertificateManager

## certNum

```TypeScript
certNum: number
```

Number of certificates contained in the credential.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Security.CertificateManager

## certPurpose

```TypeScript
certPurpose?: CertificatePurpose
```

Credential usage. The default value is **CertificatePurpose.PURPOSE_DEFAULT**.

**Type:** [CertificatePurpose](arkts-devicecertificate-certificatemanager-certificatepurpose-e.md)

**Since:** 22

**System capability:** SystemCapability.Security.CertificateManager

## credentialData

```TypeScript
credentialData: Uint8Array
```

Binary data of a credential. The value contains up to 20480 bytes.

**Type:** Uint8Array

**Since:** 11

**System capability:** SystemCapability.Security.CertificateManager

## keyNum

```TypeScript
keyNum: number
```

Number of keys contained in the credential.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Security.CertificateManager

## keyUri

```TypeScript
keyUri: string
```

Unique identifier of a credential. The value contains up to 256 bytes.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Security.CertificateManager

## type

```TypeScript
type: string
```

Type of a credential. The value contains up to 8 bytes.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Security.CertificateManager
