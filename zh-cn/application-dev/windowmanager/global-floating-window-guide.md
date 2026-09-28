# 全局悬浮窗开发指导

<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @fei_1007-->
<!--Designer: @gcw_sPCsris4; @qinliwen0417-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

## 场景介绍

全局悬浮窗具有在应用主窗口退后台时，继续在前台显示的能力，适用于如多人视频通话、屏幕共享等场景。

全局悬浮窗的层级比所有应用主窗口、子窗口的层级高。

## 约束限制

全局悬浮窗当前仅支持在PC/2in1设备上使用。

## 前提条件

创建WindowType.TYPE_FLOAT即全局悬浮窗类型的窗口，需要申请[ohos.permission.SYSTEM_FLOAT_WINDOW](../security/AccessToken/restricted-permissions.md#ohospermissionsystem_float_window)权限，该权限为受控开放权限。申请方式请参考：[申请使用受限权限](../security/AccessToken/declare-permissions-in-acl.md)。

<!--RP3-->
<!--RP3End-->


## 开发步骤

1. 创建全局悬浮窗。  

   通过[window.createWindow()](../reference/apis-arkui/arkts-apis-window-f.md#windowcreatewindow9-1)接口创建全局悬浮窗类型（TYPE_FLOAT）的窗口。

   <!-- @[floating_window](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkUIWindowSamples/AuxiliaryWindowSample/entry/src/main/ets/pages/Index.ets) -->  
   
   ``` TypeScript
   let floatWindowClass: window.Window | undefined = undefined;
   // ...
         // 1.创建全局悬浮窗。
         let context: common.UIAbilityContext | undefined = AppStorage.get<common.UIAbilityContext>('context');
         let config: window.Configuration = {
           name: 'floatWindow', windowType: window.WindowType.TYPE_FLOAT, ctx: context as common.BaseContext
         };
         window.createWindow(config, (err, data) => {
           if (err?.code) {
             console.error(`Failed to create the floatWindow. Cause code: ${err.code}, message: ${err.message}`);
             return;
           }
           floatWindowClass = data;
           console.info('Succeeded in creating the floatWindow. Data: ' + JSON.stringify(data));
           // ...
         });
   ```

2. 对全局悬浮窗进行属性设置等操作。  

   全局悬浮窗创建成功后，可以改变其大小、位置等，还可以根据应用需要设置全局悬浮窗的背景色、亮度等属性。

   <!-- @[floating_window_properties](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkUIWindowSamples/AuxiliaryWindowSample/entry/src/main/ets/pages/Index.ets) -->  
   
   ``` TypeScript
   // 2.全局悬浮窗窗口创建成功后，设置全局悬浮窗的位置、大小及相关属性等。
   floatWindowClass.moveWindowTo(100, 100, (err) => {
     if (err?.code) {
       console.error(`Failed to move the window. Cause code: ${err.code}, message: ${err.message}`);
       return;
     }
     console.info('Succeeded in moving the window.');
     if (!floatWindowClass) {
       console.error('float_windowClass is null');
       return;
     }
     floatWindowClass.resize(600, 900, (err) => {
       if (err?.code) {
         console.error(`Failed to change the window size. Cause code: ${err.code}, message: ${err.message}`);
         return;
       }
       console.info('Succeeded in changing the window size.');
     });
   });
   ```

3. 加载显示全局悬浮窗的具体内容。

   通过[setUIContent()](../reference/apis-arkui/arkts-apis-window-Window.md#setuicontent9-1)和[showWindow()](../reference/apis-arkui/arkts-apis-window-Window.md#showwindow9-1)接口加载显示全局悬浮窗的具体内容。

   <!-- @[floating_window_uiContent](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkUIWindowSamples/AuxiliaryWindowSample/entry/src/main/ets/pages/Index.ets) -->  
   
   ``` TypeScript
   // 3.为全局悬浮窗加载对应的目标页面。
   floatWindowClass.setUIContent('pages/FloatWindow', (err) => {
     if (err?.code) {
       console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
       return;
     }
     console.info('Succeeded in loading the content.');
     // 显示全局悬浮窗。
     (floatWindowClass as window.Window).showWindow((err) => {
       if (err?.code) {
         console.error(`Failed to show the window. Cause code: ${err.code}, message: ${err.message}`);
         return;
       }
       console.info('Succeeded in showing the window.');
     });
   });
   ```

4. 销毁全局悬浮窗。  

   当不再需要全局悬浮窗时，可根据具体实现逻辑，使用[destroyWindow()](../reference/apis-arkui/arkts-apis-window-Window.md#destroywindow9-1)接口销毁全局悬浮窗。

   <!-- @[destroy_floating_window](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkUIWindowSamples/AuxiliaryWindowSample/entry/src/main/ets/pages/Index.ets) -->  
   
   ``` TypeScript
   // 4.销毁全局悬浮窗。当不再需要全局悬浮窗时，可根据具体实现逻辑，使用destroy对其进行销毁。
   floatWindowClass.destroyWindow((err) => {
     if (err?.code) {
       console.error(`Failed to destroy the window. Cause code: ${err.code}, message: ${err.message}`);
       return;
     }
     console.info('Succeeded in destroying the window.');
   });
   ```