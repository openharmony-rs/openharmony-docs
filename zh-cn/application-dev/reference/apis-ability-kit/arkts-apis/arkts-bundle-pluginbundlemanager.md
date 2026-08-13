# @ohos.bundle.pluginBundleManager

本模块提供应用对自分发插件的管理能力，包括安装、卸载本地插件。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace pluginBundleManager--><!--Device-unnamed-declare namespace pluginBundleManager-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getAllLocalPluginInfoForSelf](arkts-ability-pluginbundlemanager-getalllocalplugininfoforself-f.md#getAllLocalPluginInfoForSelf) | 查询当前应用中所有自分发插件的信息。使用Promise异步回调。 |
| [installLocalPlugin](arkts-ability-pluginbundlemanager-installlocalplugin-f.md#installLocalPlugin) | 为当前应用安装自分发插件（即应用通过自有渠道分发、自主管理的插件）。使用Promise异步回调。 |
| [uninstallLocalPlugin](arkts-ability-pluginbundlemanager-uninstalllocalplugin-f.md#uninstallLocalPlugin) | 卸载当前应用已通过自分发方式安装的指定插件。使用Promise异步回调。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [PluginBundleInfo](arkts-ability-pluginbundlemanager-pluginbundleinfo-t.md) | 插件信息。 |
| [PluginModuleInfo](arkts-ability-pluginbundlemanager-pluginmoduleinfo-t.md) | 插件的模块信息。 |

