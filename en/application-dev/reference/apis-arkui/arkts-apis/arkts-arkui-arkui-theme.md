# @ohos.arkui.theme(Theme)

## Modules to Import

```TypeScript
import { Colors, CustomColors, Theme, ThemeControl, CustomTheme, CustomDarkColors } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [ThemeControl](arkts-arkui-arkui-theme-themecontrol-c.md) | Class ThemeControl provides the Theme management for whole Ability and pages. |

### Interfaces

| Name | Description |
| --- | --- |
| [Colors](arkts-arkui-arkui-theme-colors-i.md) | Defines the struct of Colors. |
| [CustomTheme](arkts-arkui-arkui-theme-customtheme-i.md) | Defines the struct of CustomTheme. |
| [Theme](arkts-arkui-arkui-theme-theme-i.md) | Defines the struct of Theme. |

### Types

| Name | Description |
| --- | --- |
| [CustomColors](arkts-arkui-customcolors-t.md) | Defines the struct of CustomColors. |
| [CustomDarkColors](arkts-arkui-customdarkcolors-t.md) | Defines the struct of CustomDarkColors. |

## Examples

### Example 1: Using setDefaultTheme

This example demonstrates how to use [ThemeControl](arkts-arkui-arkui-theme-themecontrol-c.md).[setDefaultTheme](arkts-arkui-arkui-theme-themecontrol-c.md#setdefaulttheme).





```TypeScript
import { CustomTheme, CustomColors, ThemeControl } from '@kit.ArkUI';
// Custom theme color
class BlueColors implements CustomColors {
  fontPrimary = '#FF707070'; // Level-1 text font color.
  backgroundPrimary = '#FF2787D9'; // Level-1 background color.
  brand = '#FFEEAAFF'; // Brand color.
}

class PageCustomTheme implements CustomTheme {
  colors?: CustomColors;

  constructor(colors: CustomColors) {
    this.colors = colors;
  }
}
// Create an instance.
const blueColorsTheme = new PageCustomTheme(new BlueColors());
// Call ThemeControl.setDefaultTheme before page build to set the default application style to blueColorsTheme.
ThemeControl.setDefaultTheme(blueColorsTheme);

@Entry
@Component
struct Index {

  build() {
    Row() {
      Column() {
        // Apply fontPrimary to the text color.
        Text('This is a piece of text.')
          .fontSize(30)
          .fontWeight(FontWeight.Bold)
          .margin('5%')
        // Apply backgroundPrimary to the QR code background color.
        QRCode('Hello')
          .width(100)
          .height(100)
        // Apply brand to the input box cursor color.
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

### Example 2: Setting Theme Colors for a Component

This example demonstrates how to use the brand, primary, onPrimary, and container attributes in Colors to set theme colors for a component.

The primary, onPrimary, and container attributes are added to Colors since API version 26.0.0.

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
