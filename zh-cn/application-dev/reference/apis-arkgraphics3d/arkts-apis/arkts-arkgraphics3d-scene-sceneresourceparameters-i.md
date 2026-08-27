# SceneResourceParameters

场景资源参数对象，包含name和uri，用于提供场景资源的名称以及3D场景所需的资源文件路径。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## name

```TypeScript
name: string
```

要创建资源的名称，可由开发者自定义填写，用于标识该场景资源。

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## uri

```TypeScript
uri?: ResourceStr
```

3D场景所需的资源文件路径。默认值为undefined。

**类型：** ResourceStr

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

**示例**

```TypeScript
import { Shader, SceneResourceParameters, SceneResourceFactory, Scene } from '@kit.ArkGraphics3D';

function createShaderPromise(): Promise<Shader> {
  return new Promise((resolve, reject) => {
    // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
    let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
    scene.then(async (result: Scene) => {
      let sceneFactory: SceneResourceFactory = result.getResourceFactory();

      // 创建shader资源（通过SceneResourceParameters配置），路径和文件名可根据项目实际资源自定义
      let sceneResourceParameter: SceneResourceParameters = { name: "shaderResource",
        uri: $rawfile("shaders/custom_shader/custom_material_sample.shader") };
      let shader: Shader = await sceneFactory.createShader(sceneResourceParameter);
      resolve(shader);
    }).catch((err: Error) => {
      console.error(`Failed to load scene. Message: ${err.message}`);
      reject(err);
    });
  });
}
```
