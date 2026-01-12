# Dialog Box Layer Management
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @houguobiao-->
<!--Designer: @houguobiao-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
In ArkUI, dialog boxes are directly mounted to the root node in ascending order of their levels. Under the root node, a dialog box on the right is displayed on top of a dialog box on the left. The newly created dialog box is inserted into the corresponding position based on its level. Dialog boxes with the same level are mounted in the order they were created.

Since API version 18, you can set the [levelOrder](../reference/apis-arkui/js-apis-promptAction.md#basedialogoptions11) parameter to manage the display sequence of dialog boxes. This lets you control which dialog box appears on top of others.

## Constraints

Using **levelOrder** to manage the display sequence of dialog boxes is only supported for dialog boxes created using the following APIs: [openCustomDialog](arkts-uicontext-custom-dialog.md), [CustomDialog](arkts-common-components-custom-dialog.md), [AlertDialog](arkts-fixes-style-dialog.md#alert-dialog-box-alertdialog), [ActionSheet](arkts-fixes-style-dialog.md#action-sheet-actionsheet), and [showDialog](arkts-fixes-style-dialog.md#common-dialog-box-showdialog).

> **NOTE**
> 
> Dialog box layer management does not support subwindow scenarios. If **showInSubWindow** is set to **true**, the **levelOrder** parameter has no effect, and the display sequence of dialog boxes cannot be dynamically updated.

## Creating Dialog Boxes at Different Levels

> **NOTE**
> 
> For details about the variables, see [Sample Code](#sample-code).

1. Initialize a dialog box content area with a **Text** component.

    <!-- @[normal_custom_dialog](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/DialogProject/entry/src/main/ets/pages/customdialog/dialogboxlayermanagement/DialogBoxLayer.ets) -->
    
    ``` TypeScript
    @Builder
    normalCustomDialog(index: number) {
      Column() {
        // The value in the 'open_normal_dialog' resource file is 'I am a normal dialog box.'
        Text(this.getUIContext().getHostContext()?.resourceManager.getStringByNameSync('open_normal_dialog') as string +
          index).fontSize(30)
      }.height(400).padding(5).justifyContent(FlexAlign.SpaceBetween)
    }
    ```
    

2. Initialize another dialog box content area with a button to open a common dialog box: In the click event, call the [getPromptAction](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getpromptaction) API in [UIContext](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md) to obtain a [PromptAction](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md) object. Then, use this object to call the [openCustomDialog](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#opencustomdialog12) API and set the [levelOrder](../reference/apis-arkui/js-apis-promptAction.md#basedialogoptions11) parameter to **0** to create a normal-level dialog box.
    <!-- @[top_custom_dialog](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/DialogProject/entry/src/main/ets/pages/customdialog/dialogboxlayermanagement/DialogBoxLayer.ets) -->
    
    ``` TypeScript
    @Builder
    topCustomDialog() {
      Column() {
        // The value in the 'app.string.top_dialog' resource file is 'I am a top-level dialog box.'
        Text($r('app.string.top_dialog')).fontSize(30)
        Row({ space: 50 }) {
          // The value in the 'app.string.open_dialog' resource file is 'Open Normal Dialog Box.'
          Button($r('app.string.open_dialog'))
            .onClick(() => {
              this.getUIContext().getPromptAction().openCustomDialog({
                builder: () => {
                  this.normalCustomDialog(this.dialogIndex);
                },
                levelOrder: LevelOrder.clamp(0),
              })
                .catch((err: BusinessError) => {
                  hilog.error(DOMAIN, 'dialogBoxLayer', 'openCustomDialog error: ' + err.code + '' + err.message);
                });
              this.dialogIndex++;
            })
        }
      }.height(200).padding(5).justifyContent(FlexAlign.SpaceBetween)
    }
    ```
    
    


3. Create a top-level dialog box: In the click event, call the [getPromptAction](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getpromptaction) API in [UIContext](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md) to obtain a [PromptAction](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md) object. Then, use this object to call the [openCustomDialog](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#opencustomdialog12) API and set the [levelOrder](../reference/apis-arkui/js-apis-promptAction.md#basedialogoptions11) parameter to **100000** to create a top-level dialog box.

    <!-- @[open_top_custom_dialog](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/DialogProject/entry/src/main/ets/pages/customdialog/dialogboxlayermanagement/DialogBoxLayer.ets) -->
    
    ``` TypeScript
    this.getUIContext().getPromptAction().openCustomDialog({
      builder: () => {
        this.topCustomDialog();
      },
      levelOrder: LevelOrder.clamp(100000)
    }).catch((err: BusinessError) => {
      hilog.error(DOMAIN, 'dialogBoxLayer', 'openCustomDialog error: ' + err.code + ' ' + err.message);
    });
    ```
    
 

## Sample Code
 <!-- @[dialog_box](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/DialogProject/entry/src/main/ets/pages/customdialog/dialogboxlayermanagement/DialogBoxLayer.ets) -->
 
 ``` TypeScript
 import { LevelOrder } from '@kit.ArkUI';
 import { BusinessError } from '@kit.BasicServicesKit';
 import { hilog } from '@kit.PerformanceAnalysisKit';
 
 const INDEX: number = 0;
 const DOMAIN = 0x0000;
 
 @Entry
 @Component
 export struct DialogBoxLayer {
   @StorageLink('dialogIndex') dialogIndex: number = INDEX;
 
   @Builder
   normalCustomDialog(index: number) {
     Column() {
       // The value in the 'open_normal_dialog' resource file is 'I am a normal dialog box.'
       Text(this.getUIContext().getHostContext()?.resourceManager.getStringByNameSync('open_normal_dialog') as string +
         index).fontSize(30)
     }.height(400).padding(5).justifyContent(FlexAlign.SpaceBetween)
   }
 
 
   @Builder
   topCustomDialog() {
     Column() {
       // The value in the 'app.string.top_dialog' resource file is 'I am a top-level dialog box.'
       Text($r('app.string.top_dialog')).fontSize(30)
       Row({ space: 50 }) {
         // The value in the 'app.string.open_dialog' resource file is 'Open Normal Dialog Box.'
         Button($r('app.string.open_dialog'))
           .onClick(() => {
             this.getUIContext().getPromptAction().openCustomDialog({
               builder: () => {
                 this.normalCustomDialog(this.dialogIndex);
               },
               levelOrder: LevelOrder.clamp(0),
             })
               .catch((err: BusinessError) => {
                 hilog.error(DOMAIN, 'dialogBoxLayer', 'openCustomDialog error: ' + err.code + '' + err.message);
               });
             this.dialogIndex++;
           })
       }
     }.height(200).padding(5).justifyContent(FlexAlign.SpaceBetween)
   }
 
 
   build() {
     NavDestination() {
       Row() {
         Column({ space: 5 }) {
           // The value in the 'app.string.click_dialog' resource file is 'Show Dialog Box.'
           Button($r('app.string.click_dialog'))
             .fontSize(20)
             .onClick(() => {
               this.getUIContext().getPromptAction().openCustomDialog({
                 builder: () => {
                   this.topCustomDialog();
                 },
                 levelOrder: LevelOrder.clamp(100000)
               }).catch((err: BusinessError) => {
                 hilog.error(DOMAIN, 'dialogBoxLayer', 'openCustomDialog error: ' + err.code + ' ' + err.message);
               });
             })
         }.width('100%')
       }
     }
   }
 }
 ```
 
 
 
![dialog-levelorder-demo1](figures/dialog-levelorder-demo1.gif)
