# CMSignatureSpec

表示签名、验签操作使用的参数集合，包括密钥使用目的、填充方式和摘要算法。

**起始版本：** 11

<!--Device-certificateManager-export interface CMSignatureSpec--><!--Device-certificateManager-export interface CMSignatureSpec-End-->

**系统能力：** SystemCapability.Security.CertificateManager

## 导入模块

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

## digest

```TypeScript
digest?: CmKeyDigest
```

表示摘要算法的枚举。默认值： CM_DIGEST_SHA256，表示使用SHA256摘要算法。

**类型：** CmKeyDigest

**起始版本：** 11

<!--Device-CMSignatureSpec-digest?: CmKeyDigest--><!--Device-CMSignatureSpec-digest?: CmKeyDigest-End-->

**系统能力：** SystemCapability.Security.CertificateManager

## padding

```TypeScript
padding?: CmKeyPadding
```

表示填充方式的枚举默认值： CM_PADDING_PSS，表示使用PSS填充方式。

**类型：** CmKeyPadding

**起始版本：** 11

<!--Device-CMSignatureSpec-padding?: CmKeyPadding--><!--Device-CMSignatureSpec-padding?: CmKeyPadding-End-->

**系统能力：** SystemCapability.Security.CertificateManager

## purpose

```TypeScript
purpose: CmKeyPurpose
```

表示密钥使用目的的枚举。

**类型：** CmKeyPurpose

**起始版本：** 11

<!--Device-CMSignatureSpec-purpose: CmKeyPurpose--><!--Device-CMSignatureSpec-purpose: CmKeyPurpose-End-->

**系统能力：** SystemCapability.Security.CertificateManager

