# Slider

The **Slider** component is used to quickly adjust settings, such as the volume and brightness.

> **NOTE**

## Child Components

Not supported

## Slider

```TypeScript
Slider(options?: SliderOptions)
```

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [SliderOptions](arkts-arkui-slider-comp-slideroptions-i.md) | No | Parameters of the slider. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [ColorMetricsStop](arkts-arkui-slider-comp-colormetricsstop-i.md) | Describes the breakpoint of the gradient color. |
| [SlideRange](arkts-arkui-slider-comp-sliderange-i.md) | Defines the callback type used in **SlideRange**. |
| [SliderBlockStyle](arkts-arkui-slider-comp-sliderblockstyle-i.md) | Describes the style of the slider in the block direction. |
| [SliderConfiguration](arkts-arkui-slider-comp-sliderconfiguration-i.md) | You need a custom class to implement the **ContentModifier** API. Inherits from [CommonConfiguration](arkts-arkui-common-comp-commonconfiguration-i.md). |
| [SliderCustomContentOptions](arkts-arkui-slider-comp-slidercustomcontentoptions-i.md) | Provides accessibility configuration of the slider prefix and suffix. |
| [SliderOptions](arkts-arkui-slider-comp-slideroptions-i.md) | Provides information about the slider. |
| [SliderPrefixOptions](arkts-arkui-slider-comp-sliderprefixoptions-i.md) | Provides accessibility configuration of the slider prefix. |
| [SliderShowStepOptions](arkts-arkui-slider-comp-slidershowstepoptions-i.md) | Provides accessibility text mapping for the slider step markers. |
| [SliderStepItemAccessibility](arkts-arkui-slider-comp-sliderstepitemaccessibility-i.md) | Provides accessibility configuration of the slider step markers. |
| [SliderSuffixOptions](arkts-arkui-slider-comp-slidersuffixoptions-i.md) | Provides accessibility configuration of the slider suffix. |

### Types

| Name | Description |
| --- | --- |
| [SliderTriggerChangeCallback](arkts-arkui-slider-comp-slidertriggerchangecallback-t.md) | Defines the callback type used in **SliderConfiguration**. |

### Enums

| Name | Description |
| --- | --- |
| [SliderBlockType](arkts-arkui-slider-comp-sliderblocktype-e.md) | Enumerates the types of the slider in the block direction. |
| [SliderChangeMode](arkts-arkui-slider-comp-sliderchangemode-e.md) | Enumerates the slider states. |
| [SliderInteraction](arkts-arkui-slider-comp-sliderinteraction-e.md) | Interaction mode between the user and the slider. |
| [SliderStyle](arkts-arkui-slider-comp-sliderstyle-e.md) | Enumerates the display styles of the slider thumb relative to the track. For details, see [How Are the Slider Thumb and Track of the Slider Component Aligned?](../../../ui/arkts-select-component-faq.md#how-are-the-slider-thumb-and-track-of-the-slider-component-aligned). |

## Examples

### Example 1: Using Basic Slider Styles

This example demonstrates how to control the display of the tooltip, current step, and slider thumb and track by configuring style, showTips, and showSteps.



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
        // toFixed(0) converts the return value of the slider to an integer.
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
              reverse: true // For a vertical slider, the top end is the min value and the bottom end is the max value by default. To slide from bottom to top, set reverse to true.
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

### Example 2: Using Custom Slider Styles

This example demonstrates how to customize the slider styles by setting blockBorderColor, blockSize, blockBorderWidth, and blockStyle for the slider block, stepSize and stepColor for the step, trackBorderRadius for the track's corner radius, and selectedBorderRadius for the selected part's corner radius.



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

### Example 3: Implementing a Custom Slider

This example demonstrates how to customize the Slider component using a style builder to define the content area. Clicking the increase button will increment the progress bar by the step size set in the original Slider component, and clicking the decrease button will decrement the progress bar, triggering the onChange event of the original component.



```TypeScript
// xxx.ets

@Builder
function buildSlider(config: SliderConfiguration) {
  Row() {
    Column({ space: 30 }) {
      Progress({ value: config.value, total: config.max, type: ProgressType.Ring })
        .margin({ top: 20 })

      Button('Increase')
        .onClick(() => {
          config.value = config.value + config.step;
          config.triggerChange(config.value, SliderChangeMode.Click);
        })
        .width(100)
        .height(25)
        .fontSize(10)
        .enabled(config.value < config.max)

      Button('Decrease')
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
      Text('Current state: ' + ((config.contentModifier as MySliderStyle).sliderChangeMode == 0 ? "Begin"
        : ((config.contentModifier as MySliderStyle).sliderChangeMode == 1 ? "Moving"
          : ((config.contentModifier as MySliderStyle).sliderChangeMode == 2 ? "End"
            : ((config.contentModifier as MySliderStyle).sliderChangeMode == 3 ? "Click" : "None")))))
        .fontSize(10)
      Text('Progress: ' + config.value)
        .fontSize(10)
      Text('Min: ' + config.min)
        .fontSize(10)
      Text('Max: ' + config.max)
        .fontSize(10)
      Text('Step: ' + config.step)
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

### Example 4: Applying a Color Gradient Effect and Implementing Support for Digital Crown Interactions

This example demonstrates how to set a color gradient effect to the slider using selectedColor and implement support for digital crown interactions through focusable, defaultFocus, and focusOnTouch.



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
              Text('Volume')
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

### Example 5: Setting the Slider Prefix and Suffix

This example demonstrates how to set the prefix and suffix of the slider using prefix and suffix, defining their custom content and accessibility configuration. After the accessibility configuration is specified, the screen reader announces the accessibility text accordingly.



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
  private pre: string = 'Low';
  private suf: string = 'High';
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

### Example 6: Setting Accessibility Text for Slider Step Markers

This example demonstrates how to set accessibility text for step markers using [showSteps](arkts-arkui-slider-comp-attribute.md#showsteps). The screen reader announces the set accessibility text accordingly. The options parameter is added for the [showSteps](arkts-arkui-slider-comp-attribute.md#showsteps) attribute since API version 20.



```TypeScript
class SliderBlockBorderColorModifier1 implements AttributeModifier<SliderAttribute>{
  optionMaps:Map<number, SliderStepItemAccessibility> = new Map()
    .set(1, {text : '123123'})
    .set(2, {text : 'Slider accessibility text'})
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
    this.optionMaps.set(2, {text : 'Slider accessibility text'})
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

### Example 7: Setting Two-Way Binding for the Slider

This example shows how to implement data synchronization by binding the value property of [SliderOptions](arkts-arkui-slider-comp-slideroptions-i.md) to a variable using the [$$](../../../ui/state-management/arkts-two-way-sync.md) two-way binding operator, available since API version 11.



```TypeScript
// xxx.ets
@Entry
@Component
struct SliderExample {
  @State valueWith$: number = 40
  @State valueWithout$: number = 40
  build() {
    Column({ space: 20 }) {
      Text("Using $$ two-way binding: " + this.valueWith$)
      Slider({
        value: $$this.valueWith$,
        min: 0,
        max: 100,
      })

      Text("Without $$ two-way binding: " + this.valueWithout$)
      Slider({
        value: this.valueWithout$,
        min: 0,
        max: 100,
      })
    }
  }
}
```

### Example 8: Setting a Gradient Color for the Slider Thumb

This example demonstrates how to set a gradient color for the Slider component's thumb using the blockColor attribute.



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

### Example 9: Setting the Background Color of a Slider

This example demonstrates how to set the gradient color stop of the specified color gamut using [trackColorMetrics](arkts-arkui-slider-comp-attribute.md#trackcolormetrics). In this example, colorSpace is of the ColorSpace.DISPLAY_P3 type. You need to call the setWindowColorSpace API of the corresponding window to set the current window to the wide color gamut mode. For details, see [setWindowColorSpace](../arkts-apis-window-Window.md#setwindowcolorspace).

The trackColorMetrics API is supported since API version 23.



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

### Example 10: Setting the Immersive Light Effect for the Slider

This example shows how to set the system material of the slider using the universal attribute [systemMaterial](ts-universal-attributes-image-effect.md#systemmaterial), implementing the immersive light effect. After the system material is set, a particle animation effect is generated during the sliding of the slider.

The immersive light effect of the component is adaptively adjusted based on the device computing power and the immersive light effect set by the user in the system, and you do not need to perform additional adaptation.

The systemMaterial API is supported since API version 26.0.0.

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
    // Replace it with the actual resource file.
    .backgroundImage($r("app.media.img"))
  }
}
```
