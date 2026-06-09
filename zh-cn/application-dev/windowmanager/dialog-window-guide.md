# 模态窗口开发指导

<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @fei_1007-->
<!--Designer: @gcw_sPCsris4; @qinliwen0417-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

模态窗口用于临时展示关键信息或引导用户完成特定操作（如保存信息），它会中断用户当前的操作流程，要求用户必须做出响应才能继续其他操作，通常用于需要向用户传达重要信息的场景。

## 开发步骤

1. 创建模态窗口。  

   通过[window.createWindow()](../reference/apis-arkui/arkts-apis-window-f.md#windowcreatewindow9-1)接口创建模态窗口（TYPE_DIALOG）。

   <!-- @[dialog_window](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkUIWindowSamples/AuxiliaryWindowSample/entry/src/main/ets/pages/Index.ets) --> 
   
   ``` TypeScript
   let dialogWindowClass: window.Window | undefined = undefined;
   // ...
       // 1.创建模态窗口。
       let context1: common.UIAbilityContext | undefined = AppStorage.get<common.UIAbilityContext>('context');
       let config: window.Configuration = {
         name: 'dialogWindow', windowType: window.WindowType.TYPE_DIALOG, ctx: context1 as common.BaseContext
       };
       window.createWindow(config, (err, data) => {
         if (err?.code) {
           console.error('Failed to create the dialogWindow. Cause: ' + JSON.stringify(err));
           return;
         }
         console.info('Succeeded in creating the dialogWindow. Data: ' + JSON.stringify(data));
         dialogWindowClass = data;
         // ...
       });
   ```

2. 设置模态窗口属性。

   - 模态窗口创建成功后，可以改变其大小、位置等，还可以根据应用需要设置窗口背景色、亮度等属性。

   - 在调用[showWindow()](../reference/apis-arkui/arkts-apis-window-Window.md#showwindow9)之前，建议设置模态窗口的大小和位置。

   <!-- @[dialog_window_properties](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkUIWindowSamples/AuxiliaryWindowSample/entry/src/main/ets/pages/Index.ets) --> 

3. 加载显示窗口的具体内容。  

   通过[setUIContent()](../reference/apis-arkui/arkts-apis-window-Window.md#setuicontent9)和[showWindow()](../reference/apis-arkui/arkts-apis-window-Window.md#showwindow9)接口加载显示模态窗口的具体内容。

   <!-- @[dialog_window_uiContent](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkUIWindowSamples/AuxiliaryWindowSample/entry/src/main/ets/pages/Index.ets) --> 
   
   ``` TypeScript
   // 3.为模态窗口加载对应的目标页面。
   dialogWindowClass.setUIContent('pages/DialogWindow', (err) => {
     if (err?.code) {
       console.error('Failed to load the content. Cause:' + JSON.stringify(err));
       return;
     }
     console.info('Succeeded in loading the content.');
     // 显示模态窗口。
     (dialogWindowClass as window.Window).showWindow((err) => {
       if (err?.code) {
         console.error('Failed to show the window. Cause: ' + JSON.stringify(err));
         return;
       }
       console.info('Succeeded in showing the window.');
     });
   });
   ```

4. 销毁窗口。 

   当不再需要模态窗口时，可根据具体实现逻辑，使用[destroyWindow()](../reference/apis-arkui/arkts-apis-window-Window.md#destroywindow9)接口销毁模态窗口。

   <!-- @[destroy_dialog_window](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkUIWindowSamples/AuxiliaryWindowSample/entry/src/main/ets/pages/DialogWindow.ets) --> 
   
   ``` TypeScript
   // 4.销毁子窗口。当不再需要子窗口时，可根据具体实现逻辑，使用destroy对其进行销毁。
   dialogWindowClass.destroyWindow((err: BusinessError) => {
     let errCode: number = err.code;
     if (errCode) {
       console.error('Failed to destroy the window. Cause: ' + JSON.stringify(err));
       return;
     }
     console.info('Succeeded in destroying the window.');
   });
   ```