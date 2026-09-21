# @ohos.arkui.advanced.Popup

## Modules to Import

```TypeScript
import { Popup, PopupButtonOptions, PopupIconOptions, PopupOptions, PopupTextOptions } from '@kit.ArkUI';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [Popup](arkts-arkui-arkui-advanced-popup-popup-f.md) |  |

### Interfaces

| Name | Description |
| --- | --- |
| [PopupButtonOptions](arkts-arkui-arkui-advanced-popup-popupbuttonoptions-i.md) | Defines the button attributes and events. |
| [PopupIconOptions](arkts-arkui-arkui-advanced-popup-popupiconoptions-i.md) | Defines the icon options. |
| [PopupOptions](arkts-arkui-arkui-advanced-popup-popupoptions-i.md) | Defines the style parameters of the popup. |
| [PopupTextOptions](arkts-arkui-arkui-advanced-popup-popuptextoptions-i.md) | Provides text style settings. |

## Examples

### Example 1: Setting the Popup Style

This example demonstrates how to customize the style of a popup by configuring PopupIconOptions, PopupTextOptions, and PopupButtonOptions.



```TypeScript
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

### Example 2: Setting the Mirror Effect

This example shows how to implement a mirrored layout for a popup by configuring direction.



```TypeScript
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

### Example 3: Setting the Custom Width

This example demonstrates how to set the custom width for a popup using maxWidth.

```TypeScript
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
