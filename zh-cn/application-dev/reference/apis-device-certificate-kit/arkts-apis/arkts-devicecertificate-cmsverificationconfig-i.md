# CmsVerificationConfig

CMS验签的配置。

**起始版本：** 22

**系统能力：** SystemCapability.Security.Cert

## contentData

```TypeScript
contentData?: Uint8Array
```

内容数据，如果是detached模式，则需要指定明文数据。attached模式可以不传。

**类型：** Uint8Array

**起始版本：** 22

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Cert

## contentDataFormat

```TypeScript
contentDataFormat?: CmsContentDataFormat
```

内容数据的格式。默认为CmsContentDataFormat.BINARY。

**类型：** CmsContentDataFormat

**默认值：** CmsContentDataFormat.BINARY

**起始版本：** 22

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Cert

## signerCerts

```TypeScript
signerCerts?: Array<X509Cert>
```

签名者证书。

**类型：** Array<X509Cert>

**起始版本：** 22

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Cert

## trustCerts

```TypeScript
trustCerts: Array<X509Cert>
```

信任证书。

> **说明：**
>
> 需要配置所有签名者的信任证书。

**类型：** Array<X509Cert>

**起始版本：** 22

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Cert

