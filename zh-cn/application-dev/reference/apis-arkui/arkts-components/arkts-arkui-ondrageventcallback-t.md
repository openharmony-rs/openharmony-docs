# OnDragEventCallback

```TypeScript
declare type OnDragEventCallback = (event: DragEvent, extraParams?: string) => void
```

拖拽事件的回调函数。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本15开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | DragEvent | 是 | event为拖拽事件信息，包括拖拽点坐标。 |
| extraParams | string | 否 | extraParams为拖拽事件额外信息，需要解析为JSON格式。 |

