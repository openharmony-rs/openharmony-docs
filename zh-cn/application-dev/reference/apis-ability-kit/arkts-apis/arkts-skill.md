# Skill

The module defines a skill object. Such an object can be obtained through
 [bundleManager.getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md)
 , with at least **GET_BUNDLE_INFO_WITH_HAP_MODULE**, **GET_BUNDLE_INFO_WITH_ABILITY**, and
 **GET_BUNDLE_INFO_WITH_SKILL** passed in to **bundleFlags**. (The skill information is contained in
 BundleInfo -> HapModuleInfo -> AbilityInfo or
 [ExtensionAbilityInfo](arkts-ability-extensionabilityinfo-i.md).)


## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [Skill](arkts-ability-skill-i.md) | skill标签对象。 |
| [SkillUri](arkts-ability-skill-skilluri-i.md) | Want匹配的Uri集合。 |
