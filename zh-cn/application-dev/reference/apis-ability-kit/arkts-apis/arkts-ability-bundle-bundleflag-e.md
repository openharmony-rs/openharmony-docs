# BundleFlag

> **说明：**  
>  
> 从API version 7开始支持，从API version 9开始废弃，建议使用  
> [bundleManager.BundleFlag](arkts-ability-bundlemanager-bundleflag-e.md)替代。

包信息标志，指示需要获取的包信息的内容。

当接口与标志不匹配时，该标志会被忽略，例如获取application时使用GET_ABILITY_INFO_WITH_PERMISSION对结果不会产生影响。

标志可以叠加使用，例如使用GET_APPLICATION_INFO_WITH_PERMISSION + GET_APPLICATION_INFO_WITH_DISABLE可以使结果同时包含应用权限信息和被禁用的应用信息。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [BundleFlag](arkts-ability-bundlemanager-bundleflag-e.md)

<!--Device-bundle-enum BundleFlag--><!--Device-bundle-enum BundleFlag-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## GET_BUNDLE_DEFAULT

```TypeScript
GET_BUNDLE_DEFAULT = 0x00000000
```

获取默认的应用信息。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** GET_BUNDLE_INFO_DEFAULT

<!--Device-BundleFlag-GET_BUNDLE_DEFAULT = 0x00000000--><!--Device-BundleFlag-GET_BUNDLE_DEFAULT = 0x00000000-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## GET_BUNDLE_WITH_ABILITIES

```TypeScript
GET_BUNDLE_WITH_ABILITIES = 0x00000001
```

获取包括Ability信息的包信息。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** GET_BUNDLE_INFO_WITH_ABILITY

<!--Device-BundleFlag-GET_BUNDLE_WITH_ABILITIES = 0x00000001--><!--Device-BundleFlag-GET_BUNDLE_WITH_ABILITIES = 0x00000001-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## GET_ABILITY_INFO_WITH_PERMISSION

```TypeScript
GET_ABILITY_INFO_WITH_PERMISSION = 0x00000002
```

获取包括权限的Ability信息。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** GET_ABILITY_INFO_WITH_PERMISSION

<!--Device-BundleFlag-GET_ABILITY_INFO_WITH_PERMISSION = 0x00000002--><!--Device-BundleFlag-GET_ABILITY_INFO_WITH_PERMISSION = 0x00000002-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## GET_ABILITY_INFO_WITH_APPLICATION

```TypeScript
GET_ABILITY_INFO_WITH_APPLICATION = 0x00000004
```

获取包括Application的ability信息。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** GET_ABILITY_INFO_WITH_APPLICATION

<!--Device-BundleFlag-GET_ABILITY_INFO_WITH_APPLICATION = 0x00000004--><!--Device-BundleFlag-GET_ABILITY_INFO_WITH_APPLICATION = 0x00000004-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## GET_APPLICATION_INFO_WITH_PERMISSION

```TypeScript
GET_APPLICATION_INFO_WITH_PERMISSION = 0x00000008
```

安装冲突 （常见于升级和已有应用基本信息不一致）。

**起始版本：** 7

**废弃版本：** 9

<!--Device-BundleFlag-GET_APPLICATION_INFO_WITH_PERMISSION = 0x00000008--><!--Device-BundleFlag-GET_APPLICATION_INFO_WITH_PERMISSION = 0x00000008-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## GET_BUNDLE_WITH_REQUESTED_PERMISSION

```TypeScript
GET_BUNDLE_WITH_REQUESTED_PERMISSION = 0x00000010
```

获取包括所需权限的包信息。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** GET_BUNDLE_INFO_WITH_REQUESTED_PERMISSION

<!--Device-BundleFlag-GET_BUNDLE_WITH_REQUESTED_PERMISSION = 0x00000010--><!--Device-BundleFlag-GET_BUNDLE_WITH_REQUESTED_PERMISSION = 0x00000010-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## GET_ALL_APPLICATION_INFO

```TypeScript
GET_ALL_APPLICATION_INFO = 0xFFFF0000
```

安装冲突 （常见于升级和已有应用基本信息不一致）。

**起始版本：** 7

**废弃版本：** 9

<!--Device-BundleFlag-GET_ALL_APPLICATION_INFO = 0xFFFF0000--><!--Device-BundleFlag-GET_ALL_APPLICATION_INFO = 0xFFFF0000-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## GET_ABILITY_INFO_WITH_METADATA

```TypeScript
GET_ABILITY_INFO_WITH_METADATA = 0x00000020
```

获取ability的元数据信息。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** GET_ABILITY_INFO_WITH_METADATA

<!--Device-BundleFlag-GET_ABILITY_INFO_WITH_METADATA = 0x00000020--><!--Device-BundleFlag-GET_ABILITY_INFO_WITH_METADATA = 0x00000020-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## GET_APPLICATION_INFO_WITH_METADATA

```TypeScript
GET_APPLICATION_INFO_WITH_METADATA = 0x00000040
```

缺少卸载权限。

**起始版本：** 8

**废弃版本：** 9

<!--Device-BundleFlag-GET_APPLICATION_INFO_WITH_METADATA = 0x00000040--><!--Device-BundleFlag-GET_APPLICATION_INFO_WITH_METADATA = 0x00000040-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## GET_ABILITY_INFO_SYSTEMAPP_ONLY

```TypeScript
GET_ABILITY_INFO_SYSTEMAPP_ONLY = 0x00000080
```

获取仅包括系统应用的ability信息。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** GET_ABILITY_INFO_ONLY_SYSTEM_APP

<!--Device-BundleFlag-GET_ABILITY_INFO_SYSTEMAPP_ONLY = 0x00000080--><!--Device-BundleFlag-GET_ABILITY_INFO_SYSTEMAPP_ONLY = 0x00000080-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## GET_ABILITY_INFO_WITH_DISABLE

```TypeScript
GET_ABILITY_INFO_WITH_DISABLE = 0x00000100
```

获取包括被禁用的ability信息。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** GET_ABILITY_INFO_WITH_DISABLE

<!--Device-BundleFlag-GET_ABILITY_INFO_WITH_DISABLE = 0x00000100--><!--Device-BundleFlag-GET_ABILITY_INFO_WITH_DISABLE = 0x00000100-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## GET_APPLICATION_INFO_WITH_DISABLE

```TypeScript
GET_APPLICATION_INFO_WITH_DISABLE = 0x00000200
```

缺少卸载权限。

**起始版本：** 8

**废弃版本：** 9

<!--Device-BundleFlag-GET_APPLICATION_INFO_WITH_DISABLE = 0x00000200--><!--Device-BundleFlag-GET_APPLICATION_INFO_WITH_DISABLE = 0x00000200-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

