# Credential

```TypeScript
export interface Credential
```

Represents detailed information about a credential.

**Since:** 11

<!--Device-certificateManager-export interface Credential--><!--Device-certificateManager-export interface Credential-End-->

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

<!--Device-Credential-alias: string--><!--Device-Credential-alias: string-End-->

**System capability:** SystemCapability.Security.CertificateManager

## certNum

```TypeScript
certNum: number
```

Number of certificates contained in the credential.

**Type:** number

**Since:** 11

<!--Device-Credential-certNum: int--><!--Device-Credential-certNum: int-End-->

**System capability:** SystemCapability.Security.CertificateManager

## certPurpose

```TypeScript
certPurpose?: CertificatePurpose
```

Credential usage. The default value is **CertificatePurpose.PURPOSE_DEFAULT**.

**Type:** [CertificatePurpose](arkts-devicecertificate-certificatemanager-certificatepurpose-e.md)

**Since:** 22

<!--Device-Credential-certPurpose?: CertificatePurpose--><!--Device-Credential-certPurpose?: CertificatePurpose-End-->

**System capability:** SystemCapability.Security.CertificateManager

## credentialData

```TypeScript
credentialData: Uint8Array
```

Binary data of a credential. The value contains up to 20480 bytes.

**Type:** Uint8Array

**Since:** 11

<!--Device-Credential-credentialData: Uint8Array--><!--Device-Credential-credentialData: Uint8Array-End-->

**System capability:** SystemCapability.Security.CertificateManager

## keyNum

```TypeScript
keyNum: number
```

Number of keys contained in the credential.

**Type:** number

**Since:** 11

<!--Device-Credential-keyNum: int--><!--Device-Credential-keyNum: int-End-->

**System capability:** SystemCapability.Security.CertificateManager

## keyUri

```TypeScript
keyUri: string
```

Unique identifier of a credential. The value contains up to 256 bytes.

**Type:** string

**Since:** 11

<!--Device-Credential-keyUri: string--><!--Device-Credential-keyUri: string-End-->

**System capability:** SystemCapability.Security.CertificateManager

## type

```TypeScript
type: string
```

Type of a credential. The value contains up to 8 bytes.

**Type:** string

**Since:** 11

<!--Device-Credential-type: string--><!--Device-Credential-type: string-End-->

**System capability:** SystemCapability.Security.CertificateManager
