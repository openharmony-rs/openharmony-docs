# TextTimer

The **TextTimer** component displays timing information and is controlled in text format.

## Child Components

Not supported

## TextTimer

```TypeScript
TextTimer(options?: TextTimerOptions)
```

Create TextTimer component.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [TextTimerOptions](arkts-arkui-texttimeroptions-i.md) | No | Parameters of the **TextTimer** component. The default value is inherited from [TextTimerOptions](arkts-arkui-texttimeroptions-i.md). |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [TextTimerConfiguration](arkts-arkui-texttimerconfiguration-i.md) | Defines the **TextTimer** configuration used by the **ContentModifier** API. |
| [TextTimerOptions](arkts-arkui-texttimeroptions-i.md) | Sets the options used to build the **TextTimer** component. |

## Examples

```TypeScript
### Example 1: Implementing a Text Timer with Start, Pause, and Reset Buttons

This example demonstrates the basic usage of the TextTimer component, setting the timer display format using the [format](#format) attribute.

Users can start, pause, and reset the timer by clicking the start, pause, and reset buttons.


```

```TypeScript
### Example 2: Setting the Text Shadow Style

This example shows how to set the text shadow style for the timer using the [textShadow](#textshadow11) attribute.


```

```TypeScript
### Example 3: Configuring the Custom Content Area

This example showcases two simple TextTimer components set against a light gray background. Once the timers are activated, they display the time progression in real-time. When the countdown timer starts, the background turns black; when the count-up timer starts, the background turns gray.


```

```TypeScript
### Example 4: Enabling the Timer to Start Immediately After Creation

This example demonstrates how to start the TextTimer immediately after it is created.


```

```TypeScript
### Example 5: Setting the Text Style

This example shows text effects in different styles using the [fontColor](#fontcolor), [fontSize](#fontsize), [fontStyle](#fontstyle), [fontWeight](#fontweight) and [fontFamily](#fontfamily) attributes.


```

```TypeScript
### Example 6: Setting the Initial Timing Time

This example sets the initial timing time of the timer through the startTime attribute of [TextTimerOptions](arkts-arkui-texttimeroptions-i.md).

Since API version 26.0.0, the startTime attribute has been added to [TextTimerOptions](arkts-arkui-texttimeroptions-i.md).
```
