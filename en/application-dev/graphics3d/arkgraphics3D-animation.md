# Controlling and Managing ArkGraphics 3D Scene Animations
<!--Kit: ArkGraphics 3D-->
<!--Subsystem: Graphics-->
<!--Owner: @zzhao0-->
<!--Designer: @zdustc-->
<!--Tester: @zhangyue283-->
<!--Adviser: @ge-yafang-->

Animations, an important resource type in a 3D scene, is used to control the motion of elements in the scene. For example, to simulate a scene where a person walks, it is difficult to calculate and set the rotation angle of every joint of the person in each frame. When making such an animation, the resource producer saves key frame data of the animation and the interpolator type between key frames in a model file.

ArkGraphics 3D provides APIs for you to play and control animations to achieve the expected rendering effect in the scene.

## How to Develop
  1. Import the required modules.

     Import the core types provided by ArkGraphics 3D in the page script to create and control 3D scenes, cameras, and animation resources.

     <!-- @[anim_header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/ArkGraphics3D/entry/src/main/ets/arkgraphic/animation.ets) -->
     
     ``` TypeScript
     import { Animation, Camera, Scene, SceneResourceFactory } from '@kit.ArkGraphics3D';
     ```

  2. Load scene resources.

     Call **Scene.load()** to load the .glb (or .gltf) model from the **resources/rawfile/** directory of your application, and obtain a scene object upon completion.

     <!-- @[anim_load](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/ArkGraphics3D/entry/src/main/ets/arkgraphic/animation.ets) -->
     
     ``` TypeScript
     Scene.load($rawfile('gltf/BrainStem/glTF/BrainStem.glb'))
       .then(async (result: Scene) => {
         this.scene = result;
         let rf: SceneResourceFactory = this.scene.getResourceFactory();
       // ···
       }).catch((err: string) => {
         console.error(err);
     });
     ```

  3. Obtain an animation and register callbacks.

     Obtain an animation resource from **scene.animations[0]**, enable the animation, and register the **onStarted()** and **onFinished()** callbacks to listen for the animation playback status or trigger logic.

     ArkGraphics 3D provides the following animation callback APIs:
      - **onStarted()**: called when the animation starts (either through a start or restart operation).
      - **onFinished()**: called when the animation completes playback or the finish operation is performed.

     <!-- @[anim_pick_anim](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/ArkGraphics3D/entry/src/main/ets/arkgraphic/animation.ets) -->
     
     ``` TypeScript
     this.anim = this.scene.animations[0];
     if (this.anim) {
       this.anim.enabled = true;
       // Register callback function
       this.anim.onStarted(() => {
       // ···
         this.animationCallbackInvoked = 'animation on start';
       });
     
       this.anim.onFinished(() => {
       // ···
         this.animationCallbackInvoked = 'animation on finish';
       });
       // ···
     } else {
       console.error('No animation found in scene.');
     }
     ```

  4. Create a camera and configure scene rendering parameters.

     Call **SceneResourceFactory.createCamera()** to create a camera and adjust the viewing position. Then, wrap the loaded scene into a SceneOptions object and specify the rendering type as **ModelType.SURFACE** to render the scene content via Component3D.

     <!-- @[anim_camera_sceneopt](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/ArkGraphics3D/entry/src/main/ets/arkgraphic/animation.ets) -->
     
     ``` TypeScript
     // create a new camera.
     this.cam = await rf.createCamera({ 'name': 'Camera' });
     // set the camera.
     this.cam.enabled = true;
     this.cam.position.z = 5;
     this.sceneOpt = { scene: this.scene, modelType: ModelType.SURFACE } as SceneOptions;
     ```

  5. Build the UI and control the animation.

     Render the 3D scene using Component3D and add buttons to the UI to control the animation playback status.

     ArkGraphics 3D provides the following APIs to control the animation status:
      - **start**: plays an animation based on the current progress.
      - **stop**: stops playing an animation and sets its progress to **0** (not started).
      - **finish**: finishes the playing of an animation and sets its progress of **1** (finished).
      - **pause**: pauses an animation. The animation remains in the current playing progress.
      - **restart**: plays an animation from the beginning.
      - **seek**: jumps to a specific progress point in the animation. For example, **seek(0.3)** reaches 30% of the total duration.

     <!-- @[anim_controls](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/ArkGraphics3D/entry/src/main/ets/arkgraphic/animation.ets) -->
     
     ``` TypeScript
     Button('start')
     // ···
       .onClick(async () => {
         if (!this.scene || !this.scene.animations[0]) {
           return;
         }
         this.anim = this.scene.animations[0];
         this.anim.start();
       });
     
     Button('pause')
     // ···
       .onClick(async () => {
         if (!this.scene || !this.scene.animations[0]) {
           return;
         }
         this.anim = this.scene.animations[0];
         this.anim.pause();
       });
     
     Button('stop')
     // ···
       .onClick(async () => {
         if (!this.scene || !this.scene.animations[0]) {
           return;
         }
         this.anim = this.scene.animations[0];
         this.anim.stop();
       });
     
     Button('finish')
     // ···
       .onClick(async () => {
         if (!this.scene || !this.scene.animations[0]) {
           return;
         }
         this.anim = this.scene.animations[0];
         this.anim.finish();
       });
     
     Button('restart')
     // ···
       .onClick(async () => {
         if (!this.scene || !this.scene.animations[0]) {
           return;
         }
         this.anim = this.scene.animations[0];
         this.anim.restart();
       });
     
     Button('seek to 30% progress')
     // ···
       .onClick(async () => {
         if (!this.scene || !this.scene.animations[0]) {
           return;
         }
         this.anim = this.scene.animations[0];
         // seek to 30%
         this.anim.seek(0.3);
       });
     ```
