# OnPushEventCallback

```TypeScript
export type OnPushEventCallback = (source: Want, template: PluginComponentTemplate, data: KVObject,
    extraData: KVObject) => void
```

对应push事件的监听回调函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-pluginComponentManager-export type OnPushEventCallback = (source: Want, template: PluginComponentTemplate, data: KVObject,    extraData: KVObject) => void--><!--Device-pluginComponentManager-export type OnPushEventCallback = (source: Want, template: PluginComponentTemplate, data: KVObject,    extraData: KVObject) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | push事件发送方相关信息。  |
| template | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 组件模板。  |
| data | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | push事件中传递的数据内容，以键值对形式存储，键和值类型由业务定义。  |
| extraData | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | push事件中传递的附加数据，以键值对形式存储，键和值类型由业务定义。  |

