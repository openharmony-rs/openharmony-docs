# innerBundleManager（innerBundleManager模块）

```TypeScript
declare namespace innerBundleManager
```

本模块提供launcher应用使用的接口。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [launcherBundleManager](arkts-ability-bundle-launcherbundlemanager.md)

<!--Device-unnamed-declare namespace innerBundleManager--><!--Device-unnamed-declare namespace innerBundleManager-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { innerBundleManager, BundleStatusCallback } from '@kit.AbilityKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getAllLauncherAbilityInfos](arkts-ability-innerbundlemanager-getalllauncherabilityinfos-f-sys.md#getalllauncherabilityinfos) | 获取所有的LauncherAbilityInfos，使用callback异步回调。 |
| [getAllLauncherAbilityInfos](arkts-ability-innerbundlemanager-getalllauncherabilityinfos-f-sys.md#getalllauncherabilityinfos) | 获取LauncherAbilityInfos，使用Promise异步回调。 |
| [getLauncherAbilityInfos](arkts-ability-innerbundlemanager-getlauncherabilityinfos-f-sys.md#getlauncherabilityinfos) | 根据给定的Bundle名称获取LauncherAbilityInfos，使用callback异步回调。 |
| [getLauncherAbilityInfos](arkts-ability-innerbundlemanager-getlauncherabilityinfos-f-sys.md#getlauncherabilityinfos) | 根据给定的Bundle名称获取LauncherAbilityInfos，使用Promise异步回调。 |
| [getShortcutInfos](arkts-ability-innerbundlemanager-getshortcutinfos-f-sys.md#getshortcutinfos) | 根据给定的Bundle名称获取快捷方式信息，使用callback异步回调。 |
| [getShortcutInfos](arkts-ability-innerbundlemanager-getshortcutinfos-f-sys.md#getshortcutinfos) | 根据给定的Bundle名称获取快捷方式信息，使用Promise异步回调。 |
| [off('BundleStatusChange')](arkts-ability-innerbundlemanager-off-f-sys.md#offbundlestatuschange) | 取消注册Callback。 |
| [off('BundleStatusChange')](arkts-ability-innerbundlemanager-off-f-sys.md#offbundlestatuschange) | 取消注册Callback。 |
| [on('BundleStatusChange')](arkts-ability-innerbundlemanager-on-f-sys.md#onbundlestatuschange) | 注册Callback。 |
| [on('BundleStatusChange')](arkts-ability-innerbundlemanager-on-f-sys.md#onbundlestatuschange) | 注册Callback。 |
<!--DelEnd-->
