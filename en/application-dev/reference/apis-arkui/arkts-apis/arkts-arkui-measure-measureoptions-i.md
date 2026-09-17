# MeasureOptions

Provides attributes of the measured text.

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { MeasureText, MeasureOptions } from '@kit.ArkUI';
```

## baselineOffset

```TypeScript
baselineOffset?: number | string
```

Baseline offset of the measured text.

Default value: **0**

**Type:** number &#124; string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constraintWidth

```TypeScript
constraintWidth?: number | string | Resource
```

Layout width of the measured text.

**NOTE:** 

The default unit is vp. The value cannot be a percentage. If this parameter is not set, the value of **SizeOptions** is the maximum width allowed for the single-line text.

**Type:** number &#124; string &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontFamily

```TypeScript
fontFamily?: string | Resource
```

Font family of the measured text. Default value: **'HarmonyOS Sans'**

Only the default font is supported.

**Type:** string &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: number | string | Resource
```

Font size of the text to be measured. When **fontSize** is of the number type, the unit is vp.

Default value: **16**

**NOTE:** 

The value cannot be a percentage.

Since API version 12, the fp unit is used when **fontSize** is of the number type.

**Type:** number &#124; string &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontStyle

```TypeScript
fontStyle?: number | FontStyle
```

Font style of the measured text.

Default value: **FontStyle.Normal**

Value range for the number type: [0, 1], with intervals of 1, corresponding to the values in the **FontStyle** enum

**Type:** number &#124; [FontStyle](arkts-arkui-fontstyle-e.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontWeight

```TypeScript
fontWeight?: number | string | FontWeight
```

Font width of the measured text. For the number type, the value ranges from 100 to 900, at an interval of 100. A larger value indicates a heavier font weight. The default value is **400**. For the string type, only strings of the number type are supported, for example, **400**, **"bold"**, **"bolder"**, **"lighter"**, **"regular"**, and **"medium"**, which correspond to the enumerated values in **FontWeight**.

Default value: **FontWeight.Normal**

**Type:** number &#124; string &#124; [FontWeight](arkts-arkui-fontweight-e.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## letterSpacing

```TypeScript
letterSpacing?: number | string
```

Letter spacing of the measured text.

Default value: **0**

**Type:** number &#124; string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lineHeight

```TypeScript
lineHeight?: number | string | Resource
```

Line height of the measured text.

**Type:** number &#124; string &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maxLines

```TypeScript
maxLines?: number
```

Maximum number of lines in the measured text.

Value range: [0, *INT32_MAX*]

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## overflow

```TypeScript
overflow?: number | TextOverflow
```

Display mode when the measured text is too long.

Default value: **1**

Value range for the number type: [0, 3], with intervals of 1, corresponding to the values in the **TextOverflow** enum

**Type:** number &#124; [TextOverflow](arkts-arkui-textoverflow-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textAlign

```TypeScript
textAlign?: number | TextAlign
```

Horizontal alignment mode of the measured text.

Default value: **TextAlign.Start**

Value range for the number type: [0, 3], with intervals of 1, corresponding to the values in the **TextAlign** enum

**Type:** number &#124; [TextAlign](arkts-arkui-textalign-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textCase

```TypeScript
textCase?: number | TextCase
```

Case of the measured text.

Default value: **TextCase.Normal**

Value range for the number type: [0, 2], with intervals of 1, corresponding to the values in the **TextCase** enum

**Type:** number &#124; [TextCase](arkts-arkui-textcase-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textContent

```TypeScript
textContent: string | Resource
```

Content of the measured text.

**Type:** string &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textIndent

```TypeScript
textIndent?: number | string
```

Indentation of the first line. Default value: **0**.

**Type:** number &#124; string

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## wordBreak

```TypeScript
wordBreak?: WordBreak
```

Line break rule.

Default value: **WordBreak.BREAK_WORD**

**NOTE:** 

When used with **{overflow: TextOverflow.Ellipsis}** and **maxLines**, **WordBreak.BREAK_ALL** can insert line breaks between letters when overflow occurs and display excess content with an ellipsis (...).

**Type:** [WordBreak](arkts-arkui-wordbreak-e.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
