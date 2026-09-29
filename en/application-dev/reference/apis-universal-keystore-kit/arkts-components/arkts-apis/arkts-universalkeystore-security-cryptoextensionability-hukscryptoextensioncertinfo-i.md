# HuksCryptoExtensionCertInfo

```TypeScript
export interface HuksCryptoExtensionCertInfo
```

Represents the information of certificate.

**Since:** 22

<!--Device-unnamed-export interface HuksCryptoExtensionCertInfo--><!--Device-unnamed-export interface HuksCryptoExtensionCertInfo-End-->

**System capability:** SystemCapability.Security.Huks.CryptoExtension

## Modules to Import

```TypeScript
import { CryptoExtensionAbility, HuksCryptoExtensionCertInfo, HuksCryptoExtensionResult, HuksCryptoExtensionResultCode, HuksCryptoExtensionParam, HuksCryptoExtensionParams } from '@kit.UniversalKeystoreKit';
```

## cert

```TypeScript
cert: Uint8Array
```

The content of the certificate.

**Type:** Uint8Array

**Since:** 22

<!--Device-HuksCryptoExtensionCertInfo-cert: Uint8Array--><!--Device-HuksCryptoExtensionCertInfo-cert: Uint8Array-End-->

**System capability:** SystemCapability.Security.Huks.CryptoExtension

## purpose

```TypeScript
purpose: certificateManager.CertificatePurpose
```

The type of the certificate, sign or encrypt.

**Type:** [certificateManager.CertificatePurpose](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-certificatemanager-certificatepurpose-e.md)

**Since:** 22

<!--Device-HuksCryptoExtensionCertInfo-purpose: certificateManager.CertificatePurpose--><!--Device-HuksCryptoExtensionCertInfo-purpose: certificateManager.CertificatePurpose-End-->

**System capability:** SystemCapability.Security.Huks.CryptoExtension

## resourceId

```TypeScript
resourceId: string
```

The resource index of the certificate.

**Type:** string

**Since:** 22

<!--Device-HuksCryptoExtensionCertInfo-resourceId: string--><!--Device-HuksCryptoExtensionCertInfo-resourceId: string-End-->

**System capability:** SystemCapability.Security.Huks.CryptoExtension
