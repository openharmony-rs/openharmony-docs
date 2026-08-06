# @ohos.bundle.shortcutManager

本模块提供应用对于\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_的管理能力，包括设置快捷方式是否显示等。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-unnamed-declare namespace shortcutManager--><!--Device-unnamed-declare namespace shortcutManager-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addDesktopShortcutInfo](arkts-ability-shortcutmanager-adddesktopshortcutinfo-f.md#adddesktopshortcutinfo) | 增加指定用户的快捷方式信息。使用Promise异步回调。 |
| [addDynamicShortcutInfos](arkts-ability-shortcutmanager-adddynamicshortcutinfos-f.md#adddynamicshortcutinfos) | 添加指定用户的动态快捷方式。 |
| [deleteDesktopShortcutInfo](arkts-ability-shortcutmanager-deletedesktopshortcutinfo-f.md#deletedesktopshortcutinfo) | 删除指定用户的快捷方式信息。使用Promise异步回调。 |
| [deleteDynamicShortcutInfos](arkts-ability-shortcutmanager-deletedynamicshortcutinfos-f.md#deletedynamicshortcutinfos) | 删除指定的动态快捷方式。 |
| [getAllDesktopShortcutInfo](arkts-ability-shortcutmanager-getalldesktopshortcutinfo-f.md#getalldesktopshortcutinfo) | 查询指定用户的所有快捷方式信息。 |
| [getAllShortcutInfoForSelf](arkts-ability-shortcutmanager-getallshortcutinfoforself-f.md#getallshortcutinfoforself) | 查询当前应用\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_中定义的所有快捷方式信息。使用Promise异步回调。 |
| [getShortcutInfoByAbility](arkts-ability-shortcutmanager-getshortcutinfobyability-f.md#getshortcutinfobyability) | 查询指定用户下指定UIAbility的快捷方式信息。 |
| [isShortcutSupported](arkts-ability-shortcutmanager-isshortcutsupported-f.md#isshortcutsupported) | 查询当前设备是否支持快捷方式。 |
| [setShortcutVisibleForSelf](arkts-ability-shortcutmanager-setshortcutvisibleforself-f.md#setshortcutvisibleforself) | 设置当前应用指定的快捷方式是否显示。使用Promise异步回调。 |
| [setShortcutsEnabled](arkts-ability-shortcutmanager-setshortcutsenabled-f.md#setshortcutsenabled) | 设置启用或禁用传入的静态快捷方式。使用Promise异步回调。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ParameterItem](arkts-ability-shortcutmanager-parameteritem-t.md) | 快捷方式配置信息中的自定义数据。 |
| [ShortcutInfo](arkts-ability-shortcutmanager-shortcutinfo-t.md) | 应用\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_中定义的快捷方式信息。 |
| [ShortcutWant](arkts-ability-shortcutmanager-shortcutwant-t.md) | 快捷方式内定义的目标\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_信息集合。 |

