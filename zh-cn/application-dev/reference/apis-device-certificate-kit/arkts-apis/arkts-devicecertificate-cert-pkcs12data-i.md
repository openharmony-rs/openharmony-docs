# Pkcs12Data

表示返回P12文件的解析后的证书、私钥及其他证书合集。

**起始版本：** 18

**系统能力：** SystemCapability.Security.Cert

## cert

```TypeScript
cert?: X509Cert
```

表示P12文件解析后的证书。

**类型：** X509Cert

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

## otherCerts

```TypeScript
otherCerts?: Array<X509Cert>
```

表示P12文件解析后的其他证书合集。

**类型：** Array<X509Cert>

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

## privateKey

```TypeScript
privateKey?: string | Uint8Array
```

表示P12文件解析后的私钥。

**类型：** string | Uint8Array

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

