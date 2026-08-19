# SceneResource

用于表示场景中的资源。

**起始版本：** 23

<!--Device-unnamed-export interface SceneResource--><!--Device-unnamed-export interface SceneResource-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## destroy

```TypeScript
destroy(): void
```

销毁场景资源，释放所有关联的资源或引用，一旦被释放，资源就不能被再次使用或访问。

**起始版本：** 23

<!--Device-SceneResource-destroy(): void--><!--Device-SceneResource-destroy(): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**示例**

```TypeScript
import { Shader, SceneResourceParameters, SceneResourceFactory, Scene } from '@kit.ArkGraphics3D';

function destroy(): void {
  // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result) {
      let sceneFactory: SceneResourceFactory = result.getResourceFactory();
      // 创建shader资源，路径和文件名可根据项目实际资源自定义
      let sceneResourceParameter: SceneResourceParameters = { name: "shaderResource",
        uri: $rawfile("shaders/custom_shader/custom_material_sample.shader") };
      let shader: Promise<Shader> = sceneFactory.createShader(sceneResourceParameter);
      shader.then(async (shaderResult:Shader) => {
         // 释放资源
         shaderResult.destroy();
      });
    }
  });
}
```

## name

```TypeScript
name: string
```

名称，没有特殊格式要求。

**类型：** string

**起始版本：** 23

<!--Device-SceneResource-name: string--><!--Device-SceneResource-name: string-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## resourceType

```TypeScript
readonly resourceType: SceneResourceType
```

场景资源类型，默认值为undefined。

**类型：** [SceneResourceType](arkts-arkgraphics3d-sceneresources-sceneresourcetype-e.md)

**起始版本：** 23

<!--Device-SceneResource-readonly resourceType: SceneResourceType--><!--Device-SceneResource-readonly resourceType: SceneResourceType-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## uri

```TypeScript
readonly uri?: ResourceStr
```

需要加载的资源，默认值为undefined。

**类型：** ResourceStr

**起始版本：** 23

<!--Device-SceneResource-readonly uri?: ResourceStr--><!--Device-SceneResource-readonly uri?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

