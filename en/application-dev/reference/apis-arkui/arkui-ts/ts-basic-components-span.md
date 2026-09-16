# Span
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiangyuan6-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

As a child of the [Text](ts-basic-components-text.md) and [ContainerSpan](ts-basic-components-containerspan.md) components, the **Span** component is used to display inline text, which supports fine-grained settings of the font, color, and size of the text. It is applicable to scenarios where different styles are displayed in the same line of text, such as text with different font colors, text with decorative lines, or text with shadow effects.

>  **NOTE**
>
> - This component is supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - This component is supported since API version 10. It can inherit attribute settings from its parent component **Text**. This means that, if an attribute is not set in this component, it takes the value (if any) of the attribute from its parent component. Only the following attributes can be inherited: **fontColor**, **fontSize**, **fontStyle**, **fontWeight**, **decoration**, **letterSpacing**, **textCase**, **fontFamily**, and **textShadow**.
>
> - This component supports only the [accessibility attribute](ts-universal-attributes-accessibility.md) ([accessibilityText](ts-universal-attributes-accessibility.md#accessibilitytext)), [component ID](ts-universal-attributes-component-id.md) ([id](ts-universal-attributes-component-id.md#id), [key](ts-universal-attributes-component-id.md#key12)), and [color inversion disabling attribute](ts-allow-force-dark.md) ([allowForceDark](ts-allow-force-dark.md#allowforcedark)) in [universal attributes](ts-component-general-attributes.md). To set other universal attributes, use [Text](ts-basic-components-text.md) for configuration or use [CustomSpan](ts-universal-styled-string.md#customspan) in the [styled string](ts-universal-styled-string.md) for custom drawing.
>
> - [accessibilityText](ts-universal-attributes-accessibility.md#accessibilitytext) takes effect only when the [onClick](ts-universal-events-click.md#onclick) event is set for the span. The configured text is displayed only in the embedded link pop-up window detected by the accessibility service. During direct reading, the span content is still read and is not replaced with the text configured by **accessibilityText**.
>
> - Among [universal events](ts-component-general-events.md), only [onClick](ts-universal-events-click.md#onclick) click events and [onHover](ts-universal-events-hover.md#onhover) hover events are supported.


## Child Components

Not supported


## APIs

Span(value: string | Resource)

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | string \| [Resource](ts-types.md#resource) | Yes| Plain text.|


## Attributes

Inherited from [BaseSpan](#basespan).

### decoration

decoration(value: DecorationStyleInterface)

Style and color of the text decorative line. If this API is not used, the default decorative line type is **TextDecorationType.None** (no decorative line), the color is **Color.Black** (black), and the style is **TextDecorationStyle.SOLID** (solid line).

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type     | Mandatory| Description    |
| ------ | -------- | ---- | -------------- |
| value  | [DecorationStyleInterface<sup>12+</sup>](ts-universal-styled-string.md#decorationstyleinterface) | Yes  | Style of the text decorative line.<br>**NOTE**<br>The **style** parameter cannot be used in widgets.|

>  **NOTE**
>
>  When the bottom contour of a character intersects with the decoration, underline avoidance is triggered, commonly affecting characters like "g", "j", "y", "q", and "p."
>
>  If the decoration color is set to **Color.Transparent**, it inherits the text color of the first character in each line. If the decoration color is set to **"#00FFFFFF"**, the line becomes fully transparent.

### letterSpacing

letterSpacing(value: number | ResourceStr)

Sets the letter spacing. A negative value tightens the spacing; a positive value loosens the spacing, and the letters are spread farther apart with the value. This API is applicable to scenarios where the character compactness or sparseness needs to be adjusted, such as title typesetting and label text. For the string type, numeric string values with optional units, for example, **"10"** or **"10fp"**, are supported.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type    | Mandatory|  Description  |
| ------ | ------- | ---- | -------------- |
| value  | number&nbsp;\|&nbsp;[ResourceStr](ts-types.md#resourcestr) | Yes  | Letter spacing.<br>Unit: [fp](ts-pixel-units.md#basic-pixel-units)<br>The [Resource](ts-types.md#resource) type is supported since API version 20.|

### textCase

textCase(value: TextCase)

Sets the text case. If this API is not used, the default text case is **TextCase.Normal** (normal case).

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description  |
| ------ | ------- | ---- | ------- |
| value  | [TextCase](ts-appendix-enums.md#textcase) | Yes  | Text case.|

### fontColor

fontColor(value: ResourceColor)

Sets the font color. If this API is not used, the default text color is **'#FF182431'** (dark gray). On wearables, the default text color is **'#C5FFFFFF'** (white, with opacity of about 77%).

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                      | Mandatory| Description      |
| ------ | ------------------------------------------ | ---- | ---------- |
| value  | [ResourceColor](ts-types.md#resourcecolor) | Yes  | Font color.|

### fontSize

fontSize(value: number | string | Resource)

Sets the font size. If this API is not used, the default font size is 16 fp. On wearables, the default font size is 15 fp.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | number&nbsp;\|&nbsp;string&nbsp;\|&nbsp;[Resource](ts-types.md#resource) | Yes  | Font size. If **fontSize** is of the number type, the unit fp is used. For the string type, numeric string values with optional units, for example, **"10"** or **"10fp"**, are supported. Percentage values are not supported.<br>The [Resource](ts-types.md#resource) type is supported since API version 20.|

### fontStyle

fontStyle(value: FontStyle)

Sets the font style. If this API is not used, the default font style is **FontStyle.Normal** (normal style).

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                       | Mandatory| Description                                   |
| ------ | ------------------------------------------- | ---- | --------------------------------------- |
| value  | [FontStyle](ts-appendix-enums.md#fontstyle) | Yes  | Font style.|

### fontWeight

fontWeight(value: number | FontWeight | ResourceStr)

Sets the font weight. If the value is too large, the text may be clipped depending on the font. If this API is not used, the default font weight is **FontWeight.Normal** (normal weight, corresponding to the value **400**).

> **NOTE**
>
> If both this attribute and [fontVariations](#fontvariations) are set, **fontVariations** takes precedence.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | number&nbsp;\|&nbsp;[FontWeight](ts-appendix-enums.md#fontweight)&nbsp;\|&nbsp;[ResourceStr](ts-types.md#resourcestr) | Yes  | Font weight of the text.<br>For the number type, the value ranges from 100 to 900, at an interval of 100. A larger value indicates a heavier font weight. For the string type, only strings of the number type are supported, for example, **"400"**, and **"bold"**, **"bolder"**, **"lighter"**, **"regular"**, and **"medium"**, which correspond to the enumerated values in **FontWeight**. If the value is too large, truncation may occur in different fonts. If the input value exceeds the value range or does not meet the interval requirements, the default value is used.<br>The [Resource](ts-types.md#resource) type is supported since API version 20.|

### fontWeight<sup>24+</sup>

fontWeight(weight: number | FontWeight | ResourceStr, fontWeightConfigs?: FontWeightConfigs)

Font weight of the text. If this API is not used, the default font weight is **FontWeight.Normal** (normal weight, corresponding to the value **400**).

> **NOTE**
>
> If both this attribute and **fontVariations** are set, **fontVariations** takes precedence.

**Widget capability:** This API can be used in ArkTS widgets since API version 24.

**Atomic service API:** This API can be used in atomic services since API version 24.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| weight  | number&nbsp;\|&nbsp;[FontWeight](ts-appendix-enums.md#fontweight)&nbsp;\|&nbsp;[ResourceStr](ts-types.md#resourcestr) | Yes  | Font weight of the text.<br>For the number type, the value ranges from 100 to 900, at an interval of 100. A larger value indicates a heavier font weight. For the string type, only strings of the number type are supported, for example, **"400"**, and **"bold"**, **"bolder"**, **"lighter"**, **"regular"**, and **"medium"**, which correspond to the enumerated values in **FontWeight**. If the value is too large, truncation may occur in different fonts.<br>If the input value exceeds the value range, the default value is used. If the input value does not meet the interval requirements, and **enableVariableFontWeight** of **fontWeightConfigs** is set to **true**, the input value is used. If **enableVariableFontWeight** is set to **false**, the default value is used.|
| fontWeightConfigs  | [FontWeightConfigs](ts-text-common.md#fontweightconfigs24) | No  | Font weight configuration object, which is used to configure options such as variable font weight. The default value is inherited from [FontWeightConfigs](ts-text-common.md#fontweightconfigs24).|

### fontFamily

fontFamily(value: string | Resource)

Sets the font family. If this API is not called, the default font is **'HarmonyOS Sans'**.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                | Mandatory| Description                                                        |
| ------ | ---------------------------------------------------- | ---- | ------------------------------------------------------------ |
| value  | string&nbsp;\|&nbsp;[Resource](ts-types.md#resource) | Yes  | Font family.<br>To specify multiple fonts, separate them with commas (,), and fonts are applied in priority order. Example: **'Arial, HarmonyOS Sans'**.|

> **NOTE**
>
> You can use [loadFontSync](../../apis-arkgraphics2d/js-apis-graphics-text.md#loadfontsync) to register custom fonts.

### lineHeight<sup>10+</sup>

lineHeight(value: Length)

Sets the line height for the text. If this API is not used, the system automatically calculates the line height based on the font size by default.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description |
| ------ | ------ | ---- | ---- |
| value  | [Length](ts-types.md#length) | Yes  | Line height of the text.<br> If the value is of the number type, the unit is fp. For the string type, numeric string values with optional units, for example, **"10"** or **"10fp"**, are supported. Percentage values are not supported.|

### font<sup>10+</sup>

font(value: Font)

Sets the text style, covering the font size, font weight, font family, and font style.

> **NOTE**
>
> If the value of **fontWeight** is too large, truncation may occur in different fonts.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                    | Mandatory| Description      |
| ------ | ------------------------ | ---- | ---------- |
| value  | [Font](ts-types.md#font) | Yes  | Text style, including the font size, font weight, font family, and font style.|

### font<sup>24+</sup>

font(value: Font, fontConfigs?: FontConfigs)

Sets the text style.

**Atomic service API:** This API can be used in atomic services since API version 24.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                    | Mandatory| Description      |
| ------ | ------------------------ | ---- | ---------- |
| value  | [Font](ts-types.md#font) | Yes  | Text style, including the font size, font weight, font family, and font style.|
| fontConfigs  | [FontConfigs](ts-text-common.md#fontconfigs24)| No  | Font configurations, which are used to customize font rendering behavior (for example, configuring variable font attributes). This parameter is passed when advanced font configurations are required. If this parameter is not passed, the default configurations of [FontConfigs](ts-text-common.md#fontconfigs24) are inherited.|

### textShadow<sup>11+</sup>

textShadow(value: ShadowOptions | Array&lt;ShadowOptions&gt;)

Text shadow. It supports input parameters in an array to implement multiple text shadows. This API does not work with the **fill** attribute or coloring strategy.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | ----- | ---- | --- |
| value  | [ShadowOptions](ts-universal-attributes-image-effect.md#shadowoptions)&nbsp;\|&nbsp;&nbsp;Array&lt;[ShadowOptions](ts-universal-attributes-image-effect.md#shadowoptions)> | Yes  | Text shadow. You can set parameters such as the blur radius (**radius**), color (**color**), and offset distance (**offsetX**/**offsetY**) for the shadow. Multiple shadows can be implemented using arrays.|

### fontVariations

fontVariations(fontVariations: Array&lt;FontVariation&gt;)

Sets the attributes of font variations. This API is applicable to scenarios where variable dimension parameters such as the font weight and width need to be dynamically adjusted.

**Since:** 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Widget capability**: This API can be used in ArkTS widgets since API version 26.1.0.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                         | Mandatory| Description                                         |
| ------ | --------------------------------------------- | ---- | --------------------------------------------- |
| fontVariations | Array&lt;[FontVariation](../../apis-arkgraphics2d/js-apis-graphics-text.md#fontvariation)&gt; | Yes| Array of font variations, where each element in the array contains two fields: **axis** (attribute axis name) and **value** (attribute value). The **fontVariations** attribute takes precedence over [fontWeight](#fontweight24).|

## Events

Among universal events, only [onClick](ts-universal-events-click.md#onclick) click events and [onHover](ts-universal-events-hover.md#onhover) hover events are supported.

>  **NOTE**
>
>  As the **Span** component does not include size information, the **target** attribute of the **ClickEvent** object returned by the click event is invalid.

## BaseSpan

Defines the base class **BaseSpan**, including the universal attributes of the **Span** component.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Atomic service API**: This API can be used in atomic services since API version 12.

### textBackgroundStyle<sup>11+</sup>

textBackgroundStyle(style: TextBackgroundStyle): T

Sets the text background style. As a child of the [ContainerSpan](ts-basic-components-containerspan.md) component, the **Span** component can inherit the value of this attribute and preferentially use its own settings. If this API is not used, the default background color is **Color.Transparent** (transparent) and the radius of rounded corners is 0.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type | Mandatory| Description|
| ----- | ---- | ---- | ---- |
| style  | [TextBackgroundStyle](#textbackgroundstyle11) | Yes  | Text background style.|

**Return value**

| Type                                      | Description     |
| ---------------------------------------- | ------- |
| T | Attribute object of the current span.|

### baselineOffset<sup>12+</sup>

baselineOffset(value: LengthMetrics): T

Sets the offset of the span baseline. This API applies to scenarios such as subscript typesetting and fine-tuning of text alignment with mixed font sizes. This attribute coexists with the **baselineOffset** attribute of the parent component. If this API is not used, the default offset is 0.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description |
| ----- | ---- | ---- | ---- |
| value  | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | Yes  | Offset of the baseline. If the value specified is a percentage, the default value is used.<br>A positive value moves the content upwards, while a negative value moves it downwards.<br>In the **ImageSpan**, when this parameter is set to a non-zero value, the [verticalAlign](ts-basic-components-imagespan.md#verticalalign) is fixed to **ImageSpanAlignment.BASELINE**; when this parameter is set to **0**, [verticalAlign](ts-basic-components-imagespan.md#verticalalign) must be set to **ImageSpanAlignment.BASELINE** for the baseline alignment strategy to take effect.|

**Return value**

| Type                                      | Description     |
| ---------------------------------------- | ------- |
| T | Attribute object of the current span, which is used for chain calling.|

## TextBackgroundStyle<sup>11+</sup>

Defines the background style of a span.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type    | Read-Only| Optional| Description        |
| ------ | ------- | ---- | ---- | ------------ |
| color  | [ResourceColor](ts-types.md#resourcecolor)                                  | No  | Yes| Text background color. By default, the background color is transparent.|
| radius | [Dimension](ts-types.md#dimension10) \| [BorderRadiuses](./ts-types.md#borderradiuses9) | No  | Yes| Rounded corner radius of the text background. By default, there is no rounded corner.|

## Example
### Example 1: Setting the Text Style

This example demonstrates how to apply different text styles and configure click events for the **Span** component.

```ts
// xxx.ets
@Entry
@Component
struct SpanExample {
  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Start }) {
      Text('Basic Usage').fontSize(9).fontColor(0xCCCCCC)
      Text() {
        Span('In Line')
        Span(' Component')
        Span(' !')
      }

      Text() {
        Span('This is the Span component').fontSize(12).textCase(TextCase.Normal)
          .decoration({ type: TextDecorationType.None, color: Color.Red })
          .fontFamily('HarmonyOS Sans')
      }.margin({ top: 12 })

      // Add a line under the text.
      Text('Text Decoration').fontSize(9).fontColor(0xCCCCCC).margin({ top: 12 })
      Text() {
        Span('I am Underline-WAVY-span')
          .decoration({ type: TextDecorationType.Underline, color: Color.Red, style: TextDecorationStyle.WAVY })
          .fontSize(12)
      }

      Text() {
        Span('I am LineThrough-DOTTED-span')
          .decoration({ type: TextDecorationType.LineThrough, color: Color.Red, style: TextDecorationStyle.DOTTED })
          .fontSize(12)
      }

      Text() {
        Span('I am Overline-DASHED-span')
          .decoration({ type: TextDecorationType.Overline, color: Color.Red, style: TextDecorationStyle.DASHED })
          .fontSize(12)
      }

      // Set the letter spacing.
      Text('LetterSpacing').fontSize(9).fontColor(0xCCCCCC).margin({ top: 12 })
      Text() {
        Span('span letter spacing')
          .letterSpacing(0)
          .fontSize(12)
      }

      Text() {
        Span('span letter spacing')
          .letterSpacing(-2)
          .fontSize(12)
      }

      Text() {
        Span('span letter spacing')
          .letterSpacing(3)
          .fontSize(12)
      }

      // Set the text case.
      Text('Text Case').fontSize(9).fontColor(0xCCCCCC).margin({ top: 12 })
      Text() {
        Span('I am Lower-span').fontSize(12)
          .textCase(TextCase.LowerCase)
          .decoration({ type: TextDecorationType.None })
      }

      Text() {
        Span('I am Upper-span').fontSize(12)
          .textCase(TextCase.UpperCase)
          .decoration({ type: TextDecorationType.None })
      }

      // Set the text font style.
      Text('FontStyle').fontSize(9).fontColor(0xCCCCCC).margin({ top: 12 })
      Text() {
        Span('I am FontStyle-Normal').fontSize(12)
          .fontStyle(FontStyle.Normal)
      }

      Text() {
        Span('I am FontStyle-Italic').fontSize(12)
          .fontStyle(FontStyle.Italic)
      }

      // Set the text font weight.
      Text('FontWeight').fontSize(9).fontColor(0xCCCCCC).margin({ top: 12 })
      Text() {
        Span('I am FontWeight-Lighter').fontSize(12)
          .fontWeight(FontWeight.Lighter)
      }

      Text() {
        Span('I am FontWeight-Bold').fontSize(12)
          .fontWeight(FontWeight.Bold)
      }

      // Set the text line height.
      Text('LineHeight').fontSize(9).fontColor(0xCCCCCC).margin({ top: 12 })
      Text() {
        Span('I am lineHeight default\n').fontSize(12)
          .fontWeight(FontWeight.Lighter)
        Span('I am lineHeight 30').fontSize(12)
          .lineHeight(30)
      }
      .backgroundColor(Color.Gray)

      // Set the text style.
      Text('Font').fontSize(9).fontColor(0xCCCCCC).margin({ top: 12 })
      Text() {
        Span('span font 12 Bolder Italic')
          .font({
            size: 12,
            weight: FontWeight.Bolder,
            style: FontStyle.Italic,
            family: "HarmonyOS Sans"
          })
      }

      // Sets text font configurations. The fontConfigs attribute is supported since API version 24.
      Text('Font with FontConfigs').fontSize(9).fontColor(0xCCCCCC).margin({ top: 12 })
      Text() {
        Span('span font with configs')
          .font({
            size: 14,
            weight: 550,
            style: FontStyle.Normal,
            family: "HarmonyOS Sans"
          }, {
            fontWeightConfigs: {
              enableVariableFontWeight: true
            }
          })
      }

      // Sets text font weight configurations. The fontWeightConfigs attribute is supported since API version 24.
      Text('FontWeight with FontWeightConfigs').fontSize(9).fontColor(0xCCCCCC).margin({ top: 12 })
      Text() {
        Span('span fontWeight 850 with configs')
          .fontWeight(850, {
            enableVariableFontWeight: true,
            enableDeviceFontWeightCategory: false
          })
      }
      Text() {
        Span('span fontWeight 600 with configs')
          .fontWeight(600, {
            enableVariableFontWeight: false,
            enableDeviceFontWeightCategory: true
          })
      }

      // Set the click event.
      Text('span click event').fontSize(9).fontColor(0xCCCCCC).margin({ top: 12 })
      Text() {
        Span('Span default ').fontSize(12)
        Span('Span click')
          .onClick((event) => {
            console.info("span onClick")
          })
      }
    }.width('100%').padding({ left: 35, right: 35, top: 35 })
  }
}
```

![Span](figures/span.png)

### Example 2: Setting the Text Shadow

In API version 11 and later versions, the [textShadow](#textshadow11) attribute is used to set the text shadow.

``` ts
// xxx.ets
@Entry
@Component
struct SpanExample {
  @State textShadows: ShadowOptions | Array<ShadowOptions> = [{
    radius: 10,
    color: Color.Red,
    offsetX: 10,
    offsetY: 0
  }, {
    radius: 10,
    color: Color.Orange,
    offsetX: 20,
    offsetY: 0
  },
    {
      radius: 10,
      color: Color.Yellow,
      offsetX: 30,
      offsetY: 0
    }, {
      radius: 10,
      color: Color.Green,
      offsetX: 40,
      offsetY: 0
    },
    {
      radius: 10,
      color: Color.Blue,
      offsetX: 100,
      offsetY: 0
    }]

  build() {
    Column({ space: 8 }) {
      Text() {
        Span('123456789').fontSize(50).textShadow(this.textShadows).fontColor(Color.Pink)
      }

      Text() {
        Span('123456789') // span can inherit text shadow & font size from outer text
      }.fontSize(50).textShadow(this.textShadows).fontColor(Color.Pink)
    }
  }
}
```
![TextshadowExample](figures/text_span_textshadow.png)

### Example 3: Setting the Background Style

This example demonstrates how to set the background style for text using the [textBackgroundStyle](#textbackgroundstyle11) attribute, available since API version 11.

``` ts
// xxx.ets
@Component
@Entry
struct SpanExample {
  build() {
    Column() {
      Text() {
        Span('   Hello World !   ')
          .fontSize('20fp')
          .textBackgroundStyle({ color: '#7F007DFF', radius: '5vp' })
          .fontColor(Color.White)
      }
    }.width('100%').margin({ bottom: '5vp' }).alignItems(HorizontalAlign.Center)
  }
}
```
![TextBackgroundStyleExample](figures/span_textbackgroundstyle.png)

### Example 4: Setting the Text Baseline Offset

In API version 12 and later versions, this example demonstrates how to set different baseline offsets for text through the [baselineOffset](#baselineoffset12) attribute.

```ts
// xxx.ets
import { LengthUnit, LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct SpanExample {
  build() {
    Row() {
      Column() {
        Text() {
          Span('SpanOne')
            .fontSize(10)
            .baselineOffset(new LengthMetrics(20, LengthUnit.VP))
          Span('SpanTwo')
            .fontSize(10)
            .baselineOffset(new LengthMetrics(0, LengthUnit.VP))
          // Replace $r('app.media.sky') with the image resource file you use.
          ImageSpan($r("app.media.sky"))
            .width('80px')
            .baselineOffset(new LengthMetrics(-20, LengthUnit.VP))
        }
        .backgroundColor('#7F007DFF')
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

![SpanBaselineOffset](figures/SpanBaselineOffset.png)

### Example 5: Setting Text Font Variations

This example demonstrates how to set text font variations using [fontVariations](#fontvariations).

The [fontVariations](#fontvariations) API is added since API version 26.0.0.

```ts
// xxx.ets
@Entry
@Component
struct SpanExample {
  @State weightValue: number = 400;

  build() {
    Column() {
      Text() {
        Span('Hello World !')
          // wght indicates the weight of the variable font.
          .fontVariations([{ axis: 'wght', value: this.weightValue }])
      }

      Button('Weight: ' + this.weightValue)
        .margin(10)
        .onClick(() => {
          this.weightValue += 100;
        })
    }.width('100%')
  }
}
```

![SpanFontVariations](figures/FontVariations.gif)
