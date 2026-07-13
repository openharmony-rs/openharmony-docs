# BundleInfo

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃，建议使用[bundleManager-BundleInfo](arkts-ability-bundleinfo-depr-i.md)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [bundleInfo:BundleInfo](arkts-ability-bundleinfo-depr-i.md)

**系统能力：** SystemCapability.BundleManager.BundleFramework

## abilityInfos

```TypeScript
readonly abilityInfos: Array<AbilityInfo>
```

Ability的配置信息

通过调用
[bundle.getBundleInfo](arkts-ability-getbundleinfo-f.md#getbundleinfo-3)
接口时，传入GET_BUNDLE_WITH_ABILITIES获取。

**类型：** Array<AbilityInfo>

**默认值：** Obtains configuration information about an ability

**起始版本：** 7

**废弃版本：** 9

**替代接口：** abilitiesInfo

**系统能力：** SystemCapability.BundleManager.BundleFramework

## appId

```TypeScript
readonly appId: string
```

应用包里应用程序的id。

**类型：** string

**默认值：** Indicates the ID of the application to which this bundle belongs
The application ID uniquely identifies an application. It is determined by the bundle name and signature

**起始版本：** 7

**废弃版本：** 9

**替代接口：** appId

**系统能力：** SystemCapability.BundleManager.BundleFramework

## appInfo

```TypeScript
readonly appInfo: ApplicationInfo
```

应用程序的配置信息。

**类型：** ApplicationInfo

**默认值：** Obtains configuration information about an application

**起始版本：** 7

**废弃版本：** 9

**替代接口：** appInfo

**系统能力：** SystemCapability.BundleManager.BundleFramework

## compatibleVersion

```TypeScript
readonly compatibleVersion: number
```

运行应用包所需要最低的SDK版本号。

**类型：** number

**默认值：** Indicates the compatible version number of the bundle

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

## cpuAbi

```TypeScript
readonly cpuAbi: string
```

应用包的cpuAbi信息。

**类型：** string

**默认值：** Indicates the cpuAbi information of this bundle.

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

## entryInstallationFree

```TypeScript
readonly entryInstallationFree: boolean
```

Entry是否支持免安装，取值为true表示支持免安装，取值为false表示不支持免安装。

**类型：** boolean

**默认值：** Indicates whether free installation of the entry is supported

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

## entryModuleName

```TypeScript
readonly entryModuleName: string
```

Entry的模块名称。

**类型：** string

**默认值：** Indicates entry module name

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

## hapModuleInfos

```TypeScript
readonly hapModuleInfos: Array<HapModuleInfo>
```

模块的配置信息。

**类型：** Array<HapModuleInfo>

**默认值：** Obtains configuration information about a module

**起始版本：** 7

**废弃版本：** 9

**替代接口：** hapModulesInfo

**系统能力：** SystemCapability.BundleManager.BundleFramework

## installTime

```TypeScript
readonly installTime: number
```

HAP安装时间，单位：毫秒。

**类型：** number

**默认值：** Indicates the hap install time

**起始版本：** 7

**废弃版本：** 9

**替代接口：** installTime

**系统能力：** SystemCapability.BundleManager.BundleFramework

## isCompressNativeLibs

```TypeScript
readonly isCompressNativeLibs: boolean
```

是否压缩应用包的本地库，取值为true表示压缩应用包的本地库，取值为false表示不压缩应用包的本地库。

**类型：** boolean

**默认值：** Indicates is compress native libs

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

## isSilentInstallation

```TypeScript
readonly isSilentInstallation: string
```

是否通过静默安装。

**类型：** string

**默认值：** Indicates is silent installation

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

## minCompatibleVersionCode

```TypeScript
readonly minCompatibleVersionCode: number
```

分布式场景下的应用包兼容的最低版本。

**类型：** number

**默认值：** Indicates the earliest historical version compatible with the bundle

**起始版本：** 7

**废弃版本：** 9

**替代接口：** minCompatibleVersionCode

**系统能力：** SystemCapability.BundleManager.BundleFramework

## name

```TypeScript
readonly name: string
```

应用包的名称。

**类型：** string

**默认值：** Indicates the name of this bundle

**起始版本：** 7

**废弃版本：** 9

**替代接口：** name

**系统能力：** SystemCapability.BundleManager.BundleFramework

## reqPermissionDetails

```TypeScript
readonly reqPermissionDetails: Array<ReqPermissionDetail>
```

应用运行时需向系统申请的权限集合的详细信息

通过调用
[bundle.getBundleInfo](arkts-ability-getbundleinfo-f.md#getbundleinfo-3)
接口时，传入GET_BUNDLE_WITH_REQUESTED_PERMISSION获取。

**类型：** Array<ReqPermissionDetail>

**默认值：** Indicates the required permissions details defined in file config.json

**起始版本：** 7

**废弃版本：** 9

**替代接口：** reqPermissionDetails

**系统能力：** SystemCapability.BundleManager.BundleFramework

## reqPermissionStates

```TypeScript
readonly reqPermissionStates: Array<number>
```

申请权限的授予状态。0表示申请成功，-1表示申请失败。

**类型：** Array<number>

**默认值：** Indicates the grant status of required permissions

**起始版本：** 8

**废弃版本：** 9

**替代接口：** permissionGrantStates

**系统能力：** SystemCapability.BundleManager.BundleFramework

## reqPermissions

```TypeScript
readonly reqPermissions: Array<string>
```

应用运行时需向系统申请的权限集合

通过调用
[bundle.getBundleInfo](arkts-ability-getbundleinfo-f.md#getbundleinfo-3)
接口时，传入GET_BUNDLE_WITH_REQUESTED_PERMISSION获取。

**类型：** Array<string>

**默认值：** Indicates the required permissions name defined in file config.json

**起始版本：** 7

**废弃版本：** 9

**替代接口：** permissions

**系统能力：** SystemCapability.BundleManager.BundleFramework

## targetVersion

```TypeScript
readonly targetVersion: number
```

运行应用包所需要最高SDK版本号。

**类型：** number

**默认值：** Indicates the target version number of the bundle

**起始版本：** 7

**废弃版本：** 9

**替代接口：** targetVersion

**系统能力：** SystemCapability.BundleManager.BundleFramework

## type

```TypeScript
readonly type: string
```

应用包类型。

**类型：** string

**默认值：** Indicates the name of this original bundle

**起始版本：** 7

**废弃版本：** 9

**替代接口：** bundleType

**系统能力：** SystemCapability.BundleManager.BundleFramework

## uid

```TypeScript
readonly uid: number
```

应用包里应用程序的uid。

**类型：** number

**默认值：** Indicates the UID of the application to which this bundle belongs
The UID uniquely identifies an application. It is determined by the process and user IDs of the application
After an application is installed, its UID remains unchanged unless it is uninstalled and then reinstalled

**起始版本：** 7

**废弃版本：** 9

**替代接口：** uid

**系统能力：** SystemCapability.BundleManager.BundleFramework

## updateTime

```TypeScript
readonly updateTime: number
```

HAP更新时间，单位：毫秒。

**类型：** number

**默认值：** Indicates the hap update time

**起始版本：** 7

**废弃版本：** 9

**替代接口：** updateTime

**系统能力：** SystemCapability.BundleManager.BundleFramework

## vendor

```TypeScript
readonly vendor: string
```

应用包的供应商。

**类型：** string

**默认值：** Describes the bundle vendor

**起始版本：** 7

**废弃版本：** 9

**替代接口：** vendor

**系统能力：** SystemCapability.BundleManager.BundleFramework

## versionCode

```TypeScript
readonly versionCode: number
```

应用包的版本号。

**类型：** number

**默认值：** Indicates the version number of the bundle

**起始版本：** 7

**废弃版本：** 9

**替代接口：** versionCode

**系统能力：** SystemCapability.BundleManager.BundleFramework

## versionName

```TypeScript
readonly versionName: string
```

应用包的版本文本描述信息。

**类型：** string

**默认值：** Indicates the text description of the bundle version

**起始版本：** 7

**废弃版本：** 9

**替代接口：** versionName

**系统能力：** SystemCapability.BundleManager.BundleFramework

