# promptAction

```TypeScript
declare namespace promptAction
```

This module provides API for creating and displaying toasts, dialog boxes, and action menus.

> **NOTE:** 
> 
> - This module cannot be used in the file declaration of the [UIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-uiability-c.md). In other words, the APIs of this module can be used only after a component instance is created; they cannot be called in the lifecycle of the UIAbility.
> 
> - The functionality of this module depends on UI context. This means that the APIs of this module cannot be used where [the UI context is ambiguous](../../../ui/arkts-global-interface.md#ambiguous-ui-context). For details, see [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md). It is recommended that you use the dialog box APIs provided by
> **UIContext**<!--Del-->, except for UI-less scenarios such as
> [ServiceExtensionAbility](../../../application-models/serviceextensionability-sys.md)<!--DelEnd-->.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { promptAction, LevelMode, ImmersiveMode, LevelOrder } from '@kit.ArkUI';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [showToast](arkts-arkui-promptaction-showtoast-f.md) | Creates and displays a toast. |
| [openToast](arkts-arkui-promptaction-opentoast-f.md) | Shows a toast. This API uses a promise to return the toast ID. |
| [closeToast](arkts-arkui-promptaction-closetoast-f.md) | Closes the specified toast. |
| [showDialog](arkts-arkui-promptaction-showdialog-f.md#showdialog) | Creates and displays a dialog box. This API uses an asynchronous callback to return the result. |
| [showDialog](arkts-arkui-promptaction-showdialog-f.md#showdialog-1) | Creates and displays a dialog box in the given settings. This API uses a promise to return the result. |
| [openCustomDialog](arkts-arkui-promptaction-opencustomdialog-f.md) | Opens a custom dialog box. This API uses a promise to return the result. |
| [closeCustomDialog](arkts-arkui-promptaction-closecustomdialog-f.md) | Closes the specified custom dialog box. |
| [showActionMenu](arkts-arkui-promptaction-showactionmenu-f.md#showactionmenu) | Creates and displays an action menu. This API uses an asynchronous callback to return the result. |
| [showActionMenu](arkts-arkui-promptaction-showactionmenu-f.md#showactionmenu-1) | Creates and displays an action menu in the given settings. This API uses a promise to return the result. |

### Classes

| Name | Description |
| --- | --- |
| [CommonController](arkts-arkui-promptaction-commoncontroller-c.md) | Implements a common controller for managing components related to **promptAction**. |
| [DialogController](arkts-arkui-promptaction-dialogcontroller-c.md) | Implements a custom dialog controller that inherits from [CommonController](arkts-arkui-promptaction-commoncontroller-c.md). |

### Interfaces

| Name | Description |
| --- | --- |
| [ShowToastOptions](arkts-arkui-promptaction-showtoastoptions-i.md) |  |
| [Button](arkts-arkui-promptaction-button-i.md) | Describes the menu item button in the action menu. |
| [ShowDialogSuccessResponse](arkts-arkui-promptaction-showdialogsuccessresponse-i.md) | Describes the dialog box response result. |
| [ShowDialogOptions](arkts-arkui-promptaction-showdialogoptions-i.md) | Describes the options for showing the dialog box. |
| [BaseDialogOptions](arkts-arkui-promptaction-basedialogoptions-i.md) | Defines the options of the dialog box. |
| [CustomDialogOptions](arkts-arkui-promptaction-customdialogoptions-i.md) | Extends [BaseDialogOptions](arkts-arkui-promptaction-basedialogoptions-i.md) to provide enhanced customization capabilities for the dialog box. |
| [DialogOptions](arkts-arkui-promptaction-dialogoptions-i.md) | Extends [BaseDialogOptions](arkts-arkui-promptaction-basedialogoptions-i.md) to provide enhanced customization capabilities for the dialog box. |
| [ActionMenuSuccessResponse](arkts-arkui-promptaction-actionmenusuccessresponse-i.md) | Describes the action menu response result. |
| [ActionMenuOptions](arkts-arkui-promptaction-actionmenuoptions-i.md) | Describes the options for showing the action menu. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [ShowDialogOptions](arkts-arkui-promptaction-showdialogoptions-i-sys.md) | Describes the options for showing the dialog box. |
| [BaseDialogOptions](arkts-arkui-promptaction-basedialogoptions-i-sys.md) | Defines the options of the dialog box. |
| [ActionMenuOptions](arkts-arkui-promptaction-actionmenuoptions-i-sys.md) | Describes the options for showing the action menu. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [DialogOptionsCornerRadius](arkts-arkui-promptaction-dialogoptionscornerradius-t.md) | Defines the allowed data types for specifying the background corner radius of a dialog box. |
| [DialogOptionsBorderWidth](arkts-arkui-promptaction-dialogoptionsborderwidth-t.md) | Defines the allowed data types for specifying the background border width of a dialog box. |
| [DialogOptionsBorderColor](arkts-arkui-promptaction-dialogoptionsbordercolor-t.md) | Defines the allowed data types for specifying the background border color of a dialog box. |
| [DialogOptionsBorderStyle](arkts-arkui-promptaction-dialogoptionsborderstyle-t.md) | Defines the allowed data types for specifying the background border style of a dialog box. |
| [DialogOptionsShadow](arkts-arkui-promptaction-dialogoptionsshadow-t.md) | Defines the allowed data types for specifying the background shadow of a dialog box. |

### Enums

| Name | Description |
| --- | --- |
| [ToastShowMode](arkts-arkui-promptaction-toastshowmode-e.md) | Enumerates display modes for toasts. By default, the toast is displayed within the application and supports display in subwindows. |
| [CommonState](arkts-arkui-promptaction-commonstate-e.md) | Enumerates states of the custom dialog box. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [ToastShowMode](arkts-arkui-promptaction-toastshowmode-e-sys.md) | Enumerates display modes for toasts. By default, the toast is displayed within the application and supports display in subwindows. |
<!--DelEnd-->

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
