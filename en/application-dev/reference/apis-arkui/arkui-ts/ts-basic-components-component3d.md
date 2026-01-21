# Component3D
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zzhao0-->
<!--Designer: @zdustc-->
<!--Tester: @zhangyue283-->
<!--Adviser: @ge-yafang-->

The **Component3D** component is used to load 3D model resources and create custom rendering. It is typically used to present 3D animations.

>  **NOTE**
>
>  This component is supported since API version 12. Updates will be marked with a superscript to indicate their earliest API version.

## Child Components

Not supported


## APIs

Component3D(sceneOptions?: SceneOptions)

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUi.Graphics3D

**Parameters**

| Name      | Type                                 | Mandatory| Description                                                        |
| ------------ | ------------------------------------- | ---- | ------------------------------------------------------------ |
| sceneOptions | [SceneOptions](#sceneoptions) | No  | 3D scene configuration.<br>**NOTE**<br> The 3D scene configuration cannot be dynamically modified after the component is created.|


## SceneOptions

Provides the 3D scene configuration options.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUi.Graphics3D

| Name       | Type                              | Read-Only| Optional  | Description                                      |
| --------- | -------------------------------- | ---- | ---- | ---------------------------------------- |
| scene     | [ResourceStr](ts-types.md#resourcestr) \| [Scene](#scene12) | No   | Yes   | 3D model resource file or scene object. Default value: **undefined**.<br>**NOTE**<br>Currently, only GLTF files are supported.|
| modelType | [ModelType](#modeltype) | No   | Yes   | Composition mode of the 3D scene.<br>Default value: **ModelType.SURFACE**.<br>**NOTE**<br>**ModelType.TEXTURE**: The GPU is used for composition.<br>**ModelType.SURFACE**: Dedicated hardware is used for composition.<br>In general cases, leave this parameter at its default settings.|

## ModelType

Enumerates the rendering and composition modes, which specify the rendering output mode of a 3D scene.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUi.Graphics3D

| Name   | Value  | Description                    |
| ------- | ---- | ------------------------ |
| TEXTURE | 0 | The GPU is used for composition of the 3D scene.|
| SURFACE | 1 | Dedicated hardware is used for composition of the 3D scene.|

## Scene<sup>12+</sup>

type Scene = Scene

Represents a 3D scene object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUi.Graphics3D

| Type                                                        | Description          |
| ------------------------------------------------------------ | -------------- |
| [Scene](../../apis-arkgraphics3d/js-apis-inner-scene.md#scene-1) | 3D scene object.|

## Attributes

In addition to the [universal attributes](ts-component-general-attributes.md), the following attributes are supported.

### environment

environment(uri: ResourceStr)

Sets the 3D environment resource. Currently, only GLTF files are supported. Model resources cannot be dynamically modified after the component is created.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUi.Graphics3D

**Parameters**

| Name| Type                                  | Mandatory| Description        |
| ------ | -------------------------------------- | ---- | ------------ |
| uri    | [ResourceStr](ts-types.md#resourcestr) | Yes  | 3D environment resource.|

### customRender

customRender(uri: ResourceStr, selfRenderUpdate: boolean)

Sets the custom 3D scene rendering pipeline. **uri** and **selfRenderUpdate** cannot be dynamically modified after the component is created.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUi.Graphics3D

**Parameters**

| Name          | Type                                  | Mandatory| Description                                                        |
| ---------------- | -------------------------------------- | ---- | ------------------------------------------------------------ |
| uri              | [ResourceStr](ts-types.md#resourcestr) | Yes  | Configuration file for creating a custom rendering pipeline.                                  |
| selfRenderUpdate | boolean                                | Yes  | Whether rendering can be triggered when the external UI is not updated.<br>The value **true** means that rendering can be triggered when the external UI is not updated, and **false** means the opposite.|

### shader

shader(uri: ResourceStr)

Sets the shader file for custom rendering. The shader file cannot be dynamically modified after the component is created.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUi.Graphics3D

**Parameters**

| Name| Type                                  | Mandatory| Description                        |
| ------ | -------------------------------------- | ---- | ---------------------------- |
| uri    | [ResourceStr](ts-types.md#resourcestr) | Yes  | Path to the shader file for custom rendering. For details about the .shader file format, see [Requirements on the .shader File Format](../../../graphics3d/arkgraphics3D-shader-resource.md).|

### shaderImageTexture

shaderImageTexture(uri: ResourceStr)

Sets the texture resource used for custom rendering. To use multiple texture resources for custom rendering, call this API multiple times. The sequence in which the resources are used is the same as the call sequence. The texture resource cannot be dynamically modified after the component is created.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUi.Graphics3D

**Parameters**

| Name| Type                                  | Mandatory| Description                      |
| ------ | -------------------------------------- | ---- | -------------------------- |
| uri    | [ResourceStr](ts-types.md#resourcestr) | Yes  | Path to the texture resource used for custom rendering.|

### shaderInputBuffer

shaderInputBuffer(buffer: Array&lt;number&gt;)

Set the animation parameters used for custom rendering. 

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUi.Graphics3D

**Parameters**

| Name| Type          | Mandatory| Description                      |
| ------ | -------------- | ---- | -------------------------- |
| buffer | Array<number\> | Yes  | Animation parameters used for custom rendering.<b>Array length range: [0, 1048576]|

### renderWidth

renderWidth(value: Dimension)

Sets the width of the 3D rendering resolution. The width and height of the rendering resolution may be different from those of the component. If this is the case, they are upsampled or downsampled to the component width and height.

If this attribute is not specified, the default width of the rendering resolution is used.

The rendering resolution cannot be dynamically changed after the component is created.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUi.Graphics3D

**Parameters**

| Name| Type                                | Mandatory| Description                |
| ------ | ------------------------------------ | ---- | -------------------- |
| value  | [Dimension](ts-types.md#dimension10) | Yes  | Width of the 3D rendering resolution. Currently, only **Dimension.Percentage** is supported. The value range is [0, 100%].|

### renderHeight

renderHeight(value: Dimension)

Sets the height of the 3D rendering resolution. The width and height of the rendering resolution may be different from those of the component. If this is the case, they are upsampled or downsampled to the component width and height.

If this attribute is not specified, the default height of the rendering resolution is used.

The rendering resolution cannot be dynamically changed after the component is created.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUi.Graphics3D

**Parameters**

| Name| Type                                | Mandatory| Description                |
| ------ | ------------------------------------ | ---- | -------------------- |
| value  | [Dimension](ts-types.md#dimension10) | Yes  | Height of the 3D rendering resolution. Currently, only **Dimension.Percentage** is supported. The value range is [0, 100%].|

## Events

The [universal events](ts-component-general-events.md) are supported.

## Example
You can preview how this component looks on a real device, but not in DevEco Studio Previewer.<br>
Example of loading a GLTF model:<br>
```ts
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
Custom rendering example:<br>

```ts
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
