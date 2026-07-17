# SkillInfo

<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @kongjing2-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=7eb6f57046c125c4e13d8acd776d3cbaf09f5103 translatedAt=2026-06-22T06:57:28.662Z pushedAt=2026-06-25T06:26:39.941Z -->

A skill is a capability encapsulation unit provided by the system for AI agents. Skills are declared through the skillProfiles tag in the [module.json5 Configuration File](../../quick-start/module-configuration-file.md#skillprofiles). An app can query installed skill information through the APIs provided by [skillManager](js-apis-skillManager.md), discovering and invoking AI agent capabilities on the device.

**Since:** 26.0.0

## Modules to Import

```ts
import { skillManager } from '@kit.AbilityKit';
```

## SkillInfo

Skill configuration information, used to define the skill capabilities of an AI agent.

**Since:** 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

| Name           | Type   | Read-Only | Optional | Description           |
| -------------- | ------ | ---- | ---- | -------------- |
| bundleName   | string | Yes   | No   | Bundle name of the app to which the skill belongs.   |
| moduleName   | string | Yes   | No   | Name of the module to which the skill belongs.   |
| skillName   | string | Yes   | No   | Name of the skill.   |
| skillType   | [SkillType](#skilltype) | Yes   | No   | Type of the skill.   |
| skillPath   | string | Yes   | No   | Installation path of the skill.   |
| abilityName   | string | Yes   | No   | Name of the ability associated with the skill.   |
| versionCode   | number | Yes   | No   | Version number of the skill.   |
| description   | string | Yes   | Yes   | Description of the skill. When the app calls the [skillManager](js-apis-skillManager.md) API and the [SkillInfoFlag](js-apis-skillManager.md#skillinfoflag) passed in does not include GET_SKILL_INFO_WITH_DESCRIPTION, this field returns the default value undefined. Developers must check the validity of the value to prevent code exceptions. |
| srcEntries   | Array\<string\> | Yes   | Yes   | List of code file paths that implement the skill. When the app calls the [skillManager](js-apis-skillManager.md) API and the [SkillInfoFlag](js-apis-skillManager.md#skillinfoflag) passed in does not include GET_SKILL_INFO_WITH_SRC_ENTRIES, this field returns the default value undefined. Developers must check the validity of the value to prevent code exceptions.  |
| permissions   | Array\<string\> | Yes   | Yes   | List of permissions required to call the skill. When the app calls the [skillManager](js-apis-skillManager.md) API and the [SkillInfoFlag](js-apis-skillManager.md#skillinfoflag) passed in does not include GET_SKILL_INFO_WITH_PERMISSIONS, this field returns the default value undefined. Developers must check the validity of the value to prevent code exceptions.  |
| requestPermissions   | Array\<string\> | Yes   | Yes   | Permissions requested by the module where the skill is located. When the app calls the [skillManager](js-apis-skillManager.md) API and the [SkillInfoFlag](js-apis-skillManager.md#skillinfoflag) passed in does not include GET_SKILL_INFO_WITH_REQUEST_PERMISSIONS, this field returns the default value undefined. Developers must check the validity of the value to prevent code exceptions.|

## SkillType

Enumerates the skill types.

**Since:** 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

| Name | Value | Description |
| --- | --- |------|
| APP_SKILL | 0 | App skill. |
| INDEPENDENT_SKILL | 1 | Independent skill. |