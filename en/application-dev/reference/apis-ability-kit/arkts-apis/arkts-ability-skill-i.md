# Skill

```TypeScript
export interface Skill
```

The module defines a skill object. Such an object can be obtained through [bundleManager.getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md), with at least **GET_BUNDLE_INFO_WITH_HAP_MODULE**, **GET_BUNDLE_INFO_WITH_ABILITY**, and **GET_BUNDLE_INFO_WITH_SKILL** passed in to **bundleFlags**. (The skill information is contained in [BundleInfo](arkts-ability-bundleinfo-i.md) -> [HapModuleInfo](arkts-ability-hapmoduleinfo-i.md) -> [AbilityInfo](arkts-ability-abilityinfo-i.md) or [ExtensionAbilityInfo](arkts-ability-extensionabilityinfo-i.md).)

**Since:** 12

<!--Device-unnamed-export interface Skill--><!--Device-unnamed-export interface Skill-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## actions

```TypeScript
readonly actions: Array<string>
```

[Actions](../../../reference/apis-ability-kit/js-apis-ability-wantConstant.md#action) received by the skill.

**Type:** Array&lt;string&gt;

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-Skill-readonly actions: Array<string>--><!--Device-Skill-readonly actions: Array<string>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## domainVerify

```TypeScript
readonly domainVerify: boolean
```

Whether to enable domain verification. This attribute exists only in AbilityInfo. The value true indicates that domain verification is enabled and domain verification is required; the value false indicates that domain verification is not enabled.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-Skill-readonly domainVerify: boolean--><!--Device-Skill-readonly domainVerify: boolean-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## entities

```TypeScript
readonly entities: Array<string>
```

[Entities](../../../reference/apis-ability-kit/js-apis-ability-wantConstant.md#entity) received by the skill.

**Type:** Array&lt;string&gt;

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-Skill-readonly entities: Array<string>--><!--Device-Skill-readonly entities: Array<string>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## uris

```TypeScript
readonly uris: Array<SkillUri>
```

Collection of URIs matched by Want.

**Type:** Array&lt;[SkillUri](arkts-ability-skill-skilluri-i.md)&gt;

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-Skill-readonly uris: Array<SkillUri>--><!--Device-Skill-readonly uris: Array<SkillUri>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core
