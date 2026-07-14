# OsAccountInfo

表示系统账号信息。

**起始版本：** 7

**系统能力：** SystemCapability.Account.OsAccount

## constraints

```TypeScript
constraints: Array<string>
```

系统账号[约束](../../../../reference/apis-basic-services-kit/js-apis-osAccount.md#系统账号约束列表)，默认为空。

**类型：** Array<string>

**起始版本：** 7

**系统能力：** SystemCapability.Account.OsAccount

## createTime

```TypeScript
createTime: number
```

系统账号创建时间，以Unix时间戳格式表示，单位为s。

**类型：** number

**起始版本：** 8

**系统能力：** SystemCapability.Account.OsAccount

## distributedInfo

```TypeScript
distributedInfo: distributedAccount.DistributedInfo
```

分布式账号信息，默认为空。

**类型：** distributedAccount.DistributedInfo

**起始版本：** 7

**系统能力：** SystemCapability.Account.OsAccount

## domainInfo

```TypeScript
domainInfo: DomainAccountInfo
```

域账号信息，默认为空。

**类型：** DomainAccountInfo

**起始版本：** 8

**系统能力：** SystemCapability.Account.OsAccount

## isActivated

```TypeScript
isActivated: boolean
```

系统账号是否激活。true表示指定账号已激活；false表示指定账号未激活。

**类型：** boolean

**起始版本：** 11

**系统能力：** SystemCapability.Account.OsAccount

## isActived

```TypeScript
isActived: boolean
```

系统账号激活状态。true表示指定账号处于激活状态；false表示指定账号处于未激活状态。

**说明：**从API version 7开始支持，从API version 11开始废弃，建议使用isActivated。

**类型：** boolean

**起始版本：** 8

**废弃版本：** 11

**替代接口：** [isActivated](arkts-basicservices-osaccountinfo-i.md#isactivated)

**系统能力：** SystemCapability.Account.OsAccount

## isCreateCompleted

```TypeScript
isCreateCompleted: boolean
```

系统账号创建是否完整。true表示指定账号已创建完整；false表示指定账号未创建完整。

**类型：** boolean

**起始版本：** 8

**系统能力：** SystemCapability.Account.OsAccount

## isUnlocked

```TypeScript
isUnlocked: boolean
```

账号是否已解锁（EL2级别目录是否解密）。true表示指定账号已解锁；false表示指定账号未解锁。

**类型：** boolean

**起始版本：** 11

**系统能力：** SystemCapability.Account.OsAccount

## isVerified

```TypeScript
isVerified: boolean
```

账号是否验证。true表示指定账号已验证；false表示指定账号未验证。

**说明：**从API version 7开始支持，从API version 11开始废弃，建议使用isUnlocked。

**类型：** boolean

**起始版本：** 8

**废弃版本：** 11

**替代接口：** [isUnlocked](arkts-basicservices-osaccountinfo-i.md#isunlocked)

**系统能力：** SystemCapability.Account.OsAccount

## lastLoginTime

```TypeScript
lastLoginTime: number
```

系统账号最后一次登录时间，以Unix时间戳格式表示，单位为s。

**类型：** number

**起始版本：** 8

**系统能力：** SystemCapability.Account.OsAccount

## localId

```TypeScript
localId: number
```

系统账号ID。

**类型：** number

**起始版本：** 7

**系统能力：** SystemCapability.Account.OsAccount

## localName

```TypeScript
localName: string
```

系统账号名称。

**类型：** string

**起始版本：** 7

**系统能力：** SystemCapability.Account.OsAccount

## photo

```TypeScript
photo: string
```

系统账号头像，默认为空。

**类型：** string

**起始版本：** 8

**系统能力：** SystemCapability.Account.OsAccount

## serialNumber

```TypeScript
serialNumber: number
```

系统账号SN码。

**类型：** number

**起始版本：** 8

**系统能力：** SystemCapability.Account.OsAccount

## type

```TypeScript
type: OsAccountType
```

系统账号类型。

**类型：** OsAccountType

**起始版本：** 7

**系统能力：** SystemCapability.Account.OsAccount

