# ApplicationFlag（系统接口）

应用信息标志，指示需要获取的应用信息的内容。

**起始版本：** 9

<!--Device-bundleManager-enum ApplicationFlag--><!--Device-bundleManager-enum ApplicationFlag-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## GET_APPLICATION_INFO_DEFAULT

```TypeScript
GET_APPLICATION_INFO_DEFAULT = 0x00000000
```

用于获取默认的applicationInfo，获取的applicationInfo不包含permission和metadata信息。

**起始版本：** 9

<!--Device-ApplicationFlag-GET_APPLICATION_INFO_DEFAULT = 0x00000000--><!--Device-ApplicationFlag-GET_APPLICATION_INFO_DEFAULT = 0x00000000-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## GET_APPLICATION_INFO_WITH_PERMISSION

```TypeScript
GET_APPLICATION_INFO_WITH_PERMISSION = 0x00000001
```

用于获取包含permission的applicationInfo。

**起始版本：** 9

<!--Device-ApplicationFlag-GET_APPLICATION_INFO_WITH_PERMISSION = 0x00000001--><!--Device-ApplicationFlag-GET_APPLICATION_INFO_WITH_PERMISSION = 0x00000001-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## GET_APPLICATION_INFO_WITH_METADATA

```TypeScript
GET_APPLICATION_INFO_WITH_METADATA = 0x00000002
```

用于获取包含metadata的applicationInfo。

**起始版本：** 9

<!--Device-ApplicationFlag-GET_APPLICATION_INFO_WITH_METADATA = 0x00000002--><!--Device-ApplicationFlag-GET_APPLICATION_INFO_WITH_METADATA = 0x00000002-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## GET_APPLICATION_INFO_WITH_DISABLE

```TypeScript
GET_APPLICATION_INFO_WITH_DISABLE = 0x00000004
```

用于获取包含禁用应用程序的applicationInfo。

**起始版本：** 9

<!--Device-ApplicationFlag-GET_APPLICATION_INFO_WITH_DISABLE = 0x00000004--><!--Device-ApplicationFlag-GET_APPLICATION_INFO_WITH_DISABLE = 0x00000004-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

