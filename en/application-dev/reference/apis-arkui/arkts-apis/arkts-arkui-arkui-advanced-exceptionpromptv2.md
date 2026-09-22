# @ohos.arkui.advanced.ExceptionPromptV2

## Modules to Import

```TypeScript
import { MarginTypeV2, PromptOptionsV2, PromptOptionsV2Config, ExceptionPromptV2 } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [PromptOptionsV2](arkts-arkui-arkui-advanced-exceptionpromptv2-promptoptionsv2-c.md) | Configuration parameter of ExceptionPromptV2. Use @ObservedV2 and @Trace to support deep observation and dynamic refresh of properties. |

### Structs

| Name | Description |
| --- | --- |
| [ExceptionPromptV2](arkts-arkui-arkui-advanced-exceptionpromptv2-exceptionpromptv2-s.md) | Declare struct ExceptionPromptV2 higher-order component. The exception prompt component is used to show an error message when an error arises. @struct { ExceptionPromptV2 } |

### Interfaces

| Name | Description |
| --- | --- |
| [PromptOptionsV2Config](arkts-arkui-arkui-advanced-exceptionpromptv2-promptoptionsv2config-i.md) | Configuration information interface for PromptOptionsV2. Used to construct PromptOptionsV2 object. |

### Enums

| Name | Description |
| --- | --- |
| [MarginTypeV2](arkts-arkui-arkui-advanced-exceptionpromptv2-margintypev2-e.md) | Control margin status of ExceptionPromptV2. |

### Types

| Name | Description |
| --- | --- |
| [OnActionTextClickCallback](arkts-arkui-onactiontextclickcallback-t.md) | Declare the callback function type to be called when clicking the icon button. @typedef { function } OnActionTextClickCallback |
| [OnTipClickCallback](arkts-arkui-ontipclickcallback-t.md) | Declare the callback function type to be called when clicking the text on the left. @typedef { function } OnTipClickCallback |

## Examples

### Example 1: Setting an Exception Prompt

Starting from API version 26.0.0, this example shows how to set the exception icon, exception prompt text, margin style, and text content of the right icon button for the exception prompt.

```TypeScript
import { ExceptionPromptV2, PromptOptionsV2, MarginTypeV2 } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local options: PromptOptionsV2 = new PromptOptionsV2({
    icon: $r('sys.media.ohos_ic_public_fail'),
    tip: 'Exception prompt',
    marginType: MarginTypeV2.DEFAULT_MARGIN,
    actionText: 'Set network',
    marginTop: 80,
    isShown: true,
  });

  build(): void {
    Column() {
      ExceptionPromptV2({
        options: this.options,
        onTipClick: () => {
          // Tap the text on the left to switch to the connected state.
        },
        onActionTextClick: () => {
          // Open the network configuration dialog box by tapping the "Set network" button.
        },
      })
    }
  }
}
```

### Example 2 Setting an Exception Prompt of the Dialog Box Type

Since API version 26.0.0, this example uses a custom dialog box to set an exception prompt of the dialog box type.

```TypeScript
import { ExceptionPromptV2, MarginTypeV2, PromptOptionsV2 } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index1 {
  @Local ButtonText: string = '';
  @Local MAP_HEIGHT: string = '30%';
  @Local duration: number = 2500;
  @Local tips: string = '';
  @Local actionText: string = '';
  controller: TextInputController = new TextInputController();
  cancel: () => void = () => {
  };
  confirm: () => void = () => {
  };
  @Local options: PromptOptionsV2 = new PromptOptionsV2({
    icon: $r('sys.media.ohos_ic_public_fail'),
    tip: 'Exception prompt!',
    marginType: MarginTypeV2.DEFAULT_MARGIN,
    actionText: 'Settings',
    marginTop: 5,
    isShown: true,
  })
  @Local textValue: string = '';
  @Local inputValue: string = 'click me';

  onCancel(): void {
    console.info('Callback when the first button is clicked');
  }

  onAccept(): void {
    console.info('Callback when the second button is clicked');
  }

  existApp(): void {
    console.info('Click the callback in the blank area');
  }

  private customDialogComponentId: number = 0;

  build(): void {
    Column() {
      Button('Click Me')
        .width('30%')
        .margin({ top: 420 })
        .zIndex(999)
        .onClick(() => {
          this.getUIContext().getPromptAction().openCustomDialog({
            builder: () => {
              this.customDialogComponent()
            },
            onWillDismiss: (dismissDialogAction: DismissDialogAction) => {
              console.info('reason' + JSON.stringify(dismissDialogAction.reason));
              console.info('dialog onWillDismiss');
              if (dismissDialogAction.reason == DismissReason.PRESS_BACK) {
                dismissDialogAction.dismiss();
              }
              if (dismissDialogAction.reason == DismissReason.TOUCH_OUTSIDE) {
                dismissDialogAction.dismiss();
              }
            },
            autoCancel: true,
            alignment: DialogAlignment.Bottom,
            offset: { dx: 0, dy: -20 },
          })
            .then((dialogId: number) => {
              this.customDialogComponentId = dialogId;
            })
            .catch((error: BusinessError) => {
              console.error(`openCustomDialog error code is ${error.code}, message is ${error.message}`);
            })

        })
    }
    .height('100%')
    .width('100%')
  }

  @Builder
  customDialogComponent(): void {
    Column() {
      ExceptionPromptV2({
        options: this.options,
      })
      TextInput({ placeholder: '', text: this.textValue }).margin({ top: 70 }).height(60).width('90%')
        .onChange((value: string) => {
          this.textValue = value;
        })
      Text('Whether to change the text?').fontSize(16).margin({ bottom: 10 })
      Flex({ justifyContent: FlexAlign.SpaceAround }) {
        Button('cancel')
          .onClick(() => {
            try {
              this.getUIContext().getPromptAction().closeCustomDialog(this.customDialogComponentId)
            } catch (error) {
              let message = (error as BusinessError).message;
              let code = (error as BusinessError).code;
              console.error(`closeCustomDialog error code is ${code}, message is ${message}`);
            }
          }).backgroundColor(0xffffff).fontColor(Color.Black)
        Button('confirm')
          .onClick(() => {
            try {
              this.getUIContext().getPromptAction().closeCustomDialog(this.customDialogComponentId)
            } catch (error) {
              let message = (error as BusinessError).message;
              let code = (error as BusinessError).code;
              console.error(`closeCustomDialog error code is ${code}, message is ${message}`);
            }
          }).backgroundColor(0xffffff).fontColor(Color.Red)
      }.margin({ bottom: 10 })
    }
  }
}
```

### Example 3: Setting a Symbol Icon

Since API version 26.0.0, this example demonstrates custom symbol icons by setting the symbolStyle property of PromptOptionsV2.

```TypeScript
import { ExceptionPromptV2, PromptOptionsV2, MarginTypeV2, SymbolGlyphModifier } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local options1: PromptOptionsV2 = new PromptOptionsV2({
    icon: $r('sys.symbol.house'),
    tip: 'Exception prompt',
    marginType: MarginTypeV2.DEFAULT_MARGIN,
    actionText: 'Set network',
    marginTop: 80,
    isShown: true,
  });

  @Local options2: PromptOptionsV2 = new PromptOptionsV2({
    icon: $r('sys.symbol.house'),
    symbolStyle: new SymbolGlyphModifier($r('sys.symbol.bell')).fontColor([Color.Red]),
    tip: 'Exception prompt',
    marginType: MarginTypeV2.DEFAULT_MARGIN,
    actionText: 'Set network',
    marginTop: 200,
    isShown: true,
  });

  build(): void {
    Column() {
      ExceptionPromptV2({
        options: this.options1,
      })
      ExceptionPromptV2({
        options: this.options2,
      })
    }
  }
}
```
