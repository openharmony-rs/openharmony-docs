# Gauge

The **Gauge** component represents a gauge that displays data in a circular format.

> **NOTE** > > - This component supports WithTheme since API version 26.0.0.

## Child Components

This component can contain only one child component.

> **NOTE:** 
> 
> - Supported child component types: built-in and custom components, including [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md) but excluding ForEach and LazyForEach.
> 
> - You are advised to use the **Text** component to build the current value and auxiliary text.
> 
> - If the width and height of the child component are in percentage, the reference range is the rectangle that has the outer ring as its inscribed circle.

## Gauge

```TypeScript
Gauge(options: GaugeOptions)
```

Creates a gauge.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [GaugeOptions](arkts-arkui-gaugeoptions-i.md) | Yes | Settings of the gauge. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [GaugeConfiguration](arkts-arkui-gaugeconfiguration-i.md) | You need a custom class to implement the **ContentModifier** API. Inherits from [CommonConfiguration](arkts-arkui-commonconfiguration-i.md). |
| [GaugeIndicatorOptions](arkts-arkui-gaugeindicatoroptions-i.md) | Provides gauge indicator options. |
| [GaugeOptions](arkts-arkui-gaugeoptions-i.md) | Provides gauge options. |
| [GaugeShadowOptions](arkts-arkui-gaugeshadowoptions-i.md) | Inherits from [MultiShadowOptions](arkts-arkui-multishadowoptions-i.md) and has all attributes of **MultiShadowOptions**. |

## Examples

```TypeScript
### Example 1: Implementing a Multi-color Gauge

This example demonstrates how to implement a multi-color gauge using the [colors](#colors) attribute.


```

```TypeScript
### Example 2: Implementing a Single-Color Gauge

This example demonstrates how to implement a single-color gauge using the [colors](#colors) attribute.


```

```TypeScript
### Example 3: Configuring a Custom Description Area

This example illustrates how to configure a custom description area using the [description](#description11) attribute.


```

```TypeScript
### Example 4: Configuring the Auxiliary Area

This example demonstrates how to configure the auxiliary area by setting child components.


```

```TypeScript
### Example 5: Setting the Minimum and Maximum Values

This example shows how to set the minimum and maximum values of the gauge by configuring min and max in [GaugeOptions](arkts-arkui-gaugeoptions-i.md).


```

```TypeScript
### Example 6: Setting the Indicator

This example illustrates how to set the indicator of the gauge using the [indicator](#indicator11) attribute.


```

```TypeScript
### Example 7: Setting the Start and End Angles

This example demonstrates how to set the start and end angles of the gauge using the [startAngle](#startangle) and [endAngle](#endangle) attributes.


```

```TypeScript
### Example 8: Setting the Custom Content Area

This example shows how to customize the content area of the gauge using the [contentModifier](#contentmodifier12) attribute.


```

```TypeScript
### Example 9: Securing Sensitive Information

This example shows how to call the [privacySensitive](#privacysensitive12) API. The actual privacy hiding effect requires support from the widget framework.


```

```TypeScript
### Example 10: Implementing a Custom Indicator

This example demonstrates how to implement a custom indicator using [indicator](#indicator11). You can import an SVG image to replace the default indicator.
```

```TypeScript
<svg width='200px' height='200px'>
    <path d='M 10,30 A 20,20 0,0,1 50,30 A 20,20 0,0,1 90,30 Q 90,60 50,90 Q 10,60 10,30 z'
          stroke='black' stroke-width='3' fill='white'>
    </path>
</svg>
```
