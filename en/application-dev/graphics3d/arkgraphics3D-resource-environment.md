# Creating and Using Environment Resources
<!--Kit: ArkGraphics 3D-->
<!--Subsystem: Graphics-->
<!--Owner: @zzhao0-->
<!--Designer: @zdustc-->
<!--Tester: @zhangyue283-->
<!--Adviser: @ge-yafang-->

Environment is a description of the 3D scene background, which can be created based on images. To simulate a real-world environment in a 3D scene, you can map a square or sphere onto an image and wrap the image around the square or sphere.

ArkGraphics 3D allows you to create environment resources and define the background of 3D scenes.

## How to Develop
  1. Import the required modules.

     Import the core types provided by ArkGraphics 3D in the page script to create objects like scenes, cameras, materials, and images.

     <!-- @[resource_header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/ArkGraphics3D/entry/src/main/ets/arkgraphic/resource.ets) -->
     
     ``` TypeScript
     import { Camera, Environment, Geometry, Image, Material, MaterialType, Scene, SceneResourceFactory,
       SceneResourceParameters, Shader, ShaderMaterial, EnvironmentBackgroundType } from '@kit.ArkGraphics3D';
     ```

  2. Load the scene and configure rendering parameters.

     Call **Scene.load()** to load model files in .glb or .gltf format, and obtain a scene object upon completion. Then, construct a SceneOptions object to specify the scene and rendering mode for rendering the scene content via Component3D.

     <!-- @[scene_load_init](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/ArkGraphics3D/entry/src/main/ets/arkgraphic/resource.ets) -->
     
     ``` TypeScript
     if (this.scene === null) {
       // Switched from .gltf to .glb; same content, different format
       Scene.load($rawfile('gltf/CubeWithFloor/glTF/AnimatedCube.glb'))
         .then(async (result: Scene) => {
           // Assign loaded scene to globalScene for unified resource creation
           globalScene = result;
           this.scene = result;
           this.sceneOpt = { scene: this.scene, modelType: ModelType.SURFACE } as SceneOptions;
           this.rf = this.scene.getResourceFactory();
         // ···
         })
         .catch((error: string) => {
           console.error('init error: ' + error + '.');
         });
     }
     ```

  3. Initialize the camera.

     Create a camera object, and set its enabled state and viewing position for subsequent model display.

     <!-- @[scene_camera_init](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/ArkGraphics3D/entry/src/main/ets/arkgraphic/resource.ets) -->
     
     ``` TypeScript
     this.cam = await this.rf.createCamera({ 'name': 'Camera1' });
     this.cam.enabled = true;
     this.cam.position.z = 5;
     ```

  4. Obtain the geometry node.

     Call **Scene.getNodeByPath()** to obtain the geometry node of the target model, and record its original material. This enables rollback or recovery in case the material is later modified.

     <!-- @[geometry_node_get](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/ArkGraphics3D/entry/src/main/ets/arkgraphic/resource.ets) -->
     
     ``` TypeScript
     this.geom = this.scene.getNodeByPath('rootNode_/Unnamed Node 1/AnimatedCube') as Geometry;
     
     // record original material
     this.originalMat = this.geom.mesh.subMeshes[0].material;
     ```

  5. Create an environment and bind an image.

     Call **SceneResourceFactory.createEnvironment()** to create an environment object, and call **createImage()** to load an environment map. Set **backgroundType** to the equirectangular map type, bind the image to **environmentImage**, and adjust properties like **indirectDiffuseFactor** to control the ambient lighting intensity.

     <!-- @[create_environment_promise](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/ArkGraphics3D/entry/src/main/ets/arkgraphic/resource.ets) -->
     
     ``` TypeScript
     function createEnvironmentPromise() : Promise<Environment> {
       return new Promise((resolve, reject) => {
         // Ensure the scene is loaded before accessing sceneFactory
         if (globalScene) {
           let sceneFactory: SceneResourceFactory = globalScene.getResourceFactory();
     
           // Manually load environment maps (.ktx/.jpg/.png etc.)
           let sceneImageParameter: SceneResourceParameters = { name: 'image', uri: $rawfile('image/Cube_BaseColor.png') };
           let image: Promise<Image> = sceneFactory.createImage(sceneImageParameter);
           image.then(async (imageEntity: Image) => {
             // Create Environment
             let sceneEnvironmentParameter: SceneResourceParameters = { name: 'env' };
             let env: Promise<Environment> = sceneFactory.createEnvironment(sceneEnvironmentParameter);
             env.then(async (envEntity: Environment) => {
               envEntity.backgroundType = EnvironmentBackgroundType.BACKGROUND_EQUIRECTANGULAR;
               envEntity.environmentImage  = imageEntity;
               // Set environment related properties
               envEntity.indirectDiffuseFactor.x = 1;
               envEntity.indirectDiffuseFactor.y = 1;
               envEntity.indirectDiffuseFactor.z = 1;
               envEntity.indirectDiffuseFactor.w = 1;
               resolve(envEntity);
             }).catch((err: string) => {
               console.error('Environment mapping material create failed: ' + err + '.');
               reject(err);
             });
           }).catch((err: string) => {
             console.error('Image load failed: ' + err);
             reject(err);
           });
         } else {
           reject('Scene is not loaded yet.');
         }
       });
     }
     ```

  6. Apply the environment to the scene.

     Call **createEnvironmentPromise()** in the button click event to create environment resources, and assign them to the environment property of the scene so that the environment background takes effect immediately.

     <!-- @[environment_button_action](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/ArkGraphics3D/entry/src/main/ets/arkgraphic/resource.ets) -->
     
     ``` TypeScript
     Button('Add to Environment')
     // ···
       .onClick(async (): Promise<void> => {
         console.info('Start to replace with a material of image');
     
         if (!this.scene || !this.cam) {
           return;
         }
     
         this.env = await createEnvironmentPromise();
         if (this.env) {
           this.scene.environment = this.env;
         }
       });
     ```

