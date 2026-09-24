# SceneResourceFactory

```TypeScript
export interface SceneResourceFactory extends RenderResourceFactory
```

Provides APIs for creating resources, such as cameras and light sources, used in 3D scenes. This class inherits from RenderResourceFactory.

@extends RenderResourceFactory @interface SceneResourceFactory

**Inheritance/Implementation:** SceneResourceFactory extends [RenderResourceFactory](arkts-arkgraphics3d-scene-renderresourcefactory-i.md)

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## createCamera

```TypeScript
createCamera(params: SceneNodeParameters): Promise<Camera>
```

Creates a camera based on scene node parameters. This API uses a promise to return the result.

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| params | [SceneNodeParameters](arkts-arkgraphics3d-scene-scenenodeparameters-i.md) | Yes | Scene node parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Camera](arkts-arkgraphics3d-scenenodes-camera-i.md)&gt; | Promise used to return the Camera object created. |

**Examples**

```TypeScript
import { SceneNodeParameters, Camera, SceneResourceFactory, Scene } from '@kit.ArkGraphics3D';

function createCameraPromise(): Promise<Camera> {
  return new Promise((resolve, reject) => {
    // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
    let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
    scene.then(async (result: Scene) => {
      let sceneFactory: SceneResourceFactory = result.getResourceFactory();
      let sceneCameraParameter: SceneNodeParameters = { name: "camera1" };
      // Create a camera.
      let camera: Camera = await sceneFactory.createCamera(sceneCameraParameter);
      resolve(camera);
    }).catch((err: Error) => {
      console.error(`Failed to load scene. Message: ${err.message}`);
      reject(err);
    });
  });
}
```

<a id="createcamera-1"></a>

## createCamera

```TypeScript
createCamera(params: SceneNodeParameters, cameraParams: CameraParameters): Promise<Camera>
```

Creates a camera based on scene node parameters and camera parameters. This API uses a promise to return the result.

**Since:** 21

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| params | [SceneNodeParameters](arkts-arkgraphics3d-scene-scenenodeparameters-i.md) | Yes | Scene node parameters. |
| cameraParams | [CameraParameters](arkts-arkgraphics3d-scene-cameraparameters-i.md) | Yes | Camera parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Camera](arkts-arkgraphics3d-scenenodes-camera-i.md)&gt; | Promise used to return the Camera object created. |

**Examples**

```TypeScript
import { SceneNodeParameters, Camera, SceneResourceFactory, Scene, CameraParameters,
  RenderingPipelineType } from '@kit.ArkGraphics3D';

function createCameraPromise(): Promise<Camera> {
  return new Promise((resolve, reject) => {
    // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
    let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
    scene.then(async (result: Scene) => {
      let sceneFactory: SceneResourceFactory = result.getResourceFactory();
      let nodeParameter: SceneNodeParameters = { name: "camera1" };
      let camParameter: CameraParameters = {renderingPipeline: RenderingPipelineType.FORWARD};
      // Create a camera.
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

Creates an effect object based on the effect parameters. This API uses a promise to return the result.

**Since:** 21

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| params | [EffectParameters](arkts-arkgraphics3d-scene-effectparameters-i.md) | Yes | Effect parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Effect](arkts-arkgraphics3d-sceneresources-effect-i.md)&gt; | Promise used to return the Effect object created. |

**Examples**

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
      // Effect ID, which is in the format of 'XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX', for example, 'e68a7f45-2d21-4a0d-9aef-7d9c825d3f12'.
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

Creates an environment based on the scene resource parameters. This API uses a promise to return the result.

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| params | [SceneResourceParameters](arkts-arkgraphics3d-scene-sceneresourceparameters-i.md) | Yes | Scene resource parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Environment](arkts-arkgraphics3d-sceneresources-environment-i.md)&gt; | Promise used to return the Environment object created. |

**Examples**

```TypeScript
import { Environment, SceneResourceParameters, SceneResourceFactory, Scene } from '@kit.ArkGraphics3D';

function createEnvironmentPromise(): Promise<Environment> {
  return new Promise((resolve, reject) => {
    // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
    let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
    scene.then(async (result: Scene) => {
      let sceneFactory: SceneResourceFactory = result.getResourceFactory();
      // Load environment map resources. The path and file name can be customized based on the specific project resources.
      let sceneEnvironmentParameter: SceneResourceParameters = { name: "env", uri: $rawfile("KTX/quarry_02_2k_radiance.ktx") };
      // Create an environment.
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

Creates a geometry object based on the scene node parameters and mesh data. This API uses a promise to return the result.

**Since:** 18

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| params | [SceneNodeParameters](arkts-arkgraphics3d-scene-scenenodeparameters-i.md) | Yes | Scene node parameters. |
| mesh | [MeshResource](arkts-arkgraphics3d-sceneresources-meshresource-i.md) | Yes | resource - Mesh data parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Geometry](arkts-arkgraphics3d-scenenodes-geometry-i.md)&gt; | Promise used to return the Geometry object created. |

**Examples**

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
      // Create cube geometry data.
      let cubeGeom = new CubeGeometry();
      cubeGeom.size = { x: 1, y: 1, z: 1 };
      // Create a mesh resource based on the cube geometry data.
      let meshRes = await sceneFactory.createMesh({ name: "MeshName" }, cubeGeom);
      console.info("TEST createGeometryPromise");
      // Create a geometry object based on the scene node parameters and mesh resource.
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

Creates a light based on the scene node parameters and light type. This API uses a promise to return the result.

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| params | [SceneNodeParameters](arkts-arkgraphics3d-scene-scenenodeparameters-i.md) | Yes | Scene node parameters. |
| lightType | [LightType](arkts-arkgraphics3d-scenenodes-lighttype-e.md) | Yes | Light type. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Light](arkts-arkgraphics3d-scenenodes-light-i.md)&gt; | Promise used to return the Light object created. |

**Examples**

```TypeScript
import { SceneNodeParameters, LightType, Light, SceneResourceFactory, Scene } from '@kit.ArkGraphics3D';

function createLightPromise() : Promise<Light> {
  return new Promise((resolve, reject) => {
    // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
    let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
    scene.then(async (result: Scene) => {
      let sceneFactory: SceneResourceFactory = result.getResourceFactory();
      let sceneLightParameter: SceneNodeParameters = { name: "light" };
      // Create directional light.
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

Creates a material based on the scene resource parameters and material type. This API uses a promise to return the result.

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| params | [SceneResourceParameters](arkts-arkgraphics3d-scene-sceneresourceparameters-i.md) | Yes | Scene resource parameters. |
| materialType | [MaterialType](arkts-arkgraphics3d-sceneresources-materialtype-e.md) | Yes | Material type. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Material](arkts-arkgraphics3d-sceneresources-material-i.md)&gt; | Promise used to return the Material object. |

**Examples**

```TypeScript
import { MaterialType, Material, SceneResourceParameters, SceneResourceFactory, Scene } from '@kit.ArkGraphics3D';

function createMaterialPromise() : Promise<Material> {
  return new Promise((resolve, reject) => {
    // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
    let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
    scene.then(async (result: Scene) => {
      let sceneFactory: SceneResourceFactory = result.getResourceFactory();
      let sceneMaterialParameter: SceneResourceParameters = { name: "material" };
      // Create a material.
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

Creates a node. This API uses a promise to return the result.

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| params | [SceneNodeParameters](arkts-arkgraphics3d-scene-scenenodeparameters-i.md) | Yes | Scene node parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Node](arkts-arkgraphics3d-scenenodes-node-i.md)&gt; | Promise object, which returns the node object. |

**Examples**

```TypeScript
import { SceneNodeParameters, SceneResourceFactory, Scene, Node } from '@kit.ArkGraphics3D';

function createNodePromise(): Promise<Node> {
  return new Promise((resolve, reject) => {
    // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
    let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
    scene.then(async (result: Scene) => {
      let sceneFactory: SceneResourceFactory = result.getResourceFactory();
      let sceneNodeParameter: SceneNodeParameters = { name: "empty_node",
        path:"/rootNode_/empty_node" };
      // Create a node.
      let node: Node = await sceneFactory.createNode(sceneNodeParameter);
      resolve(node);
    }).catch((err: Error) => {
      console.error(`Failed to load scene. Message: ${err.message}`);
      reject(err);
    });
  });
}
```
