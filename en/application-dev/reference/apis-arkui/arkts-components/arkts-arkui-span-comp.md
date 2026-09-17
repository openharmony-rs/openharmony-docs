# Span

As a child of the Text and ContainerSpan components, the **Span** component is used to display inline text.

> **NOTE** > > This component is supported since API version 10. It can inherit attribute settings from its parent component > **Text**. This means that, if an attribute is not set in this component, it takes the value (if any) of the > attribute from its parent component. Only the following attributes can be inherited: **fontColor**, **fontSize**, > **fontStyle**, **fontWeight**, **decoration**, **letterSpacing**, **textCase**, **fontFamily**, and **textShadow**. > > The [universal attributes](../../../reference/apis-arkui/arkui-ts/ts-component-general-attributes.md) are not > supported. To set universal attributes, use Text for configuration or use > [CustomSpan](../arkts-apis/arkts-arkui-customspan-c.md) in the Styled String for custom drawing. > > Among [universal events](../../../reference/apis-arkui/arkui-ts/ts-component-general-events.md), only > onClick click events and > onHover hover events are supported.

## Child Components

Not supported

## Span

```TypeScript
Span(value: string | Resource)
```

Defines the constructor of Span.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Plain text. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [TextBackgroundStyle](arkts-arkui-textbackgroundstyle-i.md) | Define the background style of span. |

## Examples

```TypeScript
### Example 1: Setting the Text Style

This example demonstrates how to apply different text styles and configure click events for the Span.


```

```TypeScript
### Example 2: Setting the Text Shadow

In API version 11 and later versions, the [textShadow](#textshadow11) attribute is used to set the text shadow.


```

```TypeScript
### Example 3: Setting the Background Style

This example demonstrates how to set the background style for text using the [textBackgroundStyle](#textbackgroundstyle11) attribute, available since API version 11.


```

```TypeScript
### Example 4: Setting the Text Baseline Offset

In API version 12 and later versions, this example demonstrates how to set different baseline offsets for text through the [baselineOffset](#baselineoffset12) attribute.


```

```TypeScript
### Example 5 (Set the Variable Font Attribute)

This example sets the variable font attribute through the [fontVariations](#fontvariations) attribute.

Since API version 26.0.0, the [fontVariations](#fontvariations) API is added.
```
