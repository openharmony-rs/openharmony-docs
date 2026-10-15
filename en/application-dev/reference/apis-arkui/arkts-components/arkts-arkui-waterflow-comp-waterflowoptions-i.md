# WaterFlowOptions

```TypeScript
declare interface WaterFlowOptions
```

Provides parameters of the **WaterFlow** component.

**Since:** 9

<!--Device-unnamed-declare interface WaterFlowOptions--><!--Device-unnamed-declare interface WaterFlowOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## footer

```TypeScript
footer?: CustomBuilder
```

Footer component of the **WaterFlow** component, which is used to display custom content (such as loading prompts and bottom icons) at the end of the waterfall. If this parameter is not set, no footer component is displayed. <br>**NOTE:** <br>1. For details about the usage, see [Example 1](#example-1-using-a-basic-waterflow-component). <br>2. When both **footer** and **footerContent** are set, the component set by **footerContent** takes precedence. <br>3. When group mixing layout is used, footer cannot be set separately. You can use the last group as the footer component.

**Type:** [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md)

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WaterFlowOptions-footer?: CustomBuilder--><!--Device-WaterFlowOptions-footer?: CustomBuilder-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## footerContent

```TypeScript
footerContent?: ComponentContent
```

Footer component content of **WaterFlow**. <br>This parameter has a higher priority than **footer**. That is, when both **footer** and **footerContent** are set, the component set by **footerContent** takes precedence. When **footerContent** is not set, footer can still be used to set the footer component. When group mixing layout is used, the footer component cannot be set separately. You can use the last group as the footer component.

**Type:** ComponentContent

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-WaterFlowOptions-footerContent?: ComponentContent--><!--Device-WaterFlowOptions-footerContent?: ComponentContent-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## layoutMode

```TypeScript
layoutMode?: WaterFlowLayoutMode
```

Layout mode of **WaterFlow**. Select a more suitable mode based on the usage scenario. **ALWAYS_TOP_DOWN** is suitable for scenarios with a fixed number of columns; **SLIDING_WINDOW** is suitable for scenarios such as dynamic number of columns, large data volume, and screen rotation. <br>**NOTE:** <br>Default value: [ALWAYS_TOP_DOWN](arkts-arkui-waterflow-comp-waterflowlayoutmode-e.md).

**Type:** [WaterFlowLayoutMode](arkts-arkui-waterflow-comp-waterflowlayoutmode-e.md)

**Default:** ALWAYS_TOP_DOWN

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-WaterFlowOptions-layoutMode?: WaterFlowLayoutMode--><!--Device-WaterFlowOptions-layoutMode?: WaterFlowLayoutMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scroller

```TypeScript
scroller?: Scroller
```

Controller of the scrollable component, bound to the scrollable component. When not set, no external controller is bound, and the component manages scrolling by itself. <br>**NOTE:** <br>1. It is not allowed to bind the same scroll controller to other scrollable components such as [ArcList](ts-container-arclist.md), [List](ts-container-list.md), [Grid](ts-container-grid.md), [Scroll](ts-container-scroll.md), and [WaterFlow](ts-container-waterflow.md). <br>2. When the [SLIDING_WINDOW](arkts-arkui-waterflow-comp-waterflowlayoutmode-e.md) layout mode is used, the total offset returned by [currentOffset](ts-container-scroll.md#currentoffset) or [offset](ts-container-scroll.md#offset23) of scroller is inaccurate after a jump or data update is triggered, and is recalibrated when scrolling back to the top.

**Type:** [Scroller](arkts-arkui-scroll-comp-scroller-c.md)

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WaterFlowOptions-scroller?: Scroller--><!--Device-WaterFlowOptions-scroller?: Scroller-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## sections

```TypeScript
sections?: WaterFlowSections
```

**FlowItem** groups to implement mixed layout with different numbers of columns for different groups within the same **WaterFlow** component. Suitable for scenarios where different numbers of columns are required in different areas. When not set, a unified number of columns is used for layout. <br>**NOTE:** <br>1. When group mixing layout is used, the [columnsTemplate](#columnstemplate) and [rowsTemplate](#rowstemplate) attributes are ignored. <br>2. When group mixing layout is used, **footer** cannot be set separately. You can use the last group as the footer component.

**Type:** [WaterFlowSections](arkts-arkui-waterflow-comp-waterflowsections-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-WaterFlowOptions-sections?: WaterFlowSections--><!--Device-WaterFlowOptions-sections?: WaterFlowSections-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
