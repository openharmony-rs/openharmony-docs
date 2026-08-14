# Camera

定义相机.

**继承/实现关系：** Camera extends [Node](arkts-arkgraphics3d-scenenodes-node-i.md#Node)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface Camera--><!--Device-unnamed-export interface Camera-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## getProjectionMatrix

```TypeScript
getProjectionMatrix(): Mat4x4
```

获取相机的投影矩阵.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Camera-getProjectionMatrix(): Mat4x4--><!--Device-Camera-getProjectionMatrix(): Mat4x4-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Mat4x4](arkts-arkgraphics3d-scenetypes-mat4x4-i.md) | 相机的投影矩阵 |

## 示例

```TypeScript
import { Scene, SceneResourceFactory, SceneNodeParameters, Camera, Mat4x4 } from '@kit.ArkGraphics3D';

function GetProjectionMatrix(): void {
  // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
  Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"))
    .then(async (result: Scene) => {
      if (!result.root) {
        return;
      }
      let sceneFactory: SceneResourceFactory = result.getResourceFactory();
      let sceneCameraParameter: SceneNodeParameters = { name: "camera1" };
      // 创建相机
      let camera: Camera = await sceneFactory.createCamera(sceneCameraParameter);
      camera.enabled = true;
      // 获取相机的投影矩阵
      let projectionMatrix: Mat4x4 = camera.getProjectionMatrix();
    });
}
```

## getViewMatrix

```TypeScript
getViewMatrix(): Mat4x4
```

获取相机的视图矩阵.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Camera-getViewMatrix(): Mat4x4--><!--Device-Camera-getViewMatrix(): Mat4x4-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Mat4x4](arkts-arkgraphics3d-scenetypes-mat4x4-i.md) | 相机的视图矩阵 |

## 示例

```TypeScript
import { Scene, SceneResourceFactory, SceneNodeParameters, Camera, Mat4x4 } from '@kit.ArkGraphics3D';

function GetViewMatrix(): void {
  // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
  Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"))
    .then(async (result: Scene) => {
      if (!result.root) {
        return;
      }
      let sceneFactory: SceneResourceFactory = result.getResourceFactory();
      let sceneCameraParameter: SceneNodeParameters = { name: "camera1" };
      // 创建相机
      let camera: Camera = await sceneFactory.createCamera(sceneCameraParameter);
      camera.enabled = true;
      // 获取相机的视图矩阵
      let viewMatrix: Mat4x4 = camera.getViewMatrix();
    });
}
```

## raycast

```TypeScript
raycast(viewPosition: Vec2, params: RaycastParameters): Promise<RaycastResult[]>
```

从屏幕指定位置发射射线，检测并返回所有命中的3D物体信息。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Camera-raycast(viewPosition: Vec2, params: RaycastParameters): Promise<RaycastResult[]>--><!--Device-Camera-raycast(viewPosition: Vec2, params: RaycastParameters): Promise<RaycastResult[]>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| viewPosition | [Vec2](arkts-arkgraphics3d-scenetypes-vec2-i.md) | 是 | 使用屏幕归一化坐标，取值范围为[0, 1]。 其中(0,0)表示Component3D控件的左上角，(1,1)表示Component3D控件的右下角。 |
| params | [RaycastParameters](arkts-arkgraphics3d-scene-raycastparameters-i.md) | 是 | 射线检测的配置参数（如检测范围、过滤节点等）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[RaycastResult](arkts-arkgraphics3d-scene-raycastresult-i.md)[]&gt; | Promise对象，返回命中的结果数组（按距离从近到远排序），若无命中则返回空数组。 |

## 示例

```TypeScript
import { SceneNodeParameters, Camera, SceneResourceFactory, Scene, Node, Vec2, Vec3, Quaternion,
  RaycastParameters } from '@kit.ArkGraphics3D';

function Raycast(): void {
  // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
  Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"))
    .then(async (result: Scene) => {
      if (!result.root) {
        return;
      }
      let node: Node | null | undefined = result.root.getNodeByPath("rootNode_/Unnamed Node 1/AnimatedCube");
      let sceneFactory: SceneResourceFactory = result.getResourceFactory();
      let sceneCameraParameter: SceneNodeParameters = { name: "camera1" };
      // 创建相机
      let camera: Camera = await sceneFactory.createCamera(sceneCameraParameter);
      camera.enabled = true;
      // 设置相机视角
      lookAt(camera, { x: 0, y: 0, z: -3 }, { x: 0, y: 0, z: 0 }, { x: 0, y: 1, z: 0 });

      let viewPos: Vec2 = { x: 0.5, y: 0.5 };
      let raycastParams: RaycastParameters = {};
      if (node) {
        raycastParams.rootNode = node;
      }
      return camera.raycast(viewPos, raycastParams);
    });
}

// 向量减法，返回l - r的结果
function Sub(l: Vec3, r: Vec3): Vec3 {
  return { x: l.x - r.x, y: l.y - r.y, z: l.z - r.z };
}
// 向量点积，返回l和r的内积
function Dot(l: Vec3, r: Vec3): number {
  return l.x * r.x + l.y * r.y + l.z * r.z;
}
// 向量归一化，返回l的单位向量
function Normalize(l: Vec3): Vec3 {
  let d = Math.sqrt(Dot(l, l));
  return { x: l.x / d, y: l.y / d, z: l.z / d };
}
// 向量叉积，返回l和r的叉乘结果
function Cross(l: Vec3, r: Vec3): Vec3 {
  return { x: (l.y * r.z - l.z * r.y), y: (l.z * r.x - l.x * r.z), z: (l.x * r.y - l.y * r.x) };
}
// 四元数标量乘法，返回四元数l乘以标量d的结果
function Mul(l: Quaternion, d: number): Quaternion {
  return {
    x: l.x * d,
    y: l.y * d,
    z: l.z * d,
    w: l.w * d
  };
}
// lookAt函数：将节点的位置和朝向设置为从eye位置看向center位置，up为上方向
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

背景清除颜色（环境背景会覆盖此颜色, 需要BACKGROUND_NONE才能实际生效).

**类型：** [Color](arkts-arkgraphics3d-scenetypes-color-i.md) \| null

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Camera-clearColor: Color | null--><!--Device-Camera-clearColor: Color | null-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## effects

```TypeScript
readonly effects: Container<Effect>
```

应用于相机输出的特效.

**类型：** [Container](arkts-arkgraphics3d-scenenodes-container-i.md)&lt;[Effect](arkts-arkgraphics3d-sceneresources-effect-i.md)&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Camera-readonly effects: Container<Effect>--><!--Device-Camera-readonly effects: Container<Effect>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## enabled

```TypeScript
enabled: boolean
```

相机是否启用.

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Camera-enabled: boolean--><!--Device-Camera-enabled: boolean-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## farPlane

```TypeScript
farPlane: double
```

相机远平面, 单位为世界坐标系下的场景单位（例如cm、m、km等）.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Camera-farPlane: double--><!--Device-Camera-farPlane: double-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## fov

```TypeScript
fov: double
```

相机视场, 单位为弧度.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Camera-fov: double--><!--Device-Camera-fov: double-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## msaa

```TypeScript
msaa?: boolean
```

控制是否启用MSAA.

**类型：** boolean

**默认值：** false

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Camera-msaa?: boolean--><!--Device-Camera-msaa?: boolean-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## nearPlane

```TypeScript
nearPlane: double
```

相机近平面, 单位为世界坐标系下的场景单位（例如cm、m、km等）.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Camera-nearPlane: double--><!--Device-Camera-nearPlane: double-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## postProcess

```TypeScript
postProcess: PostProcessSettings | null
```

相机的后处理设置.

**类型：** [PostProcessSettings](arkts-arkgraphics3d-scenepostprocesssettings-postprocesssettings-i.md) \| null

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Camera-postProcess: PostProcessSettings | null--><!--Device-Camera-postProcess: PostProcessSettings | null-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## renderingPipeline

```TypeScript
renderingPipeline?: RenderingPipelineType
```

控制渲染管线. 请注意，如果选择了FORWARD_LIGHTWEIGHT管线，某些功能将不可用.

**类型：** [RenderingPipelineType](arkts-arkgraphics3d-scenetypes-renderingpipelinetype-e.md)

**默认值：** RenderingPipelineType.FORWARD_LIGHTWEIGHT 前向轻量级渲染管线

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Camera-renderingPipeline?: RenderingPipelineType--><!--Device-Camera-renderingPipeline?: RenderingPipelineType-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

