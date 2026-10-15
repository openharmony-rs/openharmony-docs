# ExtensionAbilityFlag (System API)

```TypeScript
enum ExtensionAbilityFlag
```

Enumerates the ExtensionAbility flags, which indicate the type of ExtensionAbility information to obtain.

**Since:** 9

<!--Device-bundleManager-enum ExtensionAbilityFlag--><!--Device-bundleManager-enum ExtensionAbilityFlag-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## GET_EXTENSION_ABILITY_INFO_DEFAULT

```TypeScript
GET_EXTENSION_ABILITY_INFO_DEFAULT = 0x00000000
```

Used to obtain the default ExtensionAbility information. The obtained information does not contain the permission, metadata, or disabled ExtensionAbility information.

**Since:** 9

<!--Device-ExtensionAbilityFlag-GET_EXTENSION_ABILITY_INFO_DEFAULT = 0x00000000--><!--Device-ExtensionAbilityFlag-GET_EXTENSION_ABILITY_INFO_DEFAULT = 0x00000000-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## GET_EXTENSION_ABILITY_INFO_WITH_APPLICATION

```TypeScript
GET_EXTENSION_ABILITY_INFO_WITH_APPLICATION = 0x00000002
```

Used to obtain the ExtensionAbility information with application information.

**Since:** 9

<!--Device-ExtensionAbilityFlag-GET_EXTENSION_ABILITY_INFO_WITH_APPLICATION = 0x00000002--><!--Device-ExtensionAbilityFlag-GET_EXTENSION_ABILITY_INFO_WITH_APPLICATION = 0x00000002-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## GET_EXTENSION_ABILITY_INFO_WITH_METADATA

```TypeScript
GET_EXTENSION_ABILITY_INFO_WITH_METADATA = 0x00000004
```

Used to obtain the ExtensionAbility information with metadata.

**Since:** 9

<!--Device-ExtensionAbilityFlag-GET_EXTENSION_ABILITY_INFO_WITH_METADATA = 0x00000004--><!--Device-ExtensionAbilityFlag-GET_EXTENSION_ABILITY_INFO_WITH_METADATA = 0x00000004-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## GET_EXTENSION_ABILITY_INFO_WITH_PERMISSION

```TypeScript
GET_EXTENSION_ABILITY_INFO_WITH_PERMISSION = 0x00000001
```

Used to obtain the ExtensionAbility information with permission information.

**Since:** 9

<!--Device-ExtensionAbilityFlag-GET_EXTENSION_ABILITY_INFO_WITH_PERMISSION = 0x00000001--><!--Device-ExtensionAbilityFlag-GET_EXTENSION_ABILITY_INFO_WITH_PERMISSION = 0x00000001-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## GET_EXTENSION_ABILITY_INFO_WITH_SKILL

```TypeScript
GET_EXTENSION_ABILITY_INFO_WITH_SKILL = 0x00000010
```

Used to obtain the ExtensionAbility information with skills.

**Since:** 12

<!--Device-ExtensionAbilityFlag-GET_EXTENSION_ABILITY_INFO_WITH_SKILL = 0x00000010--><!--Device-ExtensionAbilityFlag-GET_EXTENSION_ABILITY_INFO_WITH_SKILL = 0x00000010-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.
