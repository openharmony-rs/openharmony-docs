# SceneResourceParameters

Describes the scene resource parameters (name and uri), which are used to provide the name of a scene resource and the path of the resource file required in the 3D scene.

@typedef SceneResourceParameters

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## name

```TypeScript
name: string
```

Name of the scene resource. It is customizable.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## uri

```TypeScript
uri?: ResourceStr
```

Path of the resource file required in the 3D scene. The default value is undefined.

**Type:** ResourceStr

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

**Examples**

```TypeScript
import { Shader, SceneResourceParameters, SceneResourceFactory, Scene } from '@kit.ArkGraphics3D';

function createShaderPromise(): Promise<Shader> {
  return new Promise((resolve, reject) => {
    // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
    let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
    scene.then(async (result: Scene) => {
      let sceneFactory: SceneResourceFactory = result.getResourceFactory();

      // Create shader resources, which are configured through SceneResourceParameters. The path and file name can be customized based on the specific project resources.
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
