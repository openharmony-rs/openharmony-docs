# 不可获焦窗口中输入框与输入法交互指南

<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @codexu62-->
<!--Designer: @zhaolinglan-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->

## 场景介绍

应用获得焦点是使用输入法的必要条件，开发者需要正确处理焦点以确保输入法的正常工作。

例如，在应用开发中，开发者可以通过[setWindowFocusable](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowfocusable9)，将创建的窗口的可获焦属性设置为false（如悬浮窗、辅助交互窗口等），并希望在该窗口中绘制输入框（如[TextInput](../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md)、[TextArea](../reference/apis-arkui/arkui-ts/ts-basic-components-textarea.md)或[自绘输入框](use-inputmethod-in-custom-edit-box.md)）以支持用户输入，即拉起系统键盘进行输入操作。

## 系统限制

当通过[setWindowFocusable](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowfocusable9)将窗口设置为不可获焦时，系统侧会对该窗口施加限制。由于窗口无焦点，输入事件（如按键信息）无法被窗口正确接收和处理，输入内容无法同步到该窗口中的输入框，导致输入框与键盘交互异常。

## 推荐方案

若需要在不可获焦窗口中绘制输入框，并希望能够与键盘正常交互，建议按照以下方式开发（以[TextInput](../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md)为例）：

1. 在主窗中创建一个子窗，设置其初始为不可获焦窗口。

   实现效果：点击主窗输入组件，弹出子窗，焦点仍然在主窗的输入框上。

   ArkTS-Dyn示例：

   <!-- @[input_case_input_create_not_focusable_subwindow](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputMethod/KikaInputMethod/entry/src/main/ets/pages/NotFocusableWindowDemo.ets) -->
   
   ``` TypeScript
   // NotFocusableWindowDemo.ets实现主窗的布局内容
   import { window } from '@kit.ArkUI';
   import { BusinessError } from '@ohos.base';
   import Log from '../model/Log';
   
   const TAG: string = 'NotFocusableWindowDemo->';
   
   @Entry
   @Component
   struct NotFocusableWindowDemo {
     private subWindow: window.Window | null = null;
   
     async createSubWindow(): Promise<void> {
       try {
         // 已创建过子窗时，直接再次显示
         if (this.subWindow !== null) {
           await this.subWindow.showWindow();
           return;
         }
         // 1.创建子窗并设置子窗id
         let windowStage: window.WindowStage | undefined = AppStorage.get<window.WindowStage>('windowStage');
         if (windowStage === undefined) {
           Log.showError(TAG, 'Failed to get windowStage');
           return;
         }
         let title: string | undefined = this.getUIContext().getHostContext()?.resourceManager.getStringSync($r('app.string.subwindow_title').id);
         let options: window.SubWindowOptions = { title: title ? title : '', decorEnabled: true };
         let subWindow: window.Window = await windowStage.createSubWindowWithOptions('mySubWindow', options);
         this.subWindow = subWindow;
         const subWindowId: number = subWindow.getWindowProperties().id;
         AppStorage.setOrCreate('subWindowId', subWindowId);
         // 2.设置子窗为不可获焦，true表示允许获取焦点，false表示不允许
         await subWindow.resize(500, 500);
         await subWindow.setUIContent('pages/SubWindowIndex');
         await subWindow.setWindowFocusable(false);
         // 3.显示子窗
         await subWindow.showWindow();
         Log.showInfo(TAG, 'Succeeded in creating and showing the subWindow.');
       } catch (exception) {
         const err = exception as BusinessError;
         Log.showError(TAG, `Failed to create the subWindow. Cause code: ${err.code}, message: ${err.message}`);
       }
     }
   
     async destroySubWindow(): Promise<void> {
       try {
         if (this.subWindow === null) {
           return;
         }
         await this.subWindow.destroyWindow();
         this.subWindow = null;
         Log.showInfo(TAG, 'Succeeded in destroying the subWindow.');
       } catch (exception) {
         const err = exception as BusinessError;
         Log.showError(TAG, `Failed to destroy the subWindow. Cause code: ${err.code}, message: ${err.message}`);
       }
     }
   
     aboutToDisappear(): void {
       // 离开页面时销毁子窗，避免残留
       this.destroySubWindow();
     }
   
     build() {
       Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
         Text($r('app.string.not_focusable_window_title'))
           .fontSize(18)
           .fontWeight(500)
           .margin(20)
         TextInput({ placeholder: $r('app.string.subwindow_placeholder') })
           .width('90%')
           .height(48)
           .margin(10)
           .onClick(() => {
             this.createSubWindow();
           })
         Button($r('app.string.subwindow_destroy'))
           .width('90%')
           .height(48)
           .margin(10)
           .onClick(() => {
             this.destroySubWindow();
           })
       }
       .width('100%')
       .height('100%')
     }
   }
   ```

   ArkTS-Sta示例：

   <!-- @[input_case_input_create_not_focusable_subwindow](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/InputMethod/SimpleKeyboard/entry/src/main/ets/pages/NotFocusableWindowDemo.ets) -->
   
   ``` TypeScript
   // NotFocusableWindowDemo.ets实现主窗的布局内容
   import {
     Entry,
     Component,
     Flex,
     Text,
     TextInput,
     Button,
     FlexOptions,
     FlexDirection,
     ItemAlign,
     FlexAlign,
     window,
     AppStorage,
     $r
   } from '@kit.ArkUI';
   import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
   import { hilog } from '@kit.PerformanceAnalysisKit';
   import { BusinessError } from '@ohos.base';
   import { common } from '@kit.AbilityKit';
   import Log from '../model/Log';
   
   const TAG: string = 'NotFocusableWindowDemo->';
   
   @Entry
   @Component
   struct NotFocusableWindowDemo {
     private subWindow: window.Window | null = null;
   
     async createSubWindow(): Promise<void> {
       try {
         if (this.subWindow !== null) {
           await this.subWindow!.showWindow();
           return;
         }
         let windowStage: window.WindowStage | undefined = AppStorage.get<window.WindowStage>('windowStage');
         if (windowStage === undefined) {
           Log.showError(TAG, 'Failed to get windowStage');
           return;
         }
         let title: string | undefined =
           this.getUIContext().getHostContext()?.resourceManager.getStringSync($r('app.string.subwindow_title').id);
         let options: window.SubWindowOptions = { title: title ? title : '', decorEnabled: true };
         let subWindow: window.Window = await windowStage.createSubWindowWithOptions('mySubWindow', options);
         this.subWindow = subWindow;
         const subWindowId: number = subWindow.getWindowProperties().id;
         AppStorage.setOrCreate('subWindowId', subWindowId);
         await subWindow.resize(500, 500);
         await subWindow.setUIContent('pages/SubWindowIndex');
         await subWindow.setWindowFocusable(false);
         await subWindow.showWindow();
         Log.showInfo(TAG, 'Succeeded in creating and showing the subWindow.');
       } catch (exception) {
         let error: BusinessError = exception as BusinessError;
         Log.showError(TAG, `Failed to create the subWindow. Cause code: ${error.code}, message: ${error.message}`);
       }
     }
   
     async destroySubWindow(): Promise<void> {
       try {
         if (this.subWindow === null) {
           return;
         }
         await this.subWindow!.destroyWindow();
         this.subWindow = null;
         Log.showInfo(TAG, 'Succeeded in destroying the subWindow.');
       } catch (exception) {
         let error: BusinessError = exception as BusinessError;
         Log.showError(TAG, `Failed to destroy the subWindow. Cause code: ${error.code}, message: ${error.message}`);
       }
     }
   
     aboutToDisappear(): void {
       this.destroySubWindow();
     }
   
     build(): void {
       Flex({
         direction: FlexDirection.Column,
         alignItems: ItemAlign.Center,
         justifyContent: FlexAlign.Center
       } as FlexOptions) {
         Text($r('app.string.not_focusable_window_title'))
           .fontSize(18)
           .fontWeight(500)
           .margin(20)
         TextInput({ placeholder: $r('app.string.subwindow_placeholder') })
           .width('90%')
           .height(48)
           .margin(10)
           .onClick(() => {
             this.createSubWindow();
           })
         Button($r('app.string.subwindow_destroy'))
           .width('90%')
           .height(48)
           .margin(10)
           .onClick(() => {
             this.destroySubWindow();
           })
       }
       .width('100%')
       .height('100%')
     }
   }
   ```
   

2. 当用户点击子窗中的输入框组件时，可以先通过[setWindowFocusable](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowfocusable9)将子窗设置为可获焦，然后通过[shiftAppWindowFocus](../reference/apis-arkui/arkts-apis-window-f.md#windowshiftappwindowfocus11)将焦点窗口从主窗切换为子窗，即可在子窗的输入框中正常使用输入法。
   ArkTS-Dyn示例：

   <!-- @[input_case_input_shift_focus_in_not_focusable_window](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputMethod/KikaInputMethod/entry/src/main/ets/pages/SubWindowIndex.ets) -->
   
   ``` TypeScript
   async shiftFocusToSubWindow(): Promise<void> {
     try {
       let windowStage: window.WindowStage | undefined = AppStorage.get<window.WindowStage>('windowStage');
       if (windowStage === undefined) {
         Log.showError(TAG, 'Failed to get the windowStage.');
         return;
       }
       let subWindowList: window.Window[] = await windowStage.getSubWindow();
       let subWindow: window.Window = subWindowList[0];
       // 1.将子窗口设置为可获焦
       await subWindow.setWindowFocusable(true);
       // 2.将焦点切换到子窗口
       const mainWindowId: number = AppStorage.get<number>('mainWindowId') ?? 0;
       const subWindowId: number = AppStorage.get<number>('subWindowId') ?? 0;
       await window.shiftAppWindowFocus(mainWindowId, subWindowId);
       Log.showInfo(TAG, 'Succeeded in shifting focus to subWindow.');
     } catch (exception) {
       const err = exception as BusinessError;
       Log.showError(TAG, `Failed to shift focus to subWindow. Cause code: ${err.code}, message: ${err.message}`);
     }
   }
   ```

   ArkTS-Sta示例：

   <!-- @[input_case_input_shift_focus_in_not_focusable_window](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/InputMethod/SimpleKeyboard/entry/src/main/ets/pages/SubWindowIndex.ets) -->


3. 当用户重新点击子窗中的非输入框组件时，可以通过[setWindowFocusable](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowfocusable9)将子窗重新设置为不可获焦，焦点窗口即可恢复至主窗。
   ArkTS-Dyn示例：

   <!-- @[input_case_input_shift_focus_to_main_window](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputMethod/KikaInputMethod/entry/src/main/ets/pages/SubWindowIndex.ets) -->

ArkTS-Sta示例：

   <!-- @[input_case_input_shift_focus_to_main_window](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/InputMethod/SimpleKeyboard/entry/src/main/ets/pages/SubWindowIndex.ets) -->
