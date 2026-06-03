# 模态窗口开发指导

<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @waterwin-->
<!--Designer: @nyankomiya; @qinliwen0417-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

模态窗口用于临时展示关键信息或引导用户完成特定操作（如保存信息），它会中断用户当前的操作流程，要求用户必须做出响应才能继续其他操作，通常用于需要向用户传达重要信息的场景。

## 开发步骤

1. 创建模态窗口。  

   通过[window.createWindow()](../reference/apis-arkui/arkts-apis-window-f.md#windowcreatewindow9-1)接口创建模态窗口（TYPE_DIALOG）。

   ```ts
   let dialog_windowClass: window.Window | undefined = undefined;
   // 1.创建模态窗口。
   let config: window.Configuration = {
     name: "DialogWindow", windowType: window.WindowType.TYPE_DIALOG, ctx: getContext(this)
   };
   window.createWindow(config, (err, data) => {
     let errCode: number = err.code;
     if (errCode) {
       console.error('Failed to create the dialogWindow. Cause: ' + JSON.stringify(err));
       return;
     }
     dialog_windowClass = data;
     if (!dialog_windowClass) {
       console.error('dialog_windowClass is null');
       return;
     }
     console.info('Succeeded in creating the dialogWindow. Data: ' + JSON.stringify(data));
   });
   ```

2. 设置模态窗口属性。

   - 模态窗口创建成功后，可以改变其大小、位置等，还可以根据应用需要设置窗口背景色、亮度等属性。

   - 在调用[showWindow()](../reference/apis-arkui/arkts-apis-window-Window.md#showwindow9)之前，建议设置模态窗口的大小和位置。
  
   ```ts
   // 2.模态窗口创建成功后，设置模态窗口的位置、大小及相关属性等。
   dialog_windowClass.moveWindowTo(700, 100, (err) => {
     let errCode: number = err.code;
     if (errCode) {
       console.error('Failed to move the window. Cause:' + JSON.stringify(err));
       return;
     }
     console.info('Succeeded in moving the window.');
     if (!dialog_windowClass) {
       console.error('dialog_windowClass is null');
       return;
     }
     dialog_windowClass.resize(500, 500, (err) => {
       let errCode: number = err.code;
       if (errCode) {
         console.error('Failed to change the window size. Cause:' + JSON.stringify(err));
         return;
        }
        console.info('Succeeded in changing the window size.');
      });
   });
   
   ```

3. 加载显示窗口的具体内容。  

   通过[setUIContent()](../reference/apis-arkui/arkts-apis-window-Window.md#setuicontent9)和[showWindow()](../reference/apis-arkui/arkts-apis-window-Window.md#showwindow9)接口加载显示模态窗口的具体内容。

   ```ts
   // 3.为模态窗口加载对应的目标页面。
   dialog_windowClass.setUIContent("pages/DialogWindow", (err) => {
     let errCode: number = err.code;
     if (errCode) {
       console.error('Failed to load the content. Cause:' + JSON.stringify(err));
       return;
     }
     console.info('Succeeded in loading the content.');
     // 显示模态窗口。
     (dialog_windowClass as window.Window).showWindow((err) => {
       let errCode: number = err.code;
       if (errCode) {
         console.error('Failed to show the window. Cause: ' + JSON.stringify(err));
         return;
       }
       console.info('Succeeded in showing the window.');
     });
   });
   ```

4. 销毁窗口。 

   当不再需要模态窗口时，可根据具体实现逻辑，使用[destroyWindow()](../reference/apis-arkui/arkts-apis-window-Window.md#destroywindow9)接口销毁模态窗口。

   ```ts
   dialog_windowClass.destroyWindow((err: BusinessError) => {
     let errCode: number = err.code;
     if (errCode) {
       console.error('Failed to destroy the window. Cause: ' + JSON.stringify(err));
       return;
     }
     console.info('Succeeded in destroying the window.');
   });
   ```