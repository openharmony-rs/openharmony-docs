# @ohos.bundle.overlay

本模块提供overlay特征应用的[OverlayModuleInfo](arkts-ability-overlaymoduleinfo-i.md)信息查询以及禁用使能的能力。

overlay特征应用指应用中包含有overlay资源包，overlay资源包详见[overlay机制](../../../quick-start/resource-categories-and-access.md#overlay机制)。
> **说明：**  
>  
> 本模块接口仅适用于stage模型，且仅适用于[静态overlay](../../../quick-start/resource-categories-and-access.md#静态overlay配置方式)。

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
| [getOverlayModuleInfo](arkts-ability-overlay-getoverlaymoduleinfo-f.md#getoverlaymoduleinfo) | 获取当前应用中overlay特征module的OverlayModuleInfo信息。使用callback异步回调。 |
| [getOverlayModuleInfo](arkts-ability-overlay-getoverlaymoduleinfo-f.md#getoverlaymoduleinfo-1) | 获取当前应用中overlay特征module的OverlayModuleInfo信息。使用Promise异步回调。 |
| [getTargetOverlayModuleInfos](arkts-ability-overlay-gettargetoverlaymoduleinfos-f.md#gettargetoverlaymoduleinfos) | 获取指定的目标module所关联的OverlayModuleInfo。overlay特征的module一般是为设备上存在的非overlay特征的module提供覆盖的资源文件，其中非overlay特征的module被称作目标module。使用callback异步回调。 |
| [getTargetOverlayModuleInfos](arkts-ability-overlay-gettargetoverlaymoduleinfos-f.md#gettargetoverlaymoduleinfos-1) | 获取指定的目标module所关联的OverlayModuleInfo。overlay特征的module一般是为设备上存在的非overlay特征的module提供覆盖的资源文件，其中非overlay特征的module被称作目标module。使用Promise异步回调。 |
| [setOverlayEnabled](arkts-ability-overlay-setoverlayenabled-f.md#setoverlayenabled) | 设置当前应用中overlay module的禁用使能状态。使用callback异步回调。 |
| [setOverlayEnabled](arkts-ability-overlay-setoverlayenabled-f.md#setoverlayenabled-1) | 设置当前应用中overlay特征module的禁用使能状态。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getOverlayModuleInfoByBundleName](arkts-ability-overlay-getoverlaymoduleinfobybundlename-f-sys.md#getoverlaymoduleinfobybundlename) | 获取指定应用中所有module的OverlayModuleInfo信息。使用callback异步回调。  指定应用是调用方自身时不需要权限。 |
| [getOverlayModuleInfoByBundleName](arkts-ability-overlay-getoverlaymoduleinfobybundlename-f-sys.md#getoverlaymoduleinfobybundlename-1) | 获取指定应用中指定module的OverlayModuleInfo信息。使用callback异步回调。  指定应用是调用方自身时不需要权限。 |
| [getOverlayModuleInfoByBundleName](arkts-ability-overlay-getoverlaymoduleinfobybundlename-f-sys.md#getoverlaymoduleinfobybundlename-2) | 获取指定应用中指定module的OverlayModuleInfo信息。使用promise异步回调。  指定应用是调用方自身时不需要权限。 |
| [getTargetOverlayModuleInfosByBundleName](arkts-ability-overlay-gettargetoverlaymoduleinfosbybundlename-f-sys.md#gettargetoverlaymoduleinfosbybundlename) | 获取指定应用中所有module关联的所有OverlayModuleInfo信息。使用callback异步回调。  指定应用是调用方自身时不需要权限。 |
| [getTargetOverlayModuleInfosByBundleName](arkts-ability-overlay-gettargetoverlaymoduleinfosbybundlename-f-sys.md#gettargetoverlaymoduleinfosbybundlename-1) | 获取指定应用中指定module关联的所有OverlayModuleInfo信息。使用callback异步回调。  指定应用是调用方自身时不需要权限。 |
| [getTargetOverlayModuleInfosByBundleName](arkts-ability-overlay-gettargetoverlaymoduleinfosbybundlename-f-sys.md#gettargetoverlaymoduleinfosbybundlename-2) | 获取指定应用中指定module关联的所有OverlayModuleInfo信息。使用promise异步回调。  指定应用是调用方自身时不需要权限。 |
| [setOverlayEnabledByBundleName](arkts-ability-overlay-setoverlayenabledbybundlename-f-sys.md#setoverlayenabledbybundlename) | 设置指定应用的overlay module的禁用使能状态。使用callback异步回调。  指定应用是调用方自身时不需要权限。 |
| [setOverlayEnabledByBundleName](arkts-ability-overlay-setoverlayenabledbybundlename-f-sys.md#setoverlayenabledbybundlename-1) | 设置指定应用的overlay module的禁用使能状态。使用Promise异步回调。  指定应用是调用方自身时不需要权限。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [OverlayModuleInfo](arkts-ability-overlay-overlaymoduleinfo-t.md) | OverlayModuleInfo信息。 |

