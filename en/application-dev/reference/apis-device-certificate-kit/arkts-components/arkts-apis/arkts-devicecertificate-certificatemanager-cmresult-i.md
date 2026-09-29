# CMResult

```TypeScript
export interface CMResult
```

Represents the result returned.

**Since:** 11

<!--Device-certificateManager-export interface CMResult--><!--Device-certificateManager-export interface CMResult-End-->

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

<!--Device-CMResult-appUidList?: Array<string>--><!--Device-CMResult-appUidList?: Array<string>-End-->

**System capability:** SystemCapability.Security.CertificateManager

## certInfo

```TypeScript
certInfo?: CertInfo
```

Detailed certificate information.

**Type:** [CertInfo](arkts-devicecertificate-certificatemanager-certinfo-i.md)

**Since:** 11

<!--Device-CMResult-certInfo?: CertInfo--><!--Device-CMResult-certInfo?: CertInfo-End-->

**System capability:** SystemCapability.Security.CertificateManager

## certList

```TypeScript
certList?: Array<CertAbstract>
```

Brief certificate information.

**Type:** Array&lt;[CertAbstract](arkts-devicecertificate-certificatemanager-certabstract-i.md)&gt;

**Since:** 11

<!--Device-CMResult-certList?: Array<CertAbstract>--><!--Device-CMResult-certList?: Array<CertAbstract>-End-->

**System capability:** SystemCapability.Security.CertificateManager

## credential

```TypeScript
credential?: Credential
```

Detailed credential information.

**Type:** [Credential](arkts-devicecertificate-certificatemanager-credential-i.md)

**Since:** 11

<!--Device-CMResult-credential?: Credential--><!--Device-CMResult-credential?: Credential-End-->

**System capability:** SystemCapability.Security.CertificateManager

## credentialDetailList

```TypeScript
credentialDetailList?: Array<Credential>
```

Represents detailed information about a credential.

**Type:** Array&lt;[Credential](arkts-devicecertificate-certificatemanager-credential-i.md)&gt;

**Since:** 22

<!--Device-CMResult-credentialDetailList?: Array<Credential>--><!--Device-CMResult-credentialDetailList?: Array<Credential>-End-->

**System capability:** SystemCapability.Security.CertificateManager

## credentialList

```TypeScript
credentialList?: Array<CredentialAbstract>
```

Brief credential information.

**Type:** Array&lt;[CredentialAbstract](arkts-devicecertificate-certificatemanager-credentialabstract-i.md)&gt;

**Since:** 11

<!--Device-CMResult-credentialList?: Array<CredentialAbstract>--><!--Device-CMResult-credentialList?: Array<CredentialAbstract>-End-->

**System capability:** SystemCapability.Security.CertificateManager

## outData

```TypeScript
outData?: Uint8Array
```

Signature generated.

**Type:** Uint8Array

**Since:** 11

<!--Device-CMResult-outData?: Uint8Array--><!--Device-CMResult-outData?: Uint8Array-End-->

**System capability:** SystemCapability.Security.CertificateManager

## uri

```TypeScript
uri?: string
```

Unique identifier of a certificate or credential. The value contains up to 256 bytes.

**Type:** string

**Since:** 11

<!--Device-CMResult-uri?: string--><!--Device-CMResult-uri?: string-End-->

**System capability:** SystemCapability.Security.CertificateManager

## uriList

```TypeScript
uriList?: Array<string>
```

Certificate URI list. **Since**: 26.0.0

**Type:** Array&lt;string&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-CMResult-uriList?: Array<string>--><!--Device-CMResult-uriList?: Array<string>-End-->

**System capability:** SystemCapability.Security.CertificateManager
