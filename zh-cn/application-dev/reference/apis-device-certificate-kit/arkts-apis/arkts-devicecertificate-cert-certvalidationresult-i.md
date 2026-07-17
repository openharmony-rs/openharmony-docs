# CertValidationResult

证书验证的结果。

**起始版本：** 26.0.0

<!--Device-cert-interface CertValidationResult--><!--Device-cert-interface CertValidationResult-End-->

**系统能力：** SystemCapability.Security.Cert

## 导入模块

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## certChain

```TypeScript
readonly certChain: Array<X509Cert>
```

验证后的证书链。验证成功时返回完整的证书链，从终端实体证书到信任锚点。可用于后续的证书信息查询或其他验证操作。

**类型：** Array<X509Cert>

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CertValidationResult-readonly certChain: Array<X509Cert>--><!--Device-CertValidationResult-readonly certChain: Array<X509Cert>-End-->

**系统能力：** SystemCapability.Security.Cert

