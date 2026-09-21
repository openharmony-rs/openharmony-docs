# @ohos.arkui.advanced.ArcSlider

## 导入模块

```TypeScript
import { ArcSlider, ArcSliderPosition, ArcSliderOptions, ArcSliderOptionsConstructorOptions, ArcSliderLayoutOptions, ArcSliderLayoutOptionsConstructorOptions, ArcSliderStyleOptions, ArcSliderStyleOptionsConstructorOptions, ArcSliderValueOptions, ArcSliderValueOptionsConstructorOptions } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ArcSliderLayoutOptions](arkts-arkui-arkui-advanced-arcslider-arcsliderlayoutoptions-c.md) | 配置弧形Slider的布局信息。 |
| [ArcSliderOptions](arkts-arkui-arkui-advanced-arcslider-arcslideroptions-c.md) | 配置弧形Slider的信息。 |
| [ArcSliderStyleOptions](arkts-arkui-arkui-advanced-arcslider-arcsliderstyleoptions-c.md) | 配置弧形Slider的样式信息。 |
| [ArcSliderValueOptions](arkts-arkui-arkui-advanced-arcslider-arcslidervalueoptions-c.md) | 配置弧形Slider的数值信息。 |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [ArcSlider](arkts-arkui-arkui-advanced-arcslider-arcslider-s.md) | 弧形滑动条组件，通常用于在圆形屏幕的穿戴设备中快速调节设置值，如音量调节、亮度调节等应用场景。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ArcSliderLayoutOptionsConstructorOptions](arkts-arkui-arkui-advanced-arcslider-arcsliderlayoutoptionsconstructoroptions-i.md) | ArcSliderLayoutOptions的构造信息。 |
| [ArcSliderOptionsConstructorOptions](arkts-arkui-arkui-advanced-arcslider-arcslideroptionsconstructoroptions-i.md) | ArcSliderOptions的构造信息。 |
| [ArcSliderStyleOptionsConstructorOptions](arkts-arkui-arkui-advanced-arcslider-arcsliderstyleoptionsconstructoroptions-i.md) | ArcSliderStyleOptions的构造信息。 |
| [ArcSliderValueOptionsConstructorOptions](arkts-arkui-arkui-advanced-arcslider-arcslidervalueoptionsconstructoroptions-i.md) | ArcSliderValueOptions的构造信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ArcSliderPosition](arkts-arkui-arkui-advanced-arcslider-arcsliderposition-e.md) | 配置弧形Slider的屏幕显示位置。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ArcSliderChangeHandler](arkts-arkui-arcsliderchangehandler-t.md) | 弧形Slider的进度值发生变化时触发回调。 |
| [ArcSliderEnlargeHandler](arkts-arkui-arcsliderenlargehandler-t.md) | 弧形Slider放大或缩小时触发回调。 |
| [ArcSliderTouchHandler](arkts-arkui-arcslidertouchhandler-t.md) | 弧形Slider被触摸时触发回调。 |

## 示例

从API version 18开始，该示例展示了ArcSlider组件的基本用法。

```TypeScript
// xxx.ets
import {
  ArcSlider,
  ArcSliderPosition,
  ArcSliderOptions,
  ArcSliderValueOptions,
  ArcSliderLayoutOptions,
  ArcSliderStyleOptions,
  ArcSliderValueOptionsConstructorOptions,
  ArcSliderLayoutOptionsConstructorOptions,
  ArcSliderStyleOptionsConstructorOptions,
  ArcSliderOptionsConstructorOptions
} from '@kit.ArkUI';

@Entry
@ComponentV2
struct ArcSliderExample {
  valueOptionsConstructorOptions: ArcSliderValueOptionsConstructorOptions = {
    progress: 60,
    min: 10,
    max: 110
  };

  layoutOptionsConstructorOptions: ArcSliderLayoutOptionsConstructorOptions = {
    reverse: true,
    position: ArcSliderPosition.RIGHT
  };
  styleOptionsConstructorOptions: ArcSliderStyleOptionsConstructorOptions = {
    trackThickness: 8,
    activeTrackThickness: 30,
    trackColor: '#ffd5d5d5',
    selectedColor: '#ff2787d9',
    trackBlur: 20
  };
  valueOptions: ArcSliderValueOptions = new ArcSliderValueOptions(this.valueOptionsConstructorOptions);
  layoutOptions: ArcSliderLayoutOptions = new ArcSliderLayoutOptions(this.layoutOptionsConstructorOptions);
  styleOptions: ArcSliderStyleOptions = new ArcSliderStyleOptions(this.styleOptionsConstructorOptions);
  // 配置ArcSlider完整选项：数值、布局、样式、表冠灵敏度以及触摸/变化/放大事件回调
  arcSliderOptionsConstructorOptions: ArcSliderOptionsConstructorOptions = {
    valueOptions: this.valueOptions,
    layoutOptions: this.layoutOptions,
    styleOptions: this.styleOptions,
    digitalCrownSensitivity: CrownSensitivity.LOW,
    onTouch: (event: TouchEvent) => {
      // ...
    },
    onChange: (progress: number) => {
      // ...
    },
    onEnlarge: (isEnlarged: boolean) => {
      // ...
    }
  };
  arcSliderOptions: ArcSliderOptions = new ArcSliderOptions(this.arcSliderOptionsConstructorOptions);

  build() {
    Column() {
      // 创建ArcSlider组件，传入配置选项
      ArcSlider({ options: this.arcSliderOptions })
    }
    .width('100%')
  }
}
```
