# @ohos.bundle.freeInstall

本模块提供免安装相关的设置和查询能力，支持BundlePackInfo、DispatchInfo等信息的查询。

> **说明：**
>
> 本模块为系统接口。

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getBundlePackInfo](arkts-ability-getbundlepackinfo-f-sys.md#getbundlepackinfo-1) | 基于bundleName和bundlePackFlag来获取bundlePackInfo。使用callback异步回调。 |
| [getBundlePackInfo](arkts-ability-getbundlepackinfo-f-sys.md#getbundlepackinfo-2) | 基于bundleName和BundlePackFlag来获取bundlePackInfo。使用Promise异步回调。 |
| [getDispatchInfo](arkts-ability-getdispatchinfo-f-sys.md#getdispatchinfo-1) | 获取有关dispatch版本的信息。使用callback异步回调。 |
| [getDispatchInfo](arkts-ability-getdispatchinfo-f-sys.md#getdispatchinfo-2) | 获取有关dispatch版本的信息。使用Promise异步回调。 |
| [isHapModuleRemovable](arkts-ability-ishapmoduleremovable-f-sys.md#ishapmoduleremovable-1) | 查询指定模块是否可以被移除。使用callback异步回调。 |
| [isHapModuleRemovable](arkts-ability-ishapmoduleremovable-f-sys.md#ishapmoduleremovable-2) | 查询指定模块是否可以被移除。使用Promise异步回调。 |
| [setHapModuleUpgradeFlag](arkts-ability-sethapmoduleupgradeflag-f-sys.md#sethapmoduleupgradeflag-1) | 设置指定模块是否升级。使用callback异步回调。 |
| [setHapModuleUpgradeFlag](arkts-ability-sethapmoduleupgradeflag-f-sys.md#sethapmoduleupgradeflag-2) | 设置指定模块是否升级。使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BundlePackFlag](arkts-ability-bundlepackflag-e-sys.md) | 要查询的应用包标志 |
| [UpgradeFlag](arkts-ability-upgradeflag-e-sys.md) | 仅供内部系统使用标志位 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AbilityFormInfo](arkts-ability-abilityforminfo-t-sys.md) | 卡片信息。 |
| [ApiVersion](arkts-ability-apiversion-t-sys.md) | module的api版本。 |
| [BundleConfigInfo](arkts-ability-bundleconfiginfo-t-sys.md) | 包的配置信息。 |
| [BundlePackInfo](arkts-ability-bundlepackinfo-t-sys.md) | 应用包信息。 |
| [DispatchInfo](arkts-ability-dispatchinfo-t-sys.md) | 免安装结构体和接口版本信息类。 |
| [ExtensionAbility](arkts-ability-extensionability-t-sys.md) | extensionAbilities的配置信息。 |
| [ModuleAbilityInfo](arkts-ability-moduleabilityinfo-t-sys.md) | module包含的ability组件信息。 |
| [ModuleConfigInfo](arkts-ability-moduleconfiginfo-t-sys.md) | 包的module配置信息。 |
| [ModuleDistroInfo](arkts-ability-moduledistroinfo-t-sys.md) | module发行版信息。 |
| [PackageConfig](arkts-ability-packageconfig-t-sys.md) | pack.info的包信息。 |
| [PackageSummary](arkts-ability-packagesummary-t-sys.md) | pack.info中的包摘要信息。 |
| [Version](arkts-ability-version-t-sys.md) | 包的版本。 |
<!--DelEnd-->

