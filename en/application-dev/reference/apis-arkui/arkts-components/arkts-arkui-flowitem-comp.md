# FlowItem

**FlowItem** is a child component of the WaterFlow container and is used to display specific items in the container layout.

> **NOTE** > > * > > * This component can be used only as a child of WaterFlow. > > * In the swiping scenario, the **FlowItem** component and its child components are frequently created and > destroyed. You are advised to encapsulate components in the **FlowItem** component into custom components and > decorating them with the @Reusable decorator, making the components reusable and reducing the overhead of > repeatedly creating and destroying nodes in the ArkUI framework. For best practices, see > [Reusing Components](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-waterflow-performance-optimization#section189041489339).

## Child Components

This component supports only one child component.

## FlowItem

```TypeScript
FlowItem()
```

Creates a child component in the **WaterFlow** layout.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Summary
