# @ohos.measure (Text Measurement)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hddgzw-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=08942777370a0b90b1f82affd44908847b9279aa translatedAt=2026-09-01T03:21:32.094Z pushedAt=2026-09-02T01:58:45.107Z -->

This module provides APIs for calculating text width and height, and supports configuring various text attributes (such as the font size, style, weight, and line height). It is applicable to scenarios where the text size needs to be obtained before component construction, such as adaptive layout, text clipping, and dynamic UI size adjustment, helping you achieve more precise layout calculation and performance optimization.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - This module cannot be used in the file declaration of the [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md). In other words, the APIs of this module can be used only after a component instance is created; they cannot be called in the lifecycle of the UIAbility.
>
> - To perform more complex text measurements, you are advised to use the measurement APIs under [Paragraph](../apis-arkgraphics2d/js-apis-graphics-text.md#paragraph).
>
> - When calling the text measurement APIs, you are advised not to use [ApplicationContext.setFontSizeScale](../apis-ability-kit/js-apis-inner-application-applicationContext.md#applicationcontextsetfontsizescale13) to set the application font size scale at the same time. To ensure timing consistency, you are advised to listen for font size scale changes on your own to guarantee the accuracy of measurement results.
>
> - For measuring text after truncation, direct use of the string length for truncation may lead to inaccuracies, because certain Unicode characters (for example, emojis) have code points with a length greater than 1. As such, you are advised to perform iterative processing based on Unicode code points during truncation.

## Modules to Import

```ts
import { MeasureText } from '@kit.ArkUI';
```

## MeasureText.measureText<sup>(deprecated)</sup>

static measureText(options: MeasureOptions): number

Measures the single-line display width of the specified text. For multi-line text (separated by newline characters **\n**), this API returns the width of the longest line.

> **NOTE**
>
> - This API is supported since API version 9 and deprecated since API version 18. You are advised to use [measureText](arkts-apis-uicontext-measureutils.md#measuretext12) instead. Before calling this API, you need to obtain the [MeasureUtils](arkts-apis-uicontext-measureutils.md) object using the [getMeasureUtils](arkts-apis-uicontext-uicontext.md#getmeasureutils12) method in [UIContext](arkts-apis-uicontext-uicontext.md). Directly using **measureText** can lead to the issue of [ambiguous UI context](../../ui/arkts-global-interface.md#ambiguous-ui-context).
>
> - Since API version 12, you can use the [getMeasureUtils](arkts-apis-uicontext-uicontext.md#getmeasureutils12) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [MeasureUtils](arkts-apis-uicontext-measureutils.md) object associated with the current UI context.
>
> - **measureText** always measures single-line text width. Layout constraints in **options** (**constraintWidth**, **maxLines**, and more) do not affect results. For layout-constrained width measurement, use [measureTextSize](arkts-apis-uicontext-measureutils.md#measuretextsize12).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                             | Mandatory  | Description       |
| ------- | ------------------------------- | ---- | --------- |
| options | [MeasureOptions](#measureoptions) | Yes   | Information about the measured text.|

**Return value**

| Type         | Description      |
| ------------  | --------- |
| number        | Text width.<br>Unit: px|

> **NOTE**
>
> Directly using **MeasureText** can lead to the issue of [ambiguous UI context](../../ui/arkts-global-interface.md#ambiguous-ui-context). To avoid this, obtain the [MeasureUtils](arkts-apis-uicontext-measureutils.md) object associated with the current UI context by using the [getMeasureUtils](./arkts-apis-uicontext-uicontext.md#getmeasureutils12) API in [UIContext](arkts-apis-uicontext-uicontext.md).

**Example**

```ts
import { MeasureText } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State textWidth: number = MeasureText.measureText({
    // You are advised to use this.getUIContext().getMeasureUtils().measureText().
    textContent: "Hello World",
    fontSize: '50px'
  });

  build() {
    Row() {
      Column() {
        Text(`The width of 'Hello World': ${this.textWidth}`)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## MeasureText.measureTextSize<sup>(deprecated)</sup>

static measureTextSize(options: MeasureOptions): SizeOptions

Measures the width and height of the given text.

> **NOTE**
>
> - This API is supported since API version 10 and deprecated since API version 18. You are advised to use [measureTextSize](arkts-apis-uicontext-measureutils.md#measuretextsize12) instead. Before calling this API, you need to obtain the [MeasureUtils](arkts-apis-uicontext-measureutils.md) object using the [getMeasureUtils](arkts-apis-uicontext-uicontext.md#getmeasureutils12) method in [UIContext](arkts-apis-uicontext-uicontext.md). Directly using **measureTextSize** can lead to the issue of [ambiguous UI context](../../ui/arkts-global-interface.md#ambiguous-ui-context).
>
> - Since API version 12, you can use the [getMeasureUtils](arkts-apis-uicontext-uicontext.md#getmeasureutils12) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [MeasureUtils](arkts-apis-uicontext-measureutils.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                             | Mandatory  | Description       |
| ------- | ------------------------------- | ---- | --------- |
| options | [MeasureOptions](#measureoptions) | Yes   | Information about the measured text.|

**Return value**

| Type         | Description      |
| ------------  | --------- |
| [SizeOptions](arkui-ts/ts-types.md#sizeoptions)  | Layout width and height occupied by the text.<br/>**Note:**<br/>The return values of the text width and height are both in px. |

> **NOTE**
>
> Directly using **MeasureText** can lead to the issue of [ambiguous UI context](../../ui/arkts-global-interface.md#ambiguous-ui-context). To avoid this, obtain the [MeasureUtils](arkts-apis-uicontext-measureutils.md) object associated with the current UI context by using the [getMeasureUtils](./arkts-apis-uicontext-uicontext.md#getmeasureutils12) API in [UIContext](arkts-apis-uicontext-uicontext.md).

**Example**

```ts
import { MeasureText } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  textSize: SizeOptions = MeasureText.measureTextSize({
    // You are advised to use this.getUIContext().getMeasureUtils().measureTextSize().
    textContent: "Hello World",
    fontSize: '50px'
  });

  build() {
    Row() {
      Column() {
        Text(`The width of 'Hello World': ${this.textSize.width}`)
        Text(`The height of 'Hello World': ${this.textSize.height}`)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## MeasureOptions

Provides attributes of the measured text.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name          | Type            | Read-Only| Optional| Description                     |
| -------------- | ------------------------- | ---- | ---- | ----------------------------- |
| textContent | string&nbsp;\|&nbsp;[Resource](arkui-ts/ts-types.md#resource)                                                                                             | No  | No| Content of the measured text.                                 |
| constraintWidth<sup>10+</sup> | number \| string \| [Resource](arkui-ts/ts-types.md#resource) | No | Yes | Layout width of the measured text. Value range: [0, +∞).<br>**Note:** <br>The default unit is vp. The value cannot be a percentage. This parameter takes effect only in the **measureTextSize** API. If it is not set, the text width is the maximum width of a single-line layout. If it is set, the set value is used, which also affects the line breaking mode and height calculation result of the text.<br>**Model restriction:** This API can be used only in the stage model. |
| fontSize       | number \| string \| [Resource](arkui-ts/ts-types.md#resource)               | No | Yes   | Font size of the measured text. Value range: [0, +∞). A value beyond the range causes an abnormal calculation result.<br>Default value: **16**<br>**Note:** <br>The value cannot be a percentage.<br>When **fontSize** is of the number type, the fp unit is used since API version 12, and the vp unit is used before API version 12.    |
| fontStyle      | number&nbsp;\|&nbsp;[FontStyle](arkui-ts/ts-appendix-enums.md#fontstyle)                        | No | Yes   | Font style of the measured text.<br>Default value: **FontStyle.Normal**<br>The value range of the number type is [0, 1], with an interval of 1, corresponding to the enumerated values in **FontStyle** in sequence. When the value is out of range, the default value **FontStyle.Normal** is used.            |
| fontWeight     | number&nbsp;\|&nbsp;string&nbsp;\|&nbsp;[FontWeight](arkui-ts/ts-appendix-enums.md#fontweight)  | No | Yes   | Font weight of the measured text. The value range of the number type is [100, 900], with an interval of 100. The default value is **400**. A larger value indicates a heavier font weight. When the value is out of range or not on an interval value, the default value **400** is used. For the string type, only strings of the number type, for example, "400", as well as "bold", "bolder", "lighter", "regular", and "medium" are supported, which correspond to the enumerated values in **FontWeight**.<br>Default value: **FontWeight.Normal**|
| fontFamily     | string&nbsp;\|&nbsp;[Resource](arkui-ts/ts-types.md#resource)                                   | No | Yes   | Font family of the measured text. The default font is **'HarmonyOS Sans'**, and currently only this font is supported. When another font name is set, the default font **'HarmonyOS Sans'** is used.|
| letterSpacing  | number \| string   | No | Yes   | Letter spacing of the measured text.<br>Default value: **0**<br>**Note:** <br>The default unit is vp. The string type supports strings with units, for example, **'10px'** and **'10vp'**. |
| textAlign<sup>10+</sup>  | number&nbsp;\|&nbsp;[TextAlign](arkui-ts/ts-appendix-enums.md#textalign)              | No | Yes   | Horizontal alignment mode of the measured text.<br>Default value: **TextAlign.Start**<br>The value range of the number type is [0, 3], with an interval of 1, corresponding to the enumerated values in **TextAlign** in sequence. When the value is out of range, the default value **TextAlign.Start** is used.<br>**Model restriction:** This API can be used only in the stage model. |
| overflow<sup>10+</sup>  | number \| [TextOverflow](arkui-ts/ts-appendix-enums.md#textoverflow)         | No | Yes   | Truncation mode when the measured text is too long. It takes effect only when used together with **maxLines**.<br>Default value: **1**<br>The value range of the number type is [0, 3], with an interval of 1, corresponding to the enumerated values in **TextOverflow** in sequence. When the value is out of range, the default value **1** is used.<br>**Note:** When set to **TextOverflow.Ellipsis**, it can be used together with **wordBreak.BREAK_ALL** and **maxLines** to truncate English words by letter and display the excess part with an ellipsis.<br>**Model restriction:** This API can be used only in the stage model. |
| maxLines<sup>10+</sup>  | number              | No | Yes   | Maximum number of lines of the measured text. When the actual number of lines exceeds this value, the calculation result of **measureTextSize** is based on the maximum number of lines, and the excess part is not included in the height calculation.<br>Value range: [0, INT32_MAX]. When a negative number or a value beyond the range is passed in, the default value is used.<br>Default value: no limit<br>**Note:** It can be used together with **TextOverflow.Ellipsis** of **overflow** and **wordBreak.BREAK_ALL** to truncate English words by letter and display the excess part with an ellipsis.<br>**Model restriction:** This API can be used only in the stage model. |
| lineHeight<sup>10+</sup>  | number \| string \| [Resource](arkui-ts/ts-types.md#resource)    | No | Yes   | Line height of the measured text, which affects the height calculation result and line spacing of multi-line text. A larger value indicates larger line spacing.<br>Value range: [0, +∞). The string type supports strings with units, for example, **'10px'** and **'10vp'**.<br>Default value: the default line height of the system<br>The default unit is vp.<br>**Model restriction:** This API can be used only in the stage model.|
| baselineOffset<sup>10+</sup>  | number \| string                                                          | No | Yes   | Baseline offset of the measured text.<br>Default value: **0**. Unit: vp. The string type supports strings with units, for example, **'10px'** and **'10vp'**.<br>**Note:** A positive number indicates that the baseline is offset upward, and a negative number indicates that the baseline is offset downward.<br>**Model restriction:** This API can be used only in the stage model. |
| textCase<sup>10+</sup>  | number&nbsp;\|&nbsp;[TextCase](arkui-ts/ts-appendix-enums.md#textcase)                 | No | Yes   | Case of the measured text.<br>Default value: **TextCase.Normal**<br>The value range of the number type is [0, 2], with an interval of 1, corresponding to the enumerated values in **TextCase** in sequence. When the value is out of range, the default value **TextCase.Normal** is used.<br>**Model restriction:** This API can be used only in the stage model. |
| textIndent<sup>11+</sup> | number \| string  | No | Yes  | Indentation of the first line of text. Value range: [0, +∞). When the value is out of range, the default value **0** is used.<br>Default value: **0**.<br>**Note:** <br>The default unit is vp. The string type supports strings with units, for example, **'10px'** and **'10vp'**.<br>**Model restriction:** This API can be used only in the stage model. |
| wordBreak<sup>11+</sup> | [WordBreak](arkui-ts/ts-appendix-enums.md#wordbreak11) | No | Yes   | Word breaking rule. <br>Default value: **WordBreak.BREAK_WORD** <br>**Note:** <br>WordBreak.BREAK_ALL, when used together with **TextOverflow.Ellipsis** of **overflow** and **maxLines**, can truncate English words by letter and display the excess part with an ellipsis.<br>**Model restriction:** This API can be used only in the stage model. |