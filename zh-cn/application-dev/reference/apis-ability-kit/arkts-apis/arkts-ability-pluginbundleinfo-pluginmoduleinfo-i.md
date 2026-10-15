# PluginModuleInfo

```TypeScript
export interface PluginModuleInfo
```

插件的模块信息。用于描述插件模块的名称和功能说明。

**起始版本：** 26.0.0

<!--Device-unnamed-export interface PluginModuleInfo--><!--Device-unnamed-export interface PluginModuleInfo-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## description

```TypeScript
readonly description: string
```

插件模块的描述信息。对应[module.json5配置文件](../../../quick-start/module-configuration-file.md#配置文件标签)中配置的description字段。

**类型：** string

**起始版本：** 26.0.0

<!--Device-PluginModuleInfo-readonly description: string--><!--Device-PluginModuleInfo-readonly description: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## descriptionId

```TypeScript
readonly descriptionId: number
```

插件模块描述的资源ID值。是编译构建时根据插件配置的description自动生成的资源ID。

**类型：** number

**起始版本：** 26.0.0

<!--Device-PluginModuleInfo-readonly descriptionId: long--><!--Device-PluginModuleInfo-readonly descriptionId: long-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## moduleName

```TypeScript
readonly moduleName: string
```

插件模块的名称。对应[module.json5配置文件](../../../quick-start/module-configuration-file.md#配置文件标签)中配置的name字段。

**类型：** string

**起始版本：** 26.0.0

<!--Device-PluginModuleInfo-readonly moduleName: string--><!--Device-PluginModuleInfo-readonly moduleName: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core
