# CertChainValidationParameters

表示证书链校验的参数。

**起始版本：** 11

<!--Device-cert-interface CertChainValidationParameters--><!--Device-cert-interface CertChainValidationParameters-End-->

**系统能力：** SystemCapability.Security.Cert

## 导入模块

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## allowDownloadIntermediateCa

```TypeScript
allowDownloadIntermediateCa?: boolean
```

表示是否允许尝试从网络下载缺失的中间CA证书。true表示允许；false表示不允许。默认值为false。下载地址将从证书AIA扩展中获取，仅支持http，如需使用网络下载，需申请ohos.permission.INTERNET权限。配置方式请参见[声明权限](../../../../security/AccessToken/declare-permissions.md)。

**类型：** boolean

**默认值：** false

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CertChainValidationParameters-allowDownloadIntermediateCa?: boolean--><!--Device-CertChainValidationParameters-allowDownloadIntermediateCa?: boolean-End-->

**系统能力：** SystemCapability.Security.Cert

## certCRLs

```TypeScript
certCRLs?: Array<CertCRLCollection>
```

用于检查证书是否被吊销的CRL集合。

**类型：** Array<CertCRLCollection>

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CertChainValidationParameters-certCRLs?: Array<CertCRLCollection>--><!--Device-CertChainValidationParameters-certCRLs?: Array<CertCRLCollection>-End-->

**系统能力：** SystemCapability.Security.Cert

## date

```TypeScript
date?: string
```

用于检查证书有效性的日期。

**类型：** string

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CertChainValidationParameters-date?: string--><!--Device-CertChainValidationParameters-date?: string-End-->

**系统能力：** SystemCapability.Security.Cert

## keyUsage

```TypeScript
keyUsage?: Array<KeyUsageType>
```

表示需要校验证书中的密钥用途。

**类型：** Array<KeyUsageType>

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CertChainValidationParameters-keyUsage?: Array<KeyUsageType>--><!--Device-CertChainValidationParameters-keyUsage?: Array<KeyUsageType>-End-->

**系统能力：** SystemCapability.Security.Cert

## policy

```TypeScript
policy?: ValidationPolicyType
```

表示需要校验证书的策略类型。

**类型：** ValidationPolicyType

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CertChainValidationParameters-policy?: ValidationPolicyType--><!--Device-CertChainValidationParameters-policy?: ValidationPolicyType-End-->

**系统能力：** SystemCapability.Security.Cert

## revocationCheckParam

```TypeScript
revocationCheckParam?: RevocationCheckParameter
```

表示需要校验证书吊销状态的参数对象。

**类型：** RevocationCheckParameter

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CertChainValidationParameters-revocationCheckParam?: RevocationCheckParameter--><!--Device-CertChainValidationParameters-revocationCheckParam?: RevocationCheckParameter-End-->

**系统能力：** SystemCapability.Security.Cert

## sslHostname

```TypeScript
sslHostname?: string
```

表示需要校验证书中主机名，与policy配合使用。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CertChainValidationParameters-sslHostname?: string--><!--Device-CertChainValidationParameters-sslHostname?: string-End-->

**系统能力：** SystemCapability.Security.Cert

## trustAnchors

```TypeScript
trustAnchors: Array<X509TrustAnchor>
```

表示信任锚列表。

**类型：** Array<X509TrustAnchor>

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CertChainValidationParameters-trustAnchors: Array<X509TrustAnchor>--><!--Device-CertChainValidationParameters-trustAnchors: Array<X509TrustAnchor>-End-->

**系统能力：** SystemCapability.Security.Cert

## trustSystemCa

```TypeScript
trustSystemCa?: boolean
```

表示是否使用系统预置CA证书校验证书链。true表示使用；false表示不使用。

**类型：** boolean

**默认值：** false

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-CertChainValidationParameters-trustSystemCa?: boolean--><!--Device-CertChainValidationParameters-trustSystemCa?: boolean-End-->

**系统能力：** SystemCapability.Security.Cert

