# BundleFlag

包信息标志，指示需要获取的包信息的内容。

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_DEFAULT

```TypeScript
GET_BUNDLE_INFO_DEFAULT = 0x00000000
```

获取默认包信息，不包含signatureInfo、applicationInfo、hapModuleInfo、ability、extensionAbility和permission的信息。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_WITH_APPLICATION

```TypeScript
GET_BUNDLE_INFO_WITH_APPLICATION = 0x00000001
```

用于获取包含applicationInfo的bundleInfo，获取的bundleInfo不包含signatureInfo、hapModuleInfo、ability、extensionAbility和permission的
信息。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_WITH_HAP_MODULE

```TypeScript
GET_BUNDLE_INFO_WITH_HAP_MODULE = 0x00000002
```

用于获取包含hapModuleInfo的bundleInfo，获取的bundleInfo不包含signatureInfo、applicationInfo、ability、extensionAbility和permission的
信息。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_WITH_ABILITY

```TypeScript
GET_BUNDLE_INFO_WITH_ABILITY = 0x00000004
```

用于获取包含ability的bundleInfo，获取的bundleInfo不包含signatureInfo、applicationInfo、extensionAbility和permission的信息。单独使用不生效，需要与
GET_BUNDLE_INFO_WITH_HAP_MODULE一起使用。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_WITH_EXTENSION_ABILITY

```TypeScript
GET_BUNDLE_INFO_WITH_EXTENSION_ABILITY = 0x00000008
```

用于获取包含extensionAbility的bundleInfo，获取的bundleInfo不包含signatureInfo、applicationInfo、ability 和permission的信息。单独使用不生效，需要
与GET_BUNDLE_INFO_WITH_HAP_MODULE一起使用。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_WITH_REQUESTED_PERMISSION

```TypeScript
GET_BUNDLE_INFO_WITH_REQUESTED_PERMISSION = 0x00000010
```

用于获取包含permission的bundleInfo。获取的bundleInfo不包含signatureInfo、applicationInfo、hapModuleInfo、extensionAbility和ability的
信息。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_WITH_METADATA

```TypeScript
GET_BUNDLE_INFO_WITH_METADATA = 0x00000020
```

用于获取applicationInfo、moduleInfo、abilityInfo和extensionAbilityInfo中包含的metadata。单独使用不生效，它需要与
GET_BUNDLE_INFO_WITH_APPLICATION、GET_BUNDLE_INFO_WITH_HAP_MODULE、GET_BUNDLE_INFO_WITH_ABILITY、
GET_BUNDLE_INFO_WITH_EXTENSION_ABILITY配合使用，其中：

-?获取applicationInfo中包含的metadata，需要与GET_BUNDLE_INFO_WITH_APPLICATION一起使用。

-?获取moduleInfo中包含的metadata，需要与GET_BUNDLE_INFO_WITH_HAP_MODULE一起使用。

-?获取abilityInfo中包含的metadata，需要与GET_BUNDLE_INFO_WITH_HAP_MODULE、GET_BUNDLE_INFO_WITH_ABILITY一起使用。

-?获取extensionAbilityInfo中包含的metadata，需要与GET_BUNDLE_INFO_WITH_HAP_MODULE、GET_BUNDLE_INFO_WITH_EXTENSION_ABILITY一起使
用。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_WITH_DISABLE

```TypeScript
GET_BUNDLE_INFO_WITH_DISABLE = 0x00000040
```

用于获取application被禁用的BundleInfo和被禁用的Ability信息。获取的bundleInfo不包含signatureInfo、applicationInfo、hapModuleInfo、ability、
extensionAbility和permission的信息。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_WITH_SIGNATURE_INFO

```TypeScript
GET_BUNDLE_INFO_WITH_SIGNATURE_INFO = 0x00000080
```

用于获取包含signatureInfo的bundleInfo。获取的bundleInfo不包含applicationInfo、hapModuleInfo、extensionAbility、ability和permission的
信息。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_WITH_MENU

```TypeScript
GET_BUNDLE_INFO_WITH_MENU = 0x00000100
```

用于获取包含fileContextMenuConfig的bundleInfo。单独使用不生效，需要与GET_BUNDLE_INFO_WITH_HAP_MODULE一起使用。

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_WITH_ROUTER_MAP

```TypeScript
GET_BUNDLE_INFO_WITH_ROUTER_MAP = 0x00000200
```

用于获取包含routerMap的bundleInfo。单独使用不生效，需要与GET_BUNDLE_INFO_WITH_HAP_MODULE一起使用。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_WITH_SKILL

```TypeScript
GET_BUNDLE_INFO_WITH_SKILL = 0x00000800
```

用于获取包含skills的bundleInfo。单独使用不生效，需要与GET_BUNDLE_INFO_WITH_HAP_MODULE、GET_BUNDLE_INFO_WITH_ABILITY、
GET_BUNDLE_INFO_WITH_EXTENSION_ABILITY一起使用。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_WITH_ENTRY_MODULE

```TypeScript
GET_BUNDLE_INFO_WITH_ENTRY_MODULE = 0x00010000
```

用于获取包含hapModuleInfo的bundleInfo，仅支持entry模块对应的bundleInfo.hapModulesInfo，如果entry模块不存在，bundleInfo.hapModulesInfo列表为空。
获取的bundleInfo不包含signatureInfo、applicationInfo、ability、extensionAbility和permission的信息。

**起始版本：** 23

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

