# SymbolSpan

As a child component of the **Text** component, the **SymbolSpan** component is used to display small icons.

> **NOTE**

> - This component can inherit attribute settings from its parent component **Text**. This means that, if an > attribute is not set in this component, it takes the value of the attribute (if set) from its parent component. > > - The **SymbolSpan** component is not dimmed when dragged.

## Child Components

Not supported

## SymbolSpan

```TypeScript
SymbolSpan(value: Resource)
```

Defines the constructor of SymbolSpan.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Resource of the **SymbolSpan** component, for example, **&#36;r('sys.symbol.ohos_wifi')**. |

## Summary

## Examples

```TypeScript
### Example 1: Setting Rendering and Animation Strategies

This example demonstrates different rendering and effect strategies using [renderingStrategy](#renderingstrategy) and [effectStrategy](#effectstrategy), available since API version 11.


```

```TypeScript
### Example 2: Configuring Dynamic Attributes

This example demonstrates how to create icons of a specified style using the [attributeModifier](#attributemodifier12) attribute, available since API version 12.


```

```TypeScript
### Example 3: Setting Font Weight

This example uses the [fontWeight](#fontweight-1) attribute to demonstrate the effects of different font weight configurations of SymbolSpan: the first row of small icon symbols shows the effects of setting the font weight values to 220 and 660 respectively after enabling variable font weight; the second row of small icon symbols shows the effects of setting whether to follow the device's system font weight level for automatic update, after the device's system font weight is set to bold.

Since API version 26.0.0, the [fontWeight](#fontweight-1) attribute is added.
```
