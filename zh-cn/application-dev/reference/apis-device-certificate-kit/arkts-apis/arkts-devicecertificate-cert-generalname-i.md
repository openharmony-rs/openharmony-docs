# GeneralName

表示X.509 GeneralName，定义在RFC 5280中，可出现在Subject Alternative Name等扩展中。

**起始版本：** 12

**系统能力：** SystemCapability.Security.Cert

## 导入模块

```TypeScript
```

## name

```TypeScript
name?: Uint8Array
```

指定GeneralName的DER编码值。

**类型：** Uint8Array

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

## type

```TypeScript
type: GeneralNameType
```

GeneralName类型。

**类型：** [GeneralNameType](arkts-devicecertificate-cert-generalnametype-e.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert
