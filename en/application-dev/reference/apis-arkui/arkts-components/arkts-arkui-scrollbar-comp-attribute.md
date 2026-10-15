# ScrollBar properties/events

```TypeScript
declare class ScrollBarAttribute extends CommonMethod<ScrollBarAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp.md), the following attributes are supported.

**Inheritance/Implementation:** ScrollBarAttribute extends CommonMethod&lt;ScrollBarAttribute&gt;

**Since:** 8

<!--Device-unnamed-declare class ScrollBarAttribute extends CommonMethod<ScrollBarAttribute>--><!--Device-unnamed-declare class ScrollBarAttribute extends CommonMethod<ScrollBarAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableNestedScroll

```TypeScript
enableNestedScroll(enabled: Optional<boolean>)
```

Sets whether the scrollbar supports nested scrolling. It is used in scenarios such as multi-layer scroll containers and nested lists where the inner scrollable component needs to be dragged through the scrollbar and linked with the parent scrolling. It takes effect only when the ScrollBar is bound to a scrollable component through a Scroller.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-ScrollBarAttribute-enableNestedScroll(enabled: Optional<boolean>): ScrollBarAttribute--><!--Device-ScrollBarAttribute-enableNestedScroll(enabled: Optional<boolean>): ScrollBarAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to perform nested scrolling. Set this parameter to **true** to pass scroll events between multiple layers of scroll containers; set it to **false** when nested scrolling is not required.<br>Default value: **false** |

## scrollBarColor

```TypeScript
scrollBarColor(color: Optional<ColorMetrics>)
```

Sets the color of the scrollbar. This parameter takes effect only when the scrollbar does not contain child components.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-ScrollBarAttribute-scrollBarColor(color: Optional<ColorMetrics>): ScrollBarAttribute--><!--Device-ScrollBarAttribute-scrollBarColor(color: Optional<ColorMetrics>): ScrollBarAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;ColorMetrics&gt; | Yes | Color of the scrollbar. This parameter takes effect only when the scrollbar does not contain any child component.<br>Default value: ColorMetrics.numeric(0x66182431) |
