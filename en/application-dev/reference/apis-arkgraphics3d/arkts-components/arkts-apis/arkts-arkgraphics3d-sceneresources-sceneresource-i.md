# SceneResource

Describes a resource in a scene.

@interface SceneResource

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## destroy

```TypeScript
destroy(): void
```

Destroys the scene resource and releases all associated resources or references. Once released, the resource can no longer be used or accessed.

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

**Examples**

```TypeScript
import { Shader, SceneResourceParameters, SceneResourceFactory, Scene } from '@kit.ArkGraphics3D';

function destroy(): void {
  // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result) {
      let sceneFactory: SceneResourceFactory = result.getResourceFactory();
      // Create shader resources. The path and file name can be customized based on the specific project resources.
      let sceneResourceParameter: SceneResourceParameters = { name: "shaderResource",
        uri: $rawfile("shaders/custom_shader/custom_material_sample.shader") };
      let shader: Promise<Shader> = sceneFactory.createShader(sceneResourceParameter);
      shader.then(async (shaderResult:Shader) => {
         // Release the resource.
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

Name. There is no special format requirement.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## resourceType

```TypeScript
readonly resourceType: SceneResourceType
```

Scene resource type. The default value is undefined.

**Type:** [SceneResourceType](arkts-arkgraphics3d-sceneresources-sceneresourcetype-e.md)

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## uri

```TypeScript
readonly uri?: ResourceStr
```

Resource to load. The default value is undefined.

**Type:** ResourceStr

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D
