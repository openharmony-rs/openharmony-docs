# CmsEnvelopedDecryptionConfig

CMS解封装的配置。

**起始版本：** 22

**系统能力：** SystemCapability.Security.Cert

## cert

```TypeScript
cert?: X509Cert
```

公钥证书。默认为空。

**类型：** X509Cert

**起始版本：** 22

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Cert

## contentDataFormat

```TypeScript
contentDataFormat?: CmsContentDataFormat
```

内容数据的格式。

**类型：** CmsContentDataFormat

**默认值：** CmsContentDataFormat.BINARY

**起始版本：** 22

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Cert

## encryptedContentData

```TypeScript
encryptedContentData?: Uint8Array
```

加密的内容数据，如果CMS不包含指定数据。

**类型：** Uint8Array

**起始版本：** 22

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Cert

## keyInfo

```TypeScript
keyInfo?: PrivateKeyInfo
```

私钥参数。默认为空。

**类型：** PrivateKeyInfo

**起始版本：** 22

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Cert

