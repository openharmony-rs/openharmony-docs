# Popup
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyi0309-->
<!--Designer: @liyi0309-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

The **Popup** component is used to display popups in a specific style.

>  **NOTE**
>
>  - This component is supported since API version 11. Updates will be marked with a superscript to indicate their earliest API version.
>  - Use this component with the custom popup features in [popup control](ts-universal-attributes-popup.md) for best results.

## Modules to Import

```ts
import { Popup, PopupOptions, PopupTextOptions, PopupButtonOptions, PopupIconOptions } from '@kit.ArkUI';
```

##  Child Components

Not supported

## Popup

Popup(options: PopupOptions): void

**Decorator**: @Builder

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

**Parameters**

| Name | Type                         | Mandatory| Description                 |
| ------- | ----------------------------- | ---- | --------------------- |
| options | [PopupOptions](#popupoptions) | Yes  | Parameters of the popup.|

## PopupOptions

Defines the style parameters of the popup.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name       | Type      | Read-Only     | Optional     | Description                           |
| ----------- | ---------- | ------| --------------------------------- | --------------------------------- |
| icon      | [PopupIconOptions](#popupiconoptions)                        | No  | Yes| Icon of the popup.<br>**NOTE**<br>The icon is not displayed when **width** and **height** are set to an invalid value or **0**.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| title     | [PopupTextOptions](#popuptextoptions)                        | No  | Yes | Title of the popup.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| message   | [PopupTextOptions](#popuptextoptions)                        | No | No | Content of the popup.<br>**NOTE**<br>**fontWeight** is not available for **messages**.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| showClose | boolean \| [Resource](ts-types.md#resource)                | No  | Yes | Whether to show the close button.<br>**true**: Show the close button. **false**: Do not show the close button.<br>**Resource**: Show the corresponding icon.<br>Default value: **true**.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| onClose   | () => void                                                   | No  | Yes | Callback for the popup close button.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| buttons   | [[PopupButtonOptions](#popupbuttonoptions)?,[PopupButtonOptions](#popupbuttonoptions)?] | No  | Yes | Buttons of the popup. A maximum of two buttons can be set.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| direction<sup>12+</sup> | [Direction](ts-appendix-enums.md#direction)                                             | No                               | Yes                              | Layout direction.<br>Default value: **Direction.Auto**<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| maxWidth<sup>18+</sup> | [Dimension](ts-types.md#dimension10)                                             | No                               | Yes                              | Maximum width of the popup. This API allows the popup to display with a custom width.<br>**NOTE**<br>1. When using resource references, ensure that the parameter type matches the attribute method type.<br>2. **maxWidth** accepts numeric values (both floating-point and integer values), such as **$r('app.float.maxWidth')** and **$r('app.integer.maxWidth')**.<br>3. When the type is Resource, values default to px units if no unit is explicitly specified.<br>Default value: 400 vp<br>**Atomic service API**: This API can be used in atomic services since API version 18.|

## PopupTextOptions

Provides text style settings.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name      | Type                                                        | Read-Only| Optional| Description        |
| ---------- | ------------------------------------------------------------ | ---- | ------------------ | ------------------ |
| text       | [ResourceStr](ts-types.md#resourcestr)                       | No | No | Text content.    |
| fontSize   | number \| string \| [Resource](ts-types.md#resource)         | No  | Yes | Text font size.<br>Default value: **$r('sys.float.ohos_id_text_size_body2')**<br>The string value must be convertible to a number (for example, **'10'**) or include a length unit (for example, **'10px'**); percentage-based strings are not supported.<br>Value range of number values: (0, +∞)|
| fontColor  | [ResourceColor](ts-types.md#resourcecolor)                   | No  | Yes | Text font color.<br>Default value: **$r('sys.color.ohos_id_color_text_secondary')**|
| fontWeight | number \| [FontWeight](ts-appendix-enums.md#fontweight) \| string | No  | Yes | Text font weight.<br>For the number type, the value ranges from 100 to 900, at an interval of 100. A larger value indicates a heavier font weight. The default value is **400**.<br>For the string type, only strings of the number type are supported, for example, **"400"**, **"bold"**, **"bolder"**, **"lighter"**, **"regular"**, and **"medium"**, which correspond to the enumerated values in **FontWeight**.<br>Default value: **FontWeight.Regular**|

## PopupButtonOptions

Defines the button attributes and events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name     | Type                                                | Read-Only| Optional| Description                |
| --------- | ---------------------------------------------------- | ---- | ---------------------- | ---------------------- |
| text      | [ResourceStr](ts-types.md#resourcestr)               | No | No | Text of the button.        |
| action    | () => void                                           | No  | Yes | Click callback of the button.|
| fontSize  | number \| string \| [Resource](ts-types.md#resource) | No  | Yes | Font size of the button text.<br>Default value: **$r('sys.float.ohos_id_text_size_button2')**<br>The string value must be convertible to a number (for example, **'10'**) or include a length unit (for example, **'10px'**); percentage-based strings are not supported.<br>Invalid values are handled as default values.|
| fontColor | [ResourceColor](ts-types.md#resourcecolor)           | No  | Yes | Font color of the button text.<br>Default value: **$r('sys.color.ohos_id_color_text_primary_activated')**|

##  PopupIconOptions

Defines the icon options.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name        | Type                                                        | Read-Only| Optional| Description                            |
| ------------ | ------------------------------------------------------------ | ---- | ---------------------------------- | ---------------------------------- |
| image        | [ResourceStr](ts-types.md#resourcestr)                       | No | No | Icon content.                    |
| width        | [Dimension](ts-types.md#dimension10)                         | No  | Yes| Icon width.<br>Default value: **32VP**|
| height       | [Dimension](ts-types.md#dimension10)                         | No  | Yes| Icon height.<br>Default value: **32VP**|
| fillColor    | [ResourceColor](ts-types.md#resourcecolor)                   | No  | Yes| Icon fill color. This property applies only to an SVG image.|
| borderRadius | [Length](ts-types.md#length) \| [BorderRadiuses](ts-types.md#borderradiuses9) | No  | Yes| Rounded corner of the icon.<br>Default value: **$r('sys.float.ohos_id_corner_radius_default_s')** |

## Example

### Example 1: Setting the Popup Style

This example demonstrates how to customize the style of a popup by configuring **PopupIconOptions**, **PopupTextOptions**, and **PopupButtonOptions**.

```ts
// xxx.ets
import { Popup, PopupTextOptions, PopupButtonOptions, PopupIconOptions } from '@kit.ArkUI';

@Entry
@Component
struct PopupExample {
  build() {
    Row() {
      // Define a popup.
      Popup({
        // Set the icon through PopupIconOptions.
        icon: {
          // Replace $r('app.media.icon') with the image resource file you use.
          image: $r('app.media.icon'),
          width: 32,
          height: 32,
          fillColor: Color.White,
          borderRadius: 16
        } as PopupIconOptions,
        // Set the text through PopupTextOptions.
        title: {
          text: 'This is a popup with PopupOptions',
          fontSize: 20,
          fontColor: Color.Black,
          fontWeight: FontWeight.Normal
        } as PopupTextOptions,
        // Set the text through PopupTextOptions.
        message: {
          text: 'This is the message',
          fontSize: 15,
          fontColor: Color.Black
        } as PopupTextOptions,
        showClose: false,
        onClose: () => {
          console.info('close Button click');
        },
        // Set the button through PopupButtonOptions.
        buttons: [{
          text: 'confirm',
          action: () => {
            console.info('confirm button click');
          },
          fontSize: 15,
          fontColor: Color.Black,
        },
          {
            text: 'cancel',
            action: () => {
              console.info('cancel button click');
            },
            fontSize: 15,
            fontColor: Color.Black
          },] as [PopupButtonOptions?, PopupButtonOptions?]
      })
    }
    .width(300)
    .height(200)
    .borderWidth(2)
    .justifyContent(FlexAlign.Center)
  }
}
```

![](figures/popup_7.png)

### Example 2: Implementing a Mirrored Layout
This example shows how to implement a mirrored layout for a popup by configuring **direction**.

```ts
// xxx.ets
import { Popup, PopupTextOptions, PopupButtonOptions, PopupIconOptions } from '@kit.ArkUI';

@Entry
@Component
struct PopupPage {
  @State currentDirection: Direction = Direction.Rtl;

  build() {
    Column() {
      // Define a popup.
      Popup({
        // Set the icon through PopupIconOptions.
        direction: this.currentDirection,
        icon: {
          // Replace $r('app.media.icon') with the image resource file you use.
          image: $r('app.media.icon'),
          width: 32,
          height: 32,
          fillColor: Color.White,
          borderRadius: 16,
        } as PopupIconOptions,
        // Set the text through PopupTextOptions.
        title: {
          text: 'This is a popup with PopupOptions',
          fontSize: 20,
          fontColor: Color.Black,
          fontWeight: FontWeight.Normal,

        } as PopupTextOptions,
        // Set the text through PopupTextOptions.
        message: {
          text: 'This is the message',
          fontSize: 15,
          fontColor: Color.Black,
        } as PopupTextOptions,
        showClose: true,
        onClose: () => {
          console.info('close Button click');
        },
        // Set the button through PopupButtonOptions.
        buttons: [{
          text: 'confirm',
          action: () => {
            console.info('confirm button click');
          },
          fontSize: 15,
          fontColor: Color.Black,

        },
          {
            text: 'cancel',
            action: () => {
              console.info('cancel button click');
            },
            fontSize: 15,
            fontColor: Color.Black,
          },] as [PopupButtonOptions?, PopupButtonOptions?],
      })

    }
    .justifyContent(FlexAlign.Center)
    .width('100%')
    .height('100%')
  }
}
```

![](figures/popup_8.png)

### Example 3: Setting the Custom Width
This example demonstrates how to set the custom width for a popup using **maxWidth**.

```ts
// xxx.ets
import { Popup, PopupTextOptions, PopupButtonOptions, PopupIconOptions } from '@kit.ArkUI';

@Entry
@Component
struct PopupPage {
  @State currentDirection: Direction = Direction.Rtl;

  build() {
    Row() {
      // Define a popup.
      Popup({
        // Set the custom width.
        maxWidth: '50%',
        // Set the icon through PopupIconOptions.
        icon: {
          // Replace $r('app.media.startIcon') with the image resource file you use.
          image: $r('app.media.startIcon'),
          width: 32,
          height: 32,
          fillColor: Color.White,
          borderRadius: 16,
        } as PopupIconOptions,
        // Set the text through PopupTextOptions.
        message: {
          text: 'This is the message. This is the message. This is the message. This is the message.',
          fontSize: 15,
          fontColor: Color.Black
        } as PopupTextOptions,
        showClose: false,
        onClose: () => {
          console.info('close Button click');
        },
        // Set the button through PopupButtonOptions.
        buttons: [{
          text: 'OK',
          action: () => {
            console.info('confirm button click');
          },
          fontSize: 15,
          fontColor: Color.Black,
        },
          {
            text: 'cancel',
            action: () => {
              console.info('cancel button click');
            },
            fontSize: 15,
            fontColor: Color.Black
          },] as [PopupButtonOptions?, PopupButtonOptions?]
      })
    }
    .width(400)
    .height(200)
    .borderWidth(2)
    .justifyContent(FlexAlign.Center)
  }
}
```

![](figures/popup_9.png)
