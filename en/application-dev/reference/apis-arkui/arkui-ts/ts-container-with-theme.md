# WithTheme

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @fangzhiyuan1-->
<!--Designer: @fangzhiyuan1-->
<!--Tester: @gouyuanyuan-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=77dbe37290f6691d2779cf62e1218d62529d67d2 translatedAt=2026-08-21T02:29:36.246Z pushedAt=2026-08-22T07:32:34.497Z -->

The **WithTheme** component is used to customize the theme style for a specific part of an application page. It allows you to set the dark/light mode and custom colors for child components. When the global theme cannot meet the requirement for an independent style in a specific area, you can use this component to implement partial skinning or independent theme style customization without affecting other areas.

> **NOTE**
>
> - This component is supported since API version 12. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.
>
> - **WithTheme** supports the following system components: [TextInput](./ts-basic-components-textinput.md), [Search](./ts-basic-components-search.md), [Button](./ts-basic-components-button.md), [Badge](./ts-container-badge.md), [Swiper](./ts-container-swiper.md), [Text](./ts-basic-components-text.md), [Select](./ts-basic-components-select.md), [Menu](./ts-basic-components-menu.md), [TimePicker](./ts-basic-components-timepicker.md), [DatePicker](./ts-basic-components-datepicker.md), [TextPicker](./ts-basic-components-textpicker.md), [Checkbox](./ts-basic-components-checkbox.md), [CheckboxGroup](./ts-basic-components-checkboxgroup.md), [Radio](./ts-basic-components-radio.md), [Slider](./ts-basic-components-slider.md), [Progress](./ts-basic-components-progress.md), [QRCode](./ts-basic-components-qrcode.md), [Toggle](./ts-basic-components-toggle.md), [TextClock](./ts-basic-components-textclock.md), [PatternLock](./ts-basic-components-patternlock.md), and [Divider](./ts-basic-components-divider.md). Since API version 26.0.0, the following components are added: [CalendarPicker](./ts-basic-components-calendarpicker.md), [UIPickerComponent](./ts-container-ui-picker-component.md), [TextArea](./ts-basic-components-textarea.md), [styled string](./ts-universal-styled-string.md), [Gauge](./ts-basic-components-gauge.md), [DataPanel](./ts-basic-components-datapanel.md), [RichEditor](./ts-basic-components-richeditor.md), [MenuItem](./ts-basic-components-menuitem.md), [MenuItemGroup](./ts-basic-components-menuitemgroup.md), [Image](./ts-basic-components-image.md), [ImageAnimator](./ts-basic-components-imageanimator.md), [Counter](./ts-container-counter.md), [bindSheet](./ts-universal-attributes-sheet-transition.md#bindsheet), and [LoadingProgress](./ts-basic-components-loadingprogress.md).
>
> - For usage guidelines of **WithTheme**, see [Setting In-App Theme Skinning](../../../ui/theme_skinning.md).

## Child Components

This component supports only one child component.

## APIs

WithTheme(options: WithThemeOptions)

Sets a custom theme style for specific application pages.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name                           | Type                                 | Mandatory | Description    |
|--------------------------------|---------------------------------------|-----|---------------|
| options | [WithThemeOptions](#withthemeoptions) | Mandatory | Used to configure the theme colors and dark/light mode of components within the **WithTheme** scope. For the supported components, see the component list in the preceding description. |

## Attributes

The [universal attributes](ts-component-general-attributes.md) are not supported.

## Events

The [universal events](ts-component-general-events.md) are not supported.

## WithThemeOptions

Sets the theme colors and dark/light mode for components within the **WithTheme** scope.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name       | Type                              | Read-Only | Optional| Description               |
|------------------------|---------------------------------------------------------| ---- | ---- |------------------------------------------------------------------|
| theme     | [CustomTheme](#customtheme)    | No | Yes  | Used to set the custom theme colors of components within the scope of WithTheme.<br/>Default value: **undefined**, which means the default colors follow the system [token default styles](../../../ui/theme_skinning.md#system-default-token-color-values). |
| colorMode | [ThemeColorMode](ts-universal-attributes-foreground-blur-style.md#themecolormode) | No | Yes  | Used to specify the dark/light mode of the component colors within the scope of WithTheme. Value rules: **ThemeColorMode.SYSTEM** follows the system dark/light mode settings, **ThemeColorMode.DARK** forces the dark mode, and **ThemeColorMode.LIGHT** forces the light mode. When setting the dark/light mode, a dark.json resource file must be added for the setting to take effect.<br/>Default value: **ThemeColorMode.SYSTEM** |

## CustomTheme

type CustomTheme = import('../api/@ohos.arkui.theme').CustomTheme

Customizes the color scheme of components within the **WithTheme** scope. The specific color items are configured through the **CustomColors** interface.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type    | Description      |
| ------ | ---------- |
| import('../api/@ohos.arkui.theme').[CustomTheme](../js-apis-arkui-theme.md#customtheme)  | Customizes the default theme colors of components within the **WithTheme** scope. |

## Examples

When setting the partial dark/light mode, you need to add the dark.json resource file for the dark/light mode to take effect.

![resources_dark](figures/resources_dark.png)

Example of the **dark.json** file content:

  ```json
    {
      "color": [
        {
          "name": "start_window_background",
          "value": "#000000"
        }
      ]
    }
  ```

### Example 1: Setting the Local Color Mode

```ts
// Set the local color mode.
@Entry
@Component
struct Index {
  build() {
    Column() {
    // System default
      Column() {
        Text('WithTheme not used')
          .fontSize(40)
          .fontWeight(FontWeight.Bold)
      }
      .justifyContent(FlexAlign.Center)
      .width('100%')
      .height('33%')
      .backgroundColor($r('app.color.start_window_background'))
      // Set the component to the dark mode.
      WithTheme({ colorMode: ThemeColorMode.DARK }) {
        Column() {
          Text('WithTheme')
            .fontSize(40)
            .fontWeight(FontWeight.Bold)
          Text('DARK')
            .fontSize(40)
            .fontWeight(FontWeight.Bold)
        }
        .justifyContent(FlexAlign.Center)
        .width('100%')
        .height('33%')
        .backgroundColor($r('sys.color.background_primary'))
      }
      // Set the component to the light mode.
      WithTheme({ colorMode: ThemeColorMode.LIGHT }) {
        Column() {
          Text('WithTheme')
            .fontSize(40)
            .fontWeight(FontWeight.Bold)
          Text('LIGHT')
            .fontSize(40)
            .fontWeight(FontWeight.Bold)
        }
        .justifyContent(FlexAlign.Center)
        .width('100%')
        .height('33%')
        .backgroundColor($r('sys.color.background_primary'))
      }
    }
    .height('100%')
    .expandSafeArea([SafeAreaType.SYSTEM], [SafeAreaEdge.TOP, SafeAreaEdge.END, SafeAreaEdge.BOTTOM, SafeAreaEdge.START])
  }
}
```

![withThemeColorMode](figures/witheThemeColorMode.png)

### Example 2: Customizing the Default Colors of Components Within the WithTheme Scope

```ts
// Customize the theme for components in the WithTheme scope.
import { CustomTheme, CustomColors } from '@kit.ArkUI';

class GreenColors implements CustomColors {
  fontPrimary = '#ff049404';
  fontEmphasize = '#FF00541F';
  fontOnPrimary = '#FFFFFFFF';
  compBackgroundTertiary = '#1111FF11';
  backgroundEmphasize = '#FF00541F';
  compEmphasizeSecondary = '#3322FF22';
}

class RedColors implements CustomColors {
  fontPrimary = '#fff32b3c';
  fontEmphasize = '#FFD53032';
  fontOnPrimary = '#FFFFFFFF';
  compBackgroundTertiary = '#44FF2222';
  backgroundEmphasize = '#FFD00000';
  compEmphasizeSecondary = '#33FF1111';
}

class PageCustomTheme implements CustomTheme {
  colors?: CustomColors;

  constructor(colors: CustomColors) {
    this.colors = colors;
  }
}

@Entry
@Component
struct IndexPage {
  static readonly themeCount = 3;
  themeNames: string[] = ['System', 'Custom (green)', 'Custom (red)'];
  themeArray: (CustomTheme | undefined)[] = [
    undefined, // System
    new PageCustomTheme(new GreenColors()),
    new PageCustomTheme(new RedColors())
  ];
  @State themeIndex: number = 0;

  build() {
    Column() {
      Column({ space: '8vp' }) {
        Text('Without WithTheme')
        // Click the button to change the theme.
        Button(`Switch Theme: ${this.themeNames[this.themeIndex]}`)
          .onClick(() => {
            this.themeIndex = (this.themeIndex + 1) % IndexPage.themeCount;
          })

        // Default button color
        Button('Button.style(NORMAL) with System Theme')
          .buttonStyle(ButtonStyleMode.NORMAL)
        Button('Button.style(EMP..ED) with System Theme')
          .buttonStyle(ButtonStyleMode.EMPHASIZED)
        Button('Button.style(TEXTUAL) with System Theme')
          .buttonStyle(ButtonStyleMode.TEXTUAL)
      }
      .margin({
        top: '50vp'
      })

      WithTheme({ theme: this.themeArray[this.themeIndex] }) {
        // WithTheme scope
        Column({ space: '8vp' }) {
          Text('Using WithTheme')
          Button('Button.style(NORMAL) with Custom Theme')
            .buttonStyle(ButtonStyleMode.NORMAL)
          Button('Button.style(EMP..ED) with Custom Theme')
            .buttonStyle(ButtonStyleMode.EMPHASIZED)
          Button('Button.style(TEXTUAL) with Custom Theme')
            .buttonStyle(ButtonStyleMode.TEXTUAL)
        }
        .width('100%')
      }
    }
  }
}
```

![withThemeSystem](figures/withThemeChangeTheme.gif)