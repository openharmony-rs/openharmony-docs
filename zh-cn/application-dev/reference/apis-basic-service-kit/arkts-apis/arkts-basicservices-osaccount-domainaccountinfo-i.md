# DomainAccountInfo

表示域账号信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-osAccount-interface DomainAccountInfo--><!--Device-osAccount-interface DomainAccountInfo-End-->

**系统能力：** SystemCapability.Account.OsAccount

## accountName

```TypeScript
accountName: string
```

域账号名。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-DomainAccountInfo-accountName: string--><!--Device-DomainAccountInfo-accountName: string-End-->

**系统能力：** SystemCapability.Account.OsAccount

## additionalInfo

```TypeScript
additionalInfo?: Record<string, RecordData>
```

域账号附加信息。 此接口仅可在Stage模型下使用。

**类型：** Record&lt;string, [RecordData](arkts-basicservices-recorddata-t.md)&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DomainAccountInfo-additionalInfo?: Record<string, RecordData>--><!--Device-DomainAccountInfo-additionalInfo?: Record<string, RecordData>-End-->

**系统能力：** SystemCapability.Account.OsAccount

## domain

```TypeScript
domain: string
```

域名。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-DomainAccountInfo-domain: string--><!--Device-DomainAccountInfo-domain: string-End-->

**系统能力：** SystemCapability.Account.OsAccount

## serverConfigId

```TypeScript
serverConfigId?: string
```

域账号配置ID，默认为空字符串。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-DomainAccountInfo-serverConfigId?: string--><!--Device-DomainAccountInfo-serverConfigId?: string-End-->

**系统能力：** SystemCapability.Account.OsAccount

