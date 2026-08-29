# Slider

滑动条组件，通常用于快速调节设置值，如音量调节、亮度调节等应用场景。支持样式定制、方向配置、交互方式和无障碍功能，能解决UI一致性问题，提升开发效率，从而改善用户体验并降低开发成本。
> **说明：**

## 子组件

无

## Slider

```TypeScript
Slider(options?: SliderOptions)
```

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SliderOptions](arkts-arkui-slideroptions-i.md) | 否 | 配置滑动条的参数。若不传入，则使用SliderOptions中各属性的默认值。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [ColorMetricsStop](arkts-arkui-colormetricsstop-i.md) | 线性渐变颜色断点类型，用于描述渐进色颜色断点。 |
| [SlideRange](arkts-arkui-sliderange-i.md) | 定义有效滑动区间。 |
| [SliderBlockStyle](arkts-arkui-sliderblockstyle-i.md) | Slider组件滑块形状参数。 |
| [SliderConfiguration](arkts-arkui-sliderconfiguration-i.md) | 开发者需要自定义class实现ContentModifier接口。继承自[CommonConfiguration](arkts-arkui-commonconfiguration-i.md)。 |
| [SliderCustomContentOptions](arkts-arkui-slidercustomcontentoptions-i.md) | Slider前后缀组件无障碍信息参数。 |
| [SliderOptions](arkts-arkui-slideroptions-i.md) | 滑动条的信息。 |
| [SliderPrefixOptions](arkts-arkui-sliderprefixoptions-i.md) | Slider前缀组件无障碍信息参数。 |
| [SliderShowStepOptions](arkts-arkui-slidershowstepoptions-i.md) | Slider刻度点的无障碍文本信息映射集。 |
| [SliderStepItemAccessibility](arkts-arkui-sliderstepitemaccessibility-i.md) | Slider刻度点的无障碍文本信息。 |
| [SliderSuffixOptions](arkts-arkui-slidersuffixoptions-i.md) | Slider后缀组件无障碍信息参数。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [SliderTriggerChangeCallback](arkts-arkui-slidertriggerchangecallback-t.md) | 定义SliderConfiguration中使用的回调类型。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [SliderBlockType](arkts-arkui-sliderblocktype-e.md) | Slider组件滑块形状枚举。 
| 名称 | 值 | 说明 | | ------- | -- | ---------------------- | | DEFAULT | 0 | 使用默认滑块（圆形）。 | | IMAGE | 1 | 使用图片资源作为滑块。 | | SHAPE | 2 | 使用自定义形状作为滑块。 | |
| [SliderChangeMode](arkts-arkui-sliderchangemode-e.md) | 滑块状态值，包括按下、拖动、离开、点击滑动条使滑块移动时。 |
| [SliderInteraction](arkts-arkui-sliderinteraction-e.md) | 用户与滑动条组件交互方式。 
| 名称 | 值 |说明 | | ------ | -- | ----------------------------- | | SLIDE_AND_CLICK | 0 | 用户可拖拽滑块或者点击滑轨使滑块移动，鼠标或手指按下即发生移动。| | SLIDE_ONLY | 1 | 禁止用户通过点击滑轨使滑块移动。| | SLIDE_AND_CLICK_UP | 2 |用户可拖拽滑块或者点击滑轨使滑块移动，当鼠标或手指抬起时，若与屏幕按压位置一致，则触发移动。| |
| [SliderStyle](arkts-arkui-sliderstyle-e.md) | 滑动条滑块在滑轨上显示的样式，样式说明请参考[Slider组件滑块与滑轨是如何对齐的](../../../ui/arkts-select-component-faq.md#slider组件滑块与滑轨是如何对齐的)。 |

## 示例

该示例通过配置style、showTips、showSteps控制气泡、刻度值、滑块和滑轨的显示。

```TypeScript
// xxx.ets
@Entry
@Component
struct SliderExample {
  @State outSetValueOne: number = 40;
  @State inSetValueOne: number = 40;
  @State noneValueOne: number = 40;
  @State outSetValueTwo: number = 40;
  @State inSetValueTwo: number = 40;
  @State vOutSetValueOne: number = 40;
  @State vInSetValueOne: number = 40;
  @State vOutSetValueTwo: number = 40;
  @State vInSetValueTwo: number = 40;

  build() {
    Column({ space: 8 }) {
      Text('outset slider').fontSize(9).fontColor(0xCCCCCC).width('90%').margin(15)
      Row() {
        Slider({
          value: this.outSetValueOne,
          min: 0,
          max: 100,
          style: SliderStyle.OutSet
        })
          .showTips(true)
          .onChange((value: number, mode: SliderChangeMode) => {
            this.outSetValueOne = value;
            console.info('value:' + value + 'mode:' + mode.toString());
          })
        // toFixed(0)将滑动条返回值处理为整数精度
        Text(this.outSetValueOne.toFixed(0)).fontSize(12)
      }
      .width('80%')
      Row() {
        Slider({
          value: this.outSetValueTwo,
          step: 10,
          style: SliderStyle.OutSet
        })
          .showSteps(true)
          .onChange((value: number, mode: SliderChangeMode) => {
            this.outSetValueTwo = value;
            console.info('value:' + value + 'mode:' + mode.toString());
          })
        Text(this.outSetValueTwo.toFixed(0)).fontSize(12)
      }
      .width('80%')

      Text('inset slider').fontSize(9).fontColor(0xCCCCCC).width('90%').margin(15)
      Row() {
        Slider({
          value: this.inSetValueOne,
          min: 0,
          max: 100,
          style: SliderStyle.InSet
        })
          .blockColor('#191970')
          .trackColor('#ADD8E6')
          .selectedColor('#4169E1')
          .showTips(true)
          .onChange((value: number, mode: SliderChangeMode) => {
            this.inSetValueOne = value;
            console.info('value:' + value + 'mode:' + mode.toString());
          })
        Text(this.inSetValueOne.toFixed(0)).fontSize(12)
      }
      .width('80%')
      Row() {
        Slider({
          value: this.inSetValueTwo,
          step: 10,
          style: SliderStyle.InSet
        })
          .blockColor('#191970')
          .trackColor('#ADD8E6')
          .selectedColor('#4169E1')
          .showSteps(true)
          .onChange((value: number, mode: SliderChangeMode) => {
            this.inSetValueTwo = value;
            console.info('value:' + value + 'mode:' + mode.toString());
          })
        Text(this.inSetValueTwo.toFixed(0)).fontSize(12)
      }
      .width('80%')

      Text('none slider').fontSize(9).fontColor(0xCCCCCC).width('90%').margin(15)
      Row() {
        Slider({
          value: this.noneValueOne,
          min: 0,
          max: 100,
          style: SliderStyle.NONE
        })
          .blockColor('#191970')
          .trackColor('#ADD8E6')
          .selectedColor('#4169E1')
          .showTips(true)
          .onChange((value: number, mode: SliderChangeMode) => {
            this.noneValueOne = value;
            console.info('value:' + value + 'mode:' + mode.toString());
          })
        Text(this.noneValueOne.toFixed(0)).fontSize(12)
      }
      .width('80%')

      Row() {
        Column() {
          Text('vertical outset slider').fontSize(9).fontColor(0xCCCCCC).width('50%').margin(15)
          Row() {
            Text().width('10%')
            Slider({
              value: this.vOutSetValueOne,
              style: SliderStyle.OutSet,
              direction: Axis.Vertical
            })
              .blockColor('#191970')
              .trackColor('#ADD8E6')
              .selectedColor('#4169E1')
              .showTips(true)
              .onChange((value: number, mode: SliderChangeMode) => {
                this.vOutSetValueOne = value;
                console.info('value:' + value + 'mode:' + mode.toString());
              })
            Slider({
              value: this.vOutSetValueTwo,
              step: 10,
              style: SliderStyle.OutSet,
              direction: Axis.Vertical
            })
              .blockColor('#191970')
              .trackColor('#ADD8E6')
              .selectedColor('#4169E1')
              .showSteps(true)
              .onChange((value: number, mode: SliderChangeMode) => {
                this.vOutSetValueTwo = value;
                console.info('value:' + value + 'mode:' + mode.toString());
              })
          }
        }.width('50%').height(300)

        Column() {
          Text('vertical inset slider').fontSize(9).fontColor(0xCCCCCC).width('50%').margin(15)
          Row() {
            Slider({
              value: this.vInSetValueOne,
              style: SliderStyle.InSet,
              direction: Axis.Vertical,
              reverse: true // 竖向Slider默认上端为min值，下端为max值。从下往上滑动需设置reverse为true
            })
              .showTips(true)
              .onChange((value: number, mode: SliderChangeMode) => {
                this.vInSetValueOne = value;
                console.info('value:' + value + 'mode:' + mode.toString());
              })
            Slider({
              value: this.vInSetValueTwo,
              step: 10,
              style: SliderStyle.InSet,
              direction: Axis.Vertical,
              reverse: true
            })
              .showSteps(true)
              .onChange((value: number, mode: SliderChangeMode) => {
                this.vInSetValueTwo = value;
                console.info('value:' + value + 'mode:' + mode.toString());
              })
          }
        }.width('50%').height(300)
      }
    }.width('100%')
  }
}
```

该示例通过blockBorderColor、blockSize、blockBorderWidth、blockStyle设置滑块的样式，通过stepSize、stepColor设置刻度值的样式，通过trackBorderRadius设置底板的圆角，通过selectedBorderRadius设置已滑动部分的圆角。

```TypeScript
@Entry
@Component
struct SliderExample {
  @State tipsValue: number = 40;

  build() {
    Column({ space: 8 }) {
      Text('block').fontSize(9).fontColor(0xCCCCCC).margin(15).width('90%')
      Slider({ style: SliderStyle.OutSet, value: 40 })
        .blockSize({ width: 40, height: 40 })
        .blockBorderColor(Color.Red)
        .blockBorderWidth(5)
      Divider()
      Text('step').fontSize(9).fontColor(0xCCCCCC).margin(15).width('90%')
      Slider({ style: SliderStyle.InSet, value: 40, step: 10 })
        .showSteps(true)
        .stepSize(8)
        .stepColor(Color.Yellow)
      Divider()
      Text('track').fontSize(9).fontColor(0xCCCCCC).margin(15).width('90%')
      Slider({ style: SliderStyle.InSet, value: 40 })
        .trackBorderRadius(2)
      Divider()
      Text('selected').fontSize(9).fontColor(0xCCCCCC).margin(15).width('90%')
      Slider({ style: SliderStyle.InSet, value: 40 })
        .selectedBorderRadius(2)
      Divider()
      Text('blockStyle').fontSize(9).fontColor(0xCCCCCC).margin(15).width('90%')
      Slider({ style: SliderStyle.OutSet, value: 40 })
        .blockStyle({ type: SliderBlockType.DEFAULT })
      Slider({ style: SliderStyle.OutSet, value: 40 })
        .blockStyle({ type: SliderBlockType.IMAGE, image: $r('sys.media.ohos_app_icon') })
      Slider({ style: SliderStyle.OutSet, value: 40 })
        .blockSize({ width: '60px', height: '60px' })
        .blockColor(Color.Red)
        .blockStyle({ type: SliderBlockType.SHAPE, shape: new Path({ commands: 'M60 60 M30 30 L15 56 L45 56 Z' }) })
      Divider()
      Text('tips').fontSize(9).fontColor(0xCCCCCC).margin(15).width('90%')
      Slider({ style: SliderStyle.InSet, value: this.tipsValue })
        .showTips(true, this.tipsValue.toFixed())
        .onChange(value => {
          this.tipsValue = value;
        })
    }
  }
}
```

通过样式Builder定制Slider组件内容区。点击增加按钮，进度条会按照原Slider设置的步长增加，反之点击减少按钮进度条会减少，并触发原组件的onChange事件。

```TypeScript
// xxx.ets

@Builder
function buildSlider(config: SliderConfiguration) {
  Row() {
    Column({ space: 30 }) {
      Progress({ value: config.value, total: config.max, type: ProgressType.Ring })
        .margin({ top: 20 })

      Button('增加')
        .onClick(() => {
          config.value = config.value + config.step;
          config.triggerChange(config.value, SliderChangeMode.Click);
        })
        .width(100)
        .height(25)
        .fontSize(10)
        .enabled(config.value < config.max)

      Button('减少')
        .onClick(() => {
          config.value = config.value - config.step;
          config.triggerChange(config.value, SliderChangeMode.Click);
        })
        .width(100)
        .height(25)
        .fontSize(10)
        .enabled(config.value > config.min)

      Slider({
        value: config.value,
        min: config.min,
        max: config.max,
        step: config.step,
      })
        .width(100)
        .visibility((config.contentModifier as MySliderStyle).showSlider ? Visibility.Visible : Visibility.Hidden)
        .showSteps(true)
        .onChange((value: number, mode: SliderChangeMode) => {
          config.triggerChange(value, mode);
        })
      Text('当前状态：' + ((config.contentModifier as MySliderStyle).sliderChangeMode == 0 ? "Begin"
        : ((config.contentModifier as MySliderStyle).sliderChangeMode == 1 ? "Moving"
          : ((config.contentModifier as MySliderStyle).sliderChangeMode == 2 ? "End"
            : ((config.contentModifier as MySliderStyle).sliderChangeMode == 3 ? "Click" : "无")))))
        .fontSize(10)
      Text('进度值：' + config.value)
        .fontSize(10)
      Text('最小值：' + config.min)
        .fontSize(10)
      Text('最大值：' + config.max)
        .fontSize(10)
      Text('步长：' + config.step)
        .fontSize(10)
    }
    .width('80%')

  }
  .width('100%')
}

class MySliderStyle implements ContentModifier<SliderConfiguration> {
  showSlider: boolean = true;
  sliderChangeMode: number = 0;

  constructor(showSlider: boolean, sliderChangeMode: number) {
    this.showSlider = showSlider;
    this.sliderChangeMode = sliderChangeMode;
  }

  applyContent(): WrappedBuilder<[SliderConfiguration]> {
    return wrapBuilder(buildSlider);
  }
}


@Entry
@Component
struct SliderExample {
  @State showSlider: boolean = true;
  @State sliderValue: number = 0;
  @State sliderMin: number = 10;
  @State sliderMax: number = 100;
  @State sliderStep: number = 20;
  @State sliderChangeMode: number = 0;

  build() {
    Column({ space: 8 }) {

      Row() {
        Slider({
          value: this.sliderValue,
          min: this.sliderMin,
          max: this.sliderMax,
          step: this.sliderStep,
        })
          .showSteps(true)
          .onChange((value: number, mode: SliderChangeMode) => {
            this.sliderValue = value;
            this.sliderChangeMode = mode;
            console.info('SliderLog value:' + value + 'mode:' + mode.toString());
          })
          .contentModifier(new MySliderStyle(this.showSlider, this.sliderChangeMode))

      }
      .width('100%')

    }.width('100%')
  }
}
```

该示例通过selectedColor设置滑动条渐变色，通过focusable、defaultFocus和focusOnTouch设置滑动条支持表冠操作。

```TypeScript
// xxx.ets
@Entry
@Component
struct SliderExample {
  @State inSetValueOne: number = 60
  @State colorGradient: LinearGradient = new LinearGradient([{ color: "#FF0000FF", offset: 0 }, { color: "#FFFF0000", offset: 1 }])
  @State sensitivity: CrownSensitivity | undefined | null = CrownSensitivity.MEDIUM
  scroller: Scroller = new Scroller()

  getIntegerDigits(num: number): string {
    let numRound = Math.round(num);
    return numRound.toString();
  }

  build() {
    Column() {
      Scroll(this.scroller){
        Column() {
          Row() {
            Stack({ alignContent: Alignment.Top }) {
              Slider({
                value: this.inSetValueOne,
                min: 0,
                max: 100,
                style: SliderStyle.NONE,
                direction: Axis.Vertical,
                reverse: true
              })
                .focusable(true)
                .defaultFocus(true)
                .focusOnTouch(true)
                .digitalCrownSensitivity(this.sensitivity)
                .trackColor("#26FFFFFF")
                .trackThickness(52)
                .selectedColor(this.colorGradient)
                .onChange((value: number, mode: SliderChangeMode) => {
                  this.inSetValueOne = value
                })
            }
            .height(233 - 66)
            .width(52)
            .margin({ top: 33, bottom: 33, left: 56 })
            Column() {
              Text('音量')
                .fontSize(19)
                .fontColor("#A9FFFFFF")
                .fontWeight(500)
                .textAlign(TextAlign.Start)
                .margin({ left: 20 })
              Row() {
                Text(this.getIntegerDigits(this.inSetValueOne))
                  .fontSize(52)
                  .fontColor("#FFFFFFFF")
                  .fontWeight(700)
                  .textAlign(TextAlign.Start)
                  .margin({ left: 20 })
                Text('%')
                  .fontSize(19)
                  .fontColor("#FFFFFFFF")
                  .fontWeight(500)
                  .textAlign(TextAlign.Start)
                  .margin({ left: 2 })
              }
            }.alignItems(HorizontalAlign.Start)
          }
          .width(233)
          .height(233)
          .borderRadius(116.5)
          .backgroundColor(Color.Black)
        }
      }
    }.width('100%')
  }
}
```

通过prefix、suffix属性设置滑动条的前后缀内容，定制其内容区以及无障碍属性。设置无障碍属性后，屏幕阅读器将以设置的无障碍内容进行朗读。

```TypeScript
// xxx.ets
import { ComponentContent } from '@kit.ArkUI';

class NodeParams {
  param: ResourceStr = ""

  constructor(param: ResourceStr) {
    this.param = param;
  }
}

@Builder
function textBuilder(params: NodeParams) {
  Text(params.param)
    .fontSize($r('sys.float.Caption_L'))
    .clip(true)
    .textAlign(TextAlign.Center)
    .fontColor(Color.Black)
}

@Entry
@Component
struct SliderExample {
  private pre: string = '低';
  private suf: string = '高';
  private uiContext: UIContext = this.getUIContext();

  private preNode1: ComponentContent<NodeParams> = new ComponentContent(this.uiContext, wrapBuilder(textBuilder), new NodeParams(this.pre));
  private sufNode1: ComponentContent<NodeParams> = new ComponentContent(this.uiContext, wrapBuilder(textBuilder), new NodeParams(this.suf));
  private preNode2: ComponentContent<NodeParams> = new ComponentContent(this.uiContext, wrapBuilder(textBuilder), new NodeParams(this.pre));
  private sufNode2: ComponentContent<NodeParams> = new ComponentContent(this.uiContext, wrapBuilder(textBuilder), new NodeParams(this.suf));
  private preNode3: ComponentContent<NodeParams> = new ComponentContent(this.uiContext, wrapBuilder(textBuilder), new NodeParams(this.pre));
  private sufNode3: ComponentContent<NodeParams> = new ComponentContent(this.uiContext, wrapBuilder(textBuilder), new NodeParams(this.suf));
  private preNode4: ComponentContent<NodeParams> = new ComponentContent(this.uiContext, wrapBuilder(textBuilder), new NodeParams(this.pre));
  private sufNode4: ComponentContent<NodeParams> = new ComponentContent(this.uiContext, wrapBuilder(textBuilder), new NodeParams(this.suf));
  private preNode5: ComponentContent<NodeParams> = new ComponentContent(this.uiContext, wrapBuilder(textBuilder), new NodeParams(this.pre));
  private sufNode5: ComponentContent<NodeParams> = new ComponentContent(this.uiContext, wrapBuilder(textBuilder), new NodeParams(this.suf));
  private preNode6: ComponentContent<NodeParams> = new ComponentContent(this.uiContext, wrapBuilder(textBuilder), new NodeParams(this.pre));
  private sufNode6: ComponentContent<NodeParams> = new ComponentContent(this.uiContext, wrapBuilder(textBuilder), new NodeParams(this.suf));

  build() {
    Column({ space: 8 }) {
      Text('outset slider').fontSize(9).fontColor(0xCCCCCC).width('90%').margin(15)
      Row() {
        Slider({
          value: 50,
          min: 0,
          max: 100,
          style: SliderStyle.OutSet
        })
          .showTips(true)
          .prefix(this.preNode1)
          .suffix(this.sufNode1)
      }
      .width('80%')

      Row() {
        Slider({
          value: 50,
          min: 0,
          max: 100,
          style: SliderStyle.OutSet
        })
          .showTips(true)
          .prefix(this.preNode3)
      }
      .width('80%')

      Row() {
        Slider({
          value: 50,
          min: 0,
          max: 100,
          style: SliderStyle.OutSet
        })
          .showTips(true)
          .suffix(this.sufNode3)
      }
      .width('80%')

      Text('inset slider').fontSize(9).fontColor(0xCCCCCC).width('90%').margin(15)
      Row() {
        Slider({
          value: 50,
          min: 0,
          max: 100,
          style: SliderStyle.InSet
        })
          .blockColor('#191970')
          .trackColor('#ADD8E6')
          .selectedColor('#4169E1')
          .showTips(true)
          .trackThickness(36)
          .prefix(this.preNode2)
          .suffix(this.sufNode2)
      }
      .width('80%')

      Row() {
        Slider({
          value: 50,
          min: 0,
          max: 100,
          style: SliderStyle.InSet
        })
          .blockColor('#191970')
          .trackColor('#ADD8E6')
          .selectedColor('#4169E1')
          .showTips(true)
          .trackThickness(36)
          .prefix(this.preNode4)
      }
      .width('80%')

      Row() {
        Slider({
          value: 50,
          min: 0,
          max: 100,
          style: SliderStyle.InSet
        })
          .blockColor('#191970')
          .trackColor('#ADD8E6')
          .selectedColor('#4169E1')
          .showTips(true)
          .trackThickness(36)
          .suffix(this.sufNode4)
      }
      .width('80%')

      Text('slider Show Step').fontSize(9).fontColor(0xCCCCCC).width('90%').margin(15)
      Row() {
        Slider({
          value: 50,
          min: 0,
          max: 100,
          step:10,
          style: SliderStyle.InSet
        })
          .blockColor('#191970')
          .trackColor('#ADD8E6')
          .selectedColor('#4169E1')
          .showTips(true)
          .trackThickness(36)
          .showSteps(true)
          .prefix(this.preNode5, {
            accessibilityText: 'prefixText',
            accessibilityDescription: 'prefixDescription',
            accessibilityLevel: 'auto',
            accessibilityGroup: true
          })
          .suffix(this.sufNode5, {
            accessibilityText: 'suffixText',
            accessibilityDescription: 'suffixDescription',
            accessibilityLevel: 'auto',
            accessibilityGroup: true
          })
      }
      .width('80%')

      Row() {
        Slider({
          value: 50,
          min: 0,
          max: 100,
          step:10,
          style: SliderStyle.InSet
        })
          .blockColor('#191970')
          .trackColor('#ADD8E6')
          .selectedColor('#4169E1')
          .showTips(true)
          .trackThickness(36)
          .showSteps(true)
          .prefix(this.preNode6, {
            accessibilityText: 'prefixText',
            accessibilityDescription: 'prefixDescription',
            accessibilityLevel: 'auto',
            accessibilityGroup: true
          })
      }
      .width('80%')
      
      Row() {
        Slider({
          value: 50,
          min: 0,
          max: 100,
          step:10,
          style: SliderStyle.InSet
        })
          .blockColor('#191970')
          .trackColor('#ADD8E6')
          .selectedColor('#4169E1')
          .showTips(true)
          .trackThickness(36)
          .showSteps(true)
          .suffix(this.sufNode6, {
            accessibilityText: 'suffixText',
            accessibilityDescription: 'suffixDescription',
            accessibilityLevel: 'auto',
            accessibilityGroup: true
          })
      }
      .width('80%')
    }.width('100%')
  }
}
```

通过[showSteps](arkts-arkui-slider-attribute.md#showsteps)属性设置刻度点的无障碍文本信息。设置后，屏幕阅读器将以设置的无障碍内容进行朗读。从API version 20开始，[showSteps](arkts-arkui-slider-attribute.md#showsteps)方法新增可选参数options。

```TypeScript
class SliderBlockBorderColorModifier1 implements AttributeModifier<SliderAttribute>{
  optionMaps:Map<number, SliderStepItemAccessibility> = new Map()
    .set(1, {text : '123123'})
    .set(2, {text : 'Slider无障碍文本'})
    .set(3, {text : $r('app.string.stepItemText')})
    .set(4, {text : '!@#$%^&*()'});
  applyNormalAttribute(instance: SliderAttribute): void {
    instance.showSteps(true, {stepsAccessibility: this.optionMaps})
  }
}
@Entry
@Component
struct SliderExample {
  @State show: boolean = true;
  @State optionMaps:Map<number, SliderStepItemAccessibility> = new Map();
  private  sliderModifier: SliderBlockBorderColorModifier1 =new SliderBlockBorderColorModifier1()
  aboutToAppear(){
    this.optionMaps.set(1, {text : '123123'})
    this.optionMaps.set(2, {text : 'Slider无障碍文本'})
    this.optionMaps.set(3, {text : $r('app.string.app_name')})
    this.optionMaps.set(4, {text : '!@#$%^&*()'})
    this.show = true;
  }
  build() {
    Column({ space: 8 }) {
      Text('This is an example for showSteps attribute').fontSize(15).fontColor(0x000000).margin(15).width('90%')
      Row() {
        Slider({
          style: SliderStyle.InSet,
          value: 20,
          step: 10,
          max: 50,
          min: 0,
          direction: Axis.Horizontal
        })
          .stepSize(8)
          .stepColor(Color.Yellow)
          .showSteps(true, {stepsAccessibility: this.optionMaps})
      }.width('80%').height(100)
      Divider()
      Text('This is an example for showSteps attribute with modifier').fontSize(15).fontColor(0x000000).margin(15)
        .width('90%')
      Row() {
        Slider({
          style: SliderStyle.InSet,
          value: 20,
          step: 10,
          max: 50,
          min: 0,
          direction: Axis.Horizontal
        })
          .stepSize(8)
          .stepColor(Color.Yellow)
          .attributeModifier(this.sliderModifier)
      }.width('80%').height(100)
      Divider()
    }
  }
}
```

从API version 11开始，将SliderOptions的value属性设置为[$$](../../../ui/state-management/arkts-two-way-sync.md)绑定的变量，实现数据同步。

```TypeScript
// xxx.ets
@Entry
@Component
struct SliderExample {
  @State valueWith$: number = 40
  @State valueWithout$: number = 40
  build() {
    Column({ space: 20 }) {
      Text("使用$$双向绑定: " + this.valueWith$)
      Slider({
        value: $$this.valueWith$,
        min: 0,
        max: 100,
      })

      Text("不使用$$双向绑定: " + this.valueWithout$)
      Slider({
        value: this.valueWithout$,
        min: 0,
        max: 100,
      })
    }
  }
}
```

通过blockColor属性设置滑块渐变色。

```TypeScript
@Entry
@Component
struct SliderExample {
  @State colorGradient: LinearGradient = new LinearGradient([{ color: "#FFFFFF", offset: 0 }, { color: "#007DFF", offset: 1 }])

  build() {
    Column({ space: 10 }) {
      Slider({
        style:SliderStyle.OutSet,
        min: 0,
        max: 100,
      })
        .blockColor(this.colorGradient)
        .blockSize({width:"50vp",height:"50vp"})
      Slider({
        style:SliderStyle.OutSet,
        min: 0,
        max: 100,
        reverse: true
      })
        .blockColor(this.colorGradient)
        .blockSize({width:"50vp",height:"50vp"})
      Slider({
        style:SliderStyle.InSet,
        min: 0,
        max: 100,
      })
        .blockColor(this.colorGradient)
        .blockSize({width:"50vp",height:"50vp"})
      Slider({
        style:SliderStyle.InSet,
        min: 0,
        max: 100,
        reverse: true
      })
        .blockColor(this.colorGradient)
        .blockSize({width:"50vp",height:"50vp"})
      Slider({
        style:SliderStyle.NONE,
        min: 0,
        max: 100,
      })
        .blockColor(this.colorGradient)
        .blockSize({width:"50vp",height:"50vp"})
      Slider({
        style:SliderStyle.NONE,
        min: 0,
        max: 100,
        reverse: true
      })
        .blockColor(this.colorGradient)
        .blockSize({width:"50vp",height:"50vp"})

      Row({ space: 20 }){
        Slider({
          style:SliderStyle.OutSet,
          min: 0,
          max: 100,
          direction:Axis.Vertical
        })
          .blockColor(this.colorGradient)
          .blockSize({width:"50vp",height:"50vp"})
        Slider({
          style:SliderStyle.OutSet,
          min: 0,
          max: 100,
          reverse: true,
          direction:Axis.Vertical
        })
          .blockColor(this.colorGradient)
          .blockSize({width:"50vp",height:"50vp"})
        Slider({
          style:SliderStyle.InSet,
          min: 0,
          max: 100,
          direction:Axis.Vertical
        })
          .blockColor(this.colorGradient)
          .blockSize({width:"50vp",height:"50vp"})
        Slider({
          style:SliderStyle.InSet,
          min: 0,
          max: 100,
          reverse: true,
          direction:Axis.Vertical
        })
          .blockColor(this.colorGradient)
          .blockSize({width:"50vp",height:"50vp"})
        Slider({
          style:SliderStyle.NONE,
          min: 0,
          max: 100,
          direction:Axis.Vertical
        })
          .blockColor(this.colorGradient)
          .blockSize({width:"50vp",height:"50vp"})
        Slider({
          style:SliderStyle.NONE,
          min: 0,
          max: 100,
          reverse: true,
          direction:Axis.Vertical
        })
          .blockColor(this.colorGradient)
          .blockSize({width:"50vp",height:"50vp"})
      }.height("50%")
    }.width("100%")

  }
}
```

从API version 23开始，新增trackColorMetrics接口。

```TypeScript
// xxx.ets
import { ColorMetrics } from '@kit.ArkUI';

@Entry
@Component
struct SliderExample {
  @State greenColor: ColorMetrics = ColorMetrics.colorWithSpace(ColorSpace.DISPLAY_P3, 0.0, 1.0, 0.0, 1);
  @State yellowColor: ColorMetrics = ColorMetrics.colorWithSpace(ColorSpace.DISPLAY_P3, 1.0, 1.0, 0.0, 1);
  @State inSetValueOne: number = 40;
  @State color: ColorMetricsLinearGradient =
    new ColorMetricsLinearGradient([{ color: this.greenColor, offset: 0 }, { color: this.yellowColor, offset: 1 }])

  build() {
    Column({ space: 8 }) {
      Slider({
        value: this.inSetValueOne,
        min: 0,
        max: 100,
        style: SliderStyle.InSet
      }).margin('10')
        .width('80%')
        .blockColor('#FF0000')
        .trackColorMetrics(this.color)
        .selectedColor('#4169E1')
        .showTips(true)
        .onChange((value: number, mode: SliderChangeMode) => {
          this.inSetValueOne = value;
          console.info('value:' + value + 'mode:' + mode.toString());
        })
    }.alignItems(HorizontalAlign.Center)
    .width('100%')
  }
}
```

从API版本26.0.0开始，新增systemMaterial接口。

```TypeScript
// xxx.ets
import { uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct SliderSystemMaterial {
  build() {
    RelativeContainer() {
      Slider({
        style: SliderStyle.InSet
      })
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center },
        })
        .systemMaterial(new uiMaterial.ImmersiveMaterial({
          style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
        }))
    }
    .height('100%')
    .width('100%')
    .backgroundColor(Color.Grey)
  }
}
```
