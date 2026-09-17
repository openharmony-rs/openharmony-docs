# MenuElement

The &lt;menu&gt; component provides menus as temporary pop-up windows to display operations that can be performed by users.

@extends Element @interface MenuElement

**Inheritance/Implementation:** MenuElement extends [Element](arkts-arkui-viewmodel-element-i.md)

**Since:** 4

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## show

```TypeScript
show(position: { x: number; y: number }): void
```

Displays the menu. x and y specify the position of the displayed menu. x indicates the X-axis coordinate from the left edge of the visible area, and does not include any scrolling offset. y indicates the Y-axis coordinate from the upper edge of the visible area, and does not include any scrolling offset or a status bar. The menu is preferentially displayed in the lower right corner. When the visible space on the right is insufficient, the menu is moved leftward. When the visible space in the lower part is insufficient, the menu is moved upward.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| position | { x: number; y: number } | Yes |  |
