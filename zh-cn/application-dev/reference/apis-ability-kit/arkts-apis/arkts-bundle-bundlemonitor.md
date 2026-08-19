# @ohos.bundle.bundleMonitor

本模块提供监听应用安装，卸载，更新的能力。

**起始版本：** 23

<!--Device-unnamed-declare namespace bundleMonitor--><!--Device-unnamed-declare namespace bundleMonitor-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { bundleMonitor } from '@kit.AbilityKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [offAdd](arkts-ability-bundlemonitor-offadd-f-sys.md) | 注销监听应用的安装。 |
| [offRemove](arkts-ability-bundlemonitor-offremove-f-sys.md) | 注销监听应用的卸载。 |
| [offUpdate](arkts-ability-bundlemonitor-offupdate-f-sys.md) | 注销监听应用的更新。 |
| [off_BundleChangedEvent](arkts-ability-bundlemonitor-offbundlechangedevent-f-sys.md#off_bundlechangedevent) | 注销监听应用的安装，卸载，更新。使用callback异步回调。 |
| [onAdd](arkts-ability-bundlemonitor-onadd-f-sys.md) | 注册监听应用的安装。 |
| [onRemove](arkts-ability-bundlemonitor-onremove-f-sys.md) | 注册监听应用的卸载。 |
| [onUpdate](arkts-ability-bundlemonitor-onupdate-f-sys.md) | 注册监听应用的更新。 |
| [on_BundleChangedEvent](arkts-ability-bundlemonitor-onbundlechangedevent-f-sys.md#on_bundlechangedevent) | 注册监听应用的安装、卸载、更新。使用callback异步回调。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BundleChangedInfo](arkts-ability-bundlemonitor-bundlechangedinfo-i-sys.md) | 应用变更信息。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BundleChangedEvent](arkts-ability-bundlemonitor-bundlechangedevent-t-sys.md) | 监听的事件类型。 |
<!--DelEnd-->

