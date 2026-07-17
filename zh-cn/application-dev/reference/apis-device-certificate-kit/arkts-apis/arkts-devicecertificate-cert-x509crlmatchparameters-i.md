# X509CRLMatchParameters

用于匹配证书吊销列表的过滤参数。如果参数中任一项都未指定，则匹配所有证书吊销列表。

**起始版本：** 11

<!--Device-cert-interface X509CRLMatchParameters--><!--Device-cert-interface X509CRLMatchParameters-End-->

**系统能力：** SystemCapability.Security.Cert

## 导入模块

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## issuer

```TypeScript
issuer?: Array<Uint8Array>
```

指定CRL颁发者，为DER编码格式。

**类型：** Array<Uint8Array>

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRLMatchParameters-issuer?: Array<Uint8Array>--><!--Device-X509CRLMatchParameters-issuer?: Array<Uint8Array>-End-->

**系统能力：** SystemCapability.Security.Cert

## maxCRL

```TypeScript
maxCRL?: bigint
```

指定CRL编号（CRL number）的最大值。

**类型：** bigint

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRLMatchParameters-maxCRL?: bigint--><!--Device-X509CRLMatchParameters-maxCRL?: bigint-End-->

**系统能力：** SystemCapability.Security.Cert

## minCRL

```TypeScript
minCRL?: bigint
```

指定CRL编号（CRL number）的最小值。

**类型：** bigint

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRLMatchParameters-minCRL?: bigint--><!--Device-X509CRLMatchParameters-minCRL?: bigint-End-->

**系统能力：** SystemCapability.Security.Cert

## updateDateTime

```TypeScript
updateDateTime?: string
```

指定CRL更新时间。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRLMatchParameters-updateDateTime?: string--><!--Device-X509CRLMatchParameters-updateDateTime?: string-End-->

**系统能力：** SystemCapability.Security.Cert

## x509Cert

```TypeScript
x509Cert?: X509Cert
```

指定具体的证书对象。

**类型：** X509Cert

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRLMatchParameters-x509Cert?: X509Cert--><!--Device-X509CRLMatchParameters-x509Cert?: X509Cert-End-->

**系统能力：** SystemCapability.Security.Cert

