# getDragPreview

## Modules to Import

```TypeScript
import { dragController } from '@kit.ArkUI';
```

## getDragPreview

```TypeScript
function getDragPreview(): DragPreview
```

Obtains the **DragPreview** object, which represents the preview displayed during a drag operation.

> **NOTE:** 
> 
> Since API version 11, you can use the [getDragController](arkts-arkui-arkui-uicontext-uicontext-c.md#getdragcontroller) API in
> [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) to obtain the [DragController](arkts-arkui-arkui-uicontext-dragcontroller-c.md) object
> associated with the current UI context.

**Since:** 11

**Deprecated since:** 18

**Substitutes:** getDragPreview

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [DragPreview](arkts-arkui-dragcontroller-dragpreview-c.md) | **DragPreview** object. It provides the API for setting the preview style. It does not work in the **OnDrop** and **OnDragEnd** callbacks. |
