# OnRequestEventCallback

```TypeScript
type OnRequestEventCallback = (source: Want, name: string, data: KVObject) => RequestEventResult
```

对应request事件的监听回调函数。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-pluginComponentManager-type OnRequestEventCallback = (source: Want, name: string, data: KVObject) => RequestEventResult--><!--Device-pluginComponentManager-type OnRequestEventCallback = (source: Want, name: string, data: KVObject) => RequestEventResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | request请求发送方相关信息。 |
| name | string | 是 | 请求的组件名称。 |
| data | [KVObject](../../apis-na/arkts-apis/arkts-na-plugincomponentmanager-kvobject-t.md) | 是 | request事件中传递的数据内容，以键值对形式存储，键和值类型由业务定义。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RequestEventResult](../../apis-na/arkts-apis/arkts-na-plugincomponentmanager-requesteventresult-i.md) | 返回request事件结果。 |

