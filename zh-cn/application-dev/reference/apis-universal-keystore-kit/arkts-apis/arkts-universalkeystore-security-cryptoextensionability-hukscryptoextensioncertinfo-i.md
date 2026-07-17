# HuksCryptoExtensionCertInfo

[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresultcode-e.md)中的certs数组中的元素。

**起始版本：** 22

<!--Device-unnamed-export interface HuksCryptoExtensionCertInfo--><!--Device-unnamed-export interface HuksCryptoExtensionCertInfo-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## 导入模块

```TypeScript
import { HuksCryptoExtensionCertInfo, HuksCryptoExtensionResultCode, HuksCryptoExtensionParams, HuksCryptoExtensionParam, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';
```

## cert

```TypeScript
cert: Uint8Array
```

证书。

**类型：** Uint8Array

**起始版本：** 22

<!--Device-HuksCryptoExtensionCertInfo-cert: Uint8Array--><!--Device-HuksCryptoExtensionCertInfo-cert: Uint8Array-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## purpose

```TypeScript
purpose: certificateManager.CertificatePurpose
```

表示证书链对应密钥的使用类型。

**类型：** certificateManager.CertificatePurpose

**起始版本：** 22

<!--Device-HuksCryptoExtensionCertInfo-purpose: certificateManager.CertificatePurpose--><!--Device-HuksCryptoExtensionCertInfo-purpose: certificateManager.CertificatePurpose-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## resourceId

```TypeScript
resourceId: string
```

资源ID。JSON格式，能够映射到Ukey中的某个资源。

**类型：** string

**起始版本：** 22

<!--Device-HuksCryptoExtensionCertInfo-resourceId: string--><!--Device-HuksCryptoExtensionCertInfo-resourceId: string-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

