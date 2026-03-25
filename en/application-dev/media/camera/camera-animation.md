# Basic Camera Animation (ArkTS)
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

During camera usage, preview stream replacement is inevitable in scenarios such as camera mode switching and front/rear camera lens switching. To optimize user experience, you can reasonably use animation effects for transition. This document mainly describes how to capture screenshots of the preview stream and implement animation effects for the following three core scenarios using the [explicit animation capability](../../reference/apis-arkui/arkui-ts/ts-explicit-animatetoimmediately.md) provided by ArkUI:

- Mode switching: Use preview stream snapshots to create a blur effect for transition.
  
  The following depicts the transition from video mode to photo mode.

  ![](figures/mode-switching.gif)

- Front/Rear camera switching: Use preview stream snapshots to create a blur-and-flip effect for transition.

  The following demonstrates the transition from using the front camera to the rear camera.

  ![](figures/front-rear-switching.gif)

- Photo capture blackout: Use a blackout component to overlay the preview stream to create a blackout transition.
  
  The following depicts the moment of photo capture.

  ![](figures/flash-black.gif)

## Blackout Animation

Use component overlay to implement the blackout effect.

The sample code in the following steps is the internal method or logic of a custom component (component decorated by @Component).

1. Import dependencies. Specifically, import the camera, image, and ArkUI modules.

   <!-- @[import_section](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Camera/cameraAnimSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   import { camera } from '@kit.CameraKit';
   import { image } from '@kit.ImageKit';
   import { curves } from '@kit.ArkUI';
   ```

2. Build a blackout component.

   Define a blackout component, which is displayed during camera blackouts for photo capture or front/rear camera switching. This component will block the XComponent.

   Define the component's properties as follows:

   <!-- @[anim_states](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Camera/cameraAnimSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   @State isShowBlur: boolean = false;
   @State isShowBlack: boolean = false;
   @StorageLink('modeChange') @Watch('onModeChange') modeChangeFlag: number = 0;
   @StorageLink('switchCamera') @Watch('onSwitchCamera') switchCameraFlag: number = 0;
   @StorageLink('frameStart') @Watch('onFrameStart') frameStartFlag: number = 0;
   @StorageLink('captureClick') @Watch('onCaptureClick') captureClickFlag: number = 0;
   @StorageLink('surfaceShot') screenshotPixelMap: image.PixelMap | undefined = undefined; // Snapshot of the preview stream.
   @StorageLink('curPosition') curPosition: number = 0; // Current front/rear camera lens status.
   @State shotImgBlur: number = 0;
   @State shotImgOpacity: number = 1;
   @State shotImgScale: ScaleOptions = { x: 1, y: 1 };
   @State shotImgRotation: RotateOptions = { y: BlurAnimateUtil.ROTATE_AXIS, angle: BlurAnimateUtil.IMG_FLIP_ANGLE_0 }
   @State flashBlackOpacity: number = 1;
   ```

   Implement the logic of the blackout component as follows:

   <!-- @[flash_black_component](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Camera/cameraAnimSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // The component is displayed during camera blackouts for photo capture or camera switching and is used to block the XComponent.
   if (this.isShowBlack) {
     Column()
       .key('black')
       .width(this.getUIContext().px2vp(Constants.X_COMPONENT_SURFACE_HEIGHT))
       .height(this.getUIContext().px2vp(Constants.X_COMPONENT_SURFACE_WIDTH))
       .backgroundColor(Color.Black)
       .opacity(this.flashBlackOpacity)
   }
   ```

3. Implement the blackout effect.

   <!-- @[flash_black_anim](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Camera/cameraAnimSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   private flashBlackAnim() {
     Logger.info(TAG, 'flashBlackAnim E');
     this.flashBlackOpacity = 1;
     this.isShowBlack = true;
     animateToImmediately({
       curve: curves.interpolatingSpring(1, 1, 410, 38),
       delay: 50,
       onFinish: () => {
         this.isShowBlack = false;
         this.flashBlackOpacity = 1;
         Logger.info(TAG, 'flashBlackAnim X');
       }
     }, () => {
       this.flashBlackOpacity = 0;
     })
   }
   ```

4. Trigger the blackout effect.

   Tap the capture button to update the value of **CaptureClick** bound to [@StorageLink](../../../application-dev/ui/state-management/arkts-appstorage.md#storagelink). This triggers the **onCaptureClick** method and starts playing the animation effect.

   <!-- @[capture_click](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Camera/cameraAnimSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   onCaptureClick(): void {
     Logger.info(TAG, 'onCaptureClick');
     this.flashBlackAnim();
   }
   ```

## Blur Animation

You can use preview stream snapshots to create a blur effect for mode switching or front/rear camera switching.

The sample code in the following steps (except step 2) is the internal method or logic of a custom component (component decorated by @Component).

1. Import dependencies. Specifically, import the camera, image, and ArkUI modules.

   <!-- @[import_section](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Camera/cameraAnimSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   import { camera } from '@kit.CameraKit';
   import { image } from '@kit.ImageKit';
   import { curves } from '@kit.ArkUI';
   ```

2. Obtain a preview stream snapshot.

   Preview stream snapshots are obtained by calling [image.createPixelMapFromSurface](../../reference/apis-image-kit/arkts-apis-image-f.md#imagecreatepixelmapfromsurface11) provided by the image module. In this API, **surfaceId** is the surface ID of the current preview stream, and **size** is the width and height of the current preview stream profile. Create a snapshot utility class (TS file), import the dependency, and export the snapshot retrieval API for the page to use. The code snippet below shows the implementation of the snapshot utility class.

   <!-- @[blur_animate_util](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Camera/cameraAnimSample/entry/src/main/ets/common/utils/BlurAnimateUtil.ts) -->
   
   ``` TypeScript
   export class BlurAnimateUtil {
     public static surfaceShot: image.PixelMap;
     // ...
   
     /**
      * Obtain a surface snapshot.
      * @param surfaceId
      * @returns
      */
     public static async doSurfaceShot(surfaceId: string) {
       Logger.info(TAG, `doSurfaceShot surfaceId:${surfaceId}.`);
       if ('' === surfaceId) {
         Logger.error(TAG, 'surface not ready!');
         return;
       }
       try {
         if (this.surfaceShot) {
           await this.surfaceShot.release();
         }
         this.surfaceShot = await image.createPixelMapFromSurface(surfaceId, {
           size: { width: Constants.X_COMPONENT_SURFACE_WIDTH, height: Constants.X_COMPONENT_SURFACE_HEIGHT }, // Obtain the width and height of the preview stream profile.
           x: 0,
           y: 0
         });
         let imageInfo: image.ImageInfo = await this.surfaceShot.getImageInfo();
         Logger.info('doSurfaceShot surfaceShot:' + JSON.stringify(imageInfo.size));
       } catch (err) {
         Logger.error(JSON.stringify(err))
       }
     }
   
     public static getSurfaceShot() {
       return this.surfaceShot;
     }
   }
   ```

3. Build a snapshot component.

   Define a snapshot component, and place it above the XComponent of the preview stream to block the XComponent.

   Define the component's properties as follows:

   <!-- @[anim_states](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Camera/cameraAnimSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   @State isShowBlur: boolean = false;
   @State isShowBlack: boolean = false;
   @StorageLink('modeChange') @Watch('onModeChange') modeChangeFlag: number = 0;
   @StorageLink('switchCamera') @Watch('onSwitchCamera') switchCameraFlag: number = 0;
   @StorageLink('frameStart') @Watch('onFrameStart') frameStartFlag: number = 0;
   @StorageLink('captureClick') @Watch('onCaptureClick') captureClickFlag: number = 0;
   @StorageLink('surfaceShot') screenshotPixelMap: image.PixelMap | undefined = undefined; // Snapshot of the preview stream.
   @StorageLink('curPosition') curPosition: number = 0; // Current front/rear camera lens status.
   @State shotImgBlur: number = 0;
   @State shotImgOpacity: number = 1;
   @State shotImgScale: ScaleOptions = { x: 1, y: 1 };
   @State shotImgRotation: RotateOptions = { y: BlurAnimateUtil.ROTATE_AXIS, angle: BlurAnimateUtil.IMG_FLIP_ANGLE_0 }
   @State flashBlackOpacity: number = 1;
   ```

   Implement the snapshot component as follows:

   <!-- @[blur_component](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Camera/cameraAnimSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   if (this.isShowBlur) {
     Column() {
       Image(this.screenshotPixelMap)
         .blur(this.shotImgBlur)
         .opacity(this.shotImgOpacity)
         .rotate(this.shotImgRotation) // Rotation capability provided by ArkUI, used to rotate components along a specified coordinate system.
         .scale(this.shotImgScale)
         .width(this.getUIContext().px2vp(Constants.X_COMPONENT_SURFACE_HEIGHT))
         .height(this.getUIContext().px2vp(Constants.X_COMPONENT_SURFACE_WIDTH))
         .syncLoad(true)
     }
     .width(this.getUIContext().px2vp(Constants.X_COMPONENT_SURFACE_HEIGHT))
     .height(this.getUIContext().px2vp(Constants.X_COMPONENT_SURFACE_WIDTH))
   }
   ```

4. (Optional) Implement the fade-in blur effect.

   The mode switching animation is implemented in two phases: fade-in blur animation and fade-out blur animation.

   When a user touches a button, and the camera takes a snapshot of the preview stream. The snapshot component is displayed, which gradually blurs over the existing preview stream, implementing the fade-in blur animation.

   > **NOTE**
   >
   > Since the [image.createPixelMapFromSurface](../../reference/apis-image-kit/arkts-apis-image-f.md#imagecreatepixelmapfromsurface11) API provided by the graphics framework retrieves a [PixelMap](../../reference/apis-image-kit/arkts-apis-image-PixelMap.md) by capturing the surface, its output differs from the rendering logic of the [XComponent](../../reference/apis-arkui/arkui-ts/ts-basic-components-xcomponent.md) component. You must apply different **rotation compensation to both the image content and the component** based on **whether the front or rear camera is in use**.

   <!-- @[show_blur_anim](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Camera/cameraAnimSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   private async showBlurAnim() {
     Logger.info(TAG, 'showBlurAnim E');
     // Obtain the surface snapshot.
     let shotPixel = BlurAnimateUtil.getSurfaceShot();
     // The rear camera is used.
     if (this.curPosition === 0) {
       Logger.info(TAG, 'showBlurAnim BACK');
       // Rotation compensation of 90° for rear camera snapshots on bar phones.
       await shotPixel.rotate(BlurAnimateUtil.IMG_ROTATE_ANGLE_90);
       // Initial flip angle of 0° for rear camera snapshots on bar phones.
       this.shotImgRotation = { y: BlurAnimateUtil.ROTATE_AXIS, angle: BlurAnimateUtil.IMG_FLIP_ANGLE_0 };
     } else {
       Logger.info(TAG, 'showBlurAnim FRONT');
       // Rotation compensation of 270° for front camera snapshots on bar phones.
       await shotPixel.rotate(BlurAnimateUtil.IMG_ROTATE_ANGLE_270);
       // Mirror compensation for front camera snapshots on bar phones.
       this.shotImgRotation = { y: BlurAnimateUtil.ROTATE_AXIS, angle: BlurAnimateUtil.IMG_FLIP_ANGLE_180 };
     }
     this.screenshotPixelMap = shotPixel;
     // Initialize animation parameters.
     this.shotImgBlur = 0; // No blur.
     this.shotImgOpacity = 1; // Opaque.
     // Trigger page rendering.
     this.isShowBlur = true;
     animateToImmediately(
       {
         duration: BlurAnimateUtil.SHOW_BLUR_DURATION,
         curve: Curve.Friction,
         onFinish: async () => {
           Logger.info(TAG, 'showBlurAnim X');
         }
       },
       () => {
         // Implement the blur change animation.
         this.shotImgBlur = BlurAnimateUtil.ANIM_MODE_SWITCH_BLUR;
       }
     );
   }
   ```

5. Implement the fade-out blur animation.

   The fade-out blur animation is triggered by the event [on('frameStart')](../../reference/apis-camera-kit/arkts-apis-camera-PreviewOutput.md#onframestart) of the new preview stream. During this effect, the snapshot component gradually becomes clear, revealing the new preview stream.

   <!-- @[hide_blur_anim](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Camera/cameraAnimSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   private hideBlurAnim(): void {
     this.isShowBlack = false;
     Logger.info(TAG, 'hideBlurAnim E');
     animateToImmediately({
       duration: BlurAnimateUtil.HIDE_BLUR_DURATION,
       curve: Curve.FastOutSlowIn,
       onFinish: () => {
         // Remove the blur component from the component tree.
         this.isShowBlur = false;
         this.shotImgBlur = 0;
         this.shotImgOpacity = 1;
         Logger.info(TAG, 'hideBlurAnim X');
       }
     }, () => {
       // Change the opacity of the snapshot component.
       this.shotImgOpacity = 0;
     });
   }
   ```

6. (Optional) Implement the blur-and-flip animation.

   The animation is carried out in two phases: blur-and-flip and fade-out blur, where fade-out blur is the same as that in step 5.

   The blur-and-flip animation is realized through two stages of component rotation—initially a 90° rotation outwards, and then a 90° rotation inwards—accompanied by additional effects such as blur, opacity changes, and scaling.

   To ensure that the preview stream is not exposed during flip, you must also build a blackout component to mask the XComponent, following the instructions provided in step 2 in [Blackout Animation](#blackout-animation).

   <!-- @[rotate_anim](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Camera/cameraAnimSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   /**
    * A 90° rotation outwards first for transition between the front and real cameras.
    */
   private async rotateFirstAnim() {
     Logger.info(TAG, 'rotateFirstAnim E');
     // Obtain the surface snapshot.
     let shotPixel = BlurAnimateUtil.getSurfaceShot();
     // Switch from the rear camera to the front camera.
     if (this.curPosition === 1) {
       Logger.info(TAG, 'rotateFirstAnim BACK');
         // Rotation compensation of 90° for snapshots when switching from rear to front camera on bar phones.
       Rotation provided by await shotPixel.rotate(BlurAnimateUtil.IMG_ROTATE_ANGLE_90); // Rotation capability provided by Image Kit, used to handle rotation of the image itself.
       // Initial flip angle of 0° for snapshots when switching from rear to front camera on bar phones.
       this.shotImgRotation = { y: BlurAnimateUtil.ROTATE_AXIS, angle: BlurAnimateUtil.IMG_FLIP_ANGLE_0 };
     } else {
       Logger.info(TAG, 'rotateFirstAnim FRONT');
       // Rotation compensation of 270° for snapshots when switching from front to rear camera on bar phones.
       await shotPixel.rotate(BlurAnimateUtil.IMG_ROTATE_ANGLE_270);
       // Initial flip angle of 180° for snapshots when switching from front to rear camera on bar phones.
       this.shotImgRotation = { y: BlurAnimateUtil.ROTATE_AXIS, angle: BlurAnimateUtil.IMG_FLIP_ANGLE_180 };
     }
     this.screenshotPixelMap = shotPixel;
     // Trigger page rendering.
     this.isShowBlack = true;
     this.isShowBlur = true;
     animateToImmediately(
       {
         duration: BlurAnimateUtil.ROTATION_DURATION,
         delay: BlurAnimateUtil.FLIP_DELAY, // This delay ensures that the component's scaling and blur effects are triggered in prior to the flip effect.
         curve: curves.cubicBezierCurve(0.20, 0.00, 0.83, 1.00),
         onFinish: () => {
           Logger.info(TAG, 'rotateFirstAnim X');
           // Trigger the second-stage rotation after onFinish is invoked.
           this.rotateSecondAnim();
         }
       },
       () => {
         // Flip animation effect for the snapshot.
         if (this.curPosition === 1) {
           this.shotImgRotation = { y: BlurAnimateUtil.ROTATE_AXIS, angle: BlurAnimateUtil.IMG_FLIP_ANGLE_90 };
         } else {
           this.shotImgRotation = { y: BlurAnimateUtil.ROTATE_AXIS, angle: BlurAnimateUtil.IMG_FLIP_ANGLE_270 };
         }
       }
     )
   }
   
   /**
    * Flip inwards by 90°.
    */
   async rotateSecondAnim() {
     Logger.info(TAG, 'rotateSecondAnim E');
     // Obtain the surface snapshot.
     let shotPixel = BlurAnimateUtil.getSurfaceShot();
     // The rear camera is used.
     if (this.curPosition === 1) {
       // Rotation compensation of 90° for rear camera on bar phones.
       Rotation provided by await shotPixel.rotate(BlurAnimateUtil.IMG_ROTATE_ANGLE_90); // Rotation capability provided by Image Kit, used to handle rotation of the image itself.
       // Instantly adjust to -90° to ensure the image is not mirrored after the second-stage rotation.
       this.shotImgRotation = { y: BlurAnimateUtil.ROTATE_AXIS, angle: BlurAnimateUtil.IMG_FLIP_ANGLE_MINUS_90 };
     } else { // The front camera is used.
       // Rotation compensation of 270° for front camera snapshots on bar phones.
       await shotPixel.rotate(BlurAnimateUtil.IMG_ROTATE_ANGLE_270);
       // Mirror compensation for front camera snapshots on bar phones.
       this.shotImgRotation = { y: BlurAnimateUtil.ROTATE_AXIS, angle: BlurAnimateUtil.IMG_FLIP_ANGLE_180 };
     }
     this.screenshotPixelMap = shotPixel;
   
     animateToImmediately(
       {
         duration: BlurAnimateUtil.ROTATION_DURATION,
         curve: curves.cubicBezierCurve(0.17, 0.00, 0.20, 1.00),
         onFinish: () => {
           Logger.info(TAG, 'rotateSecondAnim X');
         }
       },
       () => {
         // Flip to the initial state.
         if (this.curPosition === 1) {
           this.shotImgRotation = { y: BlurAnimateUtil.ROTATE_AXIS, angle: BlurAnimateUtil.IMG_FLIP_ANGLE_0 };
         } else {
           this.shotImgRotation = { y: BlurAnimateUtil.ROTATE_AXIS, angle: BlurAnimateUtil.IMG_FLIP_ANGLE_180 };
         }
       }
     )
   }
   
   /**
    * Flip outwards by 90°.
    */
   blurFirstAnim() {
     Logger.info(TAG, 'blurFirstAnim E');
     // Initialize animation parameters.
     this.shotImgBlur = 0; // No blur.
     this.shotImgOpacity = 1; // Opaque.
     this.shotImgScale = { x: 1, y: 1 };
     animateToImmediately(
       {
         duration: BlurAnimateUtil.ROTATION_DURATION,
         curve: Curve.Sharp,
         onFinish: () => {
           Logger.info(TAG, 'blurFirstAnim X');
           this.blurSecondAnim();
         }
       },
       () => {
         // Implement the blur change animation.
         this.shotImgBlur = BlurAnimateUtil.ANIM_MODE_SWITCH_BLUR;
         // Implement the scale change animation.
         this.shotImgScale = { x: BlurAnimateUtil.IMG_SCALE, y: BlurAnimateUtil.IMG_SCALE };
       }
     );
   }
   
   /**
    * Flip inwards by 90°.
    */
   blurSecondAnim() {
     Logger.info(TAG, 'blurSecondAnim E');
     animateToImmediately(
       {
         duration: BlurAnimateUtil.ROTATION_DURATION,
         curve: Curve.Sharp,
         onFinish: () => {
           Logger.info(TAG, 'blurSecondAnim X');
         }
       },
       () => {
         this.shotImgScale = { x: 1, y: 1 };
       }
     )
   }
   ```

7. Trigger the animations on demand.

   Mode switch animation trigger: Tap the mode button to immediately execute the **doSurfaceShot** snapshot method, update the value of **modeChange** bound to [@StorageLink](../../../application-dev/ui/state-management/arkts-appstorage.md#storagelink), and trigger the **onModeChange** method to start the animation.

   <!-- @[on_mode_change](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Camera/cameraAnimSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   onModeChange(): void {
     Logger.info(TAG, 'onModeChange');
     this.showBlurAnim();
   }
   ```

   Front/rear camera switch animation trigger: Tap the front/rear switch button to immediately execute the **doSurfaceShot** snapshot, update the value of **switchCamera** bound to [@StorageLink](../../../application-dev/ui/state-management/arkts-appstorage.md#storagelink), and trigger the **onSwitchCamera** method to start the animation.

   <!-- @[on_switch_camera](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Camera/cameraAnimSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   onSwitchCamera(): void {
     Logger.info(TAG, 'onSwitchCamera');
     this.blurFirstAnim();
     this.rotateFirstAnim();
   }
   ```

   Fade-out blur animation trigger: Listen for the preview stream first frame callback [on('frameStart')](../../reference/apis-camera-kit/arkts-apis-camera-PreviewOutput.md#onframestart), update the value of **frameStart** bound to [@StorageLink](../../../application-dev/ui/state-management/arkts-appstorage.md#storagelink), and trigger the **onFrameStart** method to start the animation.

   <!-- @[on_frame_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Camera/cameraAnimSample/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   onFrameStart(): void {
     Logger.info(TAG, 'onFrameStart');
     this.hideBlurAnim();
   }
   ```
