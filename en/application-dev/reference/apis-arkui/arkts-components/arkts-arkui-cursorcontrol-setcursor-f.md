# setCursor

## setCursor

```TypeScript
function setCursor(value: PointerStyle): void
```

A global API that can be used in component methods or event callbacks. Calling this API sets the current mouse cursor style, for example, displaying an I-beam cursor when hovering over a text editing area, displaying a move cursor on a draggable element, or displaying a pointing-hand cursor when hovering over a map marker.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-cursorControl-function setCursor(value: PointerStyle): void--><!--Device-cursorControl-function setCursor(value: PointerStyle): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [PointerStyle](arkts-arkui-common-comp-pointerstyle-t.md) | Yes | Mouse cursor style to set. |
