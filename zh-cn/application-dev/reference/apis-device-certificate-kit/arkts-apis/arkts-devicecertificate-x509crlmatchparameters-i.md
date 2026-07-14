# X509CRLMatchParameters

用于匹配证书吊销列表的过滤参数。如果参数中任一项都未指定，则匹配所有证书吊销列表。

**起始版本：** 11

**系统能力：** SystemCapability.Security.Cert

## issuer

```TypeScript
issuer?: Array<Uint8Array>
```

指定CRL颁发者，为DER编码格式。

**类型：** Array<Uint8Array>

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Cert

## maxCRL

```TypeScript
maxCRL?: bigint
```

指定CRL编号（CRL number）的最大值。

**类型：** bigint

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Cert

## minCRL

```TypeScript
minCRL?: bigint
```

指定CRL编号（CRL number）的最小值。

**类型：** bigint

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Cert

## updateDateTime

```TypeScript
updateDateTime?: string
```

指定CRL更新时间。

**类型：** string

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Cert

## x509Cert

```TypeScript
x509Cert?: X509Cert
```

指定具体的证书对象。

**类型：** X509Cert

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Cert

