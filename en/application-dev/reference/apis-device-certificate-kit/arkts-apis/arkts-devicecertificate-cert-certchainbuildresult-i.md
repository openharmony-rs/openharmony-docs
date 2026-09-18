# CertChainBuildResult

Represents the certificate chain build result.

**Since:** 12

**System capability:** SystemCapability.Security.Cert

## Modules to Import

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## certChain

```TypeScript
readonly certChain: X509CertChain
```

Certificate chain object created.

**Type:** [X509CertChain](arkts-devicecertificate-cert-x509certchain-i.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Cert

## validationResult

```TypeScript
readonly validationResult: CertChainValidationResult
```

Result of the certificate chain validation.

**Type:** [CertChainValidationResult](arkts-devicecertificate-cert-certchainvalidationresult-i.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Cert
