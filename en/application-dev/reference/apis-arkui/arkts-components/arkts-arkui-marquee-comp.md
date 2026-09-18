# Marquee

The **Marquee** component is used to display a scrolling piece of text. Text scrolling is activated only when the content width is greater than or equal to the component's width.

> **NOTE** > > To ensure that scrolling frame rates are not affected, it is recommended that the number of **Marquee** components > in a scroll container does not exceed four, or alternatively, use the Text component's > [TextOverflow.MARQUEE](../arkts-apis/arkts-arkui-textoverflow-e.md) as a substitute. > > For the scenario where the frame rate of the **Marquee** component is dynamic, you can use the > [MarqueeDynamicSyncScene](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md) API. > > If the text width is less than the **Marquee** component width, use the property animation to > implement scrolling.

## Child Components

Not supported

## Marquee

```TypeScript
Marquee(options: MarqueeOptions)
```

Creates a marquee.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [MarqueeOptions](arkts-arkui-marqueeoptions-i.md) | Yes | Parameters of the marquee. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [MarqueeOptions](arkts-arkui-marqueeoptions-i.md) | Describes the initialization options of the **Marquee** component. |

## Examples

```TypeScript
### Example 1: Dynamic Update of Marquee Content

This example demonstrates the running effect when the marquee content is dynamically updated, mainly involving the settings of the start, step, loop, fromStart, and src attributes, as well as the [marqueeUpdateStrategy](#marqueeupdatestrategy12) attribute.

Since API version 23, the spacing and delay attributes are added to [MarqueeOptions](#marqueeoptions18).


```

```TypeScript
### Example 2: Setting the Callback for Marquee Stopping

This example shows how to change the marquee state to trigger the onStop callback. After the callback is triggered, the value of numberStop increases by 1.

Since API version 26.0.0, the [onStop](#onstop) API is added.
```
