# 微距能力设置(ArkTS)
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

从API version 19开始，支持设置微距能力。微距能力是指通过光学设计与算法优化，实现近距离对焦并清晰捕捉微小物体细节的相机功能。



## 开发步骤

详细的API说明请参考[Camera](../../reference/apis-camera-kit/arkts-apis-camera.md)。

1. 导入camera接口，接口中提供了相机相关的属性和方法，导入方法如下。

    ```ts
    import { camera } from '@kit.CameraKit';
    import { BusinessError } from '@kit.BasicServicesKit';
    ```

2. 通过[isMacroSupported](../../reference/apis-camera-kit/arkts-apis-camera-MacroQuery.md#ismacrosupported19)接口，查询当前设备是否支持微距能力。

    ```ts
   let isSupported: boolean = photoSession.isMacroSupported();
    ```
    
3. 通过[enableMacro](../../reference/apis-camera-kit/arkts-apis-camera-Macro.md#enablemacro19)接口，开启或关闭微距能力。

    ```ts
   function EnableMacro(photoSession: camera.PhotoSession): void {
   let isSupported: boolean = photoSession.isMacroSupported();
   if (isSupported) {
      photoSession.enableMacro(true);
   }
   }
    ```


## 状态监听

从API version 20开始，支持监听微距能力是否发生改变。

注册macroStatusChanged事件监听微距能力变化，事件监听可参考[on('macroStatusChanged')](../../reference/apis-camera-kit/arkts-apis-camera-PhotoSession.md#onmacrostatuschanged20)。
   ```ts
   function callback(err: BusinessError, macroStatus: boolean): void {
      if (err !== undefined && err.code !== 0) {
         console.error(`Callback Error, errorCode: ${err.code}`);
         return;
      }
      console.info(`Macro state: ${macroStatus}`);
   }

   // 注册回调函数。
   function registerMacroStatusChanged(photoSession: camera.PhotoSession): void {
      photoSession.on('macroStatusChanged', callback);
   }

   // 解注册。
   function unregisterMacroStatusChanged(photoSession: camera.PhotoSession): void {
      photoSession.off('macroStatusChanged');
   }
   ```  