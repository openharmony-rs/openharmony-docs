# FontDescriptor

Describes the font descriptor information.

**Since:** 14

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

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Graphics.Drawing

## fontFamily

```TypeScript
fontFamily?: string
```

Family name of the font. Any string is acceptable. The default value is an empty string.

**Type:** string

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## fontFeatures

```TypeScript
fontFeatures?: Array<string>
```

Array of OpenType feature tags supported by the font. The default value is an empty array. Each element in the array is a feature tag string (such as 'liga' for standard ligatures and 'kern' for kerning adjustment), indicating the font features supported by the font.

**Type:** Array&lt;string&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Graphics.Drawing

## fontSubfamily

```TypeScript
fontSubfamily?: string
```

Subfamily name of the font. Any string is acceptable. The default value is an empty string.

**Type:** string

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## fullName

```TypeScript
fullName?: string
```

Font name. Any string is acceptable. The default value is an empty string.

**Type:** string

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## index

```TypeScript
index?: number
```

Font index. This parameter is valid only when the font file is in TTC format. The value is **0** for the TTF format.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Graphics.Drawing

## italic

```TypeScript
italic?: number
```

Whether the font is italic. The value **0** means that the font is not italic, and **1** means the opposite. The default value is **0**.

**Type:** number

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## languages

```TypeScript
languages?: Array<string>
```

List of languages supported by the font. The default value is an empty array. Each element in the array is a language tag string in BCP 47 format (such as 'en' and 'zh-Hans'), indicating the writing languages supported by the font.

**Type:** Array&lt;string&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Graphics.Drawing

## license

```TypeScript
license?: string
```

Font license information. Any string is acceptable. The default value is an empty string.

**Type:** string

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Graphics.Drawing

## localFamilyName

```TypeScript
localFamilyName?: string
```

Extracts the font family name based on the system language configuration. If the font file does not contain the configuration corresponding to the current language, the information corresponding to **en** is used.

**Type:** string

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Graphics.Drawing

## localFullName

```TypeScript
localFullName?: string
```

Extracts the full font name based on the system language configuration. If the font file does not contain the configuration corresponding to the current language, the information corresponding to **en** is used.

**Type:** string

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Graphics.Drawing

## localPostscriptName

```TypeScript
localPostscriptName?: string
```

Extracts the unique font ID based on the system language configuration. If the font file does not contain the configuration corresponding to the current language, the information corresponding to **en** is used.

**Type:** string

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Graphics.Drawing

## localSubFamilyName

```TypeScript
localSubFamilyName?: string
```

Extracts the font subfamily name based on the system language configuration. If the font file does not contain the configuration corresponding to the current language, the information corresponding to **en** is used.

**Type:** string

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Graphics.Drawing

## manufacture

```TypeScript
manufacture?: string
```

Font manufacturer information. Any string is acceptable. The default value is an empty string.

**Type:** string

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Graphics.Drawing

## monoSpace

```TypeScript
monoSpace?: boolean
```

Whether the font is monospaced. The value **true** means that the font is monospaced, and **false** means the opposite. The default value is **false**.

**Type:** boolean

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## path

```TypeScript
path?: string
```

Absolute path of the font. Any string that complies with the system restrictions is acceptable. The default value is an empty string.

**Type:** string

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## postScriptName

```TypeScript
postScriptName?: string
```

Unique name of the font. Any string is acceptable. The default value is an empty string.

**Type:** string

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## symbolic

```TypeScript
symbolic?: boolean
```

Whether the font is symbolic. The value **true** means that the font is symbolic, and **false** means the opposite.

**Type:** boolean

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## trademark

```TypeScript
trademark?: string
```

Font trademark information. Any string is acceptable. The default value is an empty string.

**Type:** string

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Graphics.Drawing

## variationAxisRecords

```TypeScript
variationAxisRecords?: Array<FontVariationAxis>
```

Font variable axis record array, which is used to describe the variable axis information supported by the font. For non-variable fonts, this field is **undefined**.

**Type:** Array&lt;[FontVariationAxis](arkts-arkgraphics2d-text-fontvariationaxis-i.md)&gt;

**Since:** 24

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Graphics.Drawing

## variationInstanceRecords

```TypeScript
variationInstanceRecords?: Array<FontVariationInstance>
```

Font variable instance record array, which is used to describe the variable instance information supported by the font. For non-variable fonts, this field is **undefined**.

**Type:** Array&lt;[FontVariationInstance](arkts-arkgraphics2d-text-fontvariationinstance-i.md)&gt;

**Since:** 24

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Graphics.Drawing

## version

```TypeScript
version?: string
```

Font version. Any string is acceptable. The default value is an empty string.

**Type:** string

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Graphics.Drawing

## weight

```TypeScript
weight?: FontWeight
```

Font weight. The default value is **0**.

**Type:** [FontWeight](arkts-arkgraphics2d-text-fontweight-e.md)

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## width

```TypeScript
width?: number
```

Font width. The value is an integer ranging from 1 to 9. The default value is **0**.

**Type:** number

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing
