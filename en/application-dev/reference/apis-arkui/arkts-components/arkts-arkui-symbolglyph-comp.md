# SymbolGlyph

The **SymbolGlyph** component represents a symbol glyph.<!--RP1--><!--RP1End-->

> **NOTE**

## Child Components

Not supported

## SymbolGlyph

```TypeScript
SymbolGlyph(value?: Resource)
```

Defines the constructor of SymbolGlyph.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Resource](../arkts-apis/arkts-arkui-resource-t.md) | No | Resource of the **SymbolGlyph** component, for example, **&#36;r('sys.symbol.ohos_wifi')**. |

## Summary

### Enums

| Name | Description |
| --- | --- |
| [EffectDirection](arkts-arkui-effectdirection-e.md) | The direction type of symbol effect. |
| [EffectFillStyle](arkts-arkui-effectfillstyle-e.md) | The fill style of symbol effect. |
| [EffectScope](arkts-arkui-effectscope-e.md) | The scope type of the symbol effect. |
| [ReplaceEffectType](arkts-arkui-replaceeffecttype-e.md) | The replace effect type of symbol. |
| [SymbolEffectStrategy](arkts-arkui-symboleffectstrategy-e.md) | Enumerates symbol effect types. Once applied, the symbol effect becomes active instantly, eliminating the need for triggering. |
| [SymbolRenderingStrategy](arkts-arkui-symbolrenderingstrategy-e.md) | The symbol rendering strategy. |

## Examples

```TypeScript
### Example 1: Setting Rendering and Effect Strategies

This example demonstrates different rendering and effect strategies using [renderingStrategy](#renderingstrategy) and [effectStrategy](#effectstrategy), available since API version 11.


```

```TypeScript
### Example 2: Setting Symbol and Shadow Effects

Starting from API version 12, this example uses the [symbolEffect](#symboleffect12) attribute to demonstrate the effects of various animations and the shadow effect combined with [symbolShadow](arkts-arkui-symbolglyph-comp-attribute.md#symbolshadow) (starting from API version 20). Among them, disabling animations and quick replacement animations require API version 20 or later.


```

```TypeScript
### Example 3: Setting Gradient Color Effects

Starting from API version 20, this example uses the [shaderStyle](#shaderstyle20) interface to implement the function of displaying the SymbolGlyph component as a gradient color.


```

```TypeScript
### Example 4 (Setting the SymbolGlyph Color)

This example passes a ColorMetrics type parameter through the [fontColor](#fontcolor-1) attribute to set the color of the SymbolGlyph component.

Starting from API version 26.0.0, [fontColor](#fontcolor-1) is newly supported.


```

```TypeScript
### Example 5 (Setting Font Weight)

This example uses the [fontWeight](#fontweight-1) attribute to demonstrate the effects of different font weight configurations of SymbolGlyph: the first row of symbol glyphs shows the effects of setting the font weight values to 220 and 660 respectively after enabling variable font weight; the second row of symbol glyphs shows the effects of setting the font weight to follow and not follow the automatic update of the device's system font weight level after setting the device's system font weight to bold.

Since API version 26.0.0, the [fontWeight](#fontweight-1) attribute is added.
```
