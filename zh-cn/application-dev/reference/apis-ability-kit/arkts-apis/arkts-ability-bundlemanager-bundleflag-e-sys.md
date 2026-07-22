# BundleFlag

包信息标志，指示需要获取的包信息的内容。

**起始版本：** 9

<!--Device-bundleManager-enum BundleFlag--><!--Device-bundleManager-enum BundleFlag-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_ONLY_WITH_LAUNCHER_ABILITY

```TypeScript
GET_BUNDLE_INFO_ONLY_WITH_LAUNCHER_ABILITY = 0x00001000
```

用于获取仅包含有桌面图标的应用的bundleInfo。它仅在[getAllBundleInfo](arkts-ability-bundlemanager-getallbundleinfo-f-sys.md#getallbundleinfo)接口中生效。

**系统API：** 该标记仅支持在系统API中使用。

**起始版本：** 12

<!--Device-BundleFlag-GET_BUNDLE_INFO_ONLY_WITH_LAUNCHER_ABILITY = 0x00001000--><!--Device-BundleFlag-GET_BUNDLE_INFO_ONLY_WITH_LAUNCHER_ABILITY = 0x00001000-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## GET_BUNDLE_INFO_OF_ANY_USER

```TypeScript
GET_BUNDLE_INFO_OF_ANY_USER = 0x00002000
```

用于获取任意用户安装的bundleInfo。它不能单独使用，需要与GET_BUNDLE_INFO_WITH_APPLICATION一起使用。它仅在[getBundleInfo](arkts-ability-bundlemanager-getbundleinfo-f.md#getbundleinfo)、[getAllBundleInfo](arkts-ability-bundlemanager-getallbundleinfo-f-sys.md#getallbundleinfo)接口生效。

**系统API：** 该标记仅支持在系统API中使用。

**起始版本：** 12

<!--Device-BundleFlag-GET_BUNDLE_INFO_OF_ANY_USER = 0x00002000--><!--Device-BundleFlag-GET_BUNDLE_INFO_OF_ANY_USER = 0x00002000-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## GET_BUNDLE_INFO_EXCLUDE_CLONE

```TypeScript
GET_BUNDLE_INFO_EXCLUDE_CLONE = 0x00004000
```

用于获取去除分身应用而仅包含主应用的bundleInfo。它仅在[getAllBundleInfo](arkts-ability-bundlemanager-getallbundleinfo-f-sys.md#getallbundleinfo)接口中生效。

**系统API：** 该标记仅支持在系统API中使用。

**起始版本：** 12

<!--Device-BundleFlag-GET_BUNDLE_INFO_EXCLUDE_CLONE = 0x00004000--><!--Device-BundleFlag-GET_BUNDLE_INFO_EXCLUDE_CLONE = 0x00004000-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## GET_BUNDLE_INFO_WITH_CLOUD_KIT

```TypeScript
GET_BUNDLE_INFO_WITH_CLOUD_KIT = 0x00008000
```

用于获取启用端云文件同步能力或者端云结构化数据同步能力的应用的bundleInfo。它仅在[getAllBundleInfo](arkts-ability-bundlemanager-getallbundleinfo-f-sys.md#getallbundleinfo)接口中生效。

**系统API：** 该标记仅支持在系统API中使用。

**起始版本：** 20

<!--Device-BundleFlag-GET_BUNDLE_INFO_WITH_CLOUD_KIT = 0x00008000--><!--Device-BundleFlag-GET_BUNDLE_INFO_WITH_CLOUD_KIT = 0x00008000-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

