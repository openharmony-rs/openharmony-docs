# CertChainValidationResult

表示证书链校验的返回值。

**起始版本：** 11

**系统能力：** SystemCapability.Security.Cert

## 导入模块

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## entityCert

```TypeScript
readonly entityCert: X509Cert
```

表示实体证书。

**类型：** [X509Cert](arkts-devicecertificate-cert-x509cert-i.md)

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Security.Cert

## trustAnchor

```TypeScript
readonly trustAnchor: X509TrustAnchor
```

表示信任锚。

**类型：** [X509TrustAnchor](arkts-devicecertificate-cert-x509trustanchor-i.md)

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Security.Cert
