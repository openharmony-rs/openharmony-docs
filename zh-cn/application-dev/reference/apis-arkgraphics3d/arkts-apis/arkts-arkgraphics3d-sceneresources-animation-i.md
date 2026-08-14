# Animation

动画资源.

**继承/实现关系：** Animation extends [SceneResource](arkts-arkgraphics3d-sceneresources-sceneresource-i.md#SceneResource)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface Animation--><!--Device-unnamed-export interface Animation-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## finish

```TypeScript
finish(): void
```

结束动画并将位置设置到结尾.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Animation-finish(): void--><!--Device-Animation-finish(): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## 示例

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

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Animation-onFinished(callback: Callback<void>): void--><!--Device-Animation-onFinished(callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | 动画完成时调用的回调 |

## 示例

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

注册动画开始时的回调.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Animation-onStarted(callback: Callback<void>): void--><!--Device-Animation-onStarted(callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | 动画开始时调用的回调 |

## 示例

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

暂停动画.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Animation-pause(): void--><!--Device-Animation-pause(): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## 示例

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

重新启动动画.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Animation-restart(): void--><!--Device-Animation-restart(): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## 示例

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
seek(position: double): void
```

将动画跳转到指定位置.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Animation-seek(position: double): void--><!--Device-Animation-seek(position: double): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | double | 是 | 跳转到0~1之间的位置 |

## 示例

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

开始动画.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Animation-start(): void--><!--Device-Animation-start(): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## 示例

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

停止动画并将位置设置到开头.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Animation-stop(): void--><!--Device-Animation-stop(): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## 示例

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
readonly duration: double
```

动画持续时间, 单位为秒.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Animation-readonly duration: double--><!--Device-Animation-readonly duration: double-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## enabled

```TypeScript
enabled: boolean
```

动画是否启用.

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Animation-enabled: boolean--><!--Device-Animation-enabled: boolean-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## progress

```TypeScript
readonly progress: double
```

动画在0~1之间的进度.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Animation-readonly progress: double--><!--Device-Animation-readonly progress: double-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## running

```TypeScript
readonly running: boolean
```

动画是否正在运行.

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Animation-readonly running: boolean--><!--Device-Animation-readonly running: boolean-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## speed

```TypeScript
speed?: double
```

动画速度因子 负值使用给定速度因子反向播放动画

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Animation-speed?: double--><!--Device-Animation-speed?: double-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

