# Component3D(Defines 3D component)

Defines Component3D component.

## Component3D

```TypeScript
Component3D(sceneOptions?: SceneOptions)
```

SceneOptions used by constructor

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sceneOptions | [SceneOptions](arkts-arkui-component3d-comp-sceneoptions-i.md) | No | The 3D scene controller |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [SceneOptions](arkts-arkui-component3d-comp-sceneoptions-i.md) | Scene options used by 3D scene control |

### Types

| Name | Description |
| --- | --- |
| [Scene](arkts-arkui-component3d-comp-scene-t.md) | Provides methods for controlling the 3d scene |

### Enums

| Name | Description |
| --- | --- |
| [ModelType](arkts-arkui-component3d-comp-modeltype-e.md) | The enum of model type @enum { number } |

## Examples

You can preview how this component looks on a real device, but not in DevEco Studio Previewer.Example of loading a GLTF model:

```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  // Load scene resources, which supports .gltf and .glb formats. Adapt the path and file name to your project.
  scene: SceneOptions = { scene: $rawfile('gltf/DamagedHelmet/glTF/DamagedHelmet.gltf'), modelType: ModelType.SURFACE};
  build() {
    Row() {
      Column() {
        Text('GLTF Example')
        Component3D( this.scene )
        // Bind environment resources, which supports .gltf and .glb formats. Adapt the path and file name to your project.
          .environment($rawfile('gltf/Environment/glTF/Environment.gltf'))
          .renderWidth('90%').renderHeight('90%')
      }.width('100%')
    }
    .height('100%')
  }
}
```

Custom rendering example:

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
  // Load scene resources, which supports .gltf and .glb formats. Adapt the path and file name to your project.
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
          // Bind the custom shader script. Adapt the path and file name to your project.
          .shader($rawfile('assets/app/shaders/shader/London.shader'))
          // Bind the texture resource as the shader input. Adapt the path and file name to your project.
          .shaderImageTexture($rawfile('assets/London.jpg'))
          .shaderInputBuffer(this.timeDelta)
          // Bind the render-node graph (.rng). The path and file name can be customized based on the specific project resources.
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
