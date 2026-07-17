# CertResult

表示执行结果的枚举。

**起始版本：** 9

<!--Device-cert-enum CertResult--><!--Device-cert-enum CertResult-End-->

**系统能力：** SystemCapability.Security.Cert

## INVALID_PARAMS

```TypeScript
INVALID_PARAMS = 401
```

非法入参。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CertResult-INVALID_PARAMS = 401--><!--Device-CertResult-INVALID_PARAMS = 401-End-->

**系统能力：** SystemCapability.Security.Cert

## NOT_SUPPORT

```TypeScript
NOT_SUPPORT = 801
```

操作不支持。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CertResult-NOT_SUPPORT = 801--><!--Device-CertResult-NOT_SUPPORT = 801-End-->

**系统能力：** SystemCapability.Security.Cert

## ERR_OUT_OF_MEMORY

```TypeScript
ERR_OUT_OF_MEMORY = 19020001
```

内存错误。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CertResult-ERR_OUT_OF_MEMORY = 19020001--><!--Device-CertResult-ERR_OUT_OF_MEMORY = 19020001-End-->

**系统能力：** SystemCapability.Security.Cert

## ERR_RUNTIME_ERROR

```TypeScript
ERR_RUNTIME_ERROR = 19020002
```

运行时外部错误。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CertResult-ERR_RUNTIME_ERROR = 19020002--><!--Device-CertResult-ERR_RUNTIME_ERROR = 19020002-End-->

**系统能力：** SystemCapability.Security.Cert

## ERR_PARAMETER_CHECK_FAILED

```TypeScript
ERR_PARAMETER_CHECK_FAILED = 19020003
```

参数检查失败。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-CertResult-ERR_PARAMETER_CHECK_FAILED = 19020003--><!--Device-CertResult-ERR_PARAMETER_CHECK_FAILED = 19020003-End-->

**系统能力：** SystemCapability.Security.Cert

## ERR_CRYPTO_OPERATION

```TypeScript
ERR_CRYPTO_OPERATION = 19030001
```

调用三方算法库API出错。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CertResult-ERR_CRYPTO_OPERATION = 19030001--><!--Device-CertResult-ERR_CRYPTO_OPERATION = 19030001-End-->

**系统能力：** SystemCapability.Security.Cert

## ERR_CERT_SIGNATURE_FAILURE

```TypeScript
ERR_CERT_SIGNATURE_FAILURE = 19030002
```

证书签名验证错误。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CertResult-ERR_CERT_SIGNATURE_FAILURE = 19030002--><!--Device-CertResult-ERR_CERT_SIGNATURE_FAILURE = 19030002-End-->

**系统能力：** SystemCapability.Security.Cert

## ERR_CERT_NOT_YET_VALID

```TypeScript
ERR_CERT_NOT_YET_VALID = 19030003
```

证书尚未生效。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CertResult-ERR_CERT_NOT_YET_VALID = 19030003--><!--Device-CertResult-ERR_CERT_NOT_YET_VALID = 19030003-End-->

**系统能力：** SystemCapability.Security.Cert

## ERR_CERT_HAS_EXPIRED

```TypeScript
ERR_CERT_HAS_EXPIRED = 19030004
```

证书过期。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CertResult-ERR_CERT_HAS_EXPIRED = 19030004--><!--Device-CertResult-ERR_CERT_HAS_EXPIRED = 19030004-End-->

**系统能力：** SystemCapability.Security.Cert

## ERR_UNABLE_TO_GET_ISSUER_CERT_LOCALLY

```TypeScript
ERR_UNABLE_TO_GET_ISSUER_CERT_LOCALLY = 19030005
```

无法获取证书的颁发者。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CertResult-ERR_UNABLE_TO_GET_ISSUER_CERT_LOCALLY = 19030005--><!--Device-CertResult-ERR_UNABLE_TO_GET_ISSUER_CERT_LOCALLY = 19030005-End-->

**系统能力：** SystemCapability.Security.Cert

## ERR_KEYUSAGE_NO_CERTSIGN

```TypeScript
ERR_KEYUSAGE_NO_CERTSIGN = 19030006
```

证书的密钥用途不含证书签名。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CertResult-ERR_KEYUSAGE_NO_CERTSIGN = 19030006--><!--Device-CertResult-ERR_KEYUSAGE_NO_CERTSIGN = 19030006-End-->

**系统能力：** SystemCapability.Security.Cert

## ERR_KEYUSAGE_NO_DIGITAL_SIGNATURE

```TypeScript
ERR_KEYUSAGE_NO_DIGITAL_SIGNATURE = 19030007
```

证书的密钥用途不含数字签名。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CertResult-ERR_KEYUSAGE_NO_DIGITAL_SIGNATURE = 19030007--><!--Device-CertResult-ERR_KEYUSAGE_NO_DIGITAL_SIGNATURE = 19030007-End-->

**系统能力：** SystemCapability.Security.Cert

## ERR_MAYBE_WRONG_PASSWORD

```TypeScript
ERR_MAYBE_WRONG_PASSWORD = 19030008
```

私钥密码可能不正确。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CertResult-ERR_MAYBE_WRONG_PASSWORD = 19030008--><!--Device-CertResult-ERR_MAYBE_WRONG_PASSWORD = 19030008-End-->

**系统能力：** SystemCapability.Security.Cert

## ERR_CERT_UNTRUSTED

```TypeScript
ERR_CERT_UNTRUSTED = 19030009
```

证书不受信任。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CertResult-ERR_CERT_UNTRUSTED = 19030009--><!--Device-CertResult-ERR_CERT_UNTRUSTED = 19030009-End-->

**系统能力：** SystemCapability.Security.Cert

## ERR_CERT_HAS_REVOKED

```TypeScript
ERR_CERT_HAS_REVOKED = 19030010
```

证书已被吊销。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CertResult-ERR_CERT_HAS_REVOKED = 19030010--><!--Device-CertResult-ERR_CERT_HAS_REVOKED = 19030010-End-->

**系统能力：** SystemCapability.Security.Cert

## ERR_UNKNOWN_CRITICAL_EXTENSION

```TypeScript
ERR_UNKNOWN_CRITICAL_EXTENSION = 19030011
```

未知的关键扩展。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CertResult-ERR_UNKNOWN_CRITICAL_EXTENSION = 19030011--><!--Device-CertResult-ERR_UNKNOWN_CRITICAL_EXTENSION = 19030011-End-->

**系统能力：** SystemCapability.Security.Cert

## ERR_CERT_HOSTNAME_MISMATCH

```TypeScript
ERR_CERT_HOSTNAME_MISMATCH = 19030012
```

证书主机名不匹配。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CertResult-ERR_CERT_HOSTNAME_MISMATCH = 19030012--><!--Device-CertResult-ERR_CERT_HOSTNAME_MISMATCH = 19030012-End-->

**系统能力：** SystemCapability.Security.Cert

## ERR_CERT_EMAIL_ADDRESS_MISMATCH

```TypeScript
ERR_CERT_EMAIL_ADDRESS_MISMATCH = 19030013
```

证书邮箱地址不匹配。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CertResult-ERR_CERT_EMAIL_ADDRESS_MISMATCH = 19030013--><!--Device-CertResult-ERR_CERT_EMAIL_ADDRESS_MISMATCH = 19030013-End-->

**系统能力：** SystemCapability.Security.Cert

## ERR_CERT_KEYUSAGE_MISMATCH

```TypeScript
ERR_CERT_KEYUSAGE_MISMATCH = 19030014
```

证书密钥用途不匹配。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CertResult-ERR_CERT_KEYUSAGE_MISMATCH = 19030014--><!--Device-CertResult-ERR_CERT_KEYUSAGE_MISMATCH = 19030014-End-->

**系统能力：** SystemCapability.Security.Cert

## ERR_CRL_NOT_FOUND

```TypeScript
ERR_CRL_NOT_FOUND = 19030015
```

无法获取证书吊销列表。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CertResult-ERR_CRL_NOT_FOUND = 19030015--><!--Device-CertResult-ERR_CRL_NOT_FOUND = 19030015-End-->

**系统能力：** SystemCapability.Security.Cert

## ERR_CRL_NOT_YET_VALID

```TypeScript
ERR_CRL_NOT_YET_VALID = 19030016
```

证书吊销列表尚未生效。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CertResult-ERR_CRL_NOT_YET_VALID = 19030016--><!--Device-CertResult-ERR_CRL_NOT_YET_VALID = 19030016-End-->

**系统能力：** SystemCapability.Security.Cert

## ERR_CRL_HAS_EXPIRED

```TypeScript
ERR_CRL_HAS_EXPIRED = 19030017
```

证书吊销列表已过期。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CertResult-ERR_CRL_HAS_EXPIRED = 19030017--><!--Device-CertResult-ERR_CRL_HAS_EXPIRED = 19030017-End-->

**系统能力：** SystemCapability.Security.Cert

## ERR_CRL_SIGNATURE_FAILURE

```TypeScript
ERR_CRL_SIGNATURE_FAILURE = 19030018
```

证书吊销列表签名验证失败。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CertResult-ERR_CRL_SIGNATURE_FAILURE = 19030018--><!--Device-CertResult-ERR_CRL_SIGNATURE_FAILURE = 19030018-End-->

**系统能力：** SystemCapability.Security.Cert

## ERR_CRL_ISSUER_NOT_FOUND

```TypeScript
ERR_CRL_ISSUER_NOT_FOUND = 19030019
```

无法获取证书吊销列表颁发者。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CertResult-ERR_CRL_ISSUER_NOT_FOUND = 19030019--><!--Device-CertResult-ERR_CRL_ISSUER_NOT_FOUND = 19030019-End-->

**系统能力：** SystemCapability.Security.Cert

## ERR_OCSP_RESPONSE_NOT_FOUND

```TypeScript
ERR_OCSP_RESPONSE_NOT_FOUND = 19030020
```

无法获取在线证书状态协议（OCSP）响应。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CertResult-ERR_OCSP_RESPONSE_NOT_FOUND = 19030020--><!--Device-CertResult-ERR_OCSP_RESPONSE_NOT_FOUND = 19030020-End-->

**系统能力：** SystemCapability.Security.Cert

## ERR_OCSP_RESPONSE_INVALID

```TypeScript
ERR_OCSP_RESPONSE_INVALID = 19030021
```

OCSP响应无效。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CertResult-ERR_OCSP_RESPONSE_INVALID = 19030021--><!--Device-CertResult-ERR_OCSP_RESPONSE_INVALID = 19030021-End-->

**系统能力：** SystemCapability.Security.Cert

## ERR_OCSP_SIGNATURE_FAILURE

```TypeScript
ERR_OCSP_SIGNATURE_FAILURE = 19030022
```

OCSP签名验证失败。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CertResult-ERR_OCSP_SIGNATURE_FAILURE = 19030022--><!--Device-CertResult-ERR_OCSP_SIGNATURE_FAILURE = 19030022-End-->

**系统能力：** SystemCapability.Security.Cert

## ERR_OCSP_CERT_STATUS_UNKNOWN

```TypeScript
ERR_OCSP_CERT_STATUS_UNKNOWN = 19030023
```

OCSP证书状态未知。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CertResult-ERR_OCSP_CERT_STATUS_UNKNOWN = 19030023--><!--Device-CertResult-ERR_OCSP_CERT_STATUS_UNKNOWN = 19030023-End-->

**系统能力：** SystemCapability.Security.Cert

## ERR_NETWORK_TIMEOUT

```TypeScript
ERR_NETWORK_TIMEOUT = 19030024
```

网络连接超时。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CertResult-ERR_NETWORK_TIMEOUT = 19030024--><!--Device-CertResult-ERR_NETWORK_TIMEOUT = 19030024-End-->

**系统能力：** SystemCapability.Security.Cert

