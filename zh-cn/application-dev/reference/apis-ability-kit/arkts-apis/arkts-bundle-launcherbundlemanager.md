# @ohos.bundle.launcherBundleManager

本模块支持launcher应用（桌面有图标的应用）所需的查询能力，支持 [LauncherAbilityInfo](arkts-ability-launcherabilityinfo-i.md#LauncherAbilityInfo)信息的查询。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace launcherBundleManager--><!--Device-unnamed-declare namespace launcherBundleManager-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getLauncherAbilityInfoSync](arkts-ability-launcherbundlemanager-getlauncherabilityinfosync-f.md#getLauncherAbilityInfoSync) | 查询指定bundleName及用户的[LauncherAbilityInfo](arkts-ability-launcherabilityinfo-i.md#LauncherAbilityInfo)。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getAllLauncherAbilityInfo](arkts-ability-launcherbundlemanager-getalllauncherabilityinfo-f-sys.md#getAllLauncherAbilityInfo) | 查询指定用户下所有应用的[LauncherAbilityInfo](arkts-ability-launcherabilityinfo-i.md#LauncherAbilityInfo)。使用callback异步回调。 |
| [getAllLauncherAbilityInfo](arkts-ability-launcherbundlemanager-getalllauncherabilityinfo-f-sys.md#getAllLauncherAbilityInfo（系统接口）) | 查询指定用户下所有应用的[LauncherAbilityInfo](arkts-ability-launcherabilityinfo-i.md#LauncherAbilityInfo)。使用Promise异步回调。 |
| [getLauncherAbilityInfo](arkts-ability-launcherbundlemanager-getlauncherabilityinfo-f-sys.md#getLauncherAbilityInfo) | 查询指定bundleName及用户的[LauncherAbilityInfo](arkts-ability-launcherabilityinfo-i.md#LauncherAbilityInfo)。使用callback异步 回调。 |
| [getLauncherAbilityInfo](arkts-ability-launcherbundlemanager-getlauncherabilityinfo-f-sys.md#getLauncherAbilityInfo（系统接口）) | 查询指定bundleName及用户的[LauncherAbilityInfo](arkts-ability-launcherabilityinfo-i.md#LauncherAbilityInfo)。使用Promise异步回 调。 |
| [getShortcutInfo](arkts-ability-launcherbundlemanager-getshortcutinfo-f-sys.md#getShortcutInfo) | 查询当前用户下指定应用的快捷方式信息ShortcutInfo，只支持查询主应用的ShortcutInfo，查询分身应用请使用 [getShortcutInfoByAppIndex](arkts-ability-launcherbundlemanager-getshortcutinfobyappindex-f-sys.md#getShortcutInfoByAppIndex（系统接口）)。使用callback异步回调。 获取调用方自身的信息时不需要权限。 |
| [getShortcutInfo](arkts-ability-launcherbundlemanager-getshortcutinfo-f-sys.md#getShortcutInfo（系统接口）) | 查询当前用户下指定应用的快捷方式信息ShortcutInfo，只支持查询主应用的ShortcutInfo，查询分身应用请使用 [getShortcutInfoByAppIndex](arkts-ability-launcherbundlemanager-getshortcutinfobyappindex-f-sys.md#getShortcutInfoByAppIndex（系统接口）)。使用Promise异步回调。 获取调用方自身的信息时不需要权限。 |
| [getShortcutInfoByAppIndex](arkts-ability-launcherbundlemanager-getshortcutinfobyappindex-f-sys.md#getShortcutInfoByAppIndex) | 查询当前用户下指定分身应用的快捷方式信息ShortcutInfo。 调用方获取自己的信息时不需要权限。 |
| [getShortcutInfoSync](arkts-ability-launcherbundlemanager-getshortcutinfosync-f-sys.md#getShortcutInfoSync) | 查询当前用户下指定应用的快捷方式信息ShortcutInfo，只支持查询主应用的ShortcutInfo，查询分身应用请使用 [getShortcutInfoByAppIndex](arkts-ability-launcherbundlemanager-getshortcutinfobyappindex-f-sys.md#getShortcutInfoByAppIndex（系统接口）)。 获取调用方自身的信息时不需要权限。 |
| [getShortcutInfoSync](arkts-ability-launcherbundlemanager-getshortcutinfosync-f-sys.md#getShortcutInfoSync（系统接口）) | 查询指定用户下指定应用的快捷方式信息ShortcutInfo，只支持查询主应用的ShortcutInfo，查询分身应用请使用 [getShortcutInfoByAppIndex](arkts-ability-launcherbundlemanager-getshortcutinfobyappindex-f-sys.md#getShortcutInfoByAppIndex（系统接口）)。 获取调用方自身的信息时不需要权限。 |
| [startShortcut](arkts-ability-launcherbundlemanager-startshortcut-f-sys.md#startShortcut) | 拉起指定ShortcutInfo中的ability。使用Promise异步回调。 |
| [startShortcutWithReason](arkts-ability-launcherbundlemanager-startshortcutwithreason-f-sys.md#startShortcutWithReason) | 根据指定的快捷方式信息，拉起对应的Ability，并携带快捷方式的启动原因。使用Promise异步回调。 被拉起方可以通过[LaunchParam](arkts-ability-abilityconstant-launchparam-i.md#LaunchParam)的launchReasonMessage字段获取到 启动原因，并根据启动原因进行业务逻辑处理。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [LauncherAbilityInfo](arkts-ability-launcherbundlemanager-launcherabilityinfo-t.md) | LauncherAbilityInfo信息。 |

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ParameterItem](arkts-ability-launcherbundlemanager-parameteritem-t-sys.md) | 快捷方式配置信息中的自定义数据。 |
| [ShortcutInfo](arkts-ability-launcherbundlemanager-shortcutinfo-t-sys.md) | 应用[module.json5配置文件](../../../quick-start/module-configuration-file.md#shortcuts标签)中定义的快捷方式信息。 |
| [ShortcutWant](arkts-ability-launcherbundlemanager-shortcutwant-t-sys.md) | 快捷方式内定义的目标[wants](../../../quick-start/module-configuration-file.md#wants标签)信息集合。 |
<!--DelEnd-->

