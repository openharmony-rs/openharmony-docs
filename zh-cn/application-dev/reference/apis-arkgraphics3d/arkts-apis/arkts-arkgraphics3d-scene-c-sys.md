# Scene（系统接口）

```TypeScript
export declare class Scene
```

用于设置场景。Scene采用树状层次结构组织场景节点，根节点（root）作为场景的入口。

**起始版本：** 12

<!--Device-unnamed-export declare class Scene--><!--Device-unnamed-export declare class Scene-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## load

```TypeScript
static load(uri: ResourceStr, param: SceneLoadParams):Promise<Scene>
```

根据指定的资源路径和场景加载参数加载资源，使用Promise异步回调。该接口为耗时操作。在异步任务执行期间，调用其他接口可能会被阻塞，直到该异步任务完成。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Scene-static load(uri: ResourceStr, param: SceneLoadParams):Promise<Scene>--><!--Device-Scene-static load(uri: ResourceStr, param: SceneLoadParams):Promise<Scene>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | ResourceStr | 是 | 待加载的模型文件资源路径。 |
| param | [SceneLoadParams](arkts-arkgraphics3d-scene-sceneloadparams-i-sys.md) | 是 | 场景加载参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Scene](arkts-arkgraphics3d-scene-c.md)&gt; | Promise对象，返回场景对象。 |

<!--Del-->
**示例**

```TypeScript
import { Scene, SceneLoadParams } from '@kit.ArkGraphics3D';

function loadModelWithParams(): Promise<Scene> {
  let loadParams: SceneLoadParams = { offset: 0 };
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"), loadParams);
  return scene;
}
```

<!--DelEnd-->

## snapshot

```TypeScript
snapshot(cameras: Camera[], params: RenderTargetParameters[]): Promise<RenderTarget[]>
```

对当前场景进行离屏离屏渲染，根据传入的相机列表和渲染目标参数列表，使用离屏渲染方式生成各相机视角的渲染结果，使用Promise异步回调。每个相机与对应位置的渲染目标参数一一对应，渲染完成后可通过返回的[RenderTarget](arkts-arkgraphics3d-sceneresources-rendertarget-i-sys.md)对象获取[PixelMap](../../../reference/apis-image-kit/arkts-apis-image-PixelMap.md)。场景销毁后调用该接口时抛出错误码25601002，离屏渲染内存申请失败时抛出错误码25601005。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Scene-snapshot(cameras: Camera[], params: RenderTargetParameters[]): Promise<RenderTarget[]>--><!--Device-Scene-snapshot(cameras: Camera[], params: RenderTargetParameters[]): Promise<RenderTarget[]>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cameras | [Camera](arkts-arkgraphics3d-scenenodes-camera-i.md)[] | 是 | 用于离屏渲染的相机列表。相机之间不能重复，且在在屏渲染模式下不能包含场景的[主相机](arkts-arkgraphics3d-scenenodes-camera-i.md)。相机数组为空、存在重复相机、包含主相机或离屏渲染后总占用相机槽位数超过16时抛出错误码25603001。相机槽位总数上限为16，由场景中所有相机共享，包括：离屏渲染相机数组中每台相机各占1个、在屏主相机（在屏渲染时固定1个）、阴影相机（每盏开启阴影的灯光占1个）、透射材质预通道相机（场景含透射材质时每台相机（在屏和离屏相机）额外1个）。 |
| params | [RenderTargetParameters](arkts-arkgraphics3d-scene-rendertargetparameters-i-sys.md)[] | 是 | 渲染目标参数列表，与相机列表一一对应，指定每个渲染目标的尺寸等信息。数组长度与相机数组长度不一致时抛出错误码25603002。渲染目标尺寸小于或等于0时抛出错误码25603001。错误码按以下顺序校验：先校验25603002（相机数组与渲染目标参数数组长度是否一致），再校验25603001（数组为空、重复相机、主相机、尺寸超限、相机槽位不足等）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[RenderTarget](arkts-arkgraphics3d-sceneresources-rendertarget-i-sys.md)[]&gt; | Promise对象，返回渲染目标对象列表，与传入的相机列表一一对应。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 25601002 | Scene used after destruction. |
| 25601005 | Memory allocation failed. |
| 25603001 | Parameter exceeds the allowed range. |
| 25603002 | Input parameter type or count mismatch. |
