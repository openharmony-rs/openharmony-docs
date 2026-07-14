# SyncType

枚举，关键资产支持的同步类型。

**起始版本：** 11

**系统能力：** SystemCapability.Security.Asset

## NEVER

```TypeScript
NEVER = 0
```

不允许同步关键资产。

**起始版本：** 11

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Asset

## THIS_DEVICE

```TypeScript
THIS_DEVICE = 1 << 0
```

只在本设备进行同步，如仅在本设备还原的备份场景。

**说明：** 本字段是能力预埋，当前不支持。

**起始版本：** 11

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Asset

## TRUSTED_DEVICE

```TypeScript
TRUSTED_DEVICE = 1 << 1
```

只在可信设备间进行同步，如克隆场景。

**起始版本：** 11

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Asset

## TRUSTED_ACCOUNT

```TypeScript
TRUSTED_ACCOUNT = 1 << 2
```

只在登录可信账号的设备间进行同步，如云同步场景。

**说明：** 本字段是能力预埋，当前不支持。

**起始版本：** 12

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Asset

