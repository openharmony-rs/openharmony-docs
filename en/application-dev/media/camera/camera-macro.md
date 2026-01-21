# Macro Photography Settings (ArkTS)
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

Starting from API version 19, you can configure macro photography. This feature allows the camera to focus closely and capture detailed images of small objects through optimized optical design and algorithms.

## How to Develop

Read [Camera](../../reference/apis-camera-kit/arkts-apis-camera.md) for the API reference.

1. Import the camera module, which provides camera-related properties and methods.

   ```ts
   import { camera } from '@kit.CameraKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   ```

2. Call [isMacroSupported](../../reference/apis-camera-kit/arkts-apis-camera-MacroQuery.md#ismacrosupported19) to check whether the current device supports macro photography.

   ```ts
   let isSupported: boolean = photoSession.isMacroSupported();
   ```
    
3. Call [enableMacro](../../reference/apis-camera-kit/arkts-apis-camera-Macro.md#enablemacro19) to enable or disable macro photography.

   ```ts
   function EnableMacro(photoSession: camera.PhotoSession): void {
      let isSupported: boolean = photoSession.isMacroSupported();
      if (isSupported) {
         photoSession.enableMacro(true);
      }
   }
   ```


## Status Listening

Starting from API version 20, you can listen for macro photography status changes.

Call [on('macroStatusChanged')](../../reference/apis-camera-kit/arkts-apis-camera-PhotoSession.md#onmacrostatuschanged20) to listen for the macroStatusChanged event to track changes in macro photography.
   ```ts
   function callback(err: BusinessError, macroStatus: boolean): void {
      if (err !== undefined && err.code !== 0) {
         console.error(`Callback Error, errorCode: ${err.code}`);
         return;
      }
      console.info(`Macro state: ${macroStatus}`);
   }

   // Register a callback.
   function registerMacroStatusChanged(photoSession: camera.PhotoSession): void {
      photoSession.on('macroStatusChanged', callback);
   }

   // Stop the listening.
   function unregisterMacroStatusChanged(photoSession: camera.PhotoSession): void {
      photoSession.off('macroStatusChanged');
   }
   ```  
