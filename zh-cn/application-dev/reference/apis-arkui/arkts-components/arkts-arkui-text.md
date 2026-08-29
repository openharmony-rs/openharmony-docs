# Text

Text组件用于显示文本内容，支持设置字体样式、文本对齐、行高、装饰线等属性，支持图文混排、文本选择、文本识别等功能，适用于需要展示文本信息的各类应用场景。

## 子组件

可以包含Span、ImageSpan、SymbolSpan和 ContainerSpan子组件。

> **说明：**
> 
> 使用子组件实现
> [图文混排](../../../ui/arkts-text-image-layout.md)场景。

## Text

```TypeScript
Text(content?: string | Resource, value?: TextOptions)
```

定义文本组件构造函数。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | string \| Resource | 否 | 文本内容。当需要直接显示文本内容时传入此参数。包含子组件Span或设置了 属性字符串时，该参数不生效。  默认值：' ' **说明：**  显示内容的优先级：属性字符串>Span>Text的文本内容。 |
| value | [TextOptions](arkts-arkui-textoptions-i.md) | 否 | 文本组件初始化选项，用于配置文本控制器。当需要使用TextController的功能控制文本内容和选择时，传入此参数。  默认值：不设置时，不使用文本控制器。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [TextMarqueeOptions](arkts-arkui-textmarqueeoptions-i.md) | Marquee初始化参数。 |
| [TextOptions](arkts-arkui-textoptions-i.md) | Text初始化参数。 |
| [TextOverflowOptions](arkts-arkui-textoverflowoptions-i.md) | 文本超长显示方式对象。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [MarqueeStartPolicy](arkts-arkui-marqueestartpolicy-e.md) | Marquee的滚动方式，可选择默认持续滚动或条件触发滚动。 |
| [MarqueeState](arkts-arkui-marqueestate-e.md) | Marquee状态回调的返回值。 |
| [MarqueeUpdatePolicy](arkts-arkui-marqueeupdatepolicy-e.md) | 跑马灯组件属性更新后，跑马灯的滚动策略。 |
| [TextResponseType](arkts-arkui-textresponsetype-e.md) | 选择菜单的响应类型。 |
| [TextSpanType](arkts-arkui-textspantype-e.md) | Span类型信息。 |

## 示例

该示例通过textAlign、lineHeight、baselineOffset、halfLeading（从API version 12开始）属性展示了文本布局的效果。

```TypeScript
// xxx.ets
@Extend(Text)
function style(textAlign: TextAlign) {
  .textAlign(textAlign)
  .fontSize(12)
  .border({ width: 1 })
  .padding(10)
  .width('100%')
  .margin(5)
}

@Entry
@Component
struct TextExample1 {
  @State changeTextAlignIndex: number = 0;
  @State textAlign: TextAlign[] = [TextAlign.Start, TextAlign.Center, TextAlign.End];
  @State textAlignStr: string[] = ['Start', 'Center', 'End'];

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center }) {
      // 设置文本水平方向对齐方式
      // 单行文本
      Text('textAlign').fontSize(9).fontColor(0xCCCCCC)
      Text(`TextAlign set to ${this.textAlignStr[this.changeTextAlignIndex]}.`)
        .style(this.textAlign[this.changeTextAlignIndex])

      // 多行文本
      Text(`This is the text content with textAlign set to ${this.textAlignStr[this.changeTextAlignIndex]}.`)
        .style(this.textAlign[this.changeTextAlignIndex])
        .margin(5)

      Row() {
        Button('当前TextAlign类型：' + this.textAlignStr[this.changeTextAlignIndex]).onClick(() => {
          this.changeTextAlignIndex++;
          if (this.changeTextAlignIndex > (this.textAlignStr.length - 1)) {
            this.changeTextAlignIndex = 0;
          }
        })
      }.justifyContent(FlexAlign.Center).width('100%')

      // 设置文本行高
      Text('lineHeight').fontSize(9).fontColor(0xCCCCCC)
      Text('This is the text with the line height set. This is the text with the line height set.')
        .style(TextAlign.Start)
      Text('This is the text with the line height set. This is the text with the line height set.')
        .style(TextAlign.Start)
        .lineHeight(20)

      // 设置文本基线偏移
      Text('baselineOffset').fontSize(9).fontColor(0xCCCCCC)
      Text('This is the text content with baselineOffset 0.')
        .baselineOffset(0)
        .style(TextAlign.Start)
      Text('This is the text content with baselineOffset 30.')
        .baselineOffset(30)
        .style(TextAlign.Start)
      Text('This is the text content with baselineOffset -20.')
        .baselineOffset(-20)
        .style(TextAlign.Start)

      // 设置文本是否居中对齐
      Text('halfLeading').fontSize(9).fontColor(0xCCCCCC)
      Text('This is the text with the halfLeading set.')
        .lineHeight(60)
        .halfLeading(true)
        .style(TextAlign.Start)
      Text('This is the text without the halfLeading set.')
        .lineHeight(60)
        .halfLeading(false)
        .style(TextAlign.Start)
    }.height(600).width('100%').padding({ left: 35, right: 35, top: 35 })
  }
}
```

该示例通过decoration、letterSpacing、textCase、fontFamily、textShadow（从API version 10开始）、fontStyle、textIndent（从API version 10开始）、fontWeight（从API version 12开始，支持设置字重无极调节配置项）属性展示了不同样式的文本效果。

```TypeScript
// xxx.ets
@Extend(Text)
function style() {
  .font({ size: 12 }, { enableVariableFontWeight: true })
  .border({ width: 1 })
  .padding(10)
  .width('100%')
  .margin(5)
}

@Entry
@Component
struct TextExample2 {
  @State changeDecorationIndex: number = 0;
  @State textDecorationType: TextDecorationType[] =
    [TextDecorationType.LineThrough, TextDecorationType.Overline, TextDecorationType.Underline];
  @State textDecorationTypeStr: string[] = ['LineThrough', 'Overline', 'Underline'];
  @State textDecorationStyle: TextDecorationStyle[] =
    [TextDecorationStyle.SOLID, TextDecorationStyle.DOTTED, TextDecorationStyle.WAVY];
  @State textDecorationStyleStr: string[] = ['SOLID', 'DOTTED', 'WAVY'];

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center }) {
      Text('decoration').fontSize(9).fontColor(0xCCCCCC)
      Text('This is the text content with the decoration set to LineThrough and the color set to Red.')
        .decoration({
          type: this.textDecorationType[this.changeDecorationIndex],
          color: Color.Red,
          style: this.textDecorationStyle[this.changeDecorationIndex]
        })
        .style()
        .margin(5)

      Row() {
        Button('decoration type：' + this.textDecorationTypeStr[this.changeDecorationIndex] + ' & ' +
        this.textDecorationStyleStr[this.changeDecorationIndex]).onClick(() => {
          this.changeDecorationIndex++;
          if (this.changeDecorationIndex > (this.textDecorationTypeStr.length - 1)) {
            this.changeDecorationIndex = 0;
          }
        })
      }.justifyContent(FlexAlign.Center).width('100%')

      // 文本字符间距
      Text('letterSpacing').fontSize(9).fontColor(0xCCCCCC)
      Text('This is the text content with letterSpacing 0.')
        .letterSpacing(0)
        .style()
      Text('This is the text content with letterSpacing 3.')
        .letterSpacing(3)
        .style()
      Text('This is the text content with letterSpacing -1.')
        .letterSpacing(-1)
        .style()

      Text('textCase').fontSize(9).fontColor(0xCCCCCC)
      Text('This is the text content with textCase set to Normal.')
        .textCase(TextCase.Normal)
        .style()
      // 文本全小写展示
      Text('This is the text content with textCase set to LowerCase.')
        .textCase(TextCase.LowerCase)
        .style()
      // 文本全大写展示
      Text('This is the text content with textCase set to UpperCase.')
        .textCase(TextCase.UpperCase)
        .style()

      Text('fontFamily').fontSize(9).fontColor(0xCCCCCC)
      // 设置字体列表
      Text('This is the text content with fontFamily')
        .style()
        .fontFamily('HarmonyOS Sans')

      Text('textShadow').fontSize(9).fontColor(0xCCCCCC)
      // 设置文字阴影效果
      Text('textShadow')
        .style()
        .textAlign(TextAlign.Center)
        .fontSize(40)
        .textShadow({
          radius: 10,
          color: Color.Black,
          offsetX: 0,
          offsetY: 0
        })

      Text('fontStyle').fontSize(9).fontColor(0xCCCCCC)
      // 设置字体样式
      Text('This is the text content with fontStyle set to Italic')
        .style()
        .fontStyle(FontStyle.Italic)
      Text('This is the text content with fontStyle set to Normal')
        .style()
        .fontStyle(FontStyle.Normal)

      Text('textIndent').fontSize(9).fontColor(0xCCCCCC)
      // 设置文字缩进
      Text('This is the text content with textIndent 30')
        .style()
        .textIndent(30)

      Text('fontWeight').fontSize(9).fontColor(0xCCCCCC)
      // 设置文本的字体粗细
      Text('This is the text content with fontWeight 800')
        .style()
        .fontWeight('800', { enableVariableFontWeight: true })

    }.width('100%').padding({ left: 35, right: 35 })
  }
}
```

从API version 24开始，EllipsisMode新增了MULTILINE_START和MULTILINE_CENTER枚举。

```TypeScript
// xxx.ets
import { LengthMetrics } from '@kit.ArkUI';

@Extend(Text)
function style() {
  .textAlign(TextAlign.Center)
  .fontSize(15)
  .border({ width: 1 })
  .padding(10)
  .width('100%')
  .margin(5)
}

@Entry
@Component
struct TextExample3 {
  @State text: string =
    'The text component is used to display a piece of textual information.' +
      'Support universal attributes and universal text attributes.' +
      'The text component is used to display a piece of textual information.' +
      'Support universal attributes and universal text attributes.';
  @State ellipsisModeIndex: number = 0;
  @State ellipsisMode: EllipsisMode[] =
    [EllipsisMode.START, EllipsisMode.CENTER, EllipsisMode.END, EllipsisMode.MULTILINE_START,
      EllipsisMode.MULTILINE_CENTER]; // 从API version 24开始新增MULTILINE_START和MULTILINE_CENTER
  @State ellipsisModeStr: string[] = ['START', 'CENTER', 'END', 'MULTILINE_START',
    'MULTILINE_CENTER'];

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center }) {
      // 文本超长时显示方式
      Text('TextOverflow+maxLines').fontSize(12).fontColor(Color.Black)
      // 超出maxLines截断内容展示
      Text('This is the setting of textOverflow to Clip text content This is the setting of textOverflow to None text content. This is the setting of textOverflow to Clip text content This is the setting of textOverflow to None text content.')
        .textOverflow({ overflow: TextOverflow.Clip })
        .maxLines(1)
        .style()

      // 超出maxLines展示省略号
      Text('This is set textOverflow to Ellipsis text content This is set textOverflow to Ellipsis text content.')
        .textOverflow({ overflow: TextOverflow.Ellipsis })
        .maxLines(1)
        .style()

      Text('marquee').fontSize(12).fontColor(Color.Black)
      // 设置文本超长时以跑马灯的方式展示
      Text('This is the text with the text overflow set marquee')
        .textOverflow({ overflow: TextOverflow.MARQUEE })
        .style()
        .marqueeOptions({
          start: true,
          fromStart: true,
          step: 6,
          spacing: LengthMetrics.vp(48), // 从API version 23开始新增
          loop: -1,
          delay: 0,
          fadeout: false,
          marqueeStartPolicy: MarqueeStartPolicy.DEFAULT,
          marqueeUpdatePolicy: MarqueeUpdatePolicy.DEFAULT // 从API version 23开始新增
        })
        .onMarqueeStateChange((state: MarqueeState) => {
          if (state == MarqueeState.START) {
            // "收到状态: START";
          } else if (state == MarqueeState.BOUNCE) {
            // "收到状态: BOUNCE";
          } else if (state == MarqueeState.FINISH) {
            // "收到状态: FINISH";
          }
        })

      // 设置文本超长时省略号的位置
      Text('ellipsisMode(单行文本)').fontSize(12).fontColor(Color.Black)
      Text(this.text)
        .textOverflow({ overflow: TextOverflow.Ellipsis })
        .ellipsisMode(this.ellipsisMode[this.ellipsisModeIndex])
        .maxLines(1)
        .style()
      Text('ellipsisMode(多行文本)').fontSize(12).fontColor(Color.Black)
      Text(this.text)
        .textOverflow({ overflow: TextOverflow.Ellipsis })
        .ellipsisMode(this.ellipsisMode[this.ellipsisModeIndex])
        .maxLines(3)
        .style()

      Row() {
        Button('更改省略号位置：' + this.ellipsisModeStr[this.ellipsisModeIndex]).onClick(() => {
          this.ellipsisModeIndex++;
          if (this.ellipsisModeIndex > (this.ellipsisModeStr.length - 1)) {
            this.ellipsisModeIndex = 0;
          }
        })
      }
    }.height(600).width('100%').padding({ left: 35, right: 35, top: 35 })
  }
}
```

该示例通过wordBreak（从API version 11开始）、lineBreakStrategy（从API version 12开始）、clip属性展示了文本在不同断行、折行规则下的效果以及文本超长时是否截断。

```TypeScript
// xxx.ets
@Extend(Text)
function style() {
  .fontSize(12)
  .border({ width: 1 })
  .padding(10)
  .width('100%')
  .margin(5)
}

@Entry
@Component
struct TextExample4 {
  @State text: string =
    'The text component is used to display a piece of textual information.Support universal attributes and universal text attributes.';
  @State longText: string =
    'They can be classified as built-in components–those directly provided by the ArkUI framework and custom components – those defined by developers' +
      'The built-in components include buttons radio buttons progress indicators and text You can set the rendering effect of these components in method chaining mode,' +
      'page components are divided into independent UI units to implement independent creation development and reuse of different units on pages making pages more engineering-oriented.';
  @State textClip: boolean = false;
  @State wordBreakIndex: number = 0;
  @State wordBreak: WordBreak[] = [WordBreak.NORMAL, WordBreak.BREAK_ALL, WordBreak.BREAK_WORD];
  @State wordBreakStr: string[] = ['NORMAL', 'BREAK_ALL', 'BREAK_WORD'];
  @State lineBreakStrategyIndex: number = 0;
  @State lineBreakStrategy: LineBreakStrategy[] =
    [LineBreakStrategy.GREEDY, LineBreakStrategy.HIGH_QUALITY, LineBreakStrategy.BALANCED];
  @State lineBreakStrategyStr: string[] = ['GREEDY', 'HIGH_QUALITY', 'BALANCED'];

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center }) {
      Text('wordBreak').fontSize(9).fontColor(0xCCCCCC)
      // 设置文本断行规则
      Text(this.text)
        .maxLines(2)
        .textOverflow({ overflow: TextOverflow.Ellipsis })
        .wordBreak(this.wordBreak[this.wordBreakIndex])
        .style()

      Row() {
        Button('当前wordBreak模式：' + this.wordBreakStr[this.wordBreakIndex]).onClick(() => {
          this.wordBreakIndex++;
          if (this.wordBreakIndex > (this.wordBreakStr.length - 1)) {
            this.wordBreakIndex = 0;
          }
        })
      }

      Text('clip').fontSize(9).fontColor(0xCCCCCC)
      // 设置文本是否超长截断
      Text('This is set wordBreak to WordBreak text Taumatawhakatangihangakoauauotamateaturipukakapikimaungahoronukupokaiwhenuakitanatahu.')
        .wordBreak(WordBreak.NORMAL)
        .maxLines(2)
        .clip(this.textClip)
        .style()
      Row() {
        Button('切换clip：' + this.textClip).onClick(() => {
          this.textClip = !this.textClip;
        })
      }

      Text('lineBreakStrategy').fontSize(9).fontColor(0xCCCCCC)
      // 设置文本折行规则
      Text(this.longText)
        .lineBreakStrategy(this.lineBreakStrategy[this.lineBreakStrategyIndex])
        .style()
      Row() {
        Button('当前lineBreakStrategy模式：' + this.lineBreakStrategyStr[this.lineBreakStrategyIndex]).onClick(() => {
          this.lineBreakStrategyIndex++;
          if (this.lineBreakStrategyIndex > (this.lineBreakStrategyStr.length - 1)) {
            this.lineBreakStrategyIndex = 0;
          }
        })
      }
    }.height(600).width('100%').padding({ left: 35, right: 35, top: 35 })
  }
}
```

从API版本26.0.0开始，新增onWillCopy接口。

```TypeScript
// xxx.ets
@Entry
@Component
struct TextExample5 {
  @State onCopy: string = '';
  @State text: string =
    'This is set selection to Selection text content This is set selection to Selection text content.';
  @State start: number = 0;
  @State end: number = 20;

  build() {
    Column() {
      Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Start }) {
        Text(this.text)
          .fontSize(12)
          .border({ width: 1 })
          .lineHeight(20)
          .margin(30)
          .copyOption(CopyOptions.InApp)
          .selection(this.start, this.end)
          .onCopy((value: string) => {
            this.onCopy = value;
          })
          // 从API版本26.0.0开始支持onWillCopy
          .onWillCopy((value: string) => {
            // 根据业务逻辑判断是否允许复制
            return true; // 允许复制时返回true，随后onCopy会被触发
          })
          .draggable(true)
          .caretColor(Color.Red)
          .selectedBackgroundColor(Color.Grey)
          .enableHapticFeedback(true)
        Button('Set text selection')
          .onClick(() => {
            // 变更文本选中起始点、终点
            this.start = 10;
            this.end = 30;
          })
        Text(this.onCopy).fontSize(12).margin(10).key('copy')
      }.height(600).width(335).padding({ left: 35, right: 35, top: 35 })
    }.width('100%')
  }
}
```

该示例通过heightAdaptivePolicy（从API version 10开始）属性展示文本自适应效果以及通过minFontScale（从API version 12开始）、maxFontScale（从API version 12开始）展示设置字体缩放倍数限制范围。

```TypeScript
// xxx.ets
@Extend(Text)
function style(heightAdaptivePolicy: TextHeightAdaptivePolicy) {
  .width('80%')
  .height(90)
  .borderWidth(1)
  .minFontSize(10)
  .maxFontSize(30)
  .maxLines(2)
  .margin(5)
  .textOverflow({ overflow: TextOverflow.Ellipsis })
  .heightAdaptivePolicy(heightAdaptivePolicy)
}

@Entry
@Component
struct TextExample6 {
  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center }) {
      // 设置文本自适应高度的方式
      Text('heightAdaptivePolicy').fontSize(9).fontColor(0xCCCCCC)
      Text('This is the text with the height adaptive policy set.')
        .style(TextHeightAdaptivePolicy.MAX_LINES_FIRST)
      Text('This is the text with the height adaptive policy set.')
        .style(TextHeightAdaptivePolicy.MIN_FONT_SIZE_FIRST)
      Text('This is the text with the height adaptive policy set.')
        .style(TextHeightAdaptivePolicy.LAYOUT_CONSTRAINT_FIRST)

      Text('fontScale').fontSize(9).fontColor(0xCCCCCC)
      Text('This is the text content with minFontScale set to 1 and maxFontScale set to 1.2')
        .style(TextHeightAdaptivePolicy.MAX_LINES_FIRST)
        .minFontScale(1)
        .maxFontScale(1.2)
    }.height(600).width('100%').padding({ left: 35, right: 35, top: 35 })
  }
}
```

从API version 11开始，该示例通过enableDataDetector、dataDetectorConfig接口实现了文本识别的功能。当enableDataDetector设为true且不设置dataDetectorConfig时，系统会识别所有实体类型，并将识别实体的字体颜色改为蓝色、添加蓝色下划线。

```TypeScript
// xxx.ets
@Entry
@Component
struct TextExample7 {
  @State phoneNumber: string = '(86) (755) ********';
  @State url: string = 'www.********.com';
  @State email: string = '***@example.com';
  @State address: string = 'XX省XX市XX区XXXX';
  @State datetime: string = 'XX年XX月XX日XXXX';
  @State enableDataDetector: boolean = true;
  @State types: TextDataDetectorType[] = [];

  build() {
    Row() {
      Column() {
        Text(
          '电话号码：' + this.phoneNumber + '\n' +
            '链接：' + this.url + '\n' +
            '邮箱：' + this.email + '\n' +
            '地址：' + this.address + '\n' +
            '时间：' + this.datetime
        )
          .fontSize(16)
          .copyOption(CopyOptions.InApp)
          .enableDataDetector(this.enableDataDetector)
          .dataDetectorConfig({
            types: this.types, onDetectResultUpdate: (result: string) => {
            }
          })
          .textAlign(TextAlign.Center)
          .borderWidth(1)
          .padding(10)
          .width('100%')
      }
      .width('100%')
      // 使用parallelGesture中的TapGesture替代onClick属性，达到非冒泡事件类似冒泡
      // 的效果，点击Text组件区域Column上的点击事件正常响应
      .parallelGesture(TapGesture().onAction((event: GestureEvent) => {
        console.info('test column onClick timestamp:' + event.timestamp);
      }), GestureMask.Normal)
    }
    .height('100%')
  }
}
```

从API version 11开始，该示例通过bindSelectionMenu、onTextSelectionChange、closeSelectionMenu接口实现了文本绑定自定义菜单的功能。

```TypeScript
// xxx.ets
@Entry
@Component
struct TextExample8 {
  controller: TextController = new TextController();
  options: TextOptions = { controller: this.controller };

  build() {
    Column() {
      Column() {
        Text(undefined, this.options) {
          Span('Hello World')
          // $r('app.media.startIcon')需要替换为开发者所需的图像资源文件。
          ImageSpan($r('app.media.startIcon'))
            .width(50)
            .height(50)
            .objectFit(ImageFit.Fill)
            .verticalAlign(ImageSpanAlignment.CENTER)
        }
        .copyOption(CopyOptions.InApp)
        .bindSelectionMenu(TextSpanType.IMAGE, this.LongPressImageCustomMenu, TextResponseType.LONG_PRESS, {
          onDisappear: () => {
            console.info(`自定义选择菜单关闭时回调`);
          },
          onAppear: () => {
            console.info(`自定义选择菜单弹出时回调`);
          },
          onMenuShow: () => {
            console.info(`自定义选择菜单显示时回调`);
          },
          onMenuHide: () => {
            console.info(`自定义选择菜单隐藏时回调`);
          }
        })
        .bindSelectionMenu(TextSpanType.TEXT, this.RightClickTextCustomMenu, TextResponseType.RIGHT_CLICK)
        .bindSelectionMenu(TextSpanType.MIXED, this.SelectMixCustomMenu, TextResponseType.SELECT)
        .onTextSelectionChange((selectionStart: number, selectionEnd: number) => {
          console.info(`文本选中区域变化回调, selectionStart: ${selectionStart}, selectionEnd: ${selectionEnd}`);
        })
        .borderWidth(1)
        .borderColor(Color.Red)
        .width(200)
        .height(100)
      }
      .width('100%')
      .backgroundColor(Color.White)
      .alignItems(HorizontalAlign.Start)
      .padding(25)
    }
    .height('100%')
  }

  @Builder
  RightClickTextCustomMenu() {
    Column() {
      Menu() {
        MenuItemGroup() {
          // $r('app.media.startIcon')需要替换为开发者所需的图像资源文件。
          MenuItem({ startIcon: $r('app.media.startIcon'), content: 'Right Click Menu 1', labelInfo: '' })
            .onClick((event) => {
              this.controller.closeSelectionMenu();
            })
          MenuItem({ startIcon: $r('app.media.startIcon'), content: 'Right Click Menu 2', labelInfo: '' })
          MenuItem({ startIcon: $r('app.media.startIcon'), content: 'Right Click Menu 3', labelInfo: '' })
        }
      }
      .MenuStyles()
    }
  }

  @Builder
  LongPressImageCustomMenu() {
    Column() {
      Menu() {
        MenuItemGroup() {
          // $r('app.media.startIcon')需要替换为开发者所需的图像资源文件。
          MenuItem({ startIcon: $r('app.media.startIcon'), content: 'Long Press Image Menu 1', labelInfo: '' })
            .onClick((event) => {
              this.controller.closeSelectionMenu();
            })
          MenuItem({ startIcon: $r('app.media.startIcon'), content: 'Long Press Image Menu 2', labelInfo: '' })
          MenuItem({ startIcon: $r('app.media.startIcon'), content: 'Long Press Image Menu 3', labelInfo: '' })
        }
      }
      .MenuStyles()
    }
  }

  @Builder
  SelectMixCustomMenu() {
    Column() {
      Menu() {
        MenuItemGroup() {
          // $r('app.media.startIcon')需要替换为开发者所需的图像资源文件。
          MenuItem({ startIcon: $r('app.media.startIcon'), content: 'Select Mixed Menu 1', labelInfo: '' })
            .onClick((event) => {
              this.controller.closeSelectionMenu();
            })
          MenuItem({ startIcon: $r('app.media.startIcon'), content: 'Select Mixed Menu 2', labelInfo: '' })
          MenuItem({ startIcon: $r('app.media.startIcon'), content: 'Select Mixed Menu 3', labelInfo: '' }) 
        }
      }
      .MenuStyles()
    }
  }
}

@Extend(Menu)
function MenuStyles() {
  .radius($r('sys.float.ohos_id_corner_radius_card'))
  .clip(true)
  .backgroundColor('#F0F0F0')
}
```

从API version 12开始，该示例通过fontFeature、lineSpacing接口展示了设置文本特性与行间距的效果，同时，配置LineSpacingOptions中的onlyBetweenLines（从API version 20开始）属性，可以设置文本的行间距，是否仅在行与行之间生效。

```TypeScript
// xxx.ets
import { LengthMetrics } from '@kit.ArkUI';

@Extend(Text)
function style() {
  .fontSize(12)
  .border({ width: 1 })
  .width('100%')
}

@Entry
@Component
struct TextExample9 {
  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.SpaceBetween }) {
      Text('lineSpacing').fontSize(9).fontColor(0xCCCCCC)
      // 设置文本行间距
      Text('This is a context with no lineSpacing set.')
        .lineSpacing(undefined)
        .style()
      Text('This is a context with lineSpacing set to 20_px.')
        .lineSpacing(LengthMetrics.px(20))
        .style()
      Text('This is the context with lineSpacing set to 20_vp.')
        .lineSpacing(LengthMetrics.vp(20))
        .style()
      Text('This is the context with lineSpacing set to 20_fp.')
        .lineSpacing(LengthMetrics.fp(20))
        .style()
      Text('This is the context with lineSpacing set to 20_lpx.')
        .lineSpacing(LengthMetrics.lpx(20))
        .style()
      Text('This is the context with lineSpacing set to 100%.')
        .lineSpacing(LengthMetrics.percent(1))
        .style()
      Text('The line spacing of this context is set to 20_px, and the spacing is effective only between the lines.')
        .lineSpacing(LengthMetrics.px(20), { onlyBetweenLines: true })
        .style()

      Text('fontFeature').fontSize(9).fontColor(0xCCCCCC)
      // 设置文本特性
      Text('This is frac on : 1/2 2/3 3/4')
        .fontFeature('"frac" on')
        .style()
      Text('This is frac off: 1/2 2/3 3/4')
        .fontFeature('"frac" off')
        .style()
    }.height(300).width(350).padding({ left: 35, right: 35, top: 35 })
  }
}
```

从API version 12开始，该示例通过getLayoutManager接口调用文本的布局管理对象获取文本信息，同时，LayoutManager中的getRectsForRange（从API version 14开始）接口可以获取指定矩形宽度和高度下，文本中任意区间范围内字符或占位符的绘制区域信息。

```TypeScript
// xxx.ets
import { text } from '@kit.ArkGraphics2D';

@Entry
@Component
struct TextExample10 {
  @State lineCount: string = "";
  @State glyphPositionAtCoordinate: string = "";
  @State lineMetrics: string = "";
  @State rectsForRangeStr: string = "";
  controller: TextController = new TextController();
  @State textStr: string =
    'Hello World! 您好，世界！';

  build() {
    Scroll() {
      Column() {
        Text('Text组件getLayoutManager接口获取段落相对组件的信息')
          .fontSize(15)
          .fontColor(0xCCCCCC)
          .width('90%')
          .padding(10)
        Text(this.textStr, { controller: this.controller })
          .fontSize(25)
          .borderWidth(1)
          .onAreaChange(() => {
            // getLayoutManager在TextController未绑定Text或Text被销毁时会返回undefined，使用时需做判空处理
            let layoutManager: LayoutManager = this.controller.getLayoutManager();
            if (!layoutManager) {
              return;
            }
            this.lineCount = 'LineCount: ' + layoutManager.getLineCount();
          })

        Text('LineCount').fontSize(15).fontColor(0xCCCCCC).width('90%').padding(10)
        Text(this.lineCount)

        Text('GlyphPositionAtCoordinate').fontSize(15).fontColor(0xCCCCCC).width('90%').padding(10)
        Button("相对组件坐标[150,50]字形信息")
          .onClick(() => {
            let layoutManager: LayoutManager = this.controller.getLayoutManager();
            if (!layoutManager) {
              return;
            }
            let position: PositionWithAffinity = layoutManager.getGlyphPositionAtCoordinate(150, 50);
            this.glyphPositionAtCoordinate =
              '相对组件坐标[150,50] glyphPositionAtCoordinate position: ' + position.position + ' affinity: ' +
              position.affinity;
          })
          .margin({ bottom: 20, top: 10 })
        Text(this.glyphPositionAtCoordinate)

        Text('LineMetrics').fontSize(15).fontColor(0xCCCCCC).width('90%').padding(10)
        Button('首行行信息、文本样式信息、以及字体属性信息')
          .onClick(() => {
            let layoutManager: LayoutManager = this.controller.getLayoutManager();
            if (!layoutManager) {
              return;
            }
            let lineMetrics: LineMetrics = layoutManager.getLineMetrics(0);
            this.lineMetrics = 'lineMetrics is ' + JSON.stringify(lineMetrics) + '\n\n';
            let runMetrics = lineMetrics.runMetrics;
            runMetrics.forEach((value, key) => {
              this.lineMetrics += 'runMetrics key is ' + key + ' ' + JSON.stringify(value) + '\n\n';
            })
          })
          .margin({ bottom: 20, top: 10 })
        Text(this.lineMetrics)

        Text('getRectsForRange').fontSize(15).fontColor(0xCCCCCC).width('90%').padding(10)
        Button('获取指定矩形宽度和高度下，文本中任意区间范围内字符或占位符的绘制区域信息')
          .onClick(() => {
            let layoutManager: LayoutManager = this.controller.getLayoutManager();
            if (!layoutManager) {
              return;
            }
            let range: TextRange = { start: 0, end: 1 };
            let rectsForRangeInfo: text.TextBox[] =
              layoutManager.getRectsForRange(range, text.RectWidthStyle.TIGHT, text.RectHeightStyle.TIGHT);
            this.rectsForRangeStr = 'getRectsForRange result is ' + '\n\n';
            rectsForRangeInfo.forEach((value, key) => {
              this.rectsForRangeStr += 'rectsForRange key is ' + key + ' ' + JSON.stringify(value) + '\n\n';
            })
          })
          .margin({ bottom: 20, top: 10 })
        Text(this.rectsForRangeStr)
      }
      .margin({ top: 100, left: 8, right: 8 })
    }
  }
}
```

从API version 12开始，该示例通过[textSelectable](arkts-arkui-text-attribute.md#textselectable)属性实现了设置TextSelectMode.SELECTABLE_FOCUSABLE时能够触发键盘框选文本功能。

```TypeScript
// xxx.ets
@Entry
@Component
struct TextExample11 {
  @State message: string =
    'TextTextTextTextTextTextTextText' + 'TextTextTextTextTextTextTextTextTextTextTextTextTextTextTextText';

  build() {
    Column() {
      Text(this.message)
        .width(300)
        .height(100)
        .maxLines(5)
        .fontColor(Color.Black)
        .copyOption(CopyOptions.InApp)
        .selection(3, 8)
        .textSelectable(TextSelectableMode.SELECTABLE_FOCUSABLE)
    }.width('100%').margin({ top: 100 })
  }
}
```

从API version 12开始，该示例通过editMenuOptions接口实现了文本设置自定义菜单扩展项的文本内容、图标以及回调的功能，同时，可以在onPrepareMenu（从API version 20开始）回调中，进行菜单数据的设置。

```TypeScript
// xxx.ets
@Entry
@Component
struct TextExample12 {
  @State text: string = 'Text editMenuOptions'
  @State endIndex: number = 0;
  onCreateMenu = (menuItems: Array<TextMenuItem>) => {
    // $r('app.media.startIcon')需要替换为开发者所需的图像资源文件。
    let item1: TextMenuItem = {
      content: 'create1',
      icon: $r('app.media.startIcon'),
      id: TextMenuItemId.of('create1'),
    };
    let item2: TextMenuItem = {
      content: 'create2',
      id: TextMenuItemId.of('create2'),
      icon: $r('app.media.startIcon'),
    };
    menuItems.push(item1);
    menuItems.unshift(item2);
    let targetIndex = menuItems.findIndex(item => item.id.equals(TextMenuItemId.askAI));
    if (targetIndex !== -1) {
      menuItems.splice(targetIndex, 1); // 从目标索引删除1个元素
    }
    targetIndex = menuItems.findIndex(item => item.id.equals(TextMenuItemId.TRANSLATE));
    if (targetIndex !== -1) {
      menuItems.splice(targetIndex, 1);
    }
    return menuItems;
  }
  onMenuItemClick = (menuItem: TextMenuItem, textRange: TextRange) => {
    if (menuItem.id.equals(TextMenuItemId.of("create2"))) {
      console.info('拦截 id: create2 start:' + textRange.start + '; end:' + textRange.end);
      return true;
    }
    if (menuItem.id.equals(TextMenuItemId.of("prepare1"))) {
      console.info('拦截 id: prepare1 start:' + textRange.start + '; end:' + textRange.end);
      return true;
    }
    if (menuItem.id.equals(TextMenuItemId.COPY)) {
      console.info('拦截 COPY start:' + textRange.start + '; end:' + textRange.end);
      return true;
    }
    if (menuItem.id.equals(TextMenuItemId.SELECT_ALL)) {
      console.info('不拦截 SELECT_ALL start:' + textRange.start + '; end:' + textRange.end);
      return false;
    }
    return false;
  }
  // $r('app.media.startIcon')需要替换为开发者所需的图像资源文件。
  onPrepareMenu = (menuItems: Array<TextMenuItem>) => {
    let item1: TextMenuItem = {
      content: 'prepare1_' + this.endIndex,
      icon: $r('app.media.startIcon'),
      id: TextMenuItemId.of('prepare1'),
    };
    menuItems.unshift(item1);
    return menuItems;
  }
  @State editMenuOptions: EditMenuOptions = {
    onCreateMenu: this.onCreateMenu,
    onMenuItemClick: this.onMenuItemClick,
    onPrepareMenu: this.onPrepareMenu
  };

  build() {
    Column() {
      Text(this.text)
        .fontSize(20)
        .copyOption(CopyOptions.LocalDevice)
        .editMenuOptions(this.editMenuOptions)
        .margin({ top: 100 })
        .onTextSelectionChange((selectionStart: number, selectionEnd: number) => {
          this.endIndex = selectionEnd;
        })
    }
    .width('90%')
    .margin('5%')
  }
}
```

从API version 12开始，该示例通过privacySensitive属性展示了文本如何配置隐私隐藏的效果，实际显示需要卡片框架支持。

```TypeScript
// xxx.ets
@Entry
@Component
struct TextExample13 {
  build() {
    Column({ space: 10 }) {
      Text('privacySensitive')
        .privacySensitive(true)
        .margin({ top: 30 })
    }
    .alignItems(HorizontalAlign.Center)
    .width('100%')
  }
}
```

从API version 20开始，该示例通过enableAutoSpacing属性设置中西文自动间距。

```TypeScript
// xxx.ets
@Entry
@Component
struct TextExample {
  build() {
    Row() {
      Column() {
        Text('开启中西文自动间距').margin(5)
        Text('中西文Auto Spacing自动间距')
          .enableAutoSpacing(true)
        Text('关闭中西文自动间距').margin(5)
        Text('中西文Auto Spacing自动间距')
          .enableAutoSpacing(false)
      }.height('100%')
    }
    .width('60%')
  }
}
```

从API version 20开始，该示例通过shaderStyle接口实现了对Text组件显示为渐变色和纯色的功能。

```TypeScript
@Entry
@Component
struct ShaderColorStyle {
  @State message: string = 'Hello World';
  @State linearGradientOptionsAngle: LinearGradientOptions =
    {
      angle: 45,
      colors: [[Color.Red, 0.0], [Color.Blue, 0.3], [Color.Green, 0.5]]
    };
  @State linearGradientOptionsDirection: LinearGradientOptions =
    {
      direction: GradientDirection.LeftTop,
      colors: [[Color.Red, 0.0], [Color.Blue, 0.3], [Color.Green, 0.5]],
      repeating: true,
    };
  @State radialGradientOptions: RadialGradientOptions =
    {
      center: [50, 50],
      radius: 20,
      colors: [[Color.Red, 0.0], [Color.Blue, 0.3], [Color.Green, 0.5]],
      repeating: true,
    };
  @State colorShaderStyle: ColorShaderStyle =
    {
      color: Color.Blue
    };
  build() {
    Column({ space: 5 }) {
      Text('angle为45°的线性渐变').fontSize(18).width('90%').fontColor(0xCCCCCC)
        .margin({ top: 40, left: 40 })
      Text(this.message)
        .fontSize(50)
        .width('80%')
        .height(50)
        .shaderStyle(this.linearGradientOptionsAngle)
      Text('direction为LeftTop的线性渐变').fontSize(18).width('90%').fontColor(0xCCCCCC)
        .margin({ top: 40, left: 40 })
      Text(this.message)
        .fontSize(50)
        .width('80%')
        .height(50)
        .shaderStyle(this.linearGradientOptionsDirection)
      Text('径向渐变').fontSize(18).width('90%').fontColor(0xCCCCCC)
        .margin({ top: 40, left: 40 })
      Text(this.message)
        .fontSize(50)
        .width('80%')
        .height(50)
        .shaderStyle(this.radialGradientOptions)
      Text('纯色').fontSize(18).width('90%').fontColor(0xCCCCCC)
        .margin({ top: 40, left: 40 })
      Text(this.message)
        .fontSize(50)
        .width('80%')
        .height(50)
        .shaderStyle(this.colorShaderStyle)
    }
  }
}
```

从API version 20开始，该示例通过[optimizeTrailingSpace](arkts-arkui-text-attribute.md#optimizetrailingspace)属性展示了文本如何配置除去行尾空格的效果，一般需要与对齐功能搭配使用，实际显示需要字体引擎支持。

```TypeScript
// xxx.ets
@Entry
@Component
struct TextExample16 {
  build() {
    Column() {
      Text('Trimmed space enabled     ')
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
        .margin({ top: 20 })
        .optimizeTrailingSpace(true)
        .textAlign(TextAlign.Center)
      Text('Trimmed space disabled     ')
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
        .margin({ top: 20 })
        .optimizeTrailingSpace(false)
        .textAlign(TextAlign.Center)
    }
    .width("100%")
  }
}
```

从API version 20开始，该示例通过textVerticalAlign属性展示了文本如何设置文本垂直对齐效果。

```TypeScript
// xxx.ets
@Entry
@Component
struct TextExample14 {
  build() {
    Column({ space: 10 }) {
      Text() {
        Span('Hello')
          .fontSize(50)
        // $r('app.media.startIcon')需要替换为开发者所需的图像资源文件。
        ImageSpan($r('app.media.startIcon'))
          .width(30).height(30)
          .verticalAlign(ImageSpanAlignment.FOLLOW_PARAGRAPH)// 从API version 20开始，支持ImageSpanAlignment.FOLLOW_PARAGRAPH
        Span('World')
      }
      .textVerticalAlign(TextVerticalAlign.CENTER)
      .borderWidth(1)
    }
    .alignItems(HorizontalAlign.Center)
    .width('100%')
  }
}
```

从API version 20开始，该示例通过contentTransition属性展示了数字翻牌效果。

```TypeScript
// xxx.ets
@Entry
@Component
struct TextNumberTransition {
  @State number: number = 98;
  @State numberTransition: NumericTextTransition =
    new NumericTextTransition({ flipDirection: FlipDirection.DOWN, enableBlur: false });

  build() {
    Column() {
      Text(this.number + '')
        .borderWidth(1)
        .fontSize(40)
        .contentTransition(this.numberTransition)
      Button('change number')
        .onClick(() => {
          this.number++;
        })
        .margin(10)
    }
    .justifyContent(FlexAlign.Center)
    .height('100%')
    .width('100%')
  }
}
```

从API version 21开始，该示例通过textContentAlign属性展示了当文本内容区高度大于组件高度时文本内容区的垂直对齐。

```TypeScript
@Entry
@Component
struct TextContentAlignExample {

  build() {
    Column() {
      Row() {
        Text('这是一段展示文字')
          .fontSize(30)
          .backgroundColor(Color.Gray)
          .width('80%')
          .height(20)
          .textContentAlign(TextContentAlign.CENTER)
      }.height('60%')
    }
  }
}
```

从API version 22开始，该示例通过lineHeightMultiple属性展示了使用倍数模式设置行高，同时通过[minLineHeight](arkts-arkui-text-attribute.md#minlineheight)和[maxLineHeight](arkts-arkui-text-attribute.md#maxlineheight)来设置最小和最大行高值。

```TypeScript
import { LengthUnit } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State message: string = 'hello';

  build() {
    Scroll() {
      Column() {
        Row() {
          Text(this.message)
            .lineHeight(176)
            .backgroundColor(0xffc0c0c0)
            .fontSize(50)
          Text(this.message)
            .lineHeightMultiple(3)
            .backgroundColor(0xffc0c0c0)
            .fontSize(50)
          Text(this.message)
            .lineHeight(300)
            .maxLineHeight({value:176,unit:LengthUnit.FP})
            .backgroundColor(0xffc0c0c0)
            .fontSize(50)
          Text(this.message)
            .lineHeight(10)
            .minLineHeight({value:176,unit:LengthUnit.FP})
            .backgroundColor(0xffc0c0c0)
            .fontSize(50)
        }
      }
    }.height('100%')
    .width('100%')
  }
}
```

从API version 22开始，该示例使用minLines属性设置文本显示的最小行数。

```TypeScript
@Entry
@Component
struct TextExample1 {
  @State shortMessage: string = 'Hello world!';
  @State longMessage: string = 'The minimum number of lines displayed for this text setting is 1';

  build() {
    Column() {
      Text(this.shortMessage)
        .minLines(3)
        .fontSize(20)
        .margin(10)
        .width('95%')
        .border({ width: 1 })
      Text(this.longMessage)
        .minLines(1)
        .fontSize(20)
        .margin(10)
        .width('95%')
        .border({ width: 1 })
    }.height(100).width('90%').margin(10)
  }
}
```

从API version 23开始，该示例使用[TextController](arkts-arkui-textcontroller-c.md)中的setTextSelection设置文本选择区域并高亮显示。

```TypeScript
@Entry
@Component
struct Index {
  controller: TextController = new TextController();
  @State textStr: string = 'Hello World! 你好，世界！';

  build() {
    Scroll() {
      Column() {
        Text(this.textStr, { controller: this.controller })
          .fontSize(25)
          .borderWidth(1)
          .copyOption(CopyOptions.LocalDevice)
        Button('setTextSelection')
          .onClick(() => {
            this.controller.setTextSelection(1, 6, { menuPolicy: MenuPolicy.HIDE })
          })
          .margin({ bottom: 20, top: 10 } as Margin)
      }
      .margin({ top: 100, left: 8, right: 8 } as Margin)
    }
  }
}
```

从API版本26.0.0开始，新增punctuationOverflow接口。

```TypeScript
@Entry
@Component
struct PunctuationDemo {
  @State compressLeadingPunctuation: boolean = false;
  @State punctuationOverflow: boolean = false;
  @State text: string = '「0123456789！\n『0123456789：\n（0123456789；\n《0123456789）\n〈0123456789】';

  build() {
    Column() {
      Text(this.text)
        .compressLeadingPunctuation(this.compressLeadingPunctuation)
        .punctuationOverflow(this.punctuationOverflow)
        .border({ width: 1, color: Color.Black })
        .copyOption(CopyOptions.LocalDevice)
        .fontSize('20fp')
        .align(Alignment.Center)
        .height('35%')
        .width('40%')

      Column() {
        Button('开启行首标点符号压缩').onClick(() => {
          this.compressLeadingPunctuation = true
        }).margin(5)
        Button('关闭行首标点符号压缩').onClick(() => {
          this.compressLeadingPunctuation = false
        }).margin(5)
        Button('开启行尾标点符号悬挂').onClick(() => {
          this.punctuationOverflow = true
        }).margin(5)
        Button('关闭行尾标点符号悬挂').onClick(() => {
          this.punctuationOverflow = false
        }).margin(5)
      }
    }.width('100%').padding(20)
  }
}
```

从API version 23开始，新增includeFontPadding和fallbackLineSpacing接口。

```TypeScript
// xxx.ets

const UYGHUR_TEXT: string = 'ياخشىمۇسەنياخشىمۇسەنياخشىمۇسەنياخشىمۇسەنياخشىمۇسەنياخشىمۇسەنياخشىمۇسەن';
@Entry
@Component
struct Index {
  @State include: boolean | null | undefined = false;
  @State fallback: boolean | null | undefined = false;
  @State displayText: string = UYGHUR_TEXT;

  build() {
    Column() {
      Text(this.displayText)
        .includeFontPadding(this.include)
        .fallbackLineSpacing(this.fallback)
        .lineHeight(5)
        .width('100%')
        .height(100)
        .backgroundColor('#eee')
        .borderWidth(1)
        .borderColor('#dddddd')

      Scroll() {
        Column() {
          // --- IncludeFontPadding相关按钮 ---
          Button('设置includePadding: ' + this.include)
            .onClick(() => {
              this.include = this.include === false ? true : false;
            })
            .margin({ bottom: 10 })

          // --- FallbackLineSpacing相关按钮 ---
          Button('设置fallbackLineSpacing: ' + this.fallback)
            .onClick(() => {
              this.fallback = this.fallback === false ? true : false;
            })
            .margin({ bottom: 10 })

        }
        .width('100%')
        .padding(5)
      }
      .height(250)
      .backgroundColor('transparent')
      .scrollBarWidth(2)
      .scrollBarColor('#888')

    }
    .width('100%')
    .height('100%')
    .padding(20)
  }
}
```

从API version 23开始，新增selectedDragPreviewStyle接口。

```TypeScript
@Entry
@Component
struct TextTest {
  build() {
    Column() {
      Text('This is drag text')
        .copyOption(CopyOptions.InApp)
        .width(200)
        .height(100)
        .margin(150)
        .draggable(true)
        .selectedDragPreviewStyle({color: 'rgba(227, 248, 249, 1)'})
    }
    .height('100%')
  }
}
```

从API version 23开始，新增textDirection接口。

```TypeScript
// xxx.ets
@Entry
@Component
struct TextExample {
  @State text: string = 'Text文本排版方向示例';

  build() {
    Column({ space: 3 }) {
      Text('Text文本排版方向DEFAULT')
        .fontSize(12).width('90%').margin(5)
      Text(this.text)
        .width('95%')
        .borderWidth(1)
      Text('Text文本排版方向RTL')
        .fontSize(12).width('90%').margin(5)
      Text(this.text)
        .width('95%')
        .borderWidth(1)
        .textDirection(TextDirection.RTL)
      Text('Text文本排版方向RTL，文本水平方向对齐方式LEFT')
        .fontSize(12).width('90%').margin(5)
      Text(this.text)
        .width('95%')
        .borderWidth(1)
        .textDirection(TextDirection.RTL)
        .textAlign(TextAlign.LEFT)
    }
    .width('100%')
    .height('100%')
  }
}
```

从API version 24开始，支持getCharacterPositionAtCoordinate，getGlyphRangeForCharacterRange，getCharacterRangeForGlyphRange接口。该示例通过getLayoutManager接口调用文本的布局管理对象获取文本信息，通过LayoutManager中的getCharacterPositionAtCoordinate获取坐标字符的位置信息，通过getGlyphRangeForCharacterRange根据字符索引范围获取字形索引范围和实际的字符索引范围，通过getCharacterRangeForGlyphRange根据字形索引范围获取字符索引范围和实际的字形索引范围。

```TypeScript
// xxx.ets
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct TextExample10 {
  @State start: number = 10;
  @State end: number = 20;
  textController: TextController = new TextController();
  textStr: string = 'Hello World! 您好，世界!';
  @State str1: string = ''
  @State str2: string = ''
  @State str3: string = ''
  @State str4: string = ''
  titleParagraphStyleAttr: ParagraphStyle =
    new ParagraphStyle({ paragraphSpacing: LengthMetrics.px(50), textIndent: LengthMetrics.vp(15) });
  mutableStyledString: MutableStyledString =
    new MutableStyledString('属性字符串TextStyle测试\n属性字符串测试\n属性字符串TextStyle测试');

  build() {
    Column() {
      Text(this.textStr, { controller: this.textController }) {
        Span('Hello World 123 \n')
        Span('Hello World 456 \n')
        Span('Hello World 789 \n')
      }
      .fontSize(25)
      .borderWidth(1)

      Text(this.str1)
      Text(this.str2)
      Text(this.str3)
      Text(this.str4)

      Button('点击可增加属性字符串').onClick(() => {
        this.textController.setStyledString(this.mutableStyledString)
      })

      Button('相对组件坐标[150,50]字形信息')
        .onClick(() => {
          // getLayoutManager在TextController未绑定Text或Text被销毁时会返回undefined，使用时需做判空处理
          let layoutManager: LayoutManager = this.textController.getLayoutManager();
          if (!layoutManager) {
            return;
          }
          let position1: PositionWithAffinity = layoutManager.getGlyphPositionAtCoordinate(150, 50);
          this.str1 = '相对组件坐标[150,50] glyphPosition position: ' + position1.position +
            ' affinity: ' +
          position1.affinity;

          let position2: PositionWithAffinity =
            layoutManager.getCharacterPositionAtCoordinate(150, 50) as PositionWithAffinity;
          this.str2 = '相对组件坐标[150,50] characterPosition position: ' + position2.position +
            ' affinity: ' +
          position2.affinity;

          let range1: TextRange = { start: this.start, end: this.end };
          let ranges1: Array<TextRange> = layoutManager.getGlyphRangeForCharacterRange(range1) as Array<TextRange>
          this.str3 = 'getGlyphRangeForCharacterRange 字形数 ' + ranges1[0].start + ' ' + ranges1[0].end + '\n' +
            'getGlyphRangeForCharacterRange 实际字符数 ' + ranges1[1].start + ' ' + ranges1[1].end

          let range2: TextRange = { start: this.start, end: this.end };
          let ranges2: Array<TextRange> = layoutManager.getCharacterRangeForGlyphRange(range2) as Array<TextRange>
          this.str4 = 'getCharacterRangeForGlyphRange 字符数 ' + ranges2[0].start + ' ' + ranges2[0].end + '\n' +
            'getCharacterRangeForGlyphRange 实际字形数 ' + ranges2[1].start + ' ' + ranges2[1].end
        })
        .margin({ bottom: 20, top: 10 })
    }.justifyContent(FlexAlign.Center).width('100%').height('100%')
  }
}
```

从API版本26.0.0开始，新增orphanCharOptimization接口。

```TypeScript
// xxx.ets
@Entry
@Component
struct TextExample {
  @State text: string = 'aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa文本aaaaaaaaaaaaa';

  build() {
    Column({ space: 3 }) {
      Text('Text不使能孤字优化')
        .fontSize(12).width('90%').margin(5)
      Text(this.text)
        .fontSize(20)
        .width('456')
        .borderWidth(1)
      Text('Text使能孤字优化')
        .fontSize(12).width('90%').margin(5)
      Text(this.text)
        .fontSize(20)
        .width('456')
        .borderWidth(1)
        .orphanCharOptimization(true)
    }
    .width('100%')
    .height('100%')
  }
}
```

从API版本26.0.0开始，新增fontVariations接口。

```TypeScript
// xxx.ets
@Entry
@Component
struct TextExample {
  @State weightValue: number = 400;

  build() {
    Column() {
      Text('Hello World !')
        // wght代表可变字体的字重属性
        .fontVariations([{ axis: 'wght', value: this.weightValue }])
      Button('字重: ' + this.weightValue)
        .margin(10)
        .onClick(() => {
          this.weightValue += 100;
        })
    }.width('100%')
  }
}
```

从API版本26.0.0开始，文本组件调用该接口时，options中的menuType属性传入MenuType.PREVIEW_MENU，设置图片预览菜单的能力生效。

```TypeScript
// xxx.ets
@Entry
@Component
struct TextExample {
  @Builder
  panel() {
    Column() {
      Text('abc').backgroundColor('#F0F0F0')
    }.width(256)
  }

  build() {
    Column() {
      Column() {
        Text() {
          Span('Hello')
            .fontSize(50)
          // $r('app.media.startIcon')需要替换为开发者所需的图像资源文件。
          ImageSpan($r('app.media.startIcon'))
            .width(30).height(30)
            .verticalAlign(ImageSpanAlignment.FOLLOW_PARAGRAPH)// 从API version 20开始，支持ImageSpanAlignment.FOLLOW_PARAGRAPH
          Span('World')
        }
        .textVerticalAlign(TextVerticalAlign.CENTER)
        .borderWidth(1)
        .copyOption(CopyOptions.InApp)
        .bindSelectionMenu(TextSpanType.IMAGE, this.panel, TextResponseType.LONG_PRESS, {
          menuType : MenuType.PREVIEW_MENU,
          previewMenuOptions : {
            hapticFeedbackMode : HapticFeedbackMode.ENABLED
          }
        })
      }.width('100%').backgroundColor(Color.White)
    }.height('100%')
  }
}
```

从API版本26.0.0开始，新增incrementalUpdatePolicy属性。

```TypeScript
// xxx.ets
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct StyledStringAppend {
  textController: TextController = new TextController();
  scroller: Scroller = new Scroller();
  @State index: number = 0
  // 段落标题样式：居中、加粗
  titleParagraphStyle: ParagraphStyle = new ParagraphStyle({ textAlign: TextAlign.Center });
  // 第一段落样式：首行缩进20vp
  paragraphStyleAttr1: ParagraphStyle = new ParagraphStyle({ textIndent: LengthMetrics.vp(20) });
  // 第二段落样式：左对齐、首行缩进20vp
  paragraphStyleAttr2: ParagraphStyle =
    new ParagraphStyle({ textAlign: TextAlign.Start, textIndent: LengthMetrics.vp(20) });
  // 行高样式
  lineHeightStyle: LineHeightStyle = new LineHeightStyle(new LengthMetrics(30));
  str: string = '属性字符串段落缓存示例'
  styledString1: MutableStyledString = new MutableStyledString(this.str, [{
    start: 0,
    length: this.str.length,
    styledKey: StyledStringKey.PARAGRAPH_STYLE,
    styledValue: this.titleParagraphStyle
  }, {
    start: 0,
    length: this.str.length,
    styledKey: StyledStringKey.LINE_HEIGHT,
    styledValue: this.lineHeightStyle
  }, {
    start: 0,
    length: this.str.length,
    styledKey: StyledStringKey.FONT,
    styledValue: new TextStyle({
      fontColor: Color.Blue,
      fontWeight: FontWeight.Bolder
    })
  }]);

  aboutToAppear() {
    // 追加初始段落内容，设置段落缩进和行高
    let str1: string = '\n首段落：'
    let str2: string = '属性字符串支持段落样式缓存，单击下方按钮追加新段落，验证段落缓存效果。'
    let paragraph1: StyledString =
      new StyledString(str1 + str2, [{
        start: 0,
        length: str1.length,
        styledKey: StyledStringKey.PARAGRAPH_STYLE,
        styledValue: this.paragraphStyleAttr1
      }, {
        start: 0,
        length: str1.length,
        styledKey: StyledStringKey.FONT,
        styledValue: new TextStyle({
          fontColor: Color.Blue,
          fontWeight: FontWeight.Bold
        })
      }, {
        start: 0,
        length: str1.length + str2.length,
        styledKey: StyledStringKey.LINE_HEIGHT,
        styledValue: this.lineHeightStyle
      }]);
    this.styledString1.appendStyledString(paragraph1);
    this.textController.setStyledString(this.styledString1);
  }

  build() {
    Column() {
      Scroll(this.scroller) {
        Column() {
          Text('示例：属性字符串段落缓存\n单击"追加文本"追加新段落，后端走段落缓存\n')
            .fontSize(16)
            .fontColor(Color.Gray)
            .margin({ bottom: 5 })
            .width("100%")

          Text(undefined, { controller: this.textController })
            .width('100%')
            .borderWidth(1)
            .padding(10)
            .copyOption(CopyOptions.InApp)
            .incrementalUpdatePolicy(IncrementalUpdatePolicy.PARAGRAPH_CACHE)
        }
        .width('100%')
        .padding({ left: 20, right: 20 })
      }
      .width('100%')

      Button("追加文本")
        .width('80%')
        .margin({ top: 10, bottom: 15 })
        .onClick(() => {
          this.index++;
          // 追加新段落，每个段落带有段落缩进样式，触发后端段落缓存
          let str1: string = '\n第' + this.index + '段落：'
          let str2: string = '这是追加的文本内容，用于验证段落缓存机制。'
          let newParagraph: StyledString = new StyledString(
            str1 + str2,
            [{
              start: 0,
              length: str1.length,
              styledKey: StyledStringKey.PARAGRAPH_STYLE,
              styledValue: this.paragraphStyleAttr2
            }, {
              start: 0,
              length: str1.length + str2.length,
              styledKey: StyledStringKey.LINE_HEIGHT,
              styledValue: this.lineHeightStyle
            }, {
              start: 0,
              length: str1.length,
              styledKey: StyledStringKey.FONT,
              styledValue: new TextStyle({
                fontColor: Color.Blue,
                fontWeight: FontWeight.Bold
              })
            }]);
          this.styledString1.appendStyledString(newParagraph);
          this.textController.setStyledString(this.styledString1);
        })
    }
    .width('100%')
    .height('70%')
  }
}
```

从API版本26.0.0开始，通过tailIndents属性设置文本尾部缩进。

```TypeScript
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct TailIndentsExample {
  build() {
    Column() {
      Text('未设置tailIndents\n未设置tailIndents\n未设置tailIndents\n未设置tailIndents\n未设置tailIndents')
        .fontSize(20)
        .borderWidth(1)
        .borderColor(Color.Blue)
        .textAlign(TextAlign.End)
        .width('100%')

      Text('设置tailIndents单值\n设置tailIndents单值\n设置tailIndents单值\n设置tailIndents单值\n设置tailIndents单值')
        .fontSize(20)
        .borderWidth(1)
        .borderColor(Color.Blue)
        .textAlign(TextAlign.End)
        .width('100%')
        .tailIndents(LengthMetrics.vp(100))

      Text('设置tailIndents数组\n设置tailIndents数组\n设置tailIndents数组\n设置tailIndents数组\n设置tailIndents数组')
        .fontSize(20)
        .borderWidth(1)
        .borderColor(Color.Blue)
        .textAlign(TextAlign.End)
        .width('100%')
        .tailIndents([LengthMetrics.vp(100), LengthMetrics.vp(50), LengthMetrics.vp(20)])

    }
    .height('100%')
    .width('100%')
  }
}
```

从API version 22开始，新增enableSelectedDataDetector。

```TypeScript
@Entry
@Component
struct DataDetectorDemo {
  exampleText: string = '示例网址：www.example.com';

  build() {
    Column() {
      Row(){
        Text(this.exampleText)
          .copyOption(CopyOptions.LocalDevice)
          .enableSelectedDataDetector(true)
          .border({ width: 1, color: Color.Black })
          .padding(10)
          .margin(10)
      }
    }.width('100%')
  }
}
```

从API版本26.0.0开始，新增带编码类型参数的getCharacterPositionAtCoordinate、getGlyphRangeForCharacterRange、getCharacterRangeForGlyphRange接口重载，以及TextEncoding枚举。

```TypeScript
// xxx.ets
import { LengthMetrics } from '@kit.ArkUI';
import { text } from '@kit.ArkGraphics2D';

const TEXT_CONTENT: string =
  '这是一段包含表情符号的测试文本\u{1F60A}。长按文字可查看渐变高亮效果\u{1F389}。\n' +
  '复杂表情符号\u{1F468}\u{200D}\u{1F469}\u{200D}\u{1F467}\u{200D}\u{1F466}也会被正确处理' +
  '\u{1F3F3}\u{FE0F}\u{200D}\u{1F308}，再来一些emoji\u{1F680}\u{1F31F}\u{1F4BB}和中文混排。\n' +
  '第三行：可以长按不同位置试试各种字符\u{1F600}\u{1F431}\u{1F409}。';

@Entry
@Component
struct Utf16GlyphHighlightPage {
  private textController: TextController = new TextController();
  private canvasContext: CanvasRenderingContext2D = new CanvasRenderingContext2D(new RenderingContextSettings(true));
  @State isCanvasReady: boolean = false;
  @State resultInfo: string = '长按下方文字（含表情符号）查看渐变背景高亮效果';

  aboutToAppear(): void {
    const styledString = new MutableStyledString(TEXT_CONTENT, [{
      start: 0, length: TEXT_CONTENT.length,
      styledKey: StyledStringKey.FONT,
      styledValue: new TextStyle({ fontSize: LengthMetrics.vp(24) })
    }]);
    this.textController.setStyledString(styledString);
  }

  build() {
    Column() {
      Text(this.resultInfo)
        .fontSize(13).fontColor('#666666')
        .padding({ left: 16, right: 16, top: 12, bottom: 8 })
        .margin({ left: 12, right: 12, top: 12 })
        .width('100%').height(110)
      Stack({ alignContent: Alignment.TopStart }) {
        Canvas(this.canvasContext).width('100%').height('100%')
          .onReady(() => { this.isCanvasReady = true; })
        Text(undefined, { controller: this.textController })
          .gesture(LongPressGesture({ repeat: false, duration: 500 })
            .onAction((event: GestureEvent) => { this.handleLongPress(event); }))
      }
      .layoutWeight(1).width('100%')
      .padding({ left: 16, right: 16, top: 12 })
      .margin({ left: 12, right: 12, bottom: 12 }).clip(true)
    }.height('100%').width('100%')
  }

  private handleLongPress(event: GestureEvent): void {
    // 处理流程：坐标转px -> getCharacterPositionAtCoordinate获取字符位置与亲和性 ->
    //           依亲和性确定字符范围 -> getGlyphRangeForCharacterRange获取字形范围与实际字符范围 ->
    //           getRectsForRange获取矩形区域 -> Canvas绘制渐变背景
    if (!this.isCanvasReady) { this.resultInfo = 'Canvas 尚未就绪，请稍后重试'; return; }
    const uiContext = this.getUIContext();
    // 获取文本布局管理对象，用于后续的字符位置/字形范围/矩形区域查询
    const layoutManager = this.textController.getLayoutManager();
    if (!layoutManager) { this.resultInfo = 'LayoutManager 不可用'; return; }
    const finger = event.fingerList[0];
    if (!finger) { this.resultInfo = '未获取到手指信息'; return; }
    // 将长按坐标从vp转换为px，供布局查询接口使用
    const localXPx = uiContext.vp2px(finger.localX);
    const localYPx = uiContext.vp2px(finger.localY);
    // 以UTF-16编码查询距离长按坐标最近的字符位置及亲和性
    const posAffinity = layoutManager.getCharacterPositionAtCoordinate(localXPx, localYPx, TextEncoding.TEXT_ENCODING_UTF16);
    if (!posAffinity) { this.resultInfo = 'getCharacterPositionAtCoordinate 返回 undefined'; return; }
    const index = posAffinity.position;
    const affinity = posAffinity.affinity;
    let charStart: number, charEnd: number;
    if (affinity === text.Affinity.UPSTREAM) {
      charStart = Math.max(0, index - 1); charEnd = index;
    } else {
      charStart = index; charEnd = index + 1;
    }
    // 根据字符范围查询对应的字形范围与实际字符范围（UTF-16编码）
    const glyphRanges = layoutManager.getGlyphRangeForCharacterRange(
      { start: charStart, end: charEnd }, TextEncoding.TEXT_ENCODING_UTF16);
    if (!glyphRanges || glyphRanges.length === 0) {
      this.resultInfo = `getGlyphRangeForCharacterRange 返回空, index=${index}, affinity=${affinity}`; return;
    }
    const actualRange: TextRange = glyphRanges.length >= 2 ? glyphRanges[1] : { start: charStart, end: charEnd };
    // 根据实际字符范围获取文本矩形区域，用于绘制高亮背景
    const textBoxes = layoutManager.getRectsForRange(actualRange, text.RectWidthStyle.TIGHT, text.RectHeightStyle.TIGHT);
    if (!textBoxes || textBoxes.length === 0) {
      this.resultInfo = `getRectsForRange 返回空, range=[${actualRange.start}, ${actualRange.end}]`; return;
    }
    this.drawGradientBackground(uiContext, textBoxes);
    const affinityStr = affinity === text.Affinity.UPSTREAM ? 'UPSTREAM(0)' : 'DOWNSTREAM(1)';
    this.resultInfo =
      `坐标: (${finger.localX.toFixed(1)}, ${finger.localY.toFixed(1)})vp\n` +
      `UTF16偏移: ${index}, 亲和性: ${affinityStr}\n` +
      `传入范围: [${charStart}, ${charEnd}] -> 实际字符范围: [${actualRange.start}, ${actualRange.end}]\n` +
      `矩形数: ${textBoxes.length}`;
  }

  private drawGradientBackground(uiContext: UIContext, textBoxes: TextBox[]): void {
    const ctx = this.canvasContext;
    ctx.clearRect(0, 0, 5000, 5000);
    for (const box of textBoxes) {
      const r = box.rect;
      const l = uiContext.px2vp(r.left), t = uiContext.px2vp(r.top);
      const w = uiContext.px2vp(r.right) - l, h = uiContext.px2vp(r.bottom) - t;
      if (w <= 0 || h <= 0) continue;
      const g = ctx.createLinearGradient(l, t, l + w, t + h);
      g.addColorStop(0, 'rgba(187, 153, 255, 0.66)');
      g.addColorStop(1, 'rgba(129, 229, 255, 0.66)');
      ctx.fillStyle = g;
      ctx.beginPath();
      ctx.roundRect(l, t, w, h, 4);
      ctx.fill();
    }
  }
}
```
