# CertValidationParams

证书验证的参数。

**起始版本：** 26.0.0

<!--Device-cert-interface CertValidationParams--><!--Device-cert-interface CertValidationParams-End-->

**系统能力：** SystemCapability.Security.Cert

## 导入模块

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## allowDownloadIntermediateCa

```TypeScript
allowDownloadIntermediateCa?: boolean
```

是否允许从网络下载中间CA证书。默认值为false。true：当构建证书链缺失中间证书时，尝试使用证书AIA扩展中颁发者地址下载颁发者证书，解决证书链不完整的问题；false：不允许从网络下载中间的CA证书。

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CertValidationParams-allowDownloadIntermediateCa?: boolean--><!--Device-CertValidationParams-allowDownloadIntermediateCa?: boolean-End-->

**系统能力：** SystemCapability.Security.Cert

## date

```TypeScript
date?: string
```

校验日期。格式为YYMMDDHHMMSSZ或YYYYMMDDHHMMSSZ，默认使用当前系统时间。支持自定义验证时间，适用于离线验证历史签名等场景。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CertValidationParams-date?: string--><!--Device-CertValidationParams-date?: string-End-->

**系统能力：** SystemCapability.Security.Cert

## emailAddresses

```TypeScript
emailAddresses?: Array<string>
```

邮箱地址。验证证书是否包含指定的邮箱地址。最大个数：1，邮箱地址最大长度：128。

**类型：** Array&lt;string&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CertValidationParams-emailAddresses?: Array<string>--><!--Device-CertValidationParams-emailAddresses?: Array<string>-End-->

**系统能力：** SystemCapability.Security.Cert

## hostnames

```TypeScript
hostnames?: Array<string>
```

主机名列表。验证证书的主体备用名（SAN）或通用名（CN）是否包含指定的主机名。最大个数：100，每个主机名最大长度：128。只要匹配其中一个主机名即校验成功。

**类型：** Array&lt;string&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CertValidationParams-hostnames?: Array<string>--><!--Device-CertValidationParams-hostnames?: Array<string>-End-->

**系统能力：** SystemCapability.Security.Cert

## ignoreErrs

```TypeScript
ignoreErrs?: Array<CertResult>
```

允许忽略特定的验证错误。最大个数：8。可忽略的错误包括：ERR_CERT_NOT_YET_VALID、ERR_CERT_HAS_EXPIRED、ERR_UNKNOWN_CRITICAL_EXTENSION、ERR_CRL_NOT_FOUND、ERR_CRL_NOT_YET_VALID、ERR_CRL_HAS_EXPIRED、ERR_OCSP_RESPONSE_NOT_FOUND、ERR_NETWORK_TIMEOUT。

**类型：** Array&lt;CertResult&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CertValidationParams-ignoreErrs?: Array<CertResult>--><!--Device-CertValidationParams-ignoreErrs?: Array<CertResult>-End-->

**系统能力：** SystemCapability.Security.Cert

## keyUsage

```TypeScript
keyUsage?: Array<KeyUsageType>
```

密钥用途列表。验证证书的密钥用途扩展是否包含指定的用途。最大个数：9。证书必须包含所有指定的密钥用途才校验成功。

**类型：** Array&lt;KeyUsageType&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CertValidationParams-keyUsage?: Array<KeyUsageType>--><!--Device-CertValidationParams-keyUsage?: Array<KeyUsageType>-End-->

**系统能力：** SystemCapability.Security.Cert

## partialChain

```TypeScript
partialChain?: boolean
```

是否允许部分链验证。默认值为false。true：允许使用信任证书中的任意证书作为信任锚，而非必须追溯到根证书；false：构建证书链时必须追溯到根证书。

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CertValidationParams-partialChain?: boolean--><!--Device-CertValidationParams-partialChain?: boolean-End-->

**系统能力：** SystemCapability.Security.Cert

## revokedParams

```TypeScript
revokedParams?: X509CertRevokedParams
```

证书吊销检查参数。用于检查证书是否被吊销。包含CRL列表、OCSP响应数据、是否允许在线检查等配置。

**类型：** X509CertRevokedParams

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CertValidationParams-revokedParams?: X509CertRevokedParams--><!--Device-CertValidationParams-revokedParams?: X509CertRevokedParams-End-->

**系统能力：** SystemCapability.Security.Cert

## trustSystemCa

```TypeScript
trustSystemCa?: boolean
```

是否信任系统CA。默认值为false。true：使用系统预置的CA证书库作为信任锚；false：不使用系统预置的CA证书库作为信任锚。

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CertValidationParams-trustSystemCa?: boolean--><!--Device-CertValidationParams-trustSystemCa?: boolean-End-->

**系统能力：** SystemCapability.Security.Cert

## trustedCerts

```TypeScript
trustedCerts?: Array<X509Cert>
```

信任证书列表。指定信任的根证书或中间CA证书，作为验证的信任锚点。最大个数：100。验证时，证书链须追溯至信任证书，必须设置此参数或将trustSystemCa设为true。

**类型：** Array&lt;X509Cert&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CertValidationParams-trustedCerts?: Array<X509Cert>--><!--Device-CertValidationParams-trustedCerts?: Array<X509Cert>-End-->

**系统能力：** SystemCapability.Security.Cert

## untrustedCerts

```TypeScript
untrustedCerts?: Array<X509Cert>
```

非信任证书列表。仅用于构建证书链的中间证书，不作为信任锚点。最大个数：100。

**类型：** Array&lt;X509Cert&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CertValidationParams-untrustedCerts?: Array<X509Cert>--><!--Device-CertValidationParams-untrustedCerts?: Array<X509Cert>-End-->

**系统能力：** SystemCapability.Security.Cert

## userId

```TypeScript
userId?: Uint8Array
```

用户ID。用于验证国密SM2证书时设置签名验证所需的用户标识符。最大长度：128。国密证书场景最常用的值为`[0x31, 0x32, 0x33, 0x34, 0x35, 0x36, 0x37, 0x38, 0x31, 0x32, 0x33, 0x34, 0x35, 0x36, 0x37, 0x38]`（对应ASCII字符串为"1234567812345678"，16字节）。设置userId后不支持证书吊销检查。

**类型：** Uint8Array

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CertValidationParams-userId?: Uint8Array--><!--Device-CertValidationParams-userId?: Uint8Array-End-->

**系统能力：** SystemCapability.Security.Cert

## validateDate

```TypeScript
validateDate?: boolean
```

是否校验日期。true：校验证书和CRL有效期；false：不校验证书和CRL有效期。

**类型：** boolean

**默认值：** true

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CertValidationParams-validateDate?: boolean--><!--Device-CertValidationParams-validateDate?: boolean-End-->

**系统能力：** SystemCapability.Security.Cert

