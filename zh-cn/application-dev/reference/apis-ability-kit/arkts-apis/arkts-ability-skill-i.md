# Skill

skill标签对象。

**起始版本：** 12

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## actions

```TypeScript
readonly actions: Array<string>
```

Skill接收的[Action集合](arkts-ability-action-depr-e.md)。

**类型：** Array<string>

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## domainVerify

```TypeScript
readonly domainVerify: boolean
```

Skill接收的DomainVerify值，仅在AbilityInfo中存在，表示是否开启域名校验，取值为true表示开启域名校验，取值为false表示未开启域名校验。

**类型：** boolean

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## entities

```TypeScript
readonly entities: Array<string>
```

Skill接收的[Entity集合](arkts-ability-entity-depr-e.md)。

**类型：** Array<string>

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## uris

```TypeScript
readonly uris: Array<SkillUri>
```

Want匹配的Uri集合。

**类型：** Array<SkillUri>

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

