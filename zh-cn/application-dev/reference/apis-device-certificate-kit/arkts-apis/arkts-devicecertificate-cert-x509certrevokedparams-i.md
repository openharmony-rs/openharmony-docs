# X509CertRevokedParams

表示证书吊销检查参数。

**起始版本：** 26.0.0

<!--Device-cert-interface X509CertRevokedParams--><!--Device-cert-interface X509CertRevokedParams-End-->

**系统能力：** SystemCapability.Security.Cert

## 导入模块

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## allowDownloadCrl

```TypeScript
allowDownloadCrl?: boolean
```

是否允许下载CRL，默认值为false。true：尝试使用证书的CDP扩展下载CRL；false：不尝试下载CRL。

> **说明：**  
>  
> 如果crls中存在匹配的CRL，则跳过下载。

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-X509CertRevokedParams-allowDownloadCrl?: boolean--><!--Device-X509CertRevokedParams-allowDownloadCrl?: boolean-End-->

**系统能力：** SystemCapability.Security.Cert

## allowOcspCheckOnline

```TypeScript
allowOcspCheckOnline?: boolean
```

是否允许在线OCSP检查，默认值为false。true：执行在线OCSP检查，即尝试从证书AIA扩展获取OCSP URL并发送请求获取响应；false：不执行在线OCSP检查。

> **说明：**  
>  
> 如果在ocspResponses中找到匹配的OCSP响应，则跳过在线OCSP检查。

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-X509CertRevokedParams-allowOcspCheckOnline?: boolean--><!--Device-X509CertRevokedParams-allowOcspCheckOnline?: boolean-End-->

**系统能力：** SystemCapability.Security.Cert

## crls

```TypeScript
crls?: Array<X509CRL>
```

CRL列表。最大个数：100。

**类型：** Array<X509CRL>

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-X509CertRevokedParams-crls?: Array<X509CRL>--><!--Device-X509CertRevokedParams-crls?: Array<X509CRL>-End-->

**系统能力：** SystemCapability.Security.Cert

## ocspDigest

```TypeScript
ocspDigest?: OcspDigest
```

OCSP请求使用的摘要算法，默认值为SHA256。

**类型：** OcspDigest

**默认值：** SHA256

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-X509CertRevokedParams-ocspDigest?: OcspDigest--><!--Device-X509CertRevokedParams-ocspDigest?: OcspDigest-End-->

**系统能力：** SystemCapability.Security.Cert

## ocspResponses

```TypeScript
ocspResponses?: Array<Uint8Array>
```

OCSP响应数据。预置的OCSP响应数据。最大个数：100。

**类型：** Array<Uint8Array>

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-X509CertRevokedParams-ocspResponses?: Array<Uint8Array>--><!--Device-X509CertRevokedParams-ocspResponses?: Array<Uint8Array>-End-->

**系统能力：** SystemCapability.Security.Cert

## revocationFlags

```TypeScript
revocationFlags: Array<CertRevocationFlag>
```

吊销检查标志。数组长度范围：[1, 4]。数组必须包含CERT_REVOCATION_CRL_CHECK或CERT_REVOCATION_OCSP_CHECK。

**类型：** Array<CertRevocationFlag>

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-X509CertRevokedParams-revocationFlags: Array<CertRevocationFlag>--><!--Device-X509CertRevokedParams-revocationFlags: Array<CertRevocationFlag>-End-->

**系统能力：** SystemCapability.Security.Cert

