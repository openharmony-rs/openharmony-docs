# @ohos.bundle.skillManager(skillManager Module)

This module provides skill query capabilities for applications.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-unnamed-declare namespace skillManager--><!--Device-unnamed-declare namespace skillManager-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## Modules to Import

```TypeScript
import { skillManager } from '@kit.AbilityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getAllSkillInfos](arkts-ability-skillmanager-getallskillinfos-f.md#getallskillinfos) | Obtains all SkillInfo objects installed on the device. To query information for other local accounts, the permission ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS must additionally be granted. |
| [getSkillInfo](arkts-ability-skillmanager-getskillinfo-f.md#getskillinfo) | Obtains SkillInfo of a specified application based on bundleName, moduleName and skillName. To query information for other local accounts, the permission ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS must additionally be granted. |
| [getSkillInfoForSelf](arkts-ability-skillmanager-getskillinfoforself-f.md#getskillinfoforself) | Obtains SkillInfo of the calling application based on moduleName and skillName. |
| [getSkillInfos](arkts-ability-skillmanager-getskillinfos-f.md#getskillinfos) | Obtains all SkillInfo of a specified application based on bundleName. To query information for other local accounts, the permission ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS must additionally be granted. |
| [getSkillInfosForSelf](arkts-ability-skillmanager-getskillinfosforself-f.md#getskillinfosforself) | Obtains all SkillInfo objects of the calling application. |

### Types

| Name | Description |
| --- | --- |
| [SkillInfo](arkts-ability-skillmanager-skillinfo-t.md) | Provides information about a skill, including skill name, type, and associated metadata. |
| [SkillType](arkts-ability-skillmanager-skilltype-t.md) | Enumerates the skill types. |

### Enums

| Name | Description |
| --- | --- |
| [SkillInfoFlag](arkts-ability-skillmanager-skillinfoflag-e.md) | Enumeration of flags used to control what content is populated in a SkillInfo. Multiple flags can be combined using bitwise OR, for example GET_SKILL_INFO_WITH_SRC_ENTRIES &#124; GET_SKILL_INFO_WITH_DESCRIPTION. |
