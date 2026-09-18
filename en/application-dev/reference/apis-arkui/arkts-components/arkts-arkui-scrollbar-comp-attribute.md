# ScrollBar properties/events

In addition to the universal attributes, the following attributes are supported.

**Inheritance/Implementation:** ScrollBarAttribute extends CommonMethod<ScrollBarAttribute>

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableNestedScroll

```TypeScript
enableNestedScroll(enabled: Optional<boolean>)
```

Sets whether nested scrolling is enabled.

> **NOTE:** 
> 
> When nested scrolling is enabled, the scroll offset is first passed to the inner scrollable component, which
> then passes it to the outer parent scrollable component based on the set nested scrolling priority.
> 
> Nested scrolling is not supported when the **WaterFlow** component is in
> [WaterFlowLayoutMode.SLIDING_WINDOW](../../../reference/apis-arkui/arkui-ts/ts-container-waterflow.md#waterflowlayoutmode12)
> layout mode.
> 
> When the nested scrolling mode is set to
> [PARALLEL](../../../reference/apis-arkui/arkui-ts/ts-appendix-enums.md#nestedscrollmode10), both the parent
> and child components scroll simultaneously. You need to manage the scroll order in the
> [onScrollFrameBegin](../../../reference/apis-arkui/arkui-ts/ts-container-scroll.md#onscrollframebegin9) event
> according to the desired logic.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | Yes | Whether nested scrolling is enabled. The value **true** means that nested scrolling is enabled, and **false** means the opposite.<br>Default value: **false** |

## scrollBarColor

```TypeScript
scrollBarColor(color: Optional<ColorMetrics>)
```

Sets the color of the scrollbar slider. This parameter is valid only when the scrollbar does not contain child components.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-optional-t.md)&lt;ColorMetrics&gt; | Yes | Scrollbar color.<br>Default value: **ColorMetrics.numeric(0x66182431)** |
