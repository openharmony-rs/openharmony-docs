# SceneResourceFactory

场景资源工厂.

**继承/实现关系：** SceneResourceFactory extends [RenderResourceFactory](arkts-arkgraphics3d-scene-renderresourcefactory-i.md#RenderResourceFactory)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface SceneResourceFactory--><!--Device-unnamed-export interface SceneResourceFactory-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## createCamera

```TypeScript
createCamera(params: SceneNodeParameters): Promise<Camera>
```

Create a camera.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SceneResourceFactory-createCamera(params: SceneNodeParameters): Promise<Camera>--><!--Device-SceneResourceFactory-createCamera(params: SceneNodeParameters): Promise<Camera>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [SceneNodeParameters](arkts-arkgraphics3d-scene-scenenodeparameters-i.md) | 是 | 创建相机的参数 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Camera](arkts-arkgraphics3d-scenenodes-camera-i.md)&gt; | 返回创建的相机 |

## 示例

```TypeScript
import { SceneNodeParameters, Camera, SceneResourceFactory, Scene } from '@kit.ArkGraphics3D';

function createCameraPromise(): Promise<Camera> {
  return new Promise((resolve, reject) => {
    // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
    let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
    scene.then(async (result: Scene) => {
      let sceneFactory: SceneResourceFactory = result.getResourceFactory();
      let sceneCameraParameter: SceneNodeParameters = { name: "camera1" };
      // 创建相机
      let camera: Camera = await sceneFactory.createCamera(sceneCameraParameter);
      resolve(camera);
    }).catch((error: Error) => {
      console.error('Scene load failed:', error);
      reject(error);
    });
  });
}
```

## createCamera

```TypeScript
createCamera(params: SceneNodeParameters, cameraParams: CameraParameters): Promise<Camera>
```

Create a camera.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SceneResourceFactory-createCamera(params: SceneNodeParameters, cameraParams: CameraParameters): Promise<Camera>--><!--Device-SceneResourceFactory-createCamera(params: SceneNodeParameters, cameraParams: CameraParameters): Promise<Camera>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [SceneNodeParameters](arkts-arkgraphics3d-scene-scenenodeparameters-i.md) | 是 | 创建相机的参数 |
| cameraParams | [CameraParameters](arkts-arkgraphics3d-scene-cameraparameters-i.md) | 是 | 相机特定的额外参数 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Camera](arkts-arkgraphics3d-scenenodes-camera-i.md)&gt; | 返回创建的相机 |

## 示例

```TypeScript
import { SceneNodeParameters, Camera, SceneResourceFactory, Scene, CameraParameters,
  RenderingPipelineType } from '@kit.ArkGraphics3D';

function createCameraPromise(): Promise<Camera> {
  return new Promise((resolve, reject) => {
    // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
    let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
    scene.then(async (result: Scene) => {
      let sceneFactory: SceneResourceFactory = result.getResourceFactory();
      let nodeParameter: SceneNodeParameters = { name: "camera1" };
      let camParameter: CameraParameters = {renderingPipeline: RenderingPipelineType.FORWARD};
      // 创建相机
      let camera: Camera = await sceneFactory.createCamera(nodeParameter, camParameter);
      resolve(camera);
    }).catch((error: Error) => {
      console.error('Scene load failed:', error);
      reject(error);
    });
  });
}
```

## createEffect

```TypeScript
createEffect(params: EffectParameters): Promise<Effect>
```

创建特效.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SceneResourceFactory-createEffect(params: EffectParameters): Promise<Effect>--><!--Device-SceneResourceFactory-createEffect(params: EffectParameters): Promise<Effect>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [EffectParameters](arkts-arkgraphics3d-scene-effectparameters-i.md) | 是 | 创建特效的参数. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Effect](arkts-arkgraphics3d-sceneresources-effect-i.md)&gt; | 返回创建的特效. |

## 示例

```TypeScript
import { SceneResourceFactory, Scene, Effect, EffectParameters } from '@kit.ArkGraphics3D';

function createEffect() : Promise<Effect> {
  return new Promise((resolve, reject) => {
    let scene: Promise<Scene> = Scene.load();
    scene.then(async (result: Scene | undefined) => {
      if (!result) {
        return;
      }
      let sceneFactory: SceneResourceFactory = result.getResourceFactory();
      // 特效ID，固定格式为'XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX'，比如'e68a7f45-2d21-4a0d-9aef-7d9c825d3f12'
      let params: EffectParameters = {effectId: "e68a7f45-2d21-4a0d-9aef-7d9c825d3f12"};
      let effect: Effect = await sceneFactory.createEffect(params);
      resolve(effect);
    }).catch((error: Error) => {
      console.error('Scene load failed:', error);
      reject(error);
    });
  });
}
```

## createEnvironment

```TypeScript
createEnvironment(params: SceneResourceParameters): Promise<Environment>
```

Create an environment.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SceneResourceFactory-createEnvironment(params: SceneResourceParameters): Promise<Environment>--><!--Device-SceneResourceFactory-createEnvironment(params: SceneResourceParameters): Promise<Environment>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [SceneResourceParameters](arkts-arkgraphics3d-scene-sceneresourceparameters-i.md) | 是 | 创建环境对象的参数 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Environment](arkts-arkgraphics3d-sceneresources-environment-i.md)&gt; | 返回创建的环境 |

## 示例

```TypeScript
import { Environment, SceneResourceParameters, SceneResourceFactory, Scene } from '@kit.ArkGraphics3D';

function createEnvironmentPromise(): Promise<Environment> {
  return new Promise((resolve, reject) => {
    // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
    let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
    scene.then(async (result: Scene) => {
      let sceneFactory: SceneResourceFactory = result.getResourceFactory();
      // 加载环境贴图资源，路径和文件名可根据项目实际资源自定义
      let sceneEnvironmentParameter: SceneResourceParameters = { name: "env", uri: $rawfile("KTX/quarry_02_2k_radiance.ktx") };
      // 创建Environment
      let env: Environment = await sceneFactory.createEnvironment(sceneEnvironmentParameter);
      resolve(env);
    }).catch((error: Error) => {
      console.error('Scene load failed:', error);
      reject(error);
    });
  });
}
```

## createGeometry

```TypeScript
createGeometry(params: SceneNodeParameters, mesh:MeshResource): Promise<Geometry>
```

创建几何节点.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SceneResourceFactory-createGeometry(params: SceneNodeParameters, mesh:MeshResource): Promise<Geometry>--><!--Device-SceneResourceFactory-createGeometry(params: SceneNodeParameters, mesh:MeshResource): Promise<Geometry>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [SceneNodeParameters](arkts-arkgraphics3d-scene-scenenodeparameters-i.md) | 是 | 创建几何体的参数 |
| mesh | [MeshResource](arkts-arkgraphics3d-sceneresources-meshresource-i.md) | 是 | resource - 几何体的网格数据 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Geometry](arkts-arkgraphics3d-scenenodes-geometry-i.md)&gt; | 返回创建的几何体 |

## 示例

```TypeScript
import { SceneResourceFactory, Scene, Geometry, CubeGeometry } from '@kit.ArkGraphics3D';

function createGeometryPromise() : Promise<Geometry> {
  return new Promise((resolve, reject) => {
    let scene: Promise<Scene> = Scene.load();
    scene.then(async (result: Scene | undefined) => {
      if (!result) {
        return;
      }
      let sceneFactory: SceneResourceFactory = result.getResourceFactory();
      // 创建立方体几何数据
      let cubeGeom = new CubeGeometry();
      cubeGeom.size = { x: 1, y: 1, z: 1 };
      // 根据立方体几何数据创建网格资源
      let meshRes = await sceneFactory.createMesh({ name: "MeshName" }, cubeGeom);
      console.info("TEST createGeometryPromise");
      // 根据场景节点参数和网格资源创建几何对象
      let geometry: Geometry = await sceneFactory.createGeometry({ name: "GeometryName" }, meshRes);
      resolve(geometry);
    }).catch((error: Error) => {
      console.error('Scene load failed:', error);
      reject(error);
    });
  });
}
```

## createLight

```TypeScript
createLight(params: SceneNodeParameters, lightType: LightType): Promise<Light>
```

Create a light.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SceneResourceFactory-createLight(params: SceneNodeParameters, lightType: LightType): Promise<Light>--><!--Device-SceneResourceFactory-createLight(params: SceneNodeParameters, lightType: LightType): Promise<Light>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [SceneNodeParameters](arkts-arkgraphics3d-scene-scenenodeparameters-i.md) | 是 | the param of creating a light |
| lightType | [LightType](arkts-arkgraphics3d-scenenodes-lighttype-e.md) | 是 | 光源类型 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Light](arkts-arkgraphics3d-scenenodes-light-i.md)&gt; | 返回创建的光源 |

## 示例

```TypeScript
import { SceneNodeParameters, LightType, Light, SceneResourceFactory, Scene } from '@kit.ArkGraphics3D';

function createLightPromise() : Promise<Light> {
  return new Promise((resolve, reject) => {
    // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
    let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
    scene.then(async (result: Scene) => {
      let sceneFactory: SceneResourceFactory = result.getResourceFactory();
      let sceneLightParameter: SceneNodeParameters = { name: "light" };
      // 创建平行光
      let light: Light = await sceneFactory.createLight(sceneLightParameter, LightType.DIRECTIONAL);
      resolve(light);
    }).catch((error: Error) => {
      console.error('Scene load failed:', error);
      reject(error);
    });
  });
}
```

## createMaterial

```TypeScript
createMaterial(params: SceneResourceParameters, materialType: MaterialType): Promise<Material>
```

Create a material.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SceneResourceFactory-createMaterial(params: SceneResourceParameters, materialType: MaterialType): Promise<Material>--><!--Device-SceneResourceFactory-createMaterial(params: SceneResourceParameters, materialType: MaterialType): Promise<Material>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [SceneResourceParameters](arkts-arkgraphics3d-scene-sceneresourceparameters-i.md) | 是 | the param of creating a material |
| materialType | [MaterialType](arkts-arkgraphics3d-sceneresources-materialtype-e.md) | 是 | 材质类型 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Material](arkts-arkgraphics3d-sceneresources-material-i.md)&gt; | 返回创建的材质 |

## 示例

```TypeScript
import { MaterialType, Material, SceneResourceParameters, SceneResourceFactory, Scene } from '@kit.ArkGraphics3D';

function createMaterialPromise() : Promise<Material> {
  return new Promise((resolve, reject) => {
    // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
    let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
    scene.then(async (result: Scene) => {
      let sceneFactory: SceneResourceFactory = result.getResourceFactory();
      let sceneMaterialParameter: SceneResourceParameters = { name: "material" };
      // 创建材质
      let material: Material = await sceneFactory.createMaterial(sceneMaterialParameter, MaterialType.SHADER);
      resolve(material);
    }).catch((error: Error) => {
      console.error('Scene load failed:', error);
      reject(error);
    });
  });
}
```

## createNode

```TypeScript
createNode(params: SceneNodeParameters): Promise<Node>
```

Create a node.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SceneResourceFactory-createNode(params: SceneNodeParameters): Promise<Node>--><!--Device-SceneResourceFactory-createNode(params: SceneNodeParameters): Promise<Node>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [SceneNodeParameters](arkts-arkgraphics3d-scene-scenenodeparameters-i.md) | 是 | 创建节点的参数 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Node](arkts-arkgraphics3d-scenenodes-node-i.md)&gt; | 返回创建的节点 |

## 示例

```TypeScript
import { SceneNodeParameters, SceneResourceFactory, Scene, Node } from '@kit.ArkGraphics3D';

function createNodePromise(): Promise<Node> {
  return new Promise((resolve, reject) => {
    // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
    let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
    scene.then(async (result: Scene) => {
      let sceneFactory: SceneResourceFactory = result.getResourceFactory();
      let sceneNodeParameter: SceneNodeParameters = { name: "empty_node",
        path:"/rootNode_/empty_node" };
      // 创建节点
      let node: Node = await sceneFactory.createNode(sceneNodeParameter);
      resolve(node);
    }).catch((error: Error) => {
      console.error('Scene load failed:', error);
      reject(error);
    });
  });
}
```

