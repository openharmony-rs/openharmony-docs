# CertInfo

表示证书详细信息。

**起始版本：** 11

**系统能力：** SystemCapability.Security.CertificateManager

## cert

```TypeScript
cert: Uint8Array
```

表示证书二进制数据，最大长度为8196字节。

**类型：** Uint8Array

**起始版本：** 11

**系统能力：** SystemCapability.Security.CertificateManager

## certAlias

```TypeScript
certAlias: string
```

表示证书的别名，最大长度为128字节。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Security.CertificateManager

## fingerprintSha256

```TypeScript
fingerprintSha256: string
```

表示证书的指纹值，最大长度为128字节。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Security.CertificateManager

## issuerName

```TypeScript
issuerName: string
```

表示证书的颁发者名称，最大长度为256字节。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Security.CertificateManager

## notAfter

```TypeScript
notAfter: string
```

表示证书有效期截止日期，最大长度为32字节。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Security.CertificateManager

## notBefore

```TypeScript
notBefore: string
```

表示证书有效期起始日期，最大长度为32字节。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Security.CertificateManager

## serial

```TypeScript
serial: string
```

表示证书的序列号，最大长度为64字节。格式为16进制字符串，例如：62C2CB4DE8405E96。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Security.CertificateManager

## state

```TypeScript
state: boolean
```

表示证书的状态，true为启用状态、false为禁用状态。

**类型：** boolean

**起始版本：** 11

**系统能力：** SystemCapability.Security.CertificateManager

## subjectName

```TypeScript
subjectName: string
```

表示证书的使用者名称，最大长度为1024字节。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Security.CertificateManager

## uri

```TypeScript
uri: string
```

表示证书的唯一标识符，最大长度为256字节。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Security.CertificateManager

