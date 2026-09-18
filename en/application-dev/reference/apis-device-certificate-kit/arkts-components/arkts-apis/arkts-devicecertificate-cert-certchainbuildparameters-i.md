# CertChainBuildParameters

Represents the parameters for building a certificate chain.

**Since:** 12

**System capability:** SystemCapability.Security.Cert

## Modules to Import

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## certMatchParameters

```TypeScript
certMatchParameters: X509CertMatchParameters
```

Filter criteria.

**Type:** [X509CertMatchParameters](arkts-devicecertificate-cert-x509certmatchparameters-i.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Cert

## maxLength

```TypeScript
maxLength?: number
```

Maximum number of CA certificates in the certificate chain.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Cert

## validationParameters

```TypeScript
validationParameters: CertChainValidationParameters
```

Parameters for certificate chain validation.

**Type:** [CertChainValidationParameters](arkts-devicecertificate-cert-certchainvalidationparameters-i.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Cert
