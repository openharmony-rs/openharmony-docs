# CMSignatureSpec

Represents a set of parameters used for signing or signature verification, including the key usage purpose, padding mode, and digest algorithm.

**Since:** 11

**System capability:** SystemCapability.Security.CertificateManager

## Modules to Import

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

## digest

```TypeScript
digest?: CmKeyDigest
```

Digest algorithm. Default value: CM_DIGEST_SHA256: indicates that the SHA256 digest algorithm is used.

**Type:** [CmKeyDigest](arkts-devicecertificate-certificatemanager-cmkeydigest-e.md)

**Since:** 11

**System capability:** SystemCapability.Security.CertificateManager

## padding

```TypeScript
padding?: CmKeyPadding
```

Enumeration representing the padding mode. Default value: CM_PADDING_PSS: indicates that the PSS filling mode is used.

**Type:** [CmKeyPadding](arkts-devicecertificate-certificatemanager-cmkeypadding-e.md)

**Since:** 11

**System capability:** SystemCapability.Security.CertificateManager

## purpose

```TypeScript
purpose: CmKeyPurpose
```

Purpose of using the key.

**Type:** [CmKeyPurpose](arkts-devicecertificate-certificatemanager-cmkeypurpose-e.md)

**Since:** 11

**System capability:** SystemCapability.Security.CertificateManager
