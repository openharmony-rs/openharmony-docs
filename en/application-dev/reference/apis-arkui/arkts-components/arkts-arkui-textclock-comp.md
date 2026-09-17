# TextClock

The **TextClock** component displays the current system time in text format for different time zones. The time is accurate to seconds.

When the component is invisible, the time change stops. The visible status of a component is processed based on [onVisibleAreaChange](arkts-arkui-commonmethod-c.md#onvisibleareachange). If the visible threshold **ratios** is greater than 0, the component is visible.

## Child Components

Not supported

## TextClock

```TypeScript
TextClock(options?: TextClockOptions)
```

Create TextClock component.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [TextClockOptions](arkts-arkui-textclockoptions-i.md) | No | Options of the text clock. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [TextClockConfiguration](arkts-arkui-textclockconfiguration-i.md) | You need a custom class to implement the **ContentModifier** API. |
| [TextClockOptions](arkts-arkui-textclockoptions-i.md) | Options used to build the **TextClock** component. |

## Examples

```TypeScript
### Example 1: Implementing a Text Clock with Start/Stop Control

This example demonstrates the basic usage of the TextClock component, setting the clock display format using the [format](#format) attribute.

Clicking "start TextClock" triggers the callback to invoke TextClockController and initiate the clock. Clicking "stop TextClock" to invoke TextClockController and stop the clock.

This example uses the [onDateChange](#ondatechange) callback to update accumulateTime whenever the text clock refreshes.


```

```TypeScript
### Example 2: Setting the Text Shadow Style

This example sets the shadow style of the clock text through [textShadow](#textshadow11).


```

```TypeScript
### Example 3: Configuring the Custom Content Area

This example implements the functionality of customizing the style of a text clock, creating a time picker component with a custom style: The time picker dynamically adjusts its selected value based on the text clock's timezone offset and the timezone offset in seconds from UTC to deliver a clock effect. Depending on whether the text clock is started, the time picker toggles between a 12-hour and a 24-hour format display.


```

```TypeScript
### Example 4: Setting Leading Zero

This example demonstrates how to use the [dateTimeOptions](#datetimeoptions12) attribute to add or remove the leading zero for the hour field. By default, the hour field includes a leading zero in the 24-hour format, but typically does not include a leading zero in the 12-hour format.


```

```TypeScript
### Example 5: Setting the Text Display Style

This example demonstrates how to use the [fontFeature](#fontfeature11), [fontColor](#fontcolor), [fontStyle](#fontstyle), [fontWeight](#fontweight) and [fontFamily](#fontfamily) attributes to set the text display style of the clock.
```
