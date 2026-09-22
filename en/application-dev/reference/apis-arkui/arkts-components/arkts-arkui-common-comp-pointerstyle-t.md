# PointerStyle

```TypeScript
declare type PointerStyle = import('../api/@ohos.multimodalInput.pointer').default.PointerStyle
```

Defines the pointer style.

> **NOTE:** 
> 
> Directly using **cursorControl** can lead to the issue of
> [ambiguous UI context](../../../ui/arkts-global-interface.md#ambiguous-ui-context). To avoid this, obtain the
> [UIContext](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md) object using the **getUIContext()** API and then obtain the
> **cursorControl** bound to the instance using the
> getCursorController API.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Type:** import('../api/@ohos.multimodalInput.pointer').default.PointerStyle
