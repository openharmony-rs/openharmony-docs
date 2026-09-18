# Camera

Camera node, which inherits from Node.

@extends Node @interface Camera

**Inheritance/Implementation:** Camera extends [Node](arkts-arkgraphics3d-scenenodes-node-i.md)

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## getProjectionMatrix

```TypeScript
getProjectionMatrix(): Mat4x4
```

Obtains the projection matrix of the camera.

**Since:** 23

**System capability:** SystemCapability.ArkUi.Graphics3D

**Return value:**

| Type | Description |
| --- | --- |
| [Mat4x4](arkts-arkgraphics3d-scenetypes-mat4x4-i.md) | Projection matrix of the camera. |

**Examples**

```TypeScript
import { Scene, SceneResourceFactory, SceneNodeParameters, Camera, Mat4x4 } from '@kit.ArkGraphics3D';

function GetProjectionMatrix(): void {
  // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
  Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"))
    .then(async (result: Scene) => {
      if (!result.root) {
        return;
      }
      let sceneFactory: SceneResourceFactory = result.getResourceFactory();
      let sceneCameraParameter: SceneNodeParameters = { name: "camera1" };
      // Create a camera.
      let camera: Camera = await sceneFactory.createCamera(sceneCameraParameter);
      camera.enabled = true;
      // Obtain the projection matrix of the camera.
      let projectionMatrix: Mat4x4 = camera.getProjectionMatrix();
    });
}
```

## getViewMatrix

```TypeScript
getViewMatrix(): Mat4x4
```

Obtains the view matrix of the camera.

**Since:** 23

**System capability:** SystemCapability.ArkUi.Graphics3D

**Return value:**

| Type | Description |
| --- | --- |
| [Mat4x4](arkts-arkgraphics3d-scenetypes-mat4x4-i.md) | View matrix of the camera. |

**Examples**

```TypeScript
import { Scene, SceneResourceFactory, SceneNodeParameters, Camera, Mat4x4 } from '@kit.ArkGraphics3D';

function GetViewMatrix(): void {
  // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
  Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"))
    .then(async (result: Scene) => {
      if (!result.root) {
        return;
      }
      let sceneFactory: SceneResourceFactory = result.getResourceFactory();
      let sceneCameraParameter: SceneNodeParameters = { name: "camera1" };
      // Create a camera.
      let camera: Camera = await sceneFactory.createCamera(sceneCameraParameter);
      camera.enabled = true;
      // Obtain the view matrix of the camera.
      let viewMatrix: Mat4x4 = camera.getViewMatrix();
    });
}
```

## raycast

```TypeScript
raycast(viewPosition: Vec2, params: RaycastParameters): Promise<RaycastResult[]>
```

Casts a ray from a specific position on the screen to detect and retrieve information about all hit 3D objects. This API uses a promise to return the result.

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| viewPosition | [Vec2](arkts-arkgraphics3d-scenetypes-vec2-i.md) | Yes | Normalized screen coordinates. The value range is [0, 1], where (0,0) corresponds to the top-left corner of the Component3D component, and (1,1) corresponds to the bottom-right corner. |
| params | [RaycastParameters](arkts-arkgraphics3d-scene-raycastparameters-i.md) | Yes | Configuration parameters for raycasting, such as detection range and filtered nodes. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[RaycastResult](arkts-arkgraphics3d-scene-raycastresult-i.md)[]&gt; | An array of hit objects sorted by distance (from nearest to farthest). If no objects are hit, an empty array is returned. |

**Examples**

```TypeScript
import { SceneNodeParameters, Camera, SceneResourceFactory, Scene, Node, Vec2, Vec3, Quaternion,
  RaycastParameters } from '@kit.ArkGraphics3D';

function Raycast(): void {
  // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
  Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"))
    .then(async (result: Scene) => {
      if (!result.root) {
        return;
      }
      let node: Node | null | undefined = result.root.getNodeByPath("rootNode_/Unnamed Node 1/AnimatedCube");
      let sceneFactory: SceneResourceFactory = result.getResourceFactory();
      let sceneCameraParameter: SceneNodeParameters = { name: "camera1" };
      // Create a camera.
      let camera: Camera = await sceneFactory.createCamera(sceneCameraParameter);
      camera.enabled = true;
      // Set the camera view.
      lookAt(camera, { x: 0, y: 0, z: -3 }, { x: 0, y: 0, z: 0 }, { x: 0, y: 1, z: 0 });

      let viewPos: Vec2 = { x: 0.5, y: 0.5 };
      let raycastParams: RaycastParameters = {};
      if (node) {
        raycastParams.rootNode = node;
      }
      return camera.raycast(viewPos, raycastParams);
    });
}

// Vector subtraction, which returns the result of l - r.
function Sub(l: Vec3, r: Vec3): Vec3 {
  return { x: l.x - r.x, y: l.y - r.y, z: l.z - r.z };
}
// Vector dot product, which returns the inner product of l and r.
function Dot(l: Vec3, r: Vec3): number {
  return l.x * r.x + l.y * r.y + l.z * r.z;
}
// Vector normalization, which returns the unit vector of l.
function Normalize(l: Vec3): Vec3 {
  let d = Math.sqrt(Dot(l, l));
  return { x: l.x / d, y: l.y / d, z: l.z / d };
}
// Vector cross product, which returns the cross product of l and r.
function Cross(l: Vec3, r: Vec3): Vec3 {
  return { x: (l.y * r.z - l.z * r.y), y: (l.z * r.x - l.x * r.z), z: (l.x * r.y - l.y * r.x) };
}
// Quaternion scalar multiplication, which returns the result of quaternion l multiplied by scalar d.
function Mul(l: Quaternion, d: number): Quaternion {
  return {
    x: l.x * d,
    y: l.y * d,
    z: l.z * d,
    w: l.w * d
  };
}
// lookAt function: sets the position and orientation of the node to look from the eye position toward the center position, with up as the up direction.
function lookAt(node: Node, eye: Vec3, center: Vec3, up: Vec3) {

  let t: number;

  let q: Quaternion = {
    x: 0.0,
    y: 0.0,
    z: 0.0,
    w: 0.0
  };
  let f = Normalize(Sub(center, eye));
  let m0 = Normalize(Cross(f, up));
  let m1 = Cross(m0, f);
  let m2: Vec3 = { x: -f.x, y: -f.y, z: -f.z };
  if (m2.z < 0) {
    if (m0.x > m1.y) {
      t = 1.0 + m0.x - m1.y - m2.z;
      q = {
        x: t,
        y: m0.y + m1.x,
        z: m2.x + m0.z,
        w: m1.z - m2.y
      };
    } else {
      t = 1.0 - m0.x + m1.y - m2.z;
      q = {
        x: m0.y + m1.x,
        y: t,
        z: m1.z + m2.y,
        w: m2.x - m0.z
      };
    }
  } else {
    if (m0.x < -m1.y) {
      t = 1.0 - m0.x - m1.y + m2.z;
      q = {
        x: m2.x + m0.z,
        y: m1.z + m2.y,
        z: t,
        w: m0.y - m1.x
      };
    } else {
      t = 1.0 + m0.x + m1.y + m2.z;
      q = {
        x: m1.z - m2.y,
        y: m2.x - m0.z,
        z: m0.y - m1.x,
        w: t
      };
    }
  }
  node.position = eye;
  node.rotation = Mul(q, 0.5 / Math.sqrt(t));
}
```

## clearColor

```TypeScript
clearColor: Color | null
```

Color after the render target is cleared.

**Type:** [Color](arkts-arkgraphics3d-scenetypes-color-i.md) &#124; null

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## effects

```TypeScript
readonly effects: Container<Effect>
```

Post-processing effects applied to the camera output.

**Type:** [Container](arkts-arkgraphics3d-scenenodes-container-i.md)&lt;[Effect](arkts-arkgraphics3d-sceneresources-effect-i.md)&gt;

**Since:** 21

**System capability:** SystemCapability.ArkUi.Graphics3D

## enabled

```TypeScript
enabled: boolean
```

Whether the camera is enabled. true if enabled, false otherwise.

**Type:** boolean

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## farPlane

```TypeScript
farPlane: number
```

Far plane. The unit is the scene unit (such as cm, m, and km) in the world coordinate system. The value is greater than that of nearPlane.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## fov

```TypeScript
fov: number
```

Field of view. The unit is radian (rad). The value ranges from 0 to π radians.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## msaa

```TypeScript
msaa?: boolean
```

Whether Multisample Anti-Aliasing (MSAA) is enabled. true if enabled, false otherwise. The default value is false.

**Type:** boolean

**Default:** false

**Since:** 22

**System capability:** SystemCapability.ArkUi.Graphics3D

## nearPlane

```TypeScript
nearPlane: number
```

Near plane. The unit is the scene unit (such as cm, m, and km) in the world coordinate system. The value is greater than 0.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## postProcess

```TypeScript
postProcess: PostProcessSettings | null
```

Post-processing settings.

**Type:** [PostProcessSettings](arkts-arkgraphics3d-scenepostprocesssettings-postprocesssettings-i.md) &#124; null

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## renderingPipeline

```TypeScript
renderingPipeline?: RenderingPipelineType
```

Rendering pipeline type. If this parameter is not set, the lightweight forward rendering pipeline is used by default. (If the FORWARD_LIGHTWEIGHT pipeline is selected, certain features are unavailable.)

**Type:** [RenderingPipelineType](arkts-arkgraphics3d-scenetypes-renderingpipelinetype-e.md)

**Default:** RenderingPipelineType.FORWARD_LIGHTWEIGHT

**Since:** 21

**System capability:** SystemCapability.ArkUi.Graphics3D
