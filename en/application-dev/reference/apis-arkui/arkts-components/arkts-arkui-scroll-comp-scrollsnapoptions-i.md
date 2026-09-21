# ScrollSnapOptions

```TypeScript
declare interface ScrollSnapOptions
```

Defines a scroll snapping mode object.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableSnapToEnd

```TypeScript
enableSnapToEnd?: boolean
```

Whether to enable the snap to end feature. When scroll snapping is defined for the &lt;em&gt;Scroll&lt;/em&gt; component, setting this parameter to &lt;em&gt;false&lt;/em&gt; enables the component to scroll between the end and the last page.

<p>&lt;strong&gt;NOTE&lt;/strong&gt; <br>1. Default value: &lt;em&gt;true&lt;/em&gt; <br>2. This attribute takes effect only when &lt;em&gt;snapPagination&lt;/em&gt; is set to a value of the &lt;em&gt;Array\&lt;Dimension\&gt;&lt;/em&gt; type; it does not work with values of the &lt;em&gt;Dimension&lt;/em&gt; type. </p>

**Type:** boolean

**Default:** true

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableSnapToStart

```TypeScript
enableSnapToStart?: boolean
```

Whether to enable the snap to start feature. When scroll snapping is defined for the &lt;em&gt;Scroll&lt;/em&gt; component, setting this parameter to &lt;em&gt;false&lt;/em&gt; enables the component to scroll between the start and the first page.

<p>&lt;strong&gt;NOTE&lt;/strong&gt; <br>1. Default value: &lt;em&gt;true&lt;/em&gt; <br>2. This attribute takes effect only when &lt;em&gt;snapPagination&lt;/em&gt; is set to a value of the &lt;em&gt;Array\&lt;Dimension\&gt;&lt;/em&gt; type; it does not work with values of the &lt;em&gt;Dimension&lt;/em&gt; type. </p>

**Type:** boolean

**Default:** true

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## snapAlign

```TypeScript
snapAlign: ScrollSnapAlign
```

Alignment mode for the scroll snap position.

**Type:** [ScrollSnapAlign](arkts-arkui-list-comp-scrollsnapalign-e.md)

**Default:** 
- API version 11+: ScrollSnapAlign.NONE

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## snapPagination

```TypeScript
snapPagination?: Dimension | Array<Dimension>
```

Pagination points for scroll snapping.

<p>&lt;strong&gt;NOTE&lt;/strong&gt; <br>1. If the value is of the Dimension type, it indicates the size of each page, and the system will paginate based on this size. <br>2. If the value is of the Array\&lt;Dimension\&gt; type, each &lt;em&gt;Dimension&lt;/em&gt; represents a pagination point, and the system will paginate accordingly. Each &lt;em&gt;Dimension&lt;/em&gt; value must be within the [0, scrollable distance] range. <br>3. If this parameter is not set or &lt;em&gt;Dimension&lt;/em&gt; is set to a value less than or equal to 0, the value is regarded as an invalid value. In this case, there is no scroll snapping. When the value is of the Array\&lt;Dimension\&gt; type, the items in the array must be monotonically increasing. <br>4. When the value is a percentage, the actual size is the product of the viewport of the &lt;em&gt;Scroll&lt;/em&gt; component and the percentage value. </p>

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) &#124; Array&lt;[Dimension](../arkts-apis/arkts-arkui-dimension-t.md)&gt;

**Default:** 100%

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
