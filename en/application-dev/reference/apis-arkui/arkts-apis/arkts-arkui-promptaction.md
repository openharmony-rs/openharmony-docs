# @ohos.promptAction

This module provides API for creating and displaying toasts, dialog boxes, and action menus.

> **NOTE:** 
> 
> - This module cannot be used in the file declaration of the [UIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-uiability-c.md). In other words, the APIs of this module can be used only after a component instance is created; they cannot be called in the lifecycle of the UIAbility.
> 
> - The functionality of this module depends on UI context. This means that the APIs of this module cannot be used where [the UI context is ambiguous](../../../ui/arkts-global-interface.md#ambiguous-ui-context). For details, see [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md). It is recommended that you use the dialog box APIs provided by
> **UIContext**<!--Del-->, except for UI-less scenarios such as
> [ServiceExtensionAbility](../../../application-models/serviceextensionability-sys.md)<!--DelEnd-->.

## Modules to Import

```TypeScript
import { promptAction, LevelMode, ImmersiveMode, LevelOrder } from '@kit.ArkUI';
```

## Summary

### Namespaces

| Name | Description |
| --- | --- |
| [promptAction](arkts-arkui-promptaction-n.md) | This module provides API for creating and displaying toasts, dialog boxes, and action menus. |

### Classes

| Name | Description |
| --- | --- |
| [LevelOrder](arkts-arkui-promptaction-levelorder-c.md) | Defines the display order of a dialog box. |

### Interfaces

| Name | Description |
| --- | --- |
| [DismissDialogAction](arkts-arkui-promptaction-dismissdialogaction-i.md) | Provides information about the action to dismiss the dialog box. |

### Enums

| Name | Description |
| --- | --- |
| [ImmersiveMode](arkts-arkui-promptaction-immersivemode-e.md) | Enumerates the display area modes of the dialog box overlay within a page. |
| [LevelMode](arkts-arkui-promptaction-levelmode-e.md) | Enumerates the display level modes of the dialog box. |

## Examples

This example demonstrates how to call the getState API of promptAction.DialogController to obtain the current state of a dialog box, supported since API version 20.

```TypeScript
// xxx.ets
import { BusinessError } from '@kit.BasicServicesKit';
import { ComponentContent, promptAction } from '@kit.ArkUI';

@Component
struct CustomDialogExample {
  build() {
    Column() {
      Text('Hello')
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .margin({ bottom: 36 })
      Button('Close Dialog Box')
        .onClick(() => {
          if (this.getDialogController()) {
            this.getDialogController().close();
          }
        })
      Button('Obtain State')
        .onClick(() => {
          if (this.getDialogController()) {
            let state: promptAction.CommonState = this.getDialogController().getState();
            switch (state) {
              case promptAction.CommonState.UNINITIALIZED: {
                console.info('The dialog state is uninitialized.');
                break;
              }
              case promptAction.CommonState.INITIALIZED: {
                console.info('The dialog state is initialized.');
                break;
              }
              case promptAction.CommonState.APPEARING: {
                console.info('The dialog state is appearing.');
                break;
              }
              case promptAction.CommonState.APPEARED: {
                console.info('The dialog state is appeared.');
                break;
              }
              case promptAction.CommonState.DISAPPEARING: {
                console.info('The dialog state is disappearing.');
                break;
              }
              case promptAction.CommonState.DISAPPEARED: {
                console.info('The dialog state is disappeared.');
                break;
              }
              default: {
                console.info('The dialog state is unknown.');
                break;
              }
            }
          }
        })

    }.backgroundColor('#FFF0F0F0')
  }
}

@Builder
function buildText() {
   CustomDialogExample()
}

@Entry
@Component
struct Index {

  private dialogController: promptAction.DialogController = new promptAction.DialogController()

  build() {
    Row() {
      Column() {
        Button("click me")
          .onClick(() => {
            let uiContext = this.getUIContext();
            let promptAction = uiContext.getPromptAction();
            let contentNode = new ComponentContent(uiContext, wrapBuilder(buildText),
            );

            promptAction.openCustomDialogWithController(contentNode, this.dialogController, {

              transition: TransitionEffect.OPACITY.animation({
                duration: 3000
              })
            }).then(() => {
              console.info('succeeded')
            }).catch((error: BusinessError) => {
              console.error(`OpenCustomDialogWithController args error code is ${error.code}, message is ${error.message}`);
            })
          })
      }
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}
```
