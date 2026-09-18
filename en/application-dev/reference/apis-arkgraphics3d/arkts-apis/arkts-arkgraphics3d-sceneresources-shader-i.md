# Shader

Shader resource, which inherits from SceneResource.

@extends SceneResource @interface Shader

**Inheritance/Implementation:** Shader extends [SceneResource](arkts-arkgraphics3d-sceneresources-sceneresource-i.md)

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## setShaderInputs

```TypeScript
setShaderInputs(inputs: Record<string, number | Vec2 | Vec3 | Vec4 | Image>): void
```

Sets the inputs for the shader. This API delivers better performance than directly setting the inputs property.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| inputs | Record&lt;string, number &#124; [Vec2](arkts-arkgraphics3d-scenetypes-vec2-i.md) &#124; [Vec3](arkts-arkgraphics3d-scenetypes-vec3-i.md) &#124; [Vec4](arkts-arkgraphics3d-scenetypes-vec4-i.md) &#124; [Image](arkts-arkgraphics3d-sceneresources-image-i.md)&gt; | Yes | A mapping of strings to values for setting shader inputs. |

**Examples**

```TypeScript
import { Image, MaterialType, Scene, SceneResourceFactory, Shader, ShaderMaterial } from '@kit.ArkGraphics3D';

function setinputs(): void {
  // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result) {
      let rf : SceneResourceFactory | null = await result.getResourceFactory();
      if (!rf) {
        return;
      }
      // Create the material and shader.
      let material: ShaderMaterial | null = await rf.createMaterial({name: "CustomMaterial"}, MaterialType.SHADER);
      let shader : Shader | null = await rf.createShader(
        {name: "CustomShader", uri: $rawfile("shaders/custom_shader/custom_material_sample.shader")});
      if (!material || !shader) {
        return;
      }
      // Load the texture resource.
      let image : Image | null = await rf.createImage({name: "envImg", uri: $rawfile("custom_image.jpg")});
      if (!image) {
        return;
      }
      // Set the shader of the material.
      material.colorShader = shader;
      // Set the shader inputs.
      material.colorShader.setShaderInputs({
        "uTime": 1.0,
        "uVelocity": {x: 1.0, y: 1.0, z:-1.0, w:-1.0},
        "uTexture": image
      });
    }
  });
}
```

## inputs

```TypeScript
readonly inputs: Record<string, number | Vec2 | Vec3 | Vec4 | Image>
```

Inputs of the shader.

**Type:** Record&lt;string, number &#124; [Vec2](arkts-arkgraphics3d-scenetypes-vec2-i.md) &#124; [Vec3](arkts-arkgraphics3d-scenetypes-vec3-i.md) &#124; [Vec4](arkts-arkgraphics3d-scenetypes-vec4-i.md) &#124; [Image](arkts-arkgraphics3d-sceneresources-image-i.md)&gt;

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D
