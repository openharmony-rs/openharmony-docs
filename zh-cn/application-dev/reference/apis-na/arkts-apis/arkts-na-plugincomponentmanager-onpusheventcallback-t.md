# OnPushEventCallback

```TypeScript
export type OnPushEventCallback = (source: Want, template: PluginComponentTemplate, data: KVObject,
    extraData: KVObject) => void
```

对应push事件的监听回调函数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-pluginComponentManager-export type OnPushEventCallback = (source: Want, template: PluginComponentTemplate, data: KVObject,    extraData: KVObject) => void--><!--Device-pluginComponentManager-export type OnPushEventCallback = (source: Want, template: PluginComponentTemplate, data: KVObject,    extraData: KVObject) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | push事件发送方相关信息。 |
| template | [PluginComponentTemplate](../../apis-arkui/arkts-apis/arkts-arkui-plugincomponent-plugincomponenttemplate-i.md) | 是 | 组件模板。 |
| data | [KVObject](../../apis-arkui/arkts-apis/arkts-arkui-plugincomponentmanager-kvobject-t.md) | 是 | push事件中传递的数据内容，以键值对形式存储，键和值类型由业务定义。 |
| extraData | [KVObject](../../apis-arkui/arkts-apis/arkts-arkui-plugincomponentmanager-kvobject-t.md) | 是 | push事件中传递的附加数据，以键值对形式存储，键和值类型由业务定义。 |

