# CertValidationResult

Result of certificate validation.

**Since:** 26.0.0

**System capability:** SystemCapability.Security.Cert

## Modules to Import

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## certChain

```TypeScript
readonly certChain: Array<X509Cert>
```

Indicates the authenticated certificate chain. Upon successful authentication, the complete certificate chain is returned, from the end-entity certificate to the trust anchor. It can be used for subsequent certificate information query or other verification operations.

**Type:** Array&lt;[X509Cert](arkts-devicecertificate-cert-x509cert-i.md)&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.Cert
