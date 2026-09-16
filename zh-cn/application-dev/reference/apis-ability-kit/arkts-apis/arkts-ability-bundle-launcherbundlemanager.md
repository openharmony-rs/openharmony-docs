# @ohos.bundle.launcherBundleManager

本模块支持launcher应用（桌面有图标的应用）所需的查询能力，支持[LauncherAbilityInfo](arkts-ability-launcherabilityinfo-i.md)信息的查询。

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

## 导入模块

```TypeScript
import { launcherBundleManager } from '@kit.AbilityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getLauncherAbilityInfoSync](arkts-ability-launcherbundlemanager-getlauncherabilityinfosync-f.md) | 查询指定bundleName及用户的[LauncherAbilityInfo](arkts-ability-launcherabilityinfo-i.md)。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getAllLauncherAbilityInfo](arkts-ability-launcherbundlemanager-getalllauncherabilityinfo-f-sys.md) | 查询指定用户下所有应用的[LauncherAbilityInfo](arkts-ability-launcherabilityinfo-i.md)。使用callback异步回调。 |
| [getAllLauncherAbilityInfo](arkts-ability-launcherbundlemanager-getalllauncherabilityinfo-f-sys.md) | 查询指定用户下所有应用的[LauncherAbilityInfo](arkts-ability-launcherabilityinfo-i.md)。使用Promise异步回调。 |
| [getLauncherAbilityInfo](arkts-ability-launcherbundlemanager-getlauncherabilityinfo-f-sys.md) | 查询指定bundleName及用户的[LauncherAbilityInfo](arkts-ability-launcherabilityinfo-i.md)。使用callback异步回调。 |
| [getLauncherAbilityInfo](arkts-ability-launcherbundlemanager-getlauncherabilityinfo-f-sys.md) | 查询指定bundleName及用户的[LauncherAbilityInfo](arkts-ability-launcherabilityinfo-i.md)。使用Promise异步回调。 |
| [getShortcutInfo](arkts-ability-launcherbundlemanager-getshortcutinfo-f-sys.md) | 查询当前用户下指定应用的快捷方式信息ShortcutInfo，只支持查询主应用的ShortcutInfo，查询分身应用请使用[getShortcutInfoByAppIndex](arkts-ability-launcherbundlemanager-getshortcutinfobyappindex-f-sys.md)。使用callback异步回调。 |
| [getShortcutInfo](arkts-ability-launcherbundlemanager-getshortcutinfo-f-sys.md) | 查询当前用户下指定应用的快捷方式信息ShortcutInfo，只支持查询主应用的ShortcutInfo，查询分身应用请使用[getShortcutInfoByAppIndex](arkts-ability-launcherbundlemanager-getshortcutinfobyappindex-f-sys.md)。使用Promise异步回调。 |
| [getShortcutInfoByAppIndex](arkts-ability-launcherbundlemanager-getshortcutinfobyappindex-f-sys.md) | 查询当前用户下指定分身应用的快捷方式信息ShortcutInfo。 |
| [getShortcutInfoSync](arkts-ability-launcherbundlemanager-getshortcutinfosync-f-sys.md) | 查询当前用户下指定应用的快捷方式信息ShortcutInfo，只支持查询主应用的ShortcutInfo，查询分身应用请使用[getShortcutInfoByAppIndex](arkts-ability-launcherbundlemanager-getshortcutinfobyappindex-f-sys.md)。 |
| [getShortcutInfoSync](arkts-ability-launcherbundlemanager-getshortcutinfosync-f-sys.md) | 查询指定用户下指定应用的快捷方式信息ShortcutInfo，只支持查询主应用的ShortcutInfo，查询分身应用请使用[getShortcutInfoByAppIndex](arkts-ability-launcherbundlemanager-getshortcutinfobyappindex-f-sys.md)。 |
| [startShortcut](arkts-ability-launcherbundlemanager-startshortcut-f-sys.md) | 拉起指定ShortcutInfo中的ability。使用Promise异步回调。 |
| [startShortcutWithReason](arkts-ability-launcherbundlemanager-startshortcutwithreason-f-sys.md) | 根据指定的快捷方式信息，拉起对应的Ability，并携带快捷方式的启动原因。使用Promise异步回调。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [LauncherAbilityInfo](arkts-ability-launcherbundlemanager-launcherabilityinfo-t.md) | LauncherAbilityInfo信息。 |
| [ParameterItem](arkts-ability-launcherbundlemanager-parameteritem-t.md) | 快捷方式配置信息中的自定义数据。 |
| [ShortcutInfo](arkts-ability-launcherbundlemanager-shortcutinfo-t.md) | 应用[module.json5配置文件](../../../quick-start/module-configuration-file.md#shortcuts标签)中定义的快捷方式信息。 |
| [ShortcutWant](arkts-ability-launcherbundlemanager-shortcutwant-t.md) | 快捷方式内定义的目标[wants](../../../quick-start/module-configuration-file.md#wants标签)信息集合。 |
