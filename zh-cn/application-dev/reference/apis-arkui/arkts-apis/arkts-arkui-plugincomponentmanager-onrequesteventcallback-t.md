# OnRequestEventCallback

```TypeScript
type OnRequestEventCallback = (source: Want, name: string, data: KVObject) => RequestEventResult
```

插件组件request事件回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-pluginComponentManager-type OnRequestEventCallback = (source: Want, name: string, data: KVObject) => RequestEventResult--><!--Device-pluginComponentManager-type OnRequestEventCallback = (source: Want, name: string, data: KVObject) => RequestEventResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | [Want](arkts-arkui-want-t-sys.md) | 是 |  |
| name | string | 是 |  |
| data | [KVObject](arkts-arkui-plugincomponentmanager-kvobject-t.md) | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RequestEventResult](arkts-arkui-plugincomponentmanager-requesteventresult-i.md) | 返回request事件结果。  |

