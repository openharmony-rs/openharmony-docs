# @ohos.arkui.advanced.ExceptionPrompt

## Modules to Import

```TypeScript
import { MarginType, PromptOptions, ExceptionPrompt } from '@kit.ArkUI';
```

## Summary

### Structs

| Name | Description |
| --- | --- |
| [ExceptionPrompt](arkts-arkui-arkui-advanced-exceptionprompt-exceptionprompt-s.md) | Declare struct ExceptionPrompt higher-order component. |

### Interfaces

| Name | Description |
| --- | --- |
| [PromptOptions](arkts-arkui-arkui-advanced-exceptionprompt-promptoptions-i.md) | Configuration parameter of ExceptionPrompt. @interface PromptOptions |

### Enums

| Name | Description |
| --- | --- |
| [MarginType](arkts-arkui-arkui-advanced-exceptionprompt-margintype-e.md) | Control margin status of ExceptionPrompt. @enum { number } |

## Examples

### Example 1: Configuring an Exception Prompt

This example demonstrates how to configure an exception prompt, including the exception icon, text, margin, and the text content of the right-side icon button.



```TypeScript
import { ExceptionPrompt, PromptOptions, MarginType } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State options: PromptOptions = {
    icon: $r('sys.media.ohos_ic_public_fail'),
    tip: 'Error',
    marginType: MarginType.DEFAULT_MARGIN,
    actionText: 'Set network',
    marginTop: 80,
    isShown: true,
  }

  build() {
    Column() {
      ExceptionPrompt({
        options: this.options,
        onTipClick: () => {
          // Handle clicks on the left text to switch to a connected state.
        },
        onActionTextClick: () => {
          // Handle clicks on the Set network button to open the network settings dialog box.
        },
      })
    }
  }
}
```

### Example 2: Setting a Dialog-Type Exception Prompt

This example uses a custom dialog box to set a dialog-type exception prompt.



```TypeScript
import { ExceptionPrompt, PromptOptions, MarginType } from '@kit.ArkUI';

@CustomDialog
struct CustomDialogExample {
  @Link textValue: string;
  @Link inputValue: string;
  @State options: PromptOptions = {
    icon: $r('sys.media.ohos_ic_public_fail'),
    tip: 'Error',
    marginType: MarginType.DEFAULT_MARGIN,
    actionText: 'Settings',
    marginTop: 5,
    isShown: true,
  };
  cancel: () => void = () => {
  };
  confirm: () => void = () => {
  };
  controller?: CustomDialogController;

  // To pass multiple other controllers into a CustomDialog to open another or several other custom dialog boxes within it,
  // place the controller pointing to itself last.
  build() {
    Column() {
      ExceptionPrompt({
        options: this.options,
      })
      TextInput({ placeholder: '', text: this.textValue }).margin({ top: 70 }).height(60).width('90%')
        .onChange((value: string) => {
          this.textValue = value;
        })
      Text('Are you sure you want to change the text?').fontSize(16).margin({ bottom: 10 })
      Flex({ justifyContent: FlexAlign.SpaceAround }) {
        Button('No')
          .onClick(() => {
            this.controller?.close();
            this.cancel();
          }).backgroundColor(0xffffff).fontColor(Color.Black)
        Button('OK')
          .onClick(() => {
            this.inputValue = this.textValue;
            this.controller?.close();
            this.confirm();
          }).backgroundColor(0xffffff).fontColor(Color.Red)
      }.margin({ bottom: 10 })
    }
  }
}

@Entry
@Component
struct Index1 {
  @State ButtonText: string = '';
  @State MAP_HEIGHT: string = '30%';
  @State duration: number = 2500;
  @State tips: string = '';
  @State actionText: string = '';
  controller: TextInputController = new TextInputController();
  cancel: () => void = () => {
  };
  confirm: () => void = () => {
  };
  @State options: PromptOptions = {
    icon: $r('sys.media.ohos_ic_public_fail'),
    tip: '',
    marginType: MarginType.DEFAULT_MARGIN,
    actionText: '',
    marginTop: 80,
    isShown: true,
  }
  @State textValue: string = '';
  @State inputValue: string = 'click me';
  dialogController: CustomDialogController | undefined = new CustomDialogController({
    builder: CustomDialogExample({
      cancel: this.onCancel,
      confirm: this.onAccept,
      textValue: $textValue,
      inputValue: $inputValue,
    }),
    cancel: this.existApp,
    autoCancel: true,
    alignment: DialogAlignment.Bottom,
    offset: { dx: 0, dy: -20 },
    gridCount: 4,
    customStyle: false,
  })

  aboutToDisappear() {
    this.dialogController = undefined; // Set dialogController to undefined.
  }

  onCancel() {
    console.info('Callback when the first button is clicked');
  }

  onAccept() {
    console.info('Callback when the second button is clicked');
  }

  existApp() {
    console.info('Click the callback in the blank area');
  }

  build() {
    Column() {
      Button('Click Me')
        .width('30%')
        .margin({ top: 420 })
        .zIndex(999)
        .onClick(() => {
          if (this.dialogController != undefined) {
            this.dialogController.open();
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

### Example 3: Setting the Symbol Icon

This example demonstrates how to use symbolStyle in PromptOptions to set custom symbol icons. This functionality is supported since API version 18.

```TypeScript
import { ExceptionPrompt, MarginType, SymbolGlyphModifier } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Column() {
      ExceptionPrompt({
        options: {
          icon: $r('sys.symbol.house'),
          tip: 'Error',
          marginType: MarginType.DEFAULT_MARGIN,
          actionText: 'Set network',
          marginTop: 80,
          isShown: true,
        },
      })
      ExceptionPrompt({
        options: {
          icon: $r('sys.symbol.house'),
          symbolStyle: new SymbolGlyphModifier($r('sys.symbol.bell')).fontColor([Color.Red]),
          tip: 'Error',
          marginType: MarginType.DEFAULT_MARGIN,
          actionText: 'Set network',
          marginTop: 200,
          isShown: true,
        },
      })
    }
  }
}
```
