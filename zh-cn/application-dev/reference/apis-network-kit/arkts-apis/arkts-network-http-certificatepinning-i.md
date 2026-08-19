# CertificatePinning

由应用配置的证书。

**起始版本：** 12

<!--Device-http-interface CertificatePinning--><!--Device-http-interface CertificatePinning-End-->

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { http } from '@kit.NetworkKit';
```

## hashAlgorithm

```TypeScript
hashAlgorithm: 'SHA-256'
```

加密算法，当前仅支持该算法。

**类型：** 'SHA-256'

**起始版本：** 12

<!--Device-CertificatePinning-hashAlgorithm: 'SHA-256'--><!--Device-CertificatePinning-hashAlgorithm: 'SHA-256'-End-->

**系统能力：** SystemCapability.Communication.NetStack

## publicKeyHash

```TypeScript
publicKeyHash: string
```

字符串类型的证书PIN码。

**类型：** string

**起始版本：** 12

<!--Device-CertificatePinning-publicKeyHash: string--><!--Device-CertificatePinning-publicKeyHash: string-End-->

**系统能力：** SystemCapability.Communication.NetStack

