# IndicatorComponent

Defines IndicatorComponent.

## IndicatorComponent

```TypeScript
IndicatorComponent(controller?: IndicatorComponentController)
```

Called when a indicator is set.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| controller | [IndicatorComponentController](arkts-arkui-indicatorcomponentcontroller-c.md) | No | indicator component controller. |

## Summary

## Examples

```TypeScript
### Example 1: Using a Dot Indicator with a Swiper Component

This example binds the same [IndicatorComponentController](arkts-arkui-indicatorcomponentcontroller-c.md) object to both the [indicator](ts-container-swiper.md#indicator) API of the [Swiper](ts-container-swiper.md) component and the [IndicatorComponent](#indicatorcomponent) constructor, enabling interaction between the dot indicator and the Swiper component.


```

```TypeScript
### Example 2: Using a Digit Indicator with a Swiper Component

This example binds the same [IndicatorComponentController](arkts-arkui-indicatorcomponentcontroller-c.md) object to both the [indicator](ts-container-swiper.md#indicator) API of the [Swiper](ts-container-swiper.md) component and the [IndicatorComponent](#indicatorcomponent) constructor, enabling interaction between the digit indicator and the Swiper component.
```
