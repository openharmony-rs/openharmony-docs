# @ohos.bundle.freeInstall

本模块提供免安装相关的设置和查询能力，支持BundlePackInfo、DispatchInfo等信息的查询。 > **说明：** > > 本模块为系统接口。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace freeInstall--><!--Device-unnamed-declare namespace freeInstall-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getBundlePackInfo](arkts-ability-freeinstall-getbundlepackinfo-f-sys.md#getBundlePackInfo) | 基于bundleName和bundlePackFlag来获取bundlePackInfo。使用callback异步回调。 |
| [getBundlePackInfo](arkts-ability-freeinstall-getbundlepackinfo-f-sys.md#getBundlePackInfo（系统接口）) | 基于bundleName和BundlePackFlag来获取bundlePackInfo。使用Promise异步回调。 |
| [getDispatchInfo](arkts-ability-freeinstall-getdispatchinfo-f-sys.md#getDispatchInfo) | 获取有关dispatch版本的信息。使用callback异步回调。 |
| [getDispatchInfo](arkts-ability-freeinstall-getdispatchinfo-f-sys.md#getDispatchInfo（系统接口）) | 获取有关dispatch版本的信息。使用Promise异步回调。 |
| [isHapModuleRemovable](arkts-ability-freeinstall-ishapmoduleremovable-f-sys.md#isHapModuleRemovable) | 查询指定模块是否可以被移除。使用callback异步回调。 |
| [isHapModuleRemovable](arkts-ability-freeinstall-ishapmoduleremovable-f-sys.md#isHapModuleRemovable（系统接口）) | 查询指定模块是否可以被移除。使用Promise异步回调。 |
| [setHapModuleUpgradeFlag](arkts-ability-freeinstall-sethapmoduleupgradeflag-f-sys.md#setHapModuleUpgradeFlag) | 设置指定模块是否升级。使用callback异步回调。 |
| [setHapModuleUpgradeFlag](arkts-ability-freeinstall-sethapmoduleupgradeflag-f-sys.md#setHapModuleUpgradeFlag（系统接口）) | 设置指定模块是否升级。使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BundlePackFlag](arkts-ability-freeinstall-bundlepackflag-e-sys.md) | 要查询的应用包标志 |
| [UpgradeFlag](arkts-ability-freeinstall-upgradeflag-e-sys.md) | 仅供内部系统使用标志位 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AbilityFormInfo](arkts-ability-freeinstall-abilityforminfo-t-sys.md) | 卡片信息。 |
| [ApiVersion](arkts-ability-freeinstall-apiversion-t-sys.md) | module的api版本。 |
| [BundleConfigInfo](arkts-ability-freeinstall-bundleconfiginfo-t-sys.md) | 包的配置信息。 |
| [BundlePackInfo](arkts-ability-freeinstall-bundlepackinfo-t-sys.md) | 应用包信息。 |
| [DispatchInfo](arkts-ability-freeinstall-dispatchinfo-t-sys.md) | 免安装结构体和接口版本信息类。 |
| [ExtensionAbility](arkts-ability-freeinstall-extensionability-t-sys.md) | extensionAbilities的配置信息。 |
| [ModuleAbilityInfo](arkts-ability-freeinstall-moduleabilityinfo-t-sys.md) | module包含的ability组件信息。 |
| [ModuleConfigInfo](arkts-ability-freeinstall-moduleconfiginfo-t-sys.md) | 包的module配置信息。 |
| [ModuleDistroInfo](arkts-ability-freeinstall-moduledistroinfo-t-sys.md) | module发行版信息。 |
| [PackageConfig](arkts-ability-freeinstall-packageconfig-t-sys.md) | pack.info的包信息。 |
| [PackageSummary](arkts-ability-freeinstall-packagesummary-t-sys.md) | pack.info中的包摘要信息。 |
| [Version](arkts-ability-freeinstall-version-t-sys.md) | 包的版本。 |
<!--DelEnd-->

