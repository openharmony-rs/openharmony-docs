# TabsOptions

```TypeScript
declare interface TabsOptions
```

Provides parameters for configuring the **Tabs** component, including tab positions, the current index of the displayed tab, the **Tabs** controller, and universal attributes for the **TabBar**.

**Since:** 15

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## barModifier

```TypeScript
barModifier?: CommonModifier
```

Universal attributes of the tab bar.

**NOTE:** 

If this parameter is dynamically set to **undefined**, the current state will be preserved, and universal attributes will not be reset.

If the setting switches from one **CommonModifier** to another, overlapping attributes will be overwritten, while non-overlapping attributes will coexist without resetting the attributes of the previous **CommonModifier**.

The [barWidth](arkts-arkui-tabs-comp-attribute.md#barwidth), [barHeight](arkts-arkui-tabs-comp-attribute.md#barheight), [barBackgroundColor](arkts-arkui-tabs-comp-attribute.md#barbackgroundcolor), [barBackgroundBlurStyle](arkts-arkui-tabs-comp-attribute.md#barbackgroundblurstyle-1), and [barBackgroundEffect](arkts-arkui-tabs-comp-attribute.md#barbackgroundeffect) attributes of **Tabs** will overwrite the [width](arkts-arkui-common-comp-commonmethod-c.md#width), [height](arkts-arkui-common-comp-commonmethod-c.md#height), [backgroundColor](arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor-1), [backgroundBlurStyle](arkts-arkui-common-comp-commonmethod-c.md#backgroundblurstyle-1), and [backgroundEffect](arkts-arkui-common-comp-commonmethod-c.md#backgroundeffect-1) attributes of **CommonModifier**.

The [align](arkts-arkui-common-comp-commonmethod-c.md#align) attribute works only in [BarMode.Scrollable](arkts-arkui-tabs-comp-attribute.md#barmode-1) mode. In addition, for a horizontal **Tabs** component, it only takes effect when [nonScrollableLayoutStyle](arkts-arkui-tabs-comp-scrollablebarmodeoptions-i.md) is set to an invalid value or is not set.

When set to the bottom tab style, [tabBar](arkts-arkui-tabcontent-comp-attribute.md#tabbar-2) attribute of the TabContent component does not support the dragging feature.

**Type:** [CommonModifier](arkts-arkui-tabs-comp-commonmodifier-t.md)

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## barPosition

```TypeScript
barPosition?: BarPosition
```

Position of the **Tabs** component.

Default value: **BarPosition.Start**

**Type:** [BarPosition](arkts-arkui-tabs-comp-barposition-e.md)

**Default:** 
- API version 11+: BarPosition.Start

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: TabsController
```

Tab controller.

**Type:** [TabsController](arkts-arkui-tabs-comp-tabscontroller-c.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index?: number
```

Index of the currently displayed tab.

Default value: **0**

**NOTE:** 

A value less than 0 evaluates to the default value.

The value ranges from 0 to the number of **TabContent** nodes minus 1.

When the tab is switched by changing the index, the tab switching animation does not take effect. When **changeIndex** of **TabController** is used for tab switching, the tab switching animation is enabled by default. You can disable the animation by setting **animationDuration** to **0**.

Since API version 10, this parameter supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md).

When the **Tabs** component is rebuilt, system resources are switched (for example, system font or theme changes), or component attributes change, the **Tab** component will switch to the one specified by **index**. To prevent this behavior, you are advised to use two-way binding.

**Type:** number

**Default:** 
- API version 11+: 0

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
