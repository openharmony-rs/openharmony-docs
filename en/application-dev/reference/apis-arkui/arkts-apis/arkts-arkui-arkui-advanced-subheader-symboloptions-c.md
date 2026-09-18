# SymbolOptions

Declare type SymbolOptions

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { OperationOption, OperationType, SelectOptions, SubHeader, SymbolOptions } from '@kit.ArkUI';
```

## effectStrategy

```TypeScript
effectStrategy?: SymbolEffectStrategy
```

Effect strategy of the symbol glyph.

Default value: **SymbolEffectStrategy.NONE**.

**NOTE:** 

For the resources referenced in **&#36;r('sys.symbol.ohos_*')**, only **ohos_wifi** supports the hierarchical effect.

**Type:** [SymbolEffectStrategy](../arkts-components/arkts-arkui-symboleffectstrategy-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor?: Array<ResourceColor>
```

Color of the symbol glyph.

Default value: depending on the rendering strategy

**Type:** Array&lt;[ResourceColor](arkts-arkui-resourcecolor-t.md)&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: number | string | Resource
```

Size of the symbol glyph.

For the number type, the value must be greater than or equal to 0.

For the string type, numeric string values with optional units, for example, **"10"** or **"10fp"**, are supported.

Default value: system default value

**Type:** number &#124; string &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontWeight

```TypeScript
fontWeight?: number | FontWeight | string
```

Weight of the symbol glyph.

For the number type, the value ranges from 100 to 900, at an interval of 100. A larger value indicates a heavier font weight. The default value is **400**.

For the string type, only strings of the number type are supported, for example, **"400"**, **"bold"**, **"bolder"**, **"lighter"**, **"regular"**, and **"medium"**, which correspond to the enumerated values in **FontWeight**.

Default value: **FontWeight.Normal**.

**Type:** number &#124; [FontWeight](arkts-arkui-fontweight-e.md) &#124; string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## renderingStrategy

```TypeScript
renderingStrategy?: SymbolRenderingStrategy
```

Rendering strategy of the symbol glyph.

Default value: **SymbolRenderingStrategy.SINGLE**.

**NOTE:** 

For the resources referenced in **&#36;r('sys.symbol.ohos_*')**, only **ohos_trash_circle**, **ohos_folder_badge_plus**, and **ohos_lungs** support the **MULTIPLE_COLOR** modes.

**Type:** [SymbolRenderingStrategy](../arkts-components/arkts-arkui-symbolrenderingstrategy-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
