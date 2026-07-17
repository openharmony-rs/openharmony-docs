# DragEvent

拖拽事件信息。

**起始版本：** 7

<!--Device-unnamed-declare interface DragEvent--><!--Device-unnamed-declare interface DragEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## executeDropAnimation

```TypeScript
executeDropAnimation(customDropAnimation: Callback<void>): void
```

设置自定义落位动效的执行函数，仅在[useCustomDropAnimation](arkts-arkui-common-dragevent-i.md#usecustomdropanimation)为true时有效。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-DragEvent-executeDropAnimation(customDropAnimation: Callback<void>): void--><!--Device-DragEvent-executeDropAnimation(customDropAnimation: Callback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| customDropAnimation | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<void> | 是 | 在此回调函数中实现自定义落位动效。<br/> **说明：** <br/>1. 该接口仅在onDrop回调中使用有效。<br/> 2.使用前需设置useCustomDropAnimation为true，否则该接口不生效。<br/> 3. 不要在动画callback中实现与动效无关的逻辑，避免影响执行效率。 |

## getData

```TypeScript
getData(): UnifiedData
```

获取拖拽相关数据。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DragEvent-getData(): UnifiedData--><!--Device-DragEvent-getData(): UnifiedData-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [UnifiedData](arkts-arkui-unifieddata-t.md) | 从DragEvent中获取拖拽相关数据。数据获取结果请参考错误码说明。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [190001](../errorcode-uicontext.md#190001-无效的uicontext对象) | Data not found. |
| [190002](../errorcode-uicontext.md#190002-无效的回调函数) | Data error. |

## getDisplayId

```TypeScript
getDisplayId(): number
```

获取当前拖拽事件发生时所在的屏幕ID，不支持在[onDragEnd](arkts-arkui-common-commonmethod-c.md#ondragend-1)阶段使用。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-DragEvent-getDisplayId(): number--><!--Device-DragEvent-getDisplayId(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 当前拖拽事件发生时所在的屏幕ID。 |

## getDisplayX

```TypeScript
getDisplayX(): number
```

获取当前拖拽点相对于屏幕左上角的x轴坐标。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DragEvent-getDisplayX(): number--><!--Device-DragEvent-getDisplayX(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 当前拖拽点相对于屏幕左上角的x轴坐标，单位为vp。 |

## getDisplayY

```TypeScript
getDisplayY(): number
```

获取当前拖拽点相对于屏幕左上角的y轴坐标。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DragEvent-getDisplayY(): number--><!--Device-DragEvent-getDisplayY(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 当前拖拽点相对于屏幕左上角的y轴坐标，单位为vp。 |

## getDragSource

```TypeScript
getDragSource(): string
```

获取拖起方包名。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-DragEvent-getDragSource(): string--><!--Device-DragEvent-getDragSource(): string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 拖起方的包名。 |

## getGlobalDisplayX

```TypeScript
getGlobalDisplayX(): number
```

当前拖拽点相对于全局屏幕的左上角的X坐标。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-DragEvent-getGlobalDisplayX(): number--><!--Device-DragEvent-getGlobalDisplayX(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回当前拖拽点相对于全局屏幕的左上角的X坐标。<br/>单位：vp，取值范围：[0, +∞) |

## getGlobalDisplayY

```TypeScript
getGlobalDisplayY(): number
```

当前拖拽点相对于全局屏幕的左上角的Y坐标。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-DragEvent-getGlobalDisplayY(): number--><!--Device-DragEvent-getGlobalDisplayY(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回当前拖拽点相对于全局屏幕的左上角的Y坐标。<br/>单位：vp，取值范围：[0, +∞) |

## getModifierKeyState

```TypeScript
getModifierKeyState?(keys: Array<string>): boolean
```

获取功能键按压状态。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-DragEvent-getModifierKeyState?(keys: Array<string>): boolean--><!--Device-DragEvent-getModifierKeyState?(keys: Array<string>): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keys | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<string> | 是 | 获取功能键按压状态。报错信息请参考以下错误码。支持功能键 'Ctrl' \| 'Alt' \| 'Shift'。<br/>**说明：**<br/>此接口不支持在手写笔场景下使用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否被按下，返回true表示被按下，返回false表示未被按下 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Incorrect parameter types. 2. Parameter verification failed. |

## getPreviewRect

```TypeScript
getPreviewRect(): Rectangle
```

获取拖拽预览图相对于当前窗口的位置，以及预览图尺寸信息。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DragEvent-getPreviewRect(): Rectangle--><!--Device-DragEvent-getPreviewRect(): Rectangle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Rectangle](arkts-arkui-common-rectangle-i.md) | 拖拽预览图相对于当前窗口的位置，以及预览图尺寸信息，单位vp，其中x和y代表预览图左上角的窗口坐标，width和height代表预览图的尺寸。 |

## getResult

```TypeScript
getResult(): DragResult
```

获取拖拽结果。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DragEvent-getResult(): DragResult--><!--Device-DragEvent-getResult(): DragResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DragResult](arkts-arkui-common-dragresult-e.md) | 从DragEvent中获取的拖拽结果。 |

## getSummary

```TypeScript
getSummary(): Summary
```

获取所拖拽数据的概要，包括数据类型及大小信息；在延迟拖拽场景下，只能获取到数据类型信息。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DragEvent-getSummary(): Summary--><!--Device-DragEvent-getSummary(): Summary-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Summary](../../apis-arkdata/arkts-apis/arkts-arkdata-unifieddatachannel-summary-c.md) | 拖拽相关数据的概要。 |

## getVelocity

```TypeScript
getVelocity(): number
```

获取当前拖拽的主方向拖动速度。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DragEvent-getVelocity(): number--><!--Device-DragEvent-getVelocity(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 当前拖拽的主方向拖动速度。为xy轴方向速度的平方和的算术平方根，单位为vp。 |

## getVelocityX

```TypeScript
getVelocityX(): number
```

获取当前拖拽的x轴方向拖动速度。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DragEvent-getVelocityX(): number--><!--Device-DragEvent-getVelocityX(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 当前拖拽的x轴方向拖动速度。坐标轴原点为屏幕左上角，单位为vp，分正负方向速度，从左往右为正，反之为负。 |

## getVelocityY

```TypeScript
getVelocityY(): number
```

获取当前拖拽的y轴方向拖动速度。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DragEvent-getVelocityY(): number--><!--Device-DragEvent-getVelocityY(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 当前拖拽的y轴方向拖动速度。坐标轴原点为屏幕左上角，单位为vp，分正负方向速度，从上往下为正，反之为负。 |

## getWindowX

```TypeScript
getWindowX(): number
```

获取拖拽点相对于窗口左上角的x轴坐标。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DragEvent-getWindowX(): number--><!--Device-DragEvent-getWindowX(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 当前拖拽点相对于窗口左上角的x轴坐标，单位为vp。 |

## getWindowY

```TypeScript
getWindowY(): number
```

获取拖拽点相对于窗口左上角的y轴坐标。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DragEvent-getWindowY(): number--><!--Device-DragEvent-getWindowY(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 当前拖拽点相对于窗口左上角的y轴坐标，单位为vp。 |

## getX

```TypeScript
getX(): number
```

当前拖拽点相对于窗口左上角的x轴坐标，单位为vp。

> **说明：**

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [getWindowX](arkts-arkui-common-dragevent-i.md#getwindowx-1)

<!--Device-DragEvent-getX(): number--><!--Device-DragEvent-getX(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回当前拖拽点相对于窗口左上角的x轴坐标。<br/>单位：vp |

## getY

```TypeScript
getY(): number
```

当前拖拽点相对于窗口左上角的y轴坐标，单位为vp。

> **说明：**

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [getWindowY](arkts-arkui-common-dragevent-i.md#getwindowy-1)

<!--Device-DragEvent-getY(): number--><!--Device-DragEvent-getY(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回当前拖拽点相对于窗口左上角的y轴坐标。<br/>单位：vp |

## isRemote

```TypeScript
isRemote(): boolean
```

获取是否是跨设备拖拽，跨设备拖拽时为true。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-DragEvent-isRemote(): boolean--><!--Device-DragEvent-isRemote(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否是跨设备拖拽，返回true表示是跨设备拖拽，返回false表示不是跨设备拖拽。 |

## setData

```TypeScript
setData(unifiedData: UnifiedData): void
```

向DragEvent中设置用于拖拽的数据。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DragEvent-setData(unifiedData: UnifiedData): void--><!--Device-DragEvent-setData(unifiedData: UnifiedData): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| unifiedData | [UnifiedData](arkts-arkui-unifieddata-t.md) | 是 | 拖拽相关的数据。 |

## setDataLoadParams

```TypeScript
setDataLoadParams(dataLoadParams: DataLoadParams): void
```

设置起拖方延迟提供数据。使用此方法向系统提供数据加载参数，而不是直接提供完整的数据对象。当用户在目标应用程序上落入时，系统将使用此参数从起拖方请求实际数据。与[setData](arkts-arkui-common-dragevent-i.md#setdata-1)方法同时使用，以最后调用的方法为准。该接口仅在[onDragStart](arkts-arkui-common-commonmethod-c.md#ondragstart-1)回调中生效。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-DragEvent-setDataLoadParams(dataLoadParams: DataLoadParams): void--><!--Device-DragEvent-setDataLoadParams(dataLoadParams: DataLoadParams): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataLoadParams | [DataLoadParams](../../apis-arkdata/arkts-apis/arkts-arkdata-unifieddatachannel-dataloadparams-i.md) | 是 | 落入操作时使用的数据加载参数。 |

## setResult

```TypeScript
setResult(dragResult: DragResult): void
```

在DragEvent中设置拖拽结果。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DragEvent-setResult(dragResult: DragResult): void--><!--Device-DragEvent-setResult(dragResult: DragResult): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dragResult | [DragResult](arkts-arkui-common-dragresult-e.md) | 是 | 拖拽结果。 |

## startDataLoading

```TypeScript
startDataLoading(options: DataSyncOptions): string
```

异步获取拖拽数据，并通知开发者当前数据同步进度，仅支持在onDrop阶段使用。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-DragEvent-startDataLoading(options: DataSyncOptions): string--><!--Device-DragEvent-startDataLoading(options: DataSyncOptions): string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DataSyncOptions](arkts-arkui-datasyncoptions-t.md) | 是 | 获取拖拽数据时的参数，包含目标路径、文件冲突选项、进度条类型等。数据传输过程中可使用[cancelDataLoading](../arkts-apis/arkts-arkui-arkui-uicontext-dragcontroller-c.md#canceldataloading-1)接口取消数据加载。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 拖拽数据的标识，用于区分每次拖拽。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. |
| [190003](../errorcode-drag-event.md#190003-当前阶段不允许操作) | Operation not allowed for current phase. |

## autoHideComponentUniqueIds

```TypeScript
autoHideComponentUniqueIds?: number | number[]
```

设置拖拽过程中需要自动隐藏的组件uniqueId，支持传入单个uniqueId或数组。

仅在[onDragStart](arkts-arkui-common-commonmethod-c.md#ondragstart-1)回调中设置生效。拖拽成功发起后，系统会在显示拖拽预览窗口前隐藏目标组件。

若拖拽源本身也需要隐藏，需要同时传入拖拽源组件的uniqueId。

组件的uniqueId可通过[UIContext.getFrameNodeById()](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#getframenodebyid-1)配合[FrameNode.getUniqueId()](../arkts-apis/arkts-arkui-framenode-c.md#getuniqueid-1)获取。

开发者应在[onDragEnd](arkts-arkui-common-commonmethod-c.md#ondragend-1)或[onDrop](arkts-arkui-common-commonmethod-c.md#ondrop-1)中恢复组件显示状态。

**类型：** number | number[]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-DragEvent-autoHideComponentUniqueIds?: int | int[]--><!--Device-DragEvent-autoHideComponentUniqueIds?: int | int[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## dragBehavior

```TypeScript
dragBehavior: DragBehavior
```

切换复制和剪贴模式的角标显示状态。

默认值：DragBehavior.COPY。

**类型：** DragBehavior

**默认值：** COPY

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DragEvent-dragBehavior: DragBehavior--><!--Device-DragEvent-dragBehavior: DragBehavior-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## useCustomDropAnimation

```TypeScript
useCustomDropAnimation: boolean
```

当拖拽结束时，是否禁用系统默认落位动效。

应用可将该值设定为true来禁用系统默认落位动效，并实现自己的自定义落位动效。

当不配置或设置为false时，系统默认落位动效生效，当[setResult](arkts-arkui-common-dragevent-i.md#setresult-1)设置为DRAG_SUCCESSFUL时，落位为缩小消失动效，不为DRAG_SUCCESSFUL时，则为放大消失动效。

当未禁用系统默认落位动效时，应用不应再实现自定义动效，以避免动效上的冲突。

默认值：false

**类型：** boolean

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DragEvent-useCustomDropAnimation: boolean--><!--Device-DragEvent-useCustomDropAnimation: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

