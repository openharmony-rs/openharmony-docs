# Animation

动画类型，继承自SceneResource。

@extends SceneResource @interface Animation

**继承/实现关系：** Animation extends [SceneResource](arkts-arkgraphics3d-sceneresources-sceneresource-i.md)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## finish

```TypeScript
finish(): void
```

直接跳转到动画的最后，并将动画的进度设置为1。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

**示例**

```TypeScript
import { Animation, Scene } from '@kit.ArkGraphics3D';

function finish(): void {
  // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result && result.animations && result.animations[0]) {
      let anim: Animation = result.animations[0];
      // 直接跳转到动画的最后，并将动画的进度设置为1。
      anim.finish();
    }
  });
}
```

## onFinished

```TypeScript
onFinished(callback: Callback<void>): void
```

动画播放结束时执行的回调函数，动画播放完成或者finish操作会触发这个回调。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | 回调函数，返回值为空。 |

**示例**

```TypeScript
import { Animation, Scene } from '@kit.ArkGraphics3D';

function onFinished(): void {
  // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result && result.animations && result.animations[0]) {
      let anim: Animation = result.animations[0];
      // 注册回调函数
      anim.onFinished(()=>{
        console.info("onFinished");  
      });
    }
  });
}
```

## onStarted

```TypeScript
onStarted(callback: Callback<void>): void
```

当动画开始播放时执行的回调函数，start操作以及restart操作也会触发这个回调。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | 回调函数，返回值为空。 |

**示例**

```TypeScript
import { Animation, Scene } from '@kit.ArkGraphics3D';

function onStarted(): void {
  // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result && result.animations && result.animations[0]) {
      let anim: Animation = result.animations[0];
      // 注册回调函数
      anim.onStarted(()=>{
        console.info("onStarted");  
      });
    }
  });
}
```

## pause

```TypeScript
pause(): void
```

将动画暂停，动画的播放进度保持在当前状态。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

**示例**

```TypeScript
import { Animation, Scene } from '@kit.ArkGraphics3D';

function pause(): void {
  // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result && result.animations && result.animations[0]) {
      let anim: Animation = result.animations[0];
      // 暂停动画
      anim.pause();
    }
  });
}
```

## restart

```TypeScript
restart(): void
```

从动画的起点开始播放动画。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

**示例**

```TypeScript
import { Animation, Scene } from '@kit.ArkGraphics3D';

function restart(): void {
  // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result && result.animations && result.animations[0]) {
      let anim: Animation = result.animations[0];
      // 重启动画
      anim.restart();
    }
  });
}
```

## seek

```TypeScript
seek(position: number): void
```

将动画进度跳转到指定位置，不改变动画的播放状态（已播放仍继续播放，已暂停仍暂停）。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | number | 是 | 要重新播放动画的起始位置，取值区间为[0, 1]。 |

**示例**

```TypeScript
import { Animation, Scene } from '@kit.ArkGraphics3D';

function seek(): void {
  // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result && result.animations && result.animations[0]) {
      let anim: Animation = result.animations[0];
      // 指定动画的播放进度到10%
      anim.seek(0.1);
    }
  });
}
```

## start

```TypeScript
start(): void
```

基于当前进度开始播放一个动画。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

**示例**

```TypeScript
import { Animation, Scene } from '@kit.ArkGraphics3D';

function start(): void {
  // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result && result.animations && result.animations[0]) {
      let anim: Animation = result.animations[0];
      // 开始动画
      anim.start();
    }
  });
}
```

## stop

```TypeScript
stop(): void
```

停止播放一个动画，并将动画的进度设置为0。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

**示例**

```TypeScript
import { Animation, Scene } from '@kit.ArkGraphics3D';

function stop(): void {
  // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result && result.animations && result.animations[0]) {
      let anim: Animation = result.animations[0];
      // 停止播放动画，并将动画的进度设置为0
      anim.stop();
    }
  });
}
```

## duration

```TypeScript
readonly duration: number
```

动画持续时间，单位为秒（s），取值范围大于等于0。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## enabled

```TypeScript
enabled: boolean
```

动画是否启用。true表示可以播放动画，false表示不可以播放动画。

**类型：** boolean

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## progress

```TypeScript
readonly progress: number
```

动画进度状态，取值区间为[0, 1]。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## running

```TypeScript
readonly running: boolean
```

动画运行状态。true表示动画正在播放，false表示动画停止播放。

**类型：** boolean

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## speed

```TypeScript
speed?: number
```

动画的播放速度因子。默认值为1.0，表示正常速度播放。如果设置为负值，动画将以反向速度播放。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.ArkUi.Graphics3D
