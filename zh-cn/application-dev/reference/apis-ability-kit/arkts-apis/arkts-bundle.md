# @ohos.bundle

本模块提供应用信息查询能力，支持[包信息](arkts-ability-bundleinfo-depr-i.md)、[应用信息](arkts-ability-applicationinfo-depr-i.md)、
[Ability组件信息](arkts-ability-abilityinfo-depr-i.md)等信息的查询，以及应用禁用状态的查询、设置等。

> **说明：**
>
> 从API version 9开始，该模块不再维护，建议使用[@ohos.bundle.bundleManager](arkts-bundle-bundlemanager.md)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [bundleManager:bundleManager](arkts-bundle-bundlemanager.md)

**系统能力：** SystemCapability.BundleManager.BundleFramework

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getAbilityIcon](arkts-ability-getabilityicon-f.md#getabilityicon-1) | 通过bundleName和abilityName获取对应Icon的[PixelMap](../../apis-image-kit/arkts-apis/arkts-multimedia-image.md)，使用callback异步回调。获取调用方自己的信息时不需要权限。 |
| [getAbilityIcon](arkts-ability-getabilityicon-f.md#getabilityicon-2) | 通过bundleName和abilityName获取对应Icon的[PixelMap](../../apis-image-kit/arkts-apis/arkts-multimedia-image.md)，使用Promise异步回调。获取调用方自己的信息时不需要权限。 |
| [getAbilityInfo](arkts-ability-getabilityinfo-f.md#getabilityinfo-1) | 通过Bundle名称和组件名获取Ability组件信息，使用callback异步回调。获取调用方自己的信息时不需要权限。 |
| [getAbilityInfo](arkts-ability-getabilityinfo-f.md#getabilityinfo-2) | 通过Bundle名称和组件名获取Ability组件信息，使用Promise形式异步回调。获取调用方自己的信息时不需要权限。 |
| [getAbilityLabel](arkts-ability-getabilitylabel-f.md#getabilitylabel-1) | 通过Bundle名称和Ability组件名获取应用名称，使用callback异步回调。获取调用方自己的信息时不需要权限。 |
| [getAbilityLabel](arkts-ability-getabilitylabel-f.md#getabilitylabel-2) | 通过Bundle名称和ability名称获取应用名称，使用Promise异步回调。获取调用方自己的信息时不需要权限。 |
| [getAllApplicationInfo](arkts-ability-getallapplicationinfo-f.md#getallapplicationinfo-1) | 获取指定用户下所有已安装的应用信息，使用callback异步回调。 |
| [getAllApplicationInfo](arkts-ability-getallapplicationinfo-f.md#getallapplicationinfo-2) | 获取调用方所在用户下已安装的应用信息，使用callback异步回调。 |
| [getAllApplicationInfo](arkts-ability-getallapplicationinfo-f.md#getallapplicationinfo-3) | 获取指定用户下所有已安装的应用信息，使用promise异步回调。 |
| [getAllBundleInfo](arkts-ability-getallbundleinfo-f.md#getallbundleinfo-1) | 获取系统中指定用户下所有的BundleInfo，使用callback异步回调。 |
| [getAllBundleInfo](arkts-ability-getallbundleinfo-f.md#getallbundleinfo-2) | 获取当前用户所有的BundleInfo，使用callback异步回调。 |
| [getAllBundleInfo](arkts-ability-getallbundleinfo-f.md#getallbundleinfo-3) | 获取指定用户所有的BundleInfo，使用Promise形式异步回调。 |
| [getApplicationInfo](arkts-ability-getapplicationinfo-f.md#getapplicationinfo-1) | 根据给定的Bundle名称获取指定用户下的ApplicationInfo，使用callback异步回调。获取调用方自己的信息时不需要权限。 |
| [getApplicationInfo](arkts-ability-getapplicationinfo-f.md#getapplicationinfo-2) | 根据给定的Bundle名称获取ApplicationInfo，使用callback异步回调。获取调用方自己的信息时不需要权限。 |
| [getApplicationInfo](arkts-ability-getapplicationinfo-f.md#getapplicationinfo-3) | 根据给定的Bundle名称获取ApplicationInfo。使用Promise异步回调。获取调用方自己的信息时不需要权限。 |
| [getBundleArchiveInfo](arkts-ability-getbundlearchiveinfo-f.md#getbundlearchiveinfo-1) | 获取有关HAP中包含的应用程序包的信息，使用callback异步回调。 |
| [getBundleArchiveInfo](arkts-ability-getbundlearchiveinfo-f.md#getbundlearchiveinfo-2) | 获取有关HAP中包含的应用程序包的信息，使用Promise异步回调。 |
| [getBundleInfo](arkts-ability-getbundleinfo-f.md#getbundleinfo-1) | 根据给定的Bundle名称获取BundleInfo，使用callback异步回调。获取调用方自己的信息时不需要权限。 |
| [getBundleInfo](arkts-ability-getbundleinfo-f.md#getbundleinfo-2) | 根据给定的Bundle名称获取BundleInfo，使用callback异步回调。获取调用方自己的信息时不需要权限。 |
| [getBundleInfo](arkts-ability-getbundleinfo-f.md#getbundleinfo-3) | 根据给定的Bundle名称获取BundleInfo，使用Promise异步回调。获取调用方自己的信息时不需要权限。 |
| [getLaunchWantForBundle](arkts-ability-getlaunchwantforbundle-f.md#getlaunchwantforbundle-1) | 查询拉起指定应用的want对象，使用callback异步回调。 |
| [getLaunchWantForBundle](arkts-ability-getlaunchwantforbundle-f.md#getlaunchwantforbundle-2) | 查询拉起指定应用的want对象，使用Promise异步回调。 |
| [getNameForUid](arkts-ability-getnameforuid-f.md#getnameforuid-1) |  |
| [getNameForUid](arkts-ability-getnameforuid-f.md#getnameforuid-2) | 通过uid获取对应的Bundle名称，使用Promise异步回调。 |
| [isAbilityEnabled](arkts-ability-isabilityenabled-f.md#isabilityenabled-1) | 根据给定的AbilityInfo查询ability是否已经启用，使用callback异步回调。 |
| [isAbilityEnabled](arkts-ability-isabilityenabled-f.md#isabilityenabled-2) | 根据给定的AbilityInfo查询ability是否已经启用，使用Promise异步回调。 |
| [isApplicationEnabled](arkts-ability-isapplicationenabled-f.md#isapplicationenabled-1) | 根据给定的bundleName查询指定应用程序是否已经启用，使用callback异步回调。 |
| [isApplicationEnabled](arkts-ability-isapplicationenabled-f.md#isapplicationenabled-2) | 根据给定的bundleName查询指定应用程序是否已经启用，使用Promise异步回调。 |
| [queryAbilityByWant](arkts-ability-queryabilitybywant-f.md#queryabilitybywant-1) | 根据给定的意图获取指定用户下Ability信息，使用callback异步回调。获取调用方自己的信息时不需要权限。 |
| [queryAbilityByWant](arkts-ability-queryabilitybywant-f.md#queryabilitybywant-2) | 根据给定的意图获取Ability信息，使用callback异步回调。获取调用方自己的信息时不需要权限。 |
| [queryAbilityByWant](arkts-ability-queryabilitybywant-f.md#queryabilitybywant-3) | 根据给定的意图获取Ability组件信息，使用Promise异步回调。获取调用方自己的信息时不需要权限。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [cleanBundleCacheFiles](arkts-ability-cleanbundlecachefiles-f-sys.md#cleanbundlecachefiles-1) | 清除指定应用程序的缓存数据，使用callback异步回调。 |
| [cleanBundleCacheFiles](arkts-ability-cleanbundlecachefiles-f-sys.md#cleanbundlecachefiles-2) | 清除指定应用程序的缓存数据，使用Promise异步回调。 |
| [getBundleInstaller](arkts-ability-getbundleinstaller-f-sys.md#getbundleinstaller-1) | 获取用于安装包的接口，使用callback异步回调。 |
| [getBundleInstaller](arkts-ability-getbundleinstaller-f-sys.md#getbundleinstaller-2) | 获取用于安装包的接口，使用Promise异步回调，返回安装接口对象。 |
| [getPermissionDef](arkts-ability-getpermissiondef-f-sys.md#getpermissiondef-1) | 按权限名称获取权限的详细信息，使用callback异步回调。 |
| [getPermissionDef](arkts-ability-getpermissiondef-f-sys.md#getpermissiondef-2) | 按权限名称获取权限的详细信息，使用promise异步回调。 |
| [setAbilityEnabled](arkts-ability-setabilityenabled-f-sys.md#setabilityenabled-1) | 设置是否启用指定的Ability组件，使用callback异步回调。 |
| [setAbilityEnabled](arkts-ability-setabilityenabled-f-sys.md#setabilityenabled-2) | 设置是否启用指定的Ability组件，使用Promise异步回调。 |
| [setApplicationEnabled](arkts-ability-setapplicationenabled-f-sys.md#setapplicationenabled-1) | 设置是否启用指定的应用程序，使用callback异步回调。 |
| [setApplicationEnabled](arkts-ability-setapplicationenabled-f-sys.md#setapplicationenabled-2) | 设置是否启用指定的应用程序，使用Promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [BundleOptions](arkts-ability-bundleoptions-i.md) |  |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AbilitySubType](arkts-ability-abilitysubtype-e.md) |  |
| [AbilityType](arkts-ability-abilitytype-e.md) | @link @ohos.bundle.bundleManager:bundleManager.AbilityType}替代。Ability组件类型。 |
| [BundleFlag](arkts-ability-bundleflag-e.md) | @link @ohos.bundle.bundleManager:bundleManager.BundleFlag}替代。包信息标志，指示需要获取的包信息的内容。当接口与标志不匹配时，该标志会被忽略，例如获取application时使用GET_ABILITY_INFO_WITH_PERMISSION对结果不会产生影响。标志可以叠加使用，例如使用GET_APPLICATION_INFO_WITH_PERMISSION + GET_APPLICATION_INFO_WITH_DISABLE可以使结果同时包含应用权限信息和被禁用的应用信息。 |
| [ColorMode](arkts-ability-colormode-e.md) |  |
| [DisplayOrientation](arkts-ability-displayorientation-e.md) | @link @ohos.bundle.bundleManager:bundleManager.DisplayOrientation}替代。屏幕显示方向。 |
| [GrantStatus](arkts-ability-grantstatus-e.md) | @link @ohos.bundle.bundleManager:bundleManager.PermissionGrantState}替代。权限授予状态。 |
| [InstallErrorCode](arkts-ability-installerrorcode-e.md) |  |
| [LaunchMode](arkts-ability-launchmode-e.md) | @link @ohos.bundle.bundleManager:bundleManager.LaunchType}替代。Ability组件的启动模式。 |

