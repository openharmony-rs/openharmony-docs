# Pkcs12Data

P12（PKCS #12）数据，包含私钥、证书和其他证书。

**起始版本：** 18

<!--Device-cert-interface Pkcs12Data--><!--Device-cert-interface Pkcs12Data-End-->

**系统能力：** SystemCapability.Security.Cert

## 导入模块

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## cert

```TypeScript
cert?: X509Cert
```

和私钥匹配的证书。

**类型：** X509Cert

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-Pkcs12Data-cert?: X509Cert--><!--Device-Pkcs12Data-cert?: X509Cert-End-->

**系统能力：** SystemCapability.Security.Cert

## otherCerts

```TypeScript
otherCerts?: Array<X509Cert>
```

其他证书。

**类型：** Array<X509Cert>

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-Pkcs12Data-otherCerts?: Array<X509Cert>--><!--Device-Pkcs12Data-otherCerts?: Array<X509Cert>-End-->

**系统能力：** SystemCapability.Security.Cert

## privateKey

```TypeScript
privateKey?: string | Uint8Array
```

私钥。**string**对应PEM格式，**Uint8Array**对应DER格式。

**类型：** string | Uint8Array

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-Pkcs12Data-privateKey?: string | Uint8Array--><!--Device-Pkcs12Data-privateKey?: string | Uint8Array-End-->

**系统能力：** SystemCapability.Security.Cert

