# Popup Migration Guide
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @houguobiao-->
<!--Designer: @houguobiao-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=d465fc803a20f7fbc421724e5a688811e04797e4 translatedAt=2026-10-29T08:56:44.287Z pushedAt=2026-10-30T02:52:09.638Z nl=1 -->

## Overview

This document helps developers understand the capability differences between the new [@ohos.arkui.dialog (Popup)](../reference/apis-arkui/js-apis-dialog.md) interface and the old interfaces ([CustomDialogController](../reference/apis-arkui/arkui-ts/ts-methods-custom-dialog-box.md#customdialogcontroller), [showAlertDialog](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#showalertdialog), [showActionSheet](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#showactionsheet), [showDialog](../reference/apis-arkui/arkts-apis-uicontext-qpromptaction.md#showdialog), [showActionMenu](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#showactionmenu), [openCustomDialog](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#opencustomdialog12), [openCustomDialogWithController](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#opencustomdialogwithcontroller18), and [presentCustomDialog](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#presentcustomdialog18)), and provides migration mappings from the old interfaces to the new interface by dialog category.

Starting from API version 26.0.1, [@ohos.arkui.dialog (dialog box)](../reference/apis-arkui/js-apis-dialog.md) is added to provide unified Dialog type declaration capabilities.

## Available APIs

On the basis of fully supporting the capabilities of the old interfaces, [@ohos.arkui.dialog (dialog box)](../reference/apis-arkui/js-apis-dialog.md) additionally supports returning error codes. The key interfaces are listed in the following table.

| API | Description |
|--------|------|
| [DialogTextStyleOptions](../reference/apis-arkui/js-apis-dialog.md#dialogtextstyleoptions) | Defines text style attributes in a Dialog, which can be used as the text style of the message content. |
| [DialogButton](../reference/apis-arkui/js-apis-dialog.md#dialogbutton) | Button configuration for fixed-style dialogs. |
| [DialogSheet](../reference/apis-arkui/js-apis-dialog.md#dialogsheet) | Popup list configuration item, used for ActionSheet-style dialogs. |
| [DialogBaseOptions](../reference/apis-arkui/js-apis-dialog.md#dialogbaseoptions) | Basic options shared by all dialogs, defining common attributes such as the background, border, alignment, mask, and keyboard avoidance of a dialog. Both `DialogStyleOptions` and `DialogCustomOptions` inherit from this interface. |
| [DialogMessage](../reference/apis-arkui/js-apis-dialog.md#dialogmessage) | Message content and text style of a dialog, inheriting from `DialogTextStyleOptions`. |
| [DialogStyleOptions](../reference/apis-arkui/js-apis-dialog.md#dialogstyleoptions) | Options for fixed-style dialogs, inheriting from `DialogBaseOptions`. |
| [DialogCustomOptions](../reference/apis-arkui/js-apis-dialog.md#dialogcustomoptions) | Options for custom-style dialogs, inheriting from `DialogBaseOptions`. |
| [DialogBaseController](../reference/apis-arkui/js-apis-dialog.md#dialogbasecontroller) | Class used to control a dialog, which can be bound to the dialog through the controller attribute in `DialogBaseOptions`. |
| [DialogResult](../reference/apis-arkui/js-apis-dialog.md#dialogresult) | Response result of a dialog. |
| [DialogDismissal](../reference/apis-arkui/js-apis-dialog.md#dialogdismissal) | Provides the information and interface for closing a dialog. |
| [DialogBaseAlignment](../reference/apis-arkui/js-apis-dialog.md#dialogbasealignment) | Alignment of a dialog. |
| [DialogButtonOrientation](../reference/apis-arkui/js-apis-dialog.md#dialogbuttonorientation) | Arrangement of buttons in a dialog. |
| [DialogState](../reference/apis-arkui/js-apis-dialog.md#dialogstate) | Popup state enumeration. |

## Differences Between Old and New Dialog APIs

The old and new APIs differ in two dimensions: attributes and usage.

- **Attribute differences**: For each dialog type, the attribute mapping between the old and new interfaces is defined, along with the differences in advanced animation parameters. Each dialog type provides an attribute comparison table (covering programming model, content construction, alignment, offset, mask, border, shadow, animation callbacks, keyboard avoidance, floating mode, hierarchical mode, system material, and other attributes) and code examples before and after migration.
- **Usage differences**: Focuses on capabilities that are not supported by the old interface but are supported only by the new interface, including dynamically modifying the dialog position (alignment, offset, mask color, etc.) after the dialog is displayed without closing and reopening it, and supporting system material in custom dialog scenarios, with code examples provided.

### Attribute Differences

- CustomDialog (custom dialog)

  | Attribute | Old API ([CustomDialogController](../reference/apis-arkui/arkui-ts/ts-methods-custom-dialog-box.md#customdialogcontroller)) | New API ([DialogPresenter.present](../reference/apis-arkui/arkts-apis-uicontext-dialogpresenter.md#present)) |
  |------|------|------|
  | Programming model | Declare a custom component with the `@CustomDialog` decorator + instantiate and control it with `CustomDialogController` | Obtain the Presenter with `UIContext.getDialogPresenter()`, and present it with `present(content, options)` |
  | Content construction | The `@CustomDialog` decorator wraps `@Component` | `CustomBuilder` / `CustomBuilderWithId` / `ComponentContent<Object>` as the first parameter of `present` |
  | Style control | `customStyle: boolean` (CustomDialogControllerOptions) | `DialogCustomOptions.customStyle: boolean` |
  | Open | `controller.open()` | `presenter.present(content, options): Promise<DialogResult>` |
  | Close | `controller.close()` | `DialogBaseController.close()` or `presenter.dismiss(target)` |
  | State query | `controller.getState(): PromptActionCommonState` | `DialogBaseController.getState(): DialogState` |
  | Alignment | `alignment: DialogAlignment` | `alignment: DialogBaseAlignment` |
  | Offset | `offset: { dx, dy }` | `offset: Offset` |
  | Auto-cancel | `autoCancel: boolean` | `autoCancel: boolean` |
  | Mask color | `maskColor: ResourceColor` | `maskColor: ResourceColor` |
  | Mask area | `maskRect: Rectangle` | `maskRect: Rectangle` |
  | Modal | `isModal: boolean` | `isModal: boolean` |
  | Subwindow | `showInSubWindow: boolean` | `showInSubWindow: boolean` |
  | Focus | `focusable: boolean` (configurable, default true) | `focusable: boolean` (configurable, default true) |
  | Open animation callback | `onWillAppear` / `onDidAppear` / `onWillDisappear` / `onDidDisappear` | `onWillAppear` / `onDidAppear` / `onWillDisappear` / `onDidDisappear` |
  | Cancel callback | `cancel: () => void` + `onWillDismiss: Callback<DismissDialogAction>` | `onWillDismiss: Callback<DialogDismissal>` |
  | Background blur | `backgroundBlurStyle` + `backgroundBlurStyleOptions` + `backgroundEffect` | `backgroundBlurStyle` + `backgroundBlurStyleOptions` + `backgroundEffect` |
  | Border | `cornerRadius` / `borderWidth` / `borderColor` / `borderStyle` | `borderRadius` / `borderWidth` / `borderColor` / `borderStyle` (`cornerRadius` corresponds to `borderRadius`) |
  | Shadow | `shadow: ShadowOptions \| ShadowStyle` | `shadow: ShadowOptions \| ShadowStyle` |
  | Content area animation | `openAnimation` + `closeAnimation` (`AnimateParam`) | `dialogTransition: TransitionEffect` |
  | Mask animation | None | `maskTransition: TransitionEffect` |
  | Keyboard Avoidance | `keyboardAvoidMode` + `keyboardAvoidDistance` | `keyboardAvoidMode` + `keyboardAvoidDistance` |
  | Floating mode | `enableHoverMode` + `hoverModeArea` | `enableHoverMode` + `hoverModeArea` |
  | Hierarchical mode | `levelMode` + `levelUniqueId` + `immersiveMode` + `levelOrder` | `levelMode` + `levelUniqueId` + `immersiveMode` + `levelOrder` |
  | System material | `systemMaterial: SystemUiMaterial` | `systemMaterial: SystemUiMaterial` |<!--Del-->
  | System API attributes | `distortionMode`, `edgeLightMode` | `distortionMode`, `edgeLightMode` |
  <!--DelEnd-->
  
  **Before migration example (old interface):** Use the `open()` and `close()` methods of [CustomDialogController](../reference/apis-arkui/arkui-ts/ts-methods-custom-dialog-box.md#customdialogcontroller) to open and close a custom dialog.
  
  <!-- @[custom_dialog_before_migrate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/opencustomdialog/CustomDialogBeforeMigrate.ets) -->
  
  ``` TypeScript
  @CustomDialog
  struct CustomDialogExample {
    controller?: CustomDialogController
    build() {
      Column() {
        Text('Custom dialog content')
        Button('Close').onClick(() => { this.controller?.close() })
      }
    }
  }
  
  @Entry
  @Component
  export struct CustomDialogBeforeMigrate {
    dialogController: CustomDialogController = new CustomDialogController({
      builder: CustomDialogExample(),
      alignment: DialogAlignment.Center,
      autoCancel: true,
      maskColor: 0x33000000
    })
    build() {
      NavDestination() {
        Column() {
          Button('Open Dialog').onClick(() => {
            this.dialogController.open()
          })
        }
        .width('100%')
        .height('100%')
        .justifyContent(FlexAlign.Center)
      }
    }
  }
  ```
  
   ![Before migration example](figures/CustomDialogBeforeMigrate.png)
  
  **After migration example (new API):** Use the `present()` and `dismiss()` methods of [DialogPresenter](../reference/apis-arkui/arkts-apis-uicontext-dialogpresenter.md) to open and close a custom dialog, and obtain the return result through a Promise.
  
  <!-- @[custom_dialog_after_migrate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/opencustomdialog/CustomDialogAfterMigrate.ets) -->
  
  ``` TypeScript
  import { DialogPresenter, DialogBaseAlignment, DialogResult, ComponentContent } from '@kit.ArkUI';
  import { BusinessError } from '@kit.BasicServicesKit';
  
  // Define a parameter class to pass data to the custom dialog content.
  class Params {
    public text: string = '';
  
    constructor(text: string) {
      this.text = text;
    }
  }
  
  // Builder function for the custom dialog content.
  @Builder
  function buildText(params: Params) {
    Column({ space: 20 }) {
      Text(params.text)
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
        .margin({ bottom: 36 })
      // Button for closing the dialog, which closes the dialog through the ComponentContent reference.
      Button('Close Popup')
        .onClick(() => {
          dialogPresenter?.dismiss(contentNode)
            .then(() => {
              console.info('dismiss success');
            })
            .catch((error: BusinessError) => {
              console.error(`dismiss error code is ${error.code}, message is ${error.message}`);
            })
        })
    }
  }
  
  let contentNode: ComponentContent<Object> | null = null;
  // Global variable that stores the DialogPresenter instance.
  let dialogPresenter: DialogPresenter | null = null;
  
  @Entry
  @Component
  export struct CustomDialogAfterMigrate {
    @State result: string = '';
  
    aboutToAppear(): void {
      // Obtain the DialogPresenter instance.
      dialogPresenter = this.getUIContext().getDialogPresenter();
      // Create a ComponentContent and bind the custom builder function and parameters.
      contentNode = new ComponentContent(this.getUIContext(), wrapBuilder(buildText), new Params('Custom dialog content'));
    }
  
    build() {
      NavDestination() {
        Row() {
          Column() {
            Text('CustomDialog migration example')
              .fontSize(18)
              .fontWeight(FontWeight.Bold)
              .margin({ bottom: 20 })
  
            Button('Old API: @CustomDialog + CustomDialogController')
              .width('90%')
              .margin({ bottom: 10 })
              .onClick(() => {
                this.showOldCustomDialog();
              })
  
            Button('New API: DialogPresenter.present (Custom Dialog)')
              .width('90%')
              .margin({ bottom: 10 })
              .onClick(() => {
                this.showNewCustomDialog();
              })
  
            if (this.result) {
              Text(this.result)
                .fontSize(14)
                .margin({ top: 10 })
            }
          }
          .width('100%')
        }
        .height('100%')
      }
    }
  
    private showOldCustomDialog(): void {
      this.result = 'For the old interface example, see the DialogProject project.';
    }
  
    private showNewCustomDialog(): void {
      dialogPresenter?.present(contentNode, {
        alignment: DialogBaseAlignment.CENTER,
        autoCancel: true,
        maskColor: 0x33000000
      }).then((result: DialogResult) => {
        this.result = 'present success, dialogId: ' + result.dialogId;
      }).catch((error: BusinessError) => {
        this.result = `present error: ${error.code}`;
      });
    }
  }
  ```
  
  ![after migration example figure](figures/CustomDialogAfterMigrate.png)

- AlertDialog (alert dialog box)

  | Attribute | Old interface ([UIContext.showAlertDialog](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#showalertdialog)) | New interface ([DialogPresenter.present](../reference/apis-arkui/arkts-apis-uicontext-dialogpresenter.md#present)) |
  |------|------|------|
  | Programming model | `AlertDialog.show(options)` imperative call | `presenter.present(options): Promise<DialogResult>` |
  | Title | `title: ResourceStr` | `title: ResourceStr` |
  | Subtitle | `subtitle: ResourceStr` | `subtitle: ResourceStr` |
  | Message content | `message: ResourceStr` | `message: DialogMessage` (content + wordBreak) |
  | Text style | `textStyle: TextStyle` | `message.wordBreak: WordBreak` (set through DialogMessage) |
  | Button | `confirm` (single) / `primaryButton` + `secondaryButton` (two) / `buttons: Array<AlertDialogButtonOptions>` (multiple) | `buttons: Array<DialogButton>` (including value/fontColor/backgroundColor/enabled/primary/style/action) |
  | Button arrangement | `buttonDirection: DialogButtonDirection` | `buttonDirection: DialogButtonOrientation` |
  | Action menu | None | `sheets: Array<DialogSheet>` (action-sheet style) |
  | Grid count | `gridCount: number` | `gridCount: number` |
  | Confirm callback | `confirm` / `primaryButton.action` / `secondaryButton.action` / `buttons[].action` | `DialogButton.action` (through the Promise result) |
  | Cancel callback | `cancel: VoidCallback` + `onWillDismiss: Callback<DismissDialogAction>` | `onWillDismiss: Callback<DialogDismissal>` |
  | Alignment | `alignment: DialogAlignment` | `alignment: DialogBaseAlignment` |
  | Offset | `offset: Offset` | `offset: Offset` |
  | Auto-cancel | `autoCancel: boolean` | `autoCancel: boolean` |
  | Mask area | `maskRect: Rectangle` | `maskRect: Rectangle` |
  | Modal | `isModal: boolean` | `isModal: boolean` |
  | Subwindow | `showInSubWindow: boolean` | `showInSubWindow: boolean` |
  | Background color | `backgroundColor` | `backgroundColor` |
  | Background blur | `backgroundBlurStyle` + `backgroundBlurStyleOptions` + `backgroundEffect` | `backgroundBlurStyle` + `backgroundBlurStyleOptions` + `backgroundEffect` |
  | Border | `cornerRadius` / `borderWidth` / `borderColor` / `borderStyle` | `borderRadius` / `borderWidth` / `borderColor` / `borderStyle` (`cornerRadius` renamed to `borderRadius`) |
  | Shadow | `shadow: ShadowOptions \| ShadowStyle` | `shadow: ShadowOptions \| ShadowStyle` |
  | Size | `width` / `height` | `width` / `height` |
  | Transition animation | `transition: TransitionEffect` | `dialogTransition: TransitionEffect` |
  | Mask animation | None | `maskTransition: TransitionEffect` |
  | Open animation callback | `onWillAppear` / `onDidAppear` / `onWillDisappear` / `onDidDisappear` | `onWillAppear` / `onDidAppear` / `onWillDisappear` / `onDidDisappear` |
  | Floating mode | `enableHoverMode` + `hoverModeArea` | `enableHoverMode` + `hoverModeArea` |
  | Hierarchical mode | `levelMode` + `levelUniqueId` + `immersiveMode` + `levelOrder` | `levelMode` + `levelUniqueId` + `immersiveMode` + `levelOrder` |
  | System material | `systemMaterial: SystemUiMaterial` | `systemMaterial: SystemUiMaterial` |

  **Before migration example (old interface):** Use [showAlertDialog](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#showalertdialog) to display an alert dialog box, including a title, message, and buttons.

  <!-- @[alert_dialog_before_migrate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/opencustomdialog/AlertDialogBeforeMigrate.ets) -->
  
  ``` TypeScript
  @Entry
  @Component
  export struct AlertDialogBeforeMigrate {
    @State result: string = '';
  
    build() {
      NavDestination() {
        Column() {
          Button('Open AlertDialog')
            .onClick(() => {
              this.getUIContext().showAlertDialog({
                title: 'Information',
                message: 'Are you sure you want to delete it?',
                autoCancel: true,
                buttons: [
                  {
                    value: 'Cancel', action: () => {
                    this.result = 'Cancel';
                  }
                  },
                  {
                    value: 'OK', action: () => {
                    this.result = 'OK';
                  }
                  }
                ],
                cancel: () => {
                  this.result = 'cancel';
                }
              });
            })
  
          if (this.result) {
            Text(this.result)
              .fontSize(14)
              .margin({ top: 10 })
          }
        }
        .width('100%')
        .height('100%')
        .justifyContent(FlexAlign.Center)
      }
    }
  }
  ```
  
  ![before migration example figure](figures/AlertDialogBeforeMigrate.png)
  
  **After migration example (new interface):** Use [DialogPresenter.present](../reference/apis-arkui/arkts-apis-uicontext-dialogpresenter.md#present) to present an alert dialog, and obtain the button click result through a Promise.
  
  <!-- @[alert_dialog_after_migrate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/opencustomdialog/AlertDialogAfterMigrate.ets) -->
  
  ``` TypeScript
  import { DialogBaseAlignment, DialogDismissal, DialogPresenter, DialogResult } from '@kit.ArkUI';
  import { BusinessError } from '@kit.BasicServicesKit';
  
  @Entry
  @Component
  export struct AlertDialogAfterMigrate {
    private presenter: DialogPresenter = this.getUIContext().getDialogPresenter();
    @State result: string = '';
  
    build() {
      NavDestination() {
        Row() {
          Column() {
            Text('AlertDialog migration example')
              .fontSize(18)
              .fontWeight(FontWeight.Bold)
              .margin({ bottom: 20 })
  
            Button('Old API: showAlertDialog')
              .width('90%')
              .margin({ bottom: 10 })
              .onClick(() => {
                this.result = 'For the old interface example, see ts-methods-alert-dialog-box.md';
              })
  
            Button('New API: DialogPresenter.present (Fixed-Style Dialog)')
              .width('90%')
              .margin({ bottom: 10 })
              .onClick(() => {
                this.showNewAlertDialog();
              })
  
            if (this.result) {
              Text(this.result)
                .fontSize(14)
                .margin({ top: 10 })
            }
          }
          .width('100%')
        }
        .height('100%')
      }
    }
  
    private showNewAlertDialog(): void {
      this.presenter.present({
        title: 'Information',
        message: { content: 'Are you sure you want to delete it?' },
        buttons: [
          {
            value: 'Cancel', action: () => {
            this.result = 'User tapped Cancel';
          }
          },
          {
            value: 'OK', action: () => {
            this.result = 'User tapped OK';
          }
          }
        ],
        alignment: DialogBaseAlignment.BOTTOM,
        onWillDismiss: (dismissal: DialogDismissal) => {
          this.result = 'onWillDismiss, reason: ' + dismissal.reason;
          dismissal.dismiss();
        }
      }).then((result: DialogResult) => {
        this.result = 'present success, dialogId: ' + result.dialogId;
      }).catch((error: BusinessError) => {
        this.result = `present error: ${error.code}`;
      });
    }
  }
  ```
  
  ![After migration example](figures/AlertDialogAfterMigrate.png)

- ActionSheet (action sheet)

  | Attribute | Old API ([UIContext.showActionSheet](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#showactionsheet)) | New API ([DialogPresenter.present](../reference/apis-arkui/arkts-apis-uicontext-dialogpresenter.md#present)) |
  |------|------|------|
  | Programming model | `ActionSheet.show(options)` imperative call | `presenter.present(options): Promise<DialogResult>` |
  | Title | `title: string \| Resource` | `title: ResourceStr` |
  | Subtitle | `subtitle: ResourceStr` | `subtitle: ResourceStr` |
  | Message content | `message: string \| Resource` | `message: DialogMessage` (content + wordBreak) |
  | Button | `confirm: ActionSheetButtonOptions` (single confirm button) | `buttons: Array<DialogButton>` |
  | Button arrangement | None | `buttonDirection: DialogButtonOrientation` |
  | Action menu | `sheets: Array<SheetInfo>` (title/icon/action) | `sheets: Array<DialogSheet>` (title/icon/action) |
  | Grid count | None | `gridCount: number` |
  | Confirm callback | `confirm.action: VoidCallback` | `DialogButton.action` |
  | Cancel callback | `cancel: VoidCallback` + `onWillDismiss: Callback<DismissDialogAction>` | `onWillDismiss: Callback<DialogDismissal>` |
  | Alignment | `alignment: DialogAlignment` | `alignment: DialogBaseAlignment` |
  | Offset | `offset: ActionSheetOffset` (with dx/dy) | `offset: Offset` (with dx/dy) |
  | Auto-cancel | `autoCancel: boolean` | `autoCancel: boolean` |
  | Mask area | `maskRect: Rectangle` | `maskRect: Rectangle` |
  | Modal | `isModal: boolean` | `isModal: boolean` |
  | Subwindow | `showInSubWindow: boolean` | `showInSubWindow: boolean` |
  | Background color | `backgroundColor` | `backgroundColor` |
  | Background blur | `backgroundBlurStyle` + `backgroundBlurStyleOptions` + `backgroundEffect` | `backgroundBlurStyle` + `backgroundBlurStyleOptions` + `backgroundEffect` |
  | Border | `cornerRadius` / `borderWidth` / `borderColor` / `borderStyle` | `borderRadius` / `borderWidth` / `borderColor` / `borderStyle` (`cornerRadius` renamed to `borderRadius`) |
  | Shadow | `shadow: ShadowOptions \| ShadowStyle` | `shadow: ShadowOptions \| ShadowStyle` |
  | Size | `width` / `height` | `width` / `height` |
  | Transition animation | `transition: TransitionEffect` | `dialogTransition: TransitionEffect` |
  | Mask animation | None | `maskTransition: TransitionEffect` |
  | Open animation callback | `onWillAppear` / `onDidAppear` / `onWillDisappear` / `onDidDisappear` | `onWillAppear` / `onDidAppear` / `onWillDisappear` / `onDidDisappear` |
  | Floating mode | `enableHoverMode` + `hoverModeArea` | `enableHoverMode` + `hoverModeArea` |
  | Hierarchical mode | `levelMode` + `levelUniqueId` + `immersiveMode` + `levelOrder` | `levelMode` + `levelUniqueId` + `immersiveMode` + `levelOrder` |
  | System material | `systemMaterial: SystemUiMaterial` | `systemMaterial: SystemUiMaterial` |

  **Before migration example (old interface):** Use [showActionSheet](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#showactionsheet) to display an action sheet that includes a title and menu items.
  
  <!-- @[action_sheet_before_migrate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/opencustomdialog/ActionSheetBeforeMigrate.ets) -->
  
  ``` TypeScript
  @Entry
  @Component
  export struct ActionSheetBeforeMigrate {
    @State result: string = '';
  
    build() {
      NavDestination() {
        Column() {
          Button('Open ActionSheet')
            .onClick(() => {
              this.getUIContext().showActionSheet({
                title: 'Select',
                message: 'Please select an action.',
                autoCancel: true,
                sheets: [
                  {
                    title: 'Copy', action: () => {
                    this.result = 'Copy';
                  }
                  },
                  {
                    title: 'Delete', action: () => {
                    this.result = 'Delete';
                  }
                  }
                ],
                cancel: () => {
                  this.result = 'Cancel';
                }
              });
            })
  
          if (this.result) {
            Text(this.result)
              .fontSize(14)
              .margin({ top: 10 })
          }
        }
        .width('100%')
        .height('100%')
        .justifyContent(FlexAlign.Center)
      }
    }
  }
  ```
  
  ![Before migration example](figures/ActionSheetBeforeMigrate.png)
  
  **After migration example (new interface):** Use [DialogPresenter.present](../reference/apis-arkui/arkts-apis-uicontext-dialogpresenter.md#present) to present an action sheet, and obtain the selection result through a Promise.
  
  <!-- @[action_sheet_after_migrate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/opencustomdialog/ActionSheetAfterMigrate.ets) -->
  
  ``` TypeScript
  import { DialogDismissal, DialogPresenter, DialogResult } from '@kit.ArkUI';
  import { BusinessError } from '@kit.BasicServicesKit';
  
  @Entry
  @Component
  export struct ActionSheetAfterMigrate {
    private presenter: DialogPresenter = this.getUIContext().getDialogPresenter();
    @State result: string = '';
  
    build() {
      NavDestination() {
        Row() {
          Column() {
            Text('ActionSheet migration example')
              .fontSize(18)
              .fontWeight(FontWeight.Bold)
              .margin({ bottom: 20 })
  
            Button('Old API: showActionSheet')
              .width('90%')
              .margin({ bottom: 10 })
              .onClick(() => {
                this.result = 'For the old interface example, see ts-methods-action-sheet.md';
              })
  
            Button('New API: DialogPresenter.present (action sheet)')
              .width('90%')
              .margin({ bottom: 10 })
              .onClick(() => {
                this.showNewActionSheet();
              })
  
            if (this.result) {
              Text(this.result)
                .fontSize(14)
                .margin({ top: 10 })
            }
          }
          .width('100%')
        }
        .height('100%')
      }
    }
  
    private showNewActionSheet(): void {
      this.presenter.present({
        title: 'Select',
        message: { content: 'Select an action' },
        autoCancel: true,
        sheets: [
          { title: 'Copy', action: () => { this.result = 'Copy'; } },
          { title: 'Delete', action: () => { this.result = 'Delete'; } }
        ],
        onWillDismiss: (dismissal: DialogDismissal) => {
          this.result = 'Cancel';
          dismissal.dismiss();
        }
      }).then((result: DialogResult) => {
        this.result = 'present success, dialogId: ' + result.dialogId;
      }).catch((error: BusinessError) => {
        this.result = `present error: ${error.code}`;
      });
    }
  }
  ```
  
  ![After migration example](figures/ActionSheetAfterMigrate.png)

- promptAction.showDialog (dialog box)

  | Attribute | Old interface ([promptAction.showDialog](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#showdialog)) | New interface ([DialogPresenter.present](../reference/apis-arkui/arkts-apis-uicontext-dialogpresenter.md#present)) |
  |------|------|------|
  | Programming model | `promptAction.showDialog(options): Promise<ShowDialogSuccessResponse>` | `presenter.present(options): Promise<DialogResult>` |
  | Title | `title: string \| Resource` | `title: ResourceStr` |
  | Subtitle | None | `subtitle: ResourceStr` |
  | Message content | `message: string \| Resource` | `message: DialogMessage` (content + wordBreak) |
  | Button | `buttons: Array<Button>` (text + color + primary only) | `buttons: Array<DialogButton>` (including value/fontColor/backgroundColor/enabled/primary/style/action) |
  | Button arrangement | None | `buttonDirection: DialogButtonOrientation` |
  | Action menu | None | `sheets: Array<DialogSheet>` |
  | Grid count | None | `gridCount: number` |
  | Confirm callback | Obtains the button index through `ShowDialogSuccessResponse.index` | `DialogButton.action` + Promise result |
  | Cancel callback | None | `onWillDismiss: Callback<DialogDismissal>` |
  | Alignment | `alignment: DialogAlignment` | `alignment: DialogBaseAlignment` |
  | Offset | `offset: Offset` | `offset: Offset` |
  | Auto-cancel | None | `autoCancel: boolean` |
  | Mask color | None | `maskColor: ResourceColor` |
  | Mask area | `maskRect: Rectangle` | `maskRect: Rectangle` |
  | Modal | `isModal: boolean` | `isModal: boolean` |
  | Subwindow | `showInSubWindow: boolean` | `showInSubWindow: boolean` |
  | Background color | `backgroundColor` | `backgroundColor` |
  | Background blur | `backgroundBlurStyle` + `backgroundBlurStyleOptions` + `backgroundEffect` | `backgroundBlurStyle` + `backgroundBlurStyleOptions` + `backgroundEffect` |
  | Border | None | `borderRadius` / `borderWidth` / `borderColor` / `borderStyle` |
  | Shadow | `shadow: ShadowOptions \| ShadowStyle` | `shadow: ShadowOptions \| ShadowStyle` |
  | Size | None | `width` / `height` |
  | Transition animation | None | `dialogTransition: TransitionEffect` |
  | Mask animation | None | `maskTransition: TransitionEffect` |
  | Open animation callback | `onWillAppear` / `onDidAppear` / `onWillDisappear` / `onDidDisappear` | `onWillAppear` / `onDidAppear` / `onWillDisappear` / `onDidDisappear` |
  | Floating mode | `enableHoverMode` + `hoverModeArea` | `enableHoverMode` + `hoverModeArea` |
  | Hierarchical mode | `levelMode` + `levelUniqueId` + `immersiveMode` + `levelOrder` | `levelMode` + `levelUniqueId` + `immersiveMode` + `levelOrder` |
  | System material | `systemMaterial: SystemUiMaterial` | `systemMaterial: SystemUiMaterial` |

  **Before migration example (old interface):** Use [showDialog](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#showdialog) to display a dialog that includes a title, message, and buttons.
  
  <!-- @[show_dialog_before_migrate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/opencustomdialog/ShowDialogBeforeMigrate.ets) -->
  
  ``` TypeScript
  import { BusinessError } from '@kit.BasicServicesKit';
  
  @Entry
  @Component
  export struct ShowDialogBeforeMigrate {
    @State result: string = '';
  
    build() {
      NavDestination() {
        Column() {
          Button('Open showDialog')
            .onClick(() => {
              this.getUIContext()
                .getPromptAction()
                .showDialog({
                  title: 'Information',
                  message: 'Confirm deletion?',
                  buttons: [
                    { text: 'Cancel', color: '#666666' },
                    { text: 'OK', color: '#0000FF' }
                  ]
                })
                .then((data) => {
                  this.result = 'click button index: ' + data.index;
                })
                .catch((error: BusinessError) => {
                  this.result = `showDialog error: ${error.code}`;
                });
            })
  
          if (this.result) {
            Text(this.result)
              .fontSize(14)
              .margin({ top: 10 })
          }
        }
        .width('100%')
        .height('100%')
        .justifyContent(FlexAlign.Center)
      }
    }
  }
  ```
  
  ![Before migration example](figures/ShowDialogBeforeMigrate.png)
  
  **After migration example (new interface):** Use [DialogPresenter.present](../reference/apis-arkui/arkts-apis-uicontext-dialogpresenter.md#present) to display a dialog and obtain the button click result through a Promise.
  
  <!-- @[show_dialog_after_migrate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/opencustomdialog/ShowDialogAfterMigrate.ets) -->
  
  ``` TypeScript
  import { DialogPresenter, DialogResult } from '@kit.ArkUI';
  import { BusinessError } from '@kit.BasicServicesKit';
  
  @Entry
  @Component
  export struct ShowDialogAfterMigrate {
    private presenter: DialogPresenter = this.getUIContext().getDialogPresenter();
    @State result: string = '';
  
    build() {
      NavDestination() {
        Row() {
          Column() {
            Text('showDialog migration example')
              .fontSize(18)
              .fontWeight(FontWeight.Bold)
              .margin({ bottom: 20 })
  
            Button('Old API: promptAction.showDialog')
              .width('90%')
              .margin({ bottom: 10 })
              .onClick(() => {
                this.result = 'For the old interface example, see js-apis-promptAction.md';
              })
  
            Button('New API: DialogPresenter.present (dialog box)')
              .width('90%')
              .margin({ bottom: 10 })
              .onClick(() => {
                this.showNewDialog();
              })
  
            if (this.result) {
              Text(this.result)
                .fontSize(14)
                .margin({ top: 10 })
            }
          }
          .width('100%')
        }
        .height('100%')
      }
    }
  
    private showNewDialog(): void {
      this.presenter.present({
        title: 'Information',
        message: { content: 'Are you sure you want to delete it?' },
        buttons: [
          { value: 'Cancel', action: () => { this.result = 'Cancel'; } },
          { value: 'OK', action: () => { this.result = 'OK'; } }
        ]
      }).then((result: DialogResult) => {
        this.result = 'present success, dialogId: ' + result.dialogId;
      }).catch((error: BusinessError) => {
        this.result = `present error: ${error.code}`;
      });
    }
  }
  ```
  
  ![After migration example](figures/ShowDialogAfterMigrate.png)

- promptAction.showActionMenu (action menu)

  | Attribute | Old interface ([promptAction.showActionMenu](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#showactionmenu)) | New interface ([DialogPresenter.present](../reference/apis-arkui/arkts-apis-uicontext-dialogpresenter.md#present)) |
  |------|------|------|
  | Programming model | `promptAction.showActionMenu(options): Promise<ActionMenuSuccessResponse>` | `presenter.present(options): Promise<DialogResult>` |
  | Title | `title: string \| Resource` | `title: ResourceStr` |
  | Subtitle | None | `subtitle: ResourceStr` |
  | Message content | None | `message: DialogMessage` |
  | Button | `buttons: [Button, ...]` (supports 1 to 6 buttons, with the structure of only text + color + primary) | `buttons: Array<DialogButton>` (no quantity limit, with the structure containing value/fontColor/backgroundColor/enabled/primary/style/action) |
  | Button arrangement | None | `buttonDirection: DialogButtonOrientation` |
  | Action menu | None | `sheets: Array<DialogSheet>` |
  | Grid count | None | `gridCount: number` |
  | Confirm callback | Obtain the button index through `ActionMenuSuccessResponse.index` | `DialogButton.action` + Promise result |
  | Cancel callback | None | `onWillDismiss: Callback<DialogDismissal>` |
  | Alignment | None | `alignment: DialogBaseAlignment` |
  | Offset | None | `offset: Offset` |
  | Auto-cancel | None | `autoCancel: boolean` |
  | Mask color | None | `maskColor: ResourceColor` |
  | Mask area | None | `maskRect: Rectangle` |
  | Modal | `isModal: boolean` | `isModal: boolean` |
  | Subwindow | `showInSubWindow: boolean` | `showInSubWindow: boolean` |
  | Background color | None | `backgroundColor` |
  | Background blur | None | `backgroundBlurStyle` + `backgroundBlurStyleOptions` + `backgroundEffect` |
  | Border | None | `borderRadius` / `borderWidth` / `borderColor` / `borderStyle` |
  | Shadow | None | `shadow: ShadowOptions \| ShadowStyle` |
  | Size | None | `width` / `height` |
  | Transition animation | None | `dialogTransition: TransitionEffect` |
  | Mask animation | None | `maskTransition: TransitionEffect` |
  | Open animation callback | `onWillAppear` / `onDidAppear` / `onWillDisappear` / `onDidDisappear` | `onWillAppear` / `onDidAppear` / `onWillDisappear` / `onDidDisappear` |
  | Floating mode | None | `enableHoverMode` + `hoverModeArea` |
  | Hierarchical mode | `levelMode` + `levelUniqueId` + `immersiveMode` | `levelMode` + `levelUniqueId` + `immersiveMode` + `levelOrder` |
  | System material | `systemMaterial: SystemUiMaterial` | `systemMaterial: SystemUiMaterial` |

  **Before migration example (old interface):** Use [showActionMenu](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#showactionmenu) to display an action menu, including a title and menu items.
  
  <!-- @[action_menu_before_migrate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/opencustomdialog/ActionMenuBeforeMigrate.ets) -->
  
  ``` TypeScript
  import { BusinessError } from '@kit.BasicServicesKit';
  
  @Entry
  @Component
  export struct ActionMenuBeforeMigrate {
    @State result: string = '';
  
    build() {
      NavDestination() {
        Column() {
          Button('Open showActionMenu')
            .onClick(() => {
              this.getUIContext()
                .getPromptAction()
                .showActionMenu({
                  title: 'Select',
                  buttons: [
                    { text: 'Save', color: '#0000FF' },
                    { text: 'Share', color: '#0000FF' },
                    { text: 'Delete', color: '#FF0000' }
                  ]
                })
                .then((data) => {
                  this.result = 'click button index: ' + data.index;
                })
                .catch((error: BusinessError) => {
                  this.result = `showActionMenu error: ${error.code}`;
                });
            })
  
          if (this.result) {
            Text(this.result)
              .fontSize(14)
              .margin({ top: 10 })
          }
        }
        .width('100%')
        .height('100%')
        .justifyContent(FlexAlign.Center)
      }
    }
  }
  ```
  
  ![before migration example](figures/ActionMenuBeforeMigrate.png)
  
  **After migration example (new interface):** Use [DialogPresenter.present](../reference/apis-arkui/arkts-apis-uicontext-dialogpresenter.md#present) to present an action menu, and obtain the selection result through a Promise.
  
  <!-- @[action_menu_after_migrate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/opencustomdialog/ActionMenuAfterMigrate.ets) -->
  
  ``` TypeScript
  import { DialogPresenter, DialogResult } from '@kit.ArkUI';
  import { BusinessError } from '@kit.BasicServicesKit';
  
  @Entry
  @Component
  export struct ActionMenuAfterMigrate {
    private presenter: DialogPresenter = this.getUIContext().getDialogPresenter();
    @State result: string = '';
  
    build() {
      NavDestination() {
        Row() {
          Column() {
            Text('showActionMenu migration example')
              .fontSize(18)
              .fontWeight(FontWeight.Bold)
              .margin({ bottom: 20 })
  
            Button('Old API: promptAction.showActionMenu')
              .width('90%')
              .margin({ bottom: 10 })
              .onClick(() => {
                this.result = 'For the old interface example, see js-apis-promptAction.md';
              })
  
            Button('New API: DialogPresenter.present (action menu)')
              .width('90%')
              .margin({ bottom: 10 })
              .onClick(() => {
                this.showNewActionMenu();
              })
  
            if (this.result) {
              Text(this.result)
                .fontSize(14)
                .margin({ top: 10 })
            }
          }
          .width('100%')
        }
        .height('100%')
      }
    }
  
    private showNewActionMenu(): void {
      this.presenter.present({
        title: 'Select',
        buttons: [
          { value: 'Save', action: () => { this.result = 'Save'; } },
          { value: 'Share', action: () => { this.result = 'Share'; } },
          { value: 'Delete', action: () => { this.result = 'Delete'; } }
        ]
      }).then((result: DialogResult) => {
        this.result = 'present success, dialogId: ' + result.dialogId;
      }).catch((error: BusinessError) => {
        this.result = `present error: ${error.code}`;
      });
    }
  }
  ```
  
  ![After migration example](figures/ActionMenuAfterMigrate.png)

- promptAction.presentCustomDialog (custom dialog)

  | Attribute | Old interface ([promptAction.presentCustomDialog](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#presentcustomdialog18)) | New interface ([DialogPresenter.present](../reference/apis-arkui/arkts-apis-uicontext-dialogpresenter.md#present)) |
  |------|------|------|
  | Programming model | `promptAction.presentCustomDialog(builder, controller?, options?): Promise<number>` | `presenter.present(content, options?: DialogCustomOptions): Promise<DialogResult>` |
  | Content construction | `CustomBuilder` / `CustomBuilderWithId` | `CustomBuilder` / `CustomBuilderWithId` / `ComponentContent<Object>` |
  | Controller | `promptAction.DialogController` | `DialogBaseController` |
  | Option type | `DialogOptions` (inherits from `BaseDialogOptions`) | `DialogCustomOptions` (inherits from `DialogBaseOptions`) |
  | Style control | No `customStyle` attribute (content style is fully determined by the builder) | `customStyle: boolean` |
  | Alignment | `alignment: DialogAlignment` | `alignment: DialogBaseAlignment` |
  | Offset | `offset: Offset` | `offset: Offset` |
  | Auto-cancel | `autoCancel: boolean` | `autoCancel: boolean` |
  | Mask color | `maskColor: ResourceColor` | `maskColor: ResourceColor` |
  | Mask area | `maskRect: Rectangle` | `maskRect: Rectangle` |
  | Modal | `isModal: boolean` | `isModal: boolean` |
  | Subwindow | `showInSubWindow: boolean` | `showInSubWindow: boolean` |
  | Background color | `backgroundColor` (`DialogOptions`) | `backgroundColor` |
  | Background blur | `backgroundBlurStyle` (`DialogOptions`) + `backgroundBlurStyleOptions` + `backgroundEffect` | `backgroundBlurStyle` + `backgroundBlurStyleOptions` + `backgroundEffect` |
  | Border | `cornerRadius` / `borderWidth` / `borderColor` / `borderStyle` (`DialogOptions`) | `borderRadius` / `borderWidth` / `borderColor` / `borderStyle` (`cornerRadius` renamed to `borderRadius`) |
  | Shadow | `shadow` (`DialogOptions`) | `shadow: ShadowOptions \| ShadowStyle` |
  | Size | `width` / `height` (`DialogOptions`) | `width` / `height` |
  | Transition animation | `transition: TransitionEffect` / `dialogTransition` | `dialogTransition: TransitionEffect` |
  | Mask animation | `maskTransition: TransitionEffect` | `maskTransition: TransitionEffect` |
  | Focus | `focusable: boolean` | `focusable: boolean` |
  | Open animation callback | `onWillAppear` / `onDidAppear` / `onWillDisappear` / `onDidDisappear` | `onWillAppear` / `onDidAppear` / `onWillDisappear` / `onDidDisappear` |
  | Cancel callback | `onWillDismiss: Callback<DismissDialogAction>` | `onWillDismiss: Callback<DialogDismissal>` |
  | Keyboard Avoidance | `keyboardAvoidMode` + `keyboardAvoidDistance`  | `keyboardAvoidMode` + `keyboardAvoidDistance` |
  | Floating mode | `enableHoverMode`  + `hoverModeArea`  | `enableHoverMode` + `hoverModeArea` |
  | Hierarchical mode | `levelMode`  + `levelUniqueId`  + `immersiveMode`  + `levelOrder`  | `levelMode` + `levelUniqueId` + `immersiveMode` + `levelOrder` |
  | System material | `systemMaterial: SystemUiMaterial`  | `systemMaterial: SystemUiMaterial` |

  **Before migration example (old interface):** Use [presentCustomDialog](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#presentcustomdialog18) to present a custom dialog.
  
  <!-- @[present_custom_dialog_before_migrate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/opencustomdialog/PresentCustomDialogBeforeMigrate.ets) -->
  
  ``` TypeScript
  import { promptAction } from '@kit.ArkUI';
  import { BusinessError } from '@kit.BasicServicesKit';
  
  @Entry
  @Component
  export struct PresentCustomDialogBeforeMigrate {
    private dialogController: promptAction.DialogController = new promptAction.DialogController();
    @State result: string = '';
  
    @Builder customDialogComponent() {
      Column() {
        Text('Custom dialog content')
          .fontSize(16)
          .margin({ bottom: 10 })
        Button('Close dialog')
          .onClick(() => {
            this.dialogController.close();
          })
      }
      .padding(20)
    }
  
    build() {
      NavDestination() {
        Column() {
          Button('Open presentCustomDialog')
            .onClick(() => {
              this.getUIContext()
                .getPromptAction()
                .presentCustomDialog(() => {
                  this.customDialogComponent()
                }, this.dialogController, { autoCancel: true })
                .then((dialogId: number) => {
                  this.result = 'present success, dialogId: ' + dialogId;
                })
                .catch((error: BusinessError) => {
                  this.result = `present error: ${error.code}`;
                });
            })
  
          if (this.result) {
            Text(this.result)
              .fontSize(14)
              .margin({ top: 10 })
          }
        }
        .width('100%')
        .height('100%')
        .justifyContent(FlexAlign.Center)
      }
    }
  }
  ```
  
  ![Before migration example](figures/PresentCustomDialogBeforeMigrate.png)
  
  **After migration example (new interface):** Use [DialogPresenter.present](../reference/apis-arkui/arkts-apis-uicontext-dialogpresenter.md#present) to present a custom dialog and obtain the return result through a Promise.
  
  <!-- @[present_custom_dialog_after_migrate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/opencustomdialog/PresentCustomDialogAfterMigrate.ets) -->
  
  ``` TypeScript
  import { DialogBaseController, DialogPresenter, DialogResult } from '@kit.ArkUI';
  import { BusinessError } from '@kit.BasicServicesKit';
  
  @Entry
  @Component
  export struct PresentCustomDialogAfterMigrate {
    private presenter: DialogPresenter = this.getUIContext().getDialogPresenter();
    private controller: DialogBaseController = new DialogBaseController();
    @State result: string = '';
  
    build() {
      NavDestination() {
        Row() {
          Column() {
            Text('presentCustomDialog migration example')
              .fontSize(18)
              .fontWeight(FontWeight.Bold)
              .margin({ bottom: 20 })
  
            Button('Old interface: promptAction.presentCustomDialog')
              .width('90%')
              .margin({ bottom: 10 })
              .onClick(() => {
                this.result = 'For the old interface example, see arkts-apis-uicontext-promptaction.md';
              })
  
            Button('New interface: DialogPresenter.present (custom dialog)')
              .width('90%')
              .margin({ bottom: 10 })
              .onClick(() => {
                this.showNewCustomDialog();
              })
  
            if (this.result) {
              Text(this.result)
                .fontSize(14)
                .margin({ top: 10 })
            }
          }
          .width('100%')
        }
        .height('100%')
      }
    }
  
    @Builder
    CustomComponentContent() {
      Column() {
        Text('Custom dialog content')
          .fontSize(16)
          .margin({ bottom: 10 })
        Button('Close dialog')
          .onClick(() => {
            this.controller.close();
          })
      }
      .padding(20)
    }
  
    private showNewCustomDialog(): void {
      this.presenter.present(() => {
        this.CustomComponentContent()
      }, {
        controller: this.controller,
        autoCancel: true
      }).then((result: DialogResult) => {
        this.result = 'present success, dialogId: ' + result.dialogId;
      }).catch((error: BusinessError) => {
        this.result = `present error: ${error.code}`;
      });
    }
  }
  ```
  
  ![After migration example](figures/PresentCustomDialogAfterMigrate.png)

- promptAction.openCustomDialogWithController (custom dialog with a controller)

  | Attribute | Old API ([promptAction.openCustomDialogWithController](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#opencustomdialogwithcontroller18)) | New API ([DialogPresenter.present](../reference/apis-arkui/arkts-apis-uicontext-dialogpresenter.md#present)) |
  |------|------|------|
  | Programming Model | `promptAction.openCustomDialogWithController(content, controller, options?): Promise<void>` | `presenter.present(content, options?: DialogCustomOptions): Promise<DialogResult>` |
  | Content construction | `ComponentContent<Object>` | `CustomBuilder` / `CustomBuilderWithId` / `ComponentContent<Object>` |
  | Controller | `promptAction.DialogController`  | `DialogBaseController` |
  | Option type | `BaseDialogOptions` | `DialogCustomOptions` (inherits from `DialogBaseOptions`) |
  | Style control | No `customStyle` attribute (the content style is fully determined by ComponentContent) | `customStyle: boolean` |
  | Alignment | `alignment: DialogAlignment` | `alignment: DialogBaseAlignment` |
  | Offset | `offset: Offset` | `offset: Offset` |
  | Auto-cancel | `autoCancel: boolean`  | `autoCancel: boolean` |
  | Mask color | `maskColor: ResourceColor`  | `maskColor: ResourceColor` |
  | Mask area | `maskRect: Rectangle` | `maskRect: Rectangle` |
  | Modal | `isModal: boolean` | `isModal: boolean` |
  | Subwindow | `showInSubWindow: boolean` | `showInSubWindow: boolean` |
  | Background color | None (`BaseDialogOptions` does not contain `backgroundColor`) | `backgroundColor` |
  | Background blur | `backgroundBlurStyleOptions`  + `backgroundEffect`  | `backgroundBlurStyle` + `backgroundBlurStyleOptions` + `backgroundEffect` |
  | Border | None (`BaseDialogOptions` does not contain border attributes) | `borderRadius` / `borderWidth` / `borderColor` / `borderStyle` |
  | Shadow | None (`BaseDialogOptions` does not contain `shadow`) | `shadow: ShadowOptions \| ShadowStyle` |
  | Size | None (`BaseDialogOptions` does not contain `width` / `height`) | `width` / `height` |
  | Transition animation | `transition: TransitionEffect`  / `dialogTransition`  | `dialogTransition: TransitionEffect` |
  | Mask animation | `maskTransition: TransitionEffect`  | `maskTransition: TransitionEffect` |
  | Focus | `focusable: boolean`  | `focusable: boolean` |
  | Open animation callback | `onWillAppear` / `onDidAppear` / `onWillDisappear` / `onDidDisappear`  | `onWillAppear` / `onDidAppear` / `onWillDisappear` / `onDidDisappear` |
  | Cancel callback | `onWillDismiss: Callback<DismissDialogAction>`  | `onWillDismiss: Callback<DialogDismissal>` |
  | Keyboard Avoidance | `keyboardAvoidMode`  + `keyboardAvoidDistance`  | `keyboardAvoidMode` + `keyboardAvoidDistance` |
  | Floating mode | `enableHoverMode`  + `hoverModeArea`  | `enableHoverMode` + `hoverModeArea` |
  | Hierarchical mode | `levelMode`  + `levelUniqueId`  + `immersiveMode`  + `levelOrder`  | `levelMode` + `levelUniqueId` + `immersiveMode` + `levelOrder` |
  | System material | `systemMaterial: SystemUiMaterial`  | `systemMaterial: SystemUiMaterial` |

  **Before migration example (old interface):** Use [openCustomDialogWithController](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#opencustomdialogwithcontroller18) to present a custom dialog with a controller.
  
  <!-- @[open_custom_dialog_with_controller_before_migrate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/opencustomdialog/OpenCustomDialogWithControllerBeforeMigrate.ets) -->
  
  ``` TypeScript
  import { ComponentContent, promptAction } from '@kit.ArkUI';
  import { BusinessError } from '@kit.BasicServicesKit';
  
  class Params {
    public text: string = '';
  
    constructor(text: string) {
      this.text = text;
    }
  }
  
  @Builder
  function buildText(params: Params) {
    Column() {
      Text(params.text)
        .fontSize(16)
        .margin({ bottom: 10 })
    }
    .padding(20)
  }
  
  @Entry
  @Component
  export struct OpenCustomDialogWithControllerBeforeMigrate {
    private dialogController: promptAction.DialogController = new promptAction.DialogController();
    @State result: string = '';
  
    build() {
      NavDestination() {
        Column() {
          Button('Open openCustomDialogWithController')
            .onClick(() => {
              let contentNode = new ComponentContent(this.getUIContext(), wrapBuilder(buildText),
                new Params('Custom dialog content'));
              this.getUIContext()
                .getPromptAction()
                .openCustomDialogWithController(contentNode,
                  this.dialogController, {
                    autoCancel: true,
                    alignment: DialogAlignment.Center
                  })
                .then(() => {
                  this.result = 'opened';
                })
                .catch((error: BusinessError) => {
                  this.result = `open error: ${error.code}`;
                });
            })
  
          if (this.result) {
            Text(this.result)
              .fontSize(14)
              .margin({ top: 10 })
          }
        }
        .width('100%')
        .height('100%')
        .justifyContent(FlexAlign.Center)
      }
    }
  }
  ```
  
  ![Before migration example](figures/OpenCustomDialogWithControllerBeforeMigrate.png)
  
  **After migration example (new interface):** Use [DialogPresenter.present](../reference/apis-arkui/arkts-apis-uicontext-dialogpresenter.md#present) to present a custom dialog with a controller, and obtain the return result through a Promise.
  
  <!-- @[open_custom_dialog_with_controller_after_migrate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/opencustomdialog/OpenCustomDialogWithControllerAfterMigrate.ets) -->
  
  ``` TypeScript
  import { DialogBaseAlignment, DialogBaseController, DialogPresenter, DialogResult } from '@kit.ArkUI';
  import { BusinessError } from '@kit.BasicServicesKit';
  
  @Entry
  @Component
  export struct OpenCustomDialogWithControllerAfterMigrate {
    private presenter: DialogPresenter = this.getUIContext().getDialogPresenter();
    private controller: DialogBaseController = new DialogBaseController();
    @State result: string = '';
  
    build() {
      NavDestination() {
        Row() {
          Column() {
            Text('openCustomDialogWithController migration example')
              .fontSize(18)
              .fontWeight(FontWeight.Bold)
              .margin({ bottom: 20 })
  
            Button('Old API: promptAction.openCustomDialogWithController')
              .width('90%')
              .margin({ bottom: 10 })
              .onClick(() => {
                this.result = 'For the old interface example, see arkts-apis-uicontext-promptaction.md';
              })
  
            Button('New API: DialogPresenter.present (custom dialog)')
              .width('90%')
              .margin({ bottom: 10 })
              .onClick(() => {
                this.showNewCustomDialog();
              })
  
            if (this.result) {
              Text(this.result)
                .fontSize(14)
                .margin({ top: 10 })
            }
          }
          .width('100%')
        }
        .height('100%')
      }
    }
  
    @Builder
    CustomContent() {
      Column() {
        Text('Custom dialog content')
          .fontSize(16)
          .margin({ bottom: 10 })
        Button('Close dialog')
          .onClick(() => {
            this.controller.close();
          })
      }
      .padding(20)
    }
  
    private showNewCustomDialog(): void {
      this.presenter.present(() => {
        this.CustomContent()
      }, {
        controller: this.controller,
        autoCancel: true,
        alignment: DialogBaseAlignment.CENTER
      }).then((result: DialogResult) => {
        this.result = 'present success, dialogId: ' + result.dialogId;
      }).catch((error: BusinessError) => {
        this.result = `present error: ${error.code}`;
      });
    }
  }
  ```
  
  ![After migration example figure](figures/OpenCustomDialogWithControllerAfterMigrate.png)

- Advanced animation parameter differences

  The old interface uses `customStyle: boolean` to control whether a custom style is used, and `openAnimation` / `closeAnimation` (`AnimateParam`) to control the open and close animations. The new interface uses `dialogTransition: TransitionEffect` to control the content area animation, and `maskTransition: TransitionEffect` to control the mask animation. The parameter types of the two differ, and **no equivalent mapping exists**. During migration, rewrite the animation parameters according to the new interface's `TransitionEffect`.

### Usage Differences

The old and new interfaces differ in the following two usage scenarios:

- **Dynamically modifying the dialog position after it is displayed**: The old interface does not support dynamically modifying the dialog position (alignment, offset, mask color, etc.) after it is displayed. You need to close it and then reopen it. The new interface supports updating it directly after it is displayed, without closing and reopening.
- **System material in custom dialog scenarios**: The old interface does not support system material in custom dialog scenarios; the new interface does.

The following uses a custom dialog as an example to compare the implementation of the old and new interfaces.

Old interface example: Use `promptAction.openCustomDialog` to display a custom dialog. When you need to update the dialog style (for example, when the color mode changes), you must call `closeCustomDialog` to close it and then reopen it, and system material is not supported.

<!-- @[custom_dialog_old_interface](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/opencustomdialog/CustomDialogOldInterface.ets) -->

``` TypeScript
import { ComponentContent } from '@kit.ArkUI';
import { AbilityConstant, Configuration, EnvironmentCallback, ConfigurationConstant } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { resourceManager } from '@kit.LocalizationKit';

class Params {
  public text: string = '';
  public colorMode: resourceManager.ColorMode = resourceManager.ColorMode.LIGHT

  constructor(text: string, colorMode: resourceManager.ColorMode) {
    this.text = text
    this.colorMode = colorMode
  }
}

@Builder
function builderDialog(params: Params) {
  Column() {
    Text(params.text)
      .fontSize(50)
      .fontWeight(FontWeight.Bold)
      .margin({ bottom: 36 })
  }.backgroundColor(params.colorMode == resourceManager.ColorMode.LIGHT ? '#D5D5D5' : '#004AAF')
}

@Entry
@Component
export struct CustomDialogOldInterface {
  @State message: string = 'hello';
  contentNode: ComponentContent<Params> | null = null;
  callbackId: number | undefined = 0;

  aboutToAppear(): void {
    let environmentCallback: EnvironmentCallback = {
      onMemoryLevel: (level: AbilityConstant.MemoryLevel): void => {
      },
      onConfigurationUpdated: (config: Configuration): void => {
        console.info(`onConfigurationUpdated ${config}`);
        this.getUIContext().getHostContext()?.getApplicationContext().resourceManager.getConfiguration((err,
          config) => {
          // Call the update method of ComponentContent to update the colorMode information.
          this.contentNode?.update(new Params(this.message, config.colorMode))
          setTimeout(() => {
            // Call updateConfiguration of ComponentContent to trigger a full update of the node.
            this.contentNode?.updateConfiguration()
          })
        })
      }
    }
    // Register a listener for system environment changes.
    this.callbackId =
      this.getUIContext().getHostContext()?.getApplicationContext().on('environment', environmentCallback)
    // Set the app to follow the system light/dark mode.
    this.getUIContext()
      .getHostContext()?.getApplicationContext().setColorMode(ConfigurationConstant.ColorMode.COLOR_MODE_NOT_SET)
  }

  aboutToDisappear() {
    // Unregister the callback for listening to system environment changes.
    this.getUIContext().getHostContext()?.getApplicationContext().off('environment', this.callbackId)
    this.contentNode?.dispose()
  }

  build() {
    NavDestination() {
      Row() {
        Column() {
          Button('click me')
            .onClick(() => {
              let uiContext = this.getUIContext();
              let promptAction = uiContext.getPromptAction();
              if (this.contentNode == null && uiContext.getHostContext() != undefined) {
                this.contentNode = new ComponentContent(uiContext, wrapBuilder(builderDialog), new Params(this.message,
                  uiContext.getHostContext()!!.getApplicationContext()
                    .resourceManager
                    .getConfigurationSync()
                    .colorMode))
              }
              if (this.contentNode == null) {
                return
              }
              promptAction.closeCustomDialog(this.contentNode)
              // Close the existing dialog first, and then reopen it.
              promptAction.openCustomDialog(this.contentNode).then(() => {
                console.info('succeeded')
              }).catch((error: BusinessError) => {
                console.error(`OpenCustomDialog args error code is ${error.code}, message is ${error.message}`);
              })
            })
        }
        .width('100%')
        .height('100%')
        .justifyContent(FlexAlign.Center)
      }
      .height('100%')
    }
  }
}
```

![Old interface example](figures/CustomDialogOldInterface.gif)

New interface example: Use `DialogPresenter.present` to display a custom dialog and set the system material, and use `DialogPresenter.update` to dynamically modify the dialog offset after it is displayed, without closing and reopening it.

<!-- @[custom_dialog_new_interface](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/opencustomdialog/CustomDialogNewInterface.ets) -->

``` TypeScript
// Index.ets
import {
  ComponentContent,
  DialogPresenter,
  DialogResult,
  uiMaterial
} from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

// Define a parameter class for passing data to the custom dialog content.
class Params {
  public text: string = '';

  constructor(text: string) {
    this.text = text;
  }
}

// Builder function for the custom dialog content.
@Builder
function buildText(params: Params) {
  Column({ space: 20 }) {
    Text(params.text)
      .fontSize(30)
      .fontWeight(FontWeight.Bold)
      .margin({ bottom: 36 })
    // Update the dialog style button to dynamically modify the mask color, alignment, and offset.
    Button('Update dialog')
      .onClick(() => {
        dialogPresenter?.update(contentNode, {
          offset: { dx: 0, dy: 30 }
        })
          .then(() => {
            console.info('update success');
          })
          .catch((error: BusinessError) => {
            console.error(`update error code is ${error.code}, message is ${error.message}`);
          })
      })
    // Close the dialog button to close the dialog through the ComponentContent reference.
    Button('Dismiss dialog')
      .onClick(() => {
        dialogPresenter?.dismiss(contentNode)
          .then(() => {
            console.info('dismiss success');
          })
          .catch((error: BusinessError) => {
            console.error(`dismiss error code is ${error.code}, message is ${error.message}`);
          })
      })
  }
}

// Global variable that stores the DialogPresenter instance.
let dialogPresenter: DialogPresenter | null = null;
// Global variable that stores the ComponentContent instance of the custom dialog.
let contentNode: ComponentContent<Object> | null = null;

@Entry
@Component
export struct CustomDialogNewInterface {
  @State message: string = 'custom dialog';

  aboutToAppear(): void {
    // Obtain the DialogPresenter instance.
    dialogPresenter = this.getUIContext().getDialogPresenter();
    // Create a ComponentContent and bind the custom builder function and parameters.
    contentNode = new ComponentContent(this.getUIContext(), wrapBuilder(buildText), new Params(this.message));
  }

  build() {
    NavDestination() {
      Row() {
        Column({ space: 10 }) {
          Button('Present custom dialog')
            .id('PresentDialog')
            .onClick(() => {
              // Display a custom-styled dialog by passing the ComponentContent and configuration options.
              dialogPresenter?.present(contentNode, {
                systemMaterial: new uiMaterial.ImmersiveMaterial({ style: uiMaterial.ImmersiveStyle.REGULAR })
              })
              // The dialog is displayed successfully. Obtain the dialog ID.
                .then((result: DialogResult) => {
                  console.info('present success, dialogId: ' + result.dialogId);
                })
                .catch((error: BusinessError) => {
                  console.error(`present error code is ${error.code}, message is ${error.message}`);
                })
            })
        }.width('100%').height('100%').justifyContent(FlexAlign.Center)
      }
      .height('100%')
    }
  }
}
```

![New interface example](figures/CustomDialogNewInterface.gif)

## Typical Scenario Migration Guide

### Migrating the Global Custom Popup

This example migrates the global custom dialog from the old interface to the new interface, encapsulates the `DialogPresenterClassNew` utility class to centrally manage the opening, closing, and updating of the dialog, and calls this utility class in the page to implement the dialog display and dynamic update (modifying the alignment and offset).

**Before migration example (old interface):**

[Complete example](arkts-uicontext-custom-dialog.md#sample-code)

**After migration example (new interface):**

<!-- @[dialog_presenter_class_new](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/common/DialogPresenterClassNew.ts) -->

``` TypeScript
// DialogPresenterClassNew.ets
import { BusinessError } from '@kit.BasicServicesKit';
import { ComponentContent, dialog, DialogResult, UIContext } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;

export class DialogPresenterClassNew {
  static ctx: UIContext;
  static contentNode: ComponentContent<Object>;
  static options: dialog.DialogBaseOptions;

  static setContext(context: UIContext) {
    DialogPresenterClassNew.ctx = context;
  }

  static setContentNode(node: ComponentContent<Object>) {
    DialogPresenterClassNew.contentNode = node;
  }

  static setOptions(options: dialog.DialogBaseOptions) {
    DialogPresenterClassNew.options = options;
  }

  // Open the dialog.
  static openDialog() {
    if (DialogPresenterClassNew.contentNode !== null) {
      DialogPresenterClassNew.ctx.getDialogPresenter()?.present(this.contentNode, DialogPresenterClassNew.options)
        .then((result: DialogResult) => {
          hilog.info(DOMAIN, 'testTag', 'testTag', 'OpenCustomDialog complete.');
        }).catch((error: BusinessError) => {
        let message = (error as BusinessError).message;
        let code = (error as BusinessError).code;
        hilog.error(DOMAIN, 'testTag', 'testTag', `OpenCustomDialog args error code is ${code}, message is ${message}`);
      });
    }
  }

  // Close the dialog.
  static closeDialog() {
    if (DialogPresenterClassNew.contentNode !== null) {
      DialogPresenterClassNew.ctx.getDialogPresenter()?.dismiss(this.contentNode)
        .then(() => {
          hilog.info(DOMAIN, 'testTag', 'testTag', 'CloseCustomDialog complete.');
        })
        .catch((error: BusinessError) => {
          let message = (error as BusinessError).message;
          let code = (error as BusinessError).code;
          hilog.error(DOMAIN, 'testTag', 'testTag', `CloseCustomDialog args error code is ${code}, message is ${message}`);
        });
    }
  }

  // Update the dialog.
  static updateDialog(options: dialog.DialogBaseOptions) {
    if (DialogPresenterClassNew.contentNode !== null) {
      DialogPresenterClassNew.ctx.getDialogPresenter()?.update(this.contentNode, options)
        .then(() => {
          hilog.info(DOMAIN, 'testTag', 'testTag', 'UpdateCustomDialog complete.');
        })
        .catch((error: BusinessError) => {
          let message = (error as BusinessError).message;
          let code = (error as BusinessError).code;
          hilog.error(DOMAIN, 'testTag', 'testTag', `UpdateCustomDialog args error code is ${code}, message is ${message}`);
        });
    }
  }
}
```

The code above encapsulates the `DialogPresenterClassNew` utility class, which provides the open (`openDialog`), close (`closeDialog`), and update (`updateDialog`) methods for the dialog. The page example below calls this utility class to demonstrate the effect of dynamically updating the alignment, offset, and content after the dialog is displayed.

<!-- @[open_dialog_and_update](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/opencustomdialog/OpenDialogAndUpdate.ets) -->

``` TypeScript
// Index.ets
import { ComponentContent, DialogBaseAlignment } from '@kit.ArkUI';
import { DialogPresenterClassNew } from '../../common/DialogPresenterClassNew';

class Params {
  public text: string = '';

  constructor(text: string) {
    this.text = text;
  }
}

@Builder
function buildText(params: Params) {
  Column() {
    Text(params.text)
      .fontSize(50)
      .fontWeight(FontWeight.Bold)
      .margin({ bottom: 36 })
    Button('Close')
      .onClick(() => {
        DialogPresenterClassNew.closeDialog();
      })
  }.backgroundColor('#FFF0F0F0')
}

@Entry
@Component
export struct OpenDialogAndUpdate {
  @State message: string = 'hello';
  private ctx: UIContext = this.getUIContext();
  private contentNode: ComponentContent<Object> =
    new ComponentContent(this.ctx, wrapBuilder(buildText), new Params(this.message));
  aboutToAppear(): void {
    DialogPresenterClassNew.setContext(this.ctx);
    DialogPresenterClassNew.setContentNode(this.contentNode);
    DialogPresenterClassNew.setOptions({ alignment: DialogBaseAlignment.TOP, offset: { dx: 0, dy: 50 } });
  }

  build() {
    NavDestination() {
      Row() {
        Column() {
          Button('open dialog and update options')
            .margin({ top: 50 })
            .onClick(() => {
              DialogPresenterClassNew.openDialog();

              setTimeout(() => {
                DialogPresenterClassNew.updateDialog({
                  alignment: DialogBaseAlignment.BOTTOM,
                  offset: { dx: 0, dy: -50 }
                });
              }, 1500)
            })
          Button('open dialog and update content')
            .margin({ top: 50 })
            .onClick(() => {
              DialogPresenterClassNew.openDialog();

              setTimeout(() => {
                this.contentNode.update(new Params('update'));
              }, 1500)
            })
        }
        .width('100%')
        .height('100%')
      }
      .height('100%')
    }
  }
}
```

![Global custom dialog](figures/GlobalDialogBasePresenter.gif)


### Page-Level Popup Migration

This example migrates the page-level dialog from the old interface to the new interface, providing implementations for two scenarios: the Router routing mode and the Navigation mode. The page-level dialog follows the lifecycle of the page where it resides, and route navigation can be performed within the dialog.

**Before migration example (old interface):**

[Complete example](arkts-embedded-dialog.md#complete-example)

**After migration example (new interface):**

- Page-level dialog in the Router routing mode:

  <!-- @[page_level_dialog](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/customdialog/pageleveldialogbox/PageLevelDialogBox.ets) -->
  
  ``` TypeScript
  import { LevelMode, ImmersiveMode, DialogResult } from '@kit.ArkUI';
  
  let customDialogId: number = 0;
  
  @Builder
  function customDialogBuilder(uiContext: UIContext) {
    Column() {
      Text('Custom dialog Message').fontSize(20).height(100)
      Row() {
        Button('Next').onClick(() => {
          // Perform route navigation within the dialog.
          uiContext.getRouter().pushUrl({ url: 'pages/customdialog/pageleveldialogbox/Next' });
        })
        Blank().width(50)
        Button('Close').onClick(() => {
          uiContext.getDialogPresenter()?.dismiss(customDialogId);
        })
      }
    }.padding(20)
  }
  
  @Entry
  @Component
  export struct PageLevelDialogBox {
    @State message: string = 'Hello World';
  
    @Builder
    customDialogComponent() {
      customDialogBuilder(this.getUIContext());
    }
  
    build() {
      NavDestination() {
        Row() {
          Column() {
            Text(this.message).id('test_text')
              .fontSize(50)
              .fontWeight(FontWeight.Bold)
              .onClick(() => {
                const node: FrameNode | null = this.getUIContext().getFrameNodeById('test_text') || null;
                this.getUIContext().getDialogPresenter()?.present(() => this.customDialogComponent(), {
                  levelMode: LevelMode.EMBEDDED, // Enable the page-level dialog
                  levelUniqueId: node?.getUniqueId(), // Set the ID of any node on the page where the page-level dialog resides
                  immersiveMode: ImmersiveMode.EXTEND, // Set the display mode of the page-level dialog mask
                })
                  .then((result: DialogResult) => {
                    customDialogId = result.dialogId;
                  });
              })
          }
          .width('100%')
        }
        .height('100%')
      }
    }
  }
  ```
  
  The following `Next.ets` is the target page to which the route jumps when the "Next" button in the dialog box is clicked. Click the "Back" button to return to the previous page.
  
  <!-- @[next](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/customdialog/pageleveldialogbox/Next.ets) -->
  
  ``` TypeScript
  // Next.ets
  @Entry
  @Component
  struct Next {
    @State message: string = 'Back';
  
    build() {
      Row() {
        Column() {
          Button(this.message)
            .fontSize(20)
            .fontWeight(FontWeight.Bold)
            .onClick(() => {
              this.getUIContext().getRouter().back();
            })
        }
        .width('100%')
      }
      .height('100%')
    }
  }
  ```
  
  ![Page-level dialog 1](figures/RoutePageLevelDialogBasePresenter.gif)

- A page-level dialog in navigation mode. Before getting started, you need to create and configure the index page and the **router_map.json** file by referring to [Using NavDestination as a Navigation Page in Navigation](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#example-16-using-navdestination-as-a-navigation-page-in-navigation). In addition, replace the **PageHome** and **PageOne** components described in the Navigation reference document with the **PageLevelDialogInNavigation** and **PageLevelDialogInNavigationTestTwo** components in the following sample code.

  <!-- @[page_level_dialog](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/customdialog/pageleveldialogbox/PageLevelDialogInNavigation.ets) -->
  
  ``` TypeScript
  import { LevelMode, ImmersiveMode, DialogResult } from '@kit.ArkUI';
  
  let customDialogId: number = 0;
  
  @Builder
  function customDialogBuilder(uiContext: UIContext, stack: NavPathStack | undefined) {
    Column() {
      Text('Custom dialog Message').fontSize(20).height(100)
      Row() {
        Button('Next').onClick(() => {
          // Perform route navigation inside the dialog box.
          if (stack) {
            stack.pushPath({ name: 'Custom_ROUTE_PREFIX/PageLevelDialogInNavigationPageTwo'})
          }
        })
        Blank().width(50)
        Button('Close').onClick(() => {
          uiContext.getDialogPresenter()?.dismiss(customDialogId);
        })
      }
    }.padding(20)
  }
  
  @Component
  export struct PageLevelDialogInNavigation {
    private stack: NavPathStack | undefined = undefined;
    private uiContext: UIContext = this.getUIContext();
    @State message: string = 'Hello World';
  
    @Builder
    customDialogComponent() {
      customDialogBuilder(this.uiContext, this.stack);
    }
  
    build() {
      NavDestination() {
        Stack({alignContent: Alignment.Center}) {
          Column() {
            Text(this.message).id('test_text')
              .fontSize(50)
              .fontWeight(FontWeight.Bold)
              .onClick(() => {
                const node: FrameNode | null = this.getUIContext().getFrameNodeById('test_text') || null;
                this.uiContext.getDialogPresenter()?.present(() => this.customDialogComponent(), {
                  levelMode: LevelMode.EMBEDDED, // Enable the page-level dialog.
                  levelUniqueId: node?.getUniqueId(), // Set the ID of any node on the page where the page-level dialog resides.
                  immersiveMode: ImmersiveMode.EXTEND, // Set the display mode of the mask of the page-level dialog.
                }).then((result: DialogResult) => {
                  customDialogId = result.dialogId;
                })
              })
          }
          .width('100%')
        }.width('100%').height('100%')
      }
      .width('100%').height('100%')
      .title('PageOne')
      .onReady((ctx: NavDestinationContext) => {
        this.stack = ctx.pathStack;
      })
    }
  }
  
  @Component
  export struct PageLevelDialogInNavigationTestTwo {
    @State message: string = 'Back';
    private stack: NavPathStack | undefined = undefined;
  
    build() {
      NavDestination() {
        Stack({alignContent: Alignment.Center}) {
          Column() {
            Button(this.message)
              .fontSize(20)
              .fontWeight(FontWeight.Bold)
              .onClick(() => {
                if (this.stack) {
                  this.stack.pop()
                }
              })
          }
          .width('100%')
        }.width('100%').height('100%')
      }
      .width('100%').height('100%')
      .title('PageTwo')
      .onReady((ctx: NavDestinationContext) => {
        this.stack = ctx.pathStack;
      })
    }
  }
  ```
  
  ![Page-level dialog 2](figures/NavigationPageLevelDialogBasePresenter.gif)

  <!--no_check-->