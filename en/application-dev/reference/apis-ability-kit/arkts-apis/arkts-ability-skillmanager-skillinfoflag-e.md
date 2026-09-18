# SkillInfoFlag

Enumeration of flags used to control what content is populated in a SkillInfo. Multiple flags can be combined using bitwise OR, for example GET_SKILL_INFO_WITH_SRC_ENTRIES | GET_SKILL_INFO_WITH_DESCRIPTION.

@enum { int }

**Since:** 26.0.0

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## GET_SKILL_INFO_DEFAULT

```TypeScript
GET_SKILL_INFO_DEFAULT = 0x00000000
```

Used to obtain the default SkillInfo.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## GET_SKILL_INFO_WITH_DESCRIPTION

```TypeScript
GET_SKILL_INFO_WITH_DESCRIPTION = 0x00000001
```

Used to obtain the SkillInfo containing description.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## GET_SKILL_INFO_WITH_SRC_ENTRIES

```TypeScript
GET_SKILL_INFO_WITH_SRC_ENTRIES = 0x00000002
```

Used to obtain the SkillInfo containing srcEntries.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## GET_SKILL_INFO_WITH_PERMISSIONS

```TypeScript
GET_SKILL_INFO_WITH_PERMISSIONS = 0x00000004
```

Used to obtain the SkillInfo containing permissions.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## GET_SKILL_INFO_WITH_REQUEST_PERMISSIONS

```TypeScript
GET_SKILL_INFO_WITH_REQUEST_PERMISSIONS = 0x00000008
```

Used to obtain the permissions declared under requestPermissions in the module manifest.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core
