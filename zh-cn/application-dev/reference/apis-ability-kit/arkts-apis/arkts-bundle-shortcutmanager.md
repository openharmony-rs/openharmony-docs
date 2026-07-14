# @ohos.bundle.shortcutManager

本模块提供应用对于[快捷方式](../../../../quick-start/typical-scenario-configuration.md)的管理能力，包括设置快捷方式是否显示等。

**起始版本：** 20

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getAllShortcutInfoForSelf](arkts-ability-getallshortcutinfoforself-f.md#getallshortcutinfoforself-1) | 查询当前应用[配置文件](../../../../quick-start/module-configuration-file.md#shortcuts标签)中定义的所有快捷方式信息。使用Promise异步回调。 |
| [isShortcutSupported](arkts-ability-isshortcutsupported-f.md#isshortcutsupported-1) | 查询当前设备是否支持快捷方式。 |
| [setShortcutVisibleForSelf](arkts-ability-setshortcutvisibleforself-f.md#setshortcutvisibleforself-1) | 设置当前应用指定的快捷方式是否显示。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [addDesktopShortcutInfo](arkts-ability-adddesktopshortcutinfo-f-sys.md#adddesktopshortcutinfo-1) | 增加指定用户的快捷方式信息。使用Promise异步回调。 |
| [addDynamicShortcutInfos](arkts-ability-adddynamicshortcutinfos-f-sys.md#adddynamicshortcutinfos-1) | 添加指定用户的动态快捷方式。 |
| [deleteDesktopShortcutInfo](arkts-ability-deletedesktopshortcutinfo-f-sys.md#deletedesktopshortcutinfo-1) | 删除指定用户的快捷方式信息。使用Promise异步回调。 |
| [deleteDynamicShortcutInfos](arkts-ability-deletedynamicshortcutinfos-f-sys.md#deletedynamicshortcutinfos-1) | 删除指定的动态快捷方式。 |
| [getAllDesktopShortcutInfo](arkts-ability-getalldesktopshortcutinfo-f-sys.md#getalldesktopshortcutinfo-1) | 查询指定用户的所有快捷方式信息。 |
| [getShortcutInfoByAbility](arkts-ability-getshortcutinfobyability-f-sys.md#getshortcutinfobyability-1) | 查询指定用户下指定UIAbility的快捷方式信息。 |
| [setShortcutsEnabled](arkts-ability-setshortcutsenabled-f-sys.md#setshortcutsenabled-1) | 设置启用或禁用传入的静态快捷方式。使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ParameterItem](arkts-ability-parameteritem-t-sys.md) | 快捷方式配置信息中的自定义数据。 |
| [ShortcutInfo](arkts-ability-shortcutinfo-t-sys.md) | 应用[module.json5配置文件](../../../../quick-start/module-configuration-file.md#shortcuts标签)中定义的快捷方式信息。 |
| [ShortcutWant](arkts-ability-shortcutwant-t-sys.md) | 快捷方式内定义的目标[wants](../../../../quick-start/module-configuration-file.md#wants标签)信息集合。 |
<!--DelEnd-->

