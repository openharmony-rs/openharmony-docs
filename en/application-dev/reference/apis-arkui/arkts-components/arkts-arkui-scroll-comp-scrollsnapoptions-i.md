# ScrollSnapOptions

```TypeScript
declare interface ScrollSnapOptions
```

Defines a scroll snapping mode object.

**Since:** 10

<!--Device-unnamed-declare interface ScrollSnapOptions--><!--Device-unnamed-declare interface ScrollSnapOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableSnapToEnd

```TypeScript
enableSnapToEnd?: boolean
```

Whether to enable the snap to end feature. When scroll snapping is defined for the <em>Scroll</em> component, setting this parameter to <em>false</em> enables the component to scroll between the end and the last page.

<p><strong>NOTE</strong> <br>1. Default value: <em>true</em> <br>2. This attribute takes effect only when <em>snapPagination</em> is set to a value of the <em>Array\<Dimension\></em> type; it does not work with values of the <em>Dimension</em> type. </p>

**Type:** boolean

**Default:** true

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScrollSnapOptions-enableSnapToEnd?: boolean--><!--Device-ScrollSnapOptions-enableSnapToEnd?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableSnapToStart

```TypeScript
enableSnapToStart?: boolean
```

Whether to enable the snap to start feature. When scroll snapping is defined for the <em>Scroll</em> component, setting this parameter to <em>false</em> enables the component to scroll between the start and the first page.

<p><strong>NOTE</strong> <br>1. Default value: <em>true</em> <br>2. This attribute takes effect only when <em>snapPagination</em> is set to a value of the <em>Array\<Dimension\></em> type; it does not work with values of the <em>Dimension</em> type. </p>

**Type:** boolean

**Default:** true

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScrollSnapOptions-enableSnapToStart?: boolean--><!--Device-ScrollSnapOptions-enableSnapToStart?: boolean-End-->

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

<!--Device-ScrollSnapOptions-snapAlign: ScrollSnapAlign--><!--Device-ScrollSnapOptions-snapAlign: ScrollSnapAlign-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## snapPagination

```TypeScript
snapPagination?: Dimension | Array<Dimension>
```

Pagination points for scroll snapping.

<p><strong>NOTE</strong> <br>1. If the value is of the Dimension type, it indicates the size of each page, and the system will paginate based on this size. <br>2. If the value is of the Array\<Dimension\> type, each <em>Dimension</em> represents a pagination point, and the system will paginate accordingly. Each <em>Dimension</em> value must be within the [0, scrollable distance] range. <br>3. If this parameter is not set or <em>Dimension</em> is set to a value less than or equal to 0, the value is regarded as an invalid value. In this case, there is no scroll snapping. When the value is of the Array\<Dimension\> type, the items in the array must be monotonically increasing. <br>4. When the value is a percentage, the actual size is the product of the viewport of the <em>Scroll</em> component and the percentage value. </p>

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) &#124; Array&lt;[Dimension](../arkts-apis/arkts-arkui-dimension-t.md)&gt;

**Default:** 100%

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScrollSnapOptions-snapPagination?: Dimension | Array<Dimension>--><!--Device-ScrollSnapOptions-snapPagination?: Dimension | Array<Dimension>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
