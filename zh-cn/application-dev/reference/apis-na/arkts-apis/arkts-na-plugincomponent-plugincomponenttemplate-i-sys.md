# PluginComponentTemplate（系统接口）

定义插件组件模板信息，用于与提供方定义的组件绑定。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface PluginComponentTemplate--><!--Device-unnamed-export interface PluginComponentTemplate-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
bundleName: string | undefined
```

提供方应用的bundleName。使用绝对路径提供模板时不需要填写，使用应用包提供模板时需要填写。

**类型：** string \| undefined

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PluginComponentTemplate-bundleName: string | undefined--><!--Device-PluginComponentTemplate-bundleName: string | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## source

```TypeScript
source: string | undefined
```

组件模板，取值可为模板绝对路径（不建议）、相对HAP包的相对路径（多HAP场景使用“相对路径&模块名称”格式）或FA模型下的AbilityName。

**类型：** string \| undefined

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PluginComponentTemplate-source: string | undefined--><!--Device-PluginComponentTemplate-source: string | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

