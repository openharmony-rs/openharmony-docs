# MeasureOptions

```TypeScript
export interface MeasureOptions
```

Provides attributes of the measured text.

**Since:** 9

<!--Device-unnamed-export interface MeasureOptions--><!--Device-unnamed-export interface MeasureOptions-End-->

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

Default value: **0**. Unit: vp. The string type supports strings with units, for example, **'10px'** and **'10vp'**.

**Note:** A positive number indicates that the baseline is offset upward, and a negative number indicates that the baseline is offset downward.

**Type:** number &#124; string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MeasureOptions-baselineOffset?: number | string--><!--Device-MeasureOptions-baselineOffset?: number | string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constraintWidth

```TypeScript
constraintWidth?: number | string | Resource
```

Layout width of the measured text. Value range: [0, +∞).

**Note:** 

The default unit is vp. The value cannot be a percentage. This parameter takes effect only in the **measureTextSize** API. If it is not set, the text width is the maximum width of a single-line layout. If it is set, the set value is used, which also affects the line breaking mode and height calculation result of the text.

**Type:** number &#124; string &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MeasureOptions-constraintWidth?: number | string | Resource--><!--Device-MeasureOptions-constraintWidth?: number | string | Resource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontFamily

```TypeScript
fontFamily?: string | Resource
```

Font family of the measured text. The default font is **'HarmonyOS Sans'**, and currently only this font is supported. When another font name is set, the default font **'HarmonyOS Sans'** is used.

**Type:** string &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MeasureOptions-fontFamily?: string | Resource--><!--Device-MeasureOptions-fontFamily?: string | Resource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: number | string | Resource
```

Font size of the measured text. Value range: [0, +∞). A value beyond the range causes an abnormal calculation result.

Default value: **16**

**Note:** 

The value cannot be a percentage.

When **fontSize** is of the number type, the fp unit is used since API version 12, and the vp unit is used before API version 12.

**Type:** number &#124; string &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MeasureOptions-fontSize?: number | string | Resource--><!--Device-MeasureOptions-fontSize?: number | string | Resource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontStyle

```TypeScript
fontStyle?: number | FontStyle
```

Font style of the measured text.

Default value: **FontStyle.Normal**

The value range of the number type is [0, 1], with an interval of 1, corresponding to the enumerated values in **FontStyle** in sequence. When the value is out of range, the default value **FontStyle.Normal** is used.

**Type:** number &#124; [FontStyle](arkts-arkui-fontstyle-e.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MeasureOptions-fontStyle?: number | FontStyle--><!--Device-MeasureOptions-fontStyle?: number | FontStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontWeight

```TypeScript
fontWeight?: number | string | FontWeight
```

Font weight of the measured text. The value range of the number type is [100, 900], with an interval of 100. The default value is **400**. A larger value indicates a heavier font weight. When the value is out of range or not on an interval value, the default value **400** is used. For the string type, only strings of the number type, for example, "400", as well as "bold", "bolder", "lighter", "regular", and "medium" are supported, which correspond to the enumerated values in **FontWeight**.

Default value: **FontWeight.Normal**

**Type:** number &#124; string &#124; [FontWeight](arkts-arkui-fontweight-e.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MeasureOptions-fontWeight?: number | string | FontWeight--><!--Device-MeasureOptions-fontWeight?: number | string | FontWeight-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## letterSpacing

```TypeScript
letterSpacing?: number | string
```

Letter spacing of the measured text.

Default value: **0**

**Note:** 

The default unit is vp. The string type supports strings with units, for example, **'10px'** and **'10vp'**.

**Type:** number &#124; string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MeasureOptions-letterSpacing?: number | string--><!--Device-MeasureOptions-letterSpacing?: number | string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lineHeight

```TypeScript
lineHeight?: number | string | Resource
```

Line height of the measured text, which affects the height calculation result and line spacing of multi-line text. A larger value indicates larger line spacing.

Value range: [0, +∞). The string type supports strings with units, for example, **'10px'** and **'10vp'**.

Default value: the default line height of the system

The default unit is vp.

**Type:** number &#124; string &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MeasureOptions-lineHeight?: number | string | Resource--><!--Device-MeasureOptions-lineHeight?: number | string | Resource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maxLines

```TypeScript
maxLines?: number
```

Maximum number of lines of the measured text. When the actual number of lines exceeds this value, the calculation result of **measureTextSize** is based on the maximum number of lines, and the excess part is not included in the height calculation.

Value range: [0, INT32_MAX]. When a negative number or a value beyond the range is passed in, the default value is used.

Default value: no limit

**Note:** It can be used together with **TextOverflow.Ellipsis** of **overflow** and **wordBreak.BREAK_ALL** to truncate English words by letter and display the excess part with an ellipsis.

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MeasureOptions-maxLines?: number--><!--Device-MeasureOptions-maxLines?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## overflow

```TypeScript
overflow?: number | TextOverflow
```

Truncation mode when the measured text is too long. It takes effect only when used together with **maxLines**.

Default value: **1**

The value range of the number type is [0, 3], with an interval of 1, corresponding to the enumerated values in **TextOverflow** in sequence. When the value is out of range, the default value **1** is used.

**Note:** When set to **TextOverflow.Ellipsis**, it can be used together with **wordBreak.BREAK_ALL** and **maxLines** to truncate English words by letter and display the excess part with an ellipsis.

**Type:** number &#124; [TextOverflow](arkts-arkui-textoverflow-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MeasureOptions-overflow?: number | TextOverflow--><!--Device-MeasureOptions-overflow?: number | TextOverflow-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textAlign

```TypeScript
textAlign?: number | TextAlign
```

Horizontal alignment mode of the measured text.

Default value: **TextAlign.Start**

The value range of the number type is [0, 3], with an interval of 1, corresponding to the enumerated values in **TextAlign** in sequence. When the value is out of range, the default value **TextAlign.Start** is used.

**Type:** number &#124; [TextAlign](arkts-arkui-textalign-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MeasureOptions-textAlign?: number | TextAlign--><!--Device-MeasureOptions-textAlign?: number | TextAlign-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textCase

```TypeScript
textCase?: number | TextCase
```

Case of the measured text.

Default value: **TextCase.Normal**

The value range of the number type is [0, 2], with an interval of 1, corresponding to the enumerated values in **TextCase** in sequence. When the value is out of range, the default value **TextCase.Normal** is used.

**Type:** number &#124; [TextCase](arkts-arkui-textcase-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MeasureOptions-textCase?: number | TextCase--><!--Device-MeasureOptions-textCase?: number | TextCase-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textContent

```TypeScript
textContent: string | Resource
```

Content of the measured text.

**Type:** string &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MeasureOptions-textContent: string | Resource--><!--Device-MeasureOptions-textContent: string | Resource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textIndent

```TypeScript
textIndent?: number | string
```

Indentation of the first line of text. Value range: [0, +∞). When the value is out of range, the default value **0** is used.

Default value: **0**.

**Note:** 

The default unit is vp. The string type supports strings with units, for example, **'10px'** and **'10vp'**.

**Type:** number &#124; string

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MeasureOptions-textIndent?: number | string--><!--Device-MeasureOptions-textIndent?: number | string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## wordBreak

```TypeScript
wordBreak?: WordBreak
```

Word breaking rule.

Default value: **WordBreak.BREAK_WORD**

**Note:** 

WordBreak.BREAK_ALL, when used together with **TextOverflow.Ellipsis** of **overflow** and **maxLines**, can truncate English words by letter and display the excess part with an ellipsis.

**Type:** [WordBreak](arkts-arkui-wordbreak-e.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MeasureOptions-wordBreak?: WordBreak--><!--Device-MeasureOptions-wordBreak?: WordBreak-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
