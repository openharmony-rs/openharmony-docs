# Popup

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyi0309-->
<!--Designer: @liyi0309-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=8e22c68cdd7ecb0668db21c4312cda839c2cdaa0 translatedAt=2026-07-29T03:03:33.179Z pushedAt=2026-08-04T02:46:58.271Z -->

The **Popup** component is a component used to display bubbles of specific styles. It supports flexible combinations of icons, text, and buttons, and is suitable for scenarios such as notification prompts, information confirmation, and warning alerts. Via customizable style options, it can quickly implement a consistent popup interaction experience.

>  **NOTE**
>
> - This component is supported since API version 11. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.
>
> - It is recommended to use this component together with the custom popup feature in [Popup Control](ts-universal-attributes-popup.md).

## Modules to Import

```ts
import { Popup, PopupOptions, PopupTextOptions, PopupButtonOptions, PopupIconOptions } from '@kit.ArkUI';
```

## Child Components

Not supported

## Popup

Popup(options: PopupOptions): void

**Decorator**: @Builder

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                         | Mandatory| Description                 |
| ------- | ----------------------------- | ---- | --------------------- |
| options | [PopupOptions](#popupoptions) | Yes   | Configuration parameters of the **Popup** component. |

## PopupOptions

Defines the style parameters of the popup.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name       | Type      | Read-Only     | Optional     | Description                           |
| ----------- | ---------- | ------| --------------------------------- | --------------------------------- |
| icon      | [PopupIconOptions](#popupiconoptions)                        | No   | Yes | Popup icon.<br />**NOTE**<br />The icon is not displayed when width and height are set to abnormal values or 0.<br/> Hidden by default. <br/>**Atomic service API:** This API can be used in atomic services since API version 12. |
| title     | [PopupTextOptions](#popuptextoptions)                        | No   | Yes  | Popup title text. <br/> Hidden by default.<br/>**Atomic service API:** This API can be used in atomic services since API version 12. |
| message   | [PopupTextOptions](#popuptextoptions)                        | No  | No  | Popup content text.<br />**NOTE**<br />**fontWeight** setting is not supported for message. <br/> Hidden by default.<br/>**Atomic service API:** This API can be used in atomic services since API version 12. |
| showClose | boolean \| [Resource](ts-types.md#resource)                | No   | Yes  | Popup close button.<br/>The value **true** indicates to show the close button, and **false** indicates to hide the close button.<br/>**Resource**: displays the corresponding icon.<br />Default value: **true**<br/>**Atomic service API:** This API can be used in atomic services since API version 12. |
| onClose   | () => void                                                   | No   | Yes  | Popup close button callback. <br/> No close button callback is set by default.<br/>**Atomic service API:** This API can be used in atomic services since API version 12. |
| buttons   | [[PopupButtonOptions](#popupbuttonoptions)?,[PopupButtonOptions](#popupbuttonoptions)?] | No   | Yes  | Popup action buttons. A maximum of two buttons can be set. <br/> Hidden by default. <br/>**Atomic service API:** This API can be used in atomic services since API version 12. |
| direction<sup>12+</sup> | [Direction](ts-appendix-enums.md#direction)                                             | No                                | Yes                               | Layout direction of the Popup content. For available enum values, see [Direction](ts-appendix-enums.md#direction).<br/>Default value: **Direction.Auto**<br/>**Atomic service API:** This API can be used in atomic services since API version 12. |
| maxWidth<sup>18+</sup> | [Dimension](ts-types.md#dimension10)                                             | No                                | Yes                               | Maximum width of the Popup. Custom width display is supported.<br />**NOTE**<br />1. When a referenced resource type is used, its parameter type must be consistent with the type of the **maxWidth** attribute itself.<br/>2. **maxWidth** is of the [Dimension](ts-types.md#dimension10) type, which supports numeric and percentage string types. Numeric types support float and integer, for example, `$r('app.float.maxWidth')` and `$r('app.integer.maxWidth')`; percentage strings, for example, '50%'.<br/>3. When the type is Resource, if no unit is set, the default unit is px.<br/>Default value: **400vp**<br/>**Atomic service API:** This API can be used in atomic services since API version 18. |

## PopupTextOptions

Provides text style settings.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name      | Type                                                        | Read-Only| Optional| Description        |
| ---------- | ------------------------------------------------------------ | ---- | ------------------ | ------------------ |
| text       | [ResourceStr](ts-types.md#resourcestr)                       | No | No | Text content.    |
| fontSize   | number \| string \| [Resource](ts-types.md#resource)         | No   | Yes  | Font size of the text.<br />Default value: `$r('sys.float.ohos_id_text_size_body2')` <br/>For the string type, the value can be a string that can be converted to a number (such as '10') or a string with a length unit (such as '10px'). Setting a percentage string is not supported.<br/>For the number type, the value range is (0, +∞). When the type is number, the unit is fp.|
| fontColor  | [ResourceColor](ts-types.md#resourcecolor)                   | No  | Yes | Text font color.<br>Default value: **$r('sys.color.ohos_id_color_text_secondary')**|
| fontWeight | number \| [FontWeight](ts-appendix-enums.md#fontweight) \| string | No  | Yes | Text font weight.<br>For the number type, the value ranges from 100 to 900, at an interval of 100. A larger value indicates a heavier font weight. The default value is **400**.<br>For the string type, only strings of the number type are supported, for example, **"400"**, **"bold"**, **"bolder"**, **"lighter"**, **"regular"**, and **"medium"**, which correspond to the enumerated values in **FontWeight**.<br>Default value: **FontWeight.Regular**|

## PopupButtonOptions

Defines the button attributes and events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Type                                                | Read-Only| Optional| Description                |
| --------- | ---------------------------------------------------- | ---- | ---------------------- | ---------------------- |
| text      | [ResourceStr](ts-types.md#resourcestr)               | No | No | Text of the button.        |
| action    | () => void                                           | No  | Yes | Click callback of the button.<br> By default, no operation is performed.|
| fontSize  | number \| string \| [Resource](ts-types.md#resource) | No   | Yes  | Font size of the button text.<br />Default value: **$r('sys.float.ohos_id_text_size_button2')**<br/>Optional values of the string type: a string that can be converted to a number (for example, '10') or a string with a length unit (for example, '10px'). Setting a percentage string is not supported.<br/>number: value range (0, +∞). When the type is number, the unit is fp.<br/>The default value is used when an abnormal value is set. |
| fontColor | [ResourceColor](ts-types.md#resourcecolor)           | No  | Yes | Font color of the button text.<br>Default value: **$r('sys.color.ohos_id_color_text_primary_activated')**|

## PopupIconOptions

Defines the icon options.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name        | Type                                                        | Read-Only| Optional| Description                            |
| ------------ | ------------------------------------------------------------ | ---- | ---------------------------------- | ---------------------------------- |
| image        | [ResourceStr](ts-types.md#resourcestr)                       | No | No | Icon content.                    |
| width | [Dimension](ts-types.md#dimension10) | No | Yes | Icon width. Unit: vp.<br />Default value: **32vp** |
| height | [Dimension](ts-types.md#dimension10) | No | Yes | Icon height. Unit: vp.<br />Default value: **32vp** |
| fillColor    | [ResourceColor](ts-types.md#resourcecolor)                   | No  | Yes| Icon fill color. This property applies only to an SVG image.<br> By default, the icon color is not changed.|
| borderRadius | [Length](ts-types.md#length) \| [BorderRadiuses](ts-types.md#borderradiuses9) | No | Yes | Icon corner radius. Unit: vp.<br />Default value: `$r('sys.float.ohos_id_corner_radius_default_s')` |

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
        // Set the text content via the PopupTextOptions type.
        title: {
          text: 'This is a popup with PopupOptions',
          fontSize: 20,
          fontColor: Color.Black,
          fontWeight: FontWeight.Normal
        } as PopupTextOptions,
        // Set the text content via the PopupTextOptions type.
        message: {
          text: 'This is the message',
          fontSize: 15,
          fontColor: Color.Black
        } as PopupTextOptions,
        showClose: false,
        onClose: () => {
          console.info('close Button click');
        },
        // Set the button content via the PopupButtonOptions type.
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

### Example 2: Setting the Mirror Effect

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
        // Set the icon content via the PopupIconOptions type.
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

  build() {
    Row() {
      // Define a popup.
      Popup({
        // Set the custom width.
        maxWidth: '50%',
        // Set the icon content using the PopupIconOptions type.
        icon: {
          // Replace $r('app.media.startIcon') with the image resource file you use.
          image: $r('app.media.startIcon'),
          width: 32,
          height: 32,
          fillColor: Color.White,
          borderRadius: 16,
        } as PopupIconOptions,
        // Set the text content using the PopupTextOptions type.
        message: {
          text: 'This is the message. This is the message. This is the message. This is the message.',
          fontSize: 15,
          fontColor: Color.Black
        } as PopupTextOptions,
        showClose: false,
        onClose: () => {
          console.info('close Button click');
        },
        // Set the button content using the PopupButtonOptions type.
        buttons: [{
          text: 'OK',
          action: () => {
            console.info('confirm button click');
          },
          fontSize: 15,
          fontColor: Color.Black,
        },
          {
            text: 'Cancel',
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