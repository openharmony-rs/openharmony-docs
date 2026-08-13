# DragController

class DragController

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class DragController--><!--Device-unnamed-export declare class DragController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## cancelDataLoading

```TypeScript
cancelDataLoading(key: string): void
```

Cancel the UDMF data sync process by passing in the data key as the identify, can only be used after the drop.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragController-cancelDataLoading(key: string): void--><!--Device-DragController-cancelDataLoading(key: string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | The data key returned by startDataLoading method. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [190004](../../apis-arkui/errorcode-drag-event.md#190004-操作失败) | Operation failed. |

## createDragAction

```TypeScript
createDragAction(customArray: Array<CustomBuilder | DragItemInfo> | undefined, dragInfo: dragController.DragInfo): dragController.DragAction
```

Create one drag action object, which can be used for starting drag later or monitoring the drag status after drag started.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragController-createDragAction(customArray: Array<CustomBuilder | DragItemInfo> | undefined, dragInfo: dragController.DragInfo): dragController.DragAction--><!--Device-DragController-createDragAction(customArray: Array<CustomBuilder | DragItemInfo> | undefined, dragInfo: dragController.DragInfo): dragController.DragAction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| customArray | Array&lt;CustomBuilder \| [DragItemInfo](arkts-na-common-dragiteminfo-i.md)&gt; \| undefined | 是 | Objects used for prompts displayed when the objects are dragged. |
| dragInfo | dragController.DragInfo | 是 | Information about the drag event. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| dragController.DragAction | one drag action object |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100001](../../apis-arkui/errorcode-internal.md#100001-接口调用异常错误码) | Internal handling failed. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |

## enableDropDisallowedBadge

```TypeScript
enableDropDisallowedBadge(enabled: boolean): void
```

Sets whether to enable the disallow badge icon show. Typically, when a component can receive or process data dragged by the user, or when it declares to the system that data should be processed in COPY way by returning DragBehavior.COPY, the system will display a plus sign together with the data number on the upper-left corner of the dragged object; if returning DragBehavior.MOVE to the system to declare that data should be processed in CUT way, the system will only display the data number on the upper-left corner of the dragged object. In some cases, when the system determines or the component explicitly declares that it cannot handle the data that the user is dragging, the system displays a badge icon in the same way as it does for DragBehavior.MOVE. So if you want to show the more clearly status, you can call this method on the UI instance in advance to force the system to display a clear prohibition icon on the upper left corner in such cases, and the user can clearly know that data cannot be dropped here.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragController-enableDropDisallowedBadge(enabled: boolean): void--><!--Device-DragController-enableDropDisallowedBadge(enabled: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | Indicating enable the disallow status showing or not. |

## executeDrag

```TypeScript
executeDrag(custom: CustomBuilder | DragItemInfo | undefined, dragInfo: dragController.DragInfo,
    callback: AsyncCallback<dragController.DragEventParam>): void
```

Execute a drag event.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragController-executeDrag(custom: CustomBuilder | DragItemInfo | undefined, dragInfo: dragController.DragInfo,    callback: AsyncCallback<dragController.DragEventParam>): void--><!--Device-DragController-executeDrag(custom: CustomBuilder | DragItemInfo | undefined, dragInfo: dragController.DragInfo,    callback: AsyncCallback<dragController.DragEventParam>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| custom | CustomBuilder \| [DragItemInfo](arkts-na-common-dragiteminfo-i.md) \| undefined | 是 | Object used for prompts displayed when the object is dragged. |
| dragInfo | dragController.DragInfo | 是 | Information about the drag event. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;dragController.DragEventParam&gt; | 是 | Callback that contains the drag event information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100001](../../apis-arkui/errorcode-internal.md#100001-接口调用异常错误码) | Internal handling failed. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |

## executeDrag

```TypeScript
executeDrag(custom: CustomBuilder | DragItemInfo | undefined, dragInfo: dragController.DragInfo)
    : Promise<dragController.DragEventParam> | null
```

Execute a drag event.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragController-executeDrag(custom: CustomBuilder | DragItemInfo | undefined, dragInfo: dragController.DragInfo)    : Promise<dragController.DragEventParam> | null--><!--Device-DragController-executeDrag(custom: CustomBuilder | DragItemInfo | undefined, dragInfo: dragController.DragInfo)    : Promise<dragController.DragEventParam> | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| custom | CustomBuilder \| [DragItemInfo](arkts-na-common-dragiteminfo-i.md) \| undefined | 是 | Object used for prompts displayed when the object is dragged. |
| dragInfo | dragController.DragInfo | 是 | Information about the drag event. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;dragController.DragEventParam&gt; | A Promise with the drag event information. Null will be returned if the parameters' checking failed or some internal errors occur, for example: the runtime environment is broken. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100001](../../apis-arkui/errorcode-internal.md#100001-接口调用异常错误码) | Internal handling failed. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |

## getDragPreview

```TypeScript
getDragPreview(): dragController.DragPreview
```

获取拖拽预览对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragController-getDragPreview(): dragController.DragPreview--><!--Device-DragController-getDragPreview(): dragController.DragPreview-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| dragController.DragPreview | A drag preview object. |

## notifyDragStartRequest

```TypeScript
notifyDragStartRequest(requestStatus: dragController.DragStartRequestStatus): void
```

Notify the drag start request to specific pending or continue.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragController-notifyDragStartRequest(requestStatus: dragController.DragStartRequestStatus): void--><!--Device-DragController-notifyDragStartRequest(requestStatus: dragController.DragStartRequestStatus): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| requestStatus | dragController.DragStartRequestStatus | 是 | Status about the drag start behavior. |

## setDragEventStrictReportingEnabled

```TypeScript
setDragEventStrictReportingEnabled(enable: boolean): void
```

Enable drag event strict reporting for drag enter and leave notification in nested situation. For example, the parent and child both register the onDragEnter/onDragLeave events, if this flag is enabled, the parent will be notified with leave event, and the child will notified with enter event at the same time, when user drag action is passing through the parent and enter the scope of the child. Please be noted, the default value of the flag is false, it means, for the same situation, the parent will not receive the leave notification, just the child can get the enter event, which is not fully strict.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragController-setDragEventStrictReportingEnabled(enable: boolean): void--><!--Device-DragController-setDragEventStrictReportingEnabled(enable: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | Indicating enable drag event strict reporting or not. |

