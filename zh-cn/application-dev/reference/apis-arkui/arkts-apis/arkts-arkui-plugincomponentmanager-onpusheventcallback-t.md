# OnPushEventCallback

```TypeScript
type OnPushEventCallback = (source: Want, template: PluginComponentTemplate, data: KVObject,
    extraData: KVObject) => void
```

插件组件push事件回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-pluginComponentManager-type OnPushEventCallback = (source: Want, template: PluginComponentTemplate, data: KVObject,
    extraData: KVObject) => void--><!--Device-pluginComponentManager-type OnPushEventCallback = (source: Want, template: PluginComponentTemplate, data: KVObject,
    extraData: KVObject) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | [Want](arkts-arkui-want-t-sys.md) | 是 |  |
| template | [PluginComponentTemplate](arkts-arkui-plugincomponent-plugincomponenttemplate-i.md) | 是 |  |
| data | [KVObject](arkts-arkui-plugincomponentmanager-kvobject-t.md) | 是 |  |
| extraData | [KVObject](arkts-arkui-plugincomponentmanager-kvobject-t.md) | 是 |  |

