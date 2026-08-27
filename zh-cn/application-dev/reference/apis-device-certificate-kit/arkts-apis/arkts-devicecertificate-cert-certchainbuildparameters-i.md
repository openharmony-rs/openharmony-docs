# CertChainBuildParameters

证书链创建参数。

**起始版本：** 12

**系统能力：** SystemCapability.Security.Cert

## 导入模块

```TypeScript
```

## certMatchParameters

```TypeScript
certMatchParameters: X509CertMatchParameters
```

指定过滤条件。

**类型：** [X509CertMatchParameters](arkts-devicecertificate-cert-x509certmatchparameters-i.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

## maxLength

```TypeScript
maxLength?: number
```

指定CA证书的最大数量。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

## validationParameters

```TypeScript
validationParameters: CertChainValidationParameters
```

指定验证条件。

**类型：** [CertChainValidationParameters](arkts-devicecertificate-cert-certchainvalidationparameters-i.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert
