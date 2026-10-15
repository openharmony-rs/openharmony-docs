# PluginBundleInfo

```TypeScript
export interface PluginBundleInfo
```

插件信息，通过接口[pluginBundleManager.getAllLocalPluginInfoForSelf](arkts-ability-pluginbundlemanager-getalllocalplugininfoforself-f.md)获取当前应用已通过自分发方式安装的所有插件信息。该信息包含插件的名称、图标、版本号及模块信息，用于管理已安装的插件，并基于版本号和模块信息进行兼容性检查与更新。

**起始版本：** 26.0.0

<!--Device-unnamed-export interface PluginBundleInfo--><!--Device-unnamed-export interface PluginBundleInfo-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## icon

```TypeScript
readonly icon: string
```

插件的图标。对应[app.json5](../../../quick-start/app-configuration-file.md#配置文件标签)中配置的icon字段。

**类型：** string

**起始版本：** 26.0.0

<!--Device-PluginBundleInfo-readonly icon: string--><!--Device-PluginBundleInfo-readonly icon: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## iconId

```TypeScript
readonly iconId: number
```

插件图标的资源ID值。是编译构建时根据插件配置的icon自动生成的资源ID。

**类型：** number

**起始版本：** 26.0.0

<!--Device-PluginBundleInfo-readonly iconId: long--><!--Device-PluginBundleInfo-readonly iconId: long-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## label

```TypeScript
readonly label: string
```

插件的名称。对应[app.json5](../../../quick-start/app-configuration-file.md#配置文件标签)中配置的label字段。

**类型：** string

**起始版本：** 26.0.0

<!--Device-PluginBundleInfo-readonly label: string--><!--Device-PluginBundleInfo-readonly label: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## labelId

```TypeScript
readonly labelId: number
```

插件名称的资源ID值。是编译构建时根据插件配置的label自动生成的资源ID。

**类型：** number

**起始版本：** 26.0.0

<!--Device-PluginBundleInfo-readonly labelId: long--><!--Device-PluginBundleInfo-readonly labelId: long-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## pluginBundleName

```TypeScript
readonly pluginBundleName: string
```

安装插件的应用包名。对应[app.json5](../../../quick-start/app-configuration-file.md#配置文件标签)中配置的bundleName字段。

**类型：** string

**起始版本：** 26.0.0

<!--Device-PluginBundleInfo-readonly pluginBundleName: string--><!--Device-PluginBundleInfo-readonly pluginBundleName: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## pluginModuleInfos

```TypeScript
readonly pluginModuleInfos: Array<PluginModuleInfo>
```

插件的模块信息。

**类型：** Array&lt;[PluginModuleInfo](arkts-ability-pluginbundleinfo-pluginmoduleinfo-i.md)&gt;

**起始版本：** 26.0.0

<!--Device-PluginBundleInfo-readonly pluginModuleInfos: Array<PluginModuleInfo>--><!--Device-PluginBundleInfo-readonly pluginModuleInfos: Array<PluginModuleInfo>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## versionCode

```TypeScript
readonly versionCode: number
```

插件的版本号。对应[app.json5](../../../quick-start/app-configuration-file.md#配置文件标签)中配置的versionCode字段。

**类型：** number

**起始版本：** 26.0.0

<!--Device-PluginBundleInfo-readonly versionCode: long--><!--Device-PluginBundleInfo-readonly versionCode: long-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## versionName

```TypeScript
readonly versionName: string
```

插件的版本名称。对应[app.json5](../../../quick-start/app-configuration-file.md#配置文件标签)中配置的versionName字段。

**类型：** string

**起始版本：** 26.0.0

<!--Device-PluginBundleInfo-readonly versionName: string--><!--Device-PluginBundleInfo-readonly versionName: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core
