# DivElement

The &lt;div&gt; component provides a div container.

@extends Element @interface DivElement

**Inheritance/Implementation:** DivElement extends [Element](arkts-arkui-viewmodel-element-i.md)

**Since:** 6

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getScrollOffset

```TypeScript
getScrollOffset(): ScrollOffset
```

Returns the offset of the current scrolling. The return value type is Object.

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [ScrollOffset](arkts-arkui-viewmodel-scrolloffset-i.md) |  |

## scrollBy

```TypeScript
scrollBy(data: ScrollParam): void
```

Scrolls the div for a certain distance.

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [ScrollParam](arkts-arkui-viewmodel-scrollparam-i.md) | Yes |  |
