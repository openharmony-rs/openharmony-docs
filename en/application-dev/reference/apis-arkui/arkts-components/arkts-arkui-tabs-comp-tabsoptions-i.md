# TabsOptions

```TypeScript
declare interface TabsOptions
```

Provides parameters for configuring the **Tabs** component, including tab positions, the current index of the displayed tab, the **Tabs** controller, and [universal attributes](arkts-arkui-common-comp.md) for the **TabBar**.

**Since:** 15

<!--Device-unnamed-declare interface TabsOptions--><!--Device-unnamed-declare interface TabsOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## barModifier

```TypeScript
barModifier?: CommonModifier
```

Used to set the [universal attributes](arkts-arkui-common-comp.md) of tab bar, used to uniformly manage the style, layout, and other universal attributes of tab bar through **CommonModifier**. Pass this parameter when you need to dynamically modify the universal attributes of **TabBar** or implement state management of attributes. When it is not passed, tab bar uses the default style and layout without additional universal attribute settings.

**NOTE:** 

When dynamically set to undefined, the current state remains unchanged and the universal attributes are not reset.

When switching from one **CommonModifier** to another, duplicate attributes are overwritten, and non-duplicate attributes take effect at the same time without resetting the universal attributes of the previous **CommonModifier**.

The [barWidth](arkts-arkui-tabs-comp-attribute.md#barwidth), [barHeight](arkts-arkui-tabs-comp-attribute.md#barheight1), [barBackgroundColor](arkts-arkui-tabs-comp-attribute.md#barbackgroundcolor), [barBackgroundBlurStyle](arkts-arkui-tabs-comp-attribute.md#barbackgroundblurstyle2), and [barBackgroundEffect](arkts-arkui-tabs-comp-attribute.md#barbackgroundeffect) attributes of **Tabs** override the [width](arkts-arkui-common-comp-commonmethod-c.md#width1), [height](arkts-arkui-common-comp-commonmethod-c.md#height1), [backgroundColor](arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor2), [backgroundBlurStyle](arkts-arkui-common-comp-commonmethod-c.md#backgroundblurstyle2), and [backgroundEffect](arkts-arkui-common-comp-commonmethod-c.md#backgroundeffect2) attributes of CommonModifier.

The [align](arkts-arkui-common-comp-commonmethod-c.md#align1) attribute takes effect only in [BarMode.Scrollable](arkts-arkui-tabs-comp-attribute.md#barmode2) mode, and when **Tabs** is horizontal, it takes effect only when [nonScrollableLayoutStyle](arkts-arkui-tabs-comp-scrollablebarmodeoptions-i.md) is not set or is set to an abnormal value.

The [tabBar](arkts-arkui-tabcontent-comp-attribute.md#tabbar3) attribute of the [TabContent](arkts-arkui-tabcontent-comp.md) component does not support the drag function when it is in the bottom tab style.

**Type:** [CommonModifier](arkts-arkui-tabs-comp-commonmodifier-t.md)

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-TabsOptions-barModifier?: CommonModifier--><!--Device-TabsOptions-barModifier?: CommonModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## barPosition

```TypeScript
barPosition?: BarPosition
```

Position of **Tabs**. The specific position of the tab is affected by the **vertical** attribute: when **vertical** is **true**, **Start** is on the left and **End** is on the right; when **vertical** is **false**, **Start** is at the top and **End** is at the bottom.

Default value: **BarPosition.Start**.

**Type:** [BarPosition](arkts-arkui-tabs-comp-barposition-e.md)

**Default:** 
- API version 11+: BarPosition.Start

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TabsOptions-barPosition?: BarPosition--><!--Device-TabsOptions-barPosition?: BarPosition-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: TabsController
```

**Tabs** controller.

**Type:** [TabsController](arkts-arkui-tabs-comp-tabscontroller-c.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TabsOptions-controller?: TabsController--><!--Device-TabsOptions-controller?: TabsController-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index?: number
```

Index of the currently displayed tab.

Default value: **0**

**NOTE:** 

When set to a value less than 0, the default value is used.

The value range is [0, number of child nodes of **TabContent** - 1].

When **index** is directly modified to switch pages, the switching animation does not take effect. When [changeIndex](arkts-arkui-tabs-comp-tabscontroller-c.md#changeindex) of **TabsController** is used, the switching animation takes effect by default. You can set [animationDuration](arkts-arkui-tabs-comp-attribute.md#animationduration) to **0** to disable the animation.

Since API version 10, this parameter supports two-way binding with [$](../../../ui/state-management/arkts-two-way-sync.md) variables.

When **Tabs** is rebuilt, system resources are switched (such as system font switching or system light/dark mode switching), or component attributes change, the page corresponding to index is jumped to. If you do not want to jump in the preceding cases, use two-way binding.

**Type:** number

**Default:** 
- API version 11+: 0

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TabsOptions-index?: number--><!--Device-TabsOptions-index?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
