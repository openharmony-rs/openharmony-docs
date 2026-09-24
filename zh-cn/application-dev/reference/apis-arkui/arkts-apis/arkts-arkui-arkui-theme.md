# @ohos.arkui.theme(主题换肤)

## 导入模块

```TypeScript
import { Colors, CustomColors, Theme, ThemeControl, CustomTheme, CustomDarkColors } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ThemeControl](arkts-arkui-arkui-theme-themecontrol-c.md) | ThemeControl将自定义Theme应用于App组件内，实现App组件风格跟随Theme切换。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [Colors](arkts-arkui-arkui-theme-colors-i.md) | 主题颜色资源。 |
| [CustomTheme](arkts-arkui-arkui-theme-customtheme-i.md) | 自定义主题风格对象。 |
| [Theme](arkts-arkui-arkui-theme-theme-i.md) | 当前生效的主题风格对象，可从[onWillApplyTheme](../arkts-components/arkts-arkui-common-comp-basecustomcomponent-c.md#onwillapplytheme)中获取。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [CustomColors](arkts-arkui-customcolors-t.md) | 自定义主题颜色资源类型。 |
| [CustomDarkColors](arkts-arkui-customdarkcolors-t.md) | 自定义深色主题颜色资源类型。 |

## 示例

### 示例1（使用setDefaultTheme）

该示例主要演示[ThemeControl](arkts-arkui-arkui-theme-themecontrol-c.md).[setDefaultTheme](arkts-arkui-arkui-theme-themecontrol-c.md#setdefaulttheme)的使用。





```TypeScript
import { CustomTheme, CustomColors, ThemeControl } from '@kit.ArkUI';
// 自定义主题颜色
class BlueColors implements CustomColors {
  fontPrimary = '#FF707070'; // 一级文本字体颜色
  backgroundPrimary = '#FF2787D9'; // 一级背景颜色
  brand = '#FFEEAAFF'; // 品牌色
}

class PageCustomTheme implements CustomTheme {
  colors?: CustomColors;

  constructor(colors: CustomColors) {
    this.colors = colors;
  }
}
// 创建实例
const blueColorsTheme = new PageCustomTheme(new BlueColors());
// 在页面build之前执行ThemeControl.setDefaultTheme，设置App默认样式风格为blueColorsTheme。
ThemeControl.setDefaultTheme(blueColorsTheme);

@Entry
@Component
struct Index {

  build() {
    Row() {
      Column() {
        // 文本颜色应用fontPrimary
        Text('这是一段文本')
          .fontSize(30)
          .fontWeight(FontWeight.Bold)
          .margin('5%')
        // 二维码背景色应用backgroundPrimary
        QRCode('Hello')
          .width(100)
          .height(100)
        // 输入框光标颜色应用brand
        TextInput({placeholder: 'input your word...'})
          .width('80%')
          .height(40)
          .margin(20)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### 示例2（设置组件主题色）

该示例主要演示使用Colors中的brand、primary、onPrimary和container设置组件主题色。

从API版本26.0.0开始，Colors新增primary、onPrimary和container属性。

```TypeScript
import { CustomColors } from '@kit.ArkUI';

class AppColors implements CustomColors {
  brand?: ResourceColor;
  primary?: ResourceColor;
  onPrimary?: ResourceColor;
  container?: ResourceColor;

  constructor(brand?: ResourceColor, primary?: ResourceColor, onPrimary?: ResourceColor, container?: ResourceColor) {
    this.brand = brand;
    this.primary = primary;
    this.onPrimary = onPrimary;
    this.container = container;
  }
}

@Entry({ routeName: 'text' })
@Component
struct TextPage {
  @State appColors: AppColors = new AppColors(
    '#ff0000', '#0000ff', '#00ff00', '#ff00ff'
  );
  controller: TextClockController = new TextClockController();
  @State accumulateTime: number = 0;

  build() {
    WithTheme({
      theme: {
        colors: this.appColors
      }
    }) {
      Column({ space: 15 }) {
        Text('11:00:00')
          .fontWeight(FontWeight.Bold)
          .fontSize(30)

        TextClock({ timeZoneOffset: -8, controller: this.controller })
          .format('aa hh:mm:ss')
          .onDateChange((value: number) => {
            this.accumulateTime = value;
          })
          .margin(20)
          .fontSize(30)
          .fontWeight(FontWeight.Bold)
      }
      .width('100%')
      .margin({ top: 30 })
      .padding(16)
    }
  }
}
```
