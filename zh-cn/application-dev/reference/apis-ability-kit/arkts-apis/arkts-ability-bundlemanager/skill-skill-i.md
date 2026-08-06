# Skill

skill标签对象。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-unnamed-export interface Skill--><!--Device-unnamed-export interface Skill-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## actions

```TypeScript
readonly actions: Array<string>
```

Skill接收的[Action集合]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**类型：** Array&lt;string&gt;

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Skill-readonly actions: Array<string>--><!--Device-Skill-readonly actions: Array<string>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## domainVerify

```TypeScript
readonly domainVerify: boolean
```

Skill接收的DomainVerify值，仅在AbilityInfo中存在，表示是否开启域名校验，取值为true表示开启域名校验，取值为false表示未开启域名校验。

**类型：** boolean

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Skill-readonly domainVerify: boolean--><!--Device-Skill-readonly domainVerify: boolean-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## entities

```TypeScript
readonly entities: Array<string>
```

Skill接收的[Entity集合]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**类型：** Array&lt;string&gt;

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Skill-readonly entities: Array<string>--><!--Device-Skill-readonly entities: Array<string>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## uris

```TypeScript
readonly uris: Array<SkillUri>
```

Want匹配的Uri集合。

**类型：** Array&lt;SkillUri&gt;

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Skill-readonly uris: Array<SkillUri>--><!--Device-Skill-readonly uris: Array<SkillUri>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

