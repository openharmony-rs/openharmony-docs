# RichEditorSymbolSpanStyleResult

Provides the symbol span style information returned by the backend.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## effectStrategy

```TypeScript
effectStrategy: SymbolEffectStrategy
```

Effect strategy of the symbol span.

Default value: **SymbolEffectStrategy.NONE**

**Type:** [SymbolEffectStrategy](arkts-arkui-symboleffectstrategy-e.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor: Array<ResourceColor>
```

Color of the symbol span.

Default value: depending on the rendering strategy

**Type:** Array&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt;

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize: number | string | Resource
```

Size of the symbol span. The default unit is fp.

The default value follows the theme.

**Type:** number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontWeight

```TypeScript
fontWeight: number | FontWeight | string
```

Weight of the symbol span.

For the number type, the value ranges from 100 to 900, at an interval of 100. A larger value indicates a heavier font weight. The default value is **400**.

For the string type, only strings of the number type are supported, for example, **"400"**, **"bold"**, **"bolder"**, **"lighter"**, **"regular"**, and **"medium"**, which correspond to the enumerated values in **FontWeight**.

Default value: **FontWeight.Normal**

**Type:** number &#124; [FontWeight](../arkts-apis/arkts-arkui-fontweight-e.md) &#124; string

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## renderingStrategy

```TypeScript
renderingStrategy: SymbolRenderingStrategy
```

Rendering strategy of the symbol span.

Default value: **SymbolRenderingStrategy.SINGLE**

**Type:** [SymbolRenderingStrategy](arkts-arkui-symbolrenderingstrategy-e.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
