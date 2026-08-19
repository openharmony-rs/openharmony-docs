# CertChainBuildResult

表示证书链创建结果。

**起始版本：** 23

<!--Device-cert-interface CertChainBuildResult--><!--Device-cert-interface CertChainBuildResult-End-->

**系统能力：** SystemCapability.Security.Cert

## 导入模块

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { certificateManager } from '@kit.DeviceCertificateKit';
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
```

## certChain

```TypeScript
readonly certChain: X509CertChain
```

生成的证书链对象。

**类型：** [X509CertChain](arkts-devicecertificate-cert-x509certchain-i.md)

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CertChainBuildResult-readonly certChain: X509CertChain--><!--Device-CertChainBuildResult-readonly certChain: X509CertChain-End-->

**系统能力：** SystemCapability.Security.Cert

## validationResult

```TypeScript
readonly validationResult: CertChainValidationResult
```

证书链校验结果。

**类型：** [CertChainValidationResult](arkts-devicecertificate-cert-certchainvalidationresult-i.md)

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CertChainBuildResult-readonly validationResult: CertChainValidationResult--><!--Device-CertChainBuildResult-readonly validationResult: CertChainValidationResult-End-->

**系统能力：** SystemCapability.Security.Cert

