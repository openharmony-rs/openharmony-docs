# Component3D(Defines 3D component)

定义Component3D组件.

## Component3D

```TypeScript
Component3D(sceneOptions?: SceneOptions)
```

构造函数使用的SceneOptions

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sceneOptions | [SceneOptions](arkts-arkui-sceneoptions-i.md) | 否 | 3D场景控制器 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [SceneOptions](arkts-arkui-sceneoptions-i.md) | 3D场景控制使用的场景选项@interface SceneOptions |

### 类型

| 名称 | 说明 |
| --- | --- |
| [Scene](arkts-arkui-scene-t.md) | 提供控制3D场景的方法 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ModelType](arkts-arkui-modeltype-e.md) | 模型类型枚举 @enum { number } |

## 示例

示例效果请以真机运行为准，当前DevEco Studio预览器不支持。GLTF模型加载示例。

```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
  scene: SceneOptions = { scene: $rawfile('gltf/DamagedHelmet/glTF/DamagedHelmet.gltf'), modelType: ModelType.SURFACE};
  build() {
    Row() {
      Column() {
        Text('GLTF Example')
        Component3D( this.scene )
        // 绑定环境资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
          .environment($rawfile('gltf/Environment/glTF/Environment.gltf'))
          .renderWidth('90%').renderHeight('90%')
      }.width('100%')
    }
    .height('100%')
  }
}
```

自定义渲染示例。

```TypeScript
import { AnimatorResult } from '@kit.ArkUI';

class EngineTime {
  totalTimeUs = 0;
  deltaTimeUs = 0;
};

let engineTime = new EngineTime();
let frameCount: number = 0;

function TickFrame() {
  if (frameCount == 10) {
    engineTime.totalTimeUs += 1.0;
    engineTime.deltaTimeUs += 1.0;
    frameCount = 0;
  } else {
    frameCount++;
  }
}

@Entry
@Component
struct Index {
  // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
  scene: SceneOptions = { scene: $rawfile('gltf/DamagedHelmet/glTF/DamagedHelmet.gltf'), modelType: ModelType.SURFACE};
  backAnimator: AnimatorResult = this.getUIContext().createAnimator({
    duration: 2000,
    easing: "ease",
    delay: 0,
    fill: "none",
    direction: "normal",
    iterations: -1,
    begin: 100,
    end: 200,
  });
  @State timeDelta: number[] = [1.0, 2.0];
  create() {
    this.backAnimator.onFinish = () => {
      console.info('backAnimator onfinish');
    }
    this.backAnimator.onFrame = (value: number) => {
      TickFrame();
      this.timeDelta[0] = engineTime.deltaTimeUs;
    }

  }
  build() {
    Row() {
      Column() {
        Text('custom rendering')
        Component3D()
          // 绑定自定义shader脚本，路径和文件名可根据项目实际资源自定义
          .shader($rawfile('assets/app/shaders/shader/London.shader'))
          // 绑定贴图资源作为shader输入纹理，路径和文件名可根据项目实际资源自定义
          .shaderImageTexture($rawfile('assets/London.jpg'))
          .shaderInputBuffer(this.timeDelta)
          // 绑定自定义渲染流程文件（如.rng），路径和文件名可根据项目实际资源自定义
          .customRender($rawfile('assets/app/rendernodegraphs/London.rng'), true)
          .renderWidth('90%').renderHeight('90%')
          .onAppear(() => {
            this.create();
            this.backAnimator.play();
          }).width('50%').height('50%')
      }.width('100%')
    }
    .height('100%')
  }
}
```
