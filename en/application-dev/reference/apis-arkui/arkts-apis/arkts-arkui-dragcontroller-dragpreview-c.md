# DragPreview

Implements a **DragPreview** object. This API does not work in the **OnDrop** and **OnDragEnd** callbacks.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { dragController } from '@kit.ArkUI';
```

## animate

```TypeScript
animate(options: AnimationOptions, handler: () =>void): void
```

Applies a foreground color animation to the drag preview. This API does not work in the **OnDrop** and **OnDragEnd** callbacks. It can only be used on the object obtained through the [getDragPreview()](arkts-arkui-arkui-uicontext-dragcontroller-c.md#getdragpreview) API.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [AnimationOptions](arkts-arkui-dragcontroller-animationoptions-i.md) | Yes | Animation settings. |
| handler | () =&gt;void | Yes | Callback used to change attributes such as the background mask color. |

**Examples**

```TypeScript
> NOTE
> 
> You are advised to use [getDragController](arkts-arkui-arkui-uicontext-uicontext-c.md#getdragcontroller) in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the DragController object associated with the current UI context.

In the EntryAbility.ets file, obtain the UI context and save it to LocalStorage.
```

```TypeScript
In the Index.ets file, call this.getUIContext().getSharedLocalStorage() to obtain the UI context and then use the DragController object obtained to perform subsequent operations.
```

## setForegroundColor

```TypeScript
setForegroundColor(color: ResourceColor): void
```

Sets the foreground color of the drag preview. This API does not work in the **OnDrop** and **OnDragEnd** callbacks. It can only be used on the object obtained through the [getDragPreview()](arkts-arkui-arkui-uicontext-dragcontroller-c.md#getdragpreview) API.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [ResourceColor](arkts-arkui-resourcecolor-t.md) | Yes | Foreground color of the drag preview. |

**Examples**

```TypeScript
See [animate](#animate).
```
