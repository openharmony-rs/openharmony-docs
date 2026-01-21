# 创建并使用环境资源
<!--Kit: ArkGraphics 3D-->
<!--Subsystem: Graphics-->
<!--Owner: @zzhao0-->
<!--Designer: @zdustc-->
<!--Tester: @zhangyue283-->
<!--Adviser: @ge-yafang-->

环境（Environment）：环境是3D场景背景的一种描述，可以基于图片进行创建。通过将一张图片进行正方体或者球体的映射处理，将图片贴在正方体或者球体上，在3D场景中模拟真实的环境。

ArkGraphics 3D支持用户创建环境资源，定义3D场景的背景。

## 开发步骤
  1. 导入相关模块。

     在页面脚本中导入ArkGraphics 3D提供的核心类型，用于创建场景、相机、材质、图片等对象。

     <!-- @[resource_header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/ArkGraphics3D/entry/src/main/ets/arkgraphic/resource.ets) -->
     
     ``` TypeScript
     import { Camera, Environment, Geometry, Image, Material, MaterialType, Scene, SceneResourceFactory,
       SceneResourceParameters, Shader, ShaderMaterial, EnvironmentBackgroundType } from '@kit.ArkGraphics3D';
     ```

  2. 加载场景并设置渲染参数。

     调用Scene.load()方法加载.glb或.gltf格式的模型文件，并在加载完成后获取Scene对象。随后构建SceneOptions对象，指定场景及渲染模式，用于后续通过Component3D将场景内容渲染到界面中。

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

  3. 初始化相机。

     创建相机对象并设置相机启用状态与观察位置，用于后续展示模型。

     <!-- @[scene_camera_init](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/ArkGraphics3D/entry/src/main/ets/arkgraphic/resource.ets) -->
     
     ``` TypeScript
     this.cam = await this.rf.createCamera({ 'name': 'Camera1' });
     this.cam.enabled = true;
     this.cam.position.z = 5;
     ```

  4. 获取几何体节点。

     通过Scene.getNodeByPath()方法获取目标模型的几何体（Geometry）节点，并记录其原始材质，以便在后续修改材质后可进行回退或恢复操作。

     <!-- @[geometry_node_get](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/ArkGraphics3D/entry/src/main/ets/arkgraphic/resource.ets) -->
     
     ``` TypeScript
     this.geom = this.scene.getNodeByPath('rootNode_/Unnamed Node 1/AnimatedCube') as Geometry;
     
     // record original material
     this.originalMat = this.geom.mesh.subMeshes[0].material;
     ```

  5. 创建环境并绑定图片。

     使用SceneResourceFactory.createEnvironment()创建环境对象，并通过createImage()加载环境贴图。设置backgroundType为等距柱状投影背景，将图片绑定到environmentImage，再调整indirectDiffuseFactor等属性以控制环境光强度。

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

  6. 应用环境到场景。

     在按钮点击事件中调用createEnvironmentPromise()创建环境资源，并将其赋值给场景的environment属性，使环境背景立即生效。

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

<!--RP1-->
## 相关实例

对于3D资源更加综合的使用可以参考以下实例：
- [3D引擎接口示例（ArkTS）（API12）](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Graphics/Graphics3d)
<!--RP1End-->