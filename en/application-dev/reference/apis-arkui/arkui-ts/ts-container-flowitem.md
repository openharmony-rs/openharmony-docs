# FlowItem

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @rongShao-Z; @guozejun-->
<!--Designer: @guozejun-->
<!--Tester: @leiyuqian-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=f1bbf293e58e8daa3733902ea6b2a7d76e6bbdaa translatedAt=2026-07-30T02:40:53.453Z pushedAt=2026-08-01T06:42:55.902Z -->

A child component of the [WaterFlow](ts-container-waterflow.md) container, used to display specific items in the waterfall layout.

> **NOTE**
>
> * This component is supported since API version 9. Updates will be marked with a superscript to indicate their earliest API version.
> * This component can be used only as a child of the [WaterFlow](ts-container-waterflow.md) container.
> * In scrolling scenarios, **FlowItem** and its child components are frequently created and destroyed. To reduce the overhead of repeated node creation and destruction within the ArkUI framework, you are advised to encapsulate the components in **FlowItem** into a custom component and decorate it with the **@Reusable** decorator to enhance component reuse. For best practices, see [Optimizing Frame Loss for Waterfall Loading - Reusing Components](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-waterflow-performance-optimization#section189041489339).

## Child Components

This component supports only one child component.

## APIs

FlowItem()

Creates a waterfall flow child component. This component can be used only as a child of the [WaterFlow](ts-container-waterflow.md) container.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## Attributes

None

## Example

See [WaterFlow](ts-container-waterflow.md#example).