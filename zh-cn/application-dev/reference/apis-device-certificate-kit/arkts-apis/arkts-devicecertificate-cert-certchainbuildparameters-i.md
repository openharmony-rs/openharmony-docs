# CertChainBuildParameters

用于指定证书链创建参数。

**起始版本：** 12

<!--Device-cert-interface CertChainBuildParameters--><!--Device-cert-interface CertChainBuildParameters-End-->

**系统能力：** SystemCapability.Security.Cert

## 导入模块

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## certMatchParameters

```TypeScript
certMatchParameters: X509CertMatchParameters
```

指定过滤条件。

**类型：** X509CertMatchParameters

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CertChainBuildParameters-certMatchParameters: X509CertMatchParameters--><!--Device-CertChainBuildParameters-certMatchParameters: X509CertMatchParameters-End-->

**系统能力：** SystemCapability.Security.Cert

## maxLength

```TypeScript
maxLength?: number
```

指定CA证书的最大数量。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CertChainBuildParameters-maxLength?: int--><!--Device-CertChainBuildParameters-maxLength?: int-End-->

**系统能力：** SystemCapability.Security.Cert

## validationParameters

```TypeScript
validationParameters: CertChainValidationParameters
```

指定验证条件。

**类型：** CertChainValidationParameters

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CertChainBuildParameters-validationParameters: CertChainValidationParameters--><!--Device-CertChainBuildParameters-validationParameters: CertChainValidationParameters-End-->

**系统能力：** SystemCapability.Security.Cert

