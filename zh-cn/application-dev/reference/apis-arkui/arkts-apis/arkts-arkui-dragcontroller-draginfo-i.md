# DragInfo

发起拖拽所需要的属性和拖拽时携带的信息。

**起始版本：** 10

<!--Device-dragController-interface DragInfo--><!--Device-dragController-interface DragInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { dragController } from '@kit.ArkUI';
```

## autoHideComponentUniqueIds

```TypeScript
autoHideComponentUniqueIds?: number | number[]
```

设置在主动拖拽过程中由系统自动隐藏的组件uniqueId，支持传入单个uniqueId或数组。

主动拖拽成功发起后，系统会在显示拖拽预览窗口前自动隐藏目标组件。

若主动拖拽源本身也需要被隐藏，需要同时传入其uniqueId。

组件的uniqueId可通过[UIContext.getFrameNodeById()](arkts-arkui-arkui-uicontext-uicontext-c.md#getframenodebyid)配合[FrameNode.getUniqueId()](arkts-arkui-framenode-c.md#getuniqueid)获取。

开发者需要在拖拽结束回调中按需恢复组件显示状态。

**类型：** number \| number[]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-DragInfo-autoHideComponentUniqueIds?: int | int[]--><!--Device-DragInfo-autoHideComponentUniqueIds?: int | int[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## data

```TypeScript
data?: unifiedDataChannel.UnifiedData
```

设置拖拽过程中携带的数据。

默认值：空

**类型：** unifiedDataChannel.UnifiedData

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DragInfo-data?: unifiedDataChannel.UnifiedData--><!--Device-DragInfo-data?: unifiedDataChannel.UnifiedData-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## dataLoadParams

```TypeScript
dataLoadParams?: unifiedDataChannel.DataLoadParams
```

设置拖起方延迟提供数据。调用此方法向系统提供数据加载参数，而非直接传入完整的数据对象。当用户将数据拖拽至目标应用程序并释放时，系统将使用此参数从起拖方请求实际数据。与data同时设置时，dataLoadParams生效。

默认值：空

**类型：** unifiedDataChannel.DataLoadParams

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-DragInfo-dataLoadParams?: unifiedDataChannel.DataLoadParams--><!--Device-DragInfo-dataLoadParams?: unifiedDataChannel.DataLoadParams-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## extraParams

```TypeScript
extraParams?: string
```

设置拖拽事件额外信息，具体功能暂未实现。

默认值：空

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DragInfo-extraParams?: string--><!--Device-DragInfo-extraParams?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## pointerId

```TypeScript
pointerId: number
```

设置启动拖拽时屏幕上触摸点的Id。取值范围为[0, 9]的整数。

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DragInfo-pointerId: number--><!--Device-DragInfo-pointerId: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## previewOptions

```TypeScript
previewOptions?: DragPreviewOptions
```

设置拖拽过程中背板图处理模式及数量角标的显示。

**类型：** DragPreviewOptions

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DragInfo-previewOptions?: DragPreviewOptions--><!--Device-DragInfo-previewOptions?: DragPreviewOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## touchPoint

```TypeScript
touchPoint?: TouchPoint
```

配置跟手点坐标。不配置时，左右居中，顶部向下偏移20%。

**类型：** TouchPoint

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DragInfo-touchPoint?: TouchPoint--><!--Device-DragInfo-touchPoint?: TouchPoint-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

