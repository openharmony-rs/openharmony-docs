# @ohos.bundle.overlay(overlay模块)

本模块提供overlay特征应用的安装，overlay特征应用的[OverlayModuleInfo](arkts-ability-overlaymoduleinfo-i.md)信息的查询以及overlay特征应用的禁用使能的能力。

> **说明：** 
> 
> 当前页面仅包含本模块的系统接口，其他公开接口参见[@ohos.bundle.overlay](arkts-ability-bundle-overlay.md)。

**起始版本：** 10

<!--Device-unnamed-declare namespace overlay--><!--Device-unnamed-declare namespace overlay-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Overlay

## 导入模块

```TypeScript
import { overlay } from '@kit.AbilityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getOverlayModuleInfo](arkts-ability-overlay-getoverlaymoduleinfo-f.md#getoverlaymoduleinfo1) | 获取当前应用中overlay特征模块的OverlayModuleInfo信息。使用callback异步回调。 |
| [getOverlayModuleInfo](arkts-ability-overlay-getoverlaymoduleinfo-f.md#getoverlaymoduleinfo2) | 获取当前应用中overlay特征模块的OverlayModuleInfo信息。使用Promise异步回调。接口调用失败时可能返回null，需校验返回值后使用。 |
| [getTargetOverlayModuleInfos](arkts-ability-overlay-gettargetoverlaymoduleinfos-f.md#gettargetoverlaymoduleinfos1) | 获取指定的目标module所关联的OverlayModuleInfo。overlay特征的module一般是为设备上存在的非overlay特征的module提供覆盖的资源文件，其中非overlay特征的module被称作目标module。使用callback异步回调。 |
| [getTargetOverlayModuleInfos](arkts-ability-overlay-gettargetoverlaymoduleinfos-f.md#gettargetoverlaymoduleinfos2) | 获取指定的目标module所关联的OverlayModuleInfo。overlay特征的module一般是为设备上存在的非overlay特征的module提供覆盖的资源文件，其中非overlay特征的module被称作目标module。使用Promise异步回调。接口调用失败时可能返回null，需校验返回值后使用。 |
| [setOverlayEnabled](arkts-ability-overlay-setoverlayenabled-f.md#setoverlayenabled1) | 设置当前应用中overlay特征模块的禁用启用状态。使用callback异步回调。 |
| [setOverlayEnabled](arkts-ability-overlay-setoverlayenabled-f.md#setoverlayenabled2) | 设置当前应用中overlay特征模块的禁用启用状态。使用Promise异步回调。接口调用失败时可能返回null，需校验返回值后使用。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getOverlayModuleInfoByBundleName](arkts-ability-overlay-getoverlaymoduleinfobybundlename-f-sys.md#getoverlaymoduleinfobybundlename1) | 获取指定应用中所有module的OverlayModuleInfo信息。使用callback异步回调。 |
| [getOverlayModuleInfoByBundleName](arkts-ability-overlay-getoverlaymoduleinfobybundlename-f-sys.md#getoverlaymoduleinfobybundlename2) | 获取指定应用中指定module的OverlayModuleInfo信息。使用callback异步回调。 |
| [getOverlayModuleInfoByBundleName](arkts-ability-overlay-getoverlaymoduleinfobybundlename-f-sys.md#getoverlaymoduleinfobybundlename3) | 获取指定应用中指定module的OverlayModuleInfo信息。使用Promise异步回调。 |
| [getTargetOverlayModuleInfosByBundleName](arkts-ability-overlay-gettargetoverlaymoduleinfosbybundlename-f-sys.md#gettargetoverlaymoduleinfosbybundlename1) | 获取指定应用中所有module关联的所有OverlayModuleInfo信息。使用callback异步回调。 |
| [getTargetOverlayModuleInfosByBundleName](arkts-ability-overlay-gettargetoverlaymoduleinfosbybundlename-f-sys.md#gettargetoverlaymoduleinfosbybundlename2) | 获取指定应用中指定module关联的所有OverlayModuleInfo信息。使用callback异步回调。 |
| [getTargetOverlayModuleInfosByBundleName](arkts-ability-overlay-gettargetoverlaymoduleinfosbybundlename-f-sys.md#gettargetoverlaymoduleinfosbybundlename3) | 获取指定应用中指定module关联的所有OverlayModuleInfo信息。使用Promise异步回调。 |
| [setOverlayEnabledByBundleName](arkts-ability-overlay-setoverlayenabledbybundlename-f-sys.md#setoverlayenabledbybundlename1) | 设置指定应用的overlay module的禁用使能状态。使用callback异步回调。 |
| [setOverlayEnabledByBundleName](arkts-ability-overlay-setoverlayenabledbybundlename-f-sys.md#setoverlayenabledbybundlename2) | 设置指定应用的overlay module的禁用使能状态。使用Promise异步回调。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [OverlayModuleInfo](arkts-ability-overlay-overlaymoduleinfo-t.md) | OverlayModuleInfo信息，包含overlay特征模块的名称、状态、目标模块等配置信息，用于描述和管理应用的资源覆盖配置。 |
