# DragAction

```TypeScript
interface DragAction
```

Implements a **DragAction** object to subscribe to drag state changes and start the drag service.

**Since:** 11

<!--Device-dragController-interface DragAction--><!--Device-dragController-interface DragAction-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { dragController } from '@kit.ArkUI';
```

## off('statusChange')

```TypeScript
off(type: 'statusChange', callback?: Callback<DragAndDropInfo>): void
```

Unsubscribes from drag state changes. This API is suitable for scenarios where the listener needs to be released when the drag ends, the page is destroyed, or the drag status change no longer needs to be responded to.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DragAction-off(type: 'statusChange', callback?: Callback<DragAndDropInfo>): void--><!--Device-DragAction-off(type: 'statusChange', callback?: Callback<DragAndDropInfo>): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'statusChange' | Yes | Event type. The value is fixed at **'statusChange'**, which indicates the drag state change event. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DragAndDropInfo](arkts-arkui-dragcontroller-draganddropinfo-i.md)&gt; | No | Callback used to return the drag state in [DragAndDropInfo](arkts-arkui-dragcontroller-draganddropinfo-i.md). |

## on('statusChange')

```TypeScript
on(type: 'statusChange', callback: Callback<DragAndDropInfo>): void
```

Subscribes to drag state changes. This API is used to obtain the drag status when proactive drag starts or ends, and to perform operations such as updating the UI, recording the status, or cleaning up resources.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DragAction-on(type: 'statusChange', callback: Callback<DragAndDropInfo>): void--><!--Device-DragAction-on(type: 'statusChange', callback: Callback<DragAndDropInfo>): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'statusChange' | Yes | Event type. The value is fixed at **'statusChange'**, which indicates the drag state change event. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DragAndDropInfo](arkts-arkui-dragcontroller-draganddropinfo-i.md)&gt; | Yes | Callback used to return the drag state in [DragAndDropInfo](arkts-arkui-dragcontroller-draganddropinfo-i.md). |

## startDrag

```TypeScript
startDrag(): Promise<void>
```

Starts the drag service. This API is suitable for scenarios where a **DragAction** object is created through **createDragAction** to proactively initiate multi-object drag or customize the drag backdrop. This API uses a promise to return the result.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DragAction-startDrag(): Promise<void>--><!--Device-DragAction-startDrag(): Promise<void>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal handling failed. |
