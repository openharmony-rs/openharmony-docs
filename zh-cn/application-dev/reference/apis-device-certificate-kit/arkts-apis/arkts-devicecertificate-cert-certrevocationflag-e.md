# CertRevocationFlag

表示证书吊销检查标志的枚举。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-cert-enum CertRevocationFlag--><!--Device-cert-enum CertRevocationFlag-End-->

**系统能力：** SystemCapability.Security.Cert

## CERT_REVOCATION_PREFER_OCSP

```TypeScript
CERT_REVOCATION_PREFER_OCSP = 0
```

优先OCSP检查。仅当CERT\_REVOCATION\_CRL\_CHECK与CERT\_REVOCATION\_OCSP\_CHECK同时设置时，该标志生效。 - 设置后先执行OCSP检查，未找到响应或超时时回退CRL； - 不设置则先执行CRL检查，未找到CRL或超时时回退OCSP。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CertRevocationFlag-CERT_REVOCATION_PREFER_OCSP = 0--><!--Device-CertRevocationFlag-CERT_REVOCATION_PREFER_OCSP = 0-End-->

**系统能力：** SystemCapability.Security.Cert

## CERT_REVOCATION_CRL_CHECK

```TypeScript
CERT_REVOCATION_CRL_CHECK = 1
```

启用CRL检查。使用证书吊销列表检查证书状态。 \_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_首先使用[X509CertRevokedParams]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_的crls参数，未匹配到CRL且 [X509CertRevokedParams]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_的allowDownloadCrl参数设置为true时则尝试使用证书的CDP扩展 下载CRL。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CertRevocationFlag-CERT_REVOCATION_CRL_CHECK = 1--><!--Device-CertRevocationFlag-CERT_REVOCATION_CRL_CHECK = 1-End-->

**系统能力：** SystemCapability.Security.Cert

## CERT_REVOCATION_OCSP_CHECK

```TypeScript
CERT_REVOCATION_OCSP_CHECK = 2
```

启用OCSP检查。使用在线证书状态协议检查证书状态。 \_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_首先使用[X509CertRevokedParams]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_的ocspResponses参数，未匹配到响应且 [X509CertRevokedParams]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_的allowOcspCheckOnline参数设置为true则尝试从证书AIA扩展 获取OCSP URL并发送请求获取响应。 > **说明：** > > - 始终使用系统当前时间校验ocsp响应的有效期，并允许前后5分钟的时间容差。 > - 始终使用系统当前时间校验ocsp签名者证书链的有效期。 > - 允许ocsp响应缺少nonce和nextUpdate。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CertRevocationFlag-CERT_REVOCATION_OCSP_CHECK = 2--><!--Device-CertRevocationFlag-CERT_REVOCATION_OCSP_CHECK = 2-End-->

**系统能力：** SystemCapability.Security.Cert

## CERT_REVOCATION_CHECK_ALL_CERT

```TypeScript
CERT_REVOCATION_CHECK_ALL_CERT = 3
```

检查所有证书的吊销状态。 - 设置后对证书链中所有证书执行吊销检查（跳过自签名证书）； - 不设置则仅检查终端实体证书（证书链第一个证书）。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CertRevocationFlag-CERT_REVOCATION_CHECK_ALL_CERT = 3--><!--Device-CertRevocationFlag-CERT_REVOCATION_CHECK_ALL_CERT = 3-End-->

**系统能力：** SystemCapability.Security.Cert

