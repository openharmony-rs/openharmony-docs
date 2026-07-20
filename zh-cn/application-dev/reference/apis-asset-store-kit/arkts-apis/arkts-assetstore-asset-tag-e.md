# Tag

枚举，关键资产支持的属性名称类型，用作[AssetMap](arkts-assetstore-asset-assetmap-t.md)的键。

> **说明：**  
>  
> 以下为Tag类型的全量枚举值，每个接口可传的Tag枚举及对应的Value取值范围不同，详见  
> [各个场景的开发指导](docroot://security/AssetStoreKit/asset-store-kit-overview.md)。

**起始版本：** 11

<!--Device-asset-enum Tag--><!--Device-asset-enum Tag-End-->

**系统能力：** SystemCapability.Security.Asset

## SECRET

```TypeScript
SECRET = TagType.BYTES | 0x01
```

关键资产明文。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-Tag-SECRET = TagType.BYTES | 0x01--><!--Device-Tag-SECRET = TagType.BYTES | 0x01-End-->

**系统能力：** SystemCapability.Security.Asset

## ALIAS

```TypeScript
ALIAS = TagType.BYTES | 0x02
```

关键资产别名，每条关键资产的唯一索引。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-Tag-ALIAS = TagType.BYTES | 0x02--><!--Device-Tag-ALIAS = TagType.BYTES | 0x02-End-->

**系统能力：** SystemCapability.Security.Asset

## ACCESSIBILITY

```TypeScript
ACCESSIBILITY = TagType.NUMBER | 0x03
```

基于锁屏状态的访问控制。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-Tag-ACCESSIBILITY = TagType.NUMBER | 0x03--><!--Device-Tag-ACCESSIBILITY = TagType.NUMBER | 0x03-End-->

**系统能力：** SystemCapability.Security.Asset

## REQUIRE_PASSWORD_SET

```TypeScript
REQUIRE_PASSWORD_SET = TagType.BOOL | 0x04
```

是否仅在设置了锁屏密码的情况下，可访问关键资产。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-Tag-REQUIRE_PASSWORD_SET = TagType.BOOL | 0x04--><!--Device-Tag-REQUIRE_PASSWORD_SET = TagType.BOOL | 0x04-End-->

**系统能力：** SystemCapability.Security.Asset

## AUTH_TYPE

```TypeScript
AUTH_TYPE = TagType.NUMBER | 0x05
```

访问关键资产所需的用户认证类型。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-Tag-AUTH_TYPE = TagType.NUMBER | 0x05--><!--Device-Tag-AUTH_TYPE = TagType.NUMBER | 0x05-End-->

**系统能力：** SystemCapability.Security.Asset

## AUTH_VALIDITY_PERIOD

```TypeScript
AUTH_VALIDITY_PERIOD = TagType.NUMBER | 0x06
```

用户认证的有效期。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-Tag-AUTH_VALIDITY_PERIOD = TagType.NUMBER | 0x06--><!--Device-Tag-AUTH_VALIDITY_PERIOD = TagType.NUMBER | 0x06-End-->

**系统能力：** SystemCapability.Security.Asset

## AUTH_CHALLENGE

```TypeScript
AUTH_CHALLENGE = TagType.BYTES | 0x07
```

用户认证的挑战值。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-Tag-AUTH_CHALLENGE = TagType.BYTES | 0x07--><!--Device-Tag-AUTH_CHALLENGE = TagType.BYTES | 0x07-End-->

**系统能力：** SystemCapability.Security.Asset

## AUTH_TOKEN

```TypeScript
AUTH_TOKEN = TagType.BYTES | 0x08
```

用户认证通过的授权令牌。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-Tag-AUTH_TOKEN = TagType.BYTES | 0x08--><!--Device-Tag-AUTH_TOKEN = TagType.BYTES | 0x08-End-->

**系统能力：** SystemCapability.Security.Asset

## SYNC_TYPE

```TypeScript
SYNC_TYPE = TagType.NUMBER | 0x10
```

关键资产支持的同步类型。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-Tag-SYNC_TYPE = TagType.NUMBER | 0x10--><!--Device-Tag-SYNC_TYPE = TagType.NUMBER | 0x10-End-->

**系统能力：** SystemCapability.Security.Asset

## IS_PERSISTENT

```TypeScript
IS_PERSISTENT = TagType.BOOL | 0x11
```

在应用卸载时是否保留关键资产。

**起始版本：** 11

<!--Device-Tag-IS_PERSISTENT = TagType.BOOL | 0x11--><!--Device-Tag-IS_PERSISTENT = TagType.BOOL | 0x11-End-->

**系统能力：** SystemCapability.Security.Asset

## DATA_LABEL_CRITICAL_1

```TypeScript
DATA_LABEL_CRITICAL_1 = TagType.BYTES | 0x20
```

关键资产附属信息，内容由业务自定义且**有完整性保护**。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-Tag-DATA_LABEL_CRITICAL_1 = TagType.BYTES | 0x20--><!--Device-Tag-DATA_LABEL_CRITICAL_1 = TagType.BYTES | 0x20-End-->

**系统能力：** SystemCapability.Security.Asset

## DATA_LABEL_CRITICAL_2

```TypeScript
DATA_LABEL_CRITICAL_2 = TagType.BYTES | 0x21
```

关键资产附属信息，内容由业务自定义且**有完整性保护**。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-Tag-DATA_LABEL_CRITICAL_2 = TagType.BYTES | 0x21--><!--Device-Tag-DATA_LABEL_CRITICAL_2 = TagType.BYTES | 0x21-End-->

**系统能力：** SystemCapability.Security.Asset

## DATA_LABEL_CRITICAL_3

```TypeScript
DATA_LABEL_CRITICAL_3 = TagType.BYTES | 0x22
```

关键资产附属信息，内容由业务自定义且**有完整性保护**。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-Tag-DATA_LABEL_CRITICAL_3 = TagType.BYTES | 0x22--><!--Device-Tag-DATA_LABEL_CRITICAL_3 = TagType.BYTES | 0x22-End-->

**系统能力：** SystemCapability.Security.Asset

## DATA_LABEL_CRITICAL_4

```TypeScript
DATA_LABEL_CRITICAL_4 = TagType.BYTES | 0x23
```

关键资产附属信息，内容由业务自定义且**有完整性保护**。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-Tag-DATA_LABEL_CRITICAL_4 = TagType.BYTES | 0x23--><!--Device-Tag-DATA_LABEL_CRITICAL_4 = TagType.BYTES | 0x23-End-->

**系统能力：** SystemCapability.Security.Asset

## DATA_LABEL_NORMAL_1

```TypeScript
DATA_LABEL_NORMAL_1 = TagType.BYTES | 0x30
```

关键资产附属信息，内容由业务自定义且**无完整性保护**。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-Tag-DATA_LABEL_NORMAL_1 = TagType.BYTES | 0x30--><!--Device-Tag-DATA_LABEL_NORMAL_1 = TagType.BYTES | 0x30-End-->

**系统能力：** SystemCapability.Security.Asset

## DATA_LABEL_NORMAL_2

```TypeScript
DATA_LABEL_NORMAL_2 = TagType.BYTES | 0x31
```

关键资产附属信息，内容由业务自定义且**无完整性保护**。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-Tag-DATA_LABEL_NORMAL_2 = TagType.BYTES | 0x31--><!--Device-Tag-DATA_LABEL_NORMAL_2 = TagType.BYTES | 0x31-End-->

**系统能力：** SystemCapability.Security.Asset

## DATA_LABEL_NORMAL_3

```TypeScript
DATA_LABEL_NORMAL_3 = TagType.BYTES | 0x32
```

关键资产附属信息，内容由业务自定义且**无完整性保护**。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-Tag-DATA_LABEL_NORMAL_3 = TagType.BYTES | 0x32--><!--Device-Tag-DATA_LABEL_NORMAL_3 = TagType.BYTES | 0x32-End-->

**系统能力：** SystemCapability.Security.Asset

## DATA_LABEL_NORMAL_4

```TypeScript
DATA_LABEL_NORMAL_4 = TagType.BYTES | 0x33
```

关键资产附属信息，内容由业务自定义且**无完整性保护**。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-Tag-DATA_LABEL_NORMAL_4 = TagType.BYTES | 0x33--><!--Device-Tag-DATA_LABEL_NORMAL_4 = TagType.BYTES | 0x33-End-->

**系统能力：** SystemCapability.Security.Asset

## DATA_LABEL_NORMAL_LOCAL_1

```TypeScript
DATA_LABEL_NORMAL_LOCAL_1 = TagType.BYTES | 0x34
```

关键资产附属的本地信息，内容由业务自定义且**无完整性保护**，该项信息不会进行同步。

**起始版本：** 12

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-Tag-DATA_LABEL_NORMAL_LOCAL_1 = TagType.BYTES | 0x34--><!--Device-Tag-DATA_LABEL_NORMAL_LOCAL_1 = TagType.BYTES | 0x34-End-->

**系统能力：** SystemCapability.Security.Asset

## DATA_LABEL_NORMAL_LOCAL_2

```TypeScript
DATA_LABEL_NORMAL_LOCAL_2 = TagType.BYTES | 0x35
```

关键资产附属的本地信息，内容由业务自定义且**无完整性保护**，该项信息不会进行同步。

**起始版本：** 12

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-Tag-DATA_LABEL_NORMAL_LOCAL_2 = TagType.BYTES | 0x35--><!--Device-Tag-DATA_LABEL_NORMAL_LOCAL_2 = TagType.BYTES | 0x35-End-->

**系统能力：** SystemCapability.Security.Asset

## DATA_LABEL_NORMAL_LOCAL_3

```TypeScript
DATA_LABEL_NORMAL_LOCAL_3 = TagType.BYTES | 0x36
```

关键资产附属的本地信息，内容由业务自定义且**无完整性保护**，该项信息不会进行同步。

**起始版本：** 12

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-Tag-DATA_LABEL_NORMAL_LOCAL_3 = TagType.BYTES | 0x36--><!--Device-Tag-DATA_LABEL_NORMAL_LOCAL_3 = TagType.BYTES | 0x36-End-->

**系统能力：** SystemCapability.Security.Asset

## DATA_LABEL_NORMAL_LOCAL_4

```TypeScript
DATA_LABEL_NORMAL_LOCAL_4 = TagType.BYTES | 0x37
```

关键资产附属的本地信息，内容由业务自定义且**无完整性保护**，该项信息不会进行同步。

**起始版本：** 12

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-Tag-DATA_LABEL_NORMAL_LOCAL_4 = TagType.BYTES | 0x37--><!--Device-Tag-DATA_LABEL_NORMAL_LOCAL_4 = TagType.BYTES | 0x37-End-->

**系统能力：** SystemCapability.Security.Asset

## RETURN_TYPE

```TypeScript
RETURN_TYPE = TagType.NUMBER | 0x40
```

关键资产查询返回的结果类型。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-Tag-RETURN_TYPE = TagType.NUMBER | 0x40--><!--Device-Tag-RETURN_TYPE = TagType.NUMBER | 0x40-End-->

**系统能力：** SystemCapability.Security.Asset

## RETURN_LIMIT

```TypeScript
RETURN_LIMIT = TagType.NUMBER | 0x41
```

关键资产查询返回的结果的最大数量。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-Tag-RETURN_LIMIT = TagType.NUMBER | 0x41--><!--Device-Tag-RETURN_LIMIT = TagType.NUMBER | 0x41-End-->

**系统能力：** SystemCapability.Security.Asset

## RETURN_OFFSET

```TypeScript
RETURN_OFFSET = TagType.NUMBER | 0x42
```

关键资产查询返回的结果偏移量。

**说明：** 用于分批查询场景，指定从第几个开始返回。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-Tag-RETURN_OFFSET = TagType.NUMBER | 0x42--><!--Device-Tag-RETURN_OFFSET = TagType.NUMBER | 0x42-End-->

**系统能力：** SystemCapability.Security.Asset

## RETURN_ORDERED_BY

```TypeScript
RETURN_ORDERED_BY = TagType.NUMBER | 0x43
```

关键资产查询返回的结果排序依据，仅支持按照附属信息排序。

**说明：** 默认按照关键资产新增的顺序返回。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-Tag-RETURN_ORDERED_BY = TagType.NUMBER | 0x43--><!--Device-Tag-RETURN_ORDERED_BY = TagType.NUMBER | 0x43-End-->

**系统能力：** SystemCapability.Security.Asset

## CONFLICT_RESOLUTION

```TypeScript
CONFLICT_RESOLUTION = TagType.NUMBER | 0x44
```

新增关键资产时的冲突（如：别名相同）处理策略。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-Tag-CONFLICT_RESOLUTION = TagType.NUMBER | 0x44--><!--Device-Tag-CONFLICT_RESOLUTION = TagType.NUMBER | 0x44-End-->

**系统能力：** SystemCapability.Security.Asset

## UPDATE_TIME

```TypeScript
UPDATE_TIME = TagType.BYTES | 0x45
```

数据的更新时间（时间戳形式）。

**起始版本：** 12

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-Tag-UPDATE_TIME = TagType.BYTES | 0x45--><!--Device-Tag-UPDATE_TIME = TagType.BYTES | 0x45-End-->

**系统能力：** SystemCapability.Security.Asset

## OPERATION_TYPE

```TypeScript
OPERATION_TYPE = TagType.NUMBER | 0x46
```

附加的操作类型。

**起始版本：** 12

<!--Device-Tag-OPERATION_TYPE = TagType.NUMBER | 0x46--><!--Device-Tag-OPERATION_TYPE = TagType.NUMBER | 0x46-End-->

**系统能力：** SystemCapability.Security.Asset

## REQUIRE_ATTR_ENCRYPTED

```TypeScript
REQUIRE_ATTR_ENCRYPTED = TagType.BOOL | 0x47
```

是否加密业务自定义附属信息。

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-Tag-REQUIRE_ATTR_ENCRYPTED = TagType.BOOL | 0x47--><!--Device-Tag-REQUIRE_ATTR_ENCRYPTED = TagType.BOOL | 0x47-End-->

**系统能力：** SystemCapability.Security.Asset

## GROUP_ID

```TypeScript
GROUP_ID = TagType.BYTES | 0x48
```

关键资产所属群组。

**起始版本：** 18

<!--Device-Tag-GROUP_ID = TagType.BYTES | 0x48--><!--Device-Tag-GROUP_ID = TagType.BYTES | 0x48-End-->

**系统能力：** SystemCapability.Security.Asset

## WRAP_TYPE

```TypeScript
WRAP_TYPE = TagType.NUMBER | 0x49
```

关键资产支持的加密导入导出类型。

**起始版本：** 18

<!--Device-Tag-WRAP_TYPE = TagType.NUMBER | 0x49--><!--Device-Tag-WRAP_TYPE = TagType.NUMBER | 0x49-End-->

**系统能力：** SystemCapability.Security.Asset

