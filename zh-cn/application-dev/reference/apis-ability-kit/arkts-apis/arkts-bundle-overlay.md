# @ohos.bundle.overlay

本模块提供overlay特征应用的[OverlayModuleInfo](arkts-ability-overlaymoduleinfo-i.md#OverlayModuleInfo)信息查询以及禁用使能的能力。 overlay特征应用指应用中包含有overlay资源包，overlay资源包详见 [overlay机制](../../../quick-start/resource-categories-and-access.md#overlay机制)。 > **说明：** > > 本模块接口仅适用于stage模型，且仅适用于[静态overlay](../../../quick-start/resource-categories-and-access.md#静态overlay配置方式)。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace overlay--><!--Device-unnamed-declare namespace overlay-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Overlay

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getOverlayModuleInfo](arkts-ability-overlay-getoverlaymoduleinfo-f.md#getOverlayModuleInfo) | 获取当前应用中overlay特征module的OverlayModuleInfo信息。使用callback异步回调。 |
| [getOverlayModuleInfo](arkts-ability-overlay-getoverlaymoduleinfo-f.md#getOverlayModuleInfo) | 获取当前应用中overlay特征module的OverlayModuleInfo信息。使用Promise异步回调。 |
| [getTargetOverlayModuleInfos](arkts-ability-overlay-gettargetoverlaymoduleinfos-f.md#getTargetOverlayModuleInfos) | 获取指定的目标module所关联的OverlayModuleInfo。overlay特征的module一般是为设备上存在的非overlay特征的module提供覆盖的资源文件，其中非overlay特征的module被称作目标 module。使用callback异步回调。 |
| [getTargetOverlayModuleInfos](arkts-ability-overlay-gettargetoverlaymoduleinfos-f.md#getTargetOverlayModuleInfos) | 获取指定的目标module所关联的OverlayModuleInfo。overlay特征的module一般是为设备上存在的非overlay特征的module提供覆盖的资源文件，其中非overlay特征的module被称作目标 module。使用Promise异步回调。 |
| [setOverlayEnabled](arkts-ability-overlay-setoverlayenabled-f.md#setOverlayEnabled) | 设置当前应用中overlay module的禁用使能状态。使用callback异步回调。 |
| [setOverlayEnabled](arkts-ability-overlay-setoverlayenabled-f.md#setOverlayEnabled) | 设置当前应用中overlay特征module的禁用使能状态。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getOverlayModuleInfoByBundleName](arkts-ability-overlay-getoverlaymoduleinfobybundlename-f-sys.md#getOverlayModuleInfoByBundleName) | 获取指定应用中所有module的OverlayModuleInfo信息。使用callback异步回调。 指定应用是调用方自身时不需要权限。 |
| [getOverlayModuleInfoByBundleName](arkts-ability-overlay-getoverlaymoduleinfobybundlename-f-sys.md#getOverlayModuleInfoByBundleName（系统接口）) | 获取指定应用中指定module的OverlayModuleInfo信息。使用callback异步回调。 指定应用是调用方自身时不需要权限。 |
| [getOverlayModuleInfoByBundleName](arkts-ability-overlay-getoverlaymoduleinfobybundlename-f-sys.md#getOverlayModuleInfoByBundleName（系统接口）) | 获取指定应用中指定module的OverlayModuleInfo信息。使用promise异步回调。 指定应用是调用方自身时不需要权限。 |
| [getTargetOverlayModuleInfosByBundleName](arkts-ability-overlay-gettargetoverlaymoduleinfosbybundlename-f-sys.md#getTargetOverlayModuleInfosByBundleName) | 获取指定应用中所有module关联的所有OverlayModuleInfo信息。使用callback异步回调。 指定应用是调用方自身时不需要权限。 |
| [getTargetOverlayModuleInfosByBundleName](arkts-ability-overlay-gettargetoverlaymoduleinfosbybundlename-f-sys.md#getTargetOverlayModuleInfosByBundleName（系统接口）) | 获取指定应用中指定module关联的所有OverlayModuleInfo信息。使用callback异步回调。 指定应用是调用方自身时不需要权限。 |
| [getTargetOverlayModuleInfosByBundleName](arkts-ability-overlay-gettargetoverlaymoduleinfosbybundlename-f-sys.md#getTargetOverlayModuleInfosByBundleName（系统接口）) | 获取指定应用中指定module关联的所有OverlayModuleInfo信息。使用promise异步回调。 指定应用是调用方自身时不需要权限。 |
| [setOverlayEnabledByBundleName](arkts-ability-overlay-setoverlayenabledbybundlename-f-sys.md#setOverlayEnabledByBundleName) | 设置指定应用的overlay module的禁用使能状态。使用callback异步回调。 指定应用是调用方自身时不需要权限。 |
| [setOverlayEnabledByBundleName](arkts-ability-overlay-setoverlayenabledbybundlename-f-sys.md#setOverlayEnabledByBundleName（系统接口）) | 设置指定应用的overlay module的禁用使能状态。使用Promise异步回调。 指定应用是调用方自身时不需要权限。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [OverlayModuleInfo](arkts-ability-overlay-overlaymoduleinfo-t.md) | overlayHap的配置文件信息 |

