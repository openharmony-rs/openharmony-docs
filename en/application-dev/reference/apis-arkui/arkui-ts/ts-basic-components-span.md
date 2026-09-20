# Span
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiangyuan6-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=091fe0769a701446e857c7326993467d178f59cc translatedAt=2026-09-03T12:11:22.498Z -->

As a child component of [Text](ts-basic-components-text.md) and [ContainerSpan](ts-basic-components-containerspan.md), it is used to display inline text and supports fine-grained settings of the font, color, size, and other styles of the text. It is suitable for scenarios where different styles are mixed in the same line of text, such as text in different font colors, and adding decorative lines or shadow effects.

>  **NOTE**
>
> - This component is supported since API version 7. New APIs added in later versions are marked with a superscript to indicate their earliest API version.
>
> - Since API version 10, this component supports inheriting the attributes of the parent **Text** component. That is, if a child component does not set an attribute but the parent component does, the child component inherits the attribute set by the parent component. The attributes that can be inherited include only: fontColor, fontSize, fontStyle, fontWeight, decoration, letterSpacing, textCase, fontFamily, and textShadow.
>
> - It supports the [accessibility attribute](ts-universal-attributes-accessibility.md) ([accessibilityText](ts-universal-attributes-accessibility.md#accessibilitytext)), [component identifier](ts-universal-attributes-component-id.md) ([id](ts-universal-attributes-component-id.md#id) and [key](ts-universal-attributes-component-id.md#key12)), and [color inversion disabling](ts-allow-force-dark.md) ([allowForceDark](ts-allow-force-dark.md#allowforcedark)) among the [universal attributes](ts-component-general-attributes.md), but does not support other universal attributes. To set other universal attributes, use [Text](ts-basic-components-text.md), or use [CustomSpan](ts-universal-styled-string.md#customspan) in [styled strings](ts-universal-styled-string.md) to draw them by yourself.
>
> - [accessibilityText](ts-universal-attributes-accessibility.md#accessibilitytext) takes effect only when the [onClick](ts-universal-events-click.md#onclick) event is set for **Span**. The configured text is reflected only in the inline link pop-up recognized by the accessibility service. During direct announcement, the content of **Span** is still announced, and it is not replaced by the text configured in accessibilityText.
>
> - Among the [universal events](ts-component-general-events.md), only the click event [onClick](ts-universal-events-click.md#onclick) and the hover event [onHover](ts-universal-events-hover.md#onhover) are supported.


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

Sets the text decoration line style and its color. If this API is not used, the default decoration line type is TextDecorationType.None (no decoration line), the color is Color.Black, and the style is TextDecorationStyle.SOLID (solid line).

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type     | Mandatory| Description    |
| ------ | -------- | ---- | -------------- |
| value  | [DecorationStyleInterface<sup>12+</sup>](ts-universal-styled-string.md#decorationstyleinterface) | Yes   | Text decoration line style object.<br>**Note:** <br>The style parameter does not support the card capability. |

>  **NOTE**
>
>  When the bottom contour of a character intersects with the decoration, underline avoidance is triggered, commonly affecting characters like "g", "j", "y", "q", and "p."
>
>  If the decoration color is set to **Color.Transparent**, it inherits the text color of the first character in each line. If the decoration color is set to **"#00FFFFFF"**, the line becomes fully transparent.

### letterSpacing

letterSpacing(value: number | ResourceStr)

Sets the text character spacing. If the value is less than 0, the characters gather and overlap. If the value is greater than 0, the character spacing increases as the value increases, resulting in a sparse distribution. It is suitable for scenarios such as title layout and label text where the compactness or sparseness of characters needs to be adjusted. The string type supports the string form of a number value and can carry a unit, for example, "10" and "10fp".

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type    | Mandatory|  Description  |
| ------ | ------- | ---- | -------------- |
| value  | number&nbsp;\|&nbsp;[ResourceStr](ts-types.md#resourcestr) | Yes   | Text character spacing.<br>Unit: [fp](ts-pixel-units.md#basic-pixel-units) <br>Since API version 20, the [Resource](ts-types.md#resource) type is supported.|

### textCase

textCase(value: TextCase)

Sets the text case. If this API is not used, the default text case is TextCase.Normal.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description  |
| ------ | ------- | ---- | ------- |
| value  | [TextCase](ts-appendix-enums.md#textcase) | Yes   | Text case. |

### fontColor

fontColor(value: ResourceColor)

Sets the font color. If this API is not used, the default font color is '#FF182431' (dark gray), and on Wearable devices, the default is '#C5FFFFFF' (white with an opacity of about 77%).

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                      | Mandatory| Description      |
| ------ | ------------------------------------------ | ---- | ---------- |
| value  | [ResourceColor](ts-types.md#resourcecolor) | Yes   | Font color. |

### fontSize

fontSize(value: number | string | Resource)

Sets the font size. If this API is not used, the default font size is 16fp, and on Wearable devices, the default is 15fp.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | number&nbsp;\|&nbsp;string&nbsp;\|&nbsp;[Resource](ts-types.md#resource) | Yes   | Font size. When fontSize is of the number type, the unit fp is used. The string type supports the string form of a number type value, which can carry a unit, for example, "10" or "10fp". Percentage strings are not supported.<br>Since API version 20, the [Resource](ts-types.md#resource) type is supported.|

### fontStyle

fontStyle(value: FontStyle)

Sets the font style. If this API is not used, the default font style is FontStyle.Normal.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                       | Mandatory| Description                                   |
| ------ | ------------------------------------------- | ---- | --------------------------------------- |
| value  | [FontStyle](ts-appendix-enums.md#fontstyle) | Yes   | Font style. |

### fontWeight

fontWeight(value: number | FontWeight | ResourceStr)

Sets the font weight of the text. If the value is too large, the text may be clipped depending on the font. If this API is not used, the default font weight is FontWeight.Normal (normal weight, corresponding to the value 400).

> **NOTE**
>
> When the [fontVariations attribute](#fontvariations) is set at the same time, the fontVariations attribute takes precedence.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | number&nbsp;\|&nbsp;[FontWeight](ts-appendix-enums.md#fontweight)&nbsp;\|&nbsp;[ResourceStr](ts-types.md#resourcestr) | Yes   | Font weight of the text.<br>For the number type, the value ranges from [100,&nbsp;900], at an interval of 100. A larger value indicates a heavier font. For the string type, only the string form of the number type value is supported, for example, "400", as well as "bold", "bolder", "lighter", "regular", and "medium", which correspond to the respective enum values in FontWeight. If the value is set too large, the font may be truncated under different fonts. If a value outside the value range or not meeting the interval requirement is passed in, the default value is used.<br>Since API version 20, the [Resource](ts-types.md#resource) type is supported.|

### fontWeight<sup>24+</sup>

fontWeight(weight: number | FontWeight | ResourceStr, fontWeightConfigs?: FontWeightConfigs)

Sets the font weight of the text. If this API is not used, the default font weight is FontWeight.Normal (normal weight, corresponding to the value 400).

> **NOTE**
>
> When the fontVariations attribute is set at the same time, the fontVariations attribute takes precedence.

**Widget capability**: This API can be used in ArkTS widgets since API version 24.

**Atomic service API**: This API can be used in atomic services since API version 24.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                                         | Mandatory | Description                                                         |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| weight  | number&nbsp;\|&nbsp;[FontWeight](ts-appendix-enums.md#fontweight)&nbsp;\|&nbsp;[ResourceStr](ts-types.md#resourcestr) | Yes   | Font weight of the text.<br>For the number type, the value ranges from 100 to 900, with an interval of 100. A larger value indicates a heavier font. For the string type, only the string form of the number type value is supported, for example, "400", as well as "bold", "bolder", "lighter", "regular", and "medium", which correspond to the respective enum values in FontWeight. If the value is set too large, the text may be truncated under different fonts.<br>If the value passed in is out of the value range, the default value is used. If the value passed in does not meet the interval requirement, the passed-in value is used when enableVariableFontWeight of fontWeightConfigs is set to true; otherwise, the default value is used.|
| fontWeightConfigs  | [FontWeightConfigs](ts-text-common.md#fontweightconfigs24) | No   | Font weight configuration object, used to configure options such as the variable font weight. The default value inherits [FontWeightConfigs](ts-text-common.md#fontweightconfigs24). |

### fontFamily

fontFamily(value: string | Resource)

Sets the font list. If this API is not used, the default font is 'HarmonyOS Sans'.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                | Mandatory| Description                                                        |
| ------ | ---------------------------------------------------- | ---- | ------------------------------------------------------------ |
| value  | string&nbsp;\|&nbsp;[Resource](ts-types.md#resource) | Yes   | Font list.<br>When multiple fonts are used, separate them with commas ','. The priority of the fonts takes effect in order. For example: 'Arial,HarmonyOS Sans'. |

> **NOTE**
>
> You can use [loadFontSync](../../apis-arkgraphics2d/js-apis-graphics-text.md#loadfontsync) to register custom fonts.

### lineHeight<sup>10+</sup>

lineHeight(value: Length)

Sets the line height for the text. If this API is not used, the line height is automatically calculated by the system based on the font size.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description |
| ------ | ------ | ---- | ---- |
| value  | [Length](ts-types.md#length) | Yes   | Text line height. <br> The unit is fp when the value is of the number type. When the value is of the string type, the string form of a number type value is supported, and a unit can be attached, for example, "10" and "10fp". Percentage strings are not supported. |

### font<sup>10+</sup>

font(value: Font)

Sets the text style, covering the font size, font width, Font family, and font style.

> **NOTE**
>
> If fontWeight is set too large, the text may be truncated under different fonts.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                     | Mandatory | Description       |
| ------ | ------------------------ | ---- | ---------- |
| value  | [Font](ts-types.md#font) | Yes   | Text style, including the font size, font weight, font family, and font style. |

### font<sup>24+</sup>

font(value: Font, fontConfigs?: FontConfigs)

Sets the text style.

**Atomic service API**: This API can be used in atomic services since API version 24.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ------------------------ | ---- | ---------- |
| value  | [Font](ts-types.md#font) | Yes | Text style, including the font size, font weight, font family, and font style. |
| fontConfigs  | [FontConfigs](ts-text-common.md#fontconfigs24) | No | Font configuration, used to customize the font rendering behavior (for example, configuring variable font attributes). Pass this parameter when advanced font configuration is required. If it is not passed, the default configuration of [FontConfigs](ts-text-common.md#fontconfigs24) is inherited. |

### textShadow<sup>11+</sup>

textShadow(value: ShadowOptions | Array&lt;ShadowOptions&gt;)

Sets the text shadow effect. This API supports an array as the input parameter to implement multiple text shadows. The **fill** field and the smart color picking mode are not supported.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | ----- | ---- | --- |
| value  | [ShadowOptions](ts-universal-attributes-image-effect.md#shadowoptions)&nbsp;\|&nbsp;&nbsp;Array&lt;[ShadowOptions](ts-universal-attributes-image-effect.md#shadowoptions)> | Yes   | Text shadow effect. You can set parameters such as the blur radius, color, and offset (offsetX/offsetY) of the shadow, and multiple shadows are supported in array form. |

### fontVariations

fontVariations(fontVariations: Array&lt;FontVariation&gt;)

Sets the attributes of a variable font. This is applicable to scenarios where variable dimension parameters such as font weight and width need to be dynamically adjusted.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.1.0.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters** 

| Name | Type                                          | Mandatory | Description                                          |
| ------ | --------------------------------------------- | ---- | --------------------------------------------- |
| fontVariations | Array&lt;[FontVariation](../../apis-arkgraphics2d/js-apis-graphics-text.md#fontvariation)&gt; | Yes | Array of variable font attributes. Each array element contains two fields: axis (attribute axis name) and value (attribute value). The fontVariations attribute has a higher priority than [fontWeight](#fontweight24). |

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

Sets the text background style. When used as a child component of [ContainerSpan](ts-basic-components-containerspan.md), this attribute value can be inherited, and the component's own setting takes precedence. If this API is not used, the default background color is Color.Transparent and the corner radius is 0.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type | Mandatory| Description|
| ----- | ---- | ---- | ---- |
| style  | [TextBackgroundStyle](#textbackgroundstyle11) | Yes   | Text background style. |

**Return value**

| Type                                      | Description     |
| ---------------------------------------- | ------- |
| T | Attribute object of the current Span. |

### baselineOffset<sup>12+</sup>

baselineOffset(value: LengthMetrics): T

Sets the baseline offset of the Span. This is applicable to scenarios such as superscript and subscript layout and fine-tuning alignment of mixed-font-size text. This attribute coexists with the baselineOffset of the parent component. If this API is not used, the default offset is 0.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description |
| ----- | ---- | ---- | ---- |
| value  | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | Yes   | Sets the baseline offset of the Span. If this value is set to a percentage, the default value is used.<br>A positive value shifts the content upward, and a negative value shifts it downward.<br>In ImageSpan, when this value is set to a non-zero value, [verticalAlign](ts-basic-components-imagespan.md#verticalalign) is fixed to ImageSpanAlignment.BASELINE. When this value is set to 0, to make the baseline alignment policy take effect, you must also set [verticalAlign](ts-basic-components-imagespan.md#verticalalign) to ImageSpanAlignment.BASELINE. |

**Return value**

| Type                                      | Description     |
| ---------------------------------------- | ------- |
| T | Attribute object of the current Span, used for chained calls. |

## TextBackgroundStyle<sup>11+</sup>

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type    | Read-Only| Optional| Description        |
| ------ | ------- | ---- | ---- | ------------ |
| color  | [ResourceColor](ts-types.md#resourcecolor)                                  | No   | Yes | Text background color. Transparent by default, meaning no background color. |
| radius | [Dimension](ts-types.md#dimension10) \| [BorderRadiuses](./ts-types.md#borderradiuses9) | No   | Yes | Corner radius of the text background. No rounded corners by default. |

## Example
### Example 1: Setting the Text Style

This example demonstrates how to apply different text styles and configure click events for the Span.

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

      // Text font configuration settings. Starting from API version 24, the fontConfigs attribute is supported.
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

      // Text font weight configuration settings. Starting from API version 24, the fontWeightConfigs attribute is supported.
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

### Example 5 (Set the Variable Font Attribute)

This example sets the variable font attribute through the [fontVariations](#fontvariations) attribute.

Since API version 26.0.0, the [fontVariations](#fontvariations) API is added.

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
          // wght represents the font weight attribute of a variable font.
          .fontVariations([{ axis: 'wght', value: this.weightValue }])
      }

      Button('Font weight: ' + this.weightValue)
        .margin(10)
        .onClick(() => {
          this.weightValue += 100;
        })
    }.width('100%')
  }
}
```

![SpanFontVariations](figures/FontVariations.gif)
