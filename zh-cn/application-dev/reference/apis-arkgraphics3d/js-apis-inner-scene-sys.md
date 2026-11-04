# Scene (系统接口)
<!--Kit: ArkGraphics 3D-->
<!--Subsystem: Graphics-->
<!--Owner: @jason_stark-->
<!--Designer: @zdustc-->
<!--Tester: @dongchao01-->
<!--Adviser: @ge-yafang-->

本模块作为ArkGraphics 3D基础模块，提供场景加载参数等数据类型和场景加载方法。

> **说明：**
>
> - 本模块首批接口从API version 12开始支持，后续版本的新增接口，采用上角标标记接口的起始版本。
> - 页面仅包含本模块的系统接口，其他公开接口参见[Scene](js-apis-inner-scene.md)。

## 导入模块

```ts
import { SceneLoadParams, RenderTargetParameters, Scene, RenderResourceFactory } from '@kit.ArkGraphics3D';
```

## SceneLoadParams

场景加载参数对象，用于指定加载3D模型资源时的额外配置选项。典型使用场景为从MP4容器文件中加载内嵌的glb模型。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| offset | number | 否 | 是 | 3D模型数据在资源文件中的起始偏移量，单位为字节。系统将从资源文件的该偏移位置定位并读取glb模型数据。例如，当glb模型嵌在MP4容器文件中时，可将此参数设置为glb数据在MP4文件中的起始字节位置，使系统能够正确提取并加载模型。取值必须大于或等于0。默认值为0，表示模型数据从文件起始位置开始。 |

## RenderTargetParameters

渲染目标参数对象，继承自[SceneResourceParameters](js-apis-inner-scene.md#sceneresourceparameters)，用于描述渲染目标。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| size | [Vec2](js-apis-inner-scene-types.md#vec2) | 否 | 否 | 渲染目标的尺寸，x表示宽度，y表示高度，单位为像素（px），取值必须大于0，当取值为浮点数时向下取整。 |

## RenderResourceFactory

### createScene

createScene(uri: ResourceStr, param: SceneLoadParams): Promise\<Scene>

根据指定的资源路径和场景加载参数创建场景，使用Promise异步回调。

该接口为耗时操作。在异步任务执行期间，调用其他接口可能会被阻塞，直到该异步任务完成。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| uri | [ResourceStr](../apis-arkui/arkui-ts/ts-types.md#resourcestr) | 是 | 创建场景使用的资源路径。 |
| param | [SceneLoadParams](#sceneloadparams) | 是 | 场景加载参数。 |

**返回值：**

| 类型 | 说明 |
| ---- | ---- |
| Promise\<[Scene](js-apis-inner-scene.md#scene-1)> | Promise对象，返回创建的场景对象。 |

**示例：**

```ts
import { Scene, SceneLoadParams, RenderContext, RenderResourceFactory } from '@kit.ArkGraphics3D';

function createSceneWithParams(): Promise<Scene> {
  const renderContext: RenderContext | null = Scene.getDefaultRenderContext();
  if (!renderContext) {
    return Promise.reject(new Error("RenderContext is null"));
  }
  const renderResourceFactory: RenderResourceFactory = renderContext.getRenderResourceFactory();
  // 创建场景并传入场景加载参数，路径和文件名可根据项目实际资源自定义
  let loadParams: SceneLoadParams = { offset: 0 };
  return renderResourceFactory.createScene($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"), loadParams);
}
```

## Scene

### load

static load(uri: ResourceStr, param: SceneLoadParams): Promise\<Scene>

根据指定的资源路径和场景加载参数加载资源，使用Promise异步回调。

该接口为耗时操作。在异步任务执行期间，调用其他接口可能会被阻塞，直到该异步任务完成。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| uri | [ResourceStr](../apis-arkui/arkui-ts/ts-types.md#resourcestr) | 是 | 待加载的模型文件资源路径。 |
| param | [SceneLoadParams](#sceneloadparams) | 是 | 场景加载参数。 |

**返回值：**

| 类型 | 说明 |
| ---- | ---- |
| Promise\<[Scene](js-apis-inner-scene.md#scene-1)> | Promise对象，返回场景对象。 |

**示例：**

```ts
import { Scene, SceneLoadParams } from '@kit.ArkGraphics3D';

function loadModelWithParams(): Promise<Scene> {
  let loadParams: SceneLoadParams = { offset: 0 };
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"), loadParams);
  return scene;
}
```

### snapshot

snapshot(cameras: Camera[], params: RenderTargetParameters[]): Promise\<RenderTarget[]\>

对当前场景进行离屏渲染。根据传入的相机列表和渲染目标参数列表，使用离屏渲染方式生成各相机视角的渲染结果，使用Promise异步回调。

每个相机与对应位置的渲染目标参数一一对应，渲染完成后可通过返回的[RenderTarget](js-apis-inner-scene-resources-sys.md#rendertarget)对象获取[PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| cameras | [Camera](js-apis-inner-scene-nodes.md#camera)[] | 是 | 用于离屏渲染的相机列表。列表中的相机不能重复，且在屏渲染模式下不能包含场景的主相机（详见[Camera](js-apis-inner-scene-nodes.md#camera)）。离屏渲染相机会占用相机槽位，槽位规则及上限说明请参见[Camera](js-apis-inner-scene-nodes.md#camera)。<br>出现以下任一情况时，系统抛出错误码25603001：<br>- 相机数组为空；<br>- 相机数组中存在重复相机；<br>- 相机数组包含场景主相机；<br>- 离屏渲染后，场景总占用的相机槽位数超过上限。 |
| params | [RenderTargetParameters](#rendertargetparameters)[] | 是 | 渲染目标参数列表与相机列表一一对应，用于指定每个渲染目标的尺寸等信息。<br>数组长度与相机数组长度不一致时抛出错误码25603002，渲染目标的宽度或高度小于或等于0时抛出错误码25603001。<br>系统先校验25603002（相机数组与渲染目标参数数组长度是否一致），再校验25603001（数组元素合法性）。 |

**返回值：**

| 类型 | 说明 |
| ---- | ---- |
| Promise\<[RenderTarget](js-apis-inner-scene-resources-sys.md#rendertarget)[]\> | Promise对象，返回渲染目标对象列表，与传入的相机列表一一对应。 |

**错误码：**

以下错误码的详细介绍请参见[图形3D错误码](errorcode-graphics3d.md)。

| 错误码ID | 错误信息 |
| ---- | ---- |
| 25601002 | Scene used after destruction. |
| 25601005 | Memory allocation failed. |
| 25603001 | Parameter exceeds the allowed range. |
| 25603002 | Input parameter type or count mismatch. |

**示例：**

```ts
import { Scene, Camera, RenderTargetParameters } from '@kit.ArkGraphics3D';

function snapshotTest(): void {
  // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
  Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"), { offset: 0 })
    .then(async (result: Scene) => {
      if (!result.root) {
        return;
      }
      let sceneFactory = result.getResourceFactory();
      // 创建离屏渲染相机，用于离屏渲染，不能使用主相机
      let offscreenCamera: Camera = await sceneFactory.createCamera({ name: "offscreenCamera" });
      offscreenCamera.position = { x: 0, y: 0, z: 3 };
      // 配置渲染目标参数，设置渲染目标的尺寸为512*512像素
      let params: RenderTargetParameters = {
        name: "snapshotTarget",
        size: { x: 512, y: 512 }
      };
      // 声明Camera数组和RenderTargetParameters数组
      let cameras: Camera[] = [offscreenCamera];
      let targetParams: RenderTargetParameters[] = [params];
      // 对当前场景进行离屏渲染
      let renderTargets = await result.snapshot(cameras, targetParams);
      if (renderTargets.length > 0) {
        console.info("Snapshot width: " + renderTargets[0].width);
      }
    }).catch((err: Error) => {
      console.error(`Failed to take snapshot. Message: ${err.message}`);
    });
}
```
