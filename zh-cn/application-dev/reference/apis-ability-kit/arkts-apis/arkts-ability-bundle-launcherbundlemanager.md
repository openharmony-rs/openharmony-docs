# @ohos.bundle.launcherBundleManager(launcherBundleManager模块)

本模块支持launcher应用（桌面有图标的应用）所需的查询能力，支持LauncherAbilityInfo、ShortcutInfo信息的查询。

**起始版本：** 9

<!--Device-unnamed-declare namespace launcherBundleManager--><!--Device-unnamed-declare namespace launcherBundleManager-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

## 导入模块

```TypeScript
import { launcherBundleManager } from '@kit.AbilityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getLauncherAbilityInfoSync](arkts-ability-launcherbundlemanager-getlauncherabilityinfosync-f.md#getlauncherabilityinfosync) | 查询指定bundleName及用户的[LauncherAbilityInfo](arkts-ability-launcherabilityinfo-i.md)。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getAllLauncherAbilityInfo](arkts-ability-launcherbundlemanager-getalllauncherabilityinfo-f-sys.md#getalllauncherabilityinfo1) | 查询指定用户下所有应用的[LauncherAbilityInfo](arkts-ability-launcherabilityinfo-i.md)。使用callback异步回调。 |
| [getAllLauncherAbilityInfo](arkts-ability-launcherbundlemanager-getalllauncherabilityinfo-f-sys.md#getalllauncherabilityinfo2) | 查询指定用户下所有应用的[LauncherAbilityInfo](arkts-ability-launcherabilityinfo-i.md)。使用Promise异步回调。 |
| [getLauncherAbilityInfo](arkts-ability-launcherbundlemanager-getlauncherabilityinfo-f-sys.md#getlauncherabilityinfo1) | 查询指定bundleName及用户的LauncherAbilityInfo。使用callback异步回调。 |
| [getLauncherAbilityInfo](arkts-ability-launcherbundlemanager-getlauncherabilityinfo-f-sys.md#getlauncherabilityinfo2) | 查询指定bundleName及用户的LauncherAbilityInfo。使用Promise异步回调。 |
| [getShortcutInfo](arkts-ability-launcherbundlemanager-getshortcutinfo-f-sys.md#getshortcutinfo1) | 查询当前用户下指定应用的快捷方式信息[ShortcutInfo](arkts-ability-shortcutinfo-i.md)，只支持查询主应用的ShortcutInfo，查询分身应用请使用[getShortcutInfoByAppIndex](arkts-ability-launcherbundlemanager-getshortcutinfobyappindex-f-sys.md)。使用callback异步回调。 |
| [getShortcutInfo](arkts-ability-launcherbundlemanager-getshortcutinfo-f-sys.md#getshortcutinfo2) | 查询当前用户下指定应用的快捷方式信息[ShortcutInfo](arkts-ability-shortcutinfo-i.md)，只支持查询主应用的ShortcutInfo，查询分身应用请使用[getShortcutInfoByAppIndex](arkts-ability-launcherbundlemanager-getshortcutinfobyappindex-f-sys.md)。使用Promise异步回调。 |
| [getShortcutInfoByAppIndex](arkts-ability-launcherbundlemanager-getshortcutinfobyappindex-f-sys.md#getshortcutinfobyappindex) | 查询当前用户下指定分身应用的快捷方式信息[ShortcutInfo](arkts-ability-shortcutinfo-i.md)。 |
| [getShortcutInfoSync](arkts-ability-launcherbundlemanager-getshortcutinfosync-f-sys.md#getshortcutinfosync1) | 查询当前用户下指定应用的快捷方式信息[ShortcutInfo](arkts-ability-shortcutinfo-i.md)，只支持查询主应用的ShortcutInfo，查询分身应用请使用[getShortcutInfoByAppIndex](arkts-ability-launcherbundlemanager-getshortcutinfobyappindex-f-sys.md)。 |
| [getShortcutInfoSync](arkts-ability-launcherbundlemanager-getshortcutinfosync-f-sys.md#getshortcutinfosync2) | 查询指定用户下指定应用的快捷方式信息[ShortcutInfo](arkts-ability-shortcutinfo-i.md)，只支持查询主应用的ShortcutInfo，查询分身应用请使用[getShortcutInfoByAppIndex](arkts-ability-launcherbundlemanager-getshortcutinfobyappindex-f-sys.md)。 |
| [startShortcut](arkts-ability-launcherbundlemanager-startshortcut-f-sys.md#startshortcut) | 拉起指定[ShortcutInfo](arkts-ability-shortcutinfo-i.md)中的ability。使用Promise异步回调。 |
| [startShortcutWithReason](arkts-ability-launcherbundlemanager-startshortcutwithreason-f-sys.md#startshortcutwithreason) | 根据指定的快捷方式信息，拉起对应的Ability，并携带快捷方式的启动原因。使用Promise异步回调。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [LauncherAbilityInfo](arkts-ability-launcherbundlemanager-launcherabilityinfo-t.md) | 桌面应用Ability的基础信息，包含应用标识、图标、名称等核心属性。详细信息请参见LauncherAbilityInfo。 |
| [ParameterItem](arkts-ability-launcherbundlemanager-parameteritem-t.md) | 快捷方式配置信息中的自定义数据。 |
| [ShortcutInfo](arkts-ability-launcherbundlemanager-shortcutinfo-t.md) | 应用[module.json5配置文件](../../../quick-start/module-configuration-file.md#shortcuts标签)中定义的快捷方式信息。 |
| [ShortcutWant](arkts-ability-launcherbundlemanager-shortcutwant-t.md) | 快捷方式内定义的目标[wants](../../../quick-start/module-configuration-file.md#wants标签)信息集合。 |
