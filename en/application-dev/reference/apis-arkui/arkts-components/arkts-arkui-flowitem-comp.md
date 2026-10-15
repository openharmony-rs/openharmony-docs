# FlowItem

A child component of the [WaterFlow](arkts-arkui-waterflow-comp.md) container, used to display specific items in the waterfall layout.

> **NOTE:** 
> 
> * This component can be used only as a child of the [WaterFlow](arkts-arkui-waterflow-comp.md) container.
> 
> * In scrolling scenarios, **FlowItem** and its child components are frequently created and destroyed. To reduce the overhead of repeated node creation and destruction within the ArkUI framework, you are advised to encapsulate the components in **FlowItem** into a custom component and decorate it with the **@Reusable** decorator to enhance component reuse. For best practices, see [Optimizing Frame Loss for Waterfall Loading - Reusing Components](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-waterflow-performance-optimization#section189041489339).

## Child Components

This component supports only one child component.

## FlowItem

```TypeScript
FlowItem()
```

Creates a waterfall flow child component. This component can be used only as a child of the [WaterFlow](arkts-arkui-waterflow-comp.md) container.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-FlowItemInterface-(): FlowItemAttribute--><!--Device-FlowItemInterface-(): FlowItemAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Summary
