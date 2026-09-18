# CMResult

Represents the result returned.

**Since:** 11

**System capability:** SystemCapability.Security.CertificateManager

## Modules to Import

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

## appUidList

```TypeScript
appUidList?: Array<string>
```

List of authorized applications.

**Type:** Array&lt;string&gt;

**Since:** 11

**System capability:** SystemCapability.Security.CertificateManager

## certInfo

```TypeScript
certInfo?: CertInfo
```

Detailed certificate information.

**Type:** [CertInfo](arkts-devicecertificate-certificatemanager-certinfo-i.md)

**Since:** 11

**System capability:** SystemCapability.Security.CertificateManager

## certList

```TypeScript
certList?: Array<CertAbstract>
```

Brief certificate information.

**Type:** Array&lt;[CertAbstract](arkts-devicecertificate-certificatemanager-certabstract-i.md)&gt;

**Since:** 11

**System capability:** SystemCapability.Security.CertificateManager

## credential

```TypeScript
credential?: Credential
```

Detailed credential information.

**Type:** [Credential](arkts-devicecertificate-certificatemanager-credential-i.md)

**Since:** 11

**System capability:** SystemCapability.Security.CertificateManager

## credentialDetailList

```TypeScript
credentialDetailList?: Array<Credential>
```

Represents detailed information about a credential.

**Type:** Array&lt;[Credential](arkts-devicecertificate-certificatemanager-credential-i.md)&gt;

**Since:** 22

**System capability:** SystemCapability.Security.CertificateManager

## credentialList

```TypeScript
credentialList?: Array<CredentialAbstract>
```

Brief credential information.

**Type:** Array&lt;[CredentialAbstract](arkts-devicecertificate-certificatemanager-credentialabstract-i.md)&gt;

**Since:** 11

**System capability:** SystemCapability.Security.CertificateManager

## outData

```TypeScript
outData?: Uint8Array
```

Signature generated.

**Type:** Uint8Array

**Since:** 11

**System capability:** SystemCapability.Security.CertificateManager

## uri

```TypeScript
uri?: string
```

Unique identifier of a certificate or credential. The value contains up to 256 bytes.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Security.CertificateManager

## uriList

```TypeScript
uriList?: Array<string>
```

Certificate URI list. **Since**: 26.0.0

**Type:** Array&lt;string&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.CertificateManager
