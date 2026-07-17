# Credential

表示凭据详细信息。

**起始版本：** 11

<!--Device-certificateManager-export interface Credential--><!--Device-certificateManager-export interface Credential-End-->

**系统能力：** SystemCapability.Security.CertificateManager

## 导入模块

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

## alias

```TypeScript
alias: string
```

表示凭据的别名，最大长度为128字节。

**类型：** string

**起始版本：** 11

<!--Device-Credential-alias: string--><!--Device-Credential-alias: string-End-->

**系统能力：** SystemCapability.Security.CertificateManager

## certNum

```TypeScript
certNum: number
```

表示凭据中包含的证书个数。

**类型：** number

**起始版本：** 11

<!--Device-Credential-certNum: int--><!--Device-Credential-certNum: int-End-->

**系统能力：** SystemCapability.Security.CertificateManager

## certPurpose

```TypeScript
certPurpose?: CertificatePurpose
```

表示凭据的用途。默认值为CertificatePurpose.PURPOSE_DEFAULT。

**类型：** CertificatePurpose

**起始版本：** 22

<!--Device-Credential-certPurpose?: CertificatePurpose--><!--Device-Credential-certPurpose?: CertificatePurpose-End-->

**系统能力：** SystemCapability.Security.CertificateManager

## credentialData

```TypeScript
credentialData: Uint8Array
```

表示凭据二进制数据，最大长度为20480字节。

**类型：** Uint8Array

**起始版本：** 11

<!--Device-Credential-credentialData: Uint8Array--><!--Device-Credential-credentialData: Uint8Array-End-->

**系统能力：** SystemCapability.Security.CertificateManager

## keyNum

```TypeScript
keyNum: number
```

表示凭据中包含的密钥个数。

**类型：** number

**起始版本：** 11

<!--Device-Credential-keyNum: int--><!--Device-Credential-keyNum: int-End-->

**系统能力：** SystemCapability.Security.CertificateManager

## keyUri

```TypeScript
keyUri: string
```

表示凭据的唯一标识符，最大长度为256字节。

**类型：** string

**起始版本：** 11

<!--Device-Credential-keyUri: string--><!--Device-Credential-keyUri: string-End-->

**系统能力：** SystemCapability.Security.CertificateManager

## type

```TypeScript
type: string
```

表示凭据的类型，最大长度为8字节。

**类型：** string

**起始版本：** 11

<!--Device-Credential-type: string--><!--Device-Credential-type: string-End-->

**系统能力：** SystemCapability.Security.CertificateManager

