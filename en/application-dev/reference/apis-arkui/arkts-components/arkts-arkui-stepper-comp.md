# Stepper

The **Stepper** component provides a step navigator, suitable for guiding users through a step-by-step task completion process.

> **NOTE**

## Child Components

Only the child component StepperItem is supported.

## Stepper

```TypeScript
Stepper(value?: { index?: number })
```

Creates a **Stepper** component.

> **NOTE:** 

**Since:** 8

**Deprecated since:** 22

**Substitutes:** index

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | { index?: number } | No | Index of the **StepperItem** that is currently displayed.<br>Default value: **0**<br> Since API version 10, this parameter supports two-way binding through [&#36;&#36;](../../../ui/state-management/arkts-two-way-sync.md). |

## Summary

## Examples

```TypeScript
### Example 1: Using the Stepper Component

This example demonstrates how to use the Stepper component.


```

```TypeScript
### Example 2: Using Swiper as a Substitute for Stepper

This example demonstrates how to use the Swiper component to achieve the functionality of the Stepper component. The resulting effect is the same as in Example 1.
```
