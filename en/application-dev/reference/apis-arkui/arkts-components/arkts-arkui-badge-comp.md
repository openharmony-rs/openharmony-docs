# Badge

The **Badge** component is a container that can be attached to another component for notification and reminder purposes.

## Child Components

This component supports only one child component.

> **NOTE:** 
> 
> - Allowed child component types: built-in and custom components, including rendering control types ([if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md), ForEach, and LazyForEach).
> 
> - A custom component defaults to a width and height of 0. You must explicitly set its width and height; otherwise,the **Badge** component will not be displayed.
> 
> - When there are multiple child components, only the last child component is displayed on the UI. However, the status update of other child components will still cause the badge and its child components to be re-rendered.
> 
> - Child component layout is independent and does not automatically adjust to avoid overlapping with the badge.

## Badge

```TypeScript
Badge(value: BadgeParamWithNumber)
```

Creates a badge with the given numerical value.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [BadgeParamWithNumber](arkts-arkui-badgeparamwithnumber-i.md) | Yes | Options of the numeric badge. |

## Badge

```TypeScript
Badge(value: BadgeParamWithString)
```

Creates a badge with the given string.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [BadgeParamWithString](arkts-arkui-badgeparamwithstring-i.md) | Yes | Options of the string-type badge. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [BadgeParam](arkts-arkui-badgeparam-i.md) | Provides basic parameters for creating a badge. |
| [BadgeParamWithNumber](arkts-arkui-badgeparamwithnumber-i.md) | Inherits from [BadgeParam](arkts-arkui-badgeparam-i.md) and has all attributes of **BadgeParam**. |
| [BadgeParamWithString](arkts-arkui-badgeparamwithstring-i.md) | Inherits from [BadgeParam](arkts-arkui-badgeparam-i.md) and has all attributes of **BadgeParam**. |
| [BadgeStyle](arkts-arkui-badgestyle-i.md) | Describes the badge style. It includes the font color, font size, badge color, badge size, etc. |

### Enums

| Name | Description |
| --- | --- |
| [BadgePosition](arkts-arkui-badgeposition-e.md) | Enumerates the display positions of a badge. |

## Examples

```TypeScript
### Example 1: Setting Badge Component Content

This example uses the input parameter count of [BadgeParamWithNumber](arkts-arkui-badgeparamwithnumber-i.md) and the input parameter value of [BadgeParamWithString](arkts-arkui-badgeparamwithstring-i.md) to display different effects of the badge component when null, a character, or a number is passed in.


```

```TypeScript
### Example 2: Setting a Number to Control Badge Display

This example uses the count attribute to hide and show the badge component when the number is set to 0 and 1.


```

```TypeScript
### Example 3: Setting the Outer Border and Text Extension Mode

Since API version 22, this example uses the outerBorderColor and outerBorderWidth attributes to set the outer border, and uses the enableAutoAvoidance attribute to control whether to avoid obstacles when the badge text is extended for display.
```
