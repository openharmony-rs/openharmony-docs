# RequestCallbackParameters

pluginComponentManager.request方法接收到的回调结果。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-pluginComponentManager-export interface RequestCallbackParameters--><!--Device-pluginComponentManager-export interface RequestCallbackParameters-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## componentTemplate

```TypeScript
componentTemplate: PluginComponentTemplate
```

组件模板。

**类型：** [PluginComponentTemplate](../../apis-arkui/arkts-apis/arkts-arkui-plugincomponent-plugincomponenttemplate-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RequestCallbackParameters-componentTemplate: PluginComponentTemplate--><!--Device-RequestCallbackParameters-componentTemplate: PluginComponentTemplate-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## data

```TypeScript
data: KVObject
```

组件数据，以键值对形式存储，键和值类型由业务定义。

**类型：** [KVObject](../../apis-arkui/arkts-apis/arkts-arkui-plugincomponentmanager-kvobject-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RequestCallbackParameters-data: KVObject--><!--Device-RequestCallbackParameters-data: KVObject-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## extraData

```TypeScript
extraData: KVObject
```

附加数据。该字段为可选字段，不提供时默认不包含在返回结果中。

**类型：** [KVObject](../../apis-arkui/arkts-apis/arkts-arkui-plugincomponentmanager-kvobject-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RequestCallbackParameters-extraData: KVObject--><!--Device-RequestCallbackParameters-extraData: KVObject-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

