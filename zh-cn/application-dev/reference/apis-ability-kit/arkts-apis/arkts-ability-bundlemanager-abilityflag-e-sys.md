# AbilityFlag（系统接口）

Ability组件信息标志，指示需要获取的Ability组件信息的内容。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-bundleManager-enum AbilityFlag--><!--Device-bundleManager-enum AbilityFlag-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## GET_ABILITY_INFO_DEFAULT

```TypeScript
GET_ABILITY_INFO_DEFAULT = 0x00000000
```

获取默认AbilityInfo，获取的AbilityInfo不包含permissions、metadata、被禁用Ability对应的 AbilityInfo。&lt;!--Del--&gt;通过 [setAbilityEnabled接口](arkts-ability-bundlemanager-setabilityenabled-f-sys.md#setAbilityEnabled（系统接口）) 可设置Ability禁用状态、通过 [isAbilityEnabled接口](arkts-ability-bundlemanager-isabilityenabled-f-sys.md#isAbilityEnabled（系统接口）)可获取 Ability禁用状态。&lt;!--DelEnd--&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityFlag-GET_ABILITY_INFO_DEFAULT = 0x00000000--><!--Device-AbilityFlag-GET_ABILITY_INFO_DEFAULT = 0x00000000-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## GET_ABILITY_INFO_WITH_PERMISSION

```TypeScript
GET_ABILITY_INFO_WITH_PERMISSION = 0x00000001
```

获取包含permissions的AbilityInfo。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityFlag-GET_ABILITY_INFO_WITH_PERMISSION = 0x00000001--><!--Device-AbilityFlag-GET_ABILITY_INFO_WITH_PERMISSION = 0x00000001-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## GET_ABILITY_INFO_WITH_APPLICATION

```TypeScript
GET_ABILITY_INFO_WITH_APPLICATION = 0x00000002
```

获取包含applicationInfo的AbilityInfo。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityFlag-GET_ABILITY_INFO_WITH_APPLICATION = 0x00000002--><!--Device-AbilityFlag-GET_ABILITY_INFO_WITH_APPLICATION = 0x00000002-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## GET_ABILITY_INFO_WITH_METADATA

```TypeScript
GET_ABILITY_INFO_WITH_METADATA = 0x00000004
```

获取包含metadata的AbilityInfo。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityFlag-GET_ABILITY_INFO_WITH_METADATA = 0x00000004--><!--Device-AbilityFlag-GET_ABILITY_INFO_WITH_METADATA = 0x00000004-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## GET_ABILITY_INFO_WITH_DISABLE

```TypeScript
GET_ABILITY_INFO_WITH_DISABLE = 0x00000008
```

获取被禁用Ability对应的AbilityInfo。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityFlag-GET_ABILITY_INFO_WITH_DISABLE = 0x00000008--><!--Device-AbilityFlag-GET_ABILITY_INFO_WITH_DISABLE = 0x00000008-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## GET_ABILITY_INFO_ONLY_SYSTEM_APP

```TypeScript
GET_ABILITY_INFO_ONLY_SYSTEM_APP = 0x00000010
```

获取系统应用对应的AbilityInfo。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityFlag-GET_ABILITY_INFO_ONLY_SYSTEM_APP = 0x00000010--><!--Device-AbilityFlag-GET_ABILITY_INFO_ONLY_SYSTEM_APP = 0x00000010-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## GET_ABILITY_INFO_WITH_APP_LINKING

```TypeScript
GET_ABILITY_INFO_WITH_APP_LINKING = 0x00000040
```

获取通过&lt;!--RP3--&gt;[域名校验](../../../application-models/app-linking-startup.md#实现原理)&lt;!--RP3End--&gt;筛选的AbilityInfo。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityFlag-GET_ABILITY_INFO_WITH_APP_LINKING = 0x00000040--><!--Device-AbilityFlag-GET_ABILITY_INFO_WITH_APP_LINKING = 0x00000040-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## GET_ABILITY_INFO_WITH_SKILL

```TypeScript
GET_ABILITY_INFO_WITH_SKILL = 0x00000080
```

获取包含skills的AbilityInfo。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityFlag-GET_ABILITY_INFO_WITH_SKILL = 0x00000080--><!--Device-AbilityFlag-GET_ABILITY_INFO_WITH_SKILL = 0x00000080-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

