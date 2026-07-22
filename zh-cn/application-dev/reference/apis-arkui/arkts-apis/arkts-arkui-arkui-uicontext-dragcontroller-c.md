# DragController

提供发起主动拖拽的能力，当应用接收到触摸或长按等事件时可以主动发起拖拽的动作，并在其中携带拖拽信息。
> **说明：**  
>  
> 以下API需先使用UIContext中的[getDragController()](arkts-arkui-arkui-uicontext-uicontext-c.md#getdragcontroller)方法获取DragController实例，再通过此实例调用对应方法。

**起始版本：** 11

<!--Device-unnamed-export class DragController--><!--Device-unnamed-export class DragController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { OverlayManager, FrameCallback, ResolvedUIContext, NodeRenderStateChangeCallback, MediaQuery, OverlayManagerOptions, TextMenuController, UIObserver, Font, KeyboardAvoidMode, MarqueeDynamicSyncScene, PromptAction, NodeRenderState, UIContext, TextSelectionClearPolicy, SwiperDynamicSyncScene, Router, MarqueeDynamicSyncSceneType, DialogPresenter, Magnifier, ContextMenuController, UIInspector, CursorController, SwiperDynamicSyncSceneType, AtomicServiceBar, PageInfo, TargetInfo, ComponentUtils, DragController, MeasureUtils, NodeIdentity } from '@kit.ArkUI';
```

## cancelDataLoading

```TypeScript
cancelDataLoading(key: string): void
```

当使用[startDataLoading](../arkts-components/arkts-arkui-dragevent-i.md#startdataloading)获取拖拽数据时，可调用该接口取消数据传输。仅可在拖拽释放后调用。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-DragController-cancelDataLoading(key: string): void--><!--Device-DragController-cancelDataLoading(key: string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 拖拽数据的标识，用于区分每次拖拽。key可通过startDataLoading接口获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. |
| [190004](../errorcode-drag-event.md#190004-操作失败) | Operation failed. |

## createDragAction

```TypeScript
createDragAction(customArray: Array<CustomBuilder | DragItemInfo>, dragInfo: dragController.DragInfo): dragController.DragAction
```

创建拖拽的Action对象，需要显式指定拖拽背板图（可多个），以及拖拽的数据，跟手点等信息；当通过一个已创建的Action对象发起的拖拽未结束时，无法再次创建新的Action对象，接口会抛出异常；当Action对象的生命周期结束后，注册在该对象上的回调函数会失效，因此需要在一个尽量长的作用域下持有该对象，并在每次发起拖拽前通过createDragAction返回新的对象覆盖旧值。
> **说明：**  
>  
> 建议控制传递的拖拽背板数量，传递过多容易导致拖起的效率问题。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DragController-createDragAction(customArray: Array<CustomBuilder | DragItemInfo>, dragInfo: dragController.DragInfo): dragController.DragAction--><!--Device-DragController-createDragAction(customArray: Array<CustomBuilder | DragItemInfo>, dragInfo: dragController.DragInfo): dragController.DragAction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| customArray | Array&lt;CustomBuilder \| DragItemInfo&gt; | 是 | 拖拽发起后跟手效果所拖拽的对象。 |
| dragInfo | dragController.DragInfo | 是 | 拖拽信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| dragController.DragAction | **DragAction** object, which is used to subscribe to drag state changes and start the drag service. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal handling failed. |

## enableDropDisallowedBadge

```TypeScript
enableDropDisallowedBadge(enabled: boolean): void
```

当组件的类型与配置的[allowDrop](../arkts-components/arkts-arkui-commonmethod-c.md#allowdrop)无交集时可显示禁用角标。通常，当组件可以接收或处理拖拽数据，或当它返回DragBehavior.COPY向系统声明数据以复制方式处理时，拖拽对象会显示加号及数据编号的角标。如果返回DragBehavior.MOVE以向系统声明数据以剪切方式处理，拖拽对象将只显示数据编号的角标。当目标进行拖拽时，若系统决定或组件显式声明无法处理拖拽数据，可通过该方法检查是否应显示拖拽禁止角标。该接口暂不支持[UIExtension](arkts-arkui-uiextension.md)。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-DragController-enableDropDisallowedBadge(enabled: boolean): void--><!--Device-DragController-enableDropDisallowedBadge(enabled: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 当组件的类型与配置的[allowDrop](../arkts-components/arkts-arkui-commonmethod-c.md#allowdrop)无交集时可显示禁用角标，当目标进行拖拽时，通过enableDropDisallowedBadge方法检查是否显示拖拽禁止角标。true表示显示拖拽禁止角标，false表示不显示拖拽禁止角标。默认值为false。 |

## executeDrag

```TypeScript
executeDrag(custom: CustomBuilder | DragItemInfo, dragInfo: dragController.DragInfo,
    callback: AsyncCallback<dragController.DragEventParam>): void
```

主动发起拖拽能力，传入拖拽发起后跟手效果所拖拽的对象以及携带拖拽信息。通过回调返回拖拽事件结果。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DragController-executeDrag(custom: CustomBuilder | DragItemInfo, dragInfo: dragController.DragInfo,    callback: AsyncCallback<dragController.DragEventParam>): void--><!--Device-DragController-executeDrag(custom: CustomBuilder | DragItemInfo, dragInfo: dragController.DragInfo,    callback: AsyncCallback<dragController.DragEventParam>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| custom | [CustomBuilder](../arkts-components/arkts-arkui-custombuilder-t.md) \| DragItemInfo | 是 | 拖拽发起后跟手效果所拖拽的对象。 <br/> **说明：** <br/>不支持全局builder。如果builder中使用了[Image](../../apis-image-kit/arkts-apis/arkts-multimedia-image.md)组件，应尽量开启同步加载，即配置Image的[syncLoad](ImageAttribute#syncLoad)为true。该builder只用于生成当次拖拽中显示的图片。builder的根组件宽高为0时，无法生成拖拽显示的图片导致拖拽失败。builder的修改不会同步到当前正在拖拽的图片，对builder的修改需要在下一次拖拽时生效。 |
| dragInfo | dragController.DragInfo | 是 | 拖拽信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;dragController.DragEventParam&gt; | 是 | 拖拽结束返回结果的回调<br/>- event：拖拽事件信息，仅包括拖拽结果。<br/>-extraParams：拖拽事件额外信息。<br>**起始版本：** 12 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal handling failed. |

## executeDrag

```TypeScript
executeDrag(custom: CustomBuilder | DragItemInfo, dragInfo: dragController.DragInfo)
    : Promise<dragController.DragEventParam>
```

主动发起拖拽能力，传入拖拽发起后跟手效果所拖拽的对象以及携带拖拽信息。通过Promise返回拖拽事件结果。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DragController-executeDrag(custom: CustomBuilder | DragItemInfo, dragInfo: dragController.DragInfo)    : Promise<dragController.DragEventParam>--><!--Device-DragController-executeDrag(custom: CustomBuilder | DragItemInfo, dragInfo: dragController.DragInfo)    : Promise<dragController.DragEventParam>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| custom | [CustomBuilder](../arkts-components/arkts-arkui-custombuilder-t.md) \| DragItemInfo | 是 | 拖拽发起后跟手效果所拖拽的对象。 |
| dragInfo | dragController.DragInfo | 是 | 拖拽信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;dragController.DragEventParam&gt; | A Promise with the drag event information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal handling failed. |

## getDragPreview

```TypeScript
getDragPreview(): dragController.DragPreview
```

返回一个代表拖拽背板的对象。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DragController-getDragPreview(): dragController.DragPreview--><!--Device-DragController-getDragPreview(): dragController.DragPreview-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| dragController.DragPreview | **DragPreview** object. It provides the API for setting the preview style.It does not work in the **OnDrop** and **OnDragEnd** callbacks. |

## notifyDragStartRequest

```TypeScript
notifyDragStartRequest(requestStatus: dragController.DragStartRequestStatus): void
```

控制应用是否可以发起拖拽。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-DragController-notifyDragStartRequest(requestStatus: dragController.DragStartRequestStatus): void--><!--Device-DragController-notifyDragStartRequest(requestStatus: dragController.DragStartRequestStatus): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| requestStatus | dragController.DragStartRequestStatus | 是 | 定义应用是否可以发起拖拽。 |

## setDragEventStrictReportingEnabled

```TypeScript
setDragEventStrictReportingEnabled(enable: boolean): void
```

当目标从父组件拖拽到子组件时，通过该方法设置是否会触发父组件的onDragLeave的回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DragController-setDragEventStrictReportingEnabled(enable: boolean): void--><!--Device-DragController-setDragEventStrictReportingEnabled(enable: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 将目标从父组件拖拽到子组件时，是否会触发父组件的onDragLeave的回调。true表示触发父组件的onDragLeave的回调，false表示不触发。 |

