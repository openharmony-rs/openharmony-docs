# @ohos.bundle.bundleResourceManager

本模块提供应用资源数据查询能力，支持[BundleResourceInfo](arkts-ability-bundleresourceinfo-i-sys.md)和[LauncherAbilityResourceInfo](arkts-ability-launcherabilityresourceinfo-i-sys.md)等信息的查询。

> **说明：**  
>  
> 本模块从API version 12 开始支持查询被禁用应用和设备上已安装应用(不区用户)的图标和名称资源。  
>  
> 本模块为系统接口。

**起始版本：** 11

<!--Device-unnamed-declare namespace bundleResourceManager--><!--Device-unnamed-declare namespace bundleResourceManager-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { bundleResourceManager } from '@kit.AbilityKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getAllBundleResourceInfo](arkts-ability-bundleresourcemanager-getallbundleresourceinfo-f-sys.md#getallbundleresourceinfo-1) | 根据给定的resourceFlags获取所有应用的BundleResourceInfo。使用callback异步回调。 |
| [getAllBundleResourceInfo](arkts-ability-bundleresourcemanager-getallbundleresourceinfo-f-sys.md#getallbundleresourceinfo-2) | 根据给定的resourceFlags获取所有应用的BundleResourceInfo。使用Promise异步回调。 |
| [getAllLauncherAbilityResourceInfo](arkts-ability-bundleresourcemanager-getalllauncherabilityresourceinfo-f-sys.md#getalllauncherabilityresourceinfo-1) | 根据给定的resourceFlags获取当前所有应用的LauncherAbilityResourceInfo。使用callback异步回调。 |
| [getAllLauncherAbilityResourceInfo](arkts-ability-bundleresourcemanager-getalllauncherabilityresourceinfo-f-sys.md#getalllauncherabilityresourceinfo-2) | 根据给定的resourceFlags获取当前所有应用的LauncherAbilityResourceInfo。使用Promise异步回调。 |
| [getAllUninstalledBundleResourceInfo](arkts-ability-bundleresourcemanager-getalluninstalledbundleresourceinfo-f-sys.md#getalluninstalledbundleresourceinfo-1) | 根据给定的resourceFlags获取所有已卸载且保留数据的应用的BundleResourceInfo。使用Promise异步回调。 |
| [getBundleResourceInfo](arkts-ability-bundleresourcemanager-getbundleresourceinfo-f-sys.md#getbundleresourceinfo-1) | 以同步方法根据给定的bundleName和resourceFlags获取当前应用的BundleResourceInfo。 |
| [getBundleResourceInfo](arkts-ability-bundleresourcemanager-getbundleresourceinfo-f-sys.md#getbundleresourceinfo-2) | 以同步方法根据给定的bundleName、resourceFlags和appIndex获取当前应用或分身应用的BundleResourceInfo。 |
| [getExtensionAbilityResourceInfo](arkts-ability-bundleresourcemanager-getextensionabilityresourceinfo-f-sys.md#getextensionabilityresourceinfo-1) | 根据应用包名、扩展组件类型、资源信息标志、应用分身ID获取应用的扩展组件资源。使用同步方式返回。 |
| [getLauncherAbilityResourceInfo](arkts-ability-bundleresourcemanager-getlauncherabilityresourceinfo-f-sys.md#getlauncherabilityresourceinfo-1) | 以同步方法根据给定的bundleName和resourceFlags获取当前应用的LauncherAbilityResourceInfo。 |
| [getLauncherAbilityResourceInfo](arkts-ability-bundleresourcemanager-getlauncherabilityresourceinfo-f-sys.md#getlauncherabilityresourceinfo-2) | 以同步方法根据给定的bundleName、resourceFlags和appIndex获取当前应用或分身应用的LauncherAbilityResourceInfo。 |
| [getLauncherAbilityResourceInfoList](arkts-ability-bundleresourcemanager-getlauncherabilityresourceinfolist-f-sys.md#getlauncherabilityresourceinfolist-1) | 根据传入的optionsList获取列表中每个BundleOptions元素对应的应用的LauncherAbilityResourceInfo。使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ResourceFlag](arkts-ability-bundleresourcemanager-resourceflag-e-sys.md) | 资源信息标志，指示需要获取的资源信息的内容。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BundleResourceInfo](arkts-ability-bundleresourcemanager-bundleresourceinfo-t-sys.md) | 应用配置的图标和名称信息。 |
| [LauncherAbilityResourceInfo](arkts-ability-bundleresourcemanager-launcherabilityresourceinfo-t-sys.md) | 应用配置的入口图标和名称信息。 |
<!--DelEnd-->

