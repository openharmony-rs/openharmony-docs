# SceneResourceFactory

用于创建3D场景中资源的接口，例如相机、光源等，继承自RenderResourceFactory。@extends RenderResourceFactory @interface SceneResourceFactory

**继承/实现关系：** SceneResourceFactory extends [RenderResourceFactory](arkts-arkgraphics3d-scene-renderresourcefactory-i.md)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## createCamera

```TypeScript
createCamera(params: SceneNodeParameters): Promise<Camera>
```

根据节点参数创建相机，使用Promise异步回调。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [SceneNodeParameters](arkts-arkgraphics3d-scene-scenenodeparameters-i.md) | 是 | 场景节点参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Camera](arkts-arkgraphics3d-scenenodes-camera-i.md)&gt; | Promise对象，返回相机对象。 |

**示例**

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
    }).catch((err: Error) => {
      console.error(`Failed to load scene. Message: ${err.message}`);
      reject(err);
    });
  });
}
```

## createCamera

```TypeScript
createCamera(params: SceneNodeParameters, cameraParams: CameraParameters): Promise<Camera>
```

根据节点参数与相机参数创建相机，使用Promise异步回调。

**起始版本：** 21

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [SceneNodeParameters](arkts-arkgraphics3d-scene-scenenodeparameters-i.md) | 是 | 场景节点参数。 |
| cameraParams | [CameraParameters](arkts-arkgraphics3d-scene-cameraparameters-i.md) | 是 | 相机参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Camera](arkts-arkgraphics3d-scenenodes-camera-i.md)&gt; | Promise对象，返回相机对象。 |

**示例**

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
    }).catch((err: Error) => {
      console.error(`Failed to load scene. Message: ${err.message}`);
      reject(err);
    });
  });
}
```

## createEffect

```TypeScript
createEffect(params: EffectParameters): Promise<Effect>
```

根据特效参数创建特效对象，使用Promise异步回调。

**起始版本：** 21

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [EffectParameters](arkts-arkgraphics3d-scene-effectparameters-i.md) | 是 | 特效参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Effect](arkts-arkgraphics3d-sceneresources-effect-i.md)&gt; | Promise对象，返回特效对象。 |

**示例**

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
    }).catch((err: Error) => {
      console.error(`Failed to load scene. Message: ${err.message}`);
      reject(err);
    });
  });
}
```

## createEnvironment

```TypeScript
createEnvironment(params: SceneResourceParameters): Promise<Environment>
```

根据场景资源参数创建环境，使用Promise异步回调。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [SceneResourceParameters](arkts-arkgraphics3d-scene-sceneresourceparameters-i.md) | 是 | 场景资源参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Environment](arkts-arkgraphics3d-sceneresources-environment-i.md)&gt; | Promise对象，返回环境对象。 |

**示例**

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
    }).catch((err: Error) => {
      console.error(`Failed to load scene. Message: ${err.message}`);
      reject(err);
    });
  });
}
```

## createGeometry

```TypeScript
createGeometry(params: SceneNodeParameters, mesh:MeshResource): Promise<Geometry>
```

根据场景节点参数和网格数据创建几何对象，使用Promise异步回调。

**起始版本：** 18

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [SceneNodeParameters](arkts-arkgraphics3d-scene-scenenodeparameters-i.md) | 是 | 场景节点参数。 |
| mesh | [MeshResource](arkts-arkgraphics3d-sceneresources-meshresource-i.md) | 是 | 网格数据参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Geometry](arkts-arkgraphics3d-scenenodes-geometry-i.md)&gt; | Promise对象，返回几何对象。 |

**示例**

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
    }).catch((err: Error) => {
      console.error(`Failed to load scene. Message: ${err.message}`);
      reject(err);
    });
  });
}
```

## createLight

```TypeScript
createLight(params: SceneNodeParameters, lightType: LightType): Promise<Light>
```

根据节点参数和灯光类型创建灯光，使用Promise异步回调。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [SceneNodeParameters](arkts-arkgraphics3d-scene-scenenodeparameters-i.md) | 是 | 场景节点参数。 |
| lightType | [LightType](arkts-arkgraphics3d-scenenodes-lighttype-e.md) | 是 | 灯光类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Light](arkts-arkgraphics3d-scenenodes-light-i.md)&gt; | Promise对象，返回灯光对象。 |

**示例**

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
    }).catch((err: Error) => {
      console.error(`Failed to load scene. Message: ${err.message}`);
      reject(err);
    });
  });
}
```

## createMaterial

```TypeScript
createMaterial(params: SceneResourceParameters, materialType: MaterialType): Promise<Material>
```

根据场景资源参数和材质类型创建材质，使用Promise异步回调。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [SceneResourceParameters](arkts-arkgraphics3d-scene-sceneresourceparameters-i.md) | 是 | 场景资源参数。 |
| materialType | [MaterialType](arkts-arkgraphics3d-sceneresources-materialtype-e.md) | 是 | 材质类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Material](arkts-arkgraphics3d-sceneresources-material-i.md)&gt; | Promise对象，返回材质对象。 |

**示例**

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
    }).catch((err: Error) => {
      console.error(`Failed to load scene. Message: ${err.message}`);
      reject(err);
    });
  });
}
```

## createNode

```TypeScript
createNode(params: SceneNodeParameters): Promise<Node>
```

创建节点，使用Promise异步回调。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [SceneNodeParameters](arkts-arkgraphics3d-scene-scenenodeparameters-i.md) | 是 | 场景节点参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Node](arkts-arkgraphics3d-scenenodes-node-i.md)&gt; | Promise对象，返回节点对象。 |

**示例**

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
    }).catch((err: Error) => {
      console.error(`Failed to load scene. Message: ${err.message}`);
      reject(err);
    });
  });
}
```
