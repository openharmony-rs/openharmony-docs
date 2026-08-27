# Span

作为Text、ContainerSpan组件的子组件，用于显示行内文本，支持对文本的字体、颜色、大小等样式进行细粒度设置。适用于在同一行文本中混合显示 不同样式的场景，如不同字体颜色的文本、添加装饰线或阴影效果等。
> **说明：** > > 该组件从API version 10开始支持继承父组件Text的属性，即如果子组件未设置属性且父组件设置属性，则继承父组件设置的属性。支持继承的属性仅包括：fontColor、fontSize、fontStyle、 > fontWeight、decoration、letterSpacing、textCase、fontFamily、textShadow。 > > 不支持[通用属性]](../../../reference/apis-arkui/arkui-ts/ts-component-general-attributes.md)。若需设置通用属性， > 应使用Text进行设置，或改用属性字符串中的[CustomSpan](../arkts-apis/arkts-arkui-customspan-c.md)自行绘制。 > > [通用事件](arkts-arkui-commonmethod-c.md)只支持点击事件 > onClick和悬浮事件 > onHover。

## 子组件

无

## Span

```TypeScript
Span(value: string | Resource)
```

定义Span组件构造函数。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| Resource | 是 | 文本内容。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [TextBackgroundStyle](arkts-arkui-textbackgroundstyle-i.md) | 定义Span的背景样式。 |

## 示例

该示例展示了设置不同样式的文本效果以及Span配置点击事件。

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

      // 文本横线添加
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

      // 文本字符间距
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

      // 文本大小写展示设置
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

      // 文本字体样式设置
      Text('FontStyle').fontSize(9).fontColor(0xCCCCCC).margin({ top: 12 })
      Text() {
        Span('I am FontStyle-Normal').fontSize(12)
          .fontStyle(FontStyle.Normal)
      }

      Text() {
        Span('I am FontStyle-Italic').fontSize(12)
          .fontStyle(FontStyle.Italic)
      }

      // 文本字体粗细设置
      Text('FontWeight').fontSize(9).fontColor(0xCCCCCC).margin({ top: 12 })
      Text() {
        Span('I am FontWeight-Lighter').fontSize(12)
          .fontWeight(FontWeight.Lighter)
      }

      Text() {
        Span('I am FontWeight-Bold').fontSize(12)
          .fontWeight(FontWeight.Bold)
      }

      // 文本行高设置
      Text('LineHeight').fontSize(9).fontColor(0xCCCCCC).margin({ top: 12 })
      Text() {
        Span('I am lineHeight default\n').fontSize(12)
          .fontWeight(FontWeight.Lighter)
        Span('I am lineHeight 30').fontSize(12)
          .lineHeight(30)
      }
      .backgroundColor(Color.Gray)

      // 文本样式设置
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

      // 文本字体配置设置。从API version 24开始新增支持fontConfigs属性。
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

      // 文本字体粗细配置设置。从API version 24开始新增支持fontWeightConfigs属性。
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

      // span点击事件设置
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

从API version 11开始，该示例通过[textShadow](#textshadow11)属性展示了文本设置阴影的效果。

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

从API version 11开始，该示例通过[textBackgroundStyle](#textbackgroundstyle11)属性展示了文本设置背景样式的效果。

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

从API version 12开始，该示例通过[baselineOffset](#baselineoffset12)属性展示了文本设置不同基线偏移量的效果。

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
          // $r('app.media.sky')需要替换为开发者所需的图像资源文件。
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

从API版本26.0.0开始，新增[fontVariations](#fontvariations)接口。

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
          // wght代表可变字体的字重属性
          .fontVariations([{ axis: 'wght', value: this.weightValue }])
      }

      Button('字重: ' + this.weightValue)
        .margin(10)
        .onClick(() => {
          this.weightValue += 100;
        })
    }.width('100%')
  }
}
```
