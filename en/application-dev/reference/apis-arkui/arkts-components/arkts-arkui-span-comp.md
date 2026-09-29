# Span

As a child component of [Text](arkts-arkui-text-comp.md) and [ContainerSpan](arkts-arkui-containerspan-comp-attribute.md#containerspanattribute), it is used to display inline text and supports fine-grained settings of the font, color, size, and other styles of the text. It is suitable for scenarios where different styles are mixed in the same line of text, such as text in different font colors, and adding decorative lines or shadow effects.

> **NOTE:** 
> 
> - This component is supported since API version 7. New APIs added in later versions are marked with a superscript to indicate their
> 
> - Since API version 10, this component supports inheriting the attributes of the parent **Text** component. That is, if a child component does not set an attribute but the parent component does, the child component inherits the attribute set by the parent component. The attributes that can be inherited include only: fontColor, fontSize,fontStyle, fontWeight, decoration, letterSpacing, textCase, fontFamily, and textShadow.
> 
> - It supports the [accessibility attribute](arkts-arkui-common-comp.md) ([accessibilityText](arkts-arkui-common-comp-commonmethod-c.md#accessibilitytext)), [component identifier](arkts-arkui-common-comp.md) ([id](arkts-arkui-common-comp-commonmethod-c.md#id) and [key](arkts-arkui-common-comp-commonmethod-c.md#key)), and [color inversion disabling](arkts-arkui-common-comp.md) ([allowForceDark](arkts-arkui-common-comp-commonmethod-c.md#allowforcedark)) among the [universal attributes](arkts-arkui-common-comp.md), but does not support other universal attributes. To set other universal attributes, use [Text](arkts-arkui-text-comp.md), or use [CustomSpan](../arkts-apis/arkts-arkui-customspan-c.md) in [styled strings](../arkts-apis/arkts-arkui-styledstring.md#styled_string) to draw them by yourself.
> 
> - [accessibilityText](arkts-arkui-common-comp-commonmethod-c.md#accessibilitytext) takes effect only when the [onClick](arkts-arkui-common-comp-commonmethod-c.md#onclick) event is set for **Span**. The configured text is reflected only in the inline link pop-up recognized by the accessibility service. During direct announcement, the content of **Span** is still announced, and it is not replaced by the text configured in accessibilityText.
> 
> - Among the [universal events](arkts-arkui-common-comp.md), only the click event [onClick](arkts-arkui-common-comp-commonmethod-c.md#onclick) and the hover event [onHover](arkts-arkui-common-comp-commonmethod-c.md#onhover) are supported.

## Child Components

Not supported

## Span

```TypeScript
Span(value: string | Resource)
```

Defines the constructor of Span.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-SpanInterface-(value: string | Resource): SpanAttribute--><!--Device-SpanInterface-(value: string | Resource): SpanAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Plain text. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [TextBackgroundStyle](arkts-arkui-span-comp-textbackgroundstyle-i.md) | Define the background style of span. |

## Examples

### Example 1: Setting the Text Style

This example demonstrates how to apply different text styles and configure click events for the Span.



```TypeScript
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

### Example 2: Setting the Text Shadow

In API version 11 and later versions, the [textShadow](#textshadow11) attribute is used to set the text shadow.



```TypeScript
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

### Example 3: Setting the Background Style

This example demonstrates how to set the background style for text using the [textBackgroundStyle](#textbackgroundstyle11) attribute, available since API version 11.



```TypeScript
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

### Example 4: Setting the Text Baseline Offset

In API version 12 and later versions, this example demonstrates how to set different baseline offsets for text through the [baselineOffset](#baselineoffset12) attribute.



```TypeScript
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

### Example 5 (Set the Variable Font Attribute)

This example sets the variable font attribute through the [fontVariations](#fontvariations) attribute.

Since API version 26.0.0, the [fontVariations](#fontvariations) API is added.

```TypeScript
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
