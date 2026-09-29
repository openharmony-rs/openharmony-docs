# FontDescriptor

```TypeScript
interface FontDescriptor
```

Describes the font descriptor information.

**Since:** 14

<!--Device-text-interface FontDescriptor--><!--Device-text-interface FontDescriptor-End-->

**System capability:** SystemCapability.Graphics.Drawing

## Modules to Import

```TypeScript
import { text } from '@kit.ArkGraphics2D';
```

## copyright

```TypeScript
copyright?: string
```

Font copyright information. Any string is acceptable. The default value is an empty string.

**Type:** string

**Since:** 23

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-FontDescriptor-copyright?: string--><!--Device-FontDescriptor-copyright?: string-End-->

**System capability:** SystemCapability.Graphics.Drawing

## fontFamily

```TypeScript
fontFamily?: string
```

Family name of the font. Any string is acceptable. The default value is an empty string.

**Type:** string

**Since:** 14

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-FontDescriptor-fontFamily?: string--><!--Device-FontDescriptor-fontFamily?: string-End-->

**System capability:** SystemCapability.Graphics.Drawing

## fontFeatures

```TypeScript
fontFeatures?: Array<string>
```

Array of OpenType feature tags supported by the font. The default value is an empty array. Each element in the array is a feature tag string (such as 'liga' for standard ligatures and 'kern' for kerning adjustment), indicating the font features supported by the font.

**Type:** Array&lt;string&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-FontDescriptor-fontFeatures?: Array<string>--><!--Device-FontDescriptor-fontFeatures?: Array<string>-End-->

**System capability:** SystemCapability.Graphics.Drawing

## fontSubfamily

```TypeScript
fontSubfamily?: string
```

Subfamily name of the font. Any string is acceptable. The default value is an empty string.

**Type:** string

**Since:** 14

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-FontDescriptor-fontSubfamily?: string--><!--Device-FontDescriptor-fontSubfamily?: string-End-->

**System capability:** SystemCapability.Graphics.Drawing

## fullName

```TypeScript
fullName?: string
```

Font name. Any string is acceptable. The default value is an empty string.

**Type:** string

**Since:** 14

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-FontDescriptor-fullName?: string--><!--Device-FontDescriptor-fullName?: string-End-->

**System capability:** SystemCapability.Graphics.Drawing

## index

```TypeScript
index?: number
```

Font index. This parameter is valid only when the font file is in TTC format. The value is **0** for the TTF format.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-FontDescriptor-index?: int--><!--Device-FontDescriptor-index?: int-End-->

**System capability:** SystemCapability.Graphics.Drawing

## italic

```TypeScript
italic?: number
```

Whether the font is italic. The value **0** means that the font is not italic, and **1** means the opposite. The default value is **0**.

**Type:** number

**Since:** 14

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-FontDescriptor-italic?: int--><!--Device-FontDescriptor-italic?: int-End-->

**System capability:** SystemCapability.Graphics.Drawing

## languages

```TypeScript
languages?: Array<string>
```

List of languages supported by the font. The default value is an empty array. Each element in the array is a language tag string in BCP 47 format (such as 'en' and 'zh-Hans'), indicating the writing languages supported by the font.

**Type:** Array&lt;string&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-FontDescriptor-languages?: Array<string>--><!--Device-FontDescriptor-languages?: Array<string>-End-->

**System capability:** SystemCapability.Graphics.Drawing

## license

```TypeScript
license?: string
```

Font license information. Any string is acceptable. The default value is an empty string.

**Type:** string

**Since:** 23

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-FontDescriptor-license?: string--><!--Device-FontDescriptor-license?: string-End-->

**System capability:** SystemCapability.Graphics.Drawing

## localFamilyName

```TypeScript
localFamilyName?: string
```

Extracts the font family name based on the system language configuration. If the font file does not contain the configuration corresponding to the current language, the information corresponding to **en** is used.

**Type:** string

**Since:** 23

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-FontDescriptor-localFamilyName?: string--><!--Device-FontDescriptor-localFamilyName?: string-End-->

**System capability:** SystemCapability.Graphics.Drawing

## localFullName

```TypeScript
localFullName?: string
```

Extracts the full font name based on the system language configuration. If the font file does not contain the configuration corresponding to the current language, the information corresponding to **en** is used.

**Type:** string

**Since:** 23

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-FontDescriptor-localFullName?: string--><!--Device-FontDescriptor-localFullName?: string-End-->

**System capability:** SystemCapability.Graphics.Drawing

## localPostscriptName

```TypeScript
localPostscriptName?: string
```

Extracts the unique font ID based on the system language configuration. If the font file does not contain the configuration corresponding to the current language, the information corresponding to **en** is used.

**Type:** string

**Since:** 23

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-FontDescriptor-localPostscriptName?: string--><!--Device-FontDescriptor-localPostscriptName?: string-End-->

**System capability:** SystemCapability.Graphics.Drawing

## localSubFamilyName

```TypeScript
localSubFamilyName?: string
```

Extracts the font subfamily name based on the system language configuration. If the font file does not contain the configuration corresponding to the current language, the information corresponding to **en** is used.

**Type:** string

**Since:** 23

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-FontDescriptor-localSubFamilyName?: string--><!--Device-FontDescriptor-localSubFamilyName?: string-End-->

**System capability:** SystemCapability.Graphics.Drawing

## manufacture

```TypeScript
manufacture?: string
```

Font manufacturer information. Any string is acceptable. The default value is an empty string.

**Type:** string

**Since:** 23

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-FontDescriptor-manufacture?: string--><!--Device-FontDescriptor-manufacture?: string-End-->

**System capability:** SystemCapability.Graphics.Drawing

## monoSpace

```TypeScript
monoSpace?: boolean
```

Whether the font is monospaced. The value **true** means that the font is monospaced, and **false** means the opposite. The default value is **false**.

**Type:** boolean

**Since:** 14

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-FontDescriptor-monoSpace?: boolean--><!--Device-FontDescriptor-monoSpace?: boolean-End-->

**System capability:** SystemCapability.Graphics.Drawing

## path

```TypeScript
path?: string
```

Absolute path of the font. Any string that complies with the system restrictions is acceptable. The default value is an empty string.

**Type:** string

**Since:** 14

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-FontDescriptor-path?: string--><!--Device-FontDescriptor-path?: string-End-->

**System capability:** SystemCapability.Graphics.Drawing

## postScriptName

```TypeScript
postScriptName?: string
```

Unique name of the font. Any string is acceptable. The default value is an empty string.

**Type:** string

**Since:** 14

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-FontDescriptor-postScriptName?: string--><!--Device-FontDescriptor-postScriptName?: string-End-->

**System capability:** SystemCapability.Graphics.Drawing

## symbolic

```TypeScript
symbolic?: boolean
```

Whether the font is symbolic. The value **true** means that the font is symbolic, and **false** means the opposite.

**Type:** boolean

**Since:** 14

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-FontDescriptor-symbolic?: boolean--><!--Device-FontDescriptor-symbolic?: boolean-End-->

**System capability:** SystemCapability.Graphics.Drawing

## trademark

```TypeScript
trademark?: string
```

Font trademark information. Any string is acceptable. The default value is an empty string.

**Type:** string

**Since:** 23

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-FontDescriptor-trademark?: string--><!--Device-FontDescriptor-trademark?: string-End-->

**System capability:** SystemCapability.Graphics.Drawing

## variationAxisRecords

```TypeScript
variationAxisRecords?: Array<FontVariationAxis>
```

Font variable axis record array, which is used to describe the variable axis information supported by the font. For non-variable fonts, this field is **undefined**.

**Type:** Array&lt;[FontVariationAxis](arkts-arkgraphics2d-text-fontvariationaxis-i.md)&gt;

**Since:** 24

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-FontDescriptor-variationAxisRecords?: Array<FontVariationAxis>--><!--Device-FontDescriptor-variationAxisRecords?: Array<FontVariationAxis>-End-->

**System capability:** SystemCapability.Graphics.Drawing

## variationInstanceRecords

```TypeScript
variationInstanceRecords?: Array<FontVariationInstance>
```

Font variable instance record array, which is used to describe the variable instance information supported by the font. For non-variable fonts, this field is **undefined**.

**Type:** Array&lt;[FontVariationInstance](arkts-arkgraphics2d-text-fontvariationinstance-i.md)&gt;

**Since:** 24

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-FontDescriptor-variationInstanceRecords?: Array<FontVariationInstance>--><!--Device-FontDescriptor-variationInstanceRecords?: Array<FontVariationInstance>-End-->

**System capability:** SystemCapability.Graphics.Drawing

## version

```TypeScript
version?: string
```

Font version. Any string is acceptable. The default value is an empty string.

**Type:** string

**Since:** 23

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-FontDescriptor-version?: string--><!--Device-FontDescriptor-version?: string-End-->

**System capability:** SystemCapability.Graphics.Drawing

## weight

```TypeScript
weight?: FontWeight
```

Font weight. The default value is **0**.

**Type:** [FontWeight](arkts-arkgraphics2d-text-fontweight-e.md)

**Since:** 14

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-FontDescriptor-weight?: FontWeight--><!--Device-FontDescriptor-weight?: FontWeight-End-->

**System capability:** SystemCapability.Graphics.Drawing

## width

```TypeScript
width?: number
```

Font width. The value is an integer ranging from 1 to 9. The default value is **0**.

**Type:** number

**Since:** 14

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-FontDescriptor-width?: int--><!--Device-FontDescriptor-width?: int-End-->

**System capability:** SystemCapability.Graphics.Drawing
