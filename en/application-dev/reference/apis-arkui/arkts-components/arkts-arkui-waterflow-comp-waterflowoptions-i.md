# WaterFlowOptions

```TypeScript
declare interface WaterFlowOptions
```

Provides parameters of the **WaterFlow** component.

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## footer

```TypeScript
footer?: CustomBuilder
```

Footer component of the **WaterFlow** component, which is used to display custom content (such as loading prompts and bottom icons) at the end of the waterfall. If this parameter is not set, no footer component is displayed.

**Type:** [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md)

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## footerContent

```TypeScript
footerContent?: ComponentContent
```

Footer of the **WaterFlow** component. This parameter has a higher priority than **footer**. If both **footer** and **footerContent** are set, the component set by **footerContent** will be used.

**Type:** ComponentContent

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## layoutMode

```TypeScript
layoutMode?: WaterFlowLayoutMode
```

Layout mode of the &lt;em&gt;WaterFlow&lt;/em&gt; component.

**Type:** [WaterFlowLayoutMode](arkts-arkui-waterflow-comp-waterflowlayoutmode-e.md)

**Default:** ALWAYS_TOP_DOWN

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scroller

```TypeScript
scroller?: Scroller
```

Controller of the scrollable component, bound to the scrollable component.

<p>&lt;strong&gt;NOTE&lt;/strong&gt; <br>The scroller cannot be bound to other scrollable components, such as ArcList, List, Grid, Scroll, or WaterFlow. </p>

**Type:** [Scroller](arkts-arkui-scroll-comp-scroller-c.md)

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## sections

```TypeScript
sections?: WaterFlowSections
```

Water flow item sections, used to implement mixed layouts with different column counts for each section within the same **WaterFlow** component. This is applicable to scenarios where different numbers of columns are required in different areas. If this parameter is not set, the layout with the same number of columns is used.

<p>&lt;strong&gt;NOTE&lt;/strong&gt; <br>1. When &lt;em&gt;sections&lt;/em&gt; is used, the &lt;em&gt;columnsTemplate&lt;/em&gt; and &lt;em&gt;rowsTemplate&lt;/em&gt; attributes are ignored. <br>2. When &lt;em&gt;sections&lt;/em&gt; is used, the footer cannot be set separately. The last section can function as the footer. </p>

**Type:** [WaterFlowSections](arkts-arkui-waterflow-comp-waterflowsections-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
