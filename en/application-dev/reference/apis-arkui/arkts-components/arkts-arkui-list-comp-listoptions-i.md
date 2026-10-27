# ListOptions

```TypeScript
interface ListOptions
```

Defines the options of the **List** component.

> **NOTE:** 
> 
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18.
> While historical version information is preserved for anonymous objects, there may be cases where the outer element
> 's

**Since:** 18

<!--Device-unnamed-interface ListOptions--><!--Device-unnamed-interface ListOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## initialIndex

```TypeScript
initialIndex?: number
```

Index of the item at the start position of the display area when the **List** is initially loaded. Anonymous Object Rectification.

<p><strong>NOTE</strong> <br>A negative value or a value greater than the index of the last item in the current **List** is invalid, and the default value is used in this case. <br>Since API version 14, if the **scrollToIndex** or **scrollEdge** method without animation in the Scroller is called before the first layout after the **List** component is created (for example, in the [onAttach](ts-universal-events-show-hide.md#onattach12) event of the List), the value set by **initialIndex** is overwritten. <br>After **initialIndex** is set, the **List** starts layout from the child component corresponding to **initialIndex**. The child components before it do not participate in the layout and their exact sizes cannot be calculated. Therefore, the total scroll offset of the **List** obtained through [currentOffset](ts-container-scroll.md#currentoffset) is estimated and may be inaccurate. You can set [childrenMainSize](#childrenmainsize12) to ensure the accuracy of the total scroll offset of the **List**. </p> <p>When **stackFromEnd** is set to **true**, the default value is the total number of items minus 1.</p>

**Type:** number

**Default:** 
- API version 18+: 0

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ListOptions-initialIndex?: number--><!--Device-ListOptions-initialIndex?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scroller

```TypeScript
scroller?: Scroller
```

Scroller, which can be bound to scrollable components. Anonymous Object Rectification.

<p><strong>NOTE</strong> <br>The scroller cannot be bound to other scrollable components. </p>

**Type:** [Scroller](arkts-arkui-scroll-comp-scroller-c.md)

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ListOptions-scroller?: Scroller--><!--Device-ListOptions-scroller?: Scroller-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
space?: number | string
```

Spacing between child components along the main axis. Default value: **0**. <br>If the parameter type is number, the unit is vp. Anonymous Object Rectification. <p><strong>NOTE</strong> <br>A negative value or a value greater than or equal to the length of the **List** content area is invalid, and the default value is used in this case. <br>When the value of **space** is less than the width of the **List** divider, the spacing between child components along the main axis is the divider width. <br>When the **visibility** attribute of a **List** child component is set to **None**, the child component is not displayed, but the **space** above and below it still takes effect. <br>If both **spaceWidth** and **space** are set, **spaceWidth** takes effect first. When **spaceWidth** is **undefined** or **null**, **space** takes effect. </p>

**Type:** number &#124; string

**Default:** 
- API version 18+: 0

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ListOptions-space?: number | string--><!--Device-ListOptions-space?: number | string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## spaceWidth

```TypeScript
spaceWidth?: Dimension
```

Spacing between list items along the main axis.

<p><strong>NOTE</strong> <br>If this parameter is set to a negative number or a value greater than or equal to the length of the list content area, the default value is used. <br>If this parameter is set to a value less than the width of the list divider, the width of the list divider is used as the spacing. <br> Child components of <em>ListItemGroup</em> whose <em>visibility</em> attribute is set to <em>None</em> are not displayed, but the spacing above and below them still takes effect. <br> If both spaceWidth and space are set, spaceWidth will take precedence. </p>

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Default:** 0

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

<!--Device-ListOptions-spaceWidth?: Dimension--><!--Device-ListOptions-spaceWidth?: Dimension-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
