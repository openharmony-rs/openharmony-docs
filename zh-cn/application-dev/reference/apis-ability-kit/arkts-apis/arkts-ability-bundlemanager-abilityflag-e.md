# AbilityFlag

Ability组件信息标志，指示需要获取的Ability组件信息的内容。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-bundleManager-enum AbilityFlag--><!--Device-bundleManager-enum AbilityFlag-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## GET_ABILITY_INFO_DEFAULT

```TypeScript
GET_ABILITY_INFO_DEFAULT = 0x00000000
```

获取默认[AbilityInfo]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_，获取的AbilityInfo不包含permissions、metadata、被禁用Ability对应的 AbilityInfo。\_\_\_MD\_COMMENT\_DESC\_USD\_3\_\_\_通过 [setAbilityEnabled接口]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_ 可设置Ability禁用状态、通过 [isAbilityEnabled接口]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_可获取 Ability禁用状态。\_\_\_MD\_COMMENT\_DESC\_USD\_4\_\_\_

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityFlag-GET_ABILITY_INFO_DEFAULT = 0x00000000--><!--Device-AbilityFlag-GET_ABILITY_INFO_DEFAULT = 0x00000000-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## GET_ABILITY_INFO_WITH_PERMISSION

```TypeScript
GET_ABILITY_INFO_WITH_PERMISSION = 0x00000001
```

获取包含permissions的AbilityInfo。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityFlag-GET_ABILITY_INFO_WITH_PERMISSION = 0x00000001--><!--Device-AbilityFlag-GET_ABILITY_INFO_WITH_PERMISSION = 0x00000001-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## GET_ABILITY_INFO_WITH_APPLICATION

```TypeScript
GET_ABILITY_INFO_WITH_APPLICATION = 0x00000002
```

获取包含applicationInfo的AbilityInfo。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityFlag-GET_ABILITY_INFO_WITH_APPLICATION = 0x00000002--><!--Device-AbilityFlag-GET_ABILITY_INFO_WITH_APPLICATION = 0x00000002-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## GET_ABILITY_INFO_WITH_METADATA

```TypeScript
GET_ABILITY_INFO_WITH_METADATA = 0x00000004
```

获取包含metadata的AbilityInfo。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityFlag-GET_ABILITY_INFO_WITH_METADATA = 0x00000004--><!--Device-AbilityFlag-GET_ABILITY_INFO_WITH_METADATA = 0x00000004-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## GET_ABILITY_INFO_WITH_DISABLE

```TypeScript
GET_ABILITY_INFO_WITH_DISABLE = 0x00000008
```

获取被禁用Ability对应的AbilityInfo。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityFlag-GET_ABILITY_INFO_WITH_DISABLE = 0x00000008--><!--Device-AbilityFlag-GET_ABILITY_INFO_WITH_DISABLE = 0x00000008-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## GET_ABILITY_INFO_ONLY_SYSTEM_APP

```TypeScript
GET_ABILITY_INFO_ONLY_SYSTEM_APP = 0x00000010
```

获取系统应用对应的AbilityInfo。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityFlag-GET_ABILITY_INFO_ONLY_SYSTEM_APP = 0x00000010--><!--Device-AbilityFlag-GET_ABILITY_INFO_ONLY_SYSTEM_APP = 0x00000010-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## GET_ABILITY_INFO_WITH_APP_LINKING

```TypeScript
GET_ABILITY_INFO_WITH_APP_LINKING = 0x00000040
```

获取通过\_\_\_MD\_COMMENT\_DESC\_USD\_1\_\_\_\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_\_\_\_MD\_COMMENT\_DESC\_USD\_2\_\_\_筛选的AbilityInfo。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityFlag-GET_ABILITY_INFO_WITH_APP_LINKING = 0x00000040--><!--Device-AbilityFlag-GET_ABILITY_INFO_WITH_APP_LINKING = 0x00000040-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## GET_ABILITY_INFO_WITH_SKILL

```TypeScript
GET_ABILITY_INFO_WITH_SKILL = 0x00000080
```

获取包含skills的AbilityInfo。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityFlag-GET_ABILITY_INFO_WITH_SKILL = 0x00000080--><!--Device-AbilityFlag-GET_ABILITY_INFO_WITH_SKILL = 0x00000080-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

