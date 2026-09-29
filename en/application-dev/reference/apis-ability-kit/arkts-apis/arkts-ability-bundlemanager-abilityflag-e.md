# AbilityFlag

```TypeScript
enum AbilityFlag
```

Enumerates the ability flags, which indicate the type of ability information to obtain.

**Since:** 20

<!--Device-bundleManager-enum AbilityFlag--><!--Device-bundleManager-enum AbilityFlag-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## GET_ABILITY_INFO_DEFAULT

```TypeScript
GET_ABILITY_INFO_DEFAULT = 0x00000000
```

Used to obtain the default ability information, which does not contain permissions, metadata, or ability information of disabled abilities. <!--Del-->You can use [setAbilityEnabled](arkts-ability-bundlemanager-setabilityenabled-f-sys.md#setabilityenabled-1) to set the ability enabling status and use [isAbilityEnabled](arkts-ability-bundlemanager-isabilityenabled-f-sys.md#isabilityenabled-2) to obtain the ability enabling status.<!--DelEnd-->

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-AbilityFlag-GET_ABILITY_INFO_DEFAULT = 0x00000000--><!--Device-AbilityFlag-GET_ABILITY_INFO_DEFAULT = 0x00000000-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## GET_ABILITY_INFO_WITH_PERMISSION

```TypeScript
GET_ABILITY_INFO_WITH_PERMISSION = 0x00000001
```

Used to obtain the ability information containing permissions.

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-AbilityFlag-GET_ABILITY_INFO_WITH_PERMISSION = 0x00000001--><!--Device-AbilityFlag-GET_ABILITY_INFO_WITH_PERMISSION = 0x00000001-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## GET_ABILITY_INFO_WITH_APPLICATION

```TypeScript
GET_ABILITY_INFO_WITH_APPLICATION = 0x00000002
```

Used to obtain the ability information containing application information.

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-AbilityFlag-GET_ABILITY_INFO_WITH_APPLICATION = 0x00000002--><!--Device-AbilityFlag-GET_ABILITY_INFO_WITH_APPLICATION = 0x00000002-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## GET_ABILITY_INFO_WITH_METADATA

```TypeScript
GET_ABILITY_INFO_WITH_METADATA = 0x00000004
```

Used to obtain the ability information containing metadata.

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-AbilityFlag-GET_ABILITY_INFO_WITH_METADATA = 0x00000004--><!--Device-AbilityFlag-GET_ABILITY_INFO_WITH_METADATA = 0x00000004-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## GET_ABILITY_INFO_WITH_DISABLE

```TypeScript
GET_ABILITY_INFO_WITH_DISABLE = 0x00000008
```

Used to obtain the ability information of disabled abilities.

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-AbilityFlag-GET_ABILITY_INFO_WITH_DISABLE = 0x00000008--><!--Device-AbilityFlag-GET_ABILITY_INFO_WITH_DISABLE = 0x00000008-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## GET_ABILITY_INFO_ONLY_SYSTEM_APP

```TypeScript
GET_ABILITY_INFO_ONLY_SYSTEM_APP = 0x00000010
```

Used to obtain the ability information of system applications.

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-AbilityFlag-GET_ABILITY_INFO_ONLY_SYSTEM_APP = 0x00000010--><!--Device-AbilityFlag-GET_ABILITY_INFO_ONLY_SYSTEM_APP = 0x00000010-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## GET_ABILITY_INFO_WITH_APP_LINKING

```TypeScript
GET_ABILITY_INFO_WITH_APP_LINKING = 0x00000040
```

Used to obtain the ability information that passes <!--RP3--> [domain name verification](../../../application-models/app-linking-startup.md#working-principles)<!--RP3End-->.

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-AbilityFlag-GET_ABILITY_INFO_WITH_APP_LINKING = 0x00000040--><!--Device-AbilityFlag-GET_ABILITY_INFO_WITH_APP_LINKING = 0x00000040-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## GET_ABILITY_INFO_WITH_SKILL

```TypeScript
GET_ABILITY_INFO_WITH_SKILL = 0x00000080
```

Used to obtain the ability information containing skills.

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-AbilityFlag-GET_ABILITY_INFO_WITH_SKILL = 0x00000080--><!--Device-AbilityFlag-GET_ABILITY_INFO_WITH_SKILL = 0x00000080-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core
