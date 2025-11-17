# @ohos.arkui.theme (Theme)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @lushi871202-->
<!--Designer: @lushi871202-->
<!--Tester: @sally__-->
<!--Adviser: @HelloCrease-->

You can define a custom theme to apply to components in your application.

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { Theme, ThemeControl, CustomColors, Colors, CustomTheme, CustomDarkColors } from '@kit.ArkUI';
```

## Theme

Defines the **Theme** object in use, which can be obtained through [onWillApplyTheme](arkui-ts/ts-custom-component-lifecycle.md#onwillapplytheme12).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type               | Read Only| Optional| Description      |
| ------ |-------------------|-----|-----|----------|
| colors | [Colors](#colors) | No  | No  |  Color resources of the theme.|

## Colors

Defines the color resources of a theme.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

<!--RP1--><!--RP1End-->

| Name                          | Type                                                | Read Only| Optional| Description              |
|-------------------------------|-----------------------------------------------------|-----|-----|------------------|
| brand                         | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Brand color.<br>Affected components: [TextInput](./arkui-ts/ts-basic-components-textinput.md), [Search](./arkui-ts/ts-basic-components-search.md)       |
| warning                       | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Warning color.<br>Affected components: [TipsDialog](./arkui-ts/ohos-arkui-advanced-Dialog.md#tipsdialog), [AlertDialog](./arkui-ts/ohos-arkui-advanced-Dialog.md#alertdialog), [CustomContentDialog](./arkui-ts/ohos-arkui-advanced-Dialog.md#customcontentdialog12),<br>[Badge](./arkui-ts/ts-container-badge.md), [Button](./arkui-ts/ts-basic-components-button.md)         |
| alert                         | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Alert color.<br>Affected components: None          |
| confirm                       | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Confirmation color.<br>Affected components: None            |
| fontPrimary                   | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Primary font color.<br>Affected components: [EditableTitleBar](./arkui-ts/ohos-arkui-advanced-EditableTitleBar.md), [LoadingDialog](./arkui-ts/ohos-arkui-advanced-Dialog.md#loadingdialog) and [TipsDialog](./arkui-ts/ohos-arkui-advanced-Dialog.md#tipsdialog)<br>[ConfirmDialog](./arkui-ts/ohos-arkui-advanced-Dialog.md#confirmdialog), [AlertDialog](./arkui-ts/ohos-arkui-advanced-Dialog.md#alertdialog), [SelectDialog](./arkui-ts/ohos-arkui-advanced-Dialog.md#selectdialog),<br>[CustomContentDialog](./arkui-ts/ohos-arkui-advanced-Dialog.md#customcontentdialog12), [Swiper](./arkui-ts/ts-container-swiper.md), [Text](./arkui-ts/ts-basic-components-text.md),<br>[SubHeader](./arkui-ts/ohos-arkui-advanced-SubHeader.md), [ProgressButton](./arkui-ts/ohos-arkui-advanced-ProgressButton.md), [AlphabetIndexer](./arkui-ts/ts-container-alphabet-indexer.md),<br>[Popup](./arkui-ts/ohos-arkui-advanced-Popup.md), [Select](./arkui-ts/ts-basic-components-select.md), [Chip](./arkui-ts/ohos-arkui-advanced-Chip.md),<br>[ToolBar](./arkui-ts/ohos-arkui-advanced-ToolBar.md), [Menu](./arkui-ts/ts-basic-components-menu.md), [TextInput](./arkui-ts/ts-basic-components-textinput.md),<br>[Search](./arkui-ts/ts-basic-components-search.md), [Counter](./arkui-ts/ts-container-counter.md), [TimePicker](./arkui-ts/ts-basic-components-timepicker.md), [DatePicker](./arkui-ts/ts-basic-components-datepicker.md),<br>[TextPicker](./arkui-ts/ts-basic-components-textpicker.md), [ComposeListItem](./arkui-ts/ohos-arkui-advanced-ComposeListItem.md), [TreeView](./arkui-ts/ohos-arkui-advanced-TreeView.md)       |
| fontSecondary                 | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Secondary font color.<br>Affected components: [EditableTitleBar](./arkui-ts/ohos-arkui-advanced-EditableTitleBar.md), [AlertDialog](./arkui-ts/ohos-arkui-advanced-Dialog.md#alertdialog), [CustomContentDialog](./arkui-ts/ohos-arkui-advanced-Dialog.md#customcontentdialog12),<br>[SubHeader](./arkui-ts/ohos-arkui-advanced-SubHeader.md), [AlphabetIndexer](./arkui-ts/ts-container-alphabet-indexer.md), [Popup](./arkui-ts/ohos-arkui-advanced-Popup.md),<br>[TextInput](./arkui-ts/ts-basic-components-textinput.md), [Search](./arkui-ts/ts-basic-components-search.md), [ComposeListItem](./arkui-ts/ohos-arkui-advanced-ComposeListItem.md),<br>[TreeView](./arkui-ts/ohos-arkui-advanced-TreeView.md)        |
| fontTertiary                  | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Tertiary font color.<br>Affected components: [ComposeListItem](./arkui-ts/ohos-arkui-advanced-ComposeListItem.md)       |
| fontFourth                    | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Fourth-level font color.<br>Affected components: None       |
| fontEmphasize                 | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Emphasis font color.<br>Affected components: [TipsDialog](./arkui-ts/ohos-arkui-advanced-Dialog.md#tipsdialog), [ConfirmDialog](./arkui-ts/ohos-arkui-advanced-Dialog.md#confirmdialog) and [AlertDialog](./arkui-ts/ohos-arkui-advanced-Dialog.md#alertdialog)<br>[SelectDialog](./arkui-ts/ohos-arkui-advanced-Dialog.md#selectdialog), [CustomContentDialog](./arkui-ts/ohos-arkui-advanced-Dialog.md#customcontentdialog12), [SubHeader](./arkui-ts/ohos-arkui-advanced-SubHeader.md),<br>[AlphabetIndexer](./arkui-ts/ts-container-alphabet-indexer.md), [Popup](./arkui-ts/ohos-arkui-advanced-Popup.md), [Button](./arkui-ts/ts-basic-components-button.md),<br>[Select](./arkui-ts/ts-basic-components-select.md), [ToolBar](./arkui-ts/ohos-arkui-advanced-ToolBar.md), [Search](./arkui-ts/ts-basic-components-search.md),<br>[TimePicker](./arkui-ts/ts-basic-components-timepicker.md), [DatePicker](./arkui-ts/ts-basic-components-datepicker.md), [TextPicker](./arkui-ts/ts-basic-components-textpicker.md)         |
| fontOnPrimary                 | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Primary inverted font color used on color background.<br>Affected components: [Badge](./arkui-ts/ts-container-badge.md), [Button](./arkui-ts/ts-basic-components-button.md) and [Chip](./arkui-ts/ohos-arkui-advanced-Chip.md)|
| fontOnSecondary               | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Secondary inverted font color used on color background.<br>Affected components: None|
| fontOnTertiary                | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Tertiary inverted font color used on color background.<br>Affected components: None|
| fontOnFourth                  | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Fourth-level inverted font color used on color background.<br>Affected components: None|
| iconPrimary                   | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Primary icon color.<br>Affected components: [EditableTitleBar](./arkui-ts/ohos-arkui-advanced-EditableTitleBar.md), [Swiper](./arkui-ts/ts-container-swiper.md) and [ToolBar](./arkui-ts/ohos-arkui-advanced-ToolBar.md)<br>[TreeView](./arkui-ts/ohos-arkui-advanced-TreeView.md)          |
| iconSecondary                 | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Secondary icon color.<br>Affected components: [LoadingDialog](./arkui-ts/ohos-arkui-advanced-Dialog.md#loadingdialog), [SubHeader](./arkui-ts/ohos-arkui-advanced-SubHeader.md) and [LoadingProgress](./arkui-ts/ts-basic-components-loadingprogress.md)<br>[Popup](./arkui-ts/ohos-arkui-advanced-Popup.md), [Chip](./arkui-ts/ohos-arkui-advanced-Chip.md), [Search](./arkui-ts/ts-basic-components-search.md),<br>[TreeView](./arkui-ts/ohos-arkui-advanced-TreeView.md)          |
| iconTertiary                  | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Tertiary icon color.<br>Affected components: [SubHeader](./arkui-ts/ohos-arkui-advanced-SubHeader.md)         |
| iconFourth                    | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Fourth-level icon color.<br>Affected components: [Checkbox](./arkui-ts/ts-basic-components-checkbox.md), [CheckboxGroup](arkui-ts/ts-basic-components-checkboxgroup.md) and [Radio](./arkui-ts/ts-basic-components-radio.md)         |
| iconEmphasize                 | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Emphasis icon color.<br>Affected components: [ToolBar](./arkui-ts/ohos-arkui-advanced-ToolBar.md)         |
| iconSubEmphasize              | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Color of the emphasis auxiliary icon.<br>Affected components: None       |
| iconOnPrimary                 | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Primary inverted icon color used on color background.<br>Affected components: [Checkbox](./arkui-ts/ts-basic-components-checkbox.md), [CheckboxGroup](arkui-ts/ts-basic-components-checkboxgroup.md), [Radio](./arkui-ts/ts-basic-components-radio.md)|
| iconOnSecondary               | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Secondary inverted icon color used on color background.<br>Affected components: [Chip](./arkui-ts/ohos-arkui-advanced-Chip.md)|
| iconOnTertiary                | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Tertiary inverted icon color used on color background.<br>Affected components: None|
| iconOnFourth                  | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Fourth-level inverted icon color used on color background.<br>Affected components: [ProgressButton](./arkui-ts/ohos-arkui-advanced-ProgressButton.md)|
| backgroundPrimary             | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Primary background color (solid, opaque).<br>Affected components: [TextInput](./arkui-ts/ts-basic-components-textinput.md), [QRCode](./arkui-ts/ts-basic-components-qrcode.md) |
| backgroundSecondary           | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Secondary background color (solid, opaque).<br>Affected components: None |
| backgroundTertiary            | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Tertiary background color (solid, opaque).<br>Affected components: None |
| backgroundFourth              | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Fourth-level background color (solid, opaque).<br>Affected components: None |
| backgroundEmphasize           | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Emphasis background color (solid, opaque).<br>Affected components: [Progress](./arkui-ts/ts-basic-components-progress.md), [Button](./arkui-ts/ts-basic-components-button.md) and [Slider](./arkui-ts/ts-basic-components-slider.md) |
| compForegroundPrimary         | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Foreground.<br>Affected components: [QRCode](./arkui-ts/ts-basic-components-qrcode.md)           |
| compBackgroundPrimary         | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | White background.<br>Affected components: none           |
| compBackgroundPrimaryTran     | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | White transparent background.<br>Affected components: none        |
| compBackgroundPrimaryContrary | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Always-on background.<br>Affected components: [Toggle](./arkui-ts/ts-basic-components-toggle.md) and [Slider](./arkui-ts/ts-basic-components-slider.md)          |
| compBackgroundGray            | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Gray background.<br>Affected components: none           |
| compBackgroundSecondary       | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Secondary background.<br>Affected components: [Swiper](./arkui-ts/ts-container-swiper.md) and [Slider](./arkui-ts/ts-basic-components-slider.md)           |
| compBackgroundTertiary        | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Tertiary background.<br>Affected components: [EditableTitleBar](./arkui-ts/ohos-arkui-advanced-EditableTitleBar.md), [Progress](./arkui-ts/ts-basic-components-progress.md) and [AlphabetIndexer](./arkui-ts/ts-container-alphabet-indexer.md)<br>[Button](./arkui-ts/ts-basic-components-button.md), [Select](./arkui-ts/ts-basic-components-select.md), [Toggle](./arkui-ts/ts-basic-components-toggle.md),<br>[Chip](./arkui-ts/ohos-arkui-advanced-Chip.md), [TextInput](./arkui-ts/ts-basic-components-textinput.md), [Search](./arkui-ts/ts-basic-components-search.md)           |
| compBackgroundEmphasize       | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Emphasis background.<br>Affected components: [Swiper](./arkui-ts/ts-container-swiper.md), [Toggle](./arkui-ts/ts-basic-components-toggle.md) and [Chip](./arkui-ts/ohos-arkui-advanced-Chip.md)<br>[Checkbox](./arkui-ts/ts-basic-components-checkbox.md), [CheckboxGroup](arkui-ts/ts-basic-components-checkboxgroup.md), [Radio](./arkui-ts/ts-basic-components-radio.md)           |
| compBackgroundNeutral         | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Black, neutral, emphasis background.<br>Affected components: [PatternLock](./arkui-ts/ts-basic-components-patternlock.md)     |
| compEmphasizeSecondary        | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | 20% emphasis background color.<br>Affected components: [Progress](./arkui-ts/ts-basic-components-progress.md), [ProgressButton](./arkui-ts/ohos-arkui-advanced-ProgressButton.md) and [AlphabetIndexer](./arkui-ts/ts-container-alphabet-indexer.md)<br>[Select](./arkui-ts/ts-basic-components-select.md), [Toggle](./arkui-ts/ts-basic-components-toggle.md)      |
| compEmphasizeTertiary         | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | 10% emphasis background color.<br>Affected components: None      |
| compDivider                   | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Common divider color.<br>Affected components: [SelectDialog](./arkui-ts/ohos-arkui-advanced-Dialog.md#selectdialog), [PatternLock](./arkui-ts/ts-basic-components-patternlock.md) and [Divider](./arkui-ts/ts-basic-components-divider.md)        |
| compCommonContrary            | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Common inverted color.<br>Affected components: None         |
| compBackgroundFocus           | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Background color in the focused state.<br>Affected components: None        |
| compFocusedPrimary            | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Primary inverted color in the focused state.<br>Affected components: None      |
| compFocusedSecondary          | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Secondary inverted color in the focused state.<br>Affected components: None      |
| compFocusedTertiary           | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Tertiary inverted color in the focused state.<br>Affected components: [Scroll](arkui-ts/ts-container-scroll.md)      |
| interactiveHover              | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Common interactive color for the hover state.<br>Affected components: [EditableTitleBar](./arkui-ts/ohos-arkui-advanced-EditableTitleBar.md), [Chip](./arkui-ts/ohos-arkui-advanced-Chip.md) and [TreeView](./arkui-ts/ohos-arkui-advanced-TreeView.md)     |
| interactivePressed            | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Common interactive color for the pressed state.<br>Affected components: [EditableTitleBar](./arkui-ts/ohos-arkui-advanced-EditableTitleBar.md), [Chip](./arkui-ts/ohos-arkui-advanced-Chip.md) and [TreeView](./arkui-ts/ohos-arkui-advanced-TreeView.md)      |
| interactiveFocus              | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Common interactive color for the focused state.<br>Affected components: [EditableTitleBar](./arkui-ts/ohos-arkui-advanced-EditableTitleBar.md), [Chip](./arkui-ts/ohos-arkui-advanced-Chip.md) and [TreeView](./arkui-ts/ohos-arkui-advanced-TreeView.md)      |
| interactiveActive             | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Common interactive color for the active state.<br>Affected components: [TreeView](./arkui-ts/ohos-arkui-advanced-TreeView.md)      |
| interactiveSelect             | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Common interactive color for the selected state.<br>Affected components: [TreeView](./arkui-ts/ohos-arkui-advanced-TreeView.md)      |
| interactiveClick              | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | No  | No  | Common interactive color for the clicked state.<br>Affected components: None      |

## CustomTheme

Defines a custom theme object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                          | Type                                                | Read Only | Optional | Description        |
|-------------------------------|-----------------------------------------------------|-----|-----|------------|
| colors | [CustomColors](#customcolors) | No  | Yes  | Color resources of the custom theme.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| darkColors<sup>20+</sup> | [CustomDarkColors](#customdarkcolors20) | No  | Yes  | Custom dark theme color resources.<br>Note: If darkColors is not set, the color values are the same as those in the colors configuration in light mode and do not change with the color mode unless the color is set through resources in the dark directory.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|

## CustomColors

type CustomColors = Partial\<Colors>

Defines the type for custom theme color resources.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type | Description          |
|-----|--------------|
| Partial<[Colors](#colors)>   | Type representing customizable theme color resources.|

## CustomDarkColors<sup>20+</sup>

type CustomDarkColors = Partial\<Colors>

Customizes dark theme color resources.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type | Description          |
|-----|--------------|
| Partial<[Colors](#colors)>   | Customizes dark theme color resources.|

## ThemeControl

Implements a **ThemeControl** object to apply the custom theme to the components in the application.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### setDefaultTheme

setDefaultTheme(theme: [CustomTheme](#customtheme)): void

Applies a custom theme to an app to implement theme-based style switching. If this API is used to set the application-level default theme on a page, ensure that this API is executed before the page is built. If this API is used to set the application-level default theme in UIAbility, ensure that this API is executed in the callback function after the windowStage.[loadContent](./arkts-apis-window-Window.md#loadcontent9) API is called in the onWindowStageCreate phase. For details, see [Setting Custom Theme Colors for Application Components](../../ui/theme_skinning.md#setting-custom-theme-colors-for-application-components).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name      | Type                          | Mandatory| Description            |
|--------------|------------------------------|------|----------------|
| theme | [CustomTheme](#customtheme)  | Yes   | Custom theme to set.|

**Example**

```ts
import { CustomTheme, CustomColors, ThemeControl } from '@kit.ArkUI';
// Custom theme color
class BlueColors implements CustomColors {
  fontPrimary = Color.Red;
  backgroundPrimary = Color.Blue;
  brand = "#FFEEAAFF"; // Brand color.
}

class PageCustomTheme implements CustomTheme {
  colors?: CustomColors;

  constructor(colors: CustomColors) {
    this.colors = colors;
  }
}
// Create an instance.
const BlueColorsTheme = new PageCustomTheme(new BlueColors());
// Call ThemeControl.setDefaultTheme before page build to set the default application style to BlueColorsTheme.
ThemeControl.setDefaultTheme(BlueColorsTheme);

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
        // Apply brand to the cursor color of the text box.
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
