# SceneNode

<!--Kit: ArkGraphics 3D-->
<!--Subsystem: Graphics-->
<!--Owner: @jason_stark-->
<!--Designer: @zdustc-->
<!--Tester: @zhangyue283-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=4d7e02a7df2a06122e229dcfa39cff42326177c0 translatedAt=2026-08-20T12:26:57.125Z pushedAt=2026-08-21T08:43:10.144Z -->

This module provides the types and operation methods of scene resource nodes in ArkGraphics 3D. SceneNode is the basic building unit of a 3D scene. It allows developers to manage objects in a scene through a hierarchical structure, implementing efficient scene organization and interaction control.

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { LayerMask, NodeType, Container, Node, Geometry, LightType, Light, SpotLight, DirectionalLight,
  Camera } from '@kit.ArkGraphics3D';
```

## LayerMask

Defines the layer mask of a node.

### getEnabled

getEnabled(index: number): boolean

Checks whether the mask is enabled for a layer of a given index.

**System capability**: SystemCapability.ArkUi.Graphics3D

**Parameters**

| Name| Type| Mandatory| Description|
| ---- | ---- | ---- | ---- |
| index | number | Yes| Index of the layer. The value is an integer greater than or equal to 0.|

**Return value**

| Type| Description|
| ---- | ---- |
| boolean | Check result for whether the layer mask is enabled. **true** if enabled, **false** otherwise.|

**Example**

```ts
import { Scene, Node } from '@kit.ArkGraphics3D';

function layerMask(): void {
  // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result) {
      let node : Node | null = result.getNodeByPath("rootNode_");
      if (node) {
          // Obtain the enabling status of the mask. You can perform subsequent processing on the return value based on service requirements.
          let enabled: boolean = node.layerMask.getEnabled(1);
      }
    }
  }).catch((err: Error) => {
    console.error(`Failed to load scene. Message: ${err.message}`);
  });
}
```

### setEnabled

setEnabled(index: number, enabled: boolean): void

Enables the mask of a layer of a given index.

**System capability**: SystemCapability.ArkUi.Graphics3D

**Parameters**

| Name| Type| Mandatory| Description|
| ---- | ---- | ---- | ---- |
| index | number | Yes| Index of the layer. The value is an integer greater than or equal to 0.|
| enabled | boolean | Yes| Whether to enable the layer mask. **true** to enable, **false** otherwise.|

**Example**

```ts
import { Scene, Node } from '@kit.ArkGraphics3D';

function layerMask(): void {
  // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result) {
      let node : Node | null = result.getNodeByPath("rootNode/Scene/");
      if (node) {
          // Set the enabled status of the mask.
          node.layerMask.setEnabled(1, true);
      }
    }
  }).catch((err: Error) => {
    console.error(`Failed to load scene. Message: ${err.message}`);
  });
}
```

## NodeType

Enumerates the node types.

**System capability**: SystemCapability.ArkUi.Graphics3D

| Name| Value| Description|
| ---- | ---- | ---- |
| NODE | 1 | The node is an empty node.|
| GEOMETRY | 2 | Geometric type node.|
| CAMERA | 3 | Camera type node.|
| LIGHT | 4 | Light type node.|
| CUSTOM<sup>21+</sup> | 255 | Custom node, which is usually defined in an extension plugin.|

## Container\<T>

Container for defining scene nodes. It provides a way to group scene nodes into a hierarchy.

### append

append(item: T): void

Appends an object to the container. If the object to be appended already exists in the container, the container removes the object first and then inserts it, so the count does not increase.

**System capability**: SystemCapability.ArkUi.Graphics3D

**Parameters**

| Name| Type| Mandatory| Description|
| ---- | ---- | ---- | ---- |
| item | T | Yes| Object of the T type.|

**Example**

```ts
import { Scene, Node } from '@kit.ArkGraphics3D';

function append(): void {
  // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result) {
      let node : Node | null = result.getNodeByPath("rootNode/Scene/");
      if (node) {
        // Append a node. If the node is already in the children list, the total count does not change, but the operation is successful.
        result.root?.children.get(0)?.children.append(node);
      }
    }
  }).catch((err: Error) => {
    console.error(`Failed to load scene. Message: ${err.message}`);
  });
}
```

### insertAfter

insertAfter(item: T, sibling: T | null): void

Inserts an object after a sibling node. If the object to be inserted already exists in the container, the container removes the object first and then inserts it, so the count does not increase.

**System capability**: SystemCapability.ArkUi.Graphics3D

**Parameters**

| Name| Type| Mandatory| Description|
| ---- | ---- | ---- | ---- |
| item | T | Yes| Node to be inserted.|
| sibling | T \| null | Yes | Sibling node. If the value is null, the node is inserted at the beginning of the container. |

**Example**

```ts
import { Scene, Node } from '@kit.ArkGraphics3D';

function insertAfter(): void {
  // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result) {
      let node : Node | null = result.getNodeByPath("rootNode/Scene/");
      if (node) {
        // Insert a node after another. If the node is already in the children list, the total count does not change, but the operation is successful.
        result.root?.children.get(0)?.children.insertAfter(node, null);
      }
    }
  }).catch((err: Error) => {
    console.error(`Failed to load scene. Message: ${err.message}`);
  });
}
```

### remove

remove(item: T): void

Removes a node.

**System capability**: SystemCapability.ArkUi.Graphics3D

**Parameters**

| Name| Type| Mandatory| Description|
| ---- | ---- | ---- | ---- |
| item | T | Yes| Node to remove.|

**Example**

```ts
import { Scene, Node } from '@kit.ArkGraphics3D';

function remove(): void {
  // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result) {
      let node : Node | null = result.getNodeByPath("rootNode/Scene/");
      if (node) {
        // Call remove to remove a node.
        result.root?.children.remove(node);
      }
    }
  }).catch((err: Error) => {
    console.error(`Failed to load scene. Message: ${err.message}`);
  });
}
```

### get

get(index: number): T | null

Obtains a node of a given index. If no node is obtained, null is returned.

**System capability**: SystemCapability.ArkUi.Graphics3D

**Parameters**

| Name| Type| Mandatory| Description|
| ---- | ---- | ---- | ---- |
| index | number | Yes| Index of the node. The value is an integer greater than or equal to 0.|

**Return value**

| Type| Description|
| ---- | ---- |
| T \| null | Object obtained. If no object is obtained, null is returned.|

**Example**

```ts
import { Scene, Node } from '@kit.ArkGraphics3D';

function get(): void {
  // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result) {
      let node : Node | null = result.getNodeByPath("rootNode/Scene/");
      if (node) {
        // Obtain the node with index 0 from children.
        result.root?.children.get(0)?.children.insertAfter(node, null);
      }
    }
  }).catch((err: Error) => {
    console.error(`Failed to load scene. Message: ${err.message}`);
  });
}
```

### clear

clear(): void

Clears all nodes in the container.

**System capability**: SystemCapability.ArkUi.Graphics3D

**Example**

```ts
import { Scene, Node } from '@kit.ArkGraphics3D';

function clear(): void {
  // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result) {
      let node : Node | null = result.getNodeByPath("rootNode/Scene/");
      if (node) {
        //Clear all child nodes of the node.
        node.children.clear();
      }
    }
  }).catch((err: Error) => {
    console.error(`Failed to load scene. Message: ${err.message}`);
  });
}
```

### count

count(): number

Obtains the number of nodes in the container.

**System capability**: SystemCapability.ArkUi.Graphics3D

**Return value**

| Type| Description|
| ---- | ---- |
| number | Number of nodes in the container. The value is a non-negative integer.|

**Example**

```ts
import { Container, Scene, Node } from '@kit.ArkGraphics3D';

function count(): void {
  // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result) {
      let node : Node | null = result.getNodeByPath("rootNode_");
      if (node) {
        let container: Container<Node> = node.children;
        // Obtain the number of nodes in children.
        let count: number = container.count();
      }
    }
  });
}
```

## Node

A 3D scene consists of nodes in a tree-like hierarchical structure, where each node implements the Node interface. Inherited from [SceneResource](js-apis-inner-scene-resources.md#sceneresource).

### Properties

**System capability**: SystemCapability.ArkUi.Graphics3D

| Name| Type| Read Only| Optional| Description|
| ---- | ---- | ---- | ---- | ---- |
| position | [Position3](js-apis-inner-scene-types.md#position3) | No| No| Node position, in scene units of the world coordinate system (for example, cm, m, or km).|
| rotation | [Quaternion](js-apis-inner-scene-types.md#quaternion) | No| No| Rotation angle of a node.|
| scale | [Scale3](js-apis-inner-scene-types.md#scale3) | No| No| Node scale.|
| visible | boolean | No| No| Whether a node is visible. **true** if visible, **false** otherwise.|
| nodeType | [NodeType](#nodetype) | Yes| No| Node type.|
| layerMask | [LayerMask](#layermask) | Yes| No| Layer mask of a node.|
| path | string | Yes| No| Node path.|
| parent | [Node](#node) \| null | Yes| No| Parent node of the node and null if it does not exist.|
| children | [Container](#containert)\<[Node](#node)> | Yes | No | Child nodes of the node. If no child node exists, the value is empty. This is a read-only property, which means that the entire children container cannot be replaced, but child nodes can be operated through container methods (such as [append()](#append), [insertAfter()](#insertafter), [remove()](#remove), or [clear()](#clear)). If the node to be appended or inserted after already exists in the container, the container removes the node first and then inserts it, so the number does not increase and the operation seems to be ineffective. Only adding a new node actually increases the number of child nodes. |

### getNodeByPath

getNodeByPath(path: string): Node | null

Obtains a node by path. If no node is obtained, null is returned.

**System capability**: SystemCapability.ArkUi.Graphics3D

**Parameters**

| Name| Type| Mandatory| Description|
| ---- | ---- | ---- | ---- |
| path | string | Yes| Path in the scene node tree. Each layer is separated by a slash (/).|

**Return value**

| Type| Description|
| ---- | ---- |
| [Node](#node) \| null | Returns the node object.|

**Example**

```ts
import { Scene, Node } from '@kit.ArkGraphics3D';

function getNode(): void {
  // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result && result.root) {
      // Search for a node.
      let geo : Node | null = result.root.getNodeByPath("scene/node");
    }
  });
}
```

When calling getNodeByPath, you need to pass in the node path parameter path. You can obtain the available path value by traversing the node tree and printing the attributes of each node. The following is an example:

```ts
import { Scene, Node } from '@kit.ArkGraphics3D';

// Print the tree structure of the given node, with each line representing the path of a node.
function printNodeTreeInRelativePath(node: Node | null): void {
  if (!node) {
    return;
  }
  let basePath: string = node.path + node.name + '/';
  let printRelative = (n: Node | null): void => {
    if (!n) {
      return;
    }
    console.info(n.path.substring(basePath.length + 1) + n.name);
    for (let i = 0; i < n.children.count(); i++) {
      printRelative(n.children.get(i));
    }
  }
  for (let i = 0; i < node.children.count(); i++) {
    printRelative(node.children.get(i));
  }
}
```

## Geometry

Geometric node type that holds renderable mesh data and supports optional deformation features. It inherits from [Node](#node).

**System capability**: SystemCapability.ArkUi.Graphics3D

| Name| Type| Read Only| Optional| Description|
| ---- | ---- | ---- | ---- | ---- |
| mesh | [Mesh](js-apis-inner-scene-resources.md#mesh) | Yes| No| Mesh property.|
| morpher<sup>20+</sup> | [Morpher](js-apis-inner-scene-resources.md#morpher20) | Yes| Yes| Optional morpher that adds vertex-based deformation or animation effects to the geometry. If this parameter is not specified, the geometry does not support deformation.|

## LightType

Enumerates the light types.

**System capability**: SystemCapability.ArkUi.Graphics3D

| Name| Value| Description|
| ---- | ---- | ---- |
| DIRECTIONAL | 1 | Directional light.|
| SPOT | 2 | Spot light type. |

## Light

Light node, which inherits from [Node](#node).

**System capability**: SystemCapability.ArkUi.Graphics3D

| Name| Type| Read Only| Optional| Description|
| ---- | ---- | ---- | ---- | ---- |
| lightType | [LightType](#lighttype) | Yes| No| Light type.|
| color | [Color](js-apis-inner-scene-types.md#color) | No| No| Color.|
| intensity | number | No | No | Light intensity, in candela (cd). The value range is a real number greater than 0. |
| shadowEnabled | boolean | No| No| Whether the shadow effect is enabled. **true** if enabled, **false** otherwise.|
| enabled | boolean | No| No| Whether the light is used. **true** if used, **false** otherwise.|

## SpotLight

Spotlight, which inherits from [Light](#light).

A spotlight emits a conical beam of light in a specific direction, with the intensity of the light decaying according to the angles defined by the **innerAngle** and **outerAngle** parameters. Like a point light, a spotlight's intensity also diminishes with distance from the source.

**System capability**: SystemCapability.ArkUi.Graphics3D

| Name| Type| Read Only| Optional| Description|
| ---- | ---- | ---- | ---- | ---- |
| innerAngle<sup>23+</sup> | number | No| Yes| Angle from the center of the spotlight to the start of the decay, corresponding to the semi-apex angle of the cone, within which the light intensity does not decay with angle. The unit is radian (rad), and the default value is **0**. The value must be greater than or equal to **0** and less than or equal to **outerAngle**.|
| outerAngle<sup>23+</sup> | number | No| Yes| Angle from the center of the spotlight to the end of the decay, corresponding to the semi-apex angle of the cone, beyond which there is no light intensity. The unit is radian (rad), and the default value is **PI/4**. The value must be greater than or equal to **innerAngle** and less than or equal to **PI/2**.|

> **NOTE**
> 
> Ensure that the **innerAngle** and **outerAngle** values are proper. If the value set for **outerAngle** is greater than **PI/2**, it is forcibly set to **PI/2** internally. If the value set for **outerAngle** is less than **innerAngle**, it is forcibly set to **innerAngle** internally.

## DirectionalLight

Directional light, which inherits from [Light](#light).

**System capability**: SystemCapability.ArkUi.Graphics3D

## Camera

Camera node, which inherits from [Node](#node).

### Properties

**System capability**: SystemCapability.ArkUi.Graphics3D

| Name| Type| Read Only| Optional| Description|
| ---- | ---- | ---- | ---- | ---- |
| fov | number | No | No | Field of view, in radians (rad), with a value range of (0, π). |
| nearPlane | number | No| No| Near plane. The unit is the scene unit (such as cm, m, and km) in the world coordinate system. The value is greater than 0.|
| farPlane | number | No| No| Far plane. The unit is the scene unit (such as cm, m, and km) in the world coordinate system. The value is greater than that of nearPlane.|
| enabled | boolean | No| No| Whether the camera is enabled. **true** if enabled, **false** otherwise.|
| postProcess | [PostProcessSettings](js-apis-inner-scene-post-process-settings.md#postprocesssettings) \| null | No| No| Post-processing settings.|
| effects<sup>21+</sup> | [Container](js-apis-inner-scene-nodes.md#containert)\<[Effect](js-apis-inner-scene-resources.md#effect21)> | Yes| No| Post-processing effects applied to the camera output.|
| clearColor | [Color](js-apis-inner-scene-types.md#color) \| null | No| No| Color after the render target is cleared.|
| msaa<sup>22+</sup> | boolean | No| Yes| Whether Multisample Anti-Aliasing (MSAA) is enabled. **true** if enabled, **false** otherwise. The default value is **false**.|
| renderingPipeline<sup>21+</sup> | [RenderingPipelineType](js-apis-inner-scene-types.md#renderingpipelinetype21) | No| Yes| Rendering pipeline type. If this parameter is not set, the lightweight forward rendering pipeline is used by default. (If the **FORWARD_LIGHTWEIGHT** pipeline is selected, certain features are unavailable.)|

### raycast<sup>20+</sup>

raycast(viewPosition: Vec2, params: RaycastParameters): Promise<RaycastResult[]>

Casts a ray from a specific position on the screen to detect and retrieve information about all hit 3D objects. This API uses a promise to return the result.

**System capability**: SystemCapability.ArkUi.Graphics3D

**Parameters**

| Name| Type| Mandatory| Description|
| ---- | ---- | ---- | ---- |
| viewPosition | [Vec2](js-apis-inner-scene-types.md#vec2) | Yes| Normalized screen coordinates. The value range is [0, 1], where (0,0) corresponds to the top-left corner of the Component3D component, and (1,1) corresponds to the bottom-right corner.|
| params | [RaycastParameters](js-apis-inner-scene.md#raycastparameters20) | Yes| Configuration parameters for raycasting, such as detection range and filtered nodes.|

**Return value**

| Type| Description|
| ---- | ---- |
| Promise<[RaycastResult](js-apis-inner-scene.md#raycastresult20)[]> | Promise used to return the result. The value is an array of hit results sorted by distance from near to far, or an empty array if no hit occurs. |

**Example**

```ts
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

### getViewMatrix<sup>23+</sup>

getViewMatrix(): Mat4x4

Obtains the view matrix of the camera.

**System capability**: SystemCapability.ArkUi.Graphics3D

**Return value**

| Type| Description|
| ---- | ---- |
| [Mat4x4](js-apis-inner-scene-types.md#mat4x423) | View matrix of the camera.|

**Example**

```ts
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

### getProjectionMatrix<sup>23+</sup>

getProjectionMatrix(): Mat4x4

Obtains the projection matrix of the camera.

**System capability**: SystemCapability.ArkUi.Graphics3D

**Return value**

| Type| Description|
| ---- | ---- |
| [Mat4x4](js-apis-inner-scene-types.md#mat4x423) | Projection matrix of the camera.|

**Example**

```ts
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