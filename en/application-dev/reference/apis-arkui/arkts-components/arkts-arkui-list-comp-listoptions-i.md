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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## initialIndex

```TypeScript
initialIndex?: number
```

Index of the item to be displayed at the start when the list is initially loaded. Anonymous Object Rectification.

<p>&lt;strong&gt;NOTE&lt;/strong&gt; <br>If the set value is a negative number or is greater than the index of the last item in the list, the value is invalid. In this case, the default value will be used. </p>

**Type:** number

**Default:** 
- API version 18+: 0

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scroller

```TypeScript
scroller?: Scroller
```

Scroller, which can be bound to scrollable components. Anonymous Object Rectification.

<p>&lt;strong&gt;NOTE&lt;/strong&gt; <br>The scroller cannot be bound to other scrollable components. </p>

**Type:** [Scroller](arkts-arkui-scroll-comp-scroller-c.md)

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
space?: number | string
```

Spacing between list items along the main axis. <br>Default value: **0** <br>If the parameter type is number, the unit is vp. Anonymous Object Rectification.

<p>&lt;strong&gt;NOTE&lt;/strong&gt; <br>If this parameter is set to a negative number or a value greater than or equal to the length of the list content area, the default value is used. <br>If this parameter is set to a value less than the width of the list divider, the width of the list divider is used as the spacing. <br> Child components of &lt;em&gt;List&lt;/em&gt; whose &lt;em&gt;visibility&lt;/em&gt; attribute is set to &lt;em&gt;None&lt;/em&gt; are not displayed, but the spacing above and below them still takes effect. </p>

**Type:** number &#124; string

**Default:** 
- API version 18+: 0

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## spaceWidth

```TypeScript
spaceWidth?: Dimension
```

Spacing between list items along the main axis.

<p>&lt;strong&gt;NOTE&lt;/strong&gt; <br>If this parameter is set to a negative number or a value greater than or equal to the length of the list content area, the default value is used. <br>If this parameter is set to a value less than the width of the list divider, the width of the list divider is used as the spacing. <br> Child components of &lt;em&gt;ListItemGroup&lt;/em&gt; whose &lt;em&gt;visibility&lt;/em&gt; attribute is set to &lt;em&gt;None&lt;/em&gt; are not displayed, but the spacing above and below them still takes effect. <br> If both spaceWidth and space are set, spaceWidth will take precedence. </p>

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Default:** 0

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
