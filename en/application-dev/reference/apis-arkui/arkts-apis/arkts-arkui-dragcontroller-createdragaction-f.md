# createDragAction

## Modules to Import

```TypeScript
import { dragController } from '@kit.ArkUI';
```

## createDragAction

```TypeScript
function createDragAction(customArray: Array<CustomBuilder | DragItemInfo>, dragInfo: DragInfo): DragAction
```

Initiates a drag action, with the object to be dragged and the drag information passed in. This API uses a promise to return the result.

> **NOTE:** 
> 
> - Since API version 11, you can use the [getDragController](arkts-arkui-arkui-uicontext-uicontext-c.md#getdragcontroller) API in [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) to obtain the [DragController](arkts-arkui-arkui-uicontext-dragcontroller-c.md) object associated with the current UI context.
> 
> - For optimal drag and drop performance, limit the number of drag previews.

**Since:** 11

**Deprecated since:** 18

**Substitutes:** createDragAction

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| customArray | Array&lt;[CustomBuilder](../arkts-components/arkts-arkui-custombuilder-t.md) &#124; [DragItemInfo](../arkts-components/arkts-arkui-dragiteminfo-i.md)&gt; | Yes | Object to be dragged. |
| dragInfo | [DragInfo](arkts-arkui-dragcontroller-draginfo-i.md) | Yes | Drag information. |

**Return value:**

| Type | Description |
| --- | --- |
| [DragAction](arkts-arkui-dragcontroller-dragaction-i.md) | **DragAction** object, which is used to subscribe to drag state changes and start the drag service. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal handling failed. |

**Examples**

```TypeScript
> NOTE
> 
> You are advised to use [getDragController](arkts-arkui-arkui-uicontext-uicontext-c.md#getdragcontroller) in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the DragController object associated with the current UI context.
```
