# ScrollOnScrollCallback

```TypeScript
declare type ScrollOnScrollCallback = (xOffset: number, yOffset: number, scrollState: ScrollState) => void
```

Represents the callback triggered when the &lt;em&gt;Scroll&lt;/em&gt; component scrolls.

<p>&lt;strong&gt;NOTE&lt;/strong&gt; <br>If the &lt;em&gt;onScrollFrameBegin&lt;/em&gt; event and &lt;em&gt;scrollBy&lt;/em&gt; method are used to implement nested scrolling, set the &lt;em&gt;edgeEffect&lt;/em&gt; attribute of the scrollable child component to &lt;em&gt;None&lt;/em&gt;. For example, if a &lt;em&gt;List&lt;/em&gt; is nested in the &lt;em&gt;Scroll&lt;/em&gt; component, &lt;em&gt;edgeEffect&lt;/em&gt; of the &lt;em&gt;List&lt;/em&gt; must be set to &lt;em&gt;EdgeEffect.None&lt;/em&gt;. </p>

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| xOffset | number | Yes | Horizontal offset per frame during scrolling. A positive offset indicates scrolling to the left, and a negative offset indicates scrolling to the right.<br>Unit: vp |
| yOffset | number | Yes | Vertical offset per frame during scrolling. A positive offset indicates scrolling upward, and a negative offset indicates scrolling downward.<br>Unit: vp |
| scrollState | [ScrollState](arkts-arkui-scrollstate-e.md) | Yes | Current scrolling state. |
