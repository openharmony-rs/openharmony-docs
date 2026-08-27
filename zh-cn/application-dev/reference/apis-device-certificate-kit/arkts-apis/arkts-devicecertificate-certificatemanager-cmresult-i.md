# CMResult

表示接口的返回结果。

**起始版本：** 11

**系统能力：** SystemCapability.Security.CertificateManager

## 导入模块

```TypeScript
```

## appUidList

```TypeScript
appUidList?: Array<string>
```

表示授权应用列表。

**类型：** Array&lt;string&gt;

**起始版本：** 11

**系统能力：** SystemCapability.Security.CertificateManager

## certInfo

```TypeScript
certInfo?: CertInfo
```

表示证书详情。

**类型：** [CertInfo](arkts-devicecertificate-certificatemanager-certinfo-i.md)

**起始版本：** 11

**系统能力：** SystemCapability.Security.CertificateManager

## certList

```TypeScript
certList?: Array<CertAbstract>
```

表示证书简要信息的列表。

**类型：** Array&lt;[CertAbstract](arkts-devicecertificate-certificatemanager-certabstract-i.md)&gt;

**起始版本：** 11

**系统能力：** SystemCapability.Security.CertificateManager

## credential

```TypeScript
credential?: Credential
```

表示凭据详情。

**类型：** Credential

**起始版本：** 11

**系统能力：** SystemCapability.Security.CertificateManager

## credentialDetailList

```TypeScript
credentialDetailList?: Array<Credential>
```

表示凭据详细信息。

**类型：** Array&lt;Credential&gt;

**起始版本：** 22

**系统能力：** SystemCapability.Security.CertificateManager

## credentialList

```TypeScript
credentialList?: Array<CredentialAbstract>
```

表示凭据简要信息的列表。

**类型：** Array&lt;[CredentialAbstract](arkts-devicecertificate-certificatemanager-credentialabstract-i.md)&gt;

**起始版本：** 11

**系统能力：** SystemCapability.Security.CertificateManager

## outData

```TypeScript
outData?: Uint8Array
```

表示签名结果。

**类型：** Uint8Array

**起始版本：** 11

**系统能力：** SystemCapability.Security.CertificateManager

## uri

```TypeScript
uri?: string
```

表示证书或凭据的唯一标识符，最大长度为256字节。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Security.CertificateManager

## uriList

```TypeScript
uriList?: Array<string>
```

表示证书URI列表。 26.0.0

**类型：** Array&lt;string&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.CertificateManager
