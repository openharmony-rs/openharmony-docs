# Pkcs12Data

P12（PKCS #12）数据，包含私钥、证书和其他证书。

**起始版本：** 18

**系统能力：** SystemCapability.Security.Cert

## cert

```TypeScript
cert?: X509Cert
```

和私钥匹配的证书。

**类型：** X509Cert

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Cert

## otherCerts

```TypeScript
otherCerts?: Array<X509Cert>
```

其他证书。

**类型：** Array<X509Cert>

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Cert

## privateKey

```TypeScript
privateKey?: string | Uint8Array
```

私钥。**string**对应PEM格式，**Uint8Array**对应DER格式。

**类型：** string | Uint8Array

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Cert

