# SpringLoadingDragInfos

定义触发悬停检测时拖拽事件信息的接口。该接口提供了拖拽数据摘要和拖拽事件额外信息，应用程序可以据此决定是否响应悬停检测回调。

**起始版本：** 20

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## dataSummary

```TypeScript
dataSummary?: unifiedDataChannel.Summary
```

拖拽数据的摘要，默认为null。

**类型：** unifiedDataChannel.Summary

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## extraInfos

```TypeScript
extraInfos?: string
```

拖拽事件额外信息，默认为空字符串。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

