# BundleInfo

应用包信息。

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## appIndex

```TypeScript
readonly appIndex: number
```

应用包的分身索引标识，仅在分身应用中生效。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## appInfo

```TypeScript
readonly appInfo: ApplicationInfo
```

应用程序的配置信息，通过调用
[getBundleInfoForSelf](arkts-ability-getbundleinfoforself-f.md#getbundleinfoforself-1)接
口，bundleFlags参数传入GET_BUNDLE_INFO_WITH_APPLICATION获取。

**类型：** ApplicationInfo

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## buildVersion

```TypeScript
readonly buildVersion?: string
```

应用包的构建版本号，用于标识相同发布版本下的不同构建版本包，对应[app.json5](../../../../quick-start/app-configuration-file.md)中配置的buildVersion字段。
**模型约束：** 此接口仅可在Stage模型下使用。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## firstInstallTime

```TypeScript
readonly firstInstallTime?: number
```

应用在当前设备的首次安装时间戳，表示从1970-01-01 08:00:00 UTC+8逝去的毫秒数，单位毫秒，预置应用的首次安装时间戳为1533657660000。

**类型：** number

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## hapModulesInfo

```TypeScript
readonly hapModulesInfo: Array<HapModuleInfo>
```

模块的配置信息，通过调用
[getBundleInfoForSelf](arkts-ability-getbundleinfoforself-f.md#getbundleinfoforself-1)接
口，bundleFlags参数传入GET_BUNDLE_INFO_WITH_HAP_MODULE获取。

**类型：** Array<HapModuleInfo>

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## installTime

```TypeScript
readonly installTime: number
```

应用包安装时间戳，表示从1970-01-01 08:00:00 UTC+8逝去的毫秒数，单位毫秒。

**说明：**

设备出厂首次开机时，如果未获取到当前时间，会以Unix时间戳基准（1970-01-01 08:00:00 UTC+8）作为当前系统的起始时间。例如，开机后未获取到时间，等待32s之后安装成功，则应用包安装时间戳为32000。

**类型：** number

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## minCompatibleVersionCode

```TypeScript
readonly minCompatibleVersionCode: number
```

分布式场景下的应用包兼容的最低版本，对应[app.json5](../../../../quick-start/app-configuration-file.md)中配置的minCompatibleVersionCode字段。

**类型：** number

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## name

```TypeScript
readonly name: string
```

应用包的名称，对应[app.json5](../../../../quick-start/app-configuration-file.md)中配置的bundleName字段。

**类型：** string

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## permissionGrantStates

```TypeScript
readonly permissionGrantStates: Array<bundleManager.PermissionGrantState>
```

申请权限的授予状态，通过调用
[getBundleInfoForSelf](arkts-ability-getbundleinfoforself-f.md#getbundleinfoforself-1)接
口，bundleFlags参数传入GET_BUNDLE_INFO_WITH_REQUESTED_PERMISSION获取。reqPermissionDetails数组和permissionGrantStates数组的索引顺序一一对
应，即reqPermissionDetails[2]的授权状态为permissionGrantStates[2]。

**类型：** Array<bundleManager.PermissionGrantState>

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## reqPermissionDetails

```TypeScript
readonly reqPermissionDetails: Array<ReqPermissionDetail>
```

应用运行时需向系统申请的权限集合的详细信息，通过调用
[getBundleInfoForSelf](arkts-ability-getbundleinfoforself-f.md#getbundleinfoforself-1)接
口，bundleFlags参数传入GET_BUNDLE_INFO_WITH_REQUESTED_PERMISSION获取。reqPermissionDetails数组和permissionGrantStates数组的索引顺序一一对
应，即reqPermissionDetails[2]的授权状态为permissionGrantStates[2]。

**类型：** Array<ReqPermissionDetail>

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## routerMap

```TypeScript
readonly routerMap: Array<RouterItem>
```

应用的路由表配置，由hapModulesInfo下的routerMap信息，根据RouterItem中的name字段进行去重后合并得到。通过调用
[getBundleInfoForSelf](arkts-ability-getbundleinfoforself-f.md#getbundleinfoforself-1)接
口，bundleFlags参数传入GET_BUNDLE_INFO_WITH_HAP_MODULE和GET_BUNDLE_INFO_WITH_ROUTER_MAP获取。

**类型：** Array<RouterItem>

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## signatureInfo

```TypeScript
readonly signatureInfo: SignatureInfo
```

应用包的签名信息，通过调用
[getBundleInfoForSelf](arkts-ability-getbundleinfoforself-f.md#getbundleinfoforself-1)接
口，bundleFlags参数传入GET_BUNDLE_INFO_WITH_SIGNATURE_INFO获取。

**类型：** SignatureInfo

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## targetVersion

```TypeScript
readonly targetVersion: number
```

应用运行目标版本，对应[app.json5](../../../../quick-start/app-configuration-file.md)中配置的targetAPIVersion字段。

**类型：** number

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## updateTime

```TypeScript
readonly updateTime: number
```

应用包更新时间戳，表示从1970-01-01 08:00:00 UTC+8逝去的毫秒数，单位毫秒。

**类型：** number

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## vendor

```TypeScript
readonly vendor: string
```

应用包的供应商，对应[app.json5](../../../../quick-start/app-configuration-file.md)中配置的vendor字段。

**类型：** string

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## versionCode

```TypeScript
readonly versionCode: number
```

应用包的版本号，对应[app.json5](../../../../quick-start/app-configuration-file.md)中配置的versionCode字段。

**类型：** number

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## versionName

```TypeScript
readonly versionName: string
```

应用包的版本文本描述信息，对应[app.json5](../../../../quick-start/app-configuration-file.md)中配置的versionName字段。

**类型：** string

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

