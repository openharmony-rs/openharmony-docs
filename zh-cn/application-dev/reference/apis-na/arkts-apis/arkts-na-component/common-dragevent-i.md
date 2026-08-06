# DragEvent

DragEvent object description

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface DragEvent--><!--Device-unnamed-export declare interface DragEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## executeDropAnimation

```TypeScript
executeDropAnimation(customDropAnimation: VoidCallback): void
```

Setup one drop animation execution callback, which will be triggered by system when user drops. Use this way to implement the custom drop animation instead of doing it in onDrop, as the system will decide when to trigger the callback during the drop handling. [Note]: 1. Please set useCustomDropAnimation to true as well when using this method. 2. Do not implement the animation no-related logics in the callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragEvent-executeDropAnimation(customDropAnimation: VoidCallback): void--><!--Device-DragEvent-executeDropAnimation(customDropAnimation: VoidCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| customDropAnimation | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | the custom drop animation function. |

## getData

```TypeScript
getData(): UnifiedData | undefined
```

Get dragData from DragEvent.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragEvent-getData(): UnifiedData | undefined--><!--Device-DragEvent-getData(): UnifiedData | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | - get dragData, undefined will be returned if the internal runtime environment is broken. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [190001](../../../apis-arkui/errorcode-uicontext.md#190001-无效的uicontext对象) | Data not found. |
| [190002](../../../apis-arkui/errorcode-uicontext.md#190002-无效的回调函数) | Data error. |

## getDisplayId

```TypeScript
getDisplayId(): int
```

Get the id of display which the drag event is occuring on.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragEvent-getDisplayId(): int--><!--Device-DragEvent-getDisplayId(): int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int |  |

## getDisplayX

```TypeScript
getDisplayX(): double
```

X coordinate of the touch point relative to the left edge of the device screen.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragEvent-getDisplayX(): double--><!--Device-DragEvent-getDisplayX(): double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double |  |

## getDisplayY

```TypeScript
getDisplayY(): double
```

Y coordinate of the touch point relative to the upper edge of the device screen.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragEvent-getDisplayY(): double--><!--Device-DragEvent-getDisplayY(): double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double |  |

## getDragSource

```TypeScript
getDragSource(): string
```

Retrieve the bundle information of the drag source application.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragEvent-getDragSource(): string--><!--Device-DragEvent-getDragSource(): string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string |  |

## getGlobalDisplayX

```TypeScript
getGlobalDisplayX(): double
```

X coordinate of the point relative to the global display.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragEvent-getGlobalDisplayX(): double--><!--Device-DragEvent-getGlobalDisplayX(): double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double |  |

## getGlobalDisplayY

```TypeScript
getGlobalDisplayY(): double
```

Y coordinate of the point relative to the global display.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragEvent-getGlobalDisplayY(): double--><!--Device-DragEvent-getGlobalDisplayY(): double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double |  |

## getPreviewRect

```TypeScript
getPreviewRect(): Rectangle
```

Get the rectangle of drag window.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragEvent-getPreviewRect(): Rectangle--><!--Device-DragEvent-getPreviewRect(): Rectangle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | - getPreview rectangle. |

## getResult

```TypeScript
getResult(): DragResult
```

Get dragEvent result from DragEvent.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragEvent-getResult(): DragResult--><!--Device-DragEvent-getResult(): DragResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | - dragResult Data. |

## getSummary

```TypeScript
getSummary(): Summary | undefined
```

Get dragData summary from DragEvent.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragEvent-getSummary(): Summary | undefined--><!--Device-DragEvent-getSummary(): Summary | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | - get Summary Data, undefined will be returned if the internal runtime environment is broken. |

## getVelocity

```TypeScript
getVelocity(): double
```

Get the velocity of drag gesture.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragEvent-getVelocity(): double--><!--Device-DragEvent-getVelocity(): double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | - get velocity. |

## getVelocityX

```TypeScript
getVelocityX(): double
```

Get the x axis velocity of drag gesture.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragEvent-getVelocityX(): double--><!--Device-DragEvent-getVelocityX(): double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | - get x axis velocity. |

## getVelocityY

```TypeScript
getVelocityY(): double
```

Get the y axis velocity of drag gesture.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragEvent-getVelocityY(): double--><!--Device-DragEvent-getVelocityY(): double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | - get y axis velocity. |

## getWindowX

```TypeScript
getWindowX(): double
```

X coordinate of the touch point relative to the left edge of the current window.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragEvent-getWindowX(): double--><!--Device-DragEvent-getWindowX(): double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double |  |

## getWindowY

```TypeScript
getWindowY(): double
```

Y coordinate of the touch point relative to the left edge of the current window.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragEvent-getWindowY(): double--><!--Device-DragEvent-getWindowY(): double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double |  |

## isRemote

```TypeScript
isRemote(): boolean
```

Call this method to determine whether the current drag operation is a cross-device drag.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragEvent-isRemote(): boolean--><!--Device-DragEvent-isRemote(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean |  |

## setData

```TypeScript
setData(unifiedData: UnifiedData): void
```

Set dragData into DragEvent.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragEvent-setData(unifiedData: UnifiedData): void--><!--Device-DragEvent-setData(unifiedData: UnifiedData): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| unifiedData | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | dragData. |

## setDataLoadParams

```TypeScript
setDataLoadParams(dataLoadParams: DataLoadParams): void
```

Use this method to provide a data representation to the system instead of directly providing a complete data object. When the user releases the drag over the target application, the system will use this data representation to request the actual data from drag source. This approach significantly improves the efficiency of initiating drag operations for large volumes of data and enhances the effectiveness of data reception. It is recommended to use this method instead of the setData method.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragEvent-setDataLoadParams(dataLoadParams: DataLoadParams): void--><!--Device-DragEvent-setDataLoadParams(dataLoadParams: DataLoadParams): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataLoadParams | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | The data backend representation. |

## setResult

```TypeScript
setResult(dragResult: DragResult): void
```

Set dragEvent result to DragEvent.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragEvent-setResult(dragResult: DragResult): void--><!--Device-DragEvent-setResult(dragResult: DragResult): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dragResult | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | the return of dragEvent. |

## startDataLoading

```TypeScript
startDataLoading(options: DataSyncOptions): string | undefined
```

Request the drag data to be synchronized to caller, can be notified with the synchronization progress. Only can be used in onDrop event processing.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragEvent-startDataLoading(options: DataSyncOptions): string | undefined--><!--Device-DragEvent-startDataLoading(options: DataSyncOptions): string | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | the data sync options. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | The data key returned by system, which can be used as the identify of the request. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. |
| [190003](../../../apis-arkui/errorcode-drag-event.md#190003-当前阶段不允许操作) | Operation not allowed for current phase. |

## autoHideComponentUniqueIds

```TypeScript
autoHideComponentUniqueIds?: int | int[]
```

Set the uniqueId or uniqueId array of components that need to be automatically hidden during dragging. This property takes effect only in onDragStart. After the drag starts successfully, the system hides the target components before the drag preview window is shown. Developers need to restore component visibility in onDragEnd or onDrop based on service requirements.

**类型：** int \| int[]

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragEvent-autoHideComponentUniqueIds?: int | int[]--><!--Device-DragEvent-autoHideComponentUniqueIds?: int | int[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## dragBehavior

```TypeScript
dragBehavior: DragBehavior
```

If copy is COPY, this DragEvent is a copy event.

**类型：** DragBehavior

**默认值：** COPY

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragEvent-dragBehavior: DragBehavior--><!--Device-DragEvent-dragBehavior: DragBehavior-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getModifierKeyState

```TypeScript
getModifierKeyState?: ModifierKeyStateGetter
```

Query the modifier key press state, support 'ctrl'|'alt'|'shift'

**类型：** ModifierKeyStateGetter

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragEvent-getModifierKeyState?: ModifierKeyStateGetter--><!--Device-DragEvent-getModifierKeyState?: ModifierKeyStateGetter-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## useCustomDropAnimation

```TypeScript
useCustomDropAnimation: boolean
```

If useCustomDropAnimation is true, System will not use drop animation.

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragEvent-useCustomDropAnimation: boolean--><!--Device-DragEvent-useCustomDropAnimation: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

