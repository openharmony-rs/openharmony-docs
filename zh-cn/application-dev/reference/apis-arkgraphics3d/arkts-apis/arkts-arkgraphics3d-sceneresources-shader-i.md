# Shader

着色器，继承自SceneResource。

**继承/实现关系：** Shader extends [SceneResource](arkts-arkgraphics3d-sceneresources-sceneresource-i.md)

**起始版本：** 23

<!--Device-unnamed-export interface Shader--><!--Device-unnamed-export interface Shader-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## setShaderInputs

```TypeScript
setShaderInputs(inputs: Record<string, double | Vec2 | Vec3 | Vec4 | Image>): void
```

设置Shader的输入，该接口性能优于直接设置inputs属性。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Shader-setShaderInputs(inputs: Record<string, double | Vec2 | Vec3 | Vec4 | Image>): void--><!--Device-Shader-setShaderInputs(inputs: Record<string, double | Vec2 | Vec3 | Vec4 | Image>): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inputs | Record&lt;string, double \| [Vec2](arkts-arkgraphics3d-scenetypes-vec2-i.md) \| [Vec3](arkts-arkgraphics3d-scenetypes-vec3-i.md) \| [Vec4](arkts-arkgraphics3d-scenetypes-vec4-i.md) \| [Image](arkts-arkgraphics3d-sceneresources-image-i.md)&gt; | 是 | 一个字符串到值的映射，用于设置着色器输入。 |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { Image, MaterialType, Scene, SceneResourceFactory, Shader, ShaderMaterial } from '@kit.ArkGraphics3D';

function setinputs(): void {
  // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result) {
      let rf : SceneResourceFactory | null = await result.getResourceFactory();
      if (!rf) {
        return;
      }
      // 创建材质和shader
      let material: ShaderMaterial | null = await rf.createMaterial({name: "CustomMaterial"}, MaterialType.SHADER);
      let shader : Shader | null = await rf.createShader(
        {name: "CustomShader", uri: $rawfile("shaders/custom_shader/custom_material_sample.shader")});
      if (!material || !shader) {
        return;
      }
      // 加载纹理资源
      let image : Image | null = await rf.createImage({name: "envImg", uri: $rawfile("custom_image.jpg")});
      if (!image) {
        return;
      }
      // 设置材质的着色器
      material.colorShader = shader;
      // 设置shader输入
      material.colorShader.setShaderInputs({
        "uTime": 1.0,
        "uVelocity": {x: 1.0, y: 1.0, z:-1.0, w:-1.0},
        "uTexture": image
      });
    }
  });
}
```

ArkTS-Sta示例：

```TypeScript
import { $rawfile } from '@ohos.arkui.component'
import { Image, MaterialType, Scene, SceneResourceFactory, Shader, ShaderMaterial } from '@ohos.graphics.scene';

function setinputs(): void {
  // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result) {
      let rf : SceneResourceFactory = result.getResourceFactory();
      // 创建材质和shader
      let material: ShaderMaterial = await rf.createMaterial({name: "CustomMaterial"}, MaterialType.SHADER) as ShaderMaterial;
      let shader : Shader = await rf.createShader(
        {name: "CustomShader", uri: $rawfile("shaders/custom_shader/custom_material_sample.shader")});
      // 加载纹理资源
      let image : Image | null = await rf.createImage({name: "envImg", uri: $rawfile("custom_image.jpg")});
      if (!image) {
        throw new Error("createImage failed");
      }
      // 绑定shader到纹理上
      material.colorShader = shader;
      // 设置shader输入
      material.colorShader?.setShaderInputs({
        "uTime": 1.0,
        "uVelocity": {x: 1.0, y: 1.0, z:-1.0, w:-1.0},
        "uTexture": image
      })
    }
  });
}
```

## inputs

```TypeScript
readonly inputs: Record<string, double | Vec2 | Vec3 | Vec4 | Image>
```

着色器输入。

**类型：** Record&lt;string, double \| [Vec2](arkts-arkgraphics3d-scenetypes-vec2-i.md) \| [Vec3](arkts-arkgraphics3d-scenetypes-vec3-i.md) \| [Vec4](arkts-arkgraphics3d-scenetypes-vec4-i.md) \| [Image](arkts-arkgraphics3d-sceneresources-image-i.md)&gt;

**起始版本：** 23

<!--Device-Shader-readonly inputs: Record<string, double | Vec2 | Vec3 | Vec4 | Image>--><!--Device-Shader-readonly inputs: Record<string, double | Vec2 | Vec3 | Vec4 | Image>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

