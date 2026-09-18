# @ohos.bundle.skillManager

This module provides skill query capabilities for applications.

@namespace skillManager

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## Modules to Import

```TypeScript
import { skillManager } from '@kit.AbilityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getAllSkillInfos](arkts-ability-skillmanager-getallskillinfos-f.md) | Obtains all SkillInfo objects installed on the device. To query information for other local accounts, the permission ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS must additionally be granted. |
| [getSkillInfo](arkts-ability-skillmanager-getskillinfo-f.md) | Obtains SkillInfo of a specified application based on bundleName, moduleName and skillName. To query information for other local accounts, the permission ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS must additionally be granted. |
| [getSkillInfoForSelf](arkts-ability-skillmanager-getskillinfoforself-f.md) | Obtains SkillInfo of the calling application based on moduleName and skillName. |
| [getSkillInfos](arkts-ability-skillmanager-getskillinfos-f.md) | Obtains all SkillInfo of a specified application based on bundleName. To query information for other local accounts, the permission ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS must additionally be granted. |
| [getSkillInfosForSelf](arkts-ability-skillmanager-getskillinfosforself-f.md) | Obtains all SkillInfo objects of the calling application. |

### Enums

| Name | Description |
| --- | --- |
| [SkillInfoFlag](arkts-ability-skillmanager-skillinfoflag-e.md) | Enumeration of flags used to control what content is populated in a SkillInfo. Multiple flags can be combined using bitwise OR, for example GET_SKILL_INFO_WITH_SRC_ENTRIES &#124; GET_SKILL_INFO_WITH_DESCRIPTION. |

### Types

| Name | Description |
| --- | --- |
| [SkillInfo](arkts-ability-skillmanager-skillinfo-t.md) | Provides information about a skill, including skill name, type, and associated metadata. |
| [SkillType](arkts-ability-skillmanager-skilltype-t.md) | Enumerates the skill types. |
