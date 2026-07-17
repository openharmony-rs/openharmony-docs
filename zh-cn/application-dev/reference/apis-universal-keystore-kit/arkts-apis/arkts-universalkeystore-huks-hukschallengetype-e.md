# HuksChallengeType

表示密钥使用时生成challenge的类型。

**起始版本：** 9

<!--Device-huks-export enum HuksChallengeType--><!--Device-huks-export enum HuksChallengeType-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_CHALLENGE_TYPE_NORMAL

```TypeScript
HUKS_CHALLENGE_TYPE_NORMAL = 0
```

表示challenge为普通类型，默认32字节。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HuksChallengeType-HUKS_CHALLENGE_TYPE_NORMAL = 0--><!--Device-HuksChallengeType-HUKS_CHALLENGE_TYPE_NORMAL = 0-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_CHALLENGE_TYPE_CUSTOM

```TypeScript
HUKS_CHALLENGE_TYPE_CUSTOM = 1
```

表示challenge为用户自定义类型。支持使用多个密钥仅一次认证。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HuksChallengeType-HUKS_CHALLENGE_TYPE_CUSTOM = 1--><!--Device-HuksChallengeType-HUKS_CHALLENGE_TYPE_CUSTOM = 1-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_CHALLENGE_TYPE_NONE

```TypeScript
HUKS_CHALLENGE_TYPE_NONE = 2
```

表示免challenge类型。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HuksChallengeType-HUKS_CHALLENGE_TYPE_NONE = 2--><!--Device-HuksChallengeType-HUKS_CHALLENGE_TYPE_NONE = 2-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

