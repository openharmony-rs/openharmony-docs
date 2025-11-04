# 创建并使用图片资源
<!--Kit: ArkGraphics 3D-->
<!--Subsystem: Graphics-->
<!--Owner: @zzhao0-->
<!--Designer: @zdustc-->
<!--Tester: @zhangyue283-->
<!--Adviser: @ge-yafang-->

图片（Image）：图片本质上是一个储存信息的二维内存块(buffer)，用于储存3D渲染计算过程需要的相关信息，比如基础色、法线等等。

ArkGraphics 3D提供基于png、jpg、ktx格式创建Image资源的能力，支持用户自定义需要的Image资源。

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

  5. 创建图片资源并绑定到材质。

     使用SceneResourceFactory.createImage()创建图片资源，再通过createMaterial()创建Shader材质。将图片资源绑定到Shader输入属性BASE_COLOR_Image上，使模型表面贴图生效。

     <!-- @[create_image_promise](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/ArkGraphics3D/entry/src/main/ets/arkgraphic/resource.ets) -->
     
     ``` TypeScript
     function createImagePromise(): Promise<Image> {
       return new Promise((resolve, reject) => {
         // Ensure the scene is loaded before accessing sceneFactory
         if (globalScene) {
           let sceneFactory: SceneResourceFactory = globalScene.getResourceFactory();
     
           let sceneImageParameter: SceneResourceParameters = {
             name: 'image',
             uri: $rawfile('image/Cube_BaseColor.png')
           };
     
           let image: Promise<Image> = sceneFactory.createImage(sceneImageParameter);
           image.then((imageEntity: Image) => {
             resolve(imageEntity);
           }).catch((err: string) => {
             console.error('Image load failed: ' + err + '.');
             reject(err);
           });
         } else {
           reject('Scene is not loaded yet.');
         }
       });
     }
     ```

  6. 应用图片材质到模型节点。

     在按钮点击回调中，通过createShader()创建Shader并绑定材质对象，调用createImagePromise()获取图片资源并将其应用到模型几何体上，实现贴图替换。

     <!-- @[replace_with_image_material](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/ArkGraphics3D/entry/src/main/ets/arkgraphic/resource.ets) -->
     
     ``` TypeScript
     Button('Replace with a Image material')
     // ···
       .onClick(async (): Promise<void> => {
         console.info('Start to replace with a material of image');
     
         if (!this.scene || !this.cam || !this.rf) {
           return;
         }
     
         // create shader
         this.shader = await this.rf.createShader({
           name: 'shaderResource',
           uri: $rawfile('shaders/custom_shader/custom_material_sample.shader')
         });
     
         // create imageMat
         this.imageMat = await this.rf.createMaterial({ name: 'imageMat' }, MaterialType.SHADER) as ShaderMaterial;
     
         // bind between shader and imageMat
         this.imageMat.colorShader = this.shader;
         let createdImage =  await createImagePromise();
         if (createdImage) {
           this.imageMat.colorShader.inputs['BASE_COLOR_Image'] = createdImage;
         }
     
         this.geom = this.scene.getNodeByPath('rootNode_/Unnamed Node 1/AnimatedCube') as Geometry;
     
         this.geom.mesh.materialOverride = undefined;
         this.geom.mesh.subMeshes[0].material = this.imageMat;
       })
     ```

<!--RP1-->
## 相关实例

对于3D资源更加综合的使用可以参考以下实例：
- [3D引擎接口示例（ArkTS）（API12）](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Graphics/Graphics3d)
<!--RP1End-->