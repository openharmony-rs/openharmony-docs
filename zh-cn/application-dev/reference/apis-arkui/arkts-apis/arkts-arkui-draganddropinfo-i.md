# DragAndDropInfo

拖拽过程中监听到status改变时上报的数据。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## event

```TypeScript
event: DragEvent
```

当前状态所对应的拖拽事件。通过dragController发起的dragEvent仅支持获取result和behavior，且用于拖拽结束状态。

**类型：** DragEvent

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## extraParams

```TypeScript
extraParams?: string
```

设置拖拽事件额外信息，具体功能暂未实现。默认值为空。

**类型：** string

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## status

```TypeScript
status: DragStatus
```

当前拖拽状态（启动和结束）。

**类型：** DragStatus

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

