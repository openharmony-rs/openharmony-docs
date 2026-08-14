# @ohos.bundle.bundleManager

本模块提供应用信息的查询能力，支持应用包信息BundleInfo、应用程序信息 ApplicationInfo、UIAbility组件信息 AbilityInfo、ExtensionAbility组件信息 [ExtensionAbilityInfo](arkts-ability-extensionabilityinfo-i.md#ExtensionAbilityInfo)等信息的查询。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace bundleManager--><!--Device-unnamed-declare namespace bundleManager-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [canOpenLink](arkts-ability-bundlemanager-canopenlink-f.md#canOpenLink) | 根据给定的链接判断目标应用是否可访问，链接中的scheme需要在[module.json5文件](../../../quick-start/module-configuration-file.md)的querySchemes字段 下配置。 |
| [cleanBundleCacheFilesForSelf](arkts-ability-bundlemanager-cleanbundlecachefilesforself-f.md#cleanBundleCacheFilesForSelf) | 清理应用自身的缓存。使用Promise异步回调。 |
| [getAbilityInfo](arkts-ability-bundlemanager-getabilityinfo-f.md#getAbilityInfo) | 获取指定资源标识符和组件信息标志对应的Ability信息。使用Promise异步回调。 |
| [getAlternateIcons](arkts-ability-bundlemanager-getalternateicons-f.md#getAlternateIcons) | 查询当前应用在app.json5中[alternateIcons标签](../../../quick-start/app-configuration-file.md#alternateicons标签)配置的备用图标信息。使用 Promise异步回调。 |
| [getAppCloneIdentity](arkts-ability-bundlemanager-getappcloneidentity-f.md#getAppCloneIdentity) | 根据uid查询分身应用的包名和分身索引。使用Promise异步回调。 |
| [getApplicationLabel](arkts-ability-bundlemanager-getapplicationlabel-f.md#getApplicationLabel) | 获取指定包名和分身索引的应用名称。使用Promise异步回调。 |
| [getBundleInfo](arkts-ability-bundlemanager-getbundleinfo-f.md#getBundleInfo) | 根据给定的bundleName和bundleFlags获取BundleInfo。使用callback异步回调。 获取调用方自身的信息时不需要权限。 |
| [getBundleInfo](arkts-ability-bundlemanager-getbundleinfo-f.md#getBundleInfo) | 根据给定的bundleName、bundleFlags和userId获取BundleInfo。使用callback异步回调。 获取调用方自身信息时不需要权限。 |
| [getBundleInfo](arkts-ability-bundlemanager-getbundleinfo-f.md#getBundleInfo) | 根据给定的bundleName、bundleFlags和userId获取BundleInfo。使用Promise异步回调。 获取调用方自身的信息时不需要权限。 |
| [getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md#getBundleInfoForSelf) | 根据给定的bundleFlags获取当前应用的BundleInfo。使用Promise异步回调。 |
| [getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md#getBundleInfoForSelf) | 根据给定的bundleFlags获取当前应用的BundleInfo。使用callback异步回调。 |
| [getBundleInfoForSelfSync](arkts-ability-bundlemanager-getbundleinfoforselfsync-f.md#getBundleInfoForSelfSync) | 以同步方法根据给定的bundleFlags获取当前应用的BundleInfo。 |
| [getBundleInfoSync](arkts-ability-bundlemanager-getbundleinfosync-f.md#getBundleInfoSync) | 以同步方法根据给定的bundleName、bundleFlags和userId获取BundleInfo。 获取调用方自身的信息时不需要权限。 |
| [getBundleInfoSync](arkts-ability-bundlemanager-getbundleinfosync-f.md#getBundleInfoSync) | 以同步方法根据给定的bundleName、bundleFlags获取调用方所在用户下的BundleInfo。 获取调用方自身的信息时不需要权限。 |
| [getBundleNameByUid](arkts-ability-bundlemanager-getbundlenamebyuid-f.md#getBundleNameByUid) | 根据给定的uid获取对应应用的bundleName。使用callback异步回调。 |
| [getBundleNameByUid](arkts-ability-bundlemanager-getbundlenamebyuid-f.md#getBundleNameByUid) | 根据给定的uid获取对应应用的bundleName。使用Promise异步回调。 |
| [getBundleNameByUidSync](arkts-ability-bundlemanager-getbundlenamebyuidsync-f.md#getBundleNameByUidSync) | 以同步方法根据给定的uid获取对应应用的bundleName。 |
| [getInstalledBundleList](arkts-ability-bundlemanager-getinstalledbundlelist-f.md#getInstalledBundleList) | 根据给定的bundleFlags获取系统中所有的BundleInfo。使用Promise异步回调。 |
| [getLaunchWant](arkts-ability-bundlemanager-getlaunchwant-f.md#getLaunchWant) | 获取本应用[入口UIAbility](../../../quick-start/application-package-glossary.md#uiability)的Want参数。 |
| [getPluginBundlePathForSelf](arkts-ability-bundlemanager-getpluginbundlepathforself-f.md#getPluginBundlePathForSelf) | 获取指定插件在当前[应用沙箱](../../../file-management/app-sandbox-directory.md)内的安装路径。 |
| [getProfileByAbility](arkts-ability-bundlemanager-getprofilebyability-f.md#getProfileByAbility) | 根据给定的moduleName、abilityName和metadataName（module.json5中 [abilities标签](../../../quick-start/module-configuration-file.md#abilities标签)下的metadata标签的name）获取自身相应配置文件的json格式字符串 。使用callback异步回调。 > 说明： > > 如果配置文件信息采用了资源引用格式，则返回值将保持资源引用格式（例如 \\$string:res_id），开发者可以通过[资源管理](../../apis-localization-kit/arkts-apis/arkts-resourcemanager.md#@ohos.resourceManager)的相 > 关接口，来获取引用的资源。 |
| [getProfileByAbility](arkts-ability-bundlemanager-getprofilebyability-f.md#getProfileByAbility) | 根据给定的moduleName、abilityName和metadataName（module.json5中 [abilities标签](../../../quick-start/module-configuration-file.md#abilities标签)下的metadata标签的name）获取自身相应配置文件的json格式字符串 。使用Promise异步回调。 > 说明： > > 如果配置文件信息采用了资源引用格式，则返回值将保持资源引用格式（例如 \\$string:res_id），开发者可以通过[资源管理](../../apis-localization-kit/arkts-apis/arkts-resourcemanager.md#@ohos.resourceManager)的相 > 关接口，来获取引用的资源。 |
| [getProfileByAbilitySync](arkts-ability-bundlemanager-getprofilebyabilitysync-f.md#getProfileByAbilitySync) | 以同步方法根据给定的moduleName、abilityName和metadataName（module.json5中 [metadata标签](../../../quick-start/module-configuration-file.md#metadata标签)下的name）获取自身相应配置文件的json格式字符串，返回对象为string数 组。 |
| [getProfileByExtensionAbility](arkts-ability-bundlemanager-getprofilebyextensionability-f.md#getProfileByExtensionAbility) | 根据给定的moduleName、extensionAbilityName和metadataName（module.json5中 [metadata标签](../../../quick-start/module-configuration-file.md#metadata标签)下的name）获取自身相应配置文件的json格式字符串。使用callback异步 回调。 |
| [getProfileByExtensionAbility](arkts-ability-bundlemanager-getprofilebyextensionability-f.md#getProfileByExtensionAbility) | 根据给定的moduleName、extensionAbilityName和metadataName（module.json5中 [metadata标签](../../../quick-start/module-configuration-file.md#metadata标签)下的name）获取自身相应配置文件的json格式字符串。使用Promise异步回 调。 |
| [getProfileByExtensionAbilitySync](arkts-ability-bundlemanager-getprofilebyextensionabilitysync-f.md#getProfileByExtensionAbilitySync) | 以同步方法根据给定的moduleName、extensionAbilityName和metadataName（module.json5中 [metadata标签](../../../quick-start/module-configuration-file.md#metadata标签)下的name）获取自身相应配置文件的json格式字符串，返回对象为string数 组。 |
| [getSignatureInfo](arkts-ability-bundlemanager-getsignatureinfo-f.md#getSignatureInfo) | 根据给定的uid获取对应应用的[签名信息](arkts-ability-bundleinfo-signatureinfo-i.md#SignatureInfo)。 |
| [setAlternateIcon](arkts-ability-bundlemanager-setalternateicon-f.md#setAlternateIcon) | 根据给定的备用图标名称设置调用方自身的备用图标。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [cleanAllBundleCache](arkts-ability-bundlemanager-cleanallbundlecache-f-sys.md#cleanAllBundleCache) | 清理全局缓存。使用Promise异步回调。 |
| [cleanBundleCacheFiles](arkts-ability-bundlemanager-cleanbundlecachefiles-f-sys.md#cleanBundleCacheFiles) | 根据给定的bundleName清理BundleCache。使用callback异步回调。 调用方清理自身缓存数据时不需要权限。 |
| [cleanBundleCacheFiles](arkts-ability-bundlemanager-cleanbundlecachefiles-f-sys.md#cleanBundleCacheFiles（系统接口）) | 根据给定的bundleName清理BundleCache。使用Promise异步回调。 调用方清理自身缓存数据时不需要权限。 |
| [cleanBundleCacheFiles](arkts-ability-bundlemanager-cleanbundlecachefiles-f-sys.md#cleanBundleCacheFiles（系统接口）) | 根据给定的bundleName和appIndex清理BundleCache。使用Promise异步回调。 调用方清理自身缓存数据时不需要权限。 |
| [deleteAbc](arkts-ability-bundlemanager-deleteabc-f-sys.md#deleteAbc) | 根据给定的abcPath删除.abc文件。使用Promise异步回调。 |
| [disableDynamicIcon](arkts-ability-bundlemanager-disabledynamicicon-f-sys.md#disableDynamicIcon) | 根据给定的bundleName禁用动态图标。使用Promise异步回调。 |
| [disableDynamicIcon](arkts-ability-bundlemanager-disabledynamicicon-f-sys.md#disableDynamicIcon（系统接口）) | 根据给定的bundleName和option禁用动态图标。使用Promise异步回调。 禁用当前用户下的动态图标信息时需要申请权限ohos.permission.ACCESS_DYNAMIC_ICON。 禁用其他用户下的动态图标信息时需要申请权限ohos.permission.ACCESS_DYNAMIC_ICON 和 ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS。 |
| [enableDynamicIcon](arkts-ability-bundlemanager-enabledynamicicon-f-sys.md#enableDynamicIcon) | 根据给定的bundleName、moduleName使能动态图标。使用Promise异步回调。 |
| [enableDynamicIcon](arkts-ability-bundlemanager-enabledynamicicon-f-sys.md#enableDynamicIcon（系统接口）) | 根据给定的bundleName、moduleName和option使能动态图标。使用Promise异步回调。 使能当前用户下的动态图标信息时需要申请权限ohos.permission.ACCESS_DYNAMIC_ICON。 使能其他用户下的动态图标信息时需要申请权限ohos.permission.ACCESS_DYNAMIC_ICON 和 ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS。 |
| [getAbilityIcon](arkts-ability-bundlemanager-getabilityicon-f-sys.md#getAbilityIcon) | 通过bundleName、moduleName和abilityName获取对应Icon的[PixelMap](../../apis-image-kit/arkts-apis/arkts-multimedia-image.md#@ohos.multimedia.image)，使用callback异步回调。 获取调用方信息时不需要权限。 |
| [getAbilityIcon](arkts-ability-bundlemanager-getabilityicon-f-sys.md#getAbilityIcon（系统接口）) | 通过bundleName、moduleName和abilityName获取对应Icon的[PixelMap](../../apis-image-kit/arkts-apis/arkts-multimedia-image.md#@ohos.multimedia.image)，使用Promise异步回调。 获取调用方信息时不需要权限。 |
| [getAbilityLabel](arkts-ability-bundlemanager-getabilitylabel-f-sys.md#getAbilityLabel) | 获取指定bundleName、moduleName和abilityName的label。使用callback异步回调。 获取调用方自身的信息时不需要权限。 |
| [getAbilityLabel](arkts-ability-bundlemanager-getabilitylabel-f-sys.md#getAbilityLabel（系统接口）) | 获取指定bundleName、moduleName和abilityName的label。使用Promise异步回调。 获取调用方自身的信息时不需要权限。 |
| [getAbilityLabelSync](arkts-ability-bundlemanager-getabilitylabelsync-f-sys.md#getAbilityLabelSync) | 以同步的方法获取指定bundleName、moduleName和abilityName的label。 获取调用方自身的信息时不需要权限。 |
| [getAdditionalInfo](arkts-ability-bundlemanager-getadditionalinfo-f-sys.md#getAdditionalInfo) | 以同步接口查询指定bundleName的额外信息。该返回值是在调用install接口时传入的[InstallParam](arkts-ability-installer-installparam-i-sys.md#InstallParam（系统接口）)中的 additionalInfo字段。 |
| [getAllAppCloneBundleInfo](arkts-ability-bundlemanager-getallappclonebundleinfo-f-sys.md#getAllAppCloneBundleInfo) | 根据bundleName、[bundleFlags](arkts-ability-bundlemanager-bundleflag-e.md#BundleFlag)以及用户ID查询主应用和分身应用的BundleInfo列表。 使用Promise异步回调。 获取调用方自身的信息时不需要权限。 |
| [getAllAppProvisionInfo](arkts-ability-bundlemanager-getallappprovisioninfo-f-sys.md#getAllAppProvisionInfo) | 根据userId获取指定用户下所有应用的Provision配置文件信息。使用Promise异步回调。 |
| [getAllApplicationInfo](arkts-ability-bundlemanager-getallapplicationinfo-f-sys.md#getAllApplicationInfo) | 根据给定的appFlags获取系统中所有的ApplicationInfo。使用callback异步回调。 |
| [getAllApplicationInfo](arkts-ability-bundlemanager-getallapplicationinfo-f-sys.md#getAllApplicationInfo（系统接口）) | 根据给定的appFlags和userId获取系统中所有的ApplicationInfo。使用callback异步回调。 |
| [getAllApplicationInfo](arkts-ability-bundlemanager-getallapplicationinfo-f-sys.md#getAllApplicationInfo（系统接口）) | 根据给定的appFlags和userId获取系统中所有的ApplicationInfo。使用Promise异步回调。 |
| [getAllBundleCacheSize](arkts-ability-bundlemanager-getallbundlecachesize-f-sys.md#getAllBundleCacheSize) | 获取全局缓存大小，单位：字节。使用Promise异步回调。 有程序运行时的应用的缓存、或者在[应用配置指南](../../../../device-dev/subsystems/subsys-app-privilege-config-guide.md)中已配置“ AllowAppDataNotCleared”特权的应用的缓存，无法被获取。 |
| [getAllBundleInfo](arkts-ability-bundlemanager-getallbundleinfo-f-sys.md#getAllBundleInfo) | 根据给定的bundleFlags获取系统中所有的BundleInfo。使用callback异步回调。 |
| [getAllBundleInfo](arkts-ability-bundlemanager-getallbundleinfo-f-sys.md#getAllBundleInfo（系统接口）) | 根据给定的bundleFlags和userId获取系统中所有的BundleInfo。使用callback异步回调。 |
| [getAllBundleInfo](arkts-ability-bundlemanager-getallbundleinfo-f-sys.md#getAllBundleInfo（系统接口）) | 根据给定的bundleFlags和userId获取系统中所有的BundleInfo。使用Promise异步回调。 |
| [getAllBundleInfoByDeveloperId](arkts-ability-bundlemanager-getallbundleinfobydeveloperid-f-sys.md#getAllBundleInfoByDeveloperId) | 根据给定的developerId获取当前用户下的包信息列表。 |
| [getAllBundleInstallInfo](arkts-ability-bundlemanager-getallbundleinstallinfo-f-sys.md#getAllBundleInstallInfo) | 获取系统内所有应用的扩展安装信息。使用Promise异步回调。 |
| [getAllBundleInstallInfo](arkts-ability-bundlemanager-getallbundleinstallinfo-f-sys.md#getAllBundleInstallInfo（系统接口）) | 获取系统内所有应用的扩展安装信息。使用Promise异步回调。 |
| [getAllDynamicIconInfo](arkts-ability-bundlemanager-getalldynamiciconinfo-f-sys.md#getAllDynamicIconInfo) | 查询指定用户下所有应用和所有分身的动态图标信息。使用Promise异步回调。 查询当前用户下所有应用和所有分身的动态图标信息时需要申请权限ohos.permission.GET_BUNDLE_INFO_PRIVILEGED。 查询其他用户或者所有用户下所有应用和所有分身的动态图标信息时需要申请权限ohos.permission.GET_BUNDLE_INFO_PRIVILEGED 和 ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS。 |
| [getAllNewPreinstalledApplicationInfo](arkts-ability-bundlemanager-getallnewpreinstalledapplicationinfo-f-sys.md#getAllNewPreinstalledApplicationInfo) | 获取设备OTA升级期间当前用户下新增的所有预置应用信息。使用Promise异步回调。 |
| [getAllPluginInfo](arkts-ability-bundlemanager-getallplugininfo-f-sys.md#getAllPluginInfo) | 根据给定的hostBundleName和userId获取所有的PluginBundleInfo。使用Promise异步回调。 |
| [getAllPreinstalledApplicationInfo](arkts-ability-bundlemanager-getallpreinstalledapplicationinfo-f-sys.md#getAllPreinstalledApplicationInfo) | 获取所有预置应用信息。使用Promise异步回调。 |
| [getAllSharedBundleInfo](arkts-ability-bundlemanager-getallsharedbundleinfo-f-sys.md#getAllSharedBundleInfo) | 获取所有的共享包信息。使用callback异步回调。 |
| [getAllSharedBundleInfo](arkts-ability-bundlemanager-getallsharedbundleinfo-f-sys.md#getAllSharedBundleInfo（系统接口）) | 获取所有的共享包信息。使用Promise异步回调。 |
| [getAppCloneBundleInfo](arkts-ability-bundlemanager-getappclonebundleinfo-f-sys.md#getAppCloneBundleInfo) | 根据bundleName、分身索引、[bundleFlags](arkts-ability-bundlemanager-bundleflag-e.md#BundleFlag)以及用户ID查询主应用或分身应用的 BundleInfo。使用Promise异步回调。 获取调用方自身的信息时不需要权限。 |
| [getAppCloneIdentityBySandboxDataDir](arkts-ability-bundlemanager-getappcloneidentitybysandboxdatadir-f-sys.md#getAppCloneIdentityBySandboxDataDir) | 根据应用的沙箱目录名称获取应用的身份信息，包括应用包名和分身索引信息。 |
| [getAppProvisionInfo](arkts-ability-bundlemanager-getappprovisioninfo-f-sys.md#getAppProvisionInfo) | 获取指定bundleName的provision配置文件信息。使用callback异步回调。 获取调用方自身的信息时不需要权限。 |
| [getAppProvisionInfo](arkts-ability-bundlemanager-getappprovisioninfo-f-sys.md#getAppProvisionInfo（系统接口）) | 获取指定bundleName和userId的provision配置文件信息。使用callback异步回调。 获取调用方自身的信息时不需要权限。 |
| [getAppProvisionInfo](arkts-ability-bundlemanager-getappprovisioninfo-f-sys.md#getAppProvisionInfo（系统接口）) | 根据bundleName和userId获取应用的provision配置文件信息。使用Promise异步回调。 获取调用方自身的信息时不需要权限。 |
| [getAppProvisionInfoSync](arkts-ability-bundlemanager-getappprovisioninfosync-f-sys.md#getAppProvisionInfoSync) | 以同步方法根据bundleName和userId获取应用的provision配置文件信息并返回结果。 获取调用方自身的信息时不需要权限。 |
| [getApplicationInfo](arkts-ability-bundlemanager-getapplicationinfo-f-sys.md#getApplicationInfo) | 根据给定的bundleName和appFlags获取ApplicationInfo。使用callback异步回调。 获取调用方自身的信息时不需要权限。 |
| [getApplicationInfo](arkts-ability-bundlemanager-getapplicationinfo-f-sys.md#getApplicationInfo（系统接口）) | 根据给定的bundleName、appFlags和userId获取ApplicationInfo。使用callback异步回调。 获取调用方自身的信息时不需要权限。 |
| [getApplicationInfo](arkts-ability-bundlemanager-getapplicationinfo-f-sys.md#getApplicationInfo（系统接口）) | 根据给定的bundleName、appFlags和userId获取ApplicationInfo。使用Promise异步回调。 获取调用方自身的信息时不需要权限。 |
| [getApplicationInfoSync](arkts-ability-bundlemanager-getapplicationinfosync-f-sys.md#getApplicationInfoSync) | 以同步方法根据给定的bundleName、applicationFlags和userId获取ApplicationInfo。 获取调用方自身的信息时不需要权限。 |
| [getApplicationInfoSync](arkts-ability-bundlemanager-getapplicationinfosync-f-sys.md#getApplicationInfoSync（系统接口）) | 以同步方法根据给定的bundleName、applicationFlags获取ApplicationInfo。 获取调用方自身的信息时不需要权限。 |
| [getBundleArchiveInfo](arkts-ability-bundlemanager-getbundlearchiveinfo-f-sys.md#getBundleArchiveInfo) | 根据给定的hapFilePath和bundleFlags获取BundleInfo。使用callback异步回调。 |
| [getBundleArchiveInfo](arkts-ability-bundlemanager-getbundlearchiveinfo-f-sys.md#getBundleArchiveInfo（系统接口）) | 根据给定的hapFilePath和bundleFlags获取BundleInfo。使用Promise异步回调。 |
| [getBundleArchiveInfoSync](arkts-ability-bundlemanager-getbundlearchiveinfosync-f-sys.md#getBundleArchiveInfoSync) | 以同步方法根据给定的hapFilePath和bundleFlags获取BundleInfo对象。 |
| [getBundleInstallStatus](arkts-ability-bundlemanager-getbundleinstallstatus-f-sys.md#getBundleInstallStatus) | 查询当前用户下指定应用的安装状态。 |
| [getDeveloperIds](arkts-ability-bundlemanager-getdeveloperids-f-sys.md#getDeveloperIds) | 根据给定的应用[appDistributionType](arkts-ability-bundlemanager-appdistributiontype-e-sys.md#AppDistributionType（系统接口）)获取当前用户下的所有开发者ID列表。 |
| [getDynamicIcon](arkts-ability-bundlemanager-getdynamicicon-f-sys.md#getDynamicIcon) | 根据给定的bundleName获得动态图标对应的moduleName。使用Promise异步回调。 |
| [getDynamicIconInfo](arkts-ability-bundlemanager-getdynamiciconinfo-f-sys.md#getDynamicIconInfo) | 根据指定的bundleName获取所有用户和所有分身下的动态图标信息。使用Promise异步回调。 |
| [getExtResource](arkts-ability-bundlemanager-getextresource-f-sys.md#getExtResource) | 根据给定的bundleName获得扩展资源对应的moduleNames。使用Promise异步回调。 |
| [getJsonProfile](arkts-ability-bundlemanager-getjsonprofile-f-sys.md#getJsonProfile) | 以同步的方法根据给定的profileType、bundleName和moduleName查询相应配置文件的JSON字符串。 获取调用方自己的配置文件时不需要权限。 |
| [getLaunchWantForBundle](arkts-ability-bundlemanager-getlaunchwantforbundle-f-sys.md#getLaunchWantForBundle) | 根据给定的bundleName和userId获取用于启动应用程序的Want参数。使用callback异步回调。 |
| [getLaunchWantForBundle](arkts-ability-bundlemanager-getlaunchwantforbundle-f-sys.md#getLaunchWantForBundle（系统接口）) | 根据给定的bundleName获取用于启动应用程序的Want参数。使用callback异步回调。 |
| [getLaunchWantForBundle](arkts-ability-bundlemanager-getlaunchwantforbundle-f-sys.md#getLaunchWantForBundle（系统接口）) | 根据给定的bundleName和userId获取用于启动应用程序的Want参数。使用Promise异步回调。 |
| [getLaunchWantForBundleSync](arkts-ability-bundlemanager-getlaunchwantforbundlesync-f-sys.md#getLaunchWantForBundleSync) | 根据给定的包名和用户ID，获取用于启动应用程序的Want参数。 |
| [getPermissionDef](arkts-ability-bundlemanager-getpermissiondef-f-sys.md#getPermissionDef) | 根据给定的permissionName获取权限定义结构体PermissionDef信息。使用callback异步回调。 |
| [getPermissionDef](arkts-ability-bundlemanager-getpermissiondef-f-sys.md#getPermissionDef（系统接口）) | 根据给定的permissionName获取权限定义结构体PermissionDef信息。使用Promise异步回调。 |
| [getPermissionDefSync](arkts-ability-bundlemanager-getpermissiondefsync-f-sys.md#getPermissionDefSync) | 以同步方法根据给定的permissionName获取权限定义结构体PermissionDef信息。 |
| [getRecoverableApplicationInfo](arkts-ability-bundlemanager-getrecoverableapplicationinfo-f-sys.md#getRecoverableApplicationInfo) | 获取所有可恢复的预置应用信息。使用callback异步回调。 |
| [getRecoverableApplicationInfo](arkts-ability-bundlemanager-getrecoverableapplicationinfo-f-sys.md#getRecoverableApplicationInfo（系统接口）) | 获取所有可恢复的预置应用信息。使用Promise异步回调。 |
| [getSandboxDataDir](arkts-ability-bundlemanager-getsandboxdatadir-f-sys.md#getSandboxDataDir) | 根据应用包名和分身索引获取对应的沙箱目录。 |
| [getSharedBundleInfo](arkts-ability-bundlemanager-getsharedbundleinfo-f-sys.md#getSharedBundleInfo) | 获取指定的共享包信息。使用callback异步回调。 获取调用方自身的信息时不需要权限。 |
| [getSharedBundleInfo](arkts-ability-bundlemanager-getsharedbundleinfo-f-sys.md#getSharedBundleInfo（系统接口）) | 获取指定的共享包信息。使用Promise异步回调。 获取调用方自身的信息时不需要权限。 |
| [getSpecifiedDistributionType](arkts-ability-bundlemanager-getspecifieddistributiontype-f-sys.md#getSpecifiedDistributionType) | 以同步的方法查询指定bundleName的[HarmonyAppProvision配置文件说明](../../../security/app-provision-structure.md)，该返回值是在调用install接口时传 入的[InstallParam](arkts-ability-installer-installparam-i-sys.md#InstallParam（系统接口）)中的specifiedDistributionType字段。 获取调用方自身的信息时不需要权限。 |
| [isAbilityEnabled](arkts-ability-bundlemanager-isabilityenabled-f-sys.md#isAbilityEnabled) | 获取应用或指定分身应用组件的禁用或使能状态。使用Promise异步回调。 |
| [isAbilityEnabled](arkts-ability-bundlemanager-isabilityenabled-f-sys.md#isAbilityEnabled（系统接口）) | 获取指定组件的禁用或使能状态。使用callback异步回调。 |
| [isAbilityEnabled](arkts-ability-bundlemanager-isabilityenabled-f-sys.md#isAbilityEnabled（系统接口）) | 获取指定组件的禁用或使能状态。使用Promise异步回调。 |
| [isAbilityEnabledSync](arkts-ability-bundlemanager-isabilityenabledsync-f-sys.md#isAbilityEnabledSync) | 以同步方法获取指定组件的禁用或使能状态。 |
| [isApplicationDisableForbidden](arkts-ability-bundlemanager-isapplicationdisableforbidden-f-sys.md#isApplicationDisableForbidden) | 以同步方法查询指定用户下指定应用或分身应用是否被设置禁止停用。 |
| [isApplicationEnabled](arkts-ability-bundlemanager-isapplicationenabled-f-sys.md#isApplicationEnabled) | 获取指定应用或分身应用的禁用或使能状态。使用Promise异步回调。 |
| [isApplicationEnabled](arkts-ability-bundlemanager-isapplicationenabled-f-sys.md#isApplicationEnabled（系统接口）) | 获取指定应用的禁用或使能状态。使用callback异步回调。 |
| [isApplicationEnabled](arkts-ability-bundlemanager-isapplicationenabled-f-sys.md#isApplicationEnabled（系统接口）) | 获取指定应用的禁用或使能状态。使用Promise异步回调。 |
| [isApplicationEnabledSync](arkts-ability-bundlemanager-isapplicationenabledsync-f-sys.md#isApplicationEnabledSync) | 以同步方法获取指定应用的禁用或使能状态。 |
| [migrateData](arkts-ability-bundlemanager-migratedata-f-sys.md#migrateData) | 拷贝文件，将文件从源路径拷贝到目标路径。使用Promise异步回调。 |
| [queryAbilityInfo](arkts-ability-bundlemanager-queryabilityinfo-f-sys.md#queryAbilityInfo) | 根据给定的want和abilityFlags获取一个或多个AbilityInfo。使用callback异步回调。 获取调用方自身的信息时不需要权限。 |
| [queryAbilityInfo](arkts-ability-bundlemanager-queryabilityinfo-f-sys.md#queryAbilityInfo（系统接口）) | 根据给定的want、abilityFlags和userId获取多个AbilityInfo。使用callback异步回调。 获取调用方自身的信息时不需要权限。 |
| [queryAbilityInfo](arkts-ability-bundlemanager-queryabilityinfo-f-sys.md#queryAbilityInfo（系统接口）) | 根据给定的want、abilityFlags和userId获取一个或多个AbilityInfo。使用Promise异步回调。 获取调用方自身的信息时不需要权限。 |
| [queryAbilityInfo](arkts-ability-bundlemanager-queryabilityinfo-f-sys.md#queryAbilityInfo（系统接口）) | 根据给定的want列表、abilityFlags和userId获取一个或多个AbilityInfo。使用Promise异步回调。 获取调用方自身的信息时不需要权限。 |
| [queryAbilityInfoSync](arkts-ability-bundlemanager-queryabilityinfosync-f-sys.md#queryAbilityInfoSync) | 以同步方法根据给定的want、abilityFlags和userId获取一个或多个AbilityInfo。 获取调用方自身的信息时不需要权限。 |
| [queryExtensionAbilityInfo](arkts-ability-bundlemanager-queryextensionabilityinfo-f-sys.md#queryExtensionAbilityInfo) | 根据给定的want、extensionAbilityType和extensionAbilityFlags获取一个或多个ExtensionAbilityInfo。使用callback异步回调。 获取调用方自身的信息时不需要权限。 |
| [queryExtensionAbilityInfo](arkts-ability-bundlemanager-queryextensionabilityinfo-f-sys.md#queryExtensionAbilityInfo（系统接口）) | 根据给定的want、extensionAbilityType、extensionAbilityFlags和userId获取一个或多个ExtensionAbilityInfo。使用callback异步回调。 获取调用方自身的信息时不需要权限。 |
| [queryExtensionAbilityInfo](arkts-ability-bundlemanager-queryextensionabilityinfo-f-sys.md#queryExtensionAbilityInfo（系统接口）) | 根据给定的want、extensionAbilityType、extensionAbilityFlags和userId获取ExtensionAbilityInfo。使用Promise异步回调。 获取调用方自身的信息时不需要权限。 |
| [queryExtensionAbilityInfoSync](arkts-ability-bundlemanager-queryextensionabilityinfosync-f-sys.md#queryExtensionAbilityInfoSync) | 以同步方法根据给定的want、extensionAbilityType、extensionAbilityFlags和userId获取ExtensionAbilityInfo。 获取调用方自身的信息时不需要权限。 |
| [queryExtensionAbilityInfoSync](arkts-ability-bundlemanager-queryextensionabilityinfosync-f-sys.md#queryExtensionAbilityInfoSync（系统接口）) | 根据给定的want、extensionAbilityType、extensionAbilityFlags和userId获取ExtensionAbilityInfo，使用同步方式返回结果。 获取调用方自身的信息时不需要权限。 |
| [queryExtensionAbilityInfoSync](arkts-ability-bundlemanager-queryextensionabilityinfosync-f-sys.md#queryExtensionAbilityInfoSync（系统接口）) | 根据给定的extensionAbilityType、extensionAbilityFlags和userId获取ExtensionAbilityInfo。 获取调用方自身的信息时不需要权限。 |
| [recoverBackupBundleData](arkts-ability-bundlemanager-recoverbackupbundledata-f-sys.md#recoverBackupBundleData) | 恢复指定用户下指定应用或分身应用的备份数据。使用Promise异步回调。 |
| [removeBackupBundleData](arkts-ability-bundlemanager-removebackupbundledata-f-sys.md#removeBackupBundleData) | 删除指定用户下指定应用或分身应用的备份数据。使用Promise异步回调。 |
| [setAbilityEnabled](arkts-ability-bundlemanager-setabilityenabled-f-sys.md#setAbilityEnabled) | 设置指定应用或分身应用组件的禁用或使能状态。使用Promise异步回调。 |
| [setAbilityEnabled](arkts-ability-bundlemanager-setabilityenabled-f-sys.md#setAbilityEnabled（系统接口）) | 设置指定组件的禁用或使能状态。使用callback异步回调。 |
| [setAbilityEnabled](arkts-ability-bundlemanager-setabilityenabled-f-sys.md#setAbilityEnabled（系统接口）) | 设置指定组件的禁用或使能状态。使用Promise异步回调。 |
| [setAbilityEnabledSync](arkts-ability-bundlemanager-setabilityenabledsync-f-sys.md#setAbilityEnabledSync) | 以同步方法设置指定组件的禁用或使能状态。 |
| [setAbilityFileTypesForSelf](arkts-ability-bundlemanager-setabilityfiletypesforself-f-sys.md#setAbilityFileTypesForSelf) | 设置当前应用支持打开的文件类型。 |
| [setAdditionalInfo](arkts-ability-bundlemanager-setadditionalinfo-f-sys.md#setAdditionalInfo) | 设置指定应用的额外信息。此接口仅供应用市场调用。 |
| [setApplicationEnabled](arkts-ability-bundlemanager-setapplicationenabled-f-sys.md#setApplicationEnabled) | 设置指定应用或分身应用的禁用或使能状态。使用Promise异步回调。 |
| [setApplicationEnabled](arkts-ability-bundlemanager-setapplicationenabled-f-sys.md#setApplicationEnabled（系统接口）) | 设置应用程序是启用还是禁用，并控制在禁用时是否杀死进程。 |
| [setApplicationEnabled](arkts-ability-bundlemanager-setapplicationenabled-f-sys.md#setApplicationEnabled（系统接口）) | 设置指定应用的禁用或使能状态。使用callback异步回调。 |
| [setApplicationEnabled](arkts-ability-bundlemanager-setapplicationenabled-f-sys.md#setApplicationEnabled（系统接口）) | 设置指定应用的禁用或使能状态。使用Promise异步回调。 |
| [setApplicationEnabledSync](arkts-ability-bundlemanager-setapplicationenabledsync-f-sys.md#setApplicationEnabledSync) | 以同步方法设置指定应用的禁用或使能状态。 |
| [setApplicationEnabledSync](arkts-ability-bundlemanager-setapplicationenabledsync-f-sys.md#setApplicationEnabledSync（系统接口）) | 设置应用程序是启用还是禁用，并控制在禁用时是否杀死进程。 |
| [switchUninstallState](arkts-ability-bundlemanager-switchuninstallstate-f-sys.md#switchUninstallState) | 切换指定应用的可卸载状态，此接口与EDM应用拦截管控机制不互相影响。 |
| [verifyAbc](arkts-ability-bundlemanager-verifyabc-f-sys.md#verifyAbc) | 根据给定的abcPaths和deleteOriginalFiles校验.abc文件。使用callback异步回调。 |
| [verifyAbc](arkts-ability-bundlemanager-verifyabc-f-sys.md#verifyAbc（系统接口）) | 根据给定的abcPaths和deleteOriginalFiles校验.abc文件。使用Promise异步回调。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AbilityType](arkts-ability-bundlemanager-abilitytype-e.md) | 标识Ability组件的类型。 |
| [BundleFlag](arkts-ability-bundlemanager-bundleflag-e.md) | 包信息标志，指示需要获取的包信息的内容。 |
| [BundleType](arkts-ability-bundlemanager-bundletype-e.md) | 标识应用的类型。 |
| [CompatiblePolicy](arkts-ability-bundlemanager-compatiblepolicy-e.md) | 标识动态共享库的版本兼容类型。 |
| [DisplayOrientation](arkts-ability-bundlemanager-displayorientation-e.md) | 标识该Ability的显示模式。仅适用于FA模型的[PageAbility](../../../application-models/pageability-overview.md)。 &lt;!--Table: 40%; 10%; 50%--&gt; |
| [ExtensionAbilityType](arkts-ability-bundlemanager-extensionabilitytype-e.md) | 扩展组件的类型。 &lt;!--Table: 30%; 10%; 60%--&gt; &lt;!--RP2--&gt;&lt;!--RP2End--&gt; |
| [LaunchType](arkts-ability-bundlemanager-launchtype-e.md) | 标识组件的[启动模式](../../../application-models/uiability-launch-type.md)。 |
| [ModuleType](arkts-ability-bundlemanager-moduletype-e.md) | 标识模块类型。 |
| [MultiAppModeType](arkts-ability-bundlemanager-multiappmodetype-e.md) | 标识应用多开的模式类型。 |
| [PermissionGrantState](arkts-ability-bundlemanager-permissiongrantstate-e.md) | 权限授予状态。 |
| [SupportWindowMode](arkts-ability-bundlemanager-supportwindowmode-e.md) | 标识该组件所支持的窗口模式。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AbilityFlag](arkts-ability-bundlemanager-abilityflag-e-sys.md) | Ability组件信息标志，指示需要获取的Ability组件信息的内容。 |
| [AppDistributionType](arkts-ability-bundlemanager-appdistributiontype-e-sys.md) | 标识应用[HarmonyAppProvision配置文件说明](../../../security/app-provision-structure.md)。 |
| [ApplicationFlag](arkts-ability-bundlemanager-applicationflag-e-sys.md) | 应用信息标志，指示需要获取的应用信息的内容。 |
| [ApplicationInfoFlag](arkts-ability-bundlemanager-applicationinfoflag-e-sys.md) | 标识应用和用户之间的各种状态类型。 |
| [BundleFlag](arkts-ability-bundlemanager-bundleflag-e-sys.md) | 包信息标志，指示需要获取的包信息的内容。 |
| [BundleInstallStatus](arkts-ability-bundlemanager-bundleinstallstatus-e-sys.md) | 标识应用的安装状态。 |
| [ExtensionAbilityFlag](arkts-ability-bundlemanager-extensionabilityflag-e-sys.md) | 扩展组件信息标志，指示需要获取的扩展组件信息的内容。 |
| [ProfileType](arkts-ability-bundlemanager-profiletype-e-sys.md) | 标识配置文件类型。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [AbilityInfo](arkts-ability-bundlemanager-abilityinfo-t.md) | Ability信息。 |
| [AlternateIconInfo](arkts-ability-bundlemanager-alternateiconinfo-t.md) | 应用备用图标信息。 |
| [AppCloneIdentity](arkts-ability-bundlemanager-appcloneidentity-t.md) | 描述应用包的身份信息。 |
| [ApplicationInfo](arkts-ability-bundlemanager-applicationinfo-t.md) | 应用程序信息。 |
| [BundleInfo](arkts-ability-bundlemanager-bundleinfo-t.md) | 应用包信息。 |
| [DataItem](arkts-ability-bundlemanager-dataitem-t.md) | 模块配置的路由表中的自定义数据。 |
| [Dependency](arkts-ability-bundlemanager-dependency-t.md) | 模块所依赖的动态共享库信息。 |
| [ElementName](arkts-ability-bundlemanager-elementname-t.md) | ElementName信息。 |
| [ExtensionAbilityInfo](arkts-ability-bundlemanager-extensionabilityinfo-t.md) | ExtensionAbility信息。 |
| [HapModuleInfo](arkts-ability-bundlemanager-hapmoduleinfo-t.md) | 模块信息。 |
| [Metadata](arkts-ability-bundlemanager-metadata-t.md) | 元数据信息。 |
| [ModuleMetadata](arkts-ability-bundlemanager-modulemetadata-t.md) | 模块的元数据信息。 |
| [PreloadItem](arkts-ability-bundlemanager-preloaditem-t.md) | 原子化服务中模块的预加载模块信息。 |
| [ReqPermissionDetail](arkts-ability-bundlemanager-reqpermissiondetail-t.md) | 应用运行时需向系统申请的权限集合的详细信息。 |
| [RouterItem](arkts-ability-bundlemanager-routeritem-t.md) | 模块配置的路由表信息。 |
| [SignatureInfo](arkts-ability-bundlemanager-signatureinfo-t.md) | 应用包的签名信息。 |
| [Skill](arkts-ability-bundlemanager-skill-t.md) | skill信息。 |
| [SkillUrl](arkts-ability-bundlemanager-skillurl-t.md) | SkillUri信息。 |
| [UsedScene](arkts-ability-bundlemanager-usedscene-t.md) | 权限使用的场景和时机。 |
| [WindowSize](arkts-ability-bundlemanager-windowsize-t.md) | 窗口尺寸。 |

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AppProvisionInfo](arkts-ability-bundlemanager-appprovisioninfo-t-sys.md) | 应用[HarmonyAppProvision配置文件](../../../security/app-provision-structure.md)中的信息。 |
| [BundleOptions](arkts-ability-bundlemanager-bundleoptions-t-sys.md) | 应用包选项，用于设置或查询应用相关信息。 |
| [DynamicIconInfo](arkts-ability-bundlemanager-dynamiciconinfo-t-sys.md) | 应用的动态图标信息。 |
| [PermissionDef](arkts-ability-bundlemanager-permissiondef-t-sys.md) | [module.json5配置文件](../../../quick-start/module-configuration-file.md)中定义的权限详细信息。 |
| [PluginBundleInfo](arkts-ability-bundlemanager-pluginbundleinfo-t-sys.md) | 插件信息。 |
| [PluginModuleInfo](arkts-ability-bundlemanager-pluginmoduleinfo-t-sys.md) | 插件的模块信息。 |
| [PreinstalledApplicationInfo](arkts-ability-bundlemanager-preinstalledapplicationinfo-t-sys.md) | 预置应用信息。 |
| [RecoverableApplicationInfo](arkts-ability-bundlemanager-recoverableapplicationinfo-t-sys.md) | 预置应用被卸载后可以恢复的预置应用信息。 |
| [SharedBundleInfo](arkts-ability-bundlemanager-sharedbundleinfo-t-sys.md) | 共享包信息。 |
| [Validity](arkts-ability-bundlemanager-validity-t-sys.md) | 配置文件中的有效期。 |
<!--DelEnd-->

