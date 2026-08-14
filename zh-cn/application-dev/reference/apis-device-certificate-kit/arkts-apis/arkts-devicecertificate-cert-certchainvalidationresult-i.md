# CertChainValidationResult

表示证书链校验的返回值。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-cert-interface CertChainValidationResult--><!--Device-cert-interface CertChainValidationResult-End-->

**系统能力：** SystemCapability.Security.Cert

## entityCert

```TypeScript
readonly entityCert: X509Cert
```

表示实体证书。

**类型：** [X509Cert](arkts-devicecertificate-cert-x509cert-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CertChainValidationResult-readonly entityCert: X509Cert--><!--Device-CertChainValidationResult-readonly entityCert: X509Cert-End-->

**系统能力：** SystemCapability.Security.Cert

## trustAnchor

```TypeScript
readonly trustAnchor: X509TrustAnchor
```

表示信任锚。

**类型：** [X509TrustAnchor](arkts-devicecertificate-cert-x509trustanchor-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CertChainValidationResult-readonly trustAnchor: X509TrustAnchor--><!--Device-CertChainValidationResult-readonly trustAnchor: X509TrustAnchor-End-->

**系统能力：** SystemCapability.Security.Cert

