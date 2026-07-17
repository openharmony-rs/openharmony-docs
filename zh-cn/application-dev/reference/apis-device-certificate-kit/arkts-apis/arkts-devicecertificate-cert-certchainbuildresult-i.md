# CertChainBuildResult

用于指定证书链创建结果。

**起始版本：** 12

<!--Device-cert-interface CertChainBuildResult--><!--Device-cert-interface CertChainBuildResult-End-->

**系统能力：** SystemCapability.Security.Cert

## 导入模块

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## certChain

```TypeScript
readonly certChain: X509CertChain
```

生成的证书链对象。

**类型：** X509CertChain

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CertChainBuildResult-readonly certChain: X509CertChain--><!--Device-CertChainBuildResult-readonly certChain: X509CertChain-End-->

**系统能力：** SystemCapability.Security.Cert

## validationResult

```TypeScript
readonly validationResult: CertChainValidationResult
```

证书链校验结果。

**类型：** CertChainValidationResult

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CertChainBuildResult-readonly validationResult: CertChainValidationResult--><!--Device-CertChainBuildResult-readonly validationResult: CertChainValidationResult-End-->

**系统能力：** SystemCapability.Security.Cert

