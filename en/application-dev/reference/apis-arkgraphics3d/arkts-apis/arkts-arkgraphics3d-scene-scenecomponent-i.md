# SceneComponent

Represents a basic scene component, which is used to describe the component information of a scene node, including the component name and its properties.

@interface SceneComponent

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

## name

```TypeScript
name: string
```

Name of the scene component, which is customizable.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

## property

```TypeScript
readonly property: Record<string, string | number | Vec2 | Vec3 | Vec4 | SceneResource | boolean | number[] |
  string[] | SceneResource[] | Vec2[] | Vec3[] | Vec4[] | null | undefined>
```

A set of component properties stored in key-value pairs. It supports multiple basic and complex types to describe various properties of the scene component. The unit and value range depend on the specific scene component.

**Type:** Record&lt;string, string &#124; number &#124; [Vec2](arkts-arkgraphics3d-scenetypes-vec2-i.md) &#124; [Vec3](arkts-arkgraphics3d-scenetypes-vec3-i.md) &#124; [Vec4](arkts-arkgraphics3d-scenetypes-vec4-i.md) &#124; [SceneResource](arkts-arkgraphics3d-sceneresources-sceneresource-i.md) &#124; boolean &#124; number[] &#124; string[] &#124; [SceneResource](arkts-arkgraphics3d-sceneresources-sceneresource-i.md)[] &#124; [Vec2](arkts-arkgraphics3d-scenetypes-vec2-i.md)[] &#124; [Vec3](arkts-arkgraphics3d-scenetypes-vec3-i.md)[] &#124; [Vec4](arkts-arkgraphics3d-scenetypes-vec4-i.md)[] &#124; null &#124; undefined&gt;

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D
