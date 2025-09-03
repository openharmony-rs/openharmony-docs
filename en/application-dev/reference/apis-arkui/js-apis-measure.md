# @ohos.measure (Text Measurement)

The **measure** module provides APIs for measuring text metrics, such as text height and width.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> 
> This module cannot be used in the file declaration of the [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md). In other words, the APIs of this module can be used only after a component instance is created; they cannot be called in the lifecycle of the UIAbility.
>
> To perform more complex text measurements, you are advised to call the corresponding graphics measurement API, specifically [Paragraph](../apis-arkgraphics2d/js-apis-graphics-text.md#paragraph).
>
> Avoid using [ApplicationContext.setFontSizeScale](../apis-ability-kit/js-apis-inner-application-applicationContext.md#applicationcontextsetfontsizescale13) during text measurement API calls. To ensure timing correctness and the accuracy of measurement results, manually listen for font scale changes.
>
> When calculating clipped text, you are advised to iterate by Unicode units instead of the string length. This approach prevents character truncation that can occur with length-based iteration, which often leads to inaccurate calculation results. A typical example of this issue is the improper truncation of emoji characters.

## Modules to Import

```ts
import { MeasureText } from '@kit.ArkUI';
```

## MeasureText.measureText<sup>(deprecated)</sup>

static measureText(options: MeasureOptions): number

Measures the width of the given text.

> **NOTE**
>
> This API is deprecated since API version 18. You are advised to use [measureText](js-apis-arkui-UIContext.md#measuretext12) instead on the obtained [MeasureUtils](js-apis-arkui-UIContext.md#measureutils12) object.
>
> Since API version 12, you can use the [getMeasureUtils](js-apis-arkui-UIContext.md#getmeasureutils12) API in [UIContext](js-apis-arkui-UIContext.md#uicontext) to obtain the [MeasureUtils](js-apis-arkui-UIContext.md#measureutils12) object associated with the current UI context.

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


**Example**

> **NOTE**
>
> Directly using **MeasureText** can lead to the issue of [ambiguous UI context](../../ui/arkts-global-interface.md#ambiguous-ui-context). To avoid this, obtain the [MeasureUtils](js-apis-arkui-UIContext.md#measureutils12) object associated with the current UI context by using the [getMeasureUtils](./js-apis-arkui-UIContext.md#getmeasureutils12) API in [UIContext](js-apis-arkui-UIContext.md#uicontext).

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
> This API is supported since API version 10 and deprecated since API version 18. You are advised to use [measureTextSize](js-apis-arkui-UIContext.md#measuretextsize12) instead on the obtained [MeasureUtils](js-apis-arkui-UIContext.md#measureutils12) object.
>
> Since API version 12, you can use the [getMeasureUtils](js-apis-arkui-UIContext.md#getmeasureutils12) API in [UIContext](js-apis-arkui-UIContext.md#uicontext) to obtain the [MeasureUtils](js-apis-arkui-UIContext.md#measureutils12) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                             | Mandatory  | Description       |
| ------- | ------------------------------- | ---- | --------- |
| options | [MeasureOptions](#measureoptions) | Yes   | Information about the measured text.|

**Return value**

| Type         | Description      |
| ------------  | --------- |
| [SizeOptions](arkui-ts/ts-types.md#sizeoptions)  | Layout width and height occupied by the text.<br>**NOTE**<br>The return values for text width and height are both in px.|


**Example**

> **NOTE**
>
> Directly using **MeasureText** can lead to the issue of [ambiguous UI context](../../ui/arkts-global-interface.md#ambiguous-ui-context). To avoid this, obtain the [MeasureUtils](js-apis-arkui-UIContext.md#measureutils12) object associated with the current UI context by using the [getMeasureUtils](./js-apis-arkui-UIContext.md#getmeasureutils12) API in [UIContext](js-apis-arkui-UIContext.md#uicontext).

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

| Name          | Type                                                                                               | Mandatory| Description                     |
| -------------- | -------------------------------------------------------------------------------------------------- | ---- | ----------------------------------------------- |
| textContent | string \| [Resource](arkui-ts/ts-types.md#resource)                                                                                             | Yes  | Content of the measured text.                                 |
| constraintWidth<sup>10+</sup> | number \| string \| [Resource](arkui-ts/ts-types.md#resource)   | No  | Layout width of the measured text.<br>**NOTE**<br>The default unit is vp. The value cannot be a percentage. If this parameter is not set, the value of **SizeOption** is the maximum width allowed for the single-line text.                            |
| fontSize       | number \| string \| [Resource](arkui-ts/ts-types.md#resource)               | No  | Font size of the text to be measured. When **fontSize** is of the number type, the unit is vp.<br>Default value: **16**<br>**NOTE**<br>The value cannot be a percentage.<br>Since API version 12, the fp unit is used when **fontSize** is of the number type.   |
| fontStyle      | number \| [FontStyle](arkui-ts/ts-appendix-enums.md#fontstyle)                        | No  | Font style of the measured text.<br>Default value: **FontStyle.Normal**<br>Value range for the number type: [0, 1], with intervals of 1, corresponding to the values in the **FontStyle** enum           |
| fontWeight     | number \| string \| [FontWeight](arkui-ts/ts-appendix-enums.md#fontweight)  | No  | Font width of the measured text. For the number type, the value ranges from 100 to 900, at an interval of 100. A larger value indicates a heavier font weight. The default value is **400**. For the string type, only strings of the number type are supported, for example, **400**, **"bold"**, **"bolder"**, **"lighter"**, **"regular"**, and **"medium"**, which correspond to the enumerated values in **FontWeight**.<br>Default value: **FontWeight.Normal**|
| fontFamily     | string \| [Resource](arkui-ts/ts-types.md#resource)                                   | No  | Font family of the measured text. Default value: **'HarmonyOS Sans'**<br>Only the default font is supported.|
| letterSpacing  | number \| string                                                                         | No  | Letter spacing of the measured text.|
| textAlign<sup>10+</sup>  | number \| [TextAlign](arkui-ts/ts-appendix-enums.md#textalign)              | No  | Horizontal alignment mode of the measured text.<br>Default value: **TextAlign.Start**<br>Value range for the number type: [0, 3], with intervals of 1, corresponding to the values in the **TextAlign** enum|
| overflow<sup>10+</sup>  | number \| [TextOverflow](arkui-ts/ts-appendix-enums.md#textoverflow)         | No  | Display mode when the measured text is too long.<br>Default value: **1**<br>Value range for the number type: [0, 3], with intervals of 1, corresponding to the values in the **TextOverflow** enum|
| maxLines<sup>10+</sup>  | number                                                                                    | No  | Maximum number of lines in the measured text.|
| lineHeight<sup>10+</sup>  | number \| string \| [Resource](arkui-ts/ts-types.md#resource)    | No  | Line height of the measured text.|
| baselineOffset<sup>10+</sup>  | number \| string                                                          | No  | Baseline offset of the measured text.<br>Default value: **0**|
| textCase<sup>10+</sup>  | number \| [TextCase](arkui-ts/ts-appendix-enums.md#textcase)                 | No  | Case of the measured text.<br>Default value: **TextCase.Normal**<br>Value range for the number type: [0, 2], with intervals of 1, corresponding to the values in the **TextCase** enum|
| textIndent<sup>11+</sup> | number \| string  | No | Indentation of the first line.<br>Default value: **0**|
| wordBreak<sup>11+</sup> | [WordBreak](arkui-ts/ts-appendix-enums.md#wordbreak11) | No  | Line break rule.<br>Default value: **WordBreak.BREAK_WORD**<br>**NOTE**<br>When used with **{overflow: TextOverflow.Ellipsis}** and **maxLines**, **WordBreak.BREAK_ALL** can insert line breaks between letters when overflow occurs and display excess content with an ellipsis (...).|
