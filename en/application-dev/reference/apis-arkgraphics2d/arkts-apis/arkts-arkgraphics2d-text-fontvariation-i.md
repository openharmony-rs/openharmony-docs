# FontVariation

```TypeScript
interface FontVariation
```

Describes a font variation.

**Since:** 12

<!--Device-text-interface FontVariation--><!--Device-text-interface FontVariation-End-->

**System capability:** SystemCapability.Graphics.Drawing

## Modules to Import

```TypeScript
import { text } from '@kit.ArkGraphics2D';
```

## axis

```TypeScript
axis: string
```

Keyword identifier in the variable font property key-value pair, such as 'wght' (weight), 'wdth' (width), and 'ital' (italic).

**Type:** string

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

**Widget capability (ArkTS-Dyn only) :** This API can be used in ArkTS widgets since version 26.0.1.

<!--Device-FontVariation-axis: string--><!--Device-FontVariation-axis: string-End-->

**System capability:** SystemCapability.Graphics.Drawing

## isNormalized

```TypeScript
isNormalized?: boolean
```

Whether to normalize. If the value is **true**, the value range of the value field is -1 to 1, which maps the minimum value to the maximum value configured in the font file. The value **0** indicates the default value configured in the font file. If the value is **false**, the value range of the value field is the adjustable range supported by the font file itself. The default value is **false**.

**Type:** boolean

**Since:** 24

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

**Widget capability (ArkTS-Dyn only) :** This API can be used in ArkTS widgets since version 26.0.1.

<!--Device-FontVariation-isNormalized?: boolean--><!--Device-FontVariation-isNormalized?: boolean-End-->

**System capability:** SystemCapability.Graphics.Drawing

## value

```TypeScript
value: number
```

Value in the font variation key-value pair.

**Type:** number

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

**Widget capability (ArkTS-Dyn only) :** This API can be used in ArkTS widgets since version 26.0.1.

<!--Device-FontVariation-value: double--><!--Device-FontVariation-value: double-End-->

**System capability:** SystemCapability.Graphics.Drawing
