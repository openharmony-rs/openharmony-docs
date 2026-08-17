# innerBundleManager

本模块提供launcher应用使用的接口。 > **说明：** > > 本模块从API version 9开始不再支持。建议使用[launcherBundleManager](arkts-bundle-launcherbundlemanager.md#ohosbundlelauncherbundlemanager) > 及[bundleMonitor](arkts-bundle-bundlemonitor.md#ohosbundlebundlemonitor)替代。 > > 本模块为系统接口。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** 9

**替代接口：** [launcherBundleManager](arkts-bundle-launcherbundlemanager.md#ohosbundlelauncherbundlemanager)

<!--Device-unnamed-declare namespace innerBundleManager--><!--Device-unnamed-declare namespace innerBundleManager-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getLauncherAbilityInfos](arkts-ability-innerbundlemanager-getlauncherabilityinfos-f-sys.md#getlauncherabilityinfos) | 根据给定的Bundle名称获取LauncherAbilityInfos，使用callback异步回调。 |
| [getLauncherAbilityInfos](arkts-ability-innerbundlemanager-getlauncherabilityinfos-f-sys.md#getlauncherabilityinfos系统接口) | 根据给定的Bundle名称获取LauncherAbilityInfos，使用Promise异步回调。 |
| [on_BundleStatusChange](arkts-ability-innerbundlemanager-onbundlestatuschange-f-sys.md#onbundlestatuschange) | 注册Callback。 |
| [on_BundleStatusChange](arkts-ability-innerbundlemanager-onbundlestatuschange-f-sys.md#onbundlestatuschange-1) | 注册Callback。 |
| [off_BundleStatusChange](arkts-ability-innerbundlemanager-offbundlestatuschange-f-sys.md#offbundlestatuschange) | 取消注册Callback。 |
| [off_BundleStatusChange](arkts-ability-innerbundlemanager-offbundlestatuschange-f-sys.md#offbundlestatuschange-1) | 取消注册Callback。 |
| [getAllLauncherAbilityInfos](arkts-ability-innerbundlemanager-getalllauncherabilityinfos-f-sys.md#getalllauncherabilityinfos) | 获取所有的LauncherAbilityInfos，使用callback异步回调。 |
| [getAllLauncherAbilityInfos](arkts-ability-innerbundlemanager-getalllauncherabilityinfos-f-sys.md#getalllauncherabilityinfos系统接口) | 获取LauncherAbilityInfos，使用Promise异步回调。 |
| [getShortcutInfos](arkts-ability-innerbundlemanager-getshortcutinfos-f-sys.md#getshortcutinfos) | 根据给定的Bundle名称获取快捷方式信息，使用callback异步回调。 |
| [getShortcutInfos](arkts-ability-innerbundlemanager-getshortcutinfos-f-sys.md#getshortcutinfos系统接口) | 根据给定的Bundle名称获取快捷方式信息，使用Promise异步回调。 |
<!--DelEnd-->

