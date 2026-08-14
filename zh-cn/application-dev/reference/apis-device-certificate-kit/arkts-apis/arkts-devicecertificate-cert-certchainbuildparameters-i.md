# CertChainBuildParameters

证书链创建参数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-cert-interface CertChainBuildParameters--><!--Device-cert-interface CertChainBuildParameters-End-->

**系统能力：** SystemCapability.Security.Cert

## certMatchParameters

```TypeScript
certMatchParameters: X509CertMatchParameters
```

指定过滤条件。

**类型：** [X509CertMatchParameters](arkts-devicecertificate-cert-x509certmatchparameters-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CertChainBuildParameters-certMatchParameters: X509CertMatchParameters--><!--Device-CertChainBuildParameters-certMatchParameters: X509CertMatchParameters-End-->

**系统能力：** SystemCapability.Security.Cert

## maxLength

```TypeScript
maxLength?: int
```

指定CA证书的最大数量。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CertChainBuildParameters-maxLength?: int--><!--Device-CertChainBuildParameters-maxLength?: int-End-->

**系统能力：** SystemCapability.Security.Cert

## validationParameters

```TypeScript
validationParameters: CertChainValidationParameters
```

指定验证条件。

**类型：** [CertChainValidationParameters](arkts-devicecertificate-cert-certchainvalidationparameters-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CertChainBuildParameters-validationParameters: CertChainValidationParameters--><!--Device-CertChainBuildParameters-validationParameters: CertChainValidationParameters-End-->

**系统能力：** SystemCapability.Security.Cert

