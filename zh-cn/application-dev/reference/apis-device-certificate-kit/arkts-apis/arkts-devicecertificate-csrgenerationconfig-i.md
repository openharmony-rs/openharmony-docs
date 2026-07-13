# CsrGenerationConfig

用于生成CSR的配置参数，包含主体名称、扩展、摘要算法、输出格式等。

> **说明：**
>
> - subject是X509定义的Name类型的对象。
>
> - mdName是摘要算法名，当前支持SHA1、SHA256、SHA384、SHA512。
>
> - attributes是可选参数，指定**PKCS #9**中规定的扩展类型跟扩展值生成CSR。例如challengePassword。
>
> - outFormat指定输出CSR的格式，若不指定默认为PEM格式。

**起始版本：** 18

**系统能力：** SystemCapability.Security.Cert

## attributes

```TypeScript
attributes?: Array<CsrAttribute>
```

属性的集合。

**类型：** Array<CsrAttribute>

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Cert

## mdName

```TypeScript
mdName: string
```

摘要算法名。

**类型：** string

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Cert

## outFormat

```TypeScript
outFormat?: EncodingBaseFormat
```

输出类型。

**类型：** EncodingBaseFormat

**默认值：** EncodingBaseFormat.PEM

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Cert

## subject

```TypeScript
subject: X500DistinguishedName
```

主体名称。

**类型：** X500DistinguishedName

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Cert

