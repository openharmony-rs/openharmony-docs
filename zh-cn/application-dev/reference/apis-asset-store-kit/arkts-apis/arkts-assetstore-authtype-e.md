# AuthType

枚举，关键资产支持的用户认证类型。

**起始版本：** 11

**系统能力：** SystemCapability.Security.Asset

## NONE

```TypeScript
NONE = 0x00
```

访问关键资产前无需用户认证。

**起始版本：** 11

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Asset

## ANY

```TypeScript
ANY = 0xFF
```

任意一种用户认证方式（PIN码、人脸、指纹等）通过后，均可访问关键资产。

**起始版本：** 11

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Asset

