# CredentialAbstract

```TypeScript
export interface CredentialAbstract
```

Represents brief information about a credential.

**Since:** 11

<!--Device-certificateManager-export interface CredentialAbstract--><!--Device-certificateManager-export interface CredentialAbstract-End-->

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

<!--Device-CredentialAbstract-alias: string--><!--Device-CredentialAbstract-alias: string-End-->

**System capability:** SystemCapability.Security.CertificateManager

## keyUri

```TypeScript
keyUri: string
```

Unique identifier of a credential. The value contains up to 256 bytes.

**Type:** string

**Since:** 11

<!--Device-CredentialAbstract-keyUri: string--><!--Device-CredentialAbstract-keyUri: string-End-->

**System capability:** SystemCapability.Security.CertificateManager

## type

```TypeScript
type: string
```

Type of a credential. The value contains up to 8 bytes.

**Type:** string

**Since:** 11

<!--Device-CredentialAbstract-type: string--><!--Device-CredentialAbstract-type: string-End-->

**System capability:** SystemCapability.Security.CertificateManager
